==========================
Back-end Integration APIs
==========================

This list documents the .NET APIs used for Back-end Integration.

List of APIs
------------

.. list-table::
   :widths: 63 37
   :header-rows: 1

   * - Class and Method
     - Purpose
   * - **UserIntegrationConfig** in Izenda.BI.Logic.CustomConfiguration
     -
   * - .. container:: lpad2
   
          `public static Func<ValidateTokenArgs, ValidateTokenResult> ValidateToken`_
     - Hosting app hooks authorization logic for Izenda
   * - .. container:: lpad2
   
          `public static Func<GenerateAccessTokenArgs, string> GetAccessToken`_
     - Izenda requests hosting app to generate token based on userName/tenantId
   * - .. container:: lpad2
   
          `public static User AddOrUpdateUser(UserDetail user)`_
     - Hosting app can add/update user in Izenda
     
   * - **RoleIntegrationConfig** in Izenda.BI.Logic.CustomConfiguration
     -
   * - .. container:: lpad2
   
          `public static RoleDetail AddOrUpdateRole(RoleDetail role)`_
     - Hosting app can add/update role in Izenda

   * - .. container:: lpad2
   
          `public static RoleDetail AddRole(RoleDetail role)`_
     - Hosting app can add a role in Izenda (v2.6.16 or greater)
   * - .. container:: lpad2
   
          `public static bool HasRole(RoleDetail role)`_
     - Hosting app can check if the specified role exists. (v2.6.16 or greater)
     
   * - **TenantIntegrationConfig** in Izenda.BI.Logic.CustomConfiguration
     -
   * - .. container:: lpad2
   
          `public static Tenants AddOrUpdateTenant(Tenants tenant)`_
     - Hosting app can add/update tenant in Izenda
   * - .. container:: lpad2
   
          `public static Tenants AddTenant(Tenants tenant)`_
     - Hosting app can add tenant in Izenda (v2.6.16 or greater)
   * - .. container:: lpad2
   
          `public static bool HasTenant(Tenants tenant)`_
     - Hosting app can check if the specified Tenant exists (v2.6.16 or greater)
     
public static Func<ValidateTokenArgs, ValidateTokenResult> ValidateToken
----------------------------------------------------------------------------------------------


Hosting app hooks authorization logic for Izenda.

**Declaration**

    ``public static Func<ValidateTokenArgs, ValidateTokenResult> ValidateToken``

**Parameters**

    :doc:`/ref/models/ValidateTokenArgs`

**Return Value**

    :doc:`/ref/models/ValidateTokenResult`

**Samples**

.. code-block:: csharp

   using Izenda.BI.Logic.CustomConfiguration;
   using Izenda.BI.Framework.Models.DBStructure;
   using Izenda.BI.Framework.Models.UserManagement;
   
   // ..
   
   const string KEY = "SECRET";
   
   UserIntegrationConfig.ValidateToken = (ValidateTokenArgs args) =>
   {
      var serializedObject = Encrypt.DecryptString(args.AccessToken, KEY);
      var userInfo = Newtonsoft.Json.JsonConvert.DeserializeObject<Models.UserInfo>(serializedObject);
      return new ValidateTokenResult { UserName = userInfo.UserName, TenantUniqueName = userInfo.TenantUniqueName };
   };

public static Func<GenerateAccessTokenArgs, string> GetAccessToken
----------------------------------------------------------------------------------------------

Izenda requests hosting app to generate token based on
userName/tenantId.

**Declaration**

    ``public static Func<GenerateAccessTokenArgs, string> GetAccessToken``

**Parameters**

    :doc:`/ref/models/ValidateTokenArgs`

**Return Value**

    string

**Samples**

.. code-block:: csharp

   using Izenda.BI.Logic.CustomConfiguration;
   using Izenda.BI.Framework.Models.UserManagement;
   using System.Web;
   
   // ..
   
   const string KEY = "SECRET";
   
   UserIntegrationConfig.GetAccessToken = (GenerateAccessTokenArgs args) => {
      return KEY + HttpContext.Current.User.Identity.Name;
   };

public static User AddOrUpdateUser(UserDetail user)
----------------------------------------------------------------------------------------------

Hosting app can add/update user in Izenda.

**Declaration**

    ``public static User AddOrUpdateUser(UserDetail user)``

**Parameters**

    :doc:`/ref/models/UserDetail`

**Return Value**

    :doc:`/ref/models/User`

**Samples**

   .. code-block:: csharp

      using Izenda.BI.Logic.CustomConfiguration;
      using Izenda.BI.Framework.Models.DBStructure;
      
      // ..
      
      var izendaUser = new UserDetail()
      {
         UserName = "admin",
         EmailAddress = "admin@acme.com",
         FirstName = "John",
         LastName = "Doe",
         TenantDisplayId = string.Empty,
         Deleted = false,
         Active = true,
         SystemAdmin = true,
         Roles = new List<Role>()
      };
      
      UserIntegrationConfig.AddOrUpdateUser(izendaUser);

