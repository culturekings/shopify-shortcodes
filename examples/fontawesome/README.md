Font Awesome Shortcode for Shopify
==================

This shortcode allows Store owners to use Icons easily within their content. Can be easily modified to suit any Icon font.

## Usage

Make sure to install the [Shortcode for Shopify](https://github.com/ryanheart/shopify-shortcodes/) plugin.

Add the required files to the `<head>` of your layout file if your theme doesn't already support Font Awesome.

    <!-- Place somewhere in the <head> of your document -->
    <link href="//maxcdn.bootstrapcdn.com/font-awesome/4.2.0/css/font-awesome.min.css" rel="stylesheet">

You can then use the following shortcode.

[icon heart]

## Available icons

You can view all available icons on the [Font Awesome](http://fortawesome.github.io/Font-Awesome/icons/) website.

Icons have been modified to not require the fa- prefix. Example syntax is below

| Font Awesome Code  | Shortcode
| --------- | --------
| fa-heart    | [icon heart]
| fa-plane   | [icon plane]  
| fa-facebook    | [icon facebook]  

## Additional Settings


| Setting  | Description | Example
| --------- | --------
| url   | Link the icon to a URL  | [icon heart url="/collection/all"]
| size   | Resize icon : lg, 1x, 2x, 3x, 4x | [icon plane size="4x"]  
| spin    | Set icon to spin | [icon facebook spin="true"]  
| class    | Add additional classes | [icon facebook class="fa-fw"]
