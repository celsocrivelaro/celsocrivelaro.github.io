---
layout: post
title: Web Server x Application Server
categories: [programming]
tags: [oo]
date: 2017-07-08 11:11:36 -0200
author: Celso Crivelaro
---

Functional Programming

Side Effects change the state of application, in your case, of the instanciated objects.

Example of a code with Side Effect
```ruby
class Person
  attr_accessor :name
end

class PersonNameChanger
  def self.change_name(person)
    person.capitalize!
  end
end

person = Person.new(name: "Celso Crivelaro")

PersonNameChanger.change_name(person)

```

This simple Class changes Person attribute name 
