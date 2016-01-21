---
layout: inner
title: 'ERB best practices'
categories: blog embedded ruby rails
tags: html css javascript rails
featured_image: 'https://media.giphy.com/media/12WggcrCyNFoti/giphy.gif'
lead_text: 'Front-end practices for rails 3 projects in the age of rails 5'
---
Working with legacy code can have a lot of [advantages](http://blog.arkency.com/2015/10/advantages-of-working-on-a-legacy-rails-application/) but as a new developer, it can also be really intimidating and confusing. Not only is the complexity level over your head, but at least in my experience, it doesn't follow homogeneous conventions or practices. In the spirit of establishing conventions and encourage coherence, the following are some of the practices that have stuck as I worked on the front-end for labs platform Kipu is soon to launch.

*Rails '3.2.22', Ruby '2.2.3' & bootstrap 3*

 Internalization
------
   Remember one of the most meaningful assets you possess is **information**. Your application offers the users a unique way of showing them information they want to see. Incorporating internalization practices early on the development cycle can save you headaches in the future when you are requested to support pirate english, or when you are requested to rename all 'name' attributes of all your models to 'title' or what not.

   *views/welcome.html.erb*
   {% highlight erb %}
    <%= "#{I18n.t('welcome')}" %>
   {% endhighlight %}


   you can define you're own translations and rails will map these when you render them in the views. By default it will look at translations define in the config/locales/en.yml but you can set your default locale to something else in config/initilizers.locale.rb
   *config/initilizers.locale.rb*
   {% highlight ruby %}
    I18n.default_locale = :pt
   {% endhighlight %}

   *config/locales/en.yml*

   {% highlight yaml %}
   en:
      welcome: 'howdy'
      activerecord:
        attributes:
          attribute_commons: &commons

   {% endhighlight %}

 Rendering Partials
------

 Local variables
------

 Nested loops
------
