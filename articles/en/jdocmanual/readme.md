<!-- Filename: Readme / Display title: Readme -->

## Jdocmanual

A work in progress started 2024-03-24

This component displays pages prepared in Markdown format in a Manual
layout with an index of pages to the left, the content of a page in
the centre and the contents of the current page to the right.

Version 3 of Jdocmanual is not compatible with previous versions. Any previous
version should be uninstalled before installing this new version.

## Simple installation

Obtain a Jdocmanual ZIP file from [github.com/ceford/cefjdemos-com-jdm](https://github.com/ceford/cefjdemos-com-jdm/archive/refs/heads/main.zip)
and install it in the same way as any other Joomla extension.

Obtain a jdocmanualcli plugin ZIP file from [github.com/cefordj4xdemos-plg-jdocmanualcli](https://github.com/ceford/j4xdemos-plg-jdocmanualcli/archive/refs/heads/main.zip)
and install it. The plugin needs to be enabled! It is used to populate the
databse.

Obtain a data set. This example is for the Help manual. Download a ZIP file
from [github.com/ceford/cefjdemos-data-jdm-help](https://github.com/ceford/cefjdemos-data-jdm-help/archive/refs/heads/main.zip). **This is NOT a Joomla extension!**. Create
a location in your file tree but outside your web tree, for example:
```
/home/username/data/manuals
```
Move the downloaded ZIP file into this folder and unzip it. It will create a
folder named cefjdemos-jdm-help-main. Rename this folder to **help**. Check
that the folder contains two folders named **articles** and **images**.
Remember the path to your manuals folder - it must end in manuals.

In the Joomla Administrator interface, select the Components/Jdocmanual/Sources
menu item. Select the Joomla Help Screens item and change its state to
Enabled. Save and Close.

Select the `Option`s button in the Toolbar. Enter the path to the Markdown source
files, ending in `/manuals/` that you remembered from a previous step. If your
Joomla installation is in a subfolder of your domain enter the subfolder name.
Save and Close.

Open a terminal window and cd into the cli folder within your Joomla
installation root. Issue the following commands in this order to populate 
your database:

```bash
cd /home/username/public_html/optional-path-to-joomla/cli
php joomla.php jdocmanual:action buildarticles help all
php joomla.php jdocmanual:action buildmenus help all
php joomla.php jdocmanual:action buildproxy help all
```

The buildarticles operation will take a long time (several minutes or longer
on slow hosts) and might crash with out of memory or time out errors. The 
buldproxy option is only relevant for the help dataset. It creates a set of
html files that you can use instead of those delivered by the Joola help
proxy server.

Otherwise, select the Jdocmanual/Manual menu to see what you have.

All data sources:

* developer: Information for Joomla developers.<br>
  source: https://github.com/ceford/cefjdemos-data-jdm-developer
* docs: Information for those contributing to Joomla Documentation.<br>
  source: https://github.com/ceford/cefjdemos-data-jdm-docs
* help: The Help screens used for the Administrator pages.<br>
  source: https://github.com/ceford/cefjdemos-data-jdm-help
*  user: Information for Joomla users with limited familiarity with HTML,
CSS and JavaScript.<br>
  source: https://github.com/ceford/cefjdemos-data-jdm-user


## Site Menu

If you want to show the Manuals on the site just create a JDOC Manual
menu item. Note the single page is for search results but it has not
been implemented.

__Important:__ The menu alias must be _jdocmanual_ or internal links
will be broken and lead to frontend problems.

You may wish to place the menu on a page without side modules so that
the full width of the page may be used for content.

## Multilingual Sites

The **System - Language Filter** plugin must have the
**Remove URL Language Code** set to **Yes** or local images will not display
and internal links will be broken.

## User Groups

If you wish to allow others to help maintain content you need to
create two User Groups:

- **JDM Author**: allowed to edit content in English and other languages.
- **JDM Publisher**: allowed to commit and publish updated content.

The **JDM Author** group should have Public as its parent. The **JDM Publisher**
group should have **JDM Author** as its parent.

### Users: Viewing Access Levels

**JDM Author** should be set to the Special Viewing Access level.
From the Users / Access Levels page select `Special` and add `JDM Author` to
the User Groups with Viewing Access.

### Global Options

In the Global Options form select the Permissions tab and then the
**JDM Author** item. Set Administrator login to Allowed.

### Jdocmanual Options

From the JDOC Manual, Manual page select the Options button. In the
Permissions list select **JDM Author** and set the following to Allowed:
- Access Administration Interface
- Create
- Delete
- Edit

Select **JDM Publisher** and set the following to Allowed:
- Publish

Save and Close

If you now login as a user in the **JDM Author** group you will see the
Home Dashboard with some modules not relevant for Jdocmanual.

### Turn off the Help menu item

Go to the list of Administrator modules and find the Administrator
Menu module. In the Module tab set the Help Menu item to Hide.

### Unpublish or restrict Access to modules

In the Administrator modules list find the Logged-in Users item used
in the cpanel position (not the cpanel-users position). Either
Unpublish it or set Access to Super Users.

Find and unpublish the Popular Articles and Recently Added Articles
items for the cpanel position (not the cpanel-content position).

There may be other modules needing similar treatment.

The Home Dashboard should now be empty for a **JDM Author**.

## Who can do what?

**JDM Author** and **JDM Publisher** can login but should only have
access to the the Home Dashboard and the Jdocmanual component.

**JDM Author** does not have access to the Commit button in the
Article Edit page toolbar so cannot update the git repository or
displayed page. Otherwise each can use all other features.

**Manager** and **Administrator** can login but will not see the
Jdocmanual component.

**Author**, **Editor** and **Publisher** do not have access to
the Administrator interface.

**Super Users** have complete access.
