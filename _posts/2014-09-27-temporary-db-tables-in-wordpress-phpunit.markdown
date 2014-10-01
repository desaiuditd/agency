---
layout: post
status: publish
published: true
title: Temporary DB tables in WordPress PhpUnit
author:
  display_name: Udit Desai
  login: desaiuditd
  email: desaiuditd@gmail.com
  url: http://about.me/desaiuditd
author_login: desaiuditd
author_email: desaiuditd@gmail.com
author_url: http://about.me/desaiuditd
wordpress_id: 279
wordpress_url: http://blog.incognitech.in/?p=279
date: '2014-09-27 11:23:41 -0400'
date_gmt: '2014-09-27 05:38:41 -0400'
categories:
- Tech
tags:
- WordPress
- PhpUnit
- Testing
- Tescases
- Database
- MySQL
comments: []
---

When we set up [WordPress-PhpUnit Environment](https://make.wordpress.org/core/handbook/automated-testing?), to automate test-cases for our plugin/theme (mainly plugins, I've not come across any WP theme which has test cases written for it), we either set it up [manually](http://ben.lobaugh.net/blog/84669/how-to-add-unit-testing-and-continuous-integration-to-your-wordpress-plugin) or we take help of [WP-CLI](https://github.com/wp-cli/wp-cli/wiki/Plugin-Unit-Tests) to build the scaffolding of our plugin. WordPress has an amazing [testcase wrapper class](https://develop.svn.wordpress.org/trunk/tests/phpunit/includes/testcase.php) for PhpUnit that can be used when we make out plugin testable.

Of course, when our plugin does not deal with database then we do not have to worry about as our plugin will only make use of the readily available tables of WordPress and there will not be any need to introduce new database tables. But if we deal with database tables through our plugin then we need these tables when we perform test-cases using PhpUnit. [wpdb](http://codex.wordpress.org/Class_Reference/wpdb) & [dbDelta](http://codex.wordpress.org/Creating_Tables_with_Plugins) gives you enough power to play with database tables in your plugin. But when we are in PhpUnit environment, schematics are a bit different. WordPress testcase wrapper creates temporary DB tables in WordPress PhpUnit environment. What this means is when we execute test-cases for our plugin, the built-in wrapper class - mentioned before - tells WordPress to create temporary (virtual) tables in MySql and NOT permanent (actual) tables ([Reference](https:&#47;&#47;core.trac.wordpress.org&#47;changeset&#47;27041&#47;trunk&#47;tests&#47;phpunit&#47;includes&#47;testcase.php)). Because of this, your test-cases related DB tables will only exist during the PhpUnit execution. They will be destroyed from the memory.

The sole purpose of such mechanism is to keep the test data away from the database and not bloat the memory with corrupt data, keeping the database intact. If this is the case then you're good to go; but there are times when we can't move ahead and believe that everything is working absolutely fine until we see the actual results :wink:. We might need those database table to retain its state even after the PhpUnit execution. In that case we can use following solution:

Override `setUp` method of `WP_UnitTestCase` class in your own testcase class. The method definition should look as follows:

    function setUp() {
        // Perform the actual task according to parent class.
        parent::setUp();
        // Remove filters that will create temporary tables. So that permanent tables will be created.
        remove_filter( 'query', array( $this, '_create_temporary_table' ) );
        remove_filter( 'query', array( $this, '_drop_temporary_table' ) );
    }

Above code will do the trick. Happy coding & testing ! :smile:
