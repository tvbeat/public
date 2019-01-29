# TVbeat Dashboard Release notes

## 111.0.1 Hotfix
15 Dec, 2019

### Bugs/Improvements
* Fix issue where audience segment gets duplicated on multiple save button clicks
* Fix bug where delete/edit buttons in audience builder list were hidden

----

## 111 Release
14 Jan, 2019

### Features
* Fill rate calculation improvement
* Time series table widget
* Enable local sorting(sorting asc/desc is limited to first 5000 items returned) to improve loading speed for tables and charts
* Operational reports for Campaigns

### Bugs/Improvements
* Fixed bug where hideZeroItems would not work for time series table widget
* Fixed bug where sometimes the metrics text in exported excel files would duplicate
* Fixed bug where when exporting Content to excel, airtime values would not be generated and displayed properly
* Improved display of max width of first column of a tables
* Fixed bug where Export option on report widget disappeared when unchecking Segmentation in settings
* Update campaign metadata fields definitions

----

## 110.0.4 Hotfix
20 Dec, 2018
Fixed rule that caused that views that were unchecked in settings appeared in Product menu

----

## 110.0.3 Hotfix
14 Dec, 2018

### Bugs/Improvements
* Fix bug with loading campaigns in filter picker
* Fix bug where metadata column in segmentation was not displaying

----

## 110.0.2 Hotfix
12 Dec, 2018

### Bugs/Improvements
* Remove local cache bug
* Fix problem with deleting datasets in client accounts
* Improve cacher to crawl through all user groups in client account

----

## 110.0.1 Hotfix
11 Dec, 2018

### Bugs/Improvements
* Fixed incorrect filters when switching between In-flight and Completed campaigns
* Fixed FFDR tooltip not displaying
* Set yesterday midnight as restriction in Campaign module

----

## 110 Release
1 Nov - 11 Dec, 2018

### Features
* Campaign view changes
   * Added new metadata fields to Campaign view (Create date, FFDR, Excess Inventory, Primary Trafficker, Campaign status, Clash Codes)
   * Changed sorting functionality by clicking on field names in table header.
   * When scrolling the campaign table, the table header sticks on top
   * When paging the table the view is automatically scrolled back on top
   * Added two metadata filters (Campaign status, Primary trafficker)
   * Added export to excel option
   * Added tooltips when hovering over metrics/metadata in table header, with descriptions of each of them
   * Added alert that notifies when the user if the campaign was booked to late(difference between create date and start date of campaign is less than 3 business days)
* Added Time series table widget which allows the display of any breakdown vertically and horizontally by days/weeks/months
* Added date restriction to exclude campaigns before the Date restriction set in the Settings
* Added FE support for Event domain datasets with a switcher for this mode in the Settings
* Added “Hide Subs. ID export” option
* (BETA) Operational reports for campaigns 

### Bugs/Improvements
* Daylight savings bug was resolved and it now displays charts correctly when including those dates
* Fixed Forgot password bug where a it wouldn’t allow the user to reset the password if they were logged out
* Fixed bug when displaying groups in segmentation/research it would not display the stacked bars correctly
* Fixed bug when reseting failed exports
* Fixed bug where the admin would not be able to delete a dataset within a client account


----

## 109.0.6 Hotfix
4 Dec, 2018

### Bugs/Improvements
* Change metric descriptions for tooltips
* Change Indexing limit to 700 to prevent query URLs from being too long

----

## 109.0.5 Hotfix
15 Nov, 2018

### Bugs/Improvements
* Change CPM metadata field from cmpgn.cpt_net => cmpgn.cpt in campaign module

----

## 109.0.4 Hotfix
14 Nov, 2018

### Bugs/Improvements
* Add new metrics tooltip descriptions

----

## 109.0.3 Hotfix
12 Nov, 2018

### Bugs/Improvements
* Remove day light saving hack to support the new solution on the BE

----

## 109.0.2 Hotfix
7 Nov, 2018

### Bugs/Improvements
* Add option to disable "Export Subscriber IDs" in settings

----

## 109.0.1 Hotfix
6 Nov, 2018

### Bugs/Improvements
* Add CPM metadata in campaign module
* Daylight savings dates adds data points bug fix
* Change staging domain URL
* Fix multi-query table not displaying title

