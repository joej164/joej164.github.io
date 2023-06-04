Title: Setting Up My Search
Date: 2023-06-03
Category: Pelican
Tags: Tutorial, Instructions, Search, Pelican

# Overview
Curious if I can get the Pelican Search Plugin working.  I got it working on my demo site, but not sure if the required binary (stork) is installed in the Github Pages Server.

# Articles
- https://docs.getpelican.com/en/latest/plugins.html
- https://github.com/pelican-plugins/search
- https://stork-search.net/docs/install

# Local Dev Environment Setup
This is the process to set up the Pelican Search plugin.

## Local Binary
I started with the Stork Installation Instructions.

For my local dev environment, I installed stork v1.6.0

Since I installed it on Friday in the WSL Ubuntu VM on my box, I didn't need to reinstall it.

One thing not mentioned, is the python library expectes to be able to run `stork` so I had to rename the downloaded binary to just `stork`.

## Python Library
Rather than install `pelican-search` directly, I just added it to the requirements.txt file and reinstalled my requirements in the virtual environment.

## Updating the templates
In article.html and pages.html, I have to wrap the `.content` jinja2 variables with a main html tag.
https://github.com/pelican-plugins/search#stork-html-selector

I did that now, specifically updated the following files:
- theme/notmyidea/templates/article.html
- theme/notmyidea/templates/page.html

## Adding the Javascript Libraries
Some External libraries are needed, as well as a search bar is required.  For this I'm going the "easy" method and using the CDN to host these files.

- https://github.com/pelican-plugins/search#static-assets--option-1-use-cdn

I updated the following files
- theme/notmyidea/templates/base.html

## Adding the Search Input Form
- https://github.com/pelican-plugins/search#search-input-form

I wasn't really sure where to put it, so I just put it in the page.html template.

Likely I'll put it on another page if it actually works on Github Pages.

# Results on my local dev environment
Initially I had issues, finally I stuck it in the `section` tag in the pages.html template.

Good news, it worked, bad news, if I had more than one static page, I'd have a search field on every page.  I'll muck around with that later, if this works when I push to Github Pages.

For now, I'm going to commit all the files and push and see what happens.

# Results in Prod
So it worked.  The `stork` binary must be installed on the Github Pages servers, so the search plugin is working.  I'll maybe create a static search page later, or maybe even a site map with search as there's a plugin for that.


