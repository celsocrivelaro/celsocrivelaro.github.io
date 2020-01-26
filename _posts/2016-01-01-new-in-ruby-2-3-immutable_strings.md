---
layout: post
title: Ruby 2.3 - Immutable Strings Pragma / Frozen Strings
categories: [programming]
tags: [ruby]
date: 2016-01-01 18:11:36 -0200
author: Celso Crivelaro
---
Ruby 2.3 was released on Christmas Day - December 25th, 2015 with some great features! As a rubyst, I excited about the importance of perfomance that Ruby team is working on.

In this post, I'm going to talk about some new String features.

# Immutable Strings Pragma

By default, Ruby has mutable String objects and `.freeze` method transforms in an immutable String. Latter I'll explain why immutable Strings are important to your Ruby code.

How it is hard to do for each String, the magic comment transforms all Strings to immutable in the file.

{% highlight ruby %}
# frozen_string_literal: true

"Ruby".frozen?
#=> true
{% endhighlight %}

Another way to have it for all your application is running on script call:

{% highlight bash %}
 $ ruby --enable-frozen-string-literal -e "puts 'a'.frozen?"
true
{% endhighlight %}

You probaly are wondering why to use immutable structures. Let's face the consequences of mutable and immutable structures:

## Same strings are different objects

{% highlight ruby %}
irb(main):001:0> 'abc'.object_id
=> 70276411205020
irb(main):002:0> 'abc'.object_id
=> 70276411155260
{% endhighlight %}

When these strings are frozen, i.e. immutable, they behave the same way of symbols:

{% highlight ruby %}
irb(main):003:0> 'abc'.freeze.object_id
=> 70276411205040
irb(main):004:0> 'abc'.freeze.object_id
=> 70276411205040
{% endhighlight %}

## String.+@ and String.-@ operators

In the context with default immutable or mutable Strings, we going to need use faster transformation operator. In order to do so, two new String operators were created:

- **String.-@** transforms mutable strings in immutable strings 
- **String.+@** transforms immutable strings in mutable strings

{% highlight ruby %}
irb(main):001:0> (-"test").frozen?
=> true
irb(main):002:0> (+("teste".freeze)).frozen?
=> false
{% endhighlight %}

# What is the importance of immutable strings?

Immutable Strings is being discussed to be the default after Ruby 3.0, however, most of programmers who learnt to program in interpreted language don't know the importante of this. 

If you have already worked with Java or Objective-C, this concept is straightforward, however, Ruby abstracts so easily this concept that is hard no know if you learned programing by Ruby.

## Less Memmory allocation and faster code

Less memory is allocated once when a String is immutable. For consequence, your code runs faster because allocating new objects is a costly operation (calling OS for free space, pagination when memory is almost full, so on...).

## Less Garbage Collector calls

Symbols are collected as well as other objects, however, as an special object, is marked to be collected after other objects that lost their reference.

Garbage Collection is a very slow operation, less calls, faster your code is.

You might see all changes in [Changelog][ruby-changelog].

[ruby-changelog]: https://github.com/ruby/ruby/blob/v2_3_0/NEWS
