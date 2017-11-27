---
layout: post
title:  Logistics behind writing my data science posts
date:   2017-11-27 13:32:20 +0300
description: This post describes the steps required behind uploading jupyter notebook to my blog. # Add post description (optional)
img: post-1.jpg # Add image post (optional)
tags: [Blog]
author: Pawel Marciniak # Add name author (optional)
---
Just a few words about what's required to convert jupyter notebook into the blog entry on my platform (jekyll templates hosted on github).

0. Play with data and create a jupyter notebook (using Anaconda Jupyter).


1. Once the notebook is created, go to bash / terminal / powershell and use the nbconvert tool to convert your jupyter notebook into something which can be uploaded as a post content to our website / blog. This is a command that you need to use:

```shell
$ jupyter nbconvert --to html --template basic notebook.ipynb
```
\* Note that if you don't have the `nbconvert` utility installed on your machine you need to install it first. See more information about this tool [here][nbconvert].

\* Also note that I experimented with number of output formats from the `nbconvert` utility, and for the jekyll templates I use, the `html basic` output works best.


2. Once you converted your jupyter notebook to html basic format, you need to remove the `??? heading` indicators as they are not comming across very well. After you are done, save the file in the `_include` folder in your github blog repository.


3. After that create a new generic post in the `_post` directory in your github blog repository, using the generic post template of your theme. After the front matter in your post, include the following piece of code, referencing your post to the respective html file in the `_include` directory (which was converted from your jupyter notebook):

{% raw %}
{% include notebook.html %}
{% endraw %}


Voila! You can save everything now and push the changes to your github blog repository. In a few moments your updated site should be published.

[nbconvert]: http://nbconvert.readthedocs.io/en/latest/usage.html#convert-html
