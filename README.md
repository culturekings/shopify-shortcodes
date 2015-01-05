Shopify Shortcodes
==================

The purpose of this project is to make advanced html usage available to store owners. This project can simplify galleries, faq, maps, videos and more for the store owner.

 - [Syntax](#syntax)
 - [Accessing variables in snippets](#accessing-variables-in-snippets)
 - [Naming convention](#naming-convention)
 - [Examples](#examples)
 - [Activating shortcodes](#activating-shortcodes)
 - [Shortcode fallback display](#shortcode-fallback-display)
 - [Brackets in content](#brackets-in-content)

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

 - [Youtube Video Embed](examples/youtube)
 - [Flexslider](examples/flexslider)
 - [Font Awesome](examples/fontawesome)

## Activating shortcodes

You must first copy `shortcode.liquid` and `shortcode-render.liquid` in to your snippets.

To activate shortcode functionality a change to liquid tags is required where the functionality is required.

    {{ page.content }}

Would need to be changed to

    {% include 'shortcode' load: page.content %}

## Shortcode fallback display

As shopify data can be sent to external applications and used in places where the shortcode is unable to render an optional syntax is available.

It plays on the fact the display of the data will more than likely be in a HTML page and uses the default HTML comment tag to hide the shortcode in places where it has not been rendered.

    <!--[youtube width="800" height="500" video="M7lc1UVf-VE"]-->

Using this syntax will however hide it from the WYISWYG editor and make editing by store owners more difficult.

## Brackets in content

You may be thinking what happens if I have square brackets in other parts of my content. Not to worry the plugin will only replace square bracket content if it finds an active shortcode. For example

    [ Random Content ]

The above won't be replaced with new content unless a shortcode with the name Random exists. There are rare cases when the word you use is a shortcode and this will need to be fixed manually such as

    [ youtube is a great channel ]

Would need to be replaced by something such as

    ( youtube is a great channel )
