
# About this keymap
After using a moonlander for a while, Ive been able to experiment quickly with Oryx. This map is the result.
<br/>
<br/>
The guiding principle is to reduce the amount of finger travel required over the course of a dev day.
<br/>
The `middle bottom` keys (`col 7/col 8`, `row 3`), Contain Single Tap for `(`, Press and hold for `{`, and Double tap for `[` and same for closing shortcuts.
<br/>
- Access to `QWERTY` is via `tog 1` (`col 7`, `row 1`),
- Access to `SYMBOLS` is via `mo 2` (`col 1/col 14`, `row 5`),
- Access to `CONFIG` (Danger layout) is hidden in `QWERTY`, via `mo 3` (`col 7`, `row 2` & `col 8`, `row 1`)
<br/>
<br/>

![Alt text](kinesis-advantage-360-pro.png)

## Layers
- **DVORAK** - default layer (`Tog 1` to swap in and out of Qwerty layer)<br/>
RGB indicator light = None <br/><br/>

- **QWERTY** - `tog 1`,  Layer 1 is to avoid having to rebind software like blender, and houses access to the danger `CONFIG` layer via `Mo 3`. <div style="display: flex; align-items: center;">RGB indicator light = <div style="margin-left: 5px; margin-right: 5px; height: 15px; width: 15px; background-color: white; border-radius: 50%"></div> (white)</div><br/>

- **SYMBOLS** - `mo 2`, Layer 2, contains handy home row access to numbers and media controls, and some non-dangerous keyboard config controls. <div style="display: flex; align-items: center;">RGB indicator light = <div style="margin-left: 5px; margin-right: 5px; height: 15px; width: 15px; background-color: blue; border-radius: 50%"></div> (blue)</div><br/>

- **CONFIG** - `mo 3`,  **Danger layer**, contains keyboard specific keybinds such as handling ZMK Bluetooth profiles, RGB lighting controls and dangerous `BOOTLOADER` keys. This access layer is purposely hidden in the `QWERTY` layer and is intentionally difficult to use to avoid accidentally entering BOOTLOAD or Bluetooth Select mode. <div style="display: flex; align-items: center;">RGB indicator light = <div style="margin-left: 5px; margin-right: 5px; height: 15px; width: 15px; background-color: lightgreen; border-radius: 50%"></div> (green)</div><br/>

### Note:
RGB Indicator colors are not configured by ZMK, they are a feature created by Kinesis.

---

<br/>

## ADV360-PRO-ZMK

The KA360 is built on top of ZMK. Kinesis have implemented their own solution for particular elements of the keyboard, e.g. the Indicator lighting.
 At this time, digging into the ZMK functionality is currently undocumented by Kinesis.
 <br/>

- **General support page:** https://kinesis-ergo.com/support/kb360pro/

- **Firmware installation guide:** https://kinesis-ergo.com/wp-content/uploads/Step-by-Step-Advantage360-Professional-Firmware-Installation-Instructions-KB360-PRO_v11-10-22.pdf

- **User manual:** https://kinesis-ergo.com/wp-content/uploads/Advantage360-ZMK-KB360-PRO-Users-Manual-v10-7-22.pdf

- **Quick guide:** https://kinesis-ergo.com/wp-content/uploads/Advantage360-Professional-QSG-v8-25-22.pdf
<br/>
<br/>

---
## ZMK

https://zmk.dev/docs


If ZMK is too obscure and you just want a keybinding, here is the Kinesis Mapping Gui:

https://kinesiscorporation.github.io/Adv360-Pro-GUI/

### Good forks
- https://github.com/adrienm7/Adv360-Pro-ZMK/tree/main/config

- https://github.com/chandlerc/Adv360-Pro-ZMK/blob/V2.0/config/keymap.json (Dvorak!)

### Useful links
- https://keyboardchecker.com/ (Check your keymap is actually triggering what you expect)
- http://www.keyboard-layout-editor.com/ Image map for keyboard layouts.

---
## K360 Keyboard Keymap template

```
//  *
//  * ,--------------------------------------------------.                                           ,--------------------------------------------------.                      
//  * |        |      |      |      |      |      |      |                                           |      |      |      |      |      |      |        |
//  * |--------+------+------+------+------+------+------|                                           |------+------+------+------+------+------+--------|
//  * |        |      |      |      |      |      |      |                                           |      |      |      |      |      |      |        |
//  * |--------+------+------+------+------+------+------|       ,-----+-----.  ,-----+-----.        |------+------+------+------+------+------+--------|
//  * |        |      |      |      |      |      |      |       |     |     |  |     |     |        |      |      |      |      |      |      |        |
//  * |--------+------+------+------+------+------+------' .-----+-----+-----|  |-----+-----+-----.  '------+------+------+------+------+------+--------|
//  * |        |      |      |      |      |      |        |     |     |     |  |     |     |     |         |      |      |      |      |      |        |
//  * |--------+------+------+------+------+------'        |     |     |-----|  |-----|     |     |         '------+------+------+------+------+--------|
//  * |        |      |      |      |      |               |     |     |     |  |     |     |     |                |      |      |      |      |        |
//  * `--------+------+------+------+------'               `-----+-----+-----'  `-----+-----+-----'                '------+------+------+------+--------'
//  *                       
//  *                        
//  *                       
//  */
//     [_LAYERINDEX] = LAYOUT(
//       _______, _______, _______, _______, _______, _______,                                     _______, _______, _______, _______, _______, _______,
//       _______, _______, _______, _______, _______, _______,                                     _______, _______, _______, _______, _______, _______,
//       _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______,
//                                  _______, _______, _______, _______, _______, _______, _______, _______, _______, _______
//     ),
```

---

## To build Firmware in GitHub Actions

### Setup

1. Fork this repo.
2. Enable GitHub Actions on your fork.

### Build firmware

1. Push a commit to trigger the build.
2. Download the artifact.

### Flash firmware

Resources can be found on Kinesis.com

https://kinesis-ergo.com/support/kb360pro/#firmware-updates

https://kinesis-ergo.com/support/kb360pro/#manuals


---

## To build Firmware locally using a container

### First run

Note: Either Podman or Docker is required, Podman is preferred if both are present.

1. Execute `make all`.
2. Check the `firmware` directory for the latest firmware build.

### Subsequent runs

If the only file you have changed is `config/adv360.keymap`, execute `make build` and check the `firmware` directory for the latest firmware build.

If you have changed other files in the `config` directory (such as `config/west.yml`) you will need to execute `make all` to rebuild the Docker image as well as the firmware.
