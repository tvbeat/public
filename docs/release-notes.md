# TVbeat Dashboard Release notes

## 106.0.1 Hotfix
21 Aug

### Bugs/Improvements
* Fixed bug where zero values didnt appear in line/bar charts
* Fixed bug where filters with a value of which ID was 0, didn't appear in the UI
* Fixed caching by adding global filter rules to Overview Query Generator

----

## Cycle 106
1 - 31 July, 2018

### Features
* Added new ad metrics
* Campaign API integration
* Global filter rules
* Custom message option in widgets when "zero" data is returned
* Add "Fill Rate %" custom metric

### Bugs/Improvements
* Export to PDF fix
* Week/Month export to excel fix for Proximus/Sky Media/Sky_4M datasets
* Fixed dash loading speed bug
* Fixed several Audience builder bugs
  * Some users couldn't delete/edit own segments
  * Content wasn't displayed in audience summary
  * Other audience segment related fixes
* Update VODContent exception to include new ad metrics
* Fixed bug that caused duplicates when saving new datasets in settings
* Set pagination as an option in the widgets
* Fix dimension category styling

----

## Cycle 105
1 - 30 June, 2018

### Features:
* Dash versioning
* Added a documentation/help app which will contain every information description the dashboard for users
* Added initial messages that describe the functionality of features and various elements in the dashboard for better on-boarding
* Zero results filtering - a message in tables that hides zero results, notifies the user and offers the ability to expand these results
* Paging in report widgets

### Bugs/Improvements:
* Export to Excel function opens a new tab with the Exporter
* Fixed the Live bug that prevent the last selected channels to be saved
* Fixed exporter bug where exporting on weekly interval produced incorrect results (for sky and sky_media datasets)
* Added title to multi-query table
* Fix server lint errors

----

## Cycle 103/104
1 Apr - 30 May, 2018

### Features: 
* Added Permissions for Audience Segments
* Multi-query chart
* Multi-query table
* Custom widgets support
* Ad Inventory
* Block breakdown widget
* Grouping in widgets
* Add Last 3 Month predefined date range

### Bugs/Improvements:
* Several Grouping improvements and bug fixes
* Several other bugs for existing features

----

## Cycle 102
5 - 30 March, 2018

### Features / Improvements
* Audience builder
  * New UI flow of creating and selecting audience segments
  * AND/OR structure of querying audience data
* Indexing update
  * Better indexing column display
  * Metric selector
  * PDF and Excel export support
  * New Visualization page with two new charts to display indexing of different audience segments
* Import subcribers optimization - Increased the amount of subscribers users can upload
* Update query limit to 5000 - Queries now return up to max 5000 results (this will be adjusted based in the future according to performance)
* Various UI design improvements
* Old Stack option - marks a dataset that uses old stack
  * Old stack datasets revert to GET method queries for Import subscribers to be compatible
  * Old stack datasets dont support AND/OR multiple sets which will only become available after we migrate those datasets to new stack

### Bug fixes
* Fixed" Add new client account" error where the input was disabled.
* Fixed bug when Importing subscribers would not upload the exact amount of subscribers from the uploaded file
* Removed condition that didnt allow the package sub-overview picker to display
