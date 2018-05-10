# Tutorials

This documentation provides a brief tutorial on how to use the features and tools on the TVbeat dashboard. 

----

## Audience builder tutorial
The **Audience Builder** enables the users to create and manage simple and/or detailed audience segments. In the audience segments users are able to filter out a specific set of subscribers. Once an audience segment is created users are then able to use it though out the dashboard to define their target audience.

Let's go thorugh an example of creating, using and managing audience segments.

### Creating a new **Audience Segment**
There are two ways of creating an audience segment. 

We can do it through the **Audience Segment Picker** which is displayed in the green bar in tools like Segmentation, Expoter, Index etc.

In **Segmentation** we see the green bar and a picker which by default is **ALL - Total audience**. This means we 
include the entire viewership/subscriber base in the query. 

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/Segmentation-Picker.png)

Clicking on the **Audience segment picker** we are presented with a menu which includes a list of already created audience 
segments(empty if none h avebeen created yet) and at the bottom a **Create a new audience** button. 

Clicking on the **Create a new audience** button redirects you to the Audience Builder creation tool. Here we can either build our segment
with various filters to filter out subscribers based on their viewership data or we can import a list of subscribers via "**.txt**" or "**.csv**" file. We can 
switch between these two options with the tabs in the top bar("Build your Target audience" or "Import subscriber list"). In this example we will build a target audience.

We first enter a title of the audience segment(a default title is generated at the beginning). 

Below the title we have filter bars where we add filters  to define the audience. We can also add AND/OR conditions between filters 
which gives more flexibility in creating complex audiences. On the right side we have the Audience size calculator; this can recalculate the audience size each time the filters are changed and check the resulting audience size before we save the audience segment.

On the bottom we have the Save, Cancel and Export buttons. By clicking on the **Save** button after creating the segment we are redirected back to the tool that we started from. The created segment is automatically selected and results are displayed. If we click the **Cancel** button we undo any changes and are redirected back to where we came from. The **Export** moves the created segment to the **Exporter** tool where we can further set options and export the data.

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/audience-builder-default.png)

Lets create simple audience segment called **Young techies**. We want a Male audience, aged between 25-35 who are interested in Technology.

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/young-techies-example.png)
NOTE: The filters may differ depending on what dimensions a specific dataset provides.

The example above is a single line audience segment but we can easily add more complexity by adding multiple lines with AND/OR conditions. So for example we want to see people who watched **Big Bang Theory** episode last week and also watched the newest episode this week. With this example we would be able to see the retention of viewers from the last episode to the new one, and analyse their data to further understand their viewing habits.

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/big-bang-theory-example.png)

After we created our Audience segment we can **Save** it and it will redirect us to the tool where we came from. In this case it would be Segmentation. We have the audience segment that we created automatically selected in the green Audience bar.

### Importing a subscriber list
We can import a list of subscribers by uploading a "**.csv**" or "**.txt**" file.In the Audience Builder creation tool we switch to **Import subscriber list** in the top tab menu. We are presented with an interface that allows us to upload the desired file.

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/import-subs.gif)

### Audience segment picker
As described above we can use the Audience segment picker to select existing audience segments or create new ones. We select an audience by clicking on it but we can also hover over the question mark icon to display the audience size and summary. The icon on the rights indicates if the audience segment is either a built segment(users icon) or an imported list of subscribers(upload icon). 

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/Segmentation-Picker.png)

We can also edit built audience segments by clicking on the pencil icon. This redirects us back to the audience builder creation tool where we save the changes and are redirected back.

### Audience Builder List
While we can create and manage our audience segments through the Audience picker, we can also manage and create audience segment in the Audience Builder view. We can find this in the top main menu.

When we click on this we are presented with **list** of all of our Audience segments in a table. Here we can view, search, create, edit and delete our Audience segments. When creating and editing audience segments from this view we will be redirected back to this list after we save our changes.

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/audience-builder-list.gif)


----

## Indexing tutorial
The Indexing Report allows you to analyse strongly or poorly performing data points such as channel or program against a base segment.

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/index.gif)

The first step when analysing audience segments is to create a Base Segment. The base segment defines the benchmark to which other audiences are compared. Clicking on the "**Add Base Segment**" button will open a window where we can select the parameters for out Base segment. We can add an Audience segment, choose the dimension to break down the data by, and additional filters. 

After we define the Base segment we can now add multiple **Audience segments** to compare against the Base. By clicking the "**Add new Audience segment** button we are presented with the **Audience picker menu**. We can search and select from a list of existing Audience segments or we can create a new one. When creating a new one we will be redirected to the Audience builder creation tool.

When we have our Base segment and multiple Audience segments selected, we can see the Metric and Index numbers and compare the difference against the Base segment. We can sort by any column by clicking on the index or metric name. We can also change the metric by which we index in the (top right bar) **Metric picker**.

At the top of each column we can either select different parameters or audience segments by clicking on the **Edit** button (pencil icon). The **Remove** button in the audience segments removes the audience column. By hovering on the title area of each column we can see the Audience size and summary in a tooltip.

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/index-hover.png)

We can also **Export** the results in **PDF** or **Excel** by clicking on either option in the **More** menu in the top right area.

### Visualisation
In the middle of the top bar we can see a menu with two icons. We can switch between the column view(default) or chart view. The chart view presents the results in two different charts:

**Chart 1** - displays the comparison of audience segments index performance.
![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/index-viz1.png)

**Chart 2** - displays the comparison of the same audience segments for a specific dimension values. For example: We want to compare the audience segments on the channel BBC One
![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/index-viz2.png)

We can also **Export** these charts in the same top right **More** menu as previously mentioned.




