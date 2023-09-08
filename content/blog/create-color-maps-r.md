---
title:       "Create Color Maps in R"
type:        blog
date:        2015-04-18
draft:       false
promote:     true
sticky:      false
aliases:     [ node/459 ]
blog categories: [ "r" ]
flattr username: [ "nesono" ]

---

This is a classic in R and I tend to forget it every once in a while. So I write it down as  a note for my future me.

This line creates a gray scale with `len` steps:

```R
grey(1:len/len)
```

This line creates a color scale going through hue, saturation, and value (luminance):

```R
hsv(1:len/len)
```

This line creates a color scale using the hue, chroma, luminance space:

```R
hcl(1:360/len)
```

That's it again.  
Cheers, iss
