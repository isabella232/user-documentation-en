# Notifications

Throughout the whole front office, the customer can receive notification messages from PrestaShop, to inform her about successes or errors for instance. Your theme can too send notifications when certain events occur.

The notification messages are not hardcoded in the template files, but are sent from the controller, so that you have consistency in case you update/change your theme. Also, this way there is a better chance that all notification messages are already translated into your language!

## Types of notifications <a id="Notifications-Typesofnotifications"></a>

An array of notification is passed to the templates, containing at least one of these:

| success | An action was performed and everything went well. |
| :--- | :--- |
| error | Something went wrong. |
| warning | Important notice the merchant should know about. |
| info | “just so you know”. |

## How to display notifications <a id="Notifications-Howtodisplaynotifications"></a>

In the Starter Theme, [notifications are implemented as a partial template file](https://github.com/PrestaShop/StarterTheme/blob/develop/templates/_partials/notifications.tpl):

```text
<aside id="notifications">
  <div class="container">
    {if $notifications.error}
      <article class="alert alert-danger" role="alert">
        <ul>
          {foreach $notifications.error as $notif}
            <li>{$notif}</li>
          {/foreach}
        </ul>
      </article>
    {/if}

    {if $notifications.warning}
      <article class="alert alert-warning" role="alert">
        <ul>
          {foreach $notifications.warning as $notif}
            <li>{$notif}</li>
          {/foreach}
        </ul>
      </article>
    {/if}

    {if $notifications.success}
      <article class="alert alert-success" role="alert">
        <ul>
          {foreach $notifications.success as $notif}
            <li>{$notif}</li>
          {/foreach}
        </ul>
      </article>
    {/if}

    {if $notifications.info}
      <article class="alert alert-info" role="alert">
        <ul>
          {foreach $notifications.info as $notif}
            <li>{$notif}</li>
          {/foreach}
        </ul>
      </article>
    {/if}
  </div>
</aside>
```

…and are then [included in the template file](https://github.com/PrestaShop/StarterTheme/blob/1.7.2.x/templates/checkout/checkout.tpl#L42-L44):

```text
{block name='notifications'}
  {include file='_partials/notifications.tpl'}
{/block}
```

## Add your own message in your front controller <a id="Notifications-Addyourownmessageinyourfrontcontroller"></a>

Your front controller holds [the 4 following variables](https://github.com/PrestaShop/PrestaShop/blob/1.7.1.x/classes/controller/FrontController.php#L667-L689):

* `$this->error`
* `$this->success`
* `$this->warning`
* `$this->danger`

They are PHP arrays, and they hold messages as a string.

Since PrestaShop 1.7, you can [redirect the customer AND display a message after an action](https://github.com/PrestaShop/PrestaShop/blob/1.7.1.x/classes/controller/FrontController.php#L597-L616).

