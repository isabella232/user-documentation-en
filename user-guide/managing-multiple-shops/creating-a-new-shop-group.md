# Creating a new shop group

Having shop groups enables you to share certain characteristics between the shops in that group: catalog, employees, carriers, modules, etc. It allows you to manage a set of shops as easily as you would a single shop, while still being able to fine-tune the details of each shop manually. Applying new parameters to all the shops in a group only requires a single action. When in multistore mode, a drop-down menu is available on most of the administration pages and enables you to filter your changes by shop or shop group.

Technically speaking, when selecting a shop group in the multistore drop-down menu, the displayed entities reflect the **union** of the entities pertaining to the shops in that group.

Generally speaking, parameters are applied to all the entities belonging to the selected entity in the multistore drop-down menu. This is explained in details later in this chapter.

Clicking the "Add a new shop group" button brings a form with few options but a lot of text: you should make sure to read each description from beginning to end, as they help you make a decision about these options. Since some are non-reversible \(you cannot disable them once they are enabled\), it is important to know exactly what you enable.

![](../../.gitbook/assets/57081985%20%281%29.png)

The available settings are:

* **Shop group name**. The name is private, customers will not see it. Still, make sure to use a telling name: the more shop groups you will have, the more you will need to be able to find a given group quickly. You can edit the name at any time.
* **Share customers**. _**Once enabled, you cannot disable this option**_. This is great when you want to allow your customers to use the same login credentials on all shops of this shop group.
* **Share available quantities to sell**. You can have different quantities of the same product for sale on your shops. With this option, all the shops from this group will share the same available quantity of products. This can make it easier to manage said quantities.
* **Share orders**. _**Once enabled, you cannot disable this option**_. This option can only be enabled if both "Share customers" and "Share available quantities to sell" options are enabled. With this option, customers who are logged in any shop from this group will be able to see their order history for all the shops in the group.
* **Status**. Choose to enable this group right away, or later. You can enable/disable a shop group at any time.  

Two shop groups cannot share customers, carts or orders.

Existing shop groups can be edited from the shop groups list on the "Multistore" front page: simply click on the "Edit" icon on the right of the shop's row to open the form. As expected, you cannot edit the "Share customers" and "Share orders" options.

