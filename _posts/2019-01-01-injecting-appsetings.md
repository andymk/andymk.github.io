---
layout: post
comments: true
title: "Injecting AppSettings.json into .Net Core Apps "
tags: [netcore]
author: "Andy Knight"
---

Back in the old days, we all used to insert connection strings and appsettings into our web.config file, then write a strongly type class to read in these values using the ConfigurationManager namespace. With .Net Core, things are slightly different, but thankfully strongly typed classes are handled for us. Lets see how.

### Web.config is dead, long live Json

I've never been a fan of xml, I find json so much easier and compact to read. So thankfully, this is the direction that Microsoft has gone. We can still store our important settings, but in .Net Core we use the `appsettings.json` class. In the following example, I'm storing settings for Ravendb client configuration. But you can create anything you want to store and read back.

<script src="https://gist.github.com/andymk/bbbdfd2ba50511904615b456e80fc8a3.js"></script>

Here I've create a new object called RavenDbSettings, which contains 2 fields, one of which is an array.

### Creating our new strongly typed class

Next we need a class with matching properties that will hold our appsettings.

<script src="https://gist.github.com/andymk/ccc8b8f4f31717c46ecab3600ac08585.js"></script>

### Changing the Startup.cs

Finally we need to add a few lines to the `startup.cs` file.

<script src="https://gist.github.com/andymk/d75b4e103f84dc642ea2d192c2655273.js"></script>

The first line retrieves the config section from the `appsettings.json` file.
The second line retrieves a strongly typed instance of the class.
The third line registers that class instance into our IOC container, which can be injected into other services at a later date if we need to. (This actual instance doesn’t really need to be used by other services, it’s just here to demonstrate)

### Conclusion

This setup is working nicely for me and makes managing configuration a little bit easier than before. .Net Core rocks!


