---
layout: post
title: Start a Feature-Rich Jekyll Blog on Github Pages Easily
tags: Jekyll
---

For the past week I had some fun setting up my blog using Github pages. I tried multiple tutorials that claim to help you set up in “minutes”. Unfortunately, almost all of them suffer from minor issues, such as CSS styling is missing on certain pages or simply being incompatible with the latest stable release of Jekyll. I ended up doing the following:

## Forked jekyll-now

Fork https://github.com/barryclark/jekyll-now and rename the resulting repository as `<userName>.github.io`. You should have a basic blog up and running immediately after doing so.

## Enable Tags

To enable the tagging mechanisms so that you can easily group your posts based on arbitrary categories, I followed the step-by-step tutorials on http://longqian.me/2017/02/09/github-jekyll-tag/. There are a few minor issues that I fixed in my Github Page repository. Here's the list:

### Empty Tag List

In “4. Display the Tags of a Post”, the approach suggested will display an empty list (i.e. [ ]) even if the post has no tag attached to it. Just add an `if` clause at the beginning to fix it:

```
{% if page.tags.size > 0 %}
<span >[ {% for tag in page.tags %} {% capture tag_name %}{{ tag }}{% endcapture %}
<a class="postTag" href="/tag/{{ tag_name }}">
    {{ tag_name }}&nbsp;</a>
{% endfor %} ]
</span>
{% endif %}
```

### Non-Standradized Tag

Throughout the post, there are 2 code snippets that use the non-standardized `<nobr>` tag. So I simply removed them.

## Optional: Comment Section

Head over to Disqus and apply for a Disqus “shortname” (not your user name). Then make a [one-line change](https://github.com/hencrice/hencrice.github.io/blob/master/_config.yml#L37) like I did.

## Optional: Google Analytics

Visit Google Analytics and get a tracking code and drop it in like [this](https://github.com/hencrice/hencrice.github.io/blob/master/_config.yml#L40). This is helpful if you want to know where your visitors are from or if you just want to see some cool real-time dashboards!

## References

1. https://github.com/barryclark/jekyll-now
2. http://longqian.me/2017/02/09/github-jekyll-tag/