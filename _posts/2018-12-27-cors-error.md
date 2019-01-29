---
layout: post
comments: true
title: "Access to XMLHttpRequest has been blocked by CORS policy"
tags: [netcore]
author: "Andy Knight"
---

Years ago I did all my development in Visual Studio. Back then, web apps had an MVC frontend and an API layer, all nicely packaged in one project. But with the latest clientside JS frameworks and .Net Core, the architecture of applications have changed. When Visual Studio 2017 first released, many developers reported issues editing projects with huge JS contents files. At the same time, Visual Studio Code was generating popularity fast as a lightweight, customisable editor, great for managing web applications. Nowadays my "goto" architecture for applications is developing Angular frontend web apps in Visual Studio Code, that communicate with a webapi developed in Visual Studio 2017. Web stuff in Code, .Net Core stuff in VS2017.

### Enter the dreaded CORS

.Net Core comes with security enhancements, which you'll soon discover if you develop in the above environments. This particular security isn’t anything new, but it’s something that becomes more relevant with modern clientside JS apps.

[Wikipedia][corswiki-url] define CORS as:

Cross-origin resource sharing (CORS) is a mechanism that allows restricted resources on a web page to be requested from another domain outside the domain from which the first resource was served.

You can read the above link to find out more but essentially its there to protect externals requests coming into your web api that you haven’t authorised, which is good. And the first time you'll experience this is when you get your Angular web working in VS Code, and send your ajax request to your VS2017 web api. Confused by the lack of response, you'll open your Chrome developer console and discover this:

![CORS Error in Chrome](/assets/img/2018-12-27/corserror.png)

### Enabling CORS

The solution is simple, 2 additions in the configuration of your `startup.cs` project file.

![Startup.cs/ConfigureServices](/assets/img/2018-12-27/cors_configureservices.png)

In the `ConfigureServices` function, add the following lines.

![Startup.cs/Configure](/assets/img/2018-12-27/cors_configure.png)

Finally add this line to the `Configure` function. This function is a kind of pipeline so the order is important. CORS is pretty flexible, you can lock down requests to a specific IP address like below; I urge you to do more reading on CORS before going into production.

![Startup.cs/Configure](/assets/img/2018-12-27/cors_alternative.png)

### Security Concerns

That’s it. Rerun your projects and your ajax requests will finally work. Now we need to discuss security, obviously. The above code gives any outsider full access to your WebApi app, which you should be very concerned about. You absolutely do not want to use the above in production without any additional authentication and authorisation technology. And remember, just because your Angular WebApp is hosted on one server, doesn't mean that your WebAPI can just allow that IP address. Angular apps run locally on clients browsers, so web requests will come in from any IP address. [JWT][jwt-url] (Json Web Token) is a brilliant authentication framework for this and I will write a post about implementing this soon. This provides authentication tokens with every request to your api; if you're not authenticated then you're not getting a response. Perfect.


[corswiki-url]: https://en.wikipedia.org/wiki/Cross-origin_resource_sharing

[jwt-url]: https://jwt.io/



