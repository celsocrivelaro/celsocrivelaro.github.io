---
layout: post
title: Hello World in Docker
categories: [docker]
tags: [docker]
date: 2015-12-26 01:52:48 -0200
author: Celso Crivelaro
---

![Docker logo](/images/dockerlogo.png)

As a programming language, Docker has its own "Hello World" container to test a basic container usage.

In order to use it, just run in your bash:

{% highlight bash %}
 $ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
b901d36b6f2f: Pull complete
0a6ba66e537a: Pull complete
Digest: sha256:8be990ef2aeb16dbcb9271ddfe2610fa6658d13f6dfb8bc72074cc1ca36966a7
Status: Downloaded newer image for hello-world:latest

Hello from Docker.
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker Hub account:
 https://hub.docker.com

For more examples and ideas, visit:
 https://docs.docker.com/userguide/
{% endhighlight %}

A couple of actions happened. What happened here in details:

{% highlight bash %}
 $ docker run hello-world
{% endhighlight %}

You ran in your console `docker run` command to run a named container `hello-world`.

{% highlight bash %}
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
{% endhighlight %}

This container was not available in locally your host and thus Docker pulls last version of the image from Docker Hub registry. More details about **pull** action will be explained in other article.

This image is available in [Docker Hub][hello-world] 

{% highlight bash %}
b901d36b6f2f: Pull complete
0a6ba66e537a: Pull complete
Digest: sha256:8be990ef2aeb16dbcb9271ddfe2610fa6658d13f6dfb8bc72074cc1ca36966a7
Status: Downloaded newer image for hello-world:latest
{% endhighlight %}

Docker downloads image layers and creates your container. As you invoked `docker run`, it runs the executable (this is a simple executable that prints on the screen).

If you run again, the image won't be pulled again:

{% highlight bash %}
 $ docker run hello-world

Hello from Docker.
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker Hub account:
 https://hub.docker.com

For more examples and ideas, visit:
 https://docs.docker.com/userguide/
{% endhighlight %}

[hello-world]: https://hub.docker.com/_/hello-world/