---
id: xtra-glossary
title: Glossary
---

The terms defined in this glossary describe core concepts, objects, services, 
and workflow that operate in the platform environment.
Also see the 
[iSP Terminology List](https://istreamplanet.atlassian.net/wiki/spaces/COM/pages/157155491/Terminology) 
for other possible terms.

--------

## account  
> Or _account owner_. A content consumer of the iStreamPlanet platform. 
> Accounts are a tenant’s customers, the "fans" who purchase and view video assets.

## artifact  
> A group of asset attributes that defines an asset type. 
> Some example types are person, genre, sport, movie, show_season, and 
> show_episode.

## asset  
> A piece of video content to be streamed and viewed.

## asset types  
> The platform supports the following broad asset product types: 
> * single purchase (a [VOD](#VOD) show episode or show season)
> * season package (a finite subscription)
> * special event (such as the Superbowl)
> * regular (monthly) subscription (with unlimited billing)

## banner
> A carousel "card" that represents and links to a video asset. 
> Banners may be configured to appear as text links, buttons, images, 
> or a combination of these elements.

## attribute
> A key-value pair that contains extra metadata about an asset.

## billing plan  
> An entity that has a price and an optional recurrence associated with it. 
> E.g. $7.99 with monthly billing that expires on 2018-10-31. 
> The number of occurrences may be unlimited if perpetual until cancelled, 
> limited for a seasonal subscription, or zero for a one-off purchase. 

## blackout
> A restriction on the available viewing area for a program. 
> For example, fans within Brazil might usually have access to all 
> games on a particular channel. However, if the tenant sets a game to be 
> "blacked out" within Brasília city limits, then any fans 
> within that city would be unable to watch that game on the tenant's channel. 
> Blackout regions always override any overlapping [whitelist regions](whitelist-region). 
> _Compare with_ [region](#region).

## collection
> An ordered group of carousel items that represent video assets, such as channels, 
> events, movies, shows, episodes, and [banners](#banner).

## content
> A file containing the actual content for an asset. 
> Usually, there will also be a meta-file containing metadata about that 
> asset, although some data sources (e.g. filesystem) merge the content 
> file and the meta-file into a single file.

## DRM   
> Digital Rights Management. 
> Access control technologies for enforcing legal restrictions on the use of copyrighted works.

## entitlement
> Legal and digital permission to access and view a video asset. 
> Entitlement to may be granted when a fan joins a streaming service, subscribes 
> to a package, or purchases a specific video product.

## EPG
> [Electronic Program Guide](https://www.wikiwand.com/en/Electronic_program_guide). 
> Scheduling data which typically describes the schedule and content of one or more Live Linear channels.

## in-app purchase 
> A purchase made via a mobile app store such as Apple iTunes or Google Play.

## item
> A specific piece of content that is associated with video 
> content—either a movie or an episode or a show. 
> This is the basic unit of content that a fan can interact with.

## layout
> A particular composition of carousel [collections](#collection)  on a client [page](#page). 
> Layouts are selected dynamically based on the requestor’s location and time window.

## metadata
> Attributes that describe an asset or other system object.

## package
> A defined collection of one or more video assets. 
> Although it is not required, a package is usually 
> associated with a [billing plan](#billing-plan).

## page
> For carousels, a logical container of [collections](#collection) requested by a client application.

## product 
> Within the platform, a [billing plan](#billing-plan) combined with 
> a [package](#package) that may be associated with one or 
> more [SKUs](#SKU) for purchase. 
> Platform tenants may define separate SKUs based on content vendor, language, 
> geographic area, etc. 

## purchase record
> _See_ [receipt](#receipt).

## receipt
> A receipt (or a purchase record) is a transaction confirmation that an account has purchased an SKU.

## region
> A defined area within which a fan may be permitted to view a media asset. 
> Regions are composed of one or more  geographic locations such as a 
> countries, provinces or states, cities, and/or postal codes. For example 
> Delaware, Maryland, and Virginia may form a region while Oregon state plus 
> Vancouver, Washington may constitute another region. 
> A video asset *must* be assigned to at least one [whitelist region](whitelist-region) to 
> be available for viewing. _Compare with_ [blackout](#blackout).

## role
> A defined collection of permissions within the Portal.
> Portal users can be assigned to one or more roles to simplify 
> management of user permissions. 
> All platform installations contain the following default roles: _Administrator, 
> ContentEditor, CustomerService, PackageManager, PricingManager,_ and _UserManager_.

## section
> An ordered list of carousel [items](#item) that are shown to account owners.

## SKU
> Stock Keeping Unit. A unique identifier for a product.

## subscription
> Access to video content based on recurring payments over time.  
> A subscription may be _finite_ for a season package, or _unlimited_ for a 
> currently on-going series.    

## tenant
> A contracted content provider, owner, or distributor that employs the iStreamPlanet
> platform API to build customized video streaming applications for their account owners (fans).

## token
> A software key used to provide temporary workflow authorization. 
> Tokens are passed between system components and expire in accordance 
> with tenant policies set in the Administration Portal.

## VOD
> Video on Demand. Describes the process or scenario where a client application or 
> account owner can request to play content at any given time. 
> (E.g., the Netflix model of video distribution.)

## whitelist region
> One or more areas within which content may be viewed. 
> A video asset *must* be assigned to at least one "whitelist" region to 
> be available for viewing. _See_ [region](#region). _Compare with_ [blackout](#blackout).

---


[Back to top](xtra-glossary)
