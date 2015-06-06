#Introduction
A learning experiment for theming Drupal 8.

Sinatra is intended to be used as a parent theme, for themes that want to drop most of the Drupalness (whatever remains), and get away from the override everything in a template approach. **This play theme will become a lot more mature in the coming weeks** I also want to experiment with includes (especially dynamic) and embeds in Twig. It should be possible to approach Drupal themes in ways not yet seen via Twig and possibly adapt to Workflows already in use for your other Twig based (or Twig like projects). 

Note: I am using this as a base theme for [Bootrun](https://github.com/chris-hall-hu/bootrun) already which is already being used on my [Running on Drupal 8 blog](http://running-on-drupal8.co.uk).

For now it is play, and possilby something useful to look at for those doing something related. Depending
how Drupal finishes up it may become something more solid.

## Provide a little useful CSS
Sinatra includes a little Drupal specific CSS to accommodate styles used in CK editor and the admin toolbar etc. 

## Provide a richer Twig Block extension experience
As of Beta 9 (and maybe later or for good) Drupal only uses twig blocks (allowing a neat way to extend templates)
in the Block templates (perhaps because of the name ;)). This theme will progressively replace many of the default
core Drupal templates with equivilents containing a rich mix of twig blocks.

For example the version of block.html.twig in this theme is a follows (just the code not the comments):

```
{% block block_full %}
<div{{ attributes }}>
  {% block full_title %}
  {{ title_prefix }}
    {% block label %}
      {% if label %}
        <h2{{ title_attributes }}>{{ label }}</h2>
      {% endif %}
    {% endblock label %}
    {{ title_suffix }}
  {% endblock full_title %}
  {% block content %}
    {{ content }}
  {% endblock content %}
</div>
{% endblock block_full %}
```
Which allows any theme using Sinatra as base theme to change the label (currently you can override the content only) for blocks as follows:

```
{% extends "@sinatra/block.html.twig" %}

{% block label %}
  {% if label %}
    <h3{{ title_attributes }}>{{ label }}</h3>
  {% endif %}
{% endblock %}
```