public static RoleDetail AddOrUpdateRole(RoleDetail role)
----------------------------------------------------------------------------------------------

Hosting app can add/update role in Izenda.

**Declaration**

    ``public static RoleDetail AddOrUpdateRole(RoleDetail role)``

**Parameters**

    :doc:`/ref/models/RoleDetail`

**Return Value**

    :doc:`/ref/models/RoleDetail`

**Samples**

    .. code-block:: csharp

       using Izenda.BI.Logic.CustomConfiguration;
       using Izenda.BI.Framework.Models.DBStructure;
       
       // ..
       
       var roleDetail = new RoleDetail()
       {
          Name = "Administrator",
          Active = true
       };
       
       RoleIntegrationConfig.AddOrUpdateRole(roleDetail);

public static RoleDetail AddRole(RoleDetail role)
----------------------------------------------------------------------------------------------

Hosting app add a role in Izenda.

**Declaration**

    ``public static RoleDetail AddRole(RoleDetail role)``

**Parameters**

    :doc:`/ref/models/RoleDetail`

**Return Value**

    :doc:`/ref/models/RoleDetail`

**Samples**

    .. code-block:: csharp

       using Izenda.BI.Logic.CustomConfiguration;
       using Izenda.BI.Framework.Models.DBStructure;
       
       // ..
       var roleDetail = new RoleDetail()
       {
            Name = "Administrator",
            Active = true,
            Permission = new Izenda.BI.Framework.Models.Permissions.Permission()
            {
                Emailing = new Izenda.BI.Framework.Models.Permissions.Emailing.Emailing()
                {
                    DeliveryMethod = new Izenda.BI.Framework.Models.Permissions.Emailing.DeliveryMethod()
                    {
                        Attachment = true,
                        EmbeddedHTML = true,
                        Link = true
                    }
                }
            }
       };

        RoleIntegrationConfig.AddRole(roleDetail);

public static bool HasRole(RoleDetail role)
----------------------------------------------------------------------------------------------
Hosting app can check if the specified role exists.

**Declaration**

    ``public static bool HasRole(RoleDetail role)``

**Parameters**

    :doc:`/ref/models/RoleDetail`

**Return Value**

    bool

**Samples**

    .. code-block:: csharp

       using Izenda.BI.Logic.CustomConfiguration;
       using Izenda.BI.Framework.Models.DBStructure;
       
       // ..
       
       var roleDetail = new RoleDetail()
        {
            Name = "Administrator"
        };

        RoleIntegrationConfig.HasRole(roleDetail);

public static Tenants AddOrUpdateTenant(Tenants tenant)
----------------------------------------------------------------------------------------------

Hosting app can add/update tenant in Izenda.

**Declaration**

    ``public static Tenants AddOrUpdateTenant(Tenants tenant)``

**Parameters**

    :doc:`/ref/models/Tenants`

**Return Value**

    :doc:`/ref/models/Tenants`

**Samples**

    .. code-block:: csharp

       using Izenda.BI.Logic.CustomConfiguration;
       using Izenda.BI.Framework.Models.DBStructure;
       
       // ..
       
       var izendaTenant = new Izenda.BI.Framework.Models.Tenants();
       izendaTenant.Active = true;
       izendaTenant.Deleted = false;
       izendaTenant.Name = "ACME Corp";
       izendaTenant.TenantID = "ACME";
       
       TenantIntegrationConfig.AddOrUpdateTenant(izendaTenant);

public static Tenants AddTenant(Tenants tenant)
----------------------------------------------------------------------------------------------
Hosting app can add tenant in Izenda.

**Declaration**

    ``public static Tenants AddTenant(Tenants tenant)``

**Parameters**

    :doc:`/ref/models/Tenants`

**Return Value**

    :doc:`/ref/models/Tenants`

**Samples**

    .. code-block:: csharp

       using Izenda.BI.Logic.CustomConfiguration;
       using Izenda.BI.Framework.Models.DBStructure;
       
       // ..
       
       var izendaTenant = new Izenda.BI.Framework.Models.Tenants();
       izendaTenant.Active = true;
       izendaTenant.Deleted = false;
       izendaTenant.Name = "ACME Corp";
       izendaTenant.TenantID = "ACME";
       
       TenantIntegrationConfig.AddTenant(izendaTenant);

public static bool HasTenant(Tenants tenant)
----------------------------------------------------------------------------------------------
Hosting app can check if the specified Tenant exists.

**Declaration**

    ``public static bool HasTenant(Tenants tenant)``

**Parameters**

    :doc:`/ref/models/Tenants`

**Return Value**

    bool

**Samples**

    .. code-block:: csharp

       using Izenda.BI.Logic.CustomConfiguration;
       using Izenda.BI.Framework.Models.DBStructure;
       
       // ..
       
       var acmeTenant = new Izenda.BI.Framework.Models.Tenants()
       {
          TenantID = "ACME"
       };

       TenantIntegrationConfig.HasTenant(acmeTenant);
	   

DLL References
--------------

-  Izenda.BI.Logic.dll for the methods
-  Izenda.BI.Framework.dll for the object models
