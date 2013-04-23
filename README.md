kohana-twig
===========

Kohana-twig is a [Kohana][1] 3.3 module for the popular [Twig][2] template
engine. It was designed to offer the full capabilities of Twig with a strong
focus on operating within the guidelines and best practices of the Kohana
framework. This module provides a way to use Twigs exactly as Kohana [Views][3]
are used, and it uses a custom Twig Loader to locate Twig template files in the
[Cascading Filesystem][4].

Installation
------------

First, clone this project from your `MODPATH/` directory:

	cd modules/
	git clone git://github.com/tommcdo/kohana-twig.git twig

Then, enable the module in `APPPATH/bootstrap.php` by adding it to the modules
initialization:

	Kohana::modules(array(
		// ... all your other modules ...
		'twig'       => MODPATH.'twig',       // Twig templating engine
	));

This module was designed for Kohana 3.3, but can be easily made to work with
Kohana 3.2 by changing all filenames within the `classes/` directory to
lowercase.

Usage
-----

Use Twigs just as you use would use Kohana Views. By default, your Twig files
go into the `twigs` directory anywhere in the cascading filesystem, and have
a `.html` extension. (Both of these settings can be configured.) For example,
suppose you have a Twig file at `APPPATH/twigs/main.html`, with contents:

	<p>Hello, {{ name }}</p>

Inside your action, you would attach the Twig as follows:

	$twig = Twig::factory('main');
	$twig->name = 'Tom';
	$this->response->body($twig);

Your Twig files can also references other templates by name, which will be
located using the cascading filesystem.

For more information on Twig templates, see [Twig for Template Designers][5]

Configuration
-------------

Default configuration is kept in `MODPATH/twig/config/twig.php`. To override
it, you can create a config file at `APPPATH/config/twig.php` (or in the
`config/` directory of any module that gets loaded before this one) that
specifies values to any options you'd like to change.

[1]: http://kohanaframework.org
[2]: http://twig.sensiolabs.org
[3]: http://kohanaframework.org/3.3/guide/kohana/mvc/views
[4]: http://kohanaframework.org/3.3/guide/kohana/files
[5]: http://twig.sensiolabs.org/doc/templates.html
