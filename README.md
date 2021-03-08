# Translate Date Plugin

The **Translate Date** Plugin is an extension for [Grav CMS](http://github.com/getgrav/grav). Define date formats for
each language and easily use for dates in your templates via Twig filter `|td`

## Installation

Installing the Translate Date plugin can be done in one of three ways: The GPM (Grav Package Manager) installation
method lets you quickly install the plugin with a simple terminal command, the manual method lets you do so via a zip
file, and the admin method lets you do so via the Admin Plugin.

> **NB:** Currently, only manual installation available. Maybe plugin will be added to GPM in the future, but not yet.

### GPM Installation (Preferred)

To install the plugin via the [GPM](http://learn.getgrav.org/advanced/grav-gpm), through your system's terminal (also
called the command line), navigate to the root of your Grav-installation, and enter:

    bin/gpm install translate-date

This will install the Translate Date plugin into your `/user/plugins`-directory within Grav. Its files can be found
under `/your/site/grav/user/plugins/translate-date`.

### Manual Installation

To install the plugin manually, download the zip-version of this repository and unzip it
under `/your/site/grav/user/plugins`. Then rename the folder to `translate-date`. You can find these files
on [GitHub](https://github.com/karmalakas/grav-plugin-translate-date) or
via [GetGrav.org](http://getgrav.org/downloads/plugins#extras).

You should now have all the plugin files under

    /your/site/grav/user/plugins/translate-date

### Admin Plugin

If you use the Admin Plugin, you can install the plugin directly by browsing the `Plugins`-menu and clicking on
the `Add` button.

## Configuration

Before configuring this plugin, you should copy the `user/plugins/translate-date/translate-date.yaml`
to `user/config/plugins/translate-date.yaml` and only edit that copy.

Here is the default configuration and an explanation of available options:

```yaml
enabled: true
formats:
  en: 'm/d/Y h:mA'
  lt: 'Y-m-d H:i'
```

Note that if you use the Admin Plugin, a file with your configuration named translate-date.yaml will be saved in
the `user/config/plugins/`-folder once the configuration is saved in the Admin.

## Usage

You should add months and weekdays names in your language to your languages file. Eg.:

```yml
en:
  PLUGIN_TRANSLATE_DATE:
    F: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']
    M: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
    l: ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
    D: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
```

If you intend to use only full names (`F` and `l`), you can skip adding translations - these will default to Grav's core
translations.

In Twig template you have several options how to use date translations:
- Leave to config - `{{ page.date|td }}`  
  This will take date format from config and translate months and/or weekdays if found  
  Eg. `Y-m l` will become `2021-03 Tuesday`
- Force language - `{{ page.date|td('lt') }}`  
  Even on EN page `Y-m D` will become `2021-03 Ant`
- Force format - `{{ page.date|td(null, 'Y M l') }}`  
  This will output `2021 Mar Tuesday`
  
You can force both language and format too. Eg. `{{ page.date|td('de', 'Y M l') }}`

## To Do

- [ ] Configure defaults through Admin
