### Add executable to Launcher

* Create `your-app.desktop` file in `~/Desktop` folder
* Use absolute paths for `Exec` and `Icon` options
* Example content of `your-app.desktop`:

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/home/richard/../your-app.AppImage
Name=AppName
Icon=/home/richard/../some-icon.png
```

* Add executable rights to file using `chmod +x your-app.desktop`
* Test that file is correct by double clicking on it (it should launch)
* Copy file to `~/.local/share/applications` (in order to add it to launcher)
* Type `Alt + F2` (will launch gnome terminal) and type `restart`
* Open ubuntu laucher type your app name, ... That's it!

### Nordvpn autoconnet
* `nordvpn set autoconnect [enabled]/[disabled] [[country]/[server]/[country_code]/[city]/[group] or [country] [city]]`
* e.g. `nordvpn set autoconnect enabled Bratislava`
