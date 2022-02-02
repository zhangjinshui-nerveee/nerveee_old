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

# Remote access to PC tower in lab
> Powerful computers are always heavy. But doing mass calculation doesn't means you have to carry them with you. Access your workstation anywhere by connecting two Ubuntu systems anytime and anywhere.<br>
> Assume (at least it's true to me) that your work station is in the lab and the network it connects to is education net.(In our lab, DukeBlue wifi.)

## On campus
If you are on campus but not in the lab (like dating some girl in the cafe), you want to access your lab PC tower and finish some calculation. 
1. Make sure your PC tower have SSH service running correctly. 
2. Fix the IP address of your lab computer. 
3. On your poor old laptop, which should also connect to the education wifi (DukeBlue), open terminal and key `ssh user@IP address`. 
> It might show some security info if it's the first time connecting. 
4. Congratulations! Your laptop now is more powerful than any laptop in this cafe!

## Out of campus (no access to edu network)
What if I am not on campus and my network is some random public wifi? Calm down. Ngrok is our savior. And just the free service it provides would be good enough. 
1. The principle of ssh connection is the same as the previous case. The only difference is that instead of using real IP address of lab PC, ngrok will generate a virtual address after it finishes NAT (Network address translation). 
2. How to NAT? Install ngrok. Open your terminal and key`ngrok tcp 22`. Then you are good to go. 
3. The virtual address may look like `0.tcp.ngrok.io -p10000`. Ngrok will tell you everything after you run the command above. 
4. Enjoy!

## For data science 
> Well, I know nothing about data science except that Jupyter Notebook makes everything in data analysis easier. 

How should we use JUpyter Notebook remotely? The principle is exactly the same. 
1. Run jupyter notebook in your lab PC. (After remotely accessing this PC, enter the path and command `jupyter notebook`). But, not just run it, you need to run it in a no-browser way. 
```
jupyter notebook --no-browser --port=8889
```
2. In your laptop, ssh connect to the jupyter server created just. 
```
ssh -N -f -L localhost:8884:local:8889 user@ip address
```
Same as before, if you are on campus, use real IP address. If not, use the ngrok virtual address. 

3. Open your browser, and enter the server. http://localhost:8884
Note that 8884 can be changed to other numbers, as long as it's consistent with the ssh command. 
4. Enjoy!

# Setting up environment for Python
- 'Access to the file was denied The file at file:///run/user/1000/jupyter/nbserver-26395-open.html is not readable. It may have been removed, moved or file permissions may be preventing access.'<br>
1. Run 'jupyter lab build'. If it fails, may need to install node.js. See the error info. Not working......

# References
[1] [7.14 Git Tools - Credential Storage](https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage)
