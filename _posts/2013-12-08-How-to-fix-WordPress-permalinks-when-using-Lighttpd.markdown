---
layout: post
title: 
date: 2013-12-08 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: How-to-fix-WordPress-permalinks-when-using-Lighttpd.png # Add image post (optional)
tags: [WordPress, Linux, Lighttpd] # add tag
---
Recently the blog has been moved over to Lighttpd. At first everything every looked happy and dandy however soon noticed that the WordPress permalinks didn’t work correctly.

Lighty didn’t recognized the re-writing of the URL, which is done by the permalinks functionality. Fortunately the Apache alternative Lighttp is ver flexible when it comes to the configuration. The solution to the problem is actually very easy. First add the mod_rewrite within server.modules section of the ```/etc/ligghttpd/lighttpd.conf```, i just had to remove the # symbol. So this server.modules now looks like:

```
[/etc/ligghttpd/lighttpd.conf]

server.modules = (
"mod_access",
"mod_alias",
"mod_compress",
"mod_redirect",
"mod_rewrite",
)
````

To fix the permalinks i added the rewriting section the end of the same ```/etc/ligghttpd/lighttpd.conf``` file. This works for multiple wordpress sites hosted by lighty. If you like/need you can adapt this section your own likings/needs.

``` 
[/etc/ligghttpd/lighttpd.conf]

#Permalink settings

$HTTP[“host”] =~ “(www.)?” {
	url.rewrite = (

	# Excludes the admin, includes, wp-content etc.
	“^/(wp-admin|wp-includes|wp-content|gallery2)/(.*)” => “$0”,

		# Exclude .php files at the root of rewriting
		“^/(.*)\.(.+)$” => “$0”,

		# Handle permalinks and feeds
		“^/(.+)/?$” => “/index.php/$1”
	)
}
```

Restarting the webserver will make the changes effective:

```
/etc/init.d/lighttpd restart
[ ok ] Stopping web server: lighttpd.
[ ok ] Starting web server: lighttpd.
```

Hurray, it works!
