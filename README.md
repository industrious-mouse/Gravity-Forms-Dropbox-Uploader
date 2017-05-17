# Gravity Forms Dropbox Uploader #

## 2.0 Updates (May 2017) ##

Partial codebase update   
Integrate with Dropbox API v2.0, as v1.0 is deprecated and EOL June 2017.

## 1.1 Updates (July 2015) ##

Original Development by [Blue Liquid Designs](http://www.blueliquiddesigns.com.au).  
Partial re-write July 2015 by [Industrious](http://industrious.agency).

## Support ##

The plugin is no longer under active development.
  
The repository/plugin will not be maintained by Industrious, we've just added the updates to help anyone out with some issues listed in the changelog below.

* * *

## Description ##
The Gravity Forms Dropbox Uploader is a simple, intuitive plugin that integrates seamlessly into Gravity Forms and allows you to store Gravity Form uploads in your Dropbox account.

## Features ##
*    Gravity Form Uploads are saved to your authenticated Dropbox account
*    Intuitive user interface allows you to select what fields will upload to Dropbox
*    Quick set up time - you're uploading in a couple of minutes
*    Option to delete files automatically from server after uploading to Dropbox

## Tutorial ##
[Head to Blue Liquid Designs](http://www.blueliquiddesigns.com.au/index.php/gravity-forms-dropbox-uploader/) - the developer of the extended Gravity Forms Dropbox Uploader plugin - and view everything you need to know about installing, configuring and using the plugin.

## Haven't purchased Gravity Forms yet? ##
Head over to [Gravity Forms' official website](https://www.e-junkie.com/ecom/gb.php?cl#54585&c#ib&aff#235154) and purchase a copy.

## Installation ##

1. Install and activate plugin on WordPress
2. Go to the Gravity Forms Settings section in the admin area and then navigate to the Dropbox settings page.
3. Open a new browser window and head to https://www.dropbox.com/developers/apps. You may need to login to your Dropbox account first.
4. Create a new App and select the 'Core' application type. Leave the permission type set to App Folder.
5. Copy the App Key and App Secret into your GF Dropbox Settings.
6. Once updated, you'll be asked to authenticate your account. Click Authenticate Account and follow the prompts.
7. Go to the Gravity Forms' Edit page, add an upload box and check the Upload file to your Dropbox account Checkbox under the File Upload's Properties tab. Save the form.
8. When you submit the live form the file will be automatically placed in your Dropbox folder.

## Frequently Asked Questions ##

**Is the plugin still supported?**
Unfortunately no. Due to time constraints and changes in the Dropbox API - the core API integration system used in the plugin needs to be upgraded - we are no longer supporting this plugin. If you would like to take over this project please contact us on enquire@blueliquiddesigns.com.au.

**Does the uploaded file get deleted off my server once it has been uploaded to Dropbox?**
Yes. As of version 1.0.8 you now have the option to delete files off the server once they have been uploaded to Dropbox.

**How do you save the files in it's own directory in wordpress?**
As of version 1.0.4 you can use macros in the file path. Macros include #username#, #date#, #time# and #uniqueid#. Go to the Dropbox settings page and enter a path like the following in the *Dropbox Upload Directory* field.  

Hook/Filter Example — Allows custom folder outside of the current macros listed above:
 
	add_filter('gform_dropbox_replace_path', function($path, $id){
	
	   $entry = \GFAPI::get_entry($id);
	
	   if($location_field = $entry[4])
	   {
	       $path = str_replace('#location#', $location_field, $path);
	   }
	
	   return $path;
	
	}, 10, 2);

## Changelog ##

### 2.0 ###

*    Dropbox v2.0 Integration

### 1.1 ###

*    Caters for Multi-File Uploads
*    Updates the Lead/Entry Meta data with the Dropbox URL
*    Adds a hook on the replace_macros function (gform_dropbox_replace_path) to allow for custom macros/folder paths

### 1.0.9 ###
* Bug: Fixed problem with the last update which stopped the global Dropbox upload path from working when the override path hadn't been set by the user.

### 1.0.8 ###
* Feature: Added the ability to remove files from your server after they have been placed in your Dropbox
* Feature: Individual upload boxes can now be saved into different locations using an 'override' box

### 1.0.7 ###
* Bug: Fixed problem uploading files with non-ascii characters. Non ascii characters will be removed. If entire file name is removed an md5 hash will be generated. 

### 1.0.5 ###
* Bug: Fixed class conflict. Dropbox-api autoloader was being called twice.

### 1.0.4 ###
* Bug: Fixed a few variable typos that were giving warnings
* Bug: Used CURL class when linking Dropbox accounts. Was throwing errors for some users
* Bug: Fix problem were some files were not being uploaded. Boolean error.

### 1.0.3 ###
* Bug: Fixed problem with compatability with some Linux servers

### 1.0.2 ###
* Bug: Fixed (hopefully) issue when Wordpress is installed in another directory. 

### 1.0.1 ###
* Security Risk: Left debugging information displaying in first release. Turned off now.
* Bug: Changed the way we call our admin style sheet. Now use wp_enqueue_style();

### 1.0.0 ###
* First release. 
