# About JavaScript

PrestaShop 1.7 has reworked a lot of JavaScript code, almost rewriting everything.

It’s recommended to read more about PrestaShop assets management before continuing.

A default store loads a lot less files in 1.7 compared to 1.6, there are no specific files per page for instance. The 2 new important files you have to master are:

| File | Content |
| :--- | :--- |
| core.js | Loads Jquery2, makes Ajax calls, defines core method that all front-end should use |
| theme.js | Bundles all theme specific code and libraries |

## Events <a id="AboutJavaScript-Events"></a>

### Dispatch an event <a id="AboutJavaScript-Dispatchanevent"></a>

The best way to trigger an event is to use the `prestashop` object. Here is a simple example:

```text
prestashop.emit(
  'product updated',
  {
    dataForm: someSelector.serializeArray(),
    productOption: 3
  }
);
```

### Dispatched events <a id="AboutJavaScript-Dispatchedevents"></a>

PrestaShop will dispatch many events from `core.js`, which your code can rely on.

| Event Name | Description |
| :--- | :--- |
| updatedCart | On the cart page, every time something happens \(change quantity, remove product and so on\) the cart is reloaded by Ajax call. After the cart is updated, this event is triggered. |
| updatedAddressForm | In the address form, some input will trigger ajax calls to modify the form \(like country change\), after the form is updated, this event is triggered. |
| updatedDeliveryForm | During checkout, if the delivery address is modified, this event will be triggered. |
| changedCheckoutStep | Each checkout step **submission** will fire this event. |
| updateProductList | On every product list page \(category, search results, price drop and so on\), the list is updated via Ajax calls if you change filters or sorting options. Each time the DOM is reloaded with new product list, this event is triggered. |
| clickQuickView | If your theme handles it, this event will be triggered when use click on the quick-view link. |
| updateProduct | On the product page, selecting a new combination will reload the DOM via Ajax calls. After the update, this event is fired. |
| More events? | Contribute to the doc to describe more events! |

### Triggering delegated events <a id="AboutJavaScript-Triggeringdelegatedevents"></a>

We use event delegation to make sure that the events are still attached after the DOM was modified \(like after an ajax call\).

Here is a simple way to trigger a delegated event.

```text
var body = $('body'); // Our events are usually attached to the body

var event = jQuery.Event('click');
event.target = body.find('.js-theClassYouNeed');

body.trigger(event);
```

