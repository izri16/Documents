### Add executable to Launcher

* Create `your-app.desktop` file in `Desktop`
* Example content of `your-app.desktop`:

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=gnome-panel-launcher
Exec=/home/richard/../your-app.AppImage
Name[en_US]=AppName
Name=AppName
Icon=/home/richard/../some-icon.png
```

* Add executable rights to file using `chmod +x your-app.desktop`
* Execute file

https://averagelinuxuser.com/ubuntu_custom_launcher_dock/
