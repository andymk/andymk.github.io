---
layout: post
comments: true
title: "Using ViewChild to focus on an element "
tags: [angular]
author: "Andy Knight"
---

The ViewChild function in Angular has many uses, but commonly used to access child elements or directives. Accessing an element allows us to make use of its native html and manipulate it. 

### Environments

Imagine we have an input element in our component that we want to access upon startup. We might have simple html like this:

{% highlight html %}
<input type="text" [(ngModel)]="anInputField"/>
{% endhighlight %}

In order to access this, we can first give it a template reference variable:

{% highlight html %}
<input type="text" #myInputField [(ngModel)]="anInputField"/>
{% endhighlight %}

In out component class we can now refer to this:

{% highlight java %}
@ViewChild('myInputField') myInputRef: ElementRef;
{% endhighlight %}

Remember that because of component lifecycle, the view is not rendered until after constructor() and ngOnInit() so in order to use this new object we must implement AfterViewInit, like this:

{% highlight java %}
export class MyComponent implements OnInit, AfterViewInit {
  ngAfterViewInit(): void {
    if (this.myInputRef.nativeElement) {
      this.myInputRef.nativeElement.focus();
    }
  }
}
{% endhighlight %}

Notice I've included a condition to test for the nativeElement object, this is to protect against serverside rendering and crawlers.

### When to use ViewChild

There are two ways we can design forms in Angular. We can use Template Forms or Reactive Forms. With Reactive Forms, we build up our form inputs in our component class so we already have a way of referencing our elements. However, in Template Forms we define our inputs using HTML and therefore have no way of accessing these objects. This is when ViewChild becomes of great use:

{% highlight java %}
this.myInputRef.valueChanges.subscribe(() => doSomeAction);
{% endhighlight %}