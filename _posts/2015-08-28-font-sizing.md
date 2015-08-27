---
layout: post
title:  "Font-Sizing: An Overview of px, Em's, & Rem's"
date:   2015-8-28
author: Jordan Barber
categories: design scss
---

Until now, we have been using pixels for sizing fonts.  This is not necessarily a bad thing.  Some of the most popular and heaviest-traffic sites the the world currently use pixels when sizing their typography (Bootstrap did not move away from pixels until the release of Bootstrap 4 only a little more than a week ago).

But there are more modern, responsive approaches to web typography, namely the Em and Rem units.  The most significant difference between pixels and Ems/Rems is that the latter are relative, while the former is not.  These relative units are nothing new (the first [article](http://clagnut.com/blog/348/) on Ems was published in 2004).

This post summarizes these three approaches, pointing out their ups and downs and when is best to use which approach.

<h4>Pixels</h4>

Pixels are a safe, fixed unit of measure.  They are straightforward and exact.  Unfortunately, simplicity and precision are the only useful aspects of pixels (well, that and browser support). The downsides of pixels are that they are non-responsive and lack accessibilty.  Because pixels are not a relative unit, they cause much more work in responsive web design. Below is a basic set up of how we would handle responsive typography with pixels inside of our SMACCS environment.

{% highlight scss %}

html { font-size: 16px; 
	@include bp(large-screens){font-size: }
}

h1 { font-size: 33px; 
	@include bp(large-screens){}
}

h2 { font-size: 28px; 
	@include bp(large-screens){}
}

h3 { font-size: 23px; 
	@include bp(large-screens){}
}

h4 { font-size: 19px; 
	@include bp(large-screens){}
}

small { font-size: 13px; 
	@include bp(large-screens){}
}

{% endhighlight %}

