# Mini ITX 4k 视频剪辑黑苹果 macOS 10.14 Mojave EFI

## 装机清单

| 名称 | 品牌型号 | 备注 |
| --- | --- | --- |
| CPU | 英特尔 i7 9700k |  |
| 主板 | 华擎 Z390 Phantom Gaming itx/ac |  |
| 散热器 | 九州风神 船长 240 EX White RGB |  |
| 内存 | 海盗船 Vengeance LPX DDR4 3000 16G x 1 |  |
| SSD | 三星 970 EVO 250G |  |
| 机箱 | 追风者 215P ITX 侧透 RGB |  |
| 电源 | 讯景 XTR550 |  |
| 显卡 | RX560\~580 | 预算超了暂时没有采购 |
| 无线网卡/蓝牙 | 博通 BCM94360CS2 | 临近春节没有买到 |
| 显示器 | LG 27UL600 4k HDR400 IPS | |

更多说明请看[攒了一台 4K 视频剪辑黑苹果](http://icyleaf.com/2019/01/itx-coffee-lake-hackintosh-build-for-4k-video-editing/)。

## 兼容情况

### 完美

- [x] Intel UHD630 核显（DisplayPort 接显示器）
- [x] 声卡
- [x] 睡眠/唤醒
- [x] 无线 WiFi（目前使用 USB 网卡后期会更换博通网络模块）
- [ ] 蓝牙 [WIP]（春节后更换博通网络模块）
    - [ ] Handoff
    - [ ] Airdrop

### 可以使用但不完美

- USB 插口（机箱前置无法使用）

### 没有测试

- 有线网卡（据说完美支持）

### 无法使用

- 雷电 3 口
- 显示器 DisplayPort 的声卡输出不识别

## EFI

- Clover r4871
- ACPI
    - patched
        - Z390-USB.aml
        - SSDT-UIAC-ALL.aml
- drivers64UEFI
    - AptioMemoryFix-64.efi
    - EmuVariableUefi-64.efi
    - HFSPlus.efi
    - ApfsDriverLoader-64.efi
    - SMCHelper-64.efi
- Kexts
    - 启动必备
        - FakeSMC.kext
        - Lilu.kext
        - USBInjectAll.kext
        - WhateverGreen.kext
    - 声卡
        - AppleALC.kext
        - VoodooHDA.kext
    - 有线网卡
        - IntelMausiEthernet.kext
    - 无线网卡
        - AirportBrcmFixup.kext
    - 蓝牙
        - WIP

## 安装教程

> 正在整理中