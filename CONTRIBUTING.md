# Contributing to the Swansea University Tree Society website  

Thank you for showing interest in contributing to this project. We are open to PRs and issues and welcome any feedback or improvements that could be made.
In this document, we will cover guidelines for contributing to the website, as well as some common FAQs and troubleshooting.

## Contents  

1. [Setup guide](#setup)
2. [Project overview](#overview)
3. [Contributing](#contributing)
    - [Issues](#issues)
    - [Pull requests](#prs)
4. [Common issues](#common-issues)

## Setup guide {#setup}  

To set up the website, you will require the [Jekyll](https://jekyllrb.com) static site generator, as well as Ruby 2.5.0 (or higher), RubyGems,  gcc and make. Read the [quickstart documentation](https://jekyllrb.com/docs/) for help with this. **It is highly recommended that you set up Jekyll on a Linux environment** (WSL or a VM works too). Once Jekyll is set up, clone the website repo somewhere convenient, open the directory in your command line and run `bundle install` to install the required dependencies. Give it a little while to install the dependencies, then (if successful) you can run `bundle exec jekyll serve` to serve the site on your localhost. Adding the flag `--livereload` means that the site is rebuilt every time a saved change is detected, useful for testing. You are now ready to contribute to the website!

## Project overview {#overview}  

The Swansea University Tree Society is a static website that uses Jekyll. It uses the [Angency Jekyll](https://github.com/raviriley/agency-jekyll-theme) remote theme with a few custom HTML components. Bootstrap is used for the page layout and styling, and is strongly encouraged where appropriate to use when editing HTML components.  

Most if not all of the site content is modifiable from the `sitetext.yml` file located in the `_data` directory, and each section of the site has its own section in this YAML file. The data for the tree planting modals is contained in markdown files in the `_portfolio` directory. A new link is added to the page when a new file is added - you may need to alter the Bootstrap for this section to fix the alignment where necessary.  

The `_includes` directory contains the HTML components used to build the page. As well as HTML and Bootstrap, the [Liquid](https://jekyllrb.com/docs/liquid/) templating language is used to add data from the YAML files to the site automatically. Liquid utilises some basic Ruby syntax, and the site does not currenlty use anything more complex than basic conditionals and referencing of variables.  

Since the Jekyll theme used is a remote theme, components which are unchanged from the original theme are not included in this repository. Instead, they are fetched from a remote version of the theme included in the bundled dependencies.

Have a look at the repo for some examples, or feel free to contact us on GitHub to ask a quesion!

## Contributing {#contributing}  

Templates are included for submitting issues and PRs. The option to use these will come up when creating one.

### Issues {#issues}  

We are open to hearing about any technical issues that appear with the site. For other general, non-technical queries, please contact [SU Tree Society](https://www.swansea-union.co.uk/activities/society/26348/) directly.  

Please bear in mind that suggestions and changes to the site content would have to be agreed upon by the committee of Tree Society as they are the ones being represented.

### Pull requests {#prs}  

Before making a pull request (or any changes in fact), make sure you are **working on a new branch!** The main branch is protected, so you will not be able to commit
and push directly to the main branch.  

When making a PR, use the template for guidance, though you are free to adapt it where appropriate. Merges are blocked by default and must be approved by one other contributor who is a maintainer or higher.  

## Common issues {#common-issues}  

### "My webpage changes aren't being reflected"   

- Check that you have served the site using the `--livereload` flag.
- Restart the server and launch it again - note that the `_config.yml` file and newly created HTML components require a restart of the server.
- Due to the design of the original Agency theme, the HTML components are divided into two sections in order to provide support for multiple languages. A check to see that the locale is set means that the HTML in each file is duplicated in order to avoid build errors if one isn't set.  

An example of this is as follows:
```
{% if site.locale and site.locale != "" and site.locale != nil %}
<div class="large text-muted">{{ site.data.sitetext[site.locale].about.body | markdownify }}</div>
{% else %}
<div class="large text-muted">{{ site.data.sitetext.about.body | markdownify }}</div>
{% endif %}
```  

We understand that this is frustrating, however a large refactor would be required to remove the duplication. If you feel up to the task of improving this, we welcome you to have a go!  

### `bundle install` is failing  

Check that you have installed ruby, rubygems, gcc and make correctly and updated them. You can find more troubleshooting for Jekyll build issues [here](https://jekyllrb.com/docs/troubleshooting/#configuration-problems)

### Other issues  

For any other issues or questions, please do not hesitate to get in touch. We will try our best to help so that you can contribute to this project.  
