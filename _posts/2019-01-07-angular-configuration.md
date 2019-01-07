---
layout: post
comments: true
title: "Using global variables in Angular "
tags: [angular]
author: "Andy Knight"
---

### Intro

This is just a quick tip post about using configuration in your Angular app. The framework has already provided a simple and easy approach to this, so lets try it out.

### Environments

Angular projects come with 2 default environment files which I find are the perfect place to insert configuration values. They can be found in the `environments` folder, one for development and one for production. The `angular.json` takes care of swapping these files around depending on your build intention.

By default, the `environment.ts` file looks something like this:

{% highlight powershell %}
export const environment = {
  production: false
};
{% endhighlight %}

We can add additional variables to this object, such as:

{% highlight powershell %}
export const environment = {
  production: false,
  endpointUrl: "http://127.0.0.1:4300/"
};
{% endhighlight %}

### Accessing our values

Now that we have set up our configuration we can easily access them by simply importing the environments object:

{% highlight powershell %}
import { environment } from './../../environments/environment';

// access our url
let url = environment.endpointUrl;

{% endhighlight %}

### Conclusion

This environment object is available anywhere in Angular, so avoid hardcoding values and make use of reusability! Oh and don't forget to modify the `environment.prod.ts` file for production settings.