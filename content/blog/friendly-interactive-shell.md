---
title:       "A friendly interactive shell"
type:        blog
date:        2017-12-21
draft:       false
promote:     true
sticky:      false
aliases:     [ node/475 ]
blog categories: [ "shells" ]
flattr username: [ "nesono" ]
---

<!--more-->
Encouraged by a [tweet](https://twitter.com/erdgeist/status/935645298768207872), intrigued by the [homepage](http://fishshell.com), and this [blog](https://www.martinklepsch.org/posts/git-prompt-for-fish-shell.html), I started playing around with the fish shell.
Reading through the tutorial and documentation, I often felt that the right choices were done, even though sometimes a little brave (e.g. with changing `&&` to `; and`).

I have been using [zsh](http://zsh.sourceforge.net) for a while now after being a bash user for a long time and work on macOS, Linux, and FreeBSD and I fancy a nice prompt, in particular including repository status, number of background jobs, last commands error code, etc.

I gave fish a shot and came up with the configuration in the following listing, which is small, simple to set up and feels like a somewhat clean configuration.
The reason for that might be that the git prompt is a first class citizen in fish and that fish's scripting language seems well designed.

```bash
# Fish git prompt
set __fish_git_prompt_showdirtystate 'yes'
set __fish_git_prompt_showstashstate 'yes'
set __fish_git_prompt_showuntrackedfiles 'yes'
set __fish_git_prompt_showupstream 'yes'
set __fish_git_prompt_color -b grey
set __fish_git_prompt_color_branch -b grey yellow
set __fish_git_prompt_color_upstream_ahead -b grey green
set __fish_git_prompt_color_upstream_behind -b grey red
set __fish_git_prompt_show_informative_status 'yes'

# Status Chars
set __fish_git_prompt_char_upstream_prefix ':'
set __fish_git_prompt_char_upstream_ahead 'A'
set __fish_git_prompt_char_upstream_behind 'B'
set __fish_git_prompt_char_stateseparator '.'
set __fish_git_prompt_char_dirtystate 'm'
set __fish_git_prompt_char_invalidstate 'x'
set __fish_git_prompt_char_stagedstate 'M'
set __fish_git_prompt_char_untrackedfiles '?'
set __fish_git_prompt_char_cleanstate ''
set __fish_git_prompt_char_stashstate '^'
set __fish_git_prompt_describe_style 'branch'

function fish_prompt
  set -l last_status $status

  if not test $last_status -eq 0
    set_color -b $fish_color_error white
    printf ' %s ' (echo $last_status)
    set_color normal
  end

  set -l jobcount (jobs | wc -l)
  printf '[%d]' $jobcount

  printf '%s ' (__fish_git_prompt)
  printf '%s ' (date "+%y-%m-%d %H:%M:%S")
  set_color green
  printf  '%s\n' (hostname)

  set_color $fish_color_cwd
  printf '%s\n> ' (prompt_pwd)

  set_color normal
end
```

The first two paragraphs are configuration settings of the git prompt, while the 'actual work' is done in the function `fish_prompt`.
It contains the last command's return code with red background (if non-zero), the number of jobs in the background, a detailed git status prompt, the date and time when the prompt was printed, the hostname and in the next line the working directory.

Very compact, very nice.
Cheers,  

iss
