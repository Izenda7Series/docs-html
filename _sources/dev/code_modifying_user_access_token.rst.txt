===========================
Modifying User Access Token
===========================

This article contains information on how to create custom properties and logic using the user's access token. Custom properties can be useful for adding conditions to determine whether a user's token is valid or for implementing hidden filters. Below is a general guide of how to perform these tasks. Note that this guide is not applicable to deployment mode 0.


Adding a custom property to the User Info
-----------------------------------------
You can add your own custom property to the application's UserInfo object, which is used to create the access token. Please note that this model is different from the User object native within Izenda.

   .. code-block:: csharp

      public class UserInfo
      {
         public string UserName { get; set; }

         // This corresponds to the 'TenantID' field in the IzendaTenant table
         public string TenantUniqueName { get; set; }

         // add a custom property
         public string FavoriteGroup { get; set; }

         // default constructor
         public UserInfo()
         {
            //Set our custom property for now, but in the future this can be set in a different place
            FavoriteGroup = "ID";
         }
      }

After modifying the UserInfo object definition in your integrated environment, the new property can be set in various ways in your code. Below is an example of setting the property using the GenerateToken method.

   .. code-block:: csharp

      [HttpGet]
      [Authorize]
      public ActionResult GenerateToken()
      {
         var username = User.Identity.GetUserName();
         var tenantName = ((System.Security.Claims.ClaimsIdentity)User.Identity).FindFirstValue("tenantName");
         var favoriteGroup = ((System.Security.Claims.ClaimsIdentity)User.Identity).FindFirstValue("favoriteGroup");
         
         var user = new UserInfo { UserName = username, TenantUniqueName = tenantName, FavoriteGroup = favoriteGroup };
         var token = IzendaBoundary.IzendaTokenAuthorization.GetToken(user);
         return Json(new { token = token }, JsonRequestBehavior.AllowGet);
      }

In the above example, we are obtaining the value from the ClaimsIdentity used inside the application. Such a claim can be set when the user logs in or after selecting a specific option. Then any time the user accesses Izenda, the FavoriteGroup property in the UserInfo will be set and integrated into the access token. The FavoriteGroup property can then be used in the ValidateIzendaAuthToken route to perform custom logic.


Adding decryption logic to IAdHocExtension
-----------------------------------------
If you are running a deployment mode 1 or 2 solution, you will need to add the same decryption logic used to decrypt the access token within the application to the IAdHocExtension solution. In this example, we will use the IzendaBoundary resources from the MVC5 starter kit. If you are running a deployment mode 3 solution, the IzendaBoundary resources and IAdHocExtension class will exist in the same solution and will thus be available in all contexts.

*  If you are using the IAdHocExtension sample from the github repository, copy IzendaTokenAuthorization.cs, StringCipher.cs, and UserInfo.cs (located in the models sub-folder) from the IzendaBoundary folder in your MVC5 starter kit. You may need to change the namespaces on these files.

   *  IzendaTokenAuthorization.cs requires the Newtonsoft.Json NuGet package, so you will need to add the package to your IAdHocExtension solution (ensure it's the same version as the one in the bin/Web.config of your MVC5 starter kit)
   *  Add a reference to System.Configuration


Retrieving the access token properties from the hidden filter method
-------------------------------------------------------------------
You can now retrieve the access_token from the UserContext and decrypt it to view the custom property.

   .. code-block:: csharp

      public override ReportFilterSetting SetHiddenFilters(SetHiddenFilterParam param)
      {
         // Get the current user's access token
         var currentAccessToken = UserContext.Current.CurrentUser.CurrentAccessToken;

         // Get the UserInfo from the current access token
         var userInfo = IzendaTokenAuthorization.GetUserInfo(currentAccessToken);

         // Retrieve the custom value
         var myFavoriteGroup = userInfo.FavoriteGroup;

         //[...Hidden Filter Logic...]
      }

Once you have decrypted the access token into a UserInfo object, you can use it in many different ways. We have only explored one example of a way the custom property can be retrieved and utilized to create custom behavior in Izenda. The goal of this exercise was to serve as a jumping off point for the basics. More complex behaviors can be derived from this sample as needed.