---
title:       "RSS Feed Icon from Font Instead of Image (PNG) with Drupal 7"
type:        blog
date:        2012-07-18
changed:     2012-09-24
draft:       false
promote:     true
sticky:      false
aliases:     [ node/393 ]
blog categories: [ "admin", "drupal", "web" ]
flattr username: [ "nesono" ]

---

<!--more-->
As written in a [post][1] before, I customized the Drupal RSS feed icon by replacing it with my own PNG icon.
Unfortunately, the PNG icon should be designed well and is never scalable when using pixels.
Therefore, I wanted to change it to a font based (vector) icon using again free fonts from [font squirrel][2].
<!--break-->

I chose the ['Web Symbols'][3] font, which includes several other nice icons, I'd probably use in the future.
For the RSS feed icon, there exist two icons, the positive
(&nbsp;<span style="font-family: WebSymbols">B</span>&nbsp;)
and the negative
(&nbsp;<span style="font-family: WebSymbols">r</span>&nbsp;)
one.

I decided to use the negative one, which is addressed by the character `r`.
Therefore, I change the function `nesono_feed_icon` as follows:

    function nesono_feed_icon($variables) {
      $text = t('Subscribe to @feed-title', array('@feed-title' => $variables['title']));
      if ($image = theme('image', array('path' => drupal_get_path('theme', 'nesono') . '/misc/feed.png', 'width' => 16, 'height' => 16, 'alt' => $text))) {
        return l('r', $variables['url'], array('html' => TRUE, 'attributes' => array('class' => array('feed-icon'), 'title' => $text)));
      }
    }

Then, I downloaded the `@font-face kit` from [Font Squirrel][3] and added the definition to my CSS (simply compiled the contents of the shipped CSS file into my main CSS).

Then, I changed the `font-family` of the feed character surrounding tag to `WebSymbols` and that's it again :)

Best,  
iss

[1]: /node/387 "Previous Blog Post"
[2]: http://www.fontsquirrel.com/ "Font Squirrel"
[3]: http://www.fontsquirrel.com/fonts/web-symbols "Web Symbols Font"
