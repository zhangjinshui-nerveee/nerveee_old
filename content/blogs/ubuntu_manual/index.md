---
title: Make Ubuntu Easier to Use
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
# customed command
alias skill-update='cd /home/jinshui/Documents/Github/make_difference_by_10k_hours
                    python3 update_daily.py'
alias slipbox='vim -p /home/jinshui/Documents/Github/slipbox/PermanentNotes/*.md'
alias todo='vim /home/jinshui/Documents/Github/slipbox/todo.md'

alias blog-power-electronics='vim /home/jinshui/Documents/Github/nerveee/content/blogs/driver_circuit_for_wbg_devices/index.md'
alias blog-neuroscience='vim /home/jinshui/Documents/Github/nerveee/content/blogs/cognitive_neuroscience/index.md'
alias blog-ubuntu='vim /home/jinshui/Documents/Github/nerveee/content/blogs/ubuntu_manual/index.md'
alias blog-fpga='vim /home/jinshui/Documents/Github/nerveee/content/blogs/fpga_development_with_sbrio_and_labview/index.md'
alias blog-machine-learning='vim /home/jinshui/Documents/Github/nerveee/content/blogs/machine_learning/index.md'
alias blog-reading-digest='vim /home/jinshui/Documents/Github/nerveee/content/blogs/reading_digest/index.md'

alias lazy-gitpush-all='
                  cd /home/jinshui/Documents/Github/ece_687d
                  git add --all
                  git commit -a -m "commit"
                  git push
                  cd /home/jinshui/Documents/Github/make_difference_by_10k_hours
                  git add --all
                  git commit -a -m "commit"
                  git push
                  cd /home/jinshui/Documents/Github/nerveee
                  git add --all
                  git commit -a -m "commit"
                  git push
                  cd /home/jinshui/Documents/Github/slipbox
                  git add --all
                  git commit -a -m "commit"
                  git push
                  cd /home/jinshui/Documents/Github/mps_tms
                  git add --all
                  git commit -a -m "commit"
                  git push
                  exit'

alias lazy-gitpull-all='
                  cd /home/jinshui/Documents/Github/ece_687d
                  git pull
                  cd /home/jinshui/Documents/Github/mps_tms
                  git pull
                  cd /home/jinshui/Documents/Github/nerveee
                  git pull
                  cd /home/jinshui/Documents/Github/slipbox
                  git pull
                  cd /home/jinshui/Documents/Github/make_difference_by_10k_hours
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

