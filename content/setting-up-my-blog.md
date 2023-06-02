Title: Setting Up My Blog
Date: 2023-06-02
Category: Pelican
Tags: Tutorial, Instructions, Setup, Pelican

# Overview
This is the steps I took to set up this Blog.

# Read and evaluate options
First I had to research some static website generators.  I wanted to use a Static Site generator as I didn't really want to deal with the overhead and complexity of a database for storing data.

I found the website https://jamstack.org/generators/ and filtered by Python, as I wanted to do this using Python as much as possible.

The top 3 options were MkDocs, Pelican, and Sphinx.  I chose Pelican as it seemed closest to what I wanted to do with the other projects I wanted to develop.

Reasons I didn't choose the other two
- MkDocs - MkDocs was for generating documentation for software.  I didn't really want that
- Sphinx - Sphinx I use at work, it works and would make a nice site, but I wanted to try something different

# Pick a hosting service
For the blog, I picked Github Pages, as it's free, and there's lots of documentation on Pelican's website on how to push code from the repo into pages.  I may use it for the other sites I build, but maybe not.

# Create a Repo
I started with the Github Pages documentation
https://docs.github.com/en/pages/quickstart

I created a repo in my github account called `joej164.github.io`.  I added a README.md file to the repo, did the initial comment, and viola, I had a basic site created.

# Set up the repo
On my dev machine, I cloned the repo.  I then set up the `requirements.txt` file to require the pelican package and tell it to use the markdown package as well.

I then set up a virtual environment in the repo..

`python3 -m venv --upgrade-deps venv`

This set up the virtual environment and also upgraded pip in the virtual environment at the same time.

Then I activated the virtual environment and installed the requirements.
`python3 -m pip install -r requirments.txt`

# Initializing Pelican
Then I started following the Pelican Quickstart Guide
https://docs.getpelican.com/en/latest/quickstart.html

I ran `pelican-quickstart` and below is the list of prompts and responses I gave.

```
(venv) root@DESKTOP-AGIBDOE:~/repos/joej164.github.io# pelican-quickstart 
Welcome to pelican-quickstart v4.8.0.

This script will help you create a new Pelican-based website.

Please answer the following questions so this script can generate the files
needed by Pelican.

    
> Where do you want to create your new web site? [.] 
> What will be the title of this web site? Joe's Blog and Notes
> Who will be the author of this web site? Joseph Jacobs
> What will be the default language of this web site? [en] 
> Do you want to specify a URL prefix? e.g., https://example.com   (Y/n) y
> What is your URL prefix? (see above example; no trailing slash) https://joej164.github.io
> Do you want to enable article pagination? (Y/n) y
> How many articles per page do you want? [10] 
> What is your time zone? [Europe/Rome] foo
Please enter a valid time zone:
 (check [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones])
> What is your time zone? [Europe/Rome] America/Los_Angeles
> Do you want to generate a tasks.py/Makefile to automate generation and publishing? (Y/n) y
> Do you want to upload your website using FTP? (y/N) n
> Do you want to upload your website using SSH? (y/N) n
> Do you want to upload your website using Dropbox? (y/N) n
> Do you want to upload your website using S3? (y/N) n
> Do you want to upload your website using Rackspace Cloud Files? (y/N) n
> Do you want to upload your website using GitHub Pages? (y/N) y
> Is this your personal page (username.github.io)? (y/N) y
Done. Your new project is available at /root/repos/joej164.github.io
```

# Create Content
Next I created a couple of markdown files including this one so I'd have some content.

The URL for Pelican Metadata is as follows
https://docs.getpelican.com/en/latest/content.html#file-metadata

I used the following as the header:

```
Title: Setting Up My Blog
Date: 2023-06-02
Tags: Tutorial, Instructions, Setup, Pelican
```

Since I'm using Markdown instead of restructured text as my content language, I scrolled down a bit and used the Markdown format.

# Customizing the Theme
I wanted to be able to customize the theme.  I knew this from experiments I did yesterday when researching how I was going to do this, so I copied the default theme into a folder in the repo so I could edit it later on.

I ran `pelican --print-settings` to find the default theme.  It was the 'THEME' parameter that was 6 from the top after running the command.

After copying the them from the themes folder to the local folder, I then updated the `pelicanconf.py` and added the line

```
THEME = "theme/notmyidea"
```

# Building the site
I ran the command `pelican` and it built the site.  Since I put the 2 markdown files in the `content` folder, the default for pelican is to look in the content folder, no other command line parameters were needed.

# Previewing the Site
I then ran `pelican --listen` to launch the pelican webserver and see how my site looked.

I navigated to `http://127.0.0.1:8000/`

# Issue with the CSS and Styling
None of the CSS and Styling showed up.  I remembered I had set the site url parameter in the `pelicanconf.py` file.  I blanked that out and reloaded it, the CSS showed up.

Now I need to figure out if theres a way to set the site URL differently when I'm deploying to prod vs deplying locally.  I'll probably see if I need to do that after I figure out how to build and deploy to github pages.

# 