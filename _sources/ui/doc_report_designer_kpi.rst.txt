

==========================
Report Designer/KPI
==========================

A KPI is a grid-oriented report part that displays a combination of simple metrics, images, and text in a more flexible layout. Users will be able to dynamically place various tiles along a grid for organization.

Configuring a KPI revolves around three areas:
    - Report Part Properties
        - Used for configuring the structure of the KPI layout and setting a background image
    - Field Properties
        - Used to manipulate the field-based data being displayed in the KPI
    - Tile Propertes
        - Used to alter/edit the values for text and image tiles within the KPI


Report Part Properties
------------------------------------------

#. Select KPI in the report body (See :ref:`Manage_Report_Parts` for how to
   add a chart).
#. Select the vertical Report Part Properties box.
#. The properties are listed in 3 sections  

    -  General Info
        - This dropdown allows the user to specify what gauge type they want for their metrics
        - Upon initial release, this only supports Simple Gauges 
    -  KPI
        - This pop-up will let users supply a background image by providing the URL
        - If the image is too large, they can crop a specific area of the image to use as the background
    -  View
        - These controls let users dictate the dimensions of the KPI grid as well as the pixel size of each cell
        - The Data Refresh option lets users determine how often an opened report will update the display data


Field Properties
----------------

#. Drag a field into the 'Values' container of the KPI
#. Select the vertical Field Properties box
#. The properties are listed in two sections

    - Data Source
        - This section shows information about the underlying data source chosen for the KPI
        - An alias can also be applied to the selected field
    - Data Formatting
        - Users can apply a specific function to the selected field, such as a Sum or Count
        - Users can apply a specific format to the selected field, such as various currency formats and comma notation
        - Users can set up rules for dynamic conditional formating to color the text based on the underlying values
        - Users can set up rules for dynamic text replacement to display unique value if certain conditions are met


Tile Properties
---------------

#. Left-click onto any empty cell on the KPI grid
#. Select the desired tile: Image, Metric, or Text
#. Select the vertical Tile Properties box.
#. The properties are listed into different sections for each tile type

    - Metric Tiles
        - Border
            - Users can apply a border to the metric tile to separate it from the rest of the KPI content.
        - Format
            - Users can apply basic text formatting to the gauge value such as font, styling, and color values.
        - Custom URL
            - Users can define a unique interaction to take place when a user clicks on the gauge value
    - Text Tiles
        - Border
            - Users can apply a border to their text tile to separate it from the rest of the KPI content.
        - Format
            - Users can apply various text formatting options to their content such as font, styling, color values, and alignment.
        - Data Formatting
            - Users can define a unique interaction to take place when a user clicks on the text content of the cell.
    - Image Tiles
        - Format
            - Users can supply a URL that the Izenda service can access that contains an image they would like to place in the KPI.
            - The image will fit into the box while maintaining the aspect ratio.
        - Data Formatting
            - Users can define a unique interaction to take place when a user clicks on their image cell.



Things to Consider
------------

- Field Properties will override certain tile properties set for the Metric Tile.
    - For example, if you format the Metric Tile to use red font, but set up conditional formatting to show green font, the green font will be shown when those conditions are met.
- The smallest number of rows and columns that can be set is 4, meansing that a 4x4 grid is the smallest body a KPI can have
- The Cell Size represents the number of pixels contained within a cell, with 15 being the smallest that can be set. There is no maximum value that can be set.
- Use of the Data Refresh Interval setting will only update the metric tile's content.
- Resetting the image crop modal will reset the image to the original state when the modal was opened, not the original state of the image.