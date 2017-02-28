Custom Options Pages
=======================
The idea of creating Custom Options Pages came from the need to organize repetitive patterns of information that most websites have. For example: contact information, social networks, website logo, fonts, theme colors, toggle sidebar, etc. What ever your user will need to custmize all over the site.

Oniros comes with one Page already created. This page is called General Information, there the wordpress user can update the business and social networks information of the company. 

You can also create more panels. In order to do that you can follow the codex instructions in: `https://codex.wordpress.org/Creating_Options_Pages <https://codex.wordpress.org/Creating_Options_Pages>`_ or go throw the next list of steps:

1. Create a new folder inside of includes/options folder, with the name of the new panel.
2. Create main.php and form.php. Copy the content form general_information files and adjust the function and variable names. Here some tips to do that: (TODO)
3. Inside your Panel folder, create a card folder with the name of the card you wish to create.
4. Inisde the card folder you just created, add a new file called input_fields.php. You need to include this file in the main.php.



General Information
---------------------
In this panel the user can easily change the business and social networks information while it's still easy for the developers to configure and call the variables in the code.

How to edit default fields
++++++++++++++++++++++++++++++++
To do this, you need to go to /includes/options/general_information/
and open the folder of the option you want to edit. E.g: location / social_links .
Then you need to open the input_fields.php file. Inside that file you will see a bunch of functions which you can change easily.
This is an example of how one of those functions should look like:

.. code-block:: php
	function display_address_element()
	{
		?>
	    	<input type="text" name="address" id="address" value="<?php echo get_option('address'); ?>" />
	    <?php
	}
	
You should rename the function, but we recommend only changing this X word: display_X_element(){} to a word that describes your field (for an improved nomenclature and order). Then you can change the input field as you would normally change an html code. If you wonder about the php code inside the input, keep reading this article.

After this being done, you need to look for the next function, which is called display_theme_panel_location(){}
Inside, you will find a few methods, which will be shown below.

The **add_settings_section()** method:

.. code-block:: php
	function display_theme_panel_location()
	{
		 add_settings_section( $id, $title, $callback, $page );
	}

This method recieves the following parameters:

**$id**
(string) (required) String for use in the 'id' attribute of tags.
Default: None
**$title**
(string) (required) Title of the section.
Default: None
**$callback**
(string) (required) Function that fills the section with the desired content. The function should echo its output.
Default: None
**$page**
(string) (required) The menu page on which to display this section. Should match $menu_slug from Function Reference/add theme page



The **add_settings_field()** method:

.. code-block:: php
	function display_theme_panel_location()
	{
		 add_settings_field( $id, $title, $callback, $page, $section, $args );
	}

This method recieves the following parameters:

**$id**
(string) (required) String for use in the 'id' attribute of tags.
Default: None
**$title**
(string) (required) Title of the field.
Default: None
**$callback**
(string) (required) Function that fills the field with the desired inputs as part of the larger form. Passed a single argument, the **$args array. Name and id of the input should match the **$id given to this function. The function should echo its output.
Default: None
**$page**
(string) (required) The menu page on which to display this field. Should match $menu_slug from add_theme_page() or from do_settings_sections().
Default: None
**$section**
(string) (optional) The section of the settings page in which to show the box (default or a section you added with add_settings_section(), look at the page in the source to see what the existing ones are.)
Default: default
**$args**
(array) (optional) Additional arguments that are passed to the $callback function. The 'label_for' key/value pair can be used to format the field title like so: <label for="value">$title</label>.
Default: array()


Explaining this:
The first parameter should be the slug of your field, the second parameter should be the label for your field (which will be shown in the admin panel), the third parameter needs to be the name of the function that you already created for your field (see previous steps), the fourth parameter needs to be the last parameter of the add_settings_section method(see previous steps) and the last parameter needs to be the the id(first parameter) that you put into your add_settings_section method (see previous steps).


The **register_setting()** method:

.. code-block:: php
	function display_theme_panel_location()
	{
		 register_setting( $option_group, $option_name, $sanitize_callback );
	}

This method recieves the following parameters:

**$option_group**
(string) (required) A settings group name. Must exist prior to the register_setting call. This must match the group name in settings_fields()
Default: None
**$option_name**
(string) (required) The name of an option to sanitize and save.
Default: None
**$sanitize_callback**
(callback) (optional) A callback function that sanitizes the option's value.
Default: None

You need to use the last parameter of the "add_settings_field" as the first parameter of the "register_setting".
You need to use the first parameter of the "add_settings_field" as the second parameter of the "register_setting".

The **display_location_section_instructions()** method:

This function will display the desired text on the top of the card in the general information panel.

How to call option fields in Php
++++++++++++++++++++++++++++++++++++++

Doing this is pretty much simple, you just need to copy the following code and edit the parameter it recieves.

.. code-block:: php
	get_option(string $option, mixed $default = false);

Parameters:
**$option**
(string) (Required) Name of option to retrieve. Expected to not be SQL-escaped.
**$default**
(mixed) (Optional) Default value to return if the option does not exist.
Default value: false

The first parameter must be the last parameter of add_settings_field() (see previous steps) and the last parameter must be the first parameter of the add_Settings_field() (see previous steps).


Where do I find the General Options Panel in the Dashboard?
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Once you've done every single step correctly, you need to upload the files you've changed to your website. After that, you will see a new menu item in the wordpress admin bar (left bar). The position of this new menu item depends on the number you set on the last parameter of the method add_menu_page() inside the add_theme_menu_item() function, which you can find in the includes/options/general_information/main.php file. The highest the number, the above the menu item gets.