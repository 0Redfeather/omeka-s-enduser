# DSpace Connector

DSpace Connector is a [module](index.md) for Omeka S which allows you to connect an Omeka S instance to a DSpace repository to import items from that repository. In addition to importing information, the Omeka S item will include a link back to the original item.

To install DSpace Connector, follow the instructions for [Installing Modules](index.md#installing-modules) on the Modules documentation.

Note that DSpace Connector only works with DSpace versions 5.6 and higher.

You can view past imports by going to the DSpace Connector tab on the left-hand navigation of the admin dashboard and clicking the *Past Imports* sub-tab.

![DSpace Connector navigation option with two sub-tab options for Import and Past Imports](../modules/modulesfiles/dspace_nav.png)

## Import Data
To use DSpace Connector, navigate to the tab labelled *DSpace Connector* on the left-hand navigation of the admin dashboard. 

![Screenshot of the field options for DSpace Connector with collections loaded from a university library](../modules/modulesfiles/dspace_import.png)

To import from a DSpace Repository: 

On the first form, enter the following information: 

* *DSpace site URL* for the Repository - note that you have to enter the entire url, including the `http://` (required);
* *Endpoint* for the api (required. by default this is "rest" but may be changed in the DSpace instance);
* *Limit* or maximum number of results to retrieve at once. 

Then click *Get collections and communities*

If the information above has been correctly entered, you will proceed to the DSpace Connector Import Options page. This has three tabs. 

### Basic Import Settings
This tab has five options:

* *Import files into Omeka S*: click this checkbox to import files in addition to metadata.
* *Item Set*: select an item set from the dropdown into which to import the items, or create a new item set named for the imported Dspace Collection.
* *Sites:* add the imported items to the specified site or sites. Global and user-specific default sites will be preselected here. 
* *Ignored Fields*: DSpace metadata fields to ignore on import, separated by commas. 
* *Comment*: for any comments you have.

![basic import settings, nothing entered and no boxes checked.](../modules/modulesfiles/dspace_importset.png) 

### Collections
This tab will display the list of collections for the DSpace repository, organized by containing community. You can import either one collection at a time or the entire DSpace repository.

To import a single collection, click the Import button to the left of its name. This will automatically begin the import.

![First few collections from mars.gmu.edu's DSpace repository](../modules/modulesfiles/dspace_coll.png)

To import the entire repository, click 'Import entire repository' at the top of the form.

**NOTE:** Importing an entire DSpace repository with a large number of items (>5,000) is likely to flood the DSpace hosting server with requests until failure. Consider importing collection by collection if at all possible. If you still wish to import an entire large repository at once, the following might help:

* On the initial Import Settings menu, set *Limit* to a smaller number such as 50 or 25
* Run the import at night and/or whenever there may be less traffic on your DSpace server
* Consider temporarily inserting a `sleep()` function between the import of each record in `Import.php` to slow the process down slightly (not recommended for production)

You can track the status of the import by navigating to the DSpace Connector > Past Imports tab or on the [Jobs](../admin/jobs.md) tab of the left-hand navigation on the admin dashboard.

- Are your jobs starting and not completing? You might need to [set the path for PHP](../configuration/) so that your system can perform the background process to make the items.

## Review Imports
Go to the DSpace Connector tab on the left-hand navigation of the admin dashboard, click on DSpace Connector and then click on Past Imports, which should appear below the DSpace Connector tab.

This page displays a table of Past DSpace Imports, with a checkbox option to *Undo*, the *Job ID* for the import, the repository’s *Dspace Collection Link*, any *Comments* made during import, the number of *Items* imported, the *Date* of the import, the import *Status*, and the *Owner*, or user who initiated the import.

![Table of past imports showing two from mars.gmu.edu](../modules/modulesfiles/mods_dspacepast.png)

## Update Imported Resources
To update resources created using the DSpace Connector, simply re-run an import from the same source. The resources will be updated, not reimported. This allows you to use the Connector to synch data between your DSpace and Omeka S installations.

## Undo an Import
To undo a completed import and remove all associated items, go to the DSpace Connector tab on the left-hand navigation of the admin dashboard, click on DSpace Connector and then click on Past Imports, which should appear below the DSpace Connector tab.

![Table of past imports showing two from mars.gmu.edu](../modules/modulesfiles/mods_dspacepast.png)

Check the box for each import you wish to undo and click submit.

