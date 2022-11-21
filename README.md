# ADV360-PRO-ZMK

The KA360 is built on top of ZMK. Kinesis have implemented their own solution for particular elements of the keyboard, e.g. the Indicator lighting.
 At this time, digging into the ZMK functionality is currently undocumented by Kinesis.

**General support page:** https://kinesis-ergo.com/support/kb360pro/

**Firmware installation guide:** https://kinesis-ergo.com/wp-content/uploads/Step-by-Step-Advantage360-Professional-Firmware-Installation-Instructions-KB360-PRO_v11-10-22.pdf

**User manual:** https://kinesis-ergo.com/wp-content/uploads/Advantage360-ZMK-KB360-PRO-Users-Manual-v10-7-22.pdf

**Quick guide:** https://kinesis-ergo.com/wp-content/uploads/Advantage360-Professional-QSG-v8-25-22.pdf

---
### ZMK

https://zmk.dev/docs


If ZMK is too obscure and you just want a keybinding, here is the Kinesis Mapping Gui:

https://kinesiscorporation.github.io/Adv360-Pro-GUI/

## Good forks
- https://github.com/adrienm7/Adv360-Pro-ZMK/tree/main/config

- https://github.com/chandlerc/Adv360-Pro-ZMK/blob/V2.0/config/keymap.json (Dvorak!)

## Useful links
- https://keyboardchecker.com/ (Check your keymap is actually triggering what you expect)

---
## Keyboard template

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
