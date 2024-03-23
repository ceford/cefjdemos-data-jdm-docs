<!-- Filename: Source_Data / Display title: Source Data -->

## The Source Data

The article data used by Jdocmanual are stored in a git repository in GitHub 
Flavoured Markdown format (GFM). They could be on GitHub but don't have to be. 
It could even be a disadvantage to use GitHub. Ancillary data used for 
importing the data into Jdocmanual are stored in txt or ini files. The 
repository structure is as follows:

```
/manuals
    /developer
    /documenter
    /help
    /user
        /de
            /articles
            /banners
            ...
            menu-headings.ini
        /en
        /es
        ...
        articles-index.txt
        menu-index.txt
```

The data originally came from the Joomla Documentation MediaWiki site. The 
conversion process was rather tortuous and not so easily repeated! An important 
feature of the conversion is that the links to article images, mostly Joomla 
screenshots, have been retained in the article files. So Jdocmanual is using 
images delivered by MediaWiki. In due course that may change. The data are on 
GitHub:

https://github.com/ceford/j4xdemos-data-jdocmanual

## Data Management

This is a complex problem! You may have set up Jdocmanual on a personal 
development server using localhost. Or you may be using a shared hosting
server with no command line access or a VPS with full server access. Also,
you may or may not be familiar with `git` and working with others to 
maintain a data repository.

Jdocmanual has been designed as a single repository component - users may
update their local repository but are not expected to contribute back to the
GitHub source, although that can be arranged. 

If you do have a team to work with you can set up two groups:

- **Article Author:** may propose changes to the documentation.
- **Article Publisher:** may commit changes to the local repository.

Authors work with their own personal copies of articles or menus stored in 
`stash` tables. Publishers do not see stashes until a `Pull Request` is made.
Data management is still a work in progress!
