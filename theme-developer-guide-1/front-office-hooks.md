# Front Office Hooks

This section of the documentation is only about front office hooks: display and action.

## All Hooks <a id="FrontOfficeHooks-AllHooks"></a>

The full list is regularly published on the Build devblog. Here is the latest.

## Creating a custom hook <a id="FrontOfficeHooks-Creatingacustomhook"></a>

### Creating a dynamic hook <a id="FrontOfficeHooks-Creatingadynamichook"></a>

When your module or theme calls a hook, PrestaShop executes it.

From a regular PHP file:

```text
Hook::exec('MyCustomHook');
```

From a Smarty template:

```text
{hook h='MyCustomHook'} 
```

### Making your hook visible and reusable <a id="FrontOfficeHooks-Makingyourhookvisibleandreusable"></a>

If you want the user to be able to see your hook in PrestaShop’s Position page \(in the back office\), it has to be registered.

You can register your hook from your theme’s theme.yml file:

```text
global_settings:
  hooks:
    custom_hooks:
      - name: displayFooterBefore
        title: displayFooterBefore
        description: Add a widget area above the footer
```

You can also register your hook from a module.

