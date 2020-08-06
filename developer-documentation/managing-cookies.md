# Managing Cookies

PrestaShop uses encrypted cookies to store all the session information, for visitors/clients as well as for employees/administrators.

The Cookie class \(`/classes/Cookie.php`\) is used to read and write cookies.

In order to access the cookies from within PrestaShop code, you can use this:

```text
$this->context->cookie;
```

All the information stored within a cookie is available using this code:

```text
$this->context->cookie->variable;
```

If you need to access the PrestaShop cookie from non-PrestaShop code, you can use this code:

```text
include_once('path_to_prestashop/config/config.inc.php');
include_once('path_to_prestashop/config/settings.inc.php');
include_once('path_to_prestashop/classes/Cookie.php');
$cookie = new Cookie('ps'); // Use "psAdmin" to read an employee's cookie.
```

## Data stored in a visitor/client’s cookie <a id="ManagingCookies-Datastoredinavisitor/client&#x2019;scookie"></a>

| Token | Description |
| :--- | :--- |
| date\_add | The date and time the cookie was created \(in YYYY-MM-DD HH:MM:SS format\). |
| id\_lang | The ID of the selected language. |
| id\_currency | The ID of the selected currency. |
| last\_visited\_category | The ID of the last visited category of product listings. |
| ajax\_blockcart\_display | Whether the cart block is “expanded” or “collapsed”. |
| viewed | The IDs of recently viewed products as a comma-separate d list. |
| id\_wishlist | The ID of the current wishlist displayed in the wishlist block. |
| checkedTOS | Whether the “Terms of service” checkbox has been ticked \(1 if it has and 0 if it hasn’t\). |
| id\_guest | The guest ID of the visitor when not logged in. |
| id\_connections | The connection ID of the visitor’s current session. |
| id\_customer | The customer ID of the visitor when logged in. |
| customer\_lastname | The last name of the customer. |
| customer\_firstname | The first name of the customer. |
| logged | Whether the customer is logged in. |
| passwd | The MD5 hash of the `_COOKIE_KEY_  in config/settings.inc.php` and the password the customer used to log in. |
| email | The email address that the customer used to log in. |
| id\_cart | The ID of the current cart displayed in the cart block. |
| checksum | The Blowfish checksum used to determine whether the cookie has been modified by a third party. The customer will be logged out and the cookie deleted if the checksum doesn’t match. |

## Data stored in an employee/administrator’s cookie <a id="ManagingCookies-Datastoredinanemployee/administrator&#x2019;scookie"></a>

| Token | Description |
| :--- | :--- |
| date\_a dd | The date and time the cookie was created \(in YYYY-MM-DD HH:MM:SS format\). |
| id\_lang | The ID of the selected language. |
| id\_employee | The ID of the employee. |
| lastname | The last name of the employee. |
| firstname | The first name of the employee. |
| email | The email address the employee used to log in. |
| profile | The ID of the profile that determines which tabs the employee can access. |
| passwd | The MD5 hash of the `_COOKIE_KEY_  in config/settings.inc.php` and the password the employee used to log in. |
| checksum | The Blowfish checksum used to determine whether the cookie has been modified by a third party. If the checksum doesn’t match, the customer will be logged out and the cookie is deleted. |

