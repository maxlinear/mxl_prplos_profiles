## Description:
 
This is repository of profiles for all Maxlinear supported hardware platforms. 

## Release Date
* 11th September 2026

## Release Highlights

```
* Updated the Wi-Fi MxL317xx WLAN firmware to wlan_7.2.460 r1840+a+115
* Upgraded to PON version 2.1.9
* Updated the SWUpdate software feature support.
* u-boot: add backward compatibility support
* mxl secure upgrade utility adaptation
* CPU Ingress QoS feature support for traffic prioritization
* Updated the Prpl Crypto API.

```

## Fixed issues

```
* PCF-2611 - OSPv2: mod-wanmgr-system: Handling Onboard BOSA and SFP Transitions
* QOS related Error logs keep getting printed on console
* Speed Test not working with IP Passthrough Enabled
* "Device.XPON.ONU.1.ANI.1.Transceiver.1.VendorName" is blank in PON network
* RG enters kernel panic after fiber disconnect/reconnect; HWWD resets device after ~4 minutes
* RG crash and unexpected reboot observed with kernel panic during overnight soak
* DVFS levels continuously toggle (High/Medium/Low) due to PM policy set to balance, causing inconsistent throughput and CPU utilization
* PON: VANI interface generates non-RFC4291 compliant IPv6 link-local address (EUI-64 deviation)
* Drift of Window seen on 7342 OLT with GLT-4 card
```

## Known issues

```
* PPW-2321 - uboot-tools: host build fails with PyPI swig 4.5.0 (PCRE2 8BIT CMake error)
* PCF-2229 - ospv2: iperf3 -R -u inside ipsec fails
* UDPST with MxL optimization is currently not functional due to the UDPST upgrade to version 9.0.0
```

## QuickStart:
 
Below are sample steps to build the Mxl UPDK Software for UPDK-9.2.11 Release.
 
Complete these steps to create the basic software build for the OSPv2,OSPv2 B,MxL25641‑HDK‑2 and MxL25641‑HDK‑2 SECURE with OpenWrt 24.10:
 
#### 1. Clone prplOS repository from prpl Foundation:

git clone -b prplware-v5.2.0 https://gitlab.com/prpl-foundation/prplos/prplos

#### 2. Select the configuration to build and synchronize files for building the UPDK Software:

cd prplos

#### 3. Clone the prplos_mxl_profiles repository to obtain the required profile for any platforms.

git clone -b updk_9.2.11_dev https://github.com/maxlinear/mxl_prplos_profiles.git

cp mxl_prplos_profiles/profiles/* profiles/

#### 4. Run the command which corresponds to the model:

a) OSPv2 A step and B step

./scripts/gen_config.py mxl_x86_osp_tb341_v2 mxl_wlan_hostap_ng_wav700 prpl

b) MxL25641‑HDK‑2

./scripts/gen_config.py mxl_x86_mb_urx mxl_wlan_hostap_ng_wav700 prpl

c) MxL25641‑HDK‑2 SECURE

./scripts/gen_config.py mxl_x86_mb_urx_sec mxl_wlan_hostap_ng_wav700 prpl

#### 5. Install the necessary patches to enable support for VLAN ID 0

These patches are located in the patches folder of the cloned mxl_prplos_profiles repository.

a) Navigate to the feeds/feed_prplos directory using this command:

cd feeds/feed_prplos/

b) Copy the feed_prplos-priority-tag.patch file from the patches folder of the

mxl_prplos_profiles repository using this command:

cp ../../mxl_prplos_profiles/patches/feed_prplos-priority-tag.patch .

c) Apply the patch using this command:

patch -p1 < feed_prplos-priority-tag.patch

d) Switch to prplos directory using this command:

cd ../../

#### 6. To build MxL25641‑HDK‑2 secure boot follow this step

Note: This step is specific to build secure boot for the MxL25641‑HDK‑2 only.

a) Create a prplos/dl directory using this command:

mkdir dl

b) Download the Trusted Execution Platform (TEP) firmware binary version 17.2.0.44 from myMxL.

c) Create a tar archive named tep_fw-17.2.0.44.tar.gz and copy this file to the prplos/dl directory.

d) Update the hash of tep_fw-17.2.0.44.tar.gz in feeds/tep_fw/tep_fw/Makefile : PKG_MIRROR_HASH.

#### 7. Type below command to start the build
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
