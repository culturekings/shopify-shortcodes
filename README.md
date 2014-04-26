Shortcodes for Shopify
==================

So quickly some information on syntax. We have tried to keep the system consistent with Wordpress so an example tag is

    [youtube width="800" height="500" video="M7lc1UVf-VE"]
    
The first part is the snippet it is going to load and the rest are variables that you can use within the snippet

The above example will load the snippet `shortcode-youtube.liquid` from your snippet folder.

It will then pass the variables `width`, `height` and `video` with the respective values.

These variables are available to the snippet by using

    {% include 'shortcode-render' render:'width' default:'640' %}

For easy reuse you can simply capture the result in to your own variable with

    {% capture youtubeWidth %}{% include 'shortcode-render' render:'width' default:'640' %}{% endcapture %}

The youtube example used is available in the examples directory of this project. If you have created a snippet feel free to create a pull request and we will add it in.


Activating Shortcodes
==================

You must first copy `shortcode.liquid` and `shortcode-render.liquid` in to your snippets.
    
To activate shortcode functionality a change to liquid tags is required where the functionality is required.

    {{ page.content }}
    
Would need to be changed to 

    {% include shortcode load: page.content %}
