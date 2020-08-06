# Building listing pages

Your catalog is mostly 2 things: a list of product and a detailed product page.

This section covers the listing pages, which includes: category, search result, products per brand, best seller list, new product list and so on.

In order to reduce code duplication, the only necessary template is the file `catalog/listing/product-list.tpl`.

## Extending product-list template <a id="Buildinglistingpages-Extendingproduct-listtemplate"></a>

We already covered how prestashop chooses the right template to use, so we know that the category template extends the product-list template.

We already covered how the template inheritance allows you to redefine only small part of bigger template.

So basically you are all set to create a category template or a search result template that make much more than the product-list template!

## AJAX page update <a id="Buildinglistingpages-AJAXpageupdate"></a>

Your product list will change as the customer filters the result with faceted navigation or sorting options for instance.

One of the golden rule of Starter Theme and PrestaShop 1.7 is: **No presentation code duplication**. Hence we didn’t want to return JSON data about the result and let JavaScript rebuild the page.

We made the core generate the sub template part and return it to the client. In the end JavaScript is only used to the place the content of HTML placeholders.

Each Ajax call will regenerate the following templates:

* `catalog/_partials/products-top.tpl`
* `catalog/_partials/products.tpl`
* `catalog/_partials/products-bottom.tpl`

### How to update the view <a id="Buildinglistingpages-Howtoupdatetheview"></a>

PrestaShop will emit JavaScript events to let you know what to do something.

Example:

```text
import $ from 'jquery';
import prestashop from 'prestashop';
import 'velocity-animate';

$(document).ready(() => {
  prestashop.on('updateProductList', (data) => {
    updateProductListDOM(data);
  });
}

function updateProductListDOM (data) {
  $('#search_filters').replaceWith(data.rendered_facets);
  $('#js-active-search-filters').replaceWith(data.rendered_active_filters);
  $('#js-product-list-top').replaceWith(data.rendered_products_top);
  $('#js-product-list').replaceWith(data.rendered_products);
  $('#js-product-list-bottom').replaceWith(data.rendered_products_bottom);
}
```

