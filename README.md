# Magento2 startup theme
Basic set of files to enable a new Magento2 theme in admin. This guide refers to Magento 2.1 version.


# Installation Instructions

Clone this repo and edit the configuration as follow:

## /theme.xml *
As mentioned in the [Magento 2.1 doc](http://devdocs.magento.com/guides/v2.1/frontend-dev-guide/themes/theme-structure.html) this file is mandatory and contains the basic info of your theme.
You need to edit this line

```
<title>Theme name</title>
```

with the name of your theme.
You can even change the path of the preview image, if needed.

## /media/preview.jpg
This image will appear in the themes' list in the admin area. You'll need to create a screenshot of your theme of 588x588px, that is Luma and the blank theme image format so I suggest you to do the same.

## /registration.php *
Another mandatory file needed to register your theme to the system.
Here you need to modify the following:

```
...
'frontend/Bitbull/startuptheme',
...
```
with your vendor name and theme code like this:

```
...
'frontend/<vendor>/<theme>',
...
```
as explained in the [Create a storefront theme](http://devdocs.magento.com/guides/v2.1/frontend-dev-guide/themes/theme-create.html) section of the doc.

## /composer.json
Keep this file if your theme is a Composer package.
Edit the name of the package

```
"name": "bitbull/theme-frontend-bitbull-startup"
```

setting your correct vendor and project name (your theme, in this case) like this:

```
"name": "<vendor>/<project-name>"
```

This name will be used in the composer.json of your Magento2 installation to add it as dependency.

Pay attention that the dependecies' versions of `magento/theme-frontend-blank` and `magento/framework` must refer to the correct versions used in the [composer.json of Magento/Framework module](https://github.com/magento/magento2/blob/2.1/lib/internal/Magento/Framework/composer.json) and the [composer.json of Magento/Blank theme](https://github.com/magento/magento2/blob/2.1/app/design/frontend/Magento/blank/composer.json) of the Magento2 current version used. You can easily know it by switching the branch on the desired tag.

## /Magento_Theme/layout/default.xml
This is not mandatory, but you may want to use this file if your theme is not based on any parent theme or just to change the path (or format only) of your theme's logo ([other cases can be found on the doc](http://devdocs.magento.com/guides/v2.1/frontend-dev-guide/themes/theme-create.html#theme_logo)).
So you'll probably want to review this lines:

```
<argument name="logo_file" xsi:type="string">images/logo-bitbull.png</argument>
<argument name="logo_img_width" xsi:type="number">480</argument>
<argument name="logo_img_height" xsi:type="number">310</argument>
```
adjusting it with your correct logo path and format.

Consider that, if you add in `/web/images/` an image named logo.svg that has the same format of the parent theme on which is based yours, you won't need this file.

## /web/images/logo-bitbull.png
Arf, Arf! This image file is just for instance. Delete it and add your correct logo image.
Consider that if there is already a logo uploaded in the admin panel this will override the one specified in the `/Magento_Theme/layout/default.xml` file. Everything else not set up in the admin panel, for instance the format, will fallback onto the settings written in this file.

## /etc/view.xml (*)
This file is required for a theme, but optional if exists in the parent theme.
The file contains images configuration for all storefront product images and thumbnails and in this repo version the file used is just the same you can find in the blank theme.


#Licence

[OSL - Open Software Licence 3.0](http://opensource.org/licenses/osl-3.0.php)


#Developers

Lorena Ramonda (@mobiledesignah): http://www.bitbull.it


# Copyright

(c) 2017 Bitbull Srl