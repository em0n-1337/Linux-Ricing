# Linux-Ricing With DWM

## Basic DWM Installation
- Go to the official website of suckless ![suckless](https://suckless.org/logo.svg)
- Navigate to [DWM](https://dwm.suckless.org/)
- Read their documentation if you are completely new to dwm
- Now let's come to the point. If you haven't git installed on your linux machine install it
  - ### For Debian Based Linux
    ```javascript
    sudo apt install git
    ```

  - ### For Arch Based Linux
    ```javascript
    sudo pacman -S git
    ```

- Now git clone the repository
```javascript
git clone https://git.suckless.org/dwm
cd dwm
sudo make
sudo make clean install
```  

Thus it will be installed on your linux machine as a window manager. But here we need a one more task to do which is setting up the window manager in our .xinitrc file so that as soon as the X-Window starts we can access DWM. Put the following command to your .xinitrc file.
```javascript
exec dwm
```


If you have another window manager running on your system then don't forget to stop it.
```javascript
# exec other-manager [comment it down]
exec dwm
```  


If this method doesn't work, create a new file to the ```javascript /usr/share/xsessions/dwm.desktop``` Then paste the following code
```javascript
[Desktop Entry]
Encoding=UTF-8
Name=Dwm
Comment=Dynamic window manager
Exec=/usr/local/bin/dwm
Icon=dwm
Type=XSession
```


Now log out from the current session and log back again with the dwm session selected. This should appear somewhere on your login screen. If you want to use my config file then navigate to the dwm folder again and type
```javascript
sudo make clean install
```

For some reason, if you want to uninstall it then type
```javascript
sudo make uninstall
```

If you're familier with C language then you can add more functionalities manually. But if not then you can add patches, check the suckless website under dwm section.
