# Polytiramisu

Simple script to display tiramisu notifications in polybar, waybar, and other bars.

This was inspired by [polynotifications](https://github.com/tam-carre/polynotifications) scripts (which did not work for me), but made in a more minimal way and is meant to work out of the box without special settings for tiramisu. At the moment there is no notification history, each notification is shown once and that's it.

![screenshot](screenshot.png)

## Installation

#### Install tiramisu

Install [tiramisu](https://github.com/Sweets/tiramisu) notification daemon. Make sure to delete other notification deamons (like dunst) from your system.

#### Download this script

Download `polytiramisu.sh` to `~/.config/polybar/scripts/` or any other folder and make it executable:

```
git clone https://github.com/anufrievroman/polytiramisu
cp polytiramisu/polytiramisu.sh $HOME/.config/polybar/scripts/
chmod =rwx $HOME/.config/polybar/scripts/polytiramisu.sh
```

#### Add to Polybar

Add this module in your polybar config (and verify the path):

```
modules-left = polytiramisu

[module/polytiramisu]
type = custom/script
# Path to where you put polytiramisu.sh:
exec = ~/.config/polybar/scripts/polytiramisu.sh
format = <label>
tail = true
```

#### Add to Waybar

Add this module in your waybar config (and verify the path):

```
"modules-left": ["custom/polytiramisu"],

"custom/polytiramisu": {
    "format": "{} ",
    "exec": "bash ~/.config/waybar/scripts/polytiramisu.sh",
},
```

## Troubleshooting

To verify that notifications are working, send a test notification: `notify-send "Test notification"`

If you see no notifications, try these steps:

- Make sure you have no other notification daemons (for example, dunst) running. Only one notification daemon can run at a time.
- You don't need to manually run tiramisu, the polytiramisu script will run it. So `killall tiramisu` and restart the polybar.
- If you restarted polybar several times, there might be several zombie instances of polytiramisu running. Kill them all (using htop for example) or just logout and log back in to start from fresh.

## Settings

- In the `polytiramisu.sh` you can choose the character limit `char_limit` and notification duration `display_duration`.
- To choose notification fields to display, add or remove `#source`, `#summary`, and `#body` in the line that says `tiramisu -o '#summary #body' |`.
- If you use nerdfont, you can replace app names with icons by setting `use_nerd_font="true"` and adding corresponding lines (see examples in the script).
- You can customize font and color of notifications. For example, in polybar:
```
format-font = 2
format-foreground = #ffffff
```
Or in waybar css file as:

```
#custom-polytiramisu {
  font-size: 14px;
  color: #ffffff;
}
```

## Support

I am not a professional developer and work on open-source projects in my free time. If you'd like to support the development, consider donations via [buymeacoffee](https://www.buymeacoffee.com/angryprofessor) or cryptocurrencies:

- BTC `bc1qpkzmutdqfxkce34skt09vll97s5smpa0r2tyzj`
- ETH `0x6f1Ce9cA181458Fc153a5f7cBF88044736C3b00C`
- BNB `0x40f22c372758E35C905458cAF8BB17f51ac133d1`
- LTC `ltc1qtu33qyv2xlzxda5mmrmk943zpksq8q75tuh85p`
