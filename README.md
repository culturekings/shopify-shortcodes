Shortcodes for Shopify
==================

So quickly some information on syntax. I've kept the open and close tags as {{ }} as they are rarely used. Also I've made the seperator to assign variables II as this is also rare. So a shortcode looks like this

    {{gallery||123||medium}}
The first part is the snippet it is going to load and the rest are variables that you can use within the snippet

So now for the functionality. It is all run from the pages.liquid file

    <div id="body">
    {% assign shortcodeBegins = page.content | split: '{{' %}
    {% if shortcodeBegins.size > 1 %}
      {% for shortcodeBegin in shortcodeBegins %}
        {% if forloop.first %}
            {{shortcodeBegin}}
        {% else %}
          {% assign shortcodeEnds = shortcodeBegin | split: '}}' %}
          {% capture shortcodeFull %}{{shortcodeEnds[0]}}{% endcapture %}
          {% assign shortcode = shortcodeFull | split: '||' %}
          {% assign variables = '' %}
          {% for section in shortcode %}
            {% if forloop.first %}
            {% if forloop.last %}
            {% assign variablesFinal = variables | split: '||' %}
            {% include shortcode.first variable: variablesFinal %}
            {% endif %}
            {% else %}
            {% if forloop.last %}
            {% assign variables = variables | append: section %}
            {% assign variablesFinal = variables | split: '||' %}
            {% include shortcode.first variable: variablesFinal %}
            {% else %}
            {% assign variables = variables | append: section | append: '||' %}
            {% endif %}
            {% endif %}
          {% endfor %}
            {{shortcodeEnds[1]}}
        {% endif %}
      {% endfor %}
    {% endif %}
    </div>
    
And your snippet that you make will have the same name conventions as your shortcode so in this case it is gallery.liquid and you can use the variables as the variable array.

    Gallery Included<br>
    {{variable[0]}}<br>
    {{variable[1]}}<br>
    <br>
