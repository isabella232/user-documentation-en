# Adding module links in the back-office side menu

**Compatibility:** PrestaShop 1.7.1.0+

On the PrestaShop back office, the links on the side menu are linked to AdminControllers and ModuleAdminController classes. The first ones come from the PrestaShop Core, but the second ones are defined by the modules. If you want to add a link to your ModuleAdminControllers in the back office sidebar, this guide is for you.

## Tabs registration <a id="Addingmodulelinksintheback-officesidemenu-Tabsregistration"></a>

In order to register new links, open your main module class.

We will now use a property called $tabs, storing an array of link details. Each of them contains a class \(= link\) to add in the side menu.

## How to define a tab in the menu <a id="Addingmodulelinksintheback-officesidemenu-Howtodefineatabinthemenu"></a>

Depending on the options you provide, your links won’t be displayed the same way:

* **class\_name**: Mandatory, this is the file called when the merchant will click on your link.
* **name**: Optional, this is the name displayed in the menu. If not provided, the class name is shown instead.
* **parent\_class\_name**: Optional if you want to display it in a subcategory. Go farther in this document to see available values.
* **icon**: Optional, will display an icon when the menu is reduced.

## How to add names and their translations to a tab <a id="Addingmodulelinksintheback-officesidemenu-Howtoaddnamesandtheirtranslationstoatab"></a>

Be default, your tab will be displayed in the menu with its **class name**. If you want to use something more explicit, you can set the **name** property.

### Option 1: Use the same name for all languages <a id="Addingmodulelinksintheback-officesidemenu-Option1:Usethesamenameforalllanguages"></a>

If you want to add the same name to all available and active languages available on the shop, just set the ‘name’ key with a single string:

|  |
| :--- |


### Option 2: Use a different name for each language <a id="Addingmodulelinksintheback-officesidemenu-Option2:Useadifferentnameforeachlanguage"></a>

You can also add your translations per locale \(ex.: fr-FR\) or per language \(ex.: fr\), both are valid.

If a language is installed on the shop but is not found in your translated names, it will be automatically associated to the first value of the array.

Hence, we advise you to define the English value first.

|  |
| :--- |


## Which parent to choose? <a id="Addingmodulelinksintheback-officesidemenu-Whichparenttochoose?"></a>

Here is the default structure of the side-menu from PrestaShop at the moment this page is written. You can choose an element from this list to use as a parent.

* AdminDashboard    
* SELL
  * AdminParentOrders
  *         AdminOrders
  *         AdminInvoices
  *         AdminSlip
  *         AdminDeliverySlip
  *         AdminCarts
  * AdminCatalog
*         AdminProducts
  *         AdminCategories
  *         AdminTracking
  *         AdminParentAttributesGroups
  *         AdminParentManufacturers
  *         AdminAttachments
  *         AdminParentCartRules
  * AdminParentCustomer
  *         AdminCustomers
  *         AdminAddresses
  *         AdminOutstanding
  * AdminParentCustomerThreads
  *         AdminCustomerThreads
  *         AdminOrderMessage
  *         AdminReturn
  * AdminStats
  * AdminStock
  *         AdminWarehouses
  *         AdminParentStockManagement
  *         AdminSupplyOrders
  *         AdminStockConfiguration
* IMPROVE
  * AdminParentModulesSf
  *         AdminModulesSf
  *         AdminModules
  *         AdminAddonsCatalog
  * AdminParentThemes
  *         AdminThemes
  *         AdminThemesCatalog
  *         AdminCmsContent
  *         AdminModulesPositions
  *         AdminImages
  *         AdminParentShipping
  *         AdminParentPayment
  * AdminInternational
  *         AdminParentLocalization
  *         AdminParentCountries
  *         AdminParentTaxes
  *         AdminTranslations
* CONFIGURE
  * ShopParameters
  *         AdminParentPreferences
  *         AdminParentOrderPreferences
  *         AdminPPreferences
  *         AdminParentCustomerPreferences
  *         AdminParentStores
  *         AdminParentMeta
  *         AdminParentSearchConf
  * AdminAdvancedParameters
  *         AdminInformation
  *         AdminPerformance
  *         AdminAdminPreferences
  *         AdminEmails
  *         AdminImport
  *         AdminParentEmployees
  *         AdminParentRequestSql
  *         AdminLogs
  *         AdminWebservice
  *         AdminShopGroup
  *         AdminShopUrl

## How to check the tabs registration <a id="Addingmodulelinksintheback-officesidemenu-Howtocheckthetabsregistration"></a>

Once you're done, just install \(or reset\) your module.

The $tabs property will be read from PrestaShop and the tabs will be automatically displayed on the side menu. They will stay as long as your module is installed.  


