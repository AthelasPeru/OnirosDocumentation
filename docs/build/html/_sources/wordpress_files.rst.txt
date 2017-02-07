Wordpress Files
===================

Most of the files are self explanatory for a WP theme developer, also they include comments to help you get started.
We will only list the files and folders we structure in a particular way.


includes/
++++++++++++++++++++++++++++

This folder holds most of our custom templates and functions, we encourage you to dwelve into them and learn what they can do for you.


functions/
**************

All of these files can be included from **functions.php**, just uncomment the ones you require.

- **admin-tweaks-php**: Specific tweaks we made to the admin panel.
- **ajax.php**: Basic boilerplate and example for working with ajax.
- **customizer**: Functions that modify the theme customizer menu.
- **image-sizes.php**: Define you rtheme Image Sizes.
- **menu.php**: Define your wordpress availiable menu areas.
- **posttypes.php**: Use Oniros CLI or manually add Custom Post Types to your theme.
- **security**: Security Functions.
- **taxonomies**: Define Custom Taxonomies for your theme.
- **theme_support.php**: Add or uncomment theme support functions here.
- **translation_strings.php**: If you like to add translation strings manually, do it here.
- **tweaks.php**: Specific tweaks we make to themes.
- **utilities.php**: a class that holds most of our in agency used functions.
- **widgets**: Register your custom widgets/sidebars here, build them inside *includes/widgets/*.

templates/
*************

Frequently used templates we include using WP built-in *get_template_part* function.

- **icons.php**: Include all the Real Vavicon Generator favicons.
- **menu.php**: The main menu template.
- **mobile-menu.php**: The mobile main menu template.
- **searchform.php**: searchform template
- **sidebar.php**: also pretty self explainatory ;-) we just love to break our templates in commonly used parts.

widgets/
************

Build all of your custom build widgets here.

- **example.php**: Example of a company data Widget.