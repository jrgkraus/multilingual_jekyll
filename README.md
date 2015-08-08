# Template for multilingual jekyll site

## Intention

I was busy converting a number of sites from joomla! to jekyll. Since some of them were multilingual, I was facing the challenge to implement a handy solution for that with jekyll, so I created this template.

## Architecture

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


