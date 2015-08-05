---
layout: post
title:  "Leverage Browser Caching"
date:   2015-8-05
author: Ben Robertson
categories: performance
---

<code>
<IfModule mod_headers.c>
	 # 1 YEAR
	<FilesMatch "\.(ico|pdf|flv)$">
	Header set Cache-Control "max-age=29030400, public"
	</FilesMatch>
	# 1 Month
	<FilesMatch "\.(xml|txt|css|js)$">
	Header set Cache-Control "max-age=2592000, must-revalidate"
	</FilesMatch>
	# 1 WEEK
	<FilesMatch "\.(jpg|jpeg|png|gif|swf|svg|.mp4)$">
	Header set Cache-Control "max-age=604800, must-revalidate"
	</FilesMatch>
	# 1 MIN
	<FilesMatch "\.(html|htm|php)$">
	Header set Cache-Control "max-age=60, private, must-revalidate"
	</FilesMatch>
</IfModule>
</code>