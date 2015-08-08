# Template for multilingual jekyll site

## Intention

I was busy converting a number of sites from joomla! to jekyll. Since some of them were multilingual, I was facing the challenge to implement a handy solution for that with jekyll, so I created this template.

## Architecture

### YAML content
For the transation of content, it is handy to have the texts in several languange together in one file, so cross checks can be done easily. 

I decided to keep the whole content in a yaml file (--> `_data/locales.yml`). For each page in the site, it keeps a record of the form: 

```yaml
index:
    de: 
        title: Zuhause
        main: Das ist die Hauptseite
    en: 
        title: About this page
        main: |
            This template is intended for web developers who face the challenge of a multilanguage site without using a content management system. I wrote this template using the marvellous jekyll site generator. For further information, please refer to the "jekyll homepage":jekyllrb.com. 
````

It starts with a key I call `base-url`. This is the file-name for the corresponding page without the type suffix. So the record shown above is intended for the `index.html`of the rendered site.

The language dependant sections (`de:`, `en:`) refer to the language versions of the page. We'll come back to this later.

The "title" var is used for the page title. This template also displays it in a `h1`tag at the top of the page.

Since I decided to use `textile` as markdown renderer, the "main" branch of the content is included with the "textilize" filter. Therefore, you can use textile markup in the content

### Language control file
Another yaml data file (`_data/languages.yml`) is used to control the multilingual functionality. 

```yaml
---
  - lang: de
    postfix: "-de"
    image: flag-de.jpg
    description: deutsch
  - lang: en
    postfix: ""
    image: flag-en.jpg
    description: English
```

The "postfix" variable is used to access the various languages for one base-url. Note that the language with the emtpy postfix is the default language. 

The two language versions of the index page are though:
* `index.textile` for the english version (which is default)
* `index-de.textile` for the german version

The "image" variable indicates the flag image for the language selector.

### Navigation control file
The file `_data/nav.yaml` controls the navigation of the site.

```yaml
main:
# This is the main navigation tree that appears in the upper nav bar
      # an icon from bootstrap's "glyphicon-" set. Here, it will be expanded to "glyphicon-home"
    - icon: home
      # the url-base is used to construct the file name including the language suffix
      # i.e. this entry stands for the files index.html, index-en.html, index-de.html
      # see _data/languages.yml for the language settings
      url-base: index
      sidebar: sidebar-main
      # this option makes a secondary menu appear on the right. It is possible to declare multiple secondary menu trees. See the "secondary" tree below
      sidemenu: secondary
    - title:
        en: Multilingual
      url-base: multilingual
    - title: # this one has a title in addition to the icon. The title is multilingual
        en: File structure
        de: Dateistruktur
      url-base: file_structure
      subpages: 
        - title:
            en: Main page files
          url-base: main_files
```

The template supports submenus up to one level of nesting. They will appear as dropdown menus in the navigation bar. Besides the "main" branch of the hierarchy, you can add one or more secondary branches that can appear as a secondary navigation menu in the sidebar setting the "sidemenu" option of a page.

The "title" subtree is used for the navigation link. It contains texts in the various languages supported by the page. The language selector will only show buttons for lanugages that are specified in this subtree. Since the actual language is not displayed in the language selector, a page without a title in a foreign language will not have any language selector.

### Skeleton page files

For the rendering of the site, it is important to have one file for each language version of each page. In this template, the following skeleton files are used:

* index-de.textile
* index.textile
* side-1-sub-1-de.textile
* side-1-sub-1.textile
* side-1-sub-2-de.textile
* side-1-sub-2.textile
* side-1.textile
* side-2.textile
* sub-1-de.textile
* sub-1.textile
* sub-2-de.textile
* sub-2.textile