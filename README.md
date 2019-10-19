# Mini ITX 4k 视频剪辑黑苹果 macOS 10.15 Catalina EFI

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
| 显卡 | 蓝宝石 RX580 8G 1411MHz Nitro+ 超白金 | 矿卡 |
| 无线网卡/蓝牙 | 博通 BCM94360CS2 | 需转接卡[替换主板原有模块 M.2 Key E 口](http://icyleaf.com/images/install-boardcom-module-to-motherboard.jpg) |
| 显示器 | LG 27UL600 4k HDR400 IPS | DisplayPort 接入 |

更多说明请看[攒了一台 4K 视频剪辑黑苹果](http://icyleaf.com/2019/01/itx-coffee-lake-hackintosh-build-for-4k-video-editing/)。

## 兼容情况

### 完美

- [x] macOS 版本
    - [x] 10.14.5 (使用 [10.14](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/tree/10.14) 分支)
    - [x] 10.15
- [x] 显卡（DisplayPort 接显示器）
    - [x] Intel UHD630 核显
    - [x] AMD RX580
- [x] 声卡(Realtek ALC1220)
    - [x] 主板后置
    - [x] 机箱前置
    - [x] DisplayPort 声音输出
- [x] 睡眠/唤醒
- [x] 有线网卡
- [x] 无线 WiFi
- [x] 蓝牙
    - [x] 耳机
    - [x] Trackpad 2
    - [x] Airdrop
    - [x] Handoff
- [x] 所有 USB 插口

### 可用不完美

- 雷电 3 口（可充电无数据）

## EFI

- Clover r5078
- ACPI
    - patched
        - SSDT-UIAC-ALL.aml
- drivers
    - UEFI
        - ApfsDriverLoader.efi
        - EmuVariableUefi.efi
        - FSInject.efi
- Kexts
    - 启动必备 (配合 Kext Utility/KextBeast 安装到系统)
        - FakeSMC.kext
        - Lilu.kext
        - WhateverGreen.kext
    - 声卡
        - AppleALC.kext
    - 有线网卡
        - IntelMausiEthernet.kext
    - 无线网卡 (配合 Kext Utility/KextBeast 安装到系统)
        - AirportBrcmFixup.kext
    - 蓝牙 (配合 Kext Utility/KextBeast 安装到系统)
        - BrcmFirmwareRepo.kext
        - BrcmPatchRAM2.kext

## 安装教程

### 前期准备

开机 F2 进入 BIOS 再按 F6 切换高级模式，至少需要做如下修改具体情况还需要看硬件情况：

- 高级（Advanced） > 芯片配置（Chipset Configuration） > VT-d -> Disabled
- 高级（Advanced） > USB 配置（USB Configuration） > XHCI Hand-off -> Enabled

### 安装黑苹果

请移步至[华擎 Z390 Gaming ITX 黑苹果安装教程](http://icyleaf.com/2019/03/asrock-z390-gaming-itx-install-hackintosh-tutorial/)

## 相同主板 EFI

- https://github.com/bydavy/EFI-ASRock-Z390-Phantom-Gaming
- https://github.com/kcunanan/Jared-PC/
- https://github.com/befuture/EFI-ASRock-Z390-Phantom-Gaming
