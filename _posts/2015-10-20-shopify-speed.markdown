---
layout:     post
title:      "How To Speed Up Your Shopify Store"
subtitle: "because page speed matters"
date:       2015-10-20 12:00:00
author:     "Wolfram Müller"
header-img: "img/speed/header.jpg"
og-img: "img/speed/og.jpg"
---

# How To Speed Up Your Shopify Store

First, let me set the stage:

Day 1, you open up a brand new Shopify store, everything looks new and shiny and the page loads blazingly fast.

You install a new theme and add some products... your store is a tiny bit slower, naturally, but not much, not enough for you to worry about anyway.

You keep customizing your store, adding new products, add a few high resolution images maybe, you install a few apps from the app store and slowly but surely you get the feeling that your store is getting slower...

Sounds fimiliar?

If it does, keep reading... this blog post is about how to improve the speed of your Shopify store.

To research different optimization techniques I set up a test store on Shopify, installed a theme, installed some apps, uploaded some images and added some products.

You can visit the store here: [http://page-speed-test-store.myshopify.com/](http://page-speed-test-store.myshopify.com/)

I then created a second store, completely indintical to the first one: installed the same theme, installed the same apps, uploaded the same images and added the same products.

With the optimization methods I'm about the show you, I was able to

- reduce the page size by **~1.1MB**
- remove **51** unecessary http requests
- make the site load **2,5 seconds faster** on the first visist

You can visit the optimized version of the store here: [http://page-speed-test-store-optimized.myshopify.com/](http://page-speed-test-store-optimized.myshopify.com/)

## Step 1: Measure, Analyze and Understand

To improve your store's page speed, you first have to understand why it is slow.

There are three great tools you can use to analyze your store's page speed:

[Google Pagespeed Insights](https://developers.google.com/speed/pagespeed/insights/)

- You can enter the url of your store and run a speed test for free. It gives you a rating, and actionable advice on what you can do to make your page load faster. It also tells you if your page is optimized for mobile users.

[webpagetest.org](http://www.webpagetest.org/)

- Another great free tool to measure your sites's performance. What I like about webpagetest.org is, it shows you how long it takes to load your site on the first visit (how long it would load for someone who never visited your site before) and for the second visit (how long it would load if someone visited your site before and has assets cached in their browser). It also shows you how many http requests it needs to load your page. (That is something you can optimize, but more on that later)

[pingdom.com](http://tools.pingdom.com/fpt/)

- Another free tool, which gives you a performance score, counts http requests, the load time and your page size.

I tested the store with the three tools I mentioned above, and here is what I got:

**Google Pagespeed Insights**:

<img src="{{ site.baseurl }}/img/speed/slow-googleinsights.png" alt="" class="img-responsive">

**Pingdom**:

<img src="{{ site.baseurl }}/img/speed/slow-pingdom.png" alt="" class="img-responsive">

**Webpagetest**:

<img src="{{ site.baseurl }}/img/speed/slow-webpagetest.png" alt="" class="img-responsive">

***Ouch!!!*** **That's not good...**

### Analyzing the results:

- **2.3 MB page size**
  - Think about the poor mobile users of your site, with slow internet connections and their precious data limit.

- **5.2 seconds until the page is fully loaded**
  - Thats long enough that impatient users already opened a new tab, are surfing facebook and have long forgotten about your store.

- **71 http requests!!!**
  - Holy crap. 71 http requests... Thats just...

Clearly we have some work to do.

## Step 2: Optimize Images

Thats the low hanging fruit. To be fair, I was pretty careless with my images, not thinking about optimization at all. I just uploaded four high resolution images for my store's homepage content slider.

Lets change that.

You can use [tinypng.com](https://tinypng.com/) or [tinyjpg.com](https://tinyjpg.com/) to dramatically reduce the size of your images. (both tools are free)

I uploaded the four product images I had, and this is what I got:

<img src="{{ site.baseurl }}/img/speed/tinypng.png" alt="" class="img-responsive">

Panda just saved me **73%** and **3MB**. Thanks panda!!

### Result:

I deleted all images on my store and replaced them with the optimized versions. Webpagetest.org tells me that it loads the page **0,5s faster**, and has to download **400kb less data** *.

<small>*Why only 400kb, although panda saved me 3MB? Probably because Shopify also does some image optimizations when you upload them.</small>

### Step 2 (b): Reduze the number of high resolution images

I know content sliders are popular. A lot of themes offer them. A lot of store's have them. 

But think about if you really need them. Or at least think about if you can reduze the number of slides you show. Let's be honest, no one really sits there and watches your content slider.

I reduced my slider to only two slides, chopping off another **600kb** and making the site another few hundred milliseconds faster. Totally worth it.

## Step 3: Reduze the number of apps installed

Although a little faster, my site still gets a pretty bad performance grade on Google Pagespeed Insights and Pingdom. I wonder if it's because the site makes **71 http requests?!?**

So why the hell does my store make 71 http requests anyway?

Fortunately both Pingdom and Webpagetest show you exactly what files are downloaded when visiting your site, and how big they are.

Going through the list, I recognize a few file names... It's the javascript and css files for all the apps that I have installed!

*How? Why?*

You see, some apps add functionality to your store's pages, by including a custom javascript file. (think reviews, social media sharing tools, pop ups, referral boxes, newsletter signups etc...)

Thats not a big problem (in fact it's the only way apps can do that), because Shopify loads those javascript files in a non-render-blocking way. Meaning, the browser can already render the page... Meaning, users can already see text, images, your navigation etc, while the javascript files are being downloaded.

What is a problem though: It loads those javascript files even if you don't **use** the app. As long as it is **installed**, it will load the files.

On my test store, I installed 12 apps, and use none of them*. Result: 71 http requests.

<small>* Well, actually I use one: I installed my app <a href="https://apps.shopify.com/presskithero">PresskitHero</a>, so I could shamelessly tell you about it at this point of the tutorial.</small>

So am I really recommending uninstalling apps for improving your store's performance, even though I make a living as a Shopify app developer? Well yes! Not the once you are using of course. But absolutely, please do remove the once you are currently not using.

On my test store I removed all, but four apps that I think are essential, and...

### The results

I removed **40 unnecessary http requests**, reduzed page size by another **300kb** and again made the site a few hundred milliseconds faster.

## Step 4: Choose a fast Theme

Unfortunately, your store's performance is somewhat dependent on which theme you have installed. A theme that is optimized for performance includes all styles in **one** css file, and includes all necessary javascript in **one** javascript file, loaded in a non-blocking way. A theme that is not optimized for performance has multiple css and javascript files, and loads them in a render blocking way.

So before you install a theme I would recommend to run the theme's preview page through Google Pagespeed Insight and see what the tool complains about.

I did that for all themes in the [Shopify theme directory](https://themes.shopify.com) and made a list of 20 themes with the best performance score:

**Theme, Google Pagespeed Insights Score**

- [Kingdom](https://themes.shopify.com//themes/kingdom/styles/king), 81
- [California](https://themes.shopify.com//themes/california/styles/kentia), 81
- [New Standard](https://themes.shopify.com//themes/new-standard/styles/dark), 81
- [Masonry](https://themes.shopify.com//themes/masonry/styles/flamingo), 80
- [Pipeline](https://themes.shopify.com//themes/pipeline-2/styles/play), 80
- [Kickstand](https://themes.shopify.com//themes/kickstand/styles/ebook), 80
- [Showcase](https://themes.shopify.com//themes/showcase/styles/luna), 80
- [Startup](https://themes.shopify.com//themes/startup/styles/art), 80
- [Expression](https://themes.shopify.com//themes/expression/styles/ocean), 80
- [Alchemy](https://themes.shopify.com//themes/alchemy/styles/driftwood), 80
- [Classic](https://themes.shopify.com//themes/classic/styles/sharp), 80
- [Blockshop](https://themes.shopify.com//themes/blockshop/styles/beat), 80
- [Supply](https://themes.shopify.com//themes/supply/styles/dark), 80
- [Symmetry](https://themes.shopify.com//themes/symmetry/styles/beatnik), 80
- [Brooklyn](https://themes.shopify.com//themes/brooklyn/styles/brooklyn), 80
- [District](https://themes.shopify.com//themes/district/styles/energy), 80
- [Vantage](https://themes.shopify.com//themes/vantage/styles/black), 80
- [Solo](https://themes.shopify.com//themes/solo/styles/solo), 80
- [Parallax](https://themes.shopify.com//themes/parallax/styles/los-angeles), 79
- [Editions](https://themes.shopify.com//themes/editions/styles/light), 79

## Step 5: Optimize your javascript and css files

OK. Now comes the hard part. If you already have a theme installed, and you don't want to install another one, but still want to improve your store's performance, you have to manually optimize your assets.

Here is how:

### Merge all stylesheets into one single file

In your theme's asset folder, create a new file called *application.scss.liquid*

Then copy and paste the content from all stylesheets into the newly created file.

In your theme's main layout (*theme.liquid*), remove all the old stylesheet link tags, and add your new main file:

{% highlight liquid %}
{% raw %}{{ 'application.scss.css' | asset_url | stylesheet_tag }}{% endraw %}
{% endhighlight %}

### Merge all javascript files into one single file

In your theme's asset folder, create a new file called *application.js.liquid*

Then copy and paste the content from all javascript files into the newly created file.

In your theme's main layout (*theme.liquid*), remove all javascript link tags, and add your new main file at the very bottom, right before the closing *</body>* tag:

{% highlight html %}
  ...
  <script src="{{ 'application.js' | asset_url }}" async defer></script>
</body>
{% endhighlight %}

**A word of caution!!!**: Some javascript files depent on others to load first. So copy and paste them in the order they were included in your theme. Make a backup of your theme first, so if things break after merging all files into one you can revert to the old version.

## Final Results:

### Before:

Pingdom:

<img src="{{ site.baseurl }}/img/speed/slow-pingdom.png" alt="" class="img-responsive">

Webpagetest

<img src="{{ site.baseurl }}/img/speed/slow-webpagetest.png" alt="" class="img-responsive">

### After:

Pingdom:

<img src="{{ site.baseurl }}/img/speed/fast-pingdom.png" alt="" class="img-responsive">

Webpagetest

<img src="{{ site.baseurl }}/img/speed/fast-webpagetest.png" alt="" class="img-responsive">

With all the optimizations I was able to 

- reduce the page size by **~1.1MB**
- remove **51** unecessary http requests
- make the site load **2,5 seconds faster** on the first visist

If you have any question, don't hesitate to write me at <a href="mailto:hello@presskithero.com">hello@presskithero.com</a>

If you like this post, feel free to share it on <a href="https://twitter.com/intent/tweet?text=How%20To%20Speed%20Up%20Your%20Shopify%20Store&tw_p=tweetbutton&url=http://blog.presskithero.com/2015/10/20/shopify-speed/&via=presskithero">twitter</a> or <a href="http://www.facebook.com/sharer/sharer.php?u=http://blog.presskithero.com/2015/10/20/shopify-speed/">Facebook</a>

If you are interested in creating a professional press kit for your Shopify store, check out my app <a href="https://apps.shopify.com/presskithero">PresskitHero</a>

<script src="//load.sumome.com/" data-sumo-site-id="ec872333eecf0b402630b94fff19e40ee21f92463f1f9f5b223102f1797ad689" async="async"></script>

