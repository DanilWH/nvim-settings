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
If you've gotten a problem:
 -  __Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'xxx' doesn't support architecture 'i386'__
    ROOT CAUSE : Google dropped support for 32-bit Chrome on Linux triggering an error when updating apt in 64-bit systems (with multi arch enabled) ... details here : http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu  

    To confirm you are using 64 bit ubuntu with multiarch enabled issue
    ```
    dpkg --print-foreign-architectures
    ```  

    if it says
    ```
    i386
    ```  

    then you have added 32 bit support, this will list your native arch ... issue
    ```
    dpkg --print-architecture
    ```  

    if you are native 64 you will see this output so do SOLUTION shown above
    ```
    amd64
    ```  

    Here is the command to remove multi architecture ( only if you have no 32 bit applications )
    ```
    sudo dpkg --remove-architecture i386
    ```

 -  __The repository cdrom… does not have a Release file__
    To resolve this problem from terminal you must remove/comment this CD-ROM repository source directly from /etc/apt/sources.list
    ```
    sudo nano /etc/apt/sources.list
    ```
    and comment or remove lines that include cdrom. eg:
    ```
    deb cdrom:[Ubuntu-Server 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.3)]/ xenial main restricted
    ```
  
After fixing the problems, run the above command again and after success, run the following command to install node:
```
sudo apt-get install -y nodejs
```
That's it.

  
(as from the official node.js repository using `snap`.)
```
sudo snap install node --classic --channel=14
```
