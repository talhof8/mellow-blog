---
layout: post
title: "How to Connect WooCommerce to Google Sheets in 3 minutes"
description: "This guide will show you how to connect your WooCommerce store to Google sheets using Mellow."
hidden: false
---

This guide will show you how to connect your WooCommerce store to Google sheets using Mellow.
Mellow is a Google Sheets add-on, which means that you don't need to install any plugin on your WooCommerce store!

It connects to your spreadsheet on one end, and to all of your sales channels on the other end - and keeps them in sync. Every inventory update is automatically being propagated to all other sales channels.

**This is an easy-to-setup, channel-agnostic alternative to tools like WP All Import, Zapier, Coupler, and Automate.io.**


#### What you need
1. Google Sheets
2. WooCommerce store

#### What will get synced
1. Inventory stock changes
2. Sales orders (optional)

## Step 1 - Install the Add-on
Install it here: [https://workspace.google.com/marketplace/app/mellow_sync_your_ecommerce_store/372066191163](https://workspace.google.com/marketplace/app/mellow_sync_your_ecommerce_store/372066191163)

If you are not able to see
<p align="center">
  <img src="/assets/images/posts/2022-09-13-install-add-on.png" />
</p>

## Step 2 - Setup sheet settings
Open your spreadsheet, then click 'Extensions' -> 'Mellow - Sync your eCommerce store'.
Note that it might take a couple of seconds for the add-on to appear on the menu.

This step requires you to specify where your inventory data can be found. That is, what's the name of your inventory sheet, and the columns for Item Name, SKU (optional), and Stock on Hold.

Mellow attempts to automatically identify those columns for you.

<p align="center">
  <img src="/assets/images/posts/2022-09-13-setup-stage.png" />
</p>

## Step 3 - Sign Up
Enter your email address and choose a password. If you already have an account, it will automatically sign you in.
As simple as that.

<p align="center">
  <img src="/assets/images/posts/2022-09-13-sign-up.png" />
</p>

## Step 4 - Connect your store!
Almost there!
All that you have left is to connect your store. Simply put your store URL and click 'Connect'.

<p align="center">
  <img src="/assets/images/posts/2022-09-13-connect-store.png" />
</p>

Now, WooCommerce's authorization window should automatically open in a new tab.
In order for Mellow to be able to read and write data on your store, we need to setup programmatic access to your store. Hence, we must have your consent.

<p align="center">
  <img src="/assets/images/posts/2022-09-13-wc-auth.png" />
</p>

After clicking 'Approve', you'll be redirected to Mellow's website. You can go ahead and close it and get back to your spreadsheet.

## You're all set
Now, you that WooCommerce is connected, you can fetch inventory changes from your store to you sheet at will.
Fetching changes will automatically update your sheet's Stock Quantity column with the updated quantities.

It is recommended that all manual stock adjustments (e.g: for recording incoming shipments) will be performed by clicking the 'Adjust stock' button. This is the only safe way to increase/decrease stock manually, because it will not override existing stock count for an item, but simply adjust it by the specified offset.

You can of-course completely overwrite stock quantities altogether right from your spreadsheet by changing quantities and clicking 'Save changes', but it is **highly discouraged**. Reason being that if a sales order for an item is being processed right before you manually overwrite the quantity for that item, then the sales order adjustment will be lost.

For instance, say you have item ABC (stock qty: 10). A sales order of 5 units was processed by WooCommerce. Unaware of that order, you noticed that 1 unit is damaged and decided to fix its stock quantity from 10 to 9 units. You manually change the quantity for item ABC to 9 units and save changes. Now, instead of having 4 units recorded for item ABC (-5 from the sales order and -1 for being damaged), you have 9, which is obviously incorrect.

To avoid encountering that issue, simply adjust the stock by -1 via the dedicated 'Adjust stock' button, and our system will make sure to adjust it properly without losing any other data.

## Bonus: Syncing sales orders
Optionally, you are also able to fetch sales orders to your spreadsheet!
This requires you to have a dedicated sales orders sheet with the following columns: Item name, SKU (optional), Order ID, Order status, Order quantity. We have a template already ready for you [here](https://docs.google.com/spreadsheets/d/1m9cFScc7jTXyRcISCiegO_LN0cQixF3oPz7lNoEsygs/edit).

You can use your own custom order statuses, but will have to map them to the ones Mellow is able to understand.
In order to configure sales orders connection settings, click 'Settings' on the top right side of the add-on. Then, this window will appear:

<p align="center">
  <img src="/assets/images/posts/2022-09-13-settings.png" />
</p>


Once your sales orders sheet is synced, Mellow automatically creates a column named 'Source' which tells you (and us 😅) where each sales order was originally created.

Example orders sheet before sync:
<p align="center">
  <img src="/assets/images/posts/2022-09-13-example-so-sheet-before.png" />
</p>

Same orders sheet after sync:
<p align="center">
  <img src="/assets/images/posts/2022-09-13-example-so-sheet-after.png" />
</p>


### Distribute manually created sales orders
It is also possible to create sales orders directly from your sheet and distribute them to your WooCommerce store!

Simply go to 'Settings' -> check the checkbox near 'WooCommerce' under section 'Distribute manually-created orders to sales channels'. You can optionally specify a Customer ID column which contains the WooCommerce Customer IDs for each order, thus associating those orders with a specific customer.

Then, simply add a row for each order item. Order ID should be a uniquely identified string and is used to associated items with orders. Hence, in order to have multiple items under the same order, simply assign them with the same Order ID.

Note that Mellow does not (yet) support merged cells, so make sure to unmerge any merged cells.


## Next up: Product Listings, More Integrations
Next up in terms of what we have planned for the near future are two main things:
1. Multichannel Listing
    * We're working on making it possible to list and edit products on your sales channels directly from your spreadsheet
2. Support for more integrations (Etsy, Amazon, Shopify, Square, BigCommerce, etc...)

## Talk to us
Your feedback means the world to us. We want to keep improving our product, and would love to hear what you have to say.
Talk to us at [tal@playmellow.com](mailto:tal@playmellow.com) anytime :)

If you find Mellow useful, it is highly appreciated if you rate it on the [Google Workspace Marketplace](https://workspace.google.com/marketplace/app/mellow_sync_your_ecommerce_store/372066191163).
