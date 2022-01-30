---
title: Make Linux Easier to Use
summary: Rookie wants to make Ubuntu comfortable.
date: 2021-03-25
math: true
diagram: true
tags:
- Other
image:
  placement: 3
  # caption: 'Image credit: [**John Moeses Bauan**](https://unsplash.com/photos/OGZtQF8iC0g)'
---

## How to push all git repositories in one command. 
1. edit .bashrc 
```
vim ~/.bashrc
```
2. use 'alias' 

```
alias skill-update='cd /home/jinshui/Documents/github/make_difference_by_10k_hours
                    python3 update_daily.py'
alias slipbox='vim -p /home/jinshui/Documents/github/slipbox/PermanentNotes/*.md'
alias todo='vim /home/jinshui/Documents/github/nerveee/content/blogs/todo/index.md'

alias blog-power-electronics='vim /home/jinshui/Documents/github/nerveee/content/blogs/driver_circuit_for_wbg_devices/index.md'
alias blog-neuroscience='vim /home/jinshui/Documents/github/nerveee/content/blogs/cognitive_neuroscience/index.md'
alias blog-ubuntu='vim /home/jinshui/Documents/github/nerveee/content/blogs/ubuntu_manual/index.md'
alias blog-fpga='vim /home/jinshui/Documents/github/nerveee/content/blogs/fpga_development_with_sbrio_and_labview/index.md'
alias blog-machine-learning='vim /home/jinshui/Documents/github/nerveee/content/blogs/machine_learning/index.md'
alias blog-reading-digest='vim /home/jinshui/Documents/github/nerveee/content/blogs/reading_digest/index.md'

alias lazy-gitpush-all='
                  cd /home/jinshui/Documents/github/make_difference_by_10k_hours
                  git add --all
                  git commit -a -m "commit"
                  git push
                  cd /home/jinshui/Documents/github/nerveee
                  git add --all
                  git commit -a -m "commit"
                  git push
                  cd /home/jinshui/Documents/github/slipbox
                  git add --all
                  git commit -a -m "commit"
                  git push
                  cd /home/jinshui/Documents/github/mps_tms
                  git add --all
                  git commit -a -m "commit"
                  git push
                  exit'

alias lazy-gitpull-all='
                  cd /home/jinshui/Documents/github/mps_tms
                  git pull
                  cd /home/jinshui/Documents/github/nerveee
                  git pull
                  cd /home/jinshui/Documents/github/slipbox
                  git pull
                  cd /home/jinshui/Documents/github/make_difference_by_10k_hours
                  git pull
                  exit'
```
3. In terminal
```
lazy-gitpush-all % push all
lazy-gitpull-all % pull all
```

And surely you can play more interesting and powerful things with .bashrc configuration. 



## How to monitor the computer status
```
free -h
```

## Connect two Ubuntu using Remmina
- Necessary: VNC server
- steps:
-


## How to use vim plugin
- fisadev

## how to store personal access token 
There are two solutions. 
```
git config --global credential.helper cache
```
Or
```
git config --global credential.helper store
```
What's the difference?

- The default is not to cache at all. Every connection will prompt you for your username and password.
- The “cache” mode keeps credentials in memory for a certain period of time. None of the passwords are ever stored on disk, and they are purged from the cache after 15 minutes.
- The “store” mode saves the credentials to a plain-text file on disk, and they never expire. This means that until you change your password for the Git host, you won’t ever have to type in your credentials again. The downside of this approach is that your passwords are stored in cleartext in a plain file in your home directory.



# References
[1] [7.14 Git Tools - Credential Storage](https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage)
