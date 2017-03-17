Image upload handler
=======================
This functionality came from the idea of repetitive patterns of images that every website uses. The most important one is the website logo.
With this image upload handler you can easily upload your website logo and change/use it dynamically.


How to use upload a logo?
******************************
First, you need to go to the Wordpress admin menu and look for Appearance > Logo, inside this menu you will see a few fields. On the "Logo" field, you must first click the "Upload Logo" button and upload the desired image.
Then click on "CHOOSE AS LOGO!". After that you will see a preview of the new logo. Finally, press Save Changes.

How to call a logo dynamically on my website
****************************************************
To do this, wherever you have your img tag for your logo (usually on your header.php file) you need to change its src attribute for the following line of code:
.. code-block:: php
	<?php if ( $athelas_options['logo'] != '' ): ?>
        <h1><a href="<?= home_url() ?>"><img src="<?php echo $athelas_options['logo']; ?>" alt=""></a></h1>
    <?php endif; ?>