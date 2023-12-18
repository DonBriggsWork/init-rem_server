# shellcheck disable=SC2148
#
# Don!s Bash aliases
#

printf '=== Loading Don Aliases\n'

alias al='clear && alias'
alias ll='ls -lh --color=auto'
alias la='ls -Ah'
alias l='clear && ll'
alias scripts='clear && ls -r ~/scripts'
alias reload='clear && echo "--- Reloading .bashrc ---" && source $HOME/.profile'
alias path='echo $PATH'
alias pip-upgrade="pip freeze --user | cut -d'=' -f1 | xargs -n1 pip3 install -U"
alias lock_keys='sudo chmod 400 ~/.ssh/*.pem'
alias apt_repos='for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done'
alias userlist='cat /etc/passwd |grep "/bin/bash" |cut -d: -f1'
alias grouplist='cut -d: -f1 /etc/group'
alias hosts="clear && cat /etc/hosts"
alias keyoff='xinput float 15'
alias keyon='xinput reattach 15 3'