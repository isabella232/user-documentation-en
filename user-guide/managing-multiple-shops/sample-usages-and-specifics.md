# Sample Usages and Specifics

* [Sample Usages and Specifics](sample-usages-and-specifics.md#SampleUsagesandSpecifics-SampleUsagesandSpecifics)
  * [Managing a catalog in multistore mode](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Managingacataloginmultistoremode)
  * [Data exchange between stores](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Dataexchangebetweenstores)
    * [Duplicating data between stores](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Duplicatingdatabetweenstores)
    * [Sharing data between stores and store groups](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Sharingdatabetweenstoresandstoregroups)
    * [Sharing products and categories](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Sharingproductsandcategories)
    * [Sharing customers and customer groups](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Sharingcustomersandcustomergroups)
    * [Sharing orders](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Sharingorders)
    * [Using a different theme for each shop/shop group](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Usingadifferentthemeforeachshop/shopgroup)
    * [Using specific settings for each shop/shop group](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Usingspecificsettingsforeachshop/shopgroup)
  * [Managing pages in multistore mode](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Managingpagesinmultistoremode)
  * [Managing discounts in multistore mode](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Managingdiscountsinmultistoremode)
  * [Web-service and multistore](sample-usages-and-specifics.md#SampleUsagesandSpecifics-Web-serviceandmultistore)

## Managing a catalog in multistore mode <a id="SampleUsagesandSpecifics-Managingacataloginmultistoremode"></a>

In the multistore mode, some of the PrestaShop administration pages feature a prominent drop-down menu, titled "Multistore configuration for". This menu gives you the context of what you are doing: it enables you to set the shop or shop group to which the changes you are making are applied.

For instance, when creating a new product, the selection in this menu will determine whether the product will be available for all shops, only one shop group, or a single shop.

When editing a product, PrestaShop displays notifications to help you understand the scope of your changes. For instance, when editing a product while in the "Shop A" context, the notification will say "Warning, if you change the value of fields with an orange bullet, the value will be changed for all other shops for this product", with said orange bullet appearing on all the implicated fields, such as "Type of product", "Reference", the package's size, etc.

Likewise, if you change a product while in the "All shops" context or in the context of a shop group, some fields will be disabled: since they have a global impact, you cannot edit them. If you really need to edit this content, each field has a box that you can check to edit that field in all the shops under this context.

If you edit a disabled field, the product is created in all the shops of the context which do not already have it in their own catalog. Make sure to double check your context.

## Data exchange between stores <a id="SampleUsagesandSpecifics-Dataexchangebetweenstores"></a>

### Duplicating data between stores <a id="SampleUsagesandSpecifics-Duplicatingdatabetweenstores"></a>

Duplicated data in PrestaShop are set during the setup of any individual shop, by importing all or some of the content from an existing shop into the new one. The content that can be imported is varied: products, categories, employees, modules, cart rules, suppliers, etc. Data importation is done once and for all: once a store has been created, you cannot easily import data again from another store.

### Sharing data between stores and store groups <a id="SampleUsagesandSpecifics-Sharingdatabetweenstoresandstoregroups"></a>

Stores can share data. Shared data are fundamentally handled at the store group level: one of the important things to understand when dealing with PrestaShop's multistore mode is that all the stores within a store group can share the same details share data – or more precisely, three types of content: customers, available quantities, and orders. Once the store group is set, the sharing of data between its stores is mostly finished: while you can change the setting for the available product quantities, you cannot change the customers and orders settings anymore as soon as any store within the group as at least one customer or one order.

### Sharing products and categories <a id="SampleUsagesandSpecifics-Sharingproductsandcategories"></a>

When you create a new store within a group, you can choose to have all, or some, of the categories in the new store to be exact duplicates of the categories in any other store on your installation of PrestaShop.

When creating a category, either for a specific store or for all the stores in the PrestaShop installation, PrestaShop registers the category for all the stores – it is simply hidden from any store where it has not been set.

By associating the new stores with a given category, any change in this category will impact all the stores which are associated with it, even if the stores are from different store groups. You can, therefore, change the category's content once and for all from one place, including its products.

### Sharing customers and customer groups <a id="SampleUsagesandSpecifics-Sharingcustomersandcustomergroups"></a>

As indicated above, stores within the same store group can share clients: all you have to do it set the proper option when creating the store group.

Groups are less detailed: if you change one of the default customer group in one store, the change is applied to all the other stores, regardless of the store group.

If you want to have different customer groups for each store, you must create a new group and use the "Multistore configuration for" selector to associate the group with the current store or store group.

If the option "Share customers" has been disabled, then your customer list will need to be empty before you can enable this.

If you'd rather keep your customer list you can do the following:

* Go to your database management software such as phpMyAdmin.
* Search for the table `ps_customer`. It might be different, depending on your database prefix.
* Export this table.
* Empty the table. Do NOT drop it. If you do want to drop it, make sure you recreate the table afterward.
* Go back to the multistore settings for the shop group.
* Enable the "Share customers" option.
* Import the table.

Sharing customers between the shop group have now been enabled without the loss of customer information.

### Sharing orders <a id="SampleUsagesandSpecifics-Sharingorders"></a>

It is possible for stores within the same store group to share orders: all you have to do it set the proper option when creating the store group.

If the option "Share orders" has been disabled, then your order list will need to be empty before you can enable this.

If you'd rather keep your orders you can do the following:

* Go to your database management software such as phpMyAdmin.
* Search for the table `ps_order`. It might be different, depending on your database prefix.
* Export this table.
* Empty the table. Do NOT drop it. If you do want to drop it, make sure you recreate the table afterward.
* Go back to the multistore settings for the shop group.
* Enable the "Share orders" option.
* Import the table.

Sharing orders between the shop group have now been enabled without the loss of order information.

### Using a different theme for each shop/shop group <a id="SampleUsagesandSpecifics-Usingadifferentthemeforeachshop/shopgroup"></a>

Once a theme is installed on your PrestaShop, you can use the "Theme & Logo" page in the "Design" menu to change the theme of the current store, or of the current store group, depending on how the "Multistore configuration for" selector is set.

### Using specific settings for each shop/shop group <a id="SampleUsagesandSpecifics-Usingspecificsettingsforeachshop/shopgroup"></a>

"Multistore configuration for" selector is the go-to option when you want your changes to have an impact on a given store or set of stores. It should even be the first option to look at when an administration screen opens up, as PrestaShop will change the available options depending on the context you are in: store, store group or all stores.

This makes it possible for you to:

* Using different image formats for each shop/shop group
* Activating/configuring a module on a per-shop basis
* Positioning/displaying front office blocks on a per-shop basis
* ...and so much more!

## Managing pages in multistore mode <a id="SampleUsagesandSpecifics-Managingpagesinmultistoremode"></a>

When viewing the list of the content pages in the "All shops" context, all the pages from all shops are displayed. Likewise, when in a shop group context, the pages for all the shops in that group are displayed.

When creating a page in a shop group context, all the shops in this group will display this page, yet the page will be unique: editing it in one shop will apply the changes in all the shops from this group.  
On the creation page, a section appears with a list, indicating which ones will be impacted.

## Managing discounts in multistore mode <a id="SampleUsagesandSpecifics-Managingdiscountsinmultistoremode"></a>

When creating cart rules or catalog price rules in a multistore context, an additional condition is available, with which you can choose the shops on which the rule should be available.

## Web-service and multistore <a id="SampleUsagesandSpecifics-Web-serviceandmultistore"></a>

Access to the web-service is also highly configurable, both at the shop level and at the shop group level. When creating a web-service key, you can choose to associate it with all shop, some shop groups, or selected shops.

