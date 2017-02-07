Custom Options Pages
=======================
The idea of creating Custom Options Pages came from the need to organize repetitive patterns of information that most websites have. For example: contact information, social networks, website logo, fonts, theme colors, toggle sidebar, etc. What ever your user will need to custmize all over the site.

Oniros comes with one Page already created. This page is called General Information, there the wordpress user can update the business and social networks information of the company. 

You can also create more panels. In order to do that you can follow the codex instructions in: `https://codex.wordpress.org/Creating_Options_Pages <https://codex.wordpress.org/Creating_Options_Pages>`_ or go throw the next list of steps:

1. Create a new folder inside of includes/options folder, with the name of the new panel.
2. Create main.php and form.php and copy the content and adjust the function and variable names. Here some tips to do that: (EXPLICAR MAS A DETALLE)
3. Inside you Panel folder create a card folder with the name of the card you wish to create.
4. Inisde the card folder you just create add a new file called input_fields.php. You will include this file in the mail.php. 


have to create a new folder inside of includes/options folder. 

General Information
---------------------
In this panel the user can easily change the business and social networks information while it's still easy for the developers to configure and call the variables in the code.

