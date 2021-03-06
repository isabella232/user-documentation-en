# Migrating a module from 1.6 to 1.7

## BACKWARD COMPAT’ BROKEN: <a id="Migratingamodulefrom1.6to1.7-BACKWARDCOMPAT&#x2019;BROKEN:"></a>

* Payment module have changed, check [specific doc](creating-a-prestashop-1.7-payment-module.md).

## ENSURE: <a id="Migratingamodulefrom1.6to1.7-ENSURE:"></a>

* We changed all variables passed to smarty, make sure what you use is still assigned
* $link is deprecated \(even if it’s still passed to smarty, it will be removed at some point\), use {url} helper
* make sure your use the new way of calling templates: fetch\(module:modulename/views/template.tpl\)
* make sure you don't add your assets with hardcoded path in displayHeader hook \(no change but it’s bad\)
* Smarty is automatically escaped, so: 1. Remove all \|escape:’html’:’UTF-8’ \(FOR FRONT TEMPLATES ONLY\) 2. Add nofilter if you print html
* Only rely documented variables ! Any other variable my come from a module or just be a left over and might be removed at any time.
* If you use the backward\_compatibility package, check that PrestaShop version is 1.4 before importing it. With PrestaShop 1.7 you’ll get a fatal error

Note: many external libraries have been updated. Here is a list of some external extra doc about it:

* [https://github.com/yellowtree/wp-geoip-detect/wiki/How-to-migrate-from-v1-to-v2](https://github.com/yellowtree/wp-geoip-detect/wiki/How-to-migrate-from-v1-to-v2)

## How to make a module compatible with 1.6 AND 1.7 <a id="Migratingamodulefrom1.6to1.7-Howtomakeamodulecompatiblewith1.6AND1.7"></a>

* Use legacy translation system \($this-&gt;l\)
* Use 2 templates different depending on the version
* Implements getWidgetVariables and renderWidget but dont explicitly implements the php interface.
* Create all specific hook method like hookDisplayHeader and call renderWidget with the correct parameters

