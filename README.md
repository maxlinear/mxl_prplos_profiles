## Description:
 
This is repository of profiles for all Maxlinear supported hardware platforms. 

## Release Date
* 29th June 2026

## Release Highlights

```
Fixes below issues:

* WLAN interface does not come up after changing the configuration from hidden SSID to non-hidden SSID
* Stability issue causing WLAN interfaces to go down after approximately 15 hours in a multi-client setup
* Hostapd crashes randomly when WLAN radio configurations are applied after boot
* tc commands failing when trying to create WMM stat queues
* lighttpd configuration fails when configured with PKCS#11 URI
* Default sessions cache not refreshed on netif status change

Enhancements:

* debugfs support for static pp session
* Configure MTU for VEIP interface to max available value
```

## Fixed issues

```
* PCF-2611 - OSPv2: mod-wanmgr-system: Handling Onboard BOSA and SFP Transitions
```

## Known issues

```
* PCF-2229 - ospv2: iperf3 -R -u inside ipsec fails
```

## QuickStart:
 
Below are sample steps to build the Mxl UPDK Software for UPDK-9.2.10-ER Release.
 
Complete these steps to create the basic software build for the OSPv2,OSPv2 B,MxL25641‑HDK‑2 and MxL25641‑HDK‑2 SECURE with OpenWrt 24.10:
 
#### 1. Clone prplOS repository from prpl Foundation:

git clone -b prplware-v5.1.0 https://gitlab.com/prpl-foundation/prplos/prplos

#### 2. Select the configuration to build and synchronize files for building the UPDK Software:

cd prplos

#### 3. Clone the prplos_mxl_profiles repository to obtain the required profile for any platforms.

git clone -b updk_9.2.10_dev https://github.com/maxlinear/mxl_prplos_profiles.git

cp mxl_prplos_profiles/profiles/* profiles/

#### 4. Run the command which corresponds to the model:

a) OSPv2 A step and B step

./scripts/gen_config.py mxl_x86_osp_tb341_v2 mxl_wlan_hostap_ng_wav700 prpl

b) MxL25641‑HDK‑2

./scripts/gen_config.py mxl_x86_mb_urx mxl_wlan_hostap_ng_wav700 prpl

c) MxL25641‑HDK‑2 SECURE

./scripts/gen_config.py mxl_x86_mb_urx_sec mxl_wlan_hostap_ng_wav700 prpl

#### 5. Type below command to start the build
make -j8
 
#### For more details please refer to the prpl foundation link below.
 
https://gitlab.com/prpl-foundation/prplos/prplos/-/wikis/Maxlinear-Open-Service-Platform/OSPv2

**OSPv2 A step Image Details**

| Category | File Name | Description | Location |
|----------|-----------|-------------|----------|
| **Single Image** | prplos-intel_x86-lgm-PRPL_OSP_v2-tb341_wav700-fullimage.itb | Single Full Image for ETH WAN / PON WAN | prplos/bin/targets/intel_x86/lgm/ |
| **SWUpdate Image** | prplos-intel_x86-lgm-PRPL_OSP_v2-tb341_wav700-image.swu | Software Upgrade Image | prplos/bin/targets/intel_x86/lgm/ |
| **U-Boot Binary** | u-boot.itb, u-boot-spl-emmc.bin | U-Boot binary file | prplos/bin/targets/intel_x86/lgm/uboot-octopus-urx641-overlay-fit-p34x-phy-emmc-prpl/ |
| **Root Filesystem** | prplos-intel_x86-lgm-PRPL_OSP_v2-rootfs.itb | RootFS image | prplos/bin/targets/intel_x86/lgm/ |
| **Kernel + DTB** | prplos-intel_x86-lgm-PRPL_OSP_v2-tb341_wav700-kernel.itb | Kernel and Device Tree Blob image | prplos/bin/targets/intel_x86/lgm/ |
| **EXT4 Filesystem** | ext4.fs | EXT4 filesystem image | prplos/bin/targets/intel_x86/lgm/ |
| **U-Boot Recovery** | u-boot-recovery.bin | U-Boot recovery image | prplos/bin/targets/intel_x86/lgm/uboot-octopus-urx641-overlay-fit-p34x-phy-emmc-prpl/ |

**OSPv2 B step Image Details**

| Category | File Name | Description | Location |
|----------|-----------|-------------|----------|
| **Single Image** | prplos-intel_x86-lgm-PRPL_OSP_v2-wgrtd159be_b_wav700-fullimage.itb | Single Full Image for ETH WAN / PON WAN | prplos/bin/targets/intel_x86/lgm/ |
| **SWUpdate Image** | prplos-intel_x86-lgm-PRPL_OSP_v2-wgrtd159be_b_wav700-image.swu | Software Upgrade Image | prplos/bin/targets/intel_x86/lgm/ |
| **U-Boot Binary** | u-boot.itb, u-boot-spl-emmc.bin | U-Boot binary file | prplos/bin/targets/intel_x86/lgm/uboot-octopus-urx641-4GB-ddr-overlay-fit-p34x-phy-emmc-prpl |
| **Root Filesystem** | prplos-intel_x86-lgm-PRPL_OSP_v2-rootfs.itb | RootFS image | prplos/bin/targets/intel_x86/lgm/ |
| **Kernel + DTB** | prplos-intel_x86-lgm-PRPL_OSP_v2-wgrtd159be_b_wav700-kernel.itb | Kernel and Device Tree Blob image | prplos/bin/targets/intel_x86/lgm/ |
| **EXT4 Filesystem** | ext4.fs | EXT4 filesystem image | prplos/bin/targets/intel_x86/lgm/ |
| **U-Boot Recovery** | u-boot-recovery.bin | U-Boot recovery image | prplos/bin/targets/intel_x86/lgm/uboot-octopus-urx641-4GB-ddr-overlay-fit-p34x-phy-emmc-prpl |

**For image flashing steps, please refer** [MaxLinear-Software-Upgrades-Downgrades](https://gitlab.com/prpl-foundation/prplos/prplos/-/wikis/MaxLinear-Open-Service-Platform/MaxLinear-Software-Upgrades-Downgrades)

**For flash layout details, please refer** [Flash layout in UPDK 9.2.10](https://gitlab.com/prpl-foundation/prplos/prplos/-/wikis/MaxLinear-Open-Service-Platform/flash-layout-updk-9.2.10)
