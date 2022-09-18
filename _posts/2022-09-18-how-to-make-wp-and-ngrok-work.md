---
layout: post
title: "How to easily make Wordpress & WooCommerce work with ngrok"
description: "A quick 3-step tutorial on how to integrate ngrok with Wordpress and WooCommerce."
hidden: false
---

Ngrok is a super useful CLI tool which enables you to expose your localhost HTTP servers to an internet-facing HTTPs endpoint, for free!
You can get it here: [https://ngrok.com/](https://ngrok.com/).

I've been struggling to find a good, short tutorial on how to make it work properly with my local WooCommerce store, so hopefully you will find this helpful:

## 1. Install the 'Relative URL' plugin
First off, make sure that your Wordpress website issues relative URLs by installing this plugin: [Relative URL](http://wordpress.org/plugins/relative-url/).

## 2. Make WP serve itself via your tunneled hostname
Add the following lines at the end of your `wp-config.php` file:
```php
define('WP_SITEURL', 'http://' . $_SERVER['HTTP_HOST']);
define('WP_HOME', 'http://' . $_SERVER['HTTP_HOST']);
```

### 3. Instruct ngrok to rewrite the host header
Add `--host-header=rewrite` to your ngrok command.
For example:
```bash
ngrok http --host-header=rewrite http://localhost:8080
```

Done 🎉

P.S: If you're a WooCommerce store owner and would like to easily sync it with your Google Sheets, [check-out our quick guide on how to do it](https://blog.playmellow.com/how-to-connect-woocommerce-to-google-sheets/).
