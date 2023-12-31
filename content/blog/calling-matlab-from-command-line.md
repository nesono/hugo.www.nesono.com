---
title:       "Calling Matlab Scripts from the Command Line"
type:        blog
date:        2012-12-05
draft:       false
promote:     true
sticky:      false
aliases:     [ node/420 ]
blog categories: [ "programming", "matlab" ]
flattr username: [ "nesono" ]

---

As I need to call Matlab scripts from the command, e.g., for running Matlab scripts in a batch, every once in a while, I post a little reminder for my self here.
Keep in mind that the called Matlab command needs to have an exit at the end, otherwise Matlab will keep running, waiting for input.

In this example I am calling `myscript` and forward bash options `$1` and `$2` to it.
Furthermore I am suppressing the GUI (`-nodisplay`), the Java Virtual Machine (`-nojvm`), the splash screen (`-nosplash`) and the Matlab Desktop (`-nodesktop`).
Anyhow, the latte two options might be implied by suppressing the GUI already - but I'm not taking chances ;).

Note that you need to adjust your path to the `matlab` binary as well as change the script (`myscript(...)`) you want to call, if you simply copy & paste the line below.
And here's the command line:

```bash
/Applications/MATLAB_R2007b/bin/matlab -nodisplay -nojvm -nosplash -nodesktop -r 'myscript($var1,$var2); exit'
```

That's it again,

iss
