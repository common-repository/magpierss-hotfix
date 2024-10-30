=== MagpieRSS Hotfix ===
Contributors: johnbillion
Tags: rss, feeds, magpierss, hotfix, enclosures, utf-8, encoding, rss, fix
Requires at least: 2.3
Tested up to: 2.7
Donate link: http://lud.icro.us/donations/
Stable tag: trunk

Adds support for RSS enclosures and fixes some character encoding problems.

== Description ==

This hotfix adds support for RSS enclosures to MagpieRSS, the RSS parser behind the `fetch_rss()` function in WordPress. It also forces MagpieRSS to use UTF-8 character encoding, which fixes some issues with feeds that contain non-ASCII characters.

== Installation ==

Unzip the ZIP file and drop the folder straight into your `wp-content/plugins/` directory.
Activate the plugin through the 'Plugins' menu in WordPress.
That's it! You can now parse enclosures contained in feeds fetched by WordPress.

== Frequently Asked Questions ==

= Is this plugin for me? =

This plugin is only going to be of use to you if:

*  You are fetching feeds on your blog with the `fetch_rss()` function and want to parse enclosures contained in the feed; or
*  You are fetching feeds on your blog either with the RSS Sidebar Widget or with `fetch_rss()` and question marks are showing up somewhere in the feed where special characters are supposed to be.

= How to I parse enclosures from my feed in my code? =

It's easy. The syntax is similar to getting other items in your feed such as the title:

`
# Grab your feed from $feed_url:
$feed = fetch_rss( $feed_url );

# Grab the title of the first entry:
$title = $feed->items[0]['title'];

# Grab the URL of the first enclosure from the first entry:
$enclosure = $feed->items[0]['enclosure'][0]['url']);
`

*This is an over-simplified example!* Don't forget to use sanity checks in your code. You'll probably want to use `foreach()` to loop over your entries too. If you're not sure what the contents of your feed looks like, you can always dump it out using:

`echo '<pre>';
print_r( $feed->items );
echo '</pre>';`