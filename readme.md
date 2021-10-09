# Polytiramisu

Script to display tiramisu notification in polybar with a simple script. 
This was inspired by [polynotifications](https://github.com/tam-carre/polynotifications) scripts (which did not work for me), but made in a more minimal way and is meant to work out of the box without much confifuration. At the moment there is no notification history, each notification is shown once and that's it.

![screenshot](screenshot.png)

## Installation

1. Install [tiramisu](https://github.com/Sweets/tiramisu) notification deamon.

2. Download `polytiramisu.sh` to `~/.config/polybar/scripts/` and make it executable:

```
git clone https://github.com/anufrievroman/polytiramisu
cp polytiramisu/polytiramisu.sh $HOME/.config/polybar/scripts/
chmod =rwx $HOME.config/polybar/scripts/polytiramisu.sh
```

3. Add this module to your polybar config (verify the path):

```
modules-left = polytiramisu

[module/polytiramisu]
type = custom/script
# Path to where you put polytiramisu.sh:
exec = ~/.config/polybar/scripts/polytiramisu.sh
format = <label>
tail = true
```

## Settings

In the `polytiramisu.sh` you can choose the character limit `char_limit` and notification duration `display_duration`. To choose nofication fields to diplay, add or remove `#source`, `#summary`, and `#body` in the line that says:

```
tiramisu -o '#summary #body' |
```
