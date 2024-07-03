# Synology M2 volume

<a href="https://github.com/007revad/Synology_M2_volume/releases"><img src="https://img.shields.io/github/release/007revad/Synology_M2_volume.svg"></a>
<a href="https://hits.seeyoufarm.com"><img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2F007revad%2FSynology_M2_volume&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=views&edge_flat=false"/></a>
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/paypalme/007revad)
[![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/007revad)
[![committers.top badge](https://user-badge.committers.top/australia/007revad.svg)](https://user-badge.committers.top/australia/007revad)

### 描述

轻松在 Synology NAS 上创建 M.2 卷，无需大量输入，也无需任何操作指南。而且您不需要Synology 品牌的 NVMe 驱动器。

该脚本在您的 NVMe 驱动器上创建 RAID 和存储池，以便您可以在存储管理器中创建卷。

您所要做的就是运行脚本并输入 yes 和 1、2、3 或 4 来回答一些简单的问题。然后转到存储管理器并选择创建卷。

它还允许您创建跨内部 NVMe 驱动器和 Synology M.2 PCIe 卡中的 NVMe 驱动器的存储池/卷。

对于 Xpenology 用户，该脚本支持无限数量的 NVMe 驱动器（RAID 1 和 Basic 除外）。

**支持 DSM 7 及更高版本** 

For [DSM 6 use v1](https://github.com/007revad/Synology_M2_volume/releases/tag/v1.3.25) and run **without** the auto update option.
对于DSM 6，使用 v1并且在没有自动更新选项的情况下运行。

**v2 中的新功能**
- 现在显示“M.2 驱动器#”，与存储管理器相同。
现在使用 synostgpool 命令，它允许以下操作:(感谢 reddit 上的 Severe_Pea_2128）
现在支持 JBOD、SHR、SHR2 和 RAID F1。
增加了多卷或单卷存储池的选择。多卷允许超额配置。
添加了跳过驱动器检查的选项。
运行脚本后不再需要重新启动。
不再需要进行在线组装。
删除了驱动器检查进度，因为 synostgpool 无法实现此操作。
您可以在存储管理器中查看驱动器检查进度。
删除了空运行模式，因为 synostgpool 无法实现该模式。
删除了对 SATA M.2 驱动器的支持。
如果您有 SATA M.2 驱动器，请使用 v1并且在没有自动更新选项的情况下运行。
https://github.com/007revad/Synology_M2_volume/releases/tag/v1.3.25

###支持的 RAID 级别

| RAID 级别  | 所需最小硬盘数  | 最大硬盘数 | 脚本版本 |
| ----------- |------------------|----------------|----------------|
| SHR 1       | 1 or more drives | Unlimited      | v2 and later (DSM 7 only) |
| SHR 2       | 4 or more drives | Unlimited      | v2 and later (DSM 7 only) |
| Basic       | 1 drive          | 1 drive        | all |
| JBOD        | 1 or more drives | Unlimited      | v2 and later (DSM 7 only) |
| RAID 0      | 2 or more drives | Unlimited      | all |
| RAID 1      | 2 or more drives | 4 drives       | all |
| RAID 5      | 3 or more drives | Unlimited      | all |
| RAID 6      | 4 or more drives | Unlimited      | v1.3.15 and later |
| RAID 10     | 4 or more drives | Unlimited      | v1.3.15 and later |
| RAID F1     | 3 or more drives | Unlimited      | v2 and later (DSM 7 only) |

如果选择了 RAID F1，则脚本将在未正式支持 RAID F1 的 Synology 型号上启用 RAID F1。

### Confirmed working on

<details>
  <summary>Click here to see list</summary>

| Model        | DSM version              | M.2 card  | Notes           |
| ------------ |--------------------------|-----------|-----------------|
| All          | DSM 6                    |           | [Use v1](https://github.com/007revad/Synology_M2_volume/releases/tag/v1.3.25) run without auto update option |
| RS2423+      | DSM 7.2-64570 Update 1   |           |
| DS1823xs+    | DSM 7.2-64561            | M2D20     |
| DS923+       | DSM 7.2.1-69057 Update 5 |           |
| DS923+       | DSM 7.2.1-69057 Update 2 |           |
| DS923+       | DSM 7.1.1-42962 Update 5 |           |
| DS723+       | DSM 7.2.1-69057 Update 3 |           |
| DS723+       | DSM 7.2-64570 Update 1   |           |
| DS723+       | DSM 7.1.1-42962 Update 4 |           |
| DS423+       | DSM 7.2.1-69057 Update 3 |           |
| DS423+       | DSM 7.2-64570 Update 3   |           |
| DS423+       | DSM 7.1.1-42962 Update 4 |           |
| DS3622xs+    | DSM 7.2-64216 Beta       | E10M20-T1 |
| DS3622xs+    | DSM 7.1.1-42962 Update 1 |           |
| DS2422+      | DSM 7.2.1-69057 Update 4 | E10M20-T1 |
| DS1522+      | DSM 7.2.1-69057 Update 4 |           |
| DS1522+      | DSM 7.2-64570            |           |
| DS1522+      | DSM 7.1.1-42962 Update 4 |           |
| DS1821+      | DSM 7.2.1-69057 Update 4 | E10M20-T1 | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1821+      | DSM 7.2.1-69057 Update 4 | M2D20     | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1821+      | DSM 7.2.1-69057 Update 4 | M2D18     | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1821+      | DSM 7.2.1-69057 Update 4 |           |
| DS1821+      | DSM 7.2.1-69057 Update 3 |           |
| DS1821+      | DSM 7.2.1-69057 Update 2 |           |
| DS1821+      | DSM 7.2.1-69057 Update 1 |           |
| DS1821+      | DSM 7.2.1-69057          |           |
| DS1821+      | DSM 7.2-64570 Update 3   |           |
| DS1821+      | DSM 7.2-64570 Update 1   | E10M20-T1 | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1821+      | DSM 7.2-64570 Update 1   | M2D18     | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1821+      | DSM 7.2-64570 Update 1   |           |
| DS1821+      | DSM 7.2-64570            |           |
| DS1821+      | DSM 7.2-64561            |           |
| DS1821+      | DSM 7.2-64216 Beta       |           |
| DS1821+      | DSM 7.2-64213 Beta       |           |
| DS1821+      | DSM 7.1.1-42962 Update 4 |           |
| DS1621+      | DSM 7.2-64570 Update 1   | E10M20-T1 | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1621+      | DSM 7.2-64570 Update 1   |           |
| DS1621+      | DSM 7.1.1-42962 Update 4 |           |
| RS1221+      | DSM 7.2-64570 Update 1   | E10M20-T1 |
| RS1221+      | DSM 7.1.1                | E10M20-T1 |
| DS1520+      | DSM 7.2.1-69057 Update 2 |           |
| DS1520+      | DSM 7.2-64570 Update 1   |           |
| DS1520+      | DSM 7.1.1-42962 Update 4 |           |
| DS920+       | DSM 7.2.1-69057 Update 5 |           |
| DS920+       | DSM 7.2.1-69057 Update 4 |           |
| DS920+       | DSM 7.2.1-69057 Update 3 |           |
| DS920+       | DSM 7.2.1-69057 Update 2 |           |
| DS920+       | DSM 7.2.1-69057 update 1 |           |
| DS920+       | DSM 7.2.1-69057          |           |
| DS920+       | DSM 7.2-64570 Update 1   |           |
| DS920+       | DSM 7.2-64561            |           |
| DS920+       | DSM 7.2-64216 Beta       |           |
| DS920+       | DSM 7.1.1-42962 Update 1 |           |
| DS918+       | DSM 7.2-64570 Update 3   |           |
| RS820+       | DSM 7.2-64570 Update 3   | M2D20     |
| DS720+       | DSM 7.2.1-69057 Update 4 |           |
| DS720+       | DSM 7.2.1-69057 Update 3 |           |
| DS720+       | DSM 7.2.1-69057 Update 2 |           |
| DS720+       | DSM 7.2.1-69057 Update 1 |           |
| DS720+       | DSM 7.2.1-69057          |           |
| DS720+       | DSM 7.2-64570 Update 3   |           |
| DS720+       | DSM 7.2-64570 Update 1   |           |
| DS720+       | DSM 7.2-64570            |           |
| DS720+       | DSM 7.2-64561            |           |
| DS720+       | DSM 7.2-64216 Beta       |           |
| DS420+       | DSM 7.2-64570 Update 1   |           |
| DS1819+      | DSM 7.2-64216 Beta       | M2D20     |
| DS1819+      | DSM 7.1.1                | M2D20     |
| DS1019+      | DSM 7.2.1-69057 Update 2 |           |
| DS1019+      | DSM 7.2-64561            |           |
| DS1019+      | DSM 7.1.1-42962 Update 4 |           |
| DS1618+      | DSM 7.1.1                | M2D18     |
| DS918+       | DSM 7.2.1-69057 Update 5 |           |
| DS918+       | DSM 7.2-64561            |           |
| DS918+       | DSM 7.1.1                |           |
| DS3617xs     | DSM 7.2-64570            | M2D20     |

</details>

### Important

If you later update DSM and your M.2 drives are shown as unsupported and the storage pool is shown as missing, and online assemble fails, you need to run the <a href="https://github.com/007revad/Synology_HDD_db">Synology_HDD_db</a> script. The <a href="https://github.com/007revad/Synology_HDD_db">Synology_HDD_db</a> script should run after every DSM update.

### Download the script

1. Download the latest version _Source code (zip)_ from https://github.com/007revad/Synology_M2_volume/releases
2. Save the download zip file to a folder on the Synology.
3. Unzip the zip file.

### To run the script via SSH

[How to enable SSH and login to DSM via SSH](https://kb.synology.com/en-global/DSM/tutorial/How_to_login_to_DSM_with_root_permission_via_SSH_Telnet)

```YAML
sudo -s /volume1/scripts/syno_create_m2_volume.sh
```

**Note:** Replace /volume1/scripts/ with the path to where the script is located.

### Troubleshooting

If the script won't run check the following:

1. If the path to the script contains any spaces you need to enclose the path/scriptname in double quotes:
   ```YAML
   sudo -s "/volume1/my scripts/syno_create_m2_volume.sh"
   ```
2. Make sure you unpacked the zip or rar file that you downloaded and are trying to run the syno_create_m2_volume.sh file.
3. Set the syno_create_m2_volume.sh file as executable:
   ```YAML
   sudo chmod +x "/volume1/scripts/syno_create_m2_volume.sh"
   ```

### Options:
```YAML
  -a, --all        List all M.2 drives even if detected as active
  -s, --steps      Show the steps to do after running this script
  -h, --help       Show this help message
  -v, --version    Show the script version
```

### What to do after running the script

1. Create the volume as you normally would:
    - Select the new Storage Pool > Create > Create Volume.
    - Set the allocated size.
      - Optionally enter a volume description. Be creative :)
    - Click Next.
    - Select the file system (Btrfs or ext4) and click Next.
    - Optionally enable *Encrypt this volume* and click Next.
      - Create an encryption password or enter your existing encryption password. 
    - Confirm your settings and click Apply to finish creating your M.2 volume.
4. Optionally enable and schedule TRIM:
    - Storage Pool > ... > Settings > SSD TRIM    
    - **Note: DSM 7.1.1. has no SSD TRIM setting for M.2 storage pools**
    - **Note: DSM 7.2 Beta has no SSD TRIM setting for M.2 RAID 0 or RAID 5**

-----
### How to repair a NVMe storage pool or upgrade to larger drives

- Repair degraded storage pool in DSM 7.2 or later
  - [Repair NVMe RAID 1 in internal M.2 slots](https://github.com/007revad/Synology_M2_volume/wiki/Repair-M.2-RAID-1-in-internal-M.2-slots)
  - [Repair NVMe RAID 1 in adaptor card](https://github.com/007revad/Synology_M2_volume/wiki/Repair-M.2-RAID-1-in-adaptor-card)
- Upgrade to larger NVMe drives in DSM 7.2 or later
  - [Replace M.2 RAID 1 with larger drives](https://github.com/007revad/Synology_M2_volume/wiki/Replace-M.2-RAID-1-with-larger-drives)
- Repair via SSH for DSM 6
  - [How Synology Support repairs RAID in DSM 6](https://github.com/007revad/Synology_M2_volume/wiki/Repair-RAID-via-SSH)

-----
### DSM 7 screen shots

<p align="center">Create SHR Storage Pool</p>
<p align="center"><img src="/images/create_shr_v2.png"></p>

<p align="center">Create Volume</p>
<p align="center"><img src="/images/create-volume1.png"></p>

<p align="center">Volume description</p>
<p align="center"><img src="/images/create-volume3.png"></p>

<p align="center">Allocate volume capacity</p>
<p align="center"><img src="/images/create-volume2.png"></p>

<p align="center">Select file system</p>
<p align="center"><img src="/images/create-volume4.png"></p>

<p align="center">Success!</p>
<p align="center"><img src="/images/create-volume5.png"></p>

<p align="center">Enable TRIM</p>
<p align="center"><img src="/images/create_m2_volume_enable_trim.png"></p>


