---
id: guide-portal-admin
title: Administration 
sidebar_label: Administration
---

This Administration Guide describes how to use the Portal 
to manage accounts, billing plans, video content, DRM entitlements, 
and system policies.

## ACCOUNTS

The ACCOUNTS section allows administrators to manage and configure user 
accounts and roles.

### Users 

Use the __Users__ menu to view the list of all administrator and user (fan) 
accounts in your installation. 
User accounts are typically added by fans though your client application.

#### Sorting and searching accounts:

To sort the account list, select the desired column title--username, email 
address, first name, or last name. 
The search field filters the listing based on data in all four columns.

NOTE: 
> In search fields, case is ignored but accented character glyphs are respected and must match exactly: B = b, ó != o, ñ &ne; n.


#### Deleting accounts:

. Select the checkbox (&#9744;) at the beginning of the row for any accounts that you wish to delete.
. Select the red delete button.
. Select [CONTINUE] at the bottom of the Delete Account dialog box.

#### Updating account details:

. Select the text for the account that you wish to update.
. On the Account tab, select any field and enter the updated information.
. Select [SAVE] at the bottom of the page.


### Section A


### Section B



[Back to top of Administration](guide-portal-admin)




<!--

// Is regex searching available for geeky admins?
// ; i.e., ó != o, ñ &ne; n, etc.
// * [*] Matches only look at the beginning of a word.
// * [*] Some pages require at least three characters to be entered.
-->


<!-- DO NOT CHANGE orbis-portal-admin NAME YET

# Orbis API Documentation 

// * EPC: terminology usage
// "administrative" == adjective
// "adminstration"  == general noun  
// "administrator"  == person

-->

<!-- image::Users-UserAccounts.jpg[details screen, role="text-left", width="80%", scaledwidth="75%"] -->


<!--
// To update details for an account&colon;


+
image::Users-Account.jpg[details screen, role="text-left", width="80%", scaledwidth="75%"]

////
{
[[package]]package:: 
    A defined collection of one or more video assets.  
    Although it is not required, a package is usually 
    associated with a <<doc-glossary.adoc#billing_plan,billing plan>>.


Viewing the list of user accounts

searching
sorting by: first name, last name, email address, account type, status 
(active/disabled), registered(???), verified, last login 
Basic information: billing address, email, preferences, etc.
Detailed subscription/billing/payment/support history (this might only 
be a reference)
Inviting new users 
User accounts cannot be directly created.  Admins can only extend invitations 
(via email); users must then register and verify, etc. 
Adding user names to accounts (such as for families)?
Will user names be associated with email accounts?
Updating account information:
Email Account:
Viewing/Editing basic info: username* (default = same as email address), 
first name, last name, email address*, phone numbers
Generate a new password

Device Registration and Login

Manage User Watch Lists
Payment Info: Payment method, Billing address
Billing Details: credits available, payment history, associated subscription plans
applying credit: amount, currency, and notes
issuing a refund: amount, currency, and notes
Viewing History
Recurring Subscription plan 
Web purchase 
applying credit: amount, currency, and notes
issuing a refund: amount, currency, and notes
iTunes purchase
applying credit: amount, currency, and notes
refunds must be requested by the user directly from Apple
preferences, etc.
Social Account
Viewing basic info: first name, last name, profile URL, email address
Disconnecting from a social account (if user also has a regular fan (email) account)
Deactivating and Deleting accounts
Cascade: delete associated entitlements, etc.

}
////

// === Administrators
// TODO: Suggest using "Members" instead of using "Users"


Creating administrator accounts&colon;::
Only SuperAdmins can create new administrator accounts.

// image::Admins-AdminAccounts.jpg[details screen, role="text-left", width="80%",scaledwidth="50%"]

Update roles and permissions for an account&colon;::
Select the text for the (administrator) account that you wish to update.

Remove roles from an account&colon;::
. Select the menu:Users[] menu.
. Select the text of the account that you wish to update.
. Select the *Roles* tab.
. On the Roles tab, select the checkbox (&#9744;) at the beginning of the row 
for any roles that you wish to remove.
. Select the red Remove Roles button (&#9940;).
. On the Remove Roles dialog box, select btn:[CONTINUE].

Assign additional roles to an account&colon;::
. On the Roles tab, select btn:[ASSIGN ROLES].
. On the Assign Roles dialog box, select the plus sign (+) at the left of any 
roles that you wish to add.
. Select btn:[ASSIGN] at the bottom of the dialog box.
+
// image::Admins-Roles.jpg[details screen,role="text-left", width="80%",scaledwidth="50%"]

// * The Permissions tab displays all current permissions for the selected administrator.
// +
// image::Admins-Permissions.jpg[details screen, role="text-left", width="80%",scaledwidth="50%"]

Demoting accounts&colon;::
If needed, administrator accounts can be demoted to basic user accounts. 
Demotion removes all administrative privileges from the account. 
. Select the checkbox at the beginning of the row for any accounts that you wish to demote.
. Select the red demote button.
. Select btn:[DEMOTE] at the bottom of the Demote Administrator dialog box.
+
image::Admins-DemoteUser.jpg[details screen, role="text-left", width="80%",scaledwidth="50%"]

SuperAdmins can restore administrative account privileges.

////
{
Administrator Accounts
(Suggestion: use the term member rather than user within the UI to refer to 
Admins and members of Roles to avoid confusion with fans.)

Inviting new Admins via email
By default, new Admins should belong to an existing group with read only permissions
Adding/Removing Roles
Setting Groups
By default, permissions for new groups should be read only; create, update, 
delete permissions must be explicitly granted
Viewing Permissions 
Roles
The Administrators Guide describes how to use the platform  Portal to manage 
accounts, billing plans, video content, and entitlements.

By default, Portal administrator accounts may be assigned to the following roles:

(See: Roles, Permissions & Authorizing Resources)
 Administrators
Defines all admin types and permissions for your installation
Content Editors
Asset and category permissions
Customer Service 
Account permissions: user details read/write, delete users, read and cancel 
subscriptions, refund.
All entitlement permissions
Package Managers
Entitlement permissions on all packages
Pricing Managers
Billing plan permissions


User Managers
OAM user details read/write, delete users, read policies
searching and sorting by name, description, number of members
Members (Users): searching, viewing, and sorting group members by first name, 
last name, and email address
add/remove members
Permissions – Roles with Descriptions (Add/Remove view and edit permissions)
Manage roles
Add sites
Export users (members)
View full secret key
View partial secret key
Edit site settlings
Providers configuration and permissions
Schema editor (!!!)
Restrictions
Signals
Edit policies and templates
UI Builder - Edit Layout / CSS /JS
Edit schema (!!!)
Identity sync permissions
comments setup and settings
Moderation management
Gamification settings
Enable/Disable client-side access
Identities, Syndication, and Usage


Reports
Settings (affects all accounts, User and Admin, universally!)
concurrent streaming limits
email verification,
email template, login attempts, lockout time, token TTL, two-factor 
authentication, Password Requirements (strength)
RESET PASSWORD
require email verification
email template
password reset page URL
NEW USER REGISTRATION
email template
password reset page URL

}
////


=== Roles
Select menu:Roles[] to view and manage the list of all current administrative 
roles in your installation. 

image::Roles-RoleList.jpg[a the account details screen, width="80%", scaledwidth="50%"]

////
{
.Sorting Roles ?
You can sort the listing by username, email address, first name, or last name 
by electing on the desired column title. 
The search field filters the listing based on data in all four columns.
}
////

Creating a new role&colon;::
. On the Roles page, select btn:[ADD NEW] at the top of the page.
. On the Create New Role dialog box, enter a name and description.
. Select btn:[CREATE] at the bottom of the dialog box.
+
image::Roles-CreateNewRole.jpg[a the account details screen, width="80%", scaledwidth="50%"]


////
{
==== Updating a Role
.Updating Account Details
To update details for an account:

. Select the text for the account that you wish to update.
. On the Account tab, select any field and enter the updated information.
. Select  btn:[SAVE] at the bottom of the page.
}
////

Deleting roles&colon;::
. Select the checkbox (&#9744;) at the beginning of the row for any roles 
that you wish to delete.
. Select the red delete button.
. Select btn:[CONTINUE] at the bottom of the Delete Role dialog box.
+
*NOTE:*
The core platform roles cannot be deleted.


////
{
=== Permissions
Permissions determine which abilities are available to administrators your within 
your installation.

=== Settings
}
////


// ============================================================================== //
== STORE 
The STORE section allows administrators to manage products, billing plans, 
asset packages, and other store details.

=== Products 
Products connect billing plans with asset packages.
Select menu:Products[] to view and manage the list of products defined in your 
installation. 


Creating a product&colon;::
. Select menu:Products[] from the left menu column to view the current list of products.
. On the Product List page, select btn:[ADD NEW].
. Define the new product:
..  Enter a new name, short description, and long description in the appropriate fields.
..	Enter a store product ID for at least one payment method.
..  Optionally, add key-value pairs to include any custom data for the product.
..	Under PRICING, select the desired currency and enter the price amounts to 
be sent to each payment processor.
..	Select an existing Asset Package to add.
..	Select an existing Billing Plan to add.
//.. Select the PRODUCTS tab.
//.. Select the packages that you 
. Select btn:[SAVE].


Deleting/removing products&colon;::
. On the Product List page, select the checkbox (&#9744;) at the beginning of 
the row for any products that you wish to delete.
. Select the red delete button.
. Select btn:[CONTINUE] at the bottom of the Delete Products dialog box.

////
{
==== Custom Attributes 
...
}
////

=== Billing Plans
Billing Plans associate a price with a recurring (or non-recurring) billing 
schedule.
Select menu:Billing_Plans[] to view and manage the list of billing plans 
defined in your installation. 

Creating a billing plan&colon;::
. Select menu:Billing_Plans[] on the left side to view the billing plans list.
. On the Billing Plans page, select btn:[ADD NEW] at the top of the page.
. Define the new billing plan on the DETAILS tab:
..  Enter a new name in the BILLING PLAN ID field.
..	Enter a DESCRIPTION for the new billing plan.
..	Under PRICING, select the desired currency and enter the price amounts to be 
sent to each payment processor.
..	Select the BILLING TYPE frequency.
//..	Select the PRODUCTS tab.
//.. Select the packages that you 
. Select btn:[SAVE].


////
{
=== Billing Plans

==== Creating a Billing Plan

===== Details
The Details tab...

===== Products 
...

==== Updating a Billing Plan
}
////

Deleting billing plans&colon;::
. Select the checkbox (&#9744;) at the beginning of the row for any billing 
plans that you wish to delete.
. Select the red delete button.
. Select btn:[CONTINUE] at the bottom of the Delete Billing Plans dialog box.

=== Asset Packages
You can group your video assets in the CMS into packages and then designate these 
packages as free or available for purchase.
Select menu:Asset_Packages[] to view and manage the list of asset packages 
defined in your installation. 

Creating an asset package&colon;::
. On the Asset Packages page, select btn:[ADD NEW] at the top of the page.
+
image::AssetPackages-AssetPackages.jpg[details screen,width="80%", scaledwidth="50%"]
+
. On the Details tab:
    .. Enter a name and description.
    .. Select the blue btn:[+] Whitelist Regions button to add desired regions.
    .. Select the checkbox if this will be a free package. 
    .. Select the Assets tab.
+ 
image::AssetPackages-Details.jpg[details screen, width="80%", scaledwidth="50%"]
+
. On the Assets tab:
    .. Select btn:[ADD NEW] in the middle of the page.
    .. Select assets from the Add Assets list. ...
    .. Select btn:[ADD].
    .. Select the Products tab.
+
image::AssetPackages-AddRegions.jpg[details screen,width="80%", scaledwidth="50%"]
+
. On the Products tab:
    .. Select products from the list based on name, package ID, or billing plan ID. ...
    .. Select the Custom Attributes tab.
. On the Custom Attributes tab:
+
Enter product details such as league, sport, SKU ID, descriptions, etc. 
+
image::AssetPackages-CustomAttributes.jpg[details screen, width="80%", scaledwidth="50%"]
+
. Select btn:[SAVE] at the bottom of the page.
+
The new asset package will now appear in the list.

// image::AssetPackages-New.jpg[a the account details screen,width="80%", scaledwidth="50%"]


Deleting asset packages&colon;::
. Select the checkbox (&#9744;) at the beginning of the row for any asset 
packages that you wish to delete.
. Select the red delete button.
. Select btn:[CONTINUE] at the bottom of the Delete Asset Packages dialog box.

////
{
==== Assets 
...
}
////



// ============================================================================== //
== CONTENT 
The CONTENT section allows administrators to modify descriptive 
information for your video assets.


=== Channels
The menu:Channels[] page allows administrators to view and manage platform content and descriptions.
//Select menu:Channels[] to view, search, filter, and manage the contents and descriptions of the 
//channels available in your installation. 

image::Channels-Channels.jpg[details screen, width="80%", scaledwidth="50%"]

Applying blackout restrictions to live linear channels&colon;::
// !!!: Needs updating

. Select the menu:Channels[] menu item.
. Select the row of the desired channel.
. Select the blue btn:[+] button to add blackout regions.
. Select the checkboxes (*&#9744;*) at the beginning of the row for any 
regions that you wish to restrict from viewing this channel.
. Select the btn:[ADD] button. The new blackout regions will now be listed for the channel.
. Select the btn:[SAVE] button to finish setting the blackout regions.
// img	


Updating descriptions for live linear channels&colon;::
//DONE: as of 18-Nov-2018
In this release, you can change the channel name, change the short name, and add blackout regions.
All other fields are currently read-only.
. Select the menu:Channels[]  menu item.
. Select the row of the desired channel.
. Optionally, select the *NAME* field and enter a new channel name.
. Optionally, select the *SHORT NAME* field and enter a new short name. 
. Scroll down on the page to view any remaining description fields.
. Select the btn:[SAVE] button to finish updating the channel descriptions.
// img


//column sorting available

////
{
==== Details
The Details tab...

==== Programs 
...
}
////

=== Schedule
The menu:Schedule[] page allows administrators to search, view, and manage  
electronic program guide (EPG) entries that are available within your installation. 

image::Schedule-Programs.jpg[details screen, width="80%", scaledwidth="50%"]

Viewing programs for a live linear channel&colon;::
. Select the menu:Schedule[] menu item.
. Optionally, select a desired start date and start time for the program schedule 
by typing or selecting a date and time from calendar field.
. Select a channel from the *Channel* field to filter the Program list. 
+
You may need to clear any channels that you have previously selected during your session.
(Channel filter selections persist for the current login session, unless manually changed or cleared.)
. Optionally, select one or more program types from the *Type* field to filter the Program list. 
+
image::Schedule-Viewing.jpg[details screen, width="80%", scaledwidth="50%"]
// todo: add call-outs for steps to screenshot above


Applying blackout restrictions to scheduled programs&colon;::
. Select the menu:Schedule[] menu item.
. Select the scheduled program that you want to restrict.
+
image::sched-1.png[the initial program schedule, width="80%", scaledwidth="50%"]
. Select the blue btn:[+] to add blackout regions.
+
image::sched-3.png[the initial program schedule, width="80%", scaledwidth="50%"]
. Select the checkboxes (&#9744;) at the beginning of the row for any regions that you wish to 
restrict from viewing the program.
+
image::sched-4.png[the initial program schedule, width="80%", scaledwidth="50%"]
. Select the btn:[ADD] button. The new blackout regions will now be listed for the program.
. Select the btn:[SAVE] button to finish setting the blackout regions.
+
image::sched-6.png[the initial program schedule, width="80%", scaledwidth="50%"]


// Updating program details:
// Select the row of the desired program.


=== VOD Catalog
The menu:VOD_Catalog[] page allows administrators to search, view, and manage 
video on demand (VOD) content available within your installation. 

Playing the video content to confirm access to the correct asset&colon;::
. Scroll down to the Playback Assets section .
. Click the play icon (&#9654;) to the left of the DASH PRIMARY URL field.
. Click the play icon (&#9654;) that appears in the popup media window.

//!!! add some screen shots/ gifs

Updating descriptions for VOD content&colon;::
In this release, you can change the program name, short name, general description, 
and short description for VOD entries.
All other fields are currently read-only.
// ?... and add blackout regions. ?
. Select the menu:VOD_Catalog[] menu item.
. Select the *Search* field and enter a character string that you want to find in the VOD Catalog.
. Optionally, select one or more program types to filter the VOD Catalog list. 
+
image::VOD-Update.jpg[details screen, width="80%", scaledwidth="50%"]
+
. Select the row of the desired VOD program.
+
image::VOD-Catalog.jpg[details screen, width="80%", scaledwidth="50%"]
+
. To change a name or description, select the desired field and enter the new name or description.
+ 
Scroll down on the page to view any remaining description fields.
+
. Select the SAVE button to finish updating the show descriptions.
+
image::VOD-save.png[VOD save, width="80%", scaledwidth="50%"]

// !! we will need to add info on how to update 

For Episodes, you can:

* Select the *VIEW SHOW DETAILS* link.
** Select the *Details* tab to view the general show description.
** Select the *Episodes* tab to view the list the episodes that are available for each season.
* Select the ** Season # ** field to filter the list on one or more seasons.
* Select one of the listed episodes to view or update the detailed description for that specific episode.
+
image::VOD-episodes.png[VOD save, width="80%", scaledwidth="50%"]

	
For Shows, you can: 

* Select the *Episodes* tab to list the episodes that are available for each season.
* Select the ** Season # ** field to filter the list on one or more seasons.
* Select one of the listed episodes to view or update the detailed description for that specific episode.
	

// content descriptions for video on demand (VOD programs).
// ...

// To search the VOD Catalog:
// ...

// To update a program description:
// ...

// === Details
// The Details tab contains a general description of the entire series.
// ...

// === Episodes
// The Episodes tab lists individual episodes for each show in a series.
// ...

=== Live Content
The menu:Live_Content[] page allows administrators to view and manage 
live sports competitions and other live events accessible from your application. 
//!!! add some screen shots/ gifs
//!!! complete this section

// To view scheduled Live Content entries:

// To add new Live Content:

// * Team Competitions

// * Other Sports Competions

// * Non-sports Live Events


// To update existing Live Content:

// To delete Live Content entries:


// Playing the video content to confirm access to the correct asset&colon;::
// . Scroll down to the Playback Assets section .
// . Click the play icon (&#9654;) to the left of the DASH PRIMARY URL field.
// . Click the play icon (&#9654;) that appears in the popup media window.

//!!! add some screen shots/ gifs



// ============================================================================== //
== PROMOTION
The PROMOTION section allows for the creation and customization of promotional objects for the platform, 
such as carousels, menus, sliders, and other user interface collections.

// TODO: Get more examples on how to use collections  (top 3 to 5 uses?)

=== Collections
The Collections page allows content curators to create, update, and delete collections 
of items that represent video assets.  The items in a collection typically share some
similarity such as genre, release dates, director, etc. can be deployed as carousels, menus, buttons, 

// video-on-demand (VOD) initially

image::Collections-list.jpg[the Collections list screen, width="80%", scaledwidth="50%"]

// !!!: Finish:
// !!!: Create, Read, Update++, Revert, Publish, Delete


// ============================================================================== //

=== Banners
The Banners page allows content curators to create, update, and delete items that 
appear in Collections. A banner is a "card" that represents and links to a video asset.
Banner items may be configured to appear as links, buttons, images, or any combination of these
elements.

// !!!! Need to add Layouts, Banners (Cards!), Collections, & Pages to the Glossary

// !!!! image::Banners-list.jpg[the Banners list screen, width="80%", scaledwidth="50%"]



// !!!: Finish:
// !!!: Create, Read, Update++, Revert, Publish, Delete


// ============================================================================== //
== CONFIGURATION
The CONFIGURATION section allows administrators to customize global settings and 
attributes for the platform.

//// 
=== General Settings 
General Settings ...
Select menu:General_Settings[] to view and adjust ... in your installation. 
}
////

=== Regions
The Regions page allows administrators to create, update, and delete recognized 
geographic regions.

image::Regions-Regions.jpg[a the account details screen, width="80%", scaledwidth="50%"]

Creating a new region&colon;::
. Select the menu:Regions[] menu item.
. On the Regions page, select btn:[ADD NEW] to choose a region based on either Locations 
or Coordinates.
* For _Coordinates_, enter the name, latitude, longitude, radius value, and radius unit 
(kilometers or miles).
* For _Locations_, enter the country, subregions, cities, and/or postal codes.
+
image::Regions-Coordinates.jpg[a the account details screen, width="80%", scaledwidth="50%"]
. Select btn:[SAVE].


////
{
// To create a new region&colon;::
. On the Create New Region dialog box, enter a name and description.
}
////


Updating a region&colon;::
. Select the menu:Regions[] menu item.
. Select the text of the region that you want to update.
. Optionally, change the name of the region.
. Optionally, select the btn:[ADD LOCATION] button to add additional named 
locations defined by country, state/province/region, city, and postal code.
. Select the btn:[ADD] button. The new location(s) will be listed for the current region.
. Select the btn:[SAVE] button. Locations for the redefined region are now displayed.

Deleting regions&colon;::
. Select the checkbox (&#9744;) at the beginning of the row for any regions that you wish to delete.
. Select the red delete button.
. Select btn:[CONTINUE] at the bottom of the Delete Regions dialog box.

// ------------------------------------------------------------------------------------ //


=== Providers
The Providers page allows administrators to add and manage content providers, service providers, and their associated  
whitelist regions.

// !!!: finish!
////
Adding a new content provider&colon;::
. Select the row of the content provider whose regions you wish to modify.
. Select the blue btn:[+] Whitelist Regions button to add desired regions.
. On the Add Regions dialog, select the checkboxes for the regions that you want to add.
. Optionally, select the btn:[ADD LOCATION] button to add additional named 
locations defined by country, state/province/region, city, and postal code.
. Select the btn:[ADD] button. The new location(s) will be listed for the current region.
. Select the btn:[SAVE] button. Locations for the redefined region are now displayed.
////

Adding a whitelist region&colon;::
. Select the row of the content provider whose regions you wish to modify.
. Select the blue btn:[+] Whitelist Regions button to add desired regions.
. On the Add Regions dialog, select the checkboxes for the regions that you want to add.
. Optionally, select the btn:[ADD LOCATION] button to add additional named 
locations defined by country, state/province/region, city, and postal code.
. Select the btn:[ADD] button. The new location(s) will be listed for the current region.
. Select the btn:[SAVE] button. Locations for the redefined region are now displayed.

Deleting whitelist regions&colon;::
. Select the row of the content provider whose regions you wish to modify.
. Select the trashcan button next to the region that you wish to delete.
. Select btn:[SAVE] at the bottom of the page to confirm and save your deletion.


// !!!: TBD!

=== Custom Attributes
The Custom Attributes page lists attributes defined for this specific tenant installation.

Select menu:Custom_Attributes[] to view the list of attributes that have been added to your installation. 

image::Custom-Attributes.jpg[The Custom Attributes screen, width="80%", scaledwidth="50%"]
////
=== Content Providers
Content Providers ...
Select menu:Content_Providers[] to view and adjust ... in your installation. 


//
== Administrator Profile
...

=== Account 
...

=== Payment Info
...

=== Billing Details
...

=== Metrics and Analytics ?

=== System Issues ?


// epc: 

EPC: heading hierarchy guidance... 
    Gerund: Managing/Working with Asset Packages        {with plural}
        Command: Update an Asset Package                {with singular}
        Process: Workflow for Credit Card HOA Processing
            infinitive: To update an asset package:     {use only when necessary}

////

-->