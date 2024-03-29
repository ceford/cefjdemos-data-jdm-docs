<!-- Filename: Source_Data / Display title: Source Data -->

## Local Storage Structure

The article data used by Jdocmanual are stored in four git repositories in
GitHub Flavoured Markdown format (GFM). Ancillary data used for importing the
data into Jdocmanual are stored in txt or ini files. Your downloaded and
unzipped data files should be organised as follows::

```
/manuals
    /developer
    /documenter
    /help
    /user
        /articles
            /de
            /en
                /articles
                /articles-metadata
                ...
                /users
                /workflows
                menu-headings.ini
            ...
            /ru
            articles-index.txt
            menu-index.txt
        /images
            /en
                /hosting
                    /hosting-apache-default-page.png
```
The images folders are created as required for local images. The image names
should start with the folder they are in.

## Reason for Structure

This structure allows a local image in English (en), typically a screenshot,
to be shared by all translations. However, if a translation wishes to use a
screenshot in its language it is a simple matter to place a new screenshot
in the appropriate language folder and then change the language code part of
the image path, for example `en` to `de` for the German translation.

## Image Sizes

Images should be reduced to a standard resolution of 1 image pixel per screen
pixel for a 1x resolution display, and to 1200 pixels wide if originally wider
than that. For example, high resolution screens may use 1.5 or 2.0 screen
pixels per image pixel. If you take a screen shot using a nominally 1440 pixel
wide screen that has 2x resolution the captured image will be 2880 pixels
wide. That is much larger than it needs to be, in pixels and storage bytes,
and will impact site performance and storage requirements.

## Local Location of Sources

Each of the developer, documenter, help and user folders is a separate
repository. The manuals folder must be somewhere in your file space but not in
your web tree. For example `/home/username/data/manuals`.

The data originally came from the Joomla Documentation MediaWiki site. The
conversion process was rather tortuous and not so easily repeated! An important
feature of the conversion is that many of the links to article images, mostly
Joomla screenshots, have been retained in the article files. So Jdocmanual is
using images delivered from docs.joomla.org. In due course that may change.

## Data Management

This is a complex problem! You may have set up Jdocmanual on a personal
development server using localhost. Or you may be using a shared hosting
server with no command line access or a VPS with full server access. Also,
you may or may not be familiar with `git` and working with others to
maintain a git repository.

Jdocmanual has an internal editing system that allows you to modify your
sources, perhaps with the help of others. However, that may put you out of
sync with the GitHub repo. For the moment let us assume you just want to
obtain the original source data and update your local copy from time to
time. The original sources on GitHub are in the following repositories:

- https://github.com/ceford/cefjdemos-data-jdm-developer
- https://github.com/ceford/cefjdemos-data-jdm-docs
- https://github.com/ceford/cefjdemos-data-jdm-help
- https://github.com/ceford/cefjdemos-data-jdm-user

### Clone with git

If you can install git on your computer, do so. It is free, fast and useful.
If not, go on to the next Download ZIP section. If you visit any of
the data sources listed above you will see a green button labelled `Code`.
From the dropdown list select the `Clone using the web URL.` copy symbol.

In a terminal window, change to your manuals folder and use the git clone
command, for example:
```bash
cd /home/username/data/manuals
git clone https://github.com/ceford/cefjdemos-data-jdm-docs.git
```
That will create a folder named `cefjdemos-data-jdm-docs`. You need to rename
that folder to its short name, `docs`. To update your local repo at any time
in the future you can change into that folder and issue a git command:
```bash
cd /home/username/data/manuals/docs
git pull
```
Then build your articles and menus again.

If you are going to make local changes to the manual content you will
probably need to checkout a new branch, or fork the source repository and
clone that. Too complicated to cover here!

### Download ZIP

If you don't have git, quite likely on shared hosting, you can download a
ZIP file from that green button on GitHub. Save the ZIP in your `manuals`
foler and unzip it there. It will have a long filename, such as
`cefjdemos-data-jdm-docs` that you need to rename to its short form, `docs`.
Then delete the ZIP file. You can download a new ZIP file from time to time
and unpack it in the same way to keep your data up to data with the original
repository. Then build your articles and menus again.

**Warning:** If you make changes with the Jdocmanual editor tools they will
be overwritten by the new download.

## Using the CLI

Jdocmanual has a command line interface to allow automation of update tasks.
For example, to update the user Manual you could issues the following commands:
```bash
cd /home/username/data/manuals/user
git pull
cd /path/to/joomla/root/cli
php joomla.php jdocmanual:action buildarticles user all
php joomla.php jdocmanual:action buildmenus user all
```
You could call these commands from a shell script and use a cron job to update
your site, perhaps once a week or once a day. If using shell script you need
to use the full path to the php executable because the command line version
of php may differ from that used by your web server.
