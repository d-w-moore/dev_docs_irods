## Appendix

# tmux

  - More about tmux and default/commonly-used key bindings [here](./tmux.md)

`tmux` logically groups a number of pseudoterminals under one session, subdividing the
text 'screen' as represented in a single terminal window.

`tmux` can be quite useful during test and troubleshooting runs of the iRODS server,
or for allowing long-running processes to stream output to console while detached.
Another advantage is that interrupted network connections do not cause a halt to
any process(es) attached to the console. ( Recovery is simple: just re-connect your
secure shell and re-attach)

## In a nutshell -


`tmux` terminal  sessions can be

  * attached with `tmux a -t<SESSION_NAME_OR_NUMBER>`
  * detached with key combination `<Ctrl-B> <d>`
  * listed via `tmux ls`




# Tailing iRODS logs:

```
tail -n [+AbsoluteLineNum|-NumberOfTailingLines] -f ~irods/log/rodsLog20XX.YYTHisZZ
```


THis abbreviated form is often convenient.
```
  tail -0f LOGFILENAME  #  follows from current EOF
```

```
ls -lart /var/lib/irods/rodsLog*
```

The simplest way to tail lines for iRODS 4.3.0 is :
```
  tail -f /var/log/irods/irods.log |jq .
```



## Git Prompts

The instructions below can enable useful annotations within the bash prompt:

  - time of day
  - git status (assuming the CWD is within a local Git repo)
  - the last command's exit status

Do the following.

  1. On some flavors of Linux OS (eg CentOS/RHEL 7) the definitions from this file will be needed, so download
  to home directory via curl or wget:
```
  $ cd ; wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
```
  2. Then append this script text to the end of .bashrc
```
[ -r $HOME/git-prompt.sh ] && . $HOME/git-prompt.sh
function tgrps1 {
  local BOLDRED="\[\033[1;31m\]"
  local GREEN="\[\033[0;32m\]"
  local BOLDYELLOW="\[\033[1;33m\]"
  local BOLDCYAN="\[\033[1;36m\]"
  local NOCOLOR="\[\033[0m\]"
  export GIT_PS1_SHOWDIRTYSTATE=1
  PS1=$BOLDRED'`echo "ERROR($?) " | sed '\''s/^ERROR(0) \$//'\''`'
  PS1+="$GREEN\$(date +%H:%M%p)"
  PS1+="$BOLDYELLOW\$(__git_ps1) "
  PS1+="$BOLDCYAN\u$NOCOLOR@\h:\w \$ "
}
tgrps1

```