----

## 109 release
1 Oct - 31 Oct, 2018

### Features
* Campaign module final improvements and fixes
* New caching generator for overviews and campaigns

### Bugs/Improvements
* Opens sub-overview in new tab on click-through
* Fixed bug when sorting table in ascending order a zero result error would display preventing the user to use the table
* Added option to add position numbers in xAxis labels for TOP charts in widgets
* Fixed misaligned rows in Indexing when dimension value titles were too long
* Table improvements
   * First column in tables is now fixed when scrolling horizontally
* Added option to display Pie chart with legend on the right to improve the UI
* Fixed several unit tests
* Fixed bug where bookmark didn't save or recall the correct date range. Now custom ranges are properly saved and recalled as well as predefined ones(ex.: Last 7 Days) which are relative.
* Improved how label on bar chart(horizontal) display
* Fixed: Hide "no data available in table" while loader is turned on

----

## 108.0.4 Hotfix
13 Oct, 2018

### Bugs/Improvements
* Fixed overview caching problem where it didn't produce correct audience structure in queries
* Fixed multiquery table overflow

----

## 108.0.3 Hotfix
12 Oct, 2018

### Bugs/Improvements
* Fixed campaign report caching - update date range adjustment for active campaigns in campaign query generator
* Fixed overview caching - when using custom date ranges the overview query generator would create wrong date range in the query

----

## 108.0.2 Hotfix
11 Oct, 2018

### Bugs/Improvements
* Fixed "Add/Sort Metrics" bug where it messed up the order if metrics were renamed
* Added new metrics
* Fixed "Go to report" link in campaign info window
* Fixed bug where Campaigns in filter picker wouldn't populate on first load

----

## 108.0.1 Hotfix
10 Oct, 2018

### Bugs/Improvements
* Remove Caching for campaigns
* Add Generation checks for metadata
* Fix the Campaign no loading on first time in filter picker

----

## 108 release
1 Sep - 9 Oct, 2018

### Features
* Version number in main menu picker
* Options button
  * Option to show/hide metrics in Segmentation/Research in table
  * Option to display a specific metadata in column in Research table when breaking down by Campaigns
  * Option to show/hide groups, new UI
* Added Campaign list view
  * Active campaigns table
  * Completed campaigns table
  * Campaign info panel
* Added connection to the new Metadata API
  * Filter picker for the Campaign dimension now consumes data from the Metadata API. It also restricts campaign results based on flight date
* Click to sub-overview is now opened in new tab
* Added tooltips with metric descriptions when hovering table header for new ad metrics
* Added error logging for FE backend


### Bugs/Improvements
* Fixed design of paging in Overview/Report tables
* Fixed bug where an error message would appear when sorting by ascending in Content tables in overviews/reports. Now a message will appear which allows the user to view the data even though its zero
* Fixed bug where bar chart(horizontal) didn’t display labels properly
* Fixed bookmark bugs which caused the bookmarks not to load correctly
* Fixed tooltip display where to many metrics would break the design
* Various table display improvements
  * Table scrolls horizontally when there are too many columns displayed
  * Table headers dont overflow when metric names are too wide
* Fixed min-width problem when resizing Overviews/Reports.

----

## 107 release
1 - 31 Aug, 2018

### Features
* Export upgrades
  * Added ability to export multi-query charts
  * Updated exporting interface in general.
* Updated Mixpanel events
* Redesigned the Bookmark window and added the ability to search through bookmarks
* Added an endpoint that points to the documentation page
* Refactored unit tests for different parts of the dashboard

### Bugs/Improvements
* Fixed item matching for multi-query charts
* Fixed empty exports when exporting the Fill Rate % metric
* Fixed the issue where dimension values with a zero ID were not being rendered
* Fixed the issue where zero values were not displayed in the chart
* Fixed an issue where email were not sent after a longer export
* Improved saving of user groups in the database

----

## 106.0.2 Hotfix
29 Aug, 2018

### Bugs/Improvements
* Caching fix: removed date range text that was occurring in overview generator queries
* Caching fix: fixed bug where overview generator didn't set proper default metrics for queries.

----

## 106.0.1 Hotfix
21 Aug, 2018

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
