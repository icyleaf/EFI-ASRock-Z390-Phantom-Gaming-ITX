# Mini ITX 4k 视频剪辑黑苹果 macOS 13 Ventura EFI

Geekbench 5 [CPU 测试报告](https://browser.geekbench.com/v5/cpu/12662933) | [OpenCL 独显测试报告](https://browser.geekbench.com/v5/compute/5789051)

## 装机清单

| 名称 | 品牌型号 | 备注 |
| --- | --- | --- |
| CPU | 英特尔 i7 9700k |  |
| 主板 | 华擎 Z390 Phantom Gaming itx/ac |  |
| 散热器 | 酷里奥屠龙 240A | 九州风神 船长 240 EX White RGB 过保后水泵头有问题  |
| 内存 | 海盗船 Vengeance LPX DDR4 3000 16G x 2 |  |
| 硬盘 | 西数 Black SN750 1T<br />致钛 PC005 Active 1T<br />镁光 CT500MX 500G<br />致钛 PC005 Active 256G<br />东芝 DT01ACA300 3T |  |
| 显卡 | 迪兰RX 5600xt 6G X 战神 | 新矿卡 |
| 无线网卡/蓝牙 | 博通 BCM94360CS2 | 需转接卡[替换主板原有模块 M.2 Key E 口](https://icyleaf.com/uploads/2019/03/28/install-boardcom-module-to-motherboard.jpg) |
| 显示器 | LG 27UL600 4k HDR400 IPS<br>LG LM270WR5-SSB1 27 4k 背板 DIY 显示器<br>NV140QUM-N61 背板 15.6 4k 便携显示器 | (Mini)HDMI 接入 |
| 机箱 | 追风者 215P ITX 侧透 RGB |  |
| 麦克风 | fifine K690<br />Comica VM10 Pro | 免驱，后置 USB 都可用 |
| 电源 | 利民 Thermalright 850W TR-TG850 ATX3.0 | 升级 5600XT 后讯景 XTR550 有点勉强 |

更多说明请看[攒了一台 4K 视频剪辑黑苹果](http://icyleaf.com/2019/01/itx-coffee-lake-hackintosh-build-for-4k-video-editing/)。

## 兼容情况

从 2021 年 3 月 25 开始升级使用 OpenCore 方案。

### 完美

- [x] BIOS 版本
    - [x] 4.40
    - [x] 1.5
- [x] macOS 版本
    - [x] [13.x](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/65) - OpenCore
    - [x] 12.x (使用 [12.6](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/tree/12.6) 分支) - OpenCore
    - [x] 11.x (使用 [11.6](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/tree/11.6) 分支) - OpenCore
    - [x] 10.15.x (使用 [10.15](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/tree/10.15) 分支) - Clover
    - [x] 10.14.5 (使用 [10.14](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/tree/10.14) 分支) - Clover
- [x] 显卡
    - [x] 单/[双](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/36)/[三](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/65#issuecomment-1321711241) 4k 显示器（DisplayPort+HDMI）
    - [x] [AMD RX5600XT](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/66)
    - [x] [AMD RX580](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues/67) - macOS Monterey 12
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
    - [ ] 前置 USB 外接麦克风无法识别
    - [ ] 多麦克风聚合设备后有一路输入会爆音

### 未知

- Intel UHD630 核显 (使用独显后没测试)

## 安装教程

### 前期准备

开机 F2 进入 BIOS 再按 F6 切换高级模式，至少需要做如下修改具体情况还需要看硬件情况：

菜单 | 条目 | 设置 | 建议值 | 备注
---|---|---|---|---
高级（Advanced）| 芯片配置（Chipset Configuration） | VT-d | Disabled | 关联 `DisableIoMapper`
| | | Share Mamory | 64M ~ 128M | 也叫 DVMT 太高可能会影响睡眠唤醒
高级（Advanced）| 存储配置（Storage Configuration）| SATA Mode | AHCI
高级（Advanced）|  USB 配置（USB Configuration）| XHCI Hand-off | Enabled | 插入 USB 设备不被卡
安全设置（Security） | Secure Boot | | Disabled
安全设置（Security） | Fast Boot | | Disabled
安全设置（Security） | CSM | | Disabled

### 安装黑苹果

使用 Clover 版本请移步至[华擎 Z390 Gaming ITX 黑苹果安装教程](http://icyleaf.com/2019/03/asrock-z390-gaming-itx-install-hackintosh-tutorial/)

### 跨版本升级 OpenCore 秘笈

- 下载 [OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools)
- OCAuxiliaryTools 挂载 `config.plist` 并同步最新版本的 [OpenCore](https://github.com/acidanthera/OpenCorePkg/releases) 和 Kexts
- 注意保存的变更项，检查无误后保存

### 升级 macOS 系统

争取尽我可能把升级步骤和注意事项记录下来提供给使用我的 EFI 的小伙伴们，请移步到 [upgrade](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues?utf8=%E2%9C%93&q=is%3Aissue+label%3Aupgrade) 标签查看所有升级说明。

## 问题索引

- [tutorial](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues?q=label%3Atutorial): 分享和教程
- [success](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues?q=label%3Asuccess): 成功解决问题或成功案例
- [opencore](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues?q=label%3Aopencore): OpenCore 配置
- [memory card](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues?q=label%3A%22memory+card%22): 内存相关
- [graphics card](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues?q=label%3A%22graphics+card%22): 显卡相关
- [clover](https://github.com/icyleaf/EFI-ASRock-Z390-Phantom-Gaming-ITX/issues?q=label%3Aclover): Clover 配置 - **已切换 OpenCore，不再新增维护**

## 教科书版黑苹果教程

- https://www.tonymacx86.com/threads/guide-asrock-z390-phantom-gaming-itx-ac-i9-9900k-rx-580.268992/
- https://www.tonymacx86.com/threads/success-asrock-z390-phantom-gaming-itx-tb3-igpu-mojave-sff-build.277418/
- https://www.tonymacx86.com/threads/success-gigabyte-designare-z390-thunderbolt-3-i7-9700k-amd-rx-580.267551/

## 我的其他 EFI

- [ASUS 华硕 B150M A D3 MATX + QL3X + 核（独）显 + HD7770](https://github.com/icyleaf/EFI-ASUS-B150M-A-D3-QL3X)
