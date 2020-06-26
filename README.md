# Mini ITX 4k 视频剪辑黑苹果 macOS 10.15 Catalina EFI

Geekbench 4 [CPU 测试报告](https://browser.geekbench.com/v4/cpu/14931592) | [OpenCL 独显测试报告](https://browser.geekbench.com/v4/compute/4634600)

## 装机清单

| 名称 | 品牌型号 | 备注 |
| --- | --- | --- |
| CPU | 英特尔 i7 9700k |  |
| 主板 | 华擎 Z390 Phantom Gaming itx/ac |  |
| 散热器 | 九州风神 船长 240 EX White RGB |  |
| 内存 | 海盗船 Vengeance LPX DDR4 3000 16G x 1 |  |
| 硬盘 | 三星 970 EVO 250G<br />西数 Black SN750 1T<br />东芝 DT01ACA300 3T | 双 SSD + 一 HDD |
| 机箱 | 追风者 215P ITX 侧透 RGB |  |
| 电源 | 讯景 XTR550 |  |
| 显卡 | 蓝宝石 RX580 8G 1411MHz Nitro+ 超白金 | 矿卡 |
| 无线网卡/蓝牙 | 博通 BCM94360CS2 | 需转接卡[替换主板原有模块 M.2 Key E 口](http://icyleaf.com/images/install-boardcom-module-to-motherboard.jpg) |
| 显示器 | LG 27UL600 4k HDR400 IPS | DisplayPort 接入 |

更多说明请看[攒了一台 4K 视频剪辑黑苹果](http://icyleaf.com/2019/01/itx-coffee-lake-hackintosh-build-for-4k-video-editing/)。

## 兼容情况

### 完美

- [x] BIOS 版本
    - [x] 1.5
- [x] macOS 版本
    - [x] [10.15.5](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/47)
    - [x] [10.15.4](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/41) - 问题：LG 显示器会自动开启 HDR
    - [x] [10.15.3](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/34)
    - [x] [10.15.2](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/33)
    - [x] [10.15.1](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/23)
    - [x] [10.15](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/tree/10.15)
    - [x] 10.14.5 (使用 [10.14](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/tree/10.14) 分支)
- [x] 显卡
    - [x] 单 4k 显示器（DisplayPort）
    - [x] [双 4k 显示器](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/36)（双 DisplayPort）
    - [x] Intel UHD630 核显
    - [x] AMD RX580
    - [x] AMD RX5700 XT [#30](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/30)
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

### 未知

- [ ] Sidecar (没有设备可以测试，[@KisCG 贡献开启方法](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/32))

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

### 升级 macOS 系统

争取尽我可能把升级步骤和注意事项记录下来提供给使用我的 EFI 的小伙伴们，如果如下没有罗列到升级的请看看 [upgrade](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues?utf8=%E2%9C%93&q=is%3Aissue+label%3Aupgrade) 标签的 Issues 有没有。

#### 10.15.2 升级 10.15.3

详情查看[#34](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/34)

#### 10.15.1 升级 10.15.2

详情查看[#33](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/33)

#### 10.15 升级 10.15.1

详情查看[#23](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/23)

#### 10.14 升级 10.15

详情查看[#16](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/16)

## 问题索引

- [tutorial](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/labels/tutorial): 分享和教程
- [success](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/labels/success): 成功解决问题或成功案例
- [colver](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/labels/clover): Clover 配置
- [memory card](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/labels/memory%20card): 内存相关
- [graphics card](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/labels/graphics%20card): 显卡相关

## 相同主板 EFI

- https://github.com/bydavy/EFI-ASRock-Z390-Phantom-Gaming
- https://github.com/kcunanan/Jared-PC/
- https://github.com/befuture/EFI-ASRock-Z390-Phantom-Gaming

## 教科书版黑苹果教程

- https://www.tonymacx86.com/threads/guide-asrock-z390-phantom-gaming-itx-ac-i9-9900k-rx-580.268992/
- https://www.tonymacx86.com/threads/success-asrock-z390-phantom-gaming-itx-tb3-igpu-mojave-sff-build.277418/
- https://www.tonymacx86.com/threads/success-gigabyte-designare-z390-thunderbolt-3-i7-9700k-amd-rx-580.267551/
