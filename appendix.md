
```
tail -n +LINENUM -f ~irods/log/rodsLog20XX.YY.ZZ
```

GIT PROMPTS

The following, if appended to ``~/.bashrc` , can be a convenience and time saver by
reflecting the current time, the last command's exit status, and Git state information
(assuming the CWD is within a local Git repo)

```
#------ This section needed in CentOS but not in Ubuntu:
        GITPROMPT=( {~,/usr/share/git-core/contrib/completion}/git-prompt.sh )
        for x in ${GITPROMPT[@]}; do [ -r $x ] && { source $x ; break; }; done
        # If download is necessary, or to fetch latest GIT prompt:
        # $ cd; wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
#------ _-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-
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
