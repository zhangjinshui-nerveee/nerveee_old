---
title: Make Ubuntu Easier to Use
date: 2021-03-25
math: true
diagram: true
image:
  placement: 3
  # caption: 'Image credit: [**John Moeses Bauan**](https://unsplash.com/photos/OGZtQF8iC0g)'
---

## How to push all git repositories in one command. 
1. edit .bashrc 
'''
vim ~/.bashrc
'''
2. use 'alias' 

```
alias slipbox='vim -p /home/jinshui/Documents/Github/SlipBox/PermanentNotes/*.md'
alias slipbox-post='cd /home/jinshui/Documents/Github/SlipBox
                    git add --all
                    git commit -a -m "commit"
                    git push'
alias todo='vim /home/jinshui/Documents/Github/SlipBox/Daily.md'
alias blog-brain='vim /home/jinshui/Documents/Github/nerveee/content/post/brain_science/index.md'
alias blog-literature='vim /home/jinshui/Documents/Github/nerveee/content/post/Reading_Digest/index.md'
alias blog-machinelearning='vim /home/jinshui/Documents/Github/nerveee/content/post/machine_learning/index.md'
alias blog-FPGA='vim /home/jinshui/Documents/Github/nerveee/content/post/FPGA/index.md'
alias blog-post='cd /home/jinshui/Documents/Github/nerveee
                  git add --all
                  git commit -a -m "commit"
                  git push'

alias lazy-gitpush-all='cd /home/jinshui/Documents/Github/ECE_687D
                   git add --all
                   git commit -a -m "commit"
                   git push
                   cd /home/jinshui/Documents/Github/Programming_MMC_Simulation
                   git add --all
                   git commit -a -m "commit"
                   git push
                   cd /home/jinshui/Documents/Github/nerveee
                   git add --all
                   git commit -a -m "commit"
                   git push
                   cd /home/jinshui/Documents/Github/SlipBox
                   git add --all
                   git commit -a -m "commit"
                   git push'
 
alias lazy-gitpull-all='cd /home/jinshui/Documents/Github/ECE_687D
                   git pull
                   cd /home/jinshui/Documents/Github/Programming_MMC_Simulation
                   git pull
                   cd /home/jinshui/Documents/Github/nerveee
                   git pull
                   cd /home/jinshui/Documents/Github/SlipBox
                   git pull'

```

