# Linux-Ricing With DWM

![linux-rice](https://github.com/em0n-1337/Linux-Ricing/assets/156088588/11a51789-571a-45cd-b791-3713adcacc6d)

## DWM Installation
- Go to the official website of suckless ![suckless](https://suckless.org/logo.svg)
- Navigate to [DWM](https://dwm.suckless.org/)
- Read their documentation if you are completely new to dwm
- Update and upgrade your system
  - ### Debian 
    ```javascript
    sudo apt-get update && sudo apt-get upgrade -y
    ```

  - ### Arch
    ```javascript
    sudo pacman -Syu
    ```


Now let's come to the point. If you haven't git installed on your linux machine install it with the following command
  - ### For Debian Based Linux
    ```javascript
    sudo apt install git
    ```

  - ### For Arch Based Linux
    ```javascript
    sudo pacman -S git
    ```

Now git clone the following repositories
```javascript
git clone https://git.suckless.org/dwm
git clone https://tools.suckless.org/dmenu/
git clone https://git.suckless.org/slstatus
```

Now make files to dwm, dmenu and slstatus
```javascript
cd dwm [dmenu/slstatus]
sudo make
sudo make clean install
```  
Thus it will be installed on your linux machine as a window manager.

## Configuring DWM Manually
Now we need a one more task to do which is setting up the window manager in our .xinitrc file so that as soon as the X-Window starts we can access DWM. Put the following command to your .xinitrc file.
```javascript
exec dwm
```


If you have another window manager running on your system then don't forget to stop that.
```javascript
# exec other-manager [comment it down]
exec dwm
```  


If this method doesn't work, create a new file to the ```/usr/share/xsessions/dwm.desktop``` location. Then paste the following code
```javascript
[Desktop Entry]
Encoding=UTF-8
Name=Dwm
Comment=Dynamic window manager
Exec=/usr/local/bin/dwm
Icon=dwm
Type=XSession
```


Now log out from the current session and log back again with the dwm session selected. This should appear somewhere on your login screen. Then login to your account and you have successfully installed DWM.


## Custom Configuration
If you want to use my config file, then unzip the dwm-customization folder and then navigate to the dwm, dmenu and slstatus folder and type
```javascript
sudo rm config.h
sudo make
sudo make clean install
```

Create an entry for dwm to ```/usr/share/xsessions/dwm.desktop``` location
```javascript
[Desktop Entry]
Encoding=UTF-8
Name=Dwm
Comment=Dynamic window manager
Exec=/usr/local/bin/dwm
Icon=dwm
Type=XSession
```

I have also added an external file to the dwm folder which is autostart.sh. This basically sets the wallpaper, if you want it to work then replace the wallpaper file with yours one
```javascript
feh --bg-fill /home/your-username/path/to/your/wallpaper/file
```

If you haven't installed feh, then make sure to install it with the following command
```javascript
sudo pacman -S feh
```

You can also set the wallpaper manually to your ```~/.fehbg``` file. But I recommend to set it to the autostart.sh file so that every time dwm starts you don't have to set it again and again. You can also add other applications as well, in this case you just need to add the application name or location to the autostart.sh file. I have included three applications here, feh for setting wallpaper, picom for terminal transparency and slstatus for showing status bar process. If you want your terminal to be transparent as mine, then download alacritty and picom with the following commands
  - ### Alacritty
    ```javascript
    sudo pacman -S alacritty
    ```

  - ### Picom
    ```javascript
    sudo pacman -S picom
    ```

Then download my alacritty.conf and picom.conf file. Put these configuration files to your ```~/.config``` folder. You can also set the configuration as per your need, I have included mine. If you don't want any background transparency for your terminal then feel free the comment out the following line to your ```dwm/autostart.sh``` file
```javascript
#picom &
```


For some reason, if you want to uninstall dwm then type
```javascript
sudo make uninstall
```

If you're familier with C language then you can add more functionalities manually. But if not then you can add patches. I have already included some of the patches, but if you want more, you can check the suckless website.

NOTE: You may face some warnings while making slstatus file, just ignore them in case they appear.
