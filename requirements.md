# Windows
### Place init.vim
Second, based on Neovim official documentation, you should put `init.vim` under the directory `~/AppData/Local/nvim` on Windows.
To find here that directory is exactly, use the command `:echo stdpath('config')` inside Neovim.  

If this directory does not exist, do not worry. Just create it and put your config file there.

### Install plugin-manager vim-plug
To install it on Windows, open a PowerShell terminal (not Windows CMD!), and execute the following command:
```
md ~\AppData\Local\nvim\autoload
$uri = 'https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
(New-Object Net.WebClient).DownloadFile(
  $uri,
  $ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath(
    "~\AppData\Local\nvim\autoload\plug.vim"
  )
)
```

### Install node.js
Go to [https://nodejs.org/en/download/](https://nodejs.org/en/download/) and install node.js.

### Install all the plugins
 Run command `:PlugInstall`. All the plugins will be installed under `~/AppData/Local/nvim/plugged`.

# Ubuntu
### Download the plug.vim plugin. (so that you can use `:PlugInstall`)
Download plug.vim and put it in the "autoload" directory.
```
sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
```

### Download node.js
(as coc.nvim suggests)
Install nodejs >= 10.12:
```
curl -sL install-node.now.sh/lts | bash
```
(as from the official node.js repository)
```
curl -fsSL https://deb.nodesource.com/setup_15.x | sudo -E bash -
sudo apt-get install -y nodejs
```
(as from the official node.js repository using `snap`.)
```
sudo snap install node --classic --channel=14
```
