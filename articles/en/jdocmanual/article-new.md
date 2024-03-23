<!-- Filename: Article_New / Display title: Article New -->

## Creating a New Article

The stash for a new article has some differences from that for an existing article. 
The `Display Title` field is not set and some related read only fields are not set
either. They are set when the `Display Title` is changed. Also, the `Heading` field
is not set and you have the option to choose from the list of existing headings 
or you may enter a new heading. The heading must consist of lower case
alphanumeric words separated by dashes. You will also notice that the
`Page ID` is 0 (zero) as the page does not exist.

![New Article Form](./images/manuals/docs/en/jdocmanual/article-new.png)

The `Stash` tab contains an empty edit field as there was no original content 
with which to initialise the content. It is always a good idea to start the new
content with an HTML comment used to populate the database for a new 
installation:

```markdown
<!-- Filename: Article_Edit / Display title: Article Edit -->
```
Before the first save all of the other tabs have empty fields. After saving with 
some Stash content the other tabs, except the Source tab, will be populated with 
new data. 
 
## Committing the New Article

**Notes:** 
- Always save Stash content before selecting `Pull Request`. 
- Stash content must end with a new line.
- Stash text should be broken into lines of 80 characters or less.

When the New Article is committed a new entry will be created for it in the jdm_articles
database table. An entry is made also in articles-index.txt so that the article can be
included when the database is built initially. However, the new entry is appended to
the list of articles rather than the logical place at the end of a list of headings.

The article will disappear from the New Articles list and appear in the Articles list.

## Create a Menu Item

After creating a new article you need to create a new menu item for it. Just follow the procedure
described under menu Items. You will need to use the heading and filename used when
creating the new article.
