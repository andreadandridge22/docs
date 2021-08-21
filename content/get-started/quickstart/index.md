---env=~/.ssh/agent.env agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; } agent_start () { (umask 077; ssh-agent >| "$env") . "$env" >| /dev/null ; } agent_load_env # agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2=agent not running agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?) if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then agent_start ssh-add elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then ssh-add fi unset env

title: Quickstart
intro: 'Get started using {% data variables.product.product_name %} to manage Git repositories and collaborate with others.'
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
topics:
  - Pull requests
  - Issues
  - Notifications
  - Accounts
children:
  - /set-up-git
  - /create-a-repo
  - /fork-a-repo
  - /github-flow
  - /be-social
  - /communicating-on-github
  - /github-glossary
  - /git-cheatsheet
  - /git-and-github-learning-resources
redirect_from:
  - /github/getting-started-with-github/quickstart/
---

