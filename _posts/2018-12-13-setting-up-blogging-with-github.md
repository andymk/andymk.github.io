---
title: "Setting up blogging with Github Pages"
tags: blogging
author: "Andy Knight"
---
I've been looking around recently for a blogging solution and there's quite a few choices. By far the favourite is Wordpress. However I came across a blog post by [Phil Haack][haacked-post] recently that intrigued me. It uses GitHub pages to serve up static content for a blog. The beauty of it is its fast and lightweight. In combination with the [Jekyll Tool][jekyll-url] I can compile plain text blog posts into neatly formatted html.

### Starting out

Setting up Github Pages is as simple as creating a new repository using your github username:
![Repository Naming](/assets/img/2018-12-13/reponame.png) 
This creates a blank repository. From here you can visit the repository settings page and select a theme. I took the slightly longer route by cloning Phil Haacks blog theme and copying into mine. I've since learned that there's an easier way of doing this. He has good instructions in his [repository][haacked-repo].


### Custom Domains

I have an existing custom domain which I wanted to use for my blog site. You can associate Github Pages with your custom domain but there's a setting up issue mentioned in the document that you need to be aware of.

At the time of writing this blog, I had to set up 4 A records for my own domain using my domain provider.

![A Records](/assets/img/2018-12-13/aname.png) 

Additionally to this, a CNAME record is also required

![CNAME](/assets/img/2018-12-13/cname.png) 



### Linking it all together

DNS propagation can potentially take up to 24 hours. Whilst this is happening there's one more thing to do. In Github visit the settings page for your blog repository. Here you can specify your custom domain name. 

![Custom Domain](/assets/img/2018-12-13/customdomain.png) 

When clicking save, this creates a repository commit with a file called CNAME. If like me you entered this when setting up the repository, you may find issues when using your custom domain to reach your new blog. The solution is to remove this field value and save. Then reenter your custom domain name again and save once more. The actions of this caused everything to link up for me and finally my blog was ready.

### Finally

Its a nice simple setup. I can create blog posts offline easily and simply commit/push to publish them online. Next time I will write in more detail about how this works. 

[haacked-post]: https://haacked.com/archive/2018/12/11/haackbar-theme/
[haacked-repo]: https://github.com/haacked/haackbar
[jekyll-url]: https://jekyllrb.com/