# cefjdemos-data-jdm-docs

## Joomla Documentation pages in markdown format

This is currently a work in progress.

These are documents about how to compose Joomla documentation.

## File Structure

There are two file trees, one for the markdown files and another for local images.

```bash
manual
    articles
        language
            heading
                xxx-yyy-zzz.md
    images
        language
            heading
                xxx-yyy-zzz-screenshot.png
```
Example for the help repository:
```bash
help
    articles
        en
            admin-modules
                admin-modules-actionlogs-latest.md
    images
        en
            admin-modules
                modules-actionlogs-latest-screenshot.png
```

## Image links

In an md file any reference to a local image should have a link of the form:
```bash
![alt text](../../../images/manual/language/heading/xxx-yyy-zzz-screenshot.png) "Optional Title"
```
This allows you to see the image in a local preview. When built for a delivery system a set of responsive image may be created and the img data turned into a picture tag.

Most of the links to images are img tags using images from the docs.joomla.org site.

