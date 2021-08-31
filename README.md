Because I always need to setup a programming environment on Ubuntu. I ENJOY it as a learning process. This repository contains the learning materials for programming on Linux.

My programming setup includes:
- [Git For Code Management](#git-for-code-management)
- [VSCode For Code Editing And Debugging](#vscode-for-code-editing-and-debugging)
- [pyenv for Python virtual environments across different Python versions](#python-virtual-environment)
- [Script for Automatic Setting-up](#script-for-automatic-setting-up)
- [Others](#others)
- [WSL 2 on Windows](#wsl-2-on-Windows)

# Git For Code Management
* Installation
```
sudo apt install git -y
```

* Setttings: refers to [this official tutorial](https://git-scm.com/book/uz/v2/Appendix-A%3A-Git-in-Other-Environments-Git-in-Bash). It includes (1) Auto-completion: Copy `[git-completion.bash](git)` somewhere handy, e.g. home directory; (2) customize command line prompt: copy `[git-prompt.sh](git)` to home directory; (3) add the following to bash profile
```
 . ~/git-prompt.sh
 export GIT_PS1_SHOWDIRTYSTATE=1
 export PS1='\w$(__git_ps1 " (%s)")\$ '
```
  
# VSCode For Code Editing And Debugging

# Python Virtual Environment

[Hands-on Scripts](pyenv.sh)



# Script for Automatic Setting-up
I set up programming environments whenever my supervisor gives me a new VM or I want to set up a VM on Azure or I accidentally lost the access to the daily-used device or I buy a new device. This script helps me painlessly setup a new device or Linux VM to continue my work.

# OTHERS
## Bash
add the following content into bash profile
```
   # customize prompt
   GOPATH=$HOME/go
   function _update_ps1() {
               PS1="$($GOPATH/bin/powerline-go -error $?)"
       }
   if [ "$TERM" != "linux" ] && [ -f "$GOPATH/bin/powerline-go" ]; then
               PROMPT_COMMAND="_update_ps1; $PROMPT_COMMAND"
   fi
   source "$HOME/.cargo/env"
```

## Tensorflow GPU

```python
  import json
  from __future__ import absolute_import, division, print_function, unicode_literals
  
  import tensorflow as tf
  print("Num GPUs Available: ", len(tf.config.experimental.list_physical_devices('GPU')))
  
  
  def greet(name):
      return 'Hello, ' + name
```

## Use R script in Jupyter. For using R in Jupyter:

1. `apt-get install r-base r-base-dev libssl-dev libcurl3-dev curl`
2. type the commands below in R prompt:
`install.packages(c('pbdZMQ', 'repr', 'devtools'))`
`devtools::install_github('IRkernel/IRkernel') `
`IRkernel::installspec()`

# WSL 2 on Windows
To following the program-on-linux principle, here is my setup on Windows using (1) WSL2 (separate linux kernel compared to WSL), (2) [Window Terminal](https://github.com/microsoft/terminal), (3) [Powerline for Windows Terminal](https://docs.microsoft.com/en-us/windows/terminal/tutorials/powerline-setup), (4) [vscode remote setup](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-vscode).

BTW, in order to have no reliability of any specific OS beyond programming, I only install common apps with web versions which can be accessed by browsers or all mainstream OS, e.g., onedrive for file management, Zoom (login), Wechat (login), notion (login).

## Use Cuda
[Nvidia use guide](https://docs.nvidia.com/cuda/wsl-user-guide/index.html)

[Microsoft use guide ](https://docs.microsoft.com/en-us/windows/ai/directml/gpu-cuda-in-wsl)

[gaps between WSL 2 and native Linux if you use Cuda-based applications](https://developer.nvidia.com/blog/leveling-up-cuda-performance-on-wsl2-with-new-enhancements/)

