# HP-ZHAN66-AMD-hackintosh

## 说明

**本EFI仅供Ventura使用**

**在安装MacOS完成前请在config.plist中禁用nootedred.kext**

**本机型需要关闭快速启动**

**机型信息已删除，请自行生成更换**

**OpneCore版本0.9.2 release（Ventura）

---
## 总览

---
### 存在的问题
1.睡眠

2.内置麦克风、声卡

3.偶尔卡住，主要表现在刚开机或者某些需要硬件加速的情况，发热较严重

4.VCN（硬件编解码）暂时还有问题，具体请移至NootedRed页面查看最新进展

### 配置

---
部件|型号|是否支持
:-|:-|:-|
CPU|AMD Ryzen 7 3700U|支持
核显|AMD Radeon Vega 10 (Renoir)|支持
网卡|Intel AX200|支持，原装MTK7921不支持
硬盘|三星PM981A|不支持，更换PM9A1解决
触控屏|I2C HID|支持
键盘|PS2 controller|支持
触控屏|I2C ELAN|支持
蓝牙|Intel AX200|支持，原装MTK7921不支持
HDMI输出||支持
音频/3.5耳机接口|ALC267【ALC3247】|不支持
内存|DDR4 2400MHz|支持

---
## 了解你的EFI

---
### ACPI
SSDT | 作用
:---------|:---------
SSDT-PLUG-ALT | 用于MacOS识别CPU，必须
SSDT-EC | 欺骗MacOS的假EC，必须
SSDT-HPET | 解决IRQ冲突，必须
SSDT-SBUS-MCHC | 解决AppleSMBus
SSDT-USBX | USB电源管理，必须
SSDT-XOSI | MAC和WIN的ACPI功能，双系统必须
SSDT-ALS0 | NootedRed提供，用于屏幕亮度调整
SSDT-PNLF | NootedRed提供，用于屏幕亮度调整

---
### Kexts
Kext | 作用
:---------|:---------
AMDRyzenCPUPowerManagement | AMD CPU 电源管理
AppleALC | 音频驱动
AppleMCEReporterDisabler | 关闭AppleIntelMCEReporter，避免在AMD CPU的设备上报错
ECEnabler | 电池读取
Lilu | 必备
NVMeFix | NVMe硬盘电源管理
RestrictEvents | CPU改名
SMCAMDProcessor | AMDRyzenCPUPowerManagement的附属
SMCBatteryManager | 电池管理
USBToolBox | USB定制
VirtualSMC | 必备
VoodooPS2Controller | PS/2 键盘，需要在config中禁用voodoops2 input以避免与i2c的input冲突，不影响使用
NootedRed | AMD核显驱动
VoodooI2C | 触控板或触屏驱动
VoodooI2CHID | 触控板或触屏驱动
BrightnessKeys | 亮度调节按键
AirportItlwm | 英特尔网卡驱动，注意不同的系统有不同的kext
BlueToolFixup | 蓝牙驱动，Monterey中搭配IntelBluetoothFirmware使用
IntelBluetoothFirmware | 蓝牙驱动

英特尔网卡的蓝牙驱动组合: 
Monterey/Ventura: IntelBluetoothFirmware+BlueToolFixup+IntelBluetoothFirmware

### 致谢

---
感谢NootedRed的开发者们，使得AMD核显黑苹果成为可能
>https://github.com/NootInc/NootedRed

以及以下的教程和指导
>https://github.com/Zrc00/Lenovo-Xiaoxin-15ARE-AMD-4800U-Hackintosh
>https://github.com/depaler/RedmiBook-14-II-AMD-hackintosh
>https://github.com/izumiiAoba/hackintosh-thinkpad-x13-gen2
>https://github.com/iamthaoly/amd-laptop-hackintosh
>https://github.com/zabdottler/Lenovo-Yoga-16S-hackintosh

---


