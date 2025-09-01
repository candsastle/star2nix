# Requirements

nix-darwin:

Uses Property List files, basically XML

```nix
    system.defaults.CustomUserPreferences."com.apple.symbolichotkeys" = {
        AppleSymbolicHotKeys = {
            "61" = {
                value = {
                    type = "standard";
                    parameters = [
                        32
                        49
                        786432
                    ];
                };
                enabled = false;
            };
        };
    };
```

Home Manager:

Reads a GVariant database and converts it to a structured Nix attribute set.
In general: Read database/file/env variables to a structured Nix attr set.

```nix
    with lib.hm.gvariant; {
        dconf.settings = {
            "apps/psensor" = { # auto generated
                graph-alpha-channel-enabled = false;
                graph-background-alpha = mkDouble "1.0";
                graph-background-color = "#e8f4e8f4a8f5";
                graph-foreground-color = "#000000000000";
                graph-monitoring-duration = 20;
                graph-update-interval = 2;
                interface-hide-on-startup = false;
                interface-window-divider-pos = 866;
                interface-window-h = 850;
                interface-window-restore-enabled = true;
                interface-window-w = 1666;
                interface-window-x = 45;
                interface-window-y = 29;
                sensor-update-interval = 2;
                slog-enabled = false;
                slog-interval = 300;
            };
        }; 
    };
```

TOML:

JSON:

YAML:


Dconf 

- System wide color -> system-wide-color 
- Task bar size -> task-bar-size 


dconf db

System-Wide-Color = "black"
Task-Bar-Size = "4"



dconf dump / | dconf2nix

-> 

dconf dump / | star2nix --gvariant

/usr/libexec/PlistBuddy <your_file_location>/info.plist | star2nix --plist
Now

Add an Emoji, Sticker, or GIF

