=====================
BI Portal Custom CSS
=====================

.. note::

   Whenever possible, we encourage you to adhere to the official CSS Guidelines for cascading styles. For the main styles, we recommend to make a copy of the izenda-us.css to modify and add the reference to the index.html.


Location of CSS
---------------

-  izenda-ui.css : Main location for CSS Stylings.



Customization (Simple)
----------------------

The simplest way to change an element’s color is to find the CSS
selector corresponding to an HTML element and replace the listed color
with your new color. In Notepad++ , this can be accomplished by pressing
CTRL + F and navigating to “Replace” tab.

.. figure::  /_static/images/FindDialogue.png
   :width: 482px

   Find Dialogue

.. note::

   For best practice, we recommend that you “Replace All” to maintain
   consistent look-and-feel.

Customization (Scalable)
------------------------

CSS Variables allow you to change one value in the CSS to change all of
our CSS selectors.

.. note::

   This solution is currently supported in Chrome and Firefox.

-  Add the following on top of izenda-ui.css

   .. figure::  /_static/images/Figure2.png


-  Replace all instances of #1c4e89 with var(--main-color).

   .. figure::  /_static/images/Figure3a.png
      :width: 485px


-  Example Replacement:

   .. figure::  /_static/images/Figure3b.png


-  Result on page.

   .. figure::  /_static/images/Figure4b.png

Key Styling Colors
------------------

Key styling for Chrome and Firefox is located in the file ``izenda-ui.css``. Below, we list 11 variables that will help
you stylize your application.

.. note::

   It is important to keep a record of each change, similar to the table
   below. This ensures that you can recreate your style if it’s
   unintentionally overwritten during an update.

.. list-table::
   :widths: 45 10 10 30 5
   :header-rows: 1
   :stub-columns: 1

   * - Identifier
     - Occurences
     - Initial color
     - Recommended |br| css variable
     - Color sample
   * - MAIN STYLE COLOR
     - 31
     - #1c4e89
     - --main-co
     - |1c4e89|
   * - SUB STYLE COLOR
     - 11
     - #10427c
     - --sub-style-co
     - |10427c|
   * - Fontello (note: |br| trivial design color)
     - 1
     - #b3cbda
     - --fontello-co
     - |b3cbda|
   * - Trans-color
     - 124
     - transparent
     - -trans-color
     - |transparent|
   * - Menu text and panel color
     - 138
     - #fff
     - --menu-text-and-panel-co
     - |fff|
   * - Panel Borders Color
     - 38
     - #EEE
     - --panel-border-co
     - |EEE|
   * - Main Background Color
     - 10
     - #e4e8eb
     - --main-bg-co
     - |e4e8eb|
   * - Search Icon And |br| Data Source Borders
     - 43
     - #DEDEDE
     - --search-ico-and-ds-borders
     - |DEDEDE|
   * - Report Part Edit-Mode |br| Tab Borders
     - 18
     - #ddd
     - -- rp-edit-mode-tab-borders
     - |ddd|
   * - Error Color #1
     - 12
     - #D0021B
     - -- error-1-co
     - |D0021B|
   * - Error Color #2
     - 7
     - Red
     -  -- error-2-co
     - |Red|


Example Color Changes
~~~~~~~~~~~~~~~~~~~~~

-  MAIN STYLE COLOR

   .. figure::  /_static/images/Figure4b.png

-  SUB STYLE COLOR

   .. figure::  /_static/images/Figure5.png

-  Trans-color

   .. figure::  /_static/images/Figure6.png

-  Menu text and panel color

   .. figure::  /_static/images/Figure7.png

-  Panel Borders Color

   .. figure::  /_static/images/Figure8.png

-  Main Background Color

   .. figure::  /_static/images/Figure9.png

-  Search Icon And Data Source Borders

   .. figure::  /_static/images/Figure10.png

Sample Code
~~~~~~~~~~~

The following code sample can be added to the top of your
izenda-ui.css . If you replace the color code provided in the
CSS comments with the name of the variable, the new color will be
applied. The results will be striking.

.. note::

   Remember, CSS variables are only supported in Chrome and Firefox.

.. code-block:: css

   root {
     --main-co: pink; /* #1c4e89 */
     --sub-style-co:green; /* #10427c */
     --fontello-co: #b3cbda; /* #b3cbda */
     --menu-text-and-panel-co: purple; /* #fff */
     --panel-border-co: indigo; /* #EEE */
     --main-bg-co: teal; /* #e4e8eb */
     --search-icon-and-data-source-borders: yellow; /* #DEDEDE */
     --rp-edit-mode-tab-borders: blue; /* #ddd */
     --error-1-co: pink; /* #D0021B */
     --error-2-co: yellow; /* red */
     --garfunkle: orange; /*Arbitrary variable created #f5f5f5 */
   }

Visually Editing CSS
--------------------

You would usually need to refresh the page to see updates to your
application. Fortunately, Chrome provides the functionality to edit the
working instance of a page’s CSS to see real-time changes. The following
example uses CSS Selectors.

.. note::

   This CSS instance is not saved when you
   edit it. If you break your CSS, simply reload the page and your sandbox
   will be refreshed. You will need to choose to save before refreshing
   your page.

-  To access Chrome’s Developer Tools, press F12 to open the console.

   .. figure::  /_static/images/Figure11.png

-  Toggle over to the Sources tab and locate the CSS file you wish to
   edit.

   .. figure::  /_static/images/Figure12.png

   .. note:: 

         To increase screen real-estate, you can pop the Developer Tool out
         into a separate window

-  Develop!

   .. figure::  /_static/images/Figure14.png

   .. figure::  /_static/images/Figure15.png

-  To save, right click on the file on left-hand panel and select save.

   .. figure::  /_static/images/Figure16.png

Other Helpful Tools
~~~~~~~~~~~~~~~~~~~

The following can be found in the Chrome Web Store for download.

-  CSS Viewer: Allows you to see the CSS applied to a particular
   element.

   .. figure::  /_static/images/Figure18.png


.. |1c4e89| raw:: html

   <div style="background: #1c4e89">&nbsp;&nbsp;</div>



.. |10427c| raw:: html

   <div style="background: #10427c">&nbsp;&nbsp;</div>



.. |b3cbda| raw:: html

   <div style="background: #b3cbda">&nbsp;&nbsp;</div>



.. |transparent| raw:: html

   <div style="background: transparent">&nbsp;&nbsp;</div>



.. |fff| raw:: html

   <div style="background: #fff">&nbsp;&nbsp;</div>



.. |EEE| raw:: html

   <div style="background: #EEE">&nbsp;&nbsp;</div>



.. |e4e8eb| raw:: html

   <div style="background: #e4e8eb">&nbsp;&nbsp;</div>



.. |DEDEDE| raw:: html

   <div style="background: #DEDEDE">&nbsp;&nbsp;</div>



.. |ddd| raw:: html

   <div style="background: #ddd">&nbsp;&nbsp;</div>



.. |D0021B| raw:: html

   <div style="background: #D0021B">&nbsp;&nbsp;</div>



.. |Red| raw:: html

   <div style="background: Red">&nbsp;&nbsp;</div>
