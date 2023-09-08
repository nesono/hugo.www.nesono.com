---
title:       "Change RSS Feed Icon with Drupal 7"
type:        blog
date:        2012-07-04
changed:     2012-09-25
draft:       false
promote:     true
sticky:      false
aliases:     [ node/387 ]
blog categories: [ "drupal" ]
flattr username: [ "nesono" ]

---

After reading this [article][1], I decided to change my RSS feed icon as well. However, the article does not cover [Drupal][3] 7 and so I explain the necessary steps here.

First, you should create your `template.php`, if [zen][2] has not created it for you, yet.
Then, you need to decide, where to put the feed icon and how to name it.
I simply use the same as Drupal: The image is `feed.png` and stored within the `misc` folder within my theme folder.

I followed the hint given in the original post and checked the [Drupal API][4] for the original function name (`theme_feed_icon`) and implementation.
I just changed the image path from the original [implementation][5] (`misc/feed.png`) to `drupal_get_path('theme', 'nesono') . '/misc/feed.png'`.

Note that if you want to use this for yourself, you need to change `nesono` in the function's name to your theme's name!


```php
function nesono_feed_icon($variables) {
  $text = t('Subscribe to @feed-title', array('@feed-title' => $variables['title']));
  if ($image = theme('image', array('path' => drupal_get_path('theme', 'nesono') . '/misc/feed.png', 'width' => 16, 'height' => 16, 'alt' => $text))) {
    return l($image, $variables['url'], array('html' => TRUE, 'attributes' => array('class' => array('feed-icon'), 'title' => $text)));
  }
}
```

That's it again  
Cheers,  
iss

[1]: http://mydrupalblog.lhmdesign.com/overriding-drupals-default-rss-feed-icon "overriding drupals rss feed icon"
[2]: http://drupal.org/project/zen/ "Zen Starting Theme"
[3]: http://drupal.org "Drupal Home Page"
[4]: http://api.drupal.org/api/drupal "Drupal API"
[5]: http://api.drupal.org/api/drupal/includes%21theme.inc/function/theme_feed_icon/7 "theme_feed_icon documentation"
