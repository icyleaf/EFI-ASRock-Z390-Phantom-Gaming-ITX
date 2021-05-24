# Mini ITX 4k 视频剪辑黑苹果 macOS 11 Big Sur EFI

Geekbench 5 [CPU 测试报告](https://browser.geekbench.com/v5/cpu/8065088) | [OpenCL 独显测试报告](https://browser.geekbench.com/v5/compute/2877627)

## 装机清单

| 名称 | 品牌型号 | 备注 |
| --- | --- | --- |
| CPU | 英特尔 i7 9700k |  |
| 主板 | 华擎 Z390 Phantom Gaming itx/ac |  |
| 散热器 | 九州风神 船长 240 EX White RGB |  |
| 内存 | 海盗船 Vengeance LPX DDR4 3000 16G x 2 |  |
| 硬盘 | 西数 Black SN750 1T<br />致钛 PC005 Active 1T<br />镁光 CT500MX 500G<br />东芝 DT01ACA300 3T | 三星 970 EVO 250G 使用佳翼 i9-GTR 做 U 盘 |
| 显卡 | 蓝宝石 RX580 8G 1411MHz Nitro+ 超白金 | 矿卡 |
| 无线网卡/蓝牙 | 博通 BCM94360CS2 | 需转接卡[替换主板原有模块 M.2 Key E 口](http://icyleaf.com/images/install-boardcom-module-to-motherboard.jpg) |
| 显示器 | LG 27UL600 4k HDR400 IPS<br>LG LM270WR5-SSB1 27 4k 背板 DIY 显示器<br>NV140QUM-N61 背板 15.6 4k 便携显示器 | (Mini)DisplayPort 接入 |
| 机箱 | 追风者 215P ITX 侧透 RGB |  |
| 电源 | 讯景 XTR550 |  |

更多说明请看[攒了一台 4K 视频剪辑黑苹果](http://icyleaf.com/2019/01/itx-coffee-lake-hackintosh-build-for-4k-video-editing/)。

## 兼容情况

从 2021 年 3 月 25 开始升级使用 OpenCore 方案。

### 完美

- [x] BIOS 版本
    - [x] 1.5
- [x] macOS 版本
    - [x] [11.0](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/51) - OpenCore
    - [x] 10.15.x (使用 [10.15](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/tree/10.15) 分支) - Clover
    - [x] 10.14.5 (使用 [10.14](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/tree/10.14) 分支) - Clover
- [x] 显卡
    - [x] 单/[双](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/36) 4k 显示器（DisplayPort）
    - [x] AMD RX580
- [x] 声卡(Realtek ALC1220)
    - [x] 主板后置
    - [x] 机箱前置
    - [x] DisplayPort 声音输出
- [x] 睡眠/唤醒
- [x] 有线网卡
- [x] 无线 WiFi
- [x] 蓝牙
    - [x] Handoff
    - [x] Airdrop
- [x] 所有 USB 插口

### 未知

- Intel UHD630 核显 (没有时间测试)

## 安装教程

### 前期准备

开机 F2 进入 BIOS 再按 F6 切换高级模式，至少需要做如下修改具体情况还需要看硬件情况：

- 高级（Advanced） > 芯片配置（Chipset Configuration） > VT-d -> Disabled
- 高级（Advanced） > USB 配置（USB Configuration） > XHCI Hand-off -> Enabled

### 安装黑苹果

请移步至[华擎 Z390 Gaming ITX 黑苹果安装教程](http://icyleaf.com/2019/03/asrock-z390-gaming-itx-install-hackintosh-tutorial/)

### 升级 macOS 系统

争取尽我可能把升级步骤和注意事项记录下来提供给使用我的 EFI 的小伙伴们，请移步到 [upgrade](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues?utf8=%E2%9C%93&q=is%3Aissue+label%3Aupgrade) 标签查看所有升级说明。

## 问题索引

- [tutorial](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/labels/tutorial): 分享和教程
- [success](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/labels/success): 成功解决问题或成功案例
- [opencore](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/labels/opencore): OpenCore 配置
- [memory card](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/labels/memory%20card): 内存相关
- [graphics card](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/labels/graphics%20card): 显卡相关
- [colver](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/labels/clover): Clover 配置 - **已切换 OpenCore，不再新增维护**

## 教科书版黑苹果教程

- https://www.tonymacx86.com/threads/guide-asrock-z390-phantom-gaming-itx-ac-i9-9900k-rx-580.268992/
- https://www.tonymacx86.com/threads/success-asrock-z390-phantom-gaming-itx-tb3-igpu-mojave-sff-build.277418/
- https://www.tonymacx86.com/threads/success-gigabyte-designare-z390-thunderbolt-3-i7-9700k-amd-rx-580.267551/

## 我的其他 EFI

- [ASUS 华硕 B150M A D3 MATX + QL3X + 核显 + HD7770](https://github.com/icyleaf/EFI-ASUS-B150M-A-D3-QL3X)
