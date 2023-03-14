# China Battery BMS

Fork from https://github.com/mytest4u/BMS

> **Warning**
> Use at your own risk, especially the firmware!

## Facts:
```
BMS: DR01 or DR-JC03
Capacity: from 60Ah, up to 300Ah
Where to buy: all over Aliexpress, like "PAPOOL LiFePO4"
```

## Connect to Victron Controller
First of when only DIP 6 is facing upwards, it's recognized as a "Pylontech battery" and the charge controller will not see any battery details like cell voltage, temps - so avoid using this mode.

### Cerbo GX
Buy a cable from Victron or build it yourself: [Cerbo GX: VE.Can to CAN-bus BMS cables manual](https://www.victronenergy.com/live/battery_compatibility:can-bus_bms-cable).
DIP 5 & DIP 6 up, conenct the special CAT cabel and enjoy the battery details.


### Venus OS
* [Venus OS on Pi: CAN Interfaces](https://github.com/victronenergy/venus/wiki/RaspberryPi-CAN-Interfaces)

Victron [Venus OS](https://github.com/victronenergy/venus) provides the Battery Can Bus drivers but not the Hardware port. So just get a [Waveshare RS485 CAN Pi HAT](https://www.waveshare.com/wiki/RS485_CAN_HAT) and connect GND, CAN-L (Low) to Pin 5 and CAN-H (High) to Pin 4.

There are certainly other options for non-Raspberry Pis Venus OS setups. So we do not need BMS support in [dbus-serialbattery](https://github.com/Louisvdw/dbus-serialbattery) / [issue support BMS DR-JC03](https://github.com/Louisvdw/dbus-serialbattery/issues/327).

## Battery Stack Setup
1. Connect the master pack with DIP 5 and 6 facing upwards, as indicated in the Victron connection instructions.
2. The pack will be recognized as an "LFP battery" and you can view the voltage of the highest and lowest cell under the "Details" section.
3. You can also see the number of packs online and if there's a pack preventing charging/discharging.

## [Documentation and Manuals](Docs) of the Akku
* DipSwitch, Reset...
* [Guidance - How To Communicate With Upper Computer.pdf](Docs/Guidance%20-%20How%20To%20Communicate%20With%20Upper%20Computer.pdf)
* [Battery Upgrade Process.pdf](Docs/Battery%20Upgrade%20Process.pdf)

## [DR Software](DR_Software) - Reading data/Firmware Upgrade Tool
* Set address to 0
* Password: 666666

## [Firmware](Firmware)

#### How to update the firmware
1. Connect the PC and battery using a cable, ensuring that DIP 1 is turned ON for PC connection.
2. Make sure to install the necessary RS485 drivers for the connection to be established.
3. Open the "DR-Application.exe" application and keep the window open.
4. Open the "index.html" file located in the "dist" folder using a web browser.
5. On the "Help" tab, change the language to English and enter the password 666666 if prompted.
6. In the "Settings" tab, select the "Update" option, choose the bin file, and initiate the flashing process (you will know it's working if the green LED on the battery is flashing).

or take a look at [Battery Upgrade Process.pdf](Docs/Battery%20Upgrade%20Process.pdf)

---

### Firmware Files (gladly PR new ones)
#### [`DR01_16S100JC03_V2 0 0_T1_V`](Firmware/DR01_16S100JC03_V2.0.0_T1_V.bin) - The V in the file stands for Victron

`sha256 96a0056fe39f611eaca99b5e9c753bf73fabed1b06a1ef61a0f659c9b8b9498d`
```
Product info 2.2
Hardware model T1_G
Product model JC03
Project code 16S100
Software version 2.01
Boot version 1.1
```

#### [`48V100AH`](Firmware/48V100AH.bin) - also detects the 120AH battery version
`sha256 377a63935bc880420edbaf2faf335d6700fa1701b2f09f6ecd427720856bd2f9`
```
Product info 2.2
Hardware model T1_V
Product model DR01
Project code 16S100JC03
Software version 2.0.0
Boot version 1.1
```

#### Untested

> **Info**
> Please commit if tested.

- BOOT_UP_KF01JC00014V2.4.bin
`sha256 649e54ece972b0706a18d90687674c584f596b8bad1b803fd2c6db2e2d4823b0`

- DR-HUANY04_16S100A_V1.0.3_T1_V.bin
`sha256 2ab40293fe1cc930837c42cb04495545e93a98633c7a6b8c0b7f2b2cdf014e05`

- DR01_16S100JC03_V2.0.0_T1_G.bin
`sha256 0e0ba2e8e551c005d1cd58bd3407c254c03bf80fc6b5fd6d6c3cc39c622d339a`

- DR01_16S100JC03_V2.0.0_T2_V_R.bin
`sha256 1045c8b26c0770612da1726135c0606075eeb9d43ef77526d3e939386367df5d`

- DR_SAIENSI01_16S100A_V1.0.3_T1_G.bin
`sha256 9bf6b00d5d507c91dd6141682beae771fb1754d74db53631df96c3aeb25205e2`