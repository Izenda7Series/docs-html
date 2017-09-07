=================================
Exporting
=================================
|

Charts and other visualizations are not rendered in exports
-----------------------------------------------------------------

This issue can occur if the WebUrl value in the IzendaSystemSetting table is empty or not set correctly. You may receive an error in the Izenda log similar to the example below:

.. code-block:: python
   :emphasize-lines: 2
   
	2017-01-11 8:22:21,222 [47  ][ERROR][ExportingLogic                      ] Convert to image: ReportId=eeb95aa2-452d-448d-b6f5-6b1698407ef0, ReportPartId=b3d214b6-1d16-4f37-a312-33695d23ecb5 
	ImageUrl=/viewer/reportpart/b3d214b6-1d16-4f37-a312-33695d23ecb5?hideTitle=true&print=true&width=1080&height=360&token={your token}&draftId=3d55afd4-c7b2-4e5a-b55d-c488c93cce8b&reportPartName=Chart&tenantId=
	System.Exception: HTML load error. The remote content was not found at the server - HTTP error 404
	  at EvoPdf.HtmlToImageConverter.?(String A_0, Boolean A_1, ?& A_2, Boolean A_3, Boolean A_4, Boolean A_5)
	  at EvoPdf.HtmlToImageConverter.ConvertUrlToImageObject(String url)
	  at EvoPdf.HtmlToImageConverter.ConvertUrl(String url, ImageFormat format)
	  at Izenda.BI.Exporting.ExportHelper.ConvertToImage(ExportSetting setting, ExportData data, Int32 width, Int32 height, Object separatorValue)


In this case, the ImageUrl path is not complete. The Izenda API will make a request to the Front-End in order to render the graphics needed for the export. Try updating the WebUrl value in the IzendaSystemSetting table with the URL for your front-end. 

==================   ============
Name                 		Value
==================   ============
WebUrl        				http://localhost/
==================   ============


You can use the script below to accomplish this. 

.. code-block:: sql

	-- This is a MSSQL snippet, you may need to adjust the query for other databases.
	UPDATE [IzendaSystemSetting]
	SET [Value] = '<your url here including the trailing slash>'
	WHERE [Name] = 'WebUrl'


.. Warning::

   As general best practice, we recommend backing up your database before making any manual updates.
   
If you still encounter errors, try manually browsing to the ImageURL path specified in the log file. If you are in an integrated kit, you may need to adjust your application routing.

|

Exporting not working in Azure environments
----------------------------------------------------
If you are using an Azure website, or similar service the default exporting provider for Izenda will not work properly due to 
restrictions imposed by Azure App Services environment. Please consult our guide to configure `Pdf Exports in Azure Websites <https://www.izenda.com/docs/install/supplementary_guides/doc_azure_evo.html>`__.



