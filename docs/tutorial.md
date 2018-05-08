# Tutorial

This documentation provides a brief tutorial on how to use the features and tools on the TVbeat dashboard. 

## Audience builder
The **Audience Builder** enables the users to create and manage, simple and/or detailed audience segments. In the audience segments users are
able to filter out a specific set of subscribers. Once an audience segment is created, the users are able to use it though out the dashboard to
define their target audience.

Let's go thorugh an example of creating, using and managing audience segments.

#### Creating a new **Audience Segment**
There are two ways of creating an audience segment. 

We can do it through the **Audience Segment Picker** which is displayed in the green bar in tools like Segmentation, Expoter, Index etc.

In  **Segmentation** we can see the green bar and a picker which by default we have the **ALL - Total audience**. This basically means we 
are including the entire viewership/subscriber base. 

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/Segmentation-Picker.png)

By clicking on the **Audience segment picker** we are presented with a menu which includes a list of already created audience 
segments(empty if none has been created yet) and at the bottom a **Create a new audience** button. 

Clicking on the **Create a new audience** button redirects you to the Audience Builder creation tool. Here we can either build our segment
with various filters to filter out our viewership data or we can import a list of subscribers via "**.txt**" or "**.csv**" file. We can 
switch between these two options with the tabs in the top bar("Build your Target audience" or "Import subscriber list").

We first enter a title of the audience segment(a default title is generated at the beggining). 

Bellow the title we have our filter bars where we add our filters. We can also add AND/OR conditions between filters 
which gives us more flexibility in creating more complex audiences. On the right side we have the Audience size calculator. We can calculate the audience size each time we change the filters and check the resulting audience size before we save the audience segment.

On the bottom we have the Save, Cancel and Export buttons. By clicking on the **Save** button after creating the segment we are redirected back to the tool that we started from. The created segment is automatically selected and results are displayed. If we click the **Cancel** button we undo any changes and are redirected back to where we came from. The **Export** moves the created segment to the **Exporter** tool where we can further set options and export the desired data.

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/audience-builder-default.png)

Lets create simple audience segment called **Young techies**. We want a Male audience, aged between 25-35 who are interested in Technology.  
![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/young-techies-example.png)
NOTE: The filters may differ depending on what dimensions a specific dataset provides.

The example above is a single line audience segment but we can easily add more complexity by adding multiple lines with AND/OR conditions. So for example we want to see people who watched **Big Bang Theory** episode last week and also watched the newest episode this week. With this example we would be able to see the retention of viewers from the last episode to the new one.
![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/big-bang-theory-example.png)

After we created our Audience segment we can **Save** it and it will redirect us to the tool where we came from. In this case it would be Segmentation. We have the audience segment that we created automatically selected in the green Audience bar.

#### Importing a subscriber list
We can import a list of subscribers by uploading a "**.csv**" or "**.txt**" file. This is done in the same manner that we described in the example above. When we are in the Audience Builder creation tool we switch to **Import subscriber list** in the top tab menu. We are presented with an interface that allows us to upload the desired file.
![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/import-subs.gif)

#### Audience segment picker
As described above we can use the Audience segment picker to select exsiting audience segments or create new ones. We select an audience by clicking on it but we can also hover over the question mark icon to display the audience size and summary for said audience segment. The icon on the rights indicates if the audience segment is either a built segment(users icon) or an imported list of subscribers(upload icon). 

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/Segmentation-Picker.png)

We can also edit built audience segments by clicking on the pencil icon. This redirects us again to the audience builder creation tool where we save the changes and are redirected back.

#### Audience Builder List
While we can create and manage our audience segments through the mentioned Audience picker, we can also manage and create audience segment in the Audience Builder view. We can find this in the top main menu.

When we click on this we are presented with **list** of all of our Audience segments in a table. Here we can view, search, create, edit and delete our Audience segments. When creating and editing audience segment from this view we will be redirected back to this list after we save our changes.

![Audience Builder Default](https://raw.githubusercontent.com/tvbeat/public/master/docs/img/audience-builder-list.gif)


