Flexslider Shortcode for Shopify
==================

This shortcode allows the easy use the Flexslider plugin with shopify.

## Usage

Make sure to install the [Shortcode for Shopify](https://github.com/ryanheart/shopify-shortcodes/) plugin.

Add the required files to the `<head>` of your layout file if your theme doesn't already support flexslider.

    <!-- Place somewhere in the <head> of your document -->
    <link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/flexslider/2.2.2/flexslider.css" type="text/css">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js"></script>
    <script src="//cdnjs.cloudflare.com/ajax/libs/flexslider/2.2.2/jquery.flexslider.js"></script>

Initialise the slider by including after the code above if your theme doesn't already support flexslider.

    <!-- Place in the <head>, after the three links -->
    <script type="text/javascript" charset="utf-8">
      $(window).load(function() {
        $('.flexslider').flexslider();
      });
    </script>

You can then use the following shortcode where needed.

    [flexslider action="new slider"]
    [flexslider action="new slide"]
    <img src="http://placehold.it/966x190/333333/FFFFFF&amp;text=Slide+1" />
    [flexslider action="end slide"]
    [flexslider action="new slide"]
    <img src="http://placehold.it/966x190/666666/FFFFFF&amp;text=Slide+2" />
    [flexslider action="end slide"]
    [flexslider action="new slide"]
    <img src="http://placehold.it/966x190/999999/FFFFFF&amp;text=Slide+3" />
    [flexslider action="end slide"]
    [flexslider action="end slider"]

## Available variables

| Variable  | Default  | Description |
| --------- | -------- | ----------- |
| action     | required | This controls what the shortcode will output. `new slider` starts a new slider. `end slider` ends the slider. `new slide` starts a new slide. `end slide` ends the slide  |