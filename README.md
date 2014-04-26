Shortcodes for Shopify
==================

The purpose of this project is to make advanced html usage available to store owners. This project can simplify galleries, faq, maps, videos and more for the store owner.

 - [Syntax](#syntax)
 - [Accessing variables in snippets](#accessing-variables-in-snippets)
 - [Naming convention](#naming-convention)
 - [Examples](#examples)
 - [Activating shortcodes](#activating-shortcodes)

## Syntax

So quickly some information on syntax. We have tried to keep the system consistent with Wordpress so an example tag is

    [youtube width="800" height="500" video="M7lc1UVf-VE"]
    
The first part is the snippet it is going to load and the rest are variables that you can use within the snippet

The above example will load the snippet `shortcode-youtube.liquid` from your snippet folder.

It will then pass the variables `width`, `height` and `video` with the respective values.

## Accessing variables in snippets

These variables are available to the snippet by using

    {% include 'shortcode-render' render:'width' default:'640' %}

For easy reuse you can simply capture the result in to your own variable with

    {% capture youtubeWidth %}{% include 'shortcode-render' render:'width' default:'640' %}{% endcapture %}

## Naming convention

All shortcodes are prefixed in the file system with `shortcode-` so make sure that if you want a shortcode of `youtube` you create a `shortcode-youtube.liquid` file.

The purpose of this is to allow store owners to easily find all active shortcodes within a store and avoid collisions with other snippets.

## Examples

The youtube example used is available in the examples directory of this project. If you have created a shortcode you would like to share feel free to create a pull request and we will add it in.

## Activating shortcodes

You must first copy `shortcode.liquid` and `shortcode-render.liquid` in to your snippets.
    
To activate shortcode functionality a change to liquid tags is required where the functionality is required.

    {{ page.content }}
    
Would need to be changed to 

    {% include shortcode load: page.content %}
