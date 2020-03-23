
DEBUGGING IN MIXED SOURCE / ASSEMBLY

```
g++ -masm=intel -xc - -S -o-

 1923  gcc -g `pwd`/aa.c
 1924  ./Insight-90f2e23-x86_64.AppImage  `pwd`/a.out

https://github.com/antony-jr/insight/releases/download/continuous/Insight-90f2e23-x86_64.AppImage
./Insight-90f2e23-x86_64.AppImage  --appimage-extract

```

---

GENERATING LISTING OF SOURCE / ASSEMBLY (MIXED) FROM COMPILER

   - ```
     https://www.systutorials.com/generate-a-mixed-source-and-assembly-listing-using-gcc/
     gcc -Wa,-adhln -g helloworld.c > helloworld.s
     ```

---
CLING

  - [Brief description](
    https://root.cern.ch/cling-brief
    )

  - [Downloads](
    https://root.cern.ch/download/cling
    )


GIT PROMPTS

The following, if appended to ``~/.bashrc` , can be a convenience and time saver by 
reflecting the current time, the last command's exit status, and Git state information
(assuming the CWD is within a local Git repo)

```
#------ This section needed in CentOS but not in Ubuntu:
        GITPROMPT=( {~,/usr/share/git-core/contrib/completion}/git-prompt.sh )
        for x in ${GITPROMPT[@]}; do [ -r $x ] && { source $x ; break; }; done
        # If Download necessary or to fetch latest GIT prompt:
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
