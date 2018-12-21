---
layout: post
comments: true
title: "Angular Startup Project"
tags: [angular]
author: "Andy Knight"
---
I wanted to write about how I get up and running with a new angular project. This is a real beginner post but also just to show I do things. My favourite editor for all client side JS and web is definitely Visual Studio Code. Its lightweight, fast and perfect for traversing a web project. So here goes!

#### Creating the project
Make sure you're up to date with the latest npm. You'll also need the latest angular CLI package, which you can install with the following:

{% highlight powershell %}
npm install -g @angular/cli
{% endhighlight %}

Next up we need to create our new project using the Angular CLI. Simply the following command including your project name, this will create a sub folder from whichever directory you're in.

{% highlight powershell %}
ng new my-app
{% endhighlight %}

> At the time of writing this post, I'm using version 6.5.0 of the Angular CLI. In this version you will be prompted the following questions: Would you like to add Angular routing? Which stylesheet format would you like to use? I always choose Yes for routing and default CSS.

After a few minutes and a whirlwind of messages, you're new angular will be ready. Open Visual Studio Code and select your new project folder.

![Project files](/assets/img/2018-12-21/appfiles.png) 

### Project Changes

There's a couple things I want to immediately change in the `project.json` file. Firstly I like to have a browser window automatically open when I run the project. Secondly, I want to include some additional dependencies that we'll need. Bootstrap is a great and common way to style your web apps so we'll introduce that. It requires two other dependencies so go ahead and edit the `project.json` file to the changes I've made below. (The version you have available maybe different to mine at the time of writing)

![package.json](/assets/img/2018-12-21/packagejson.png) 

Secondly, open the `angular.json` file. We need to include our css in the `[styles]` section. Add the following line below the existing `src/styles.css` line:

{% highlight powershell %}
"node_modules/bootstrap/dist/css/bootstrap.css"
{% endhighlight %}

### Html Changes

We'll go ahead and build our new project shortly but to get started with a bootstrap layout, replace the contents of the `index.html` file with the following:

<script src="https://gist.github.com/andymk/9658e4f0978edf1752a7eac8e3e360a0.js"></script>

### Running your webapp

Because we made changes to the `package.json` file we need to get NPM to do its job. Open a terminal window in VS Code (`<Ctrl> + '`) and type the following commands: 

{% highlight powershell %}
npm install
npm start
{% endhighlight %}

The install parameter will download the bootstrap packages. The start parameter build our project and launch a web server and browser.

![bootstrapped](/assets/img/2018-12-21/bootstrapped.png) 

### Finally

This is the very basics on getting a new angular project going. I will continue this with next steps to layout components and routing. Until next time!
