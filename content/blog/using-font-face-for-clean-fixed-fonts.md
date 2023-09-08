---
title:       "Using @font-face for Clean Fixed Fonts On Any Platform"
type:        blog
date:        2012-06-25
changed:     2014-08-21
draft:       false
promote:     true
sticky:      false
aliases:     [ node/384 ]
blog categories: [ "web", "css", "drupal", "html", "programming" ]
flattr username: [ "nesono" ]

---

<!--more-->
As I [promised](/node/374 "Another Site Clean-Up and Theme Upgrade") a while ago, I will discover some details of the current nesono Drupal 7 theme. 
It has been optimized towards readability and is inspired by services like [pocket (read it later)](http://getpocket.com/ "Pocket (Read it Later)"), [readability](http://www.readability.com/ "Readability"), and the reading plugins for several browsers.

In this post, I will explain the font settings as specified in the CSS files of this [site's theme](https://github.com/nesono/nesono.drupal7 "nesono.drupal7 on github").
<!--break-->
As a big fan of LaTeX type setting and the Palatino font, I was searching for an open or free look-alike on the web (because web fonts should not suffer from copyright issues).
Finally, I found the font [TeX Gyre Pagella](http://www.fontsquirrel.com/fonts/TeX-Gyre-Pagella "TeX Gyre Pagella") on [fontsquirrel](http://www.fontsquirrel.com/ "FontSquirrel").
I downloaded the *@font-face kit* for highest convenience.

The kit includes the following font formats:

* **TTF** - Works in most browsers except IE and iPhone.
* **EOT** - IE only. 
* **WOFF** - Compressed, emerging standard. 
* **SVG** - iPhone/iPad.

I recognized that Mobile Safari uses **SVG** font files, which was new to me.
Don't forget to choose the subset of the font to the languages you like to support.

Then, after downloading just copy the package into your theme folder and insert the *modified* version of `stylesheet.css` into [`normalize.css`](https://github.com/nesono/nesono.drupal7/blob/master/css/normalize.css).
 I have changed the font's name to be the same (`font-family: 'TeXGyrePagella'`) in every specification.
This makes bold an italic font files to be automatically chosen.
Besides that, I removed some useless `font-weight` and `font-style` statements and fixed the path to the font.

	@font-face {
	    font-family: 'TeXGyrePagella';
	    src: url('../fonts/texgyrepagella-regular-webfont.eot');
	    src: url('../fonts/texgyrepagella-regular-webfont.eot?#iefix') format('embedded-opentype'),
	         url('../fonts/texgyrepagella-regular-webfont.woff') format('woff'),
	         url('../fonts/texgyrepagella-regular-webfont.ttf') format('truetype'),
	         url('../fonts/texgyrepagella-regular-webfont.svg#TeXGyrePagellaRegular') format('svg');
	}
	
	@font-face {
	    font-family: 'TeXGyrePagella';
	    src: url('../fonts/texgyrepagella-italic-webfont.eot');
	    src: url('../fonts/texgyrepagella-italic-webfont.eot?#iefix') format('embedded-opentype'),
	         url('../fonts/texgyrepagella-italic-webfont.woff') format('woff'),
	         url('../fonts/texgyrepagella-italic-webfont.ttf') format('truetype'),
	         url('../fonts/texgyrepagella-italic-webfont.svg#TeXGyrePagellaItalic') format('svg');
	    font-style: italic;
	}
	
	@font-face {
	    font-family: 'TeXGyrePagella';
	    src: url('../fonts/texgyrepagella-bold-webfont.eot');
	    src: url('../fonts/texgyrepagella-bold-webfont.eot?#iefix') 	format('embedded-opentype'),
	         url('../fonts/texgyrepagella-bold-webfont.woff') format('woff'),
	         url('../fonts/texgyrepagella-bold-webfont.ttf') format('truetype'),
	         url('../fonts/texgyrepagella-bold-webfont.svg#TeXGyrePagellaBold') format('svg');
	    font-weight: bold;
	}
	
	@font-face {
	    font-family: 'TeXGyrePagella';
	    src: url('../fonts/texgyrepagella-bolditalic-webfont.eot');
	    src: url('../fonts/texgyrepagella-bolditalic-webfont.eot?#iefix') format('embedded-opentype'),
	         url('../fonts/texgyrepagella-bolditalic-webfont.woff') format('woff'),
	         url('../fonts/texgyrepagella-bolditalic-webfont.ttf') format('truetype'),
	         url('../fonts/texgyrepagella-bolditalic-webfont.svg#TeXGyrePagellaBoldItalic') format('svg');
	    font-weight: bold;
	    font-style: italic;
	}

That way, I can simply specify the font using:

	font-family: 'TeXGyrePagella', Palatino, Georgia, "DejaVu Serif", serif;

If you have any questions, or if this is also available as a browser plug-in, don't hesitate to correct me! :)

That's it again and cheers,  
iss
