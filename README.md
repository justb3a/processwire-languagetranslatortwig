### ProcessWire 

# Template Twig Replace Language Support

Adds twig support for language translator list.

Supports the following modules:

* [TemplateTwigReplace](http://modules.processwire.com/modules/template-engine-twig/)
* [TemplateEngineTwig](http://modules.processwire.com/modules/template-twig-replace/)

## Installation

1. Clone the module and place `TemplateTwigReplaceLanguageSupport` in your site/modules/ directory. 

```
git clone https://github.com/justonestep/processwire-templatetwigreplacelanguagesupport your/path/site/modules/TemplateTwigReplaceLanguageSupport
```

2. Login to ProcessWire admin and click Modules. 
3. Click "Check for new modules".
4. Click "install" next to the new `TemplateTwigReplaceLanguageSupport ` module. 
   This module requires `TemplateTwigReplace` as well as `LanguageTranslatorList` module.
5. That's all!

## Usage

To get your `.twig` files listed as well, you need to wrap the phrases like this:

```html
{{ __('text to translate', 'filepath/filename relative to site/templates/') }}
{{ __('another text to translate', 'home') }}
{{ __('one more text to translate', 'partials/header') }}
```

* first line - general usage
* second line - example for a text in _site/templates/home.twig_
* third line - example tor a text in _site/templates/partials/header.twig_

## Often used translations

You could wrap often used translations in a file called ``_strings.twig`` placed in ``site/templates``. Doing this you can copy this file between various ProcessWire installations und reuse it. Make sure to copy also the corresponding json file and import it.

Calling such a translation in another file is really easy, you don't have to provide a translation domain:

```html
{{ __('Save') }}
```

Now have a look at ``_strings.twig``, in this file you need to have the same entry (one per line) including a translation domain.

Example on how ``_strings.twig`` could look like:

```html
{# Intentionally commented out

{% set s = '_strings' %}

{{ __('Save', s) }}
{{ __('Send', s) }}
{{ __('Email address', s) }}

#}
```

## Enable the Twig Intl Extension

[The Intl Extension](http://twig.sensiolabs.org/doc/extensions/intl.html) provides the **localizeddate**, **localizednumber** and **localizedcurrency** filters.

First of all, you will need the [PHP intl extension](https://secure.php.net/manual/en/book.intl.php), as the Twig extension is built on top of that.

The Twig Intl extension will throw an Exception if the PHP intl extension is not enabled.

Installation instructions can be found in the official PHP documentation. 

Go to module settings (Template Twig Replace Language Support) and activate the checkbox.
