## Description:
 
This is repository of profiles for all Maxlinear supported hardware platforms. 

Select the appropriate profile to build images for any supported Maxlinear platform, as described in the QuickStart steps below.
 
## QuickStart:
 
Below are sample steps to build the Mxl UPDK Software for UPDK-9.2.3 Release.
 
Complete these steps to create the basic software build for the OSPv2,OSPv2 B,MxL25641‑HDK‑2, with OpenWrt 24.10:
 
#### 1. Clone prplOS repository from prpl Foundation:

git clone -b latest-24.10 https://gitlab.com/prpl-foundation/prplos/prplos

#### 2. Select the configuration to build and synchronize files for building the UPDK Software:

cd prplos

#### 3. Clone the prplos_mxl_profiles repository to obtain the required profile for any platforms.

git clone -b updk_9.2.3 https://github.com/maxlinear/mxl_prplos_profiles.git

cp mxl_prplos_profiles/profiles/* profiles/

#### 4. Run the command which corresponds to the model:

a) OSPv2 A step and B step

./scripts/gen_config.py mxl_x86_osp_tb341_v2 mxl_wlan_hostap_ng_wav700 prpl

b) MxL25641‑HDK‑2

./scripts/gen_config.py mxl_x86_mb_urx mxl_wlan_hostap_ng_wav700 prpl

#### 5. Type below command to start the build
make -j8

#### Note: Built images are located in the 'prplos/bin/targets/intel_x86/lgm/single-images' folder.
#### The U-Boot images for OSPv2 & MXL25641-HDK2 are located in the 'prplos/bin/targets/intel_x86/lgm/uboot-octopus-urx641-overlay-fit-p34x-phy-emmc-prpl/' folder.
#### The U-Boot images for OSPv2 B are located in the 'prplos/bin/targets/intel_x86/lgm/uboot-octopus-urx641-4GB-ddr-overlay-fit-p34x-phy-emmc-prpl/' folder
 
#### For more details please refer to the prpl foundation link below.
 
https://gitlab.com/prpl-foundation/prplos/prplos/-/wikis/Maxlinear-Open-Service-Platform/OSPv2
## Image Details:

#### OSPV2 Image details:

prplos-intel_x86-lgm-PRPL_OSP_v2-tb341_wav700_fullimage.fit  **->** **Fullimage for ETH WAN/PON WAN.**

prplos-intel_x86-lgm-PRPL_OSP_v2-tb341_wav700_kernel_dtb.fit  **->** **Kernel+dtb**

ext4.fs -> **ext4 file system.**

u-boot.itb, u-boot-plus-spl-emmc.bin                                          **->** **U-Boot binary file.**

u-boot-recovery.asc 							                                                   **->** **U-Boot recovery file.**

#### OSPV2-B Image details:
prplos-intel_x86-lgm-PRPL_OSP_v2-wgrtd159be_b_wav700_fullimage.fit             **->** **Fullimage for ETH WAN/PON WAN**

prplos-intel_x86-lgm-PRPL_OSP_v2-wgrtd159be_b_wav700_kernel_dtb.fit            **->** **Kernel+dtb.**

ext4.fs                                                                       **->** **ext4 file system.**

u-boot.itb, u-boot-plus-spl-emmc.bin                                          **->** **U-Boot binary file.**

u-boot-recovery.asc                                                           **->** **U-Boot recovery file.**

#### MxL25641‑HDK‑2 Image details:

prplos-intel_x86-lgm-PRPL_MB_URX-641_wav700_fullimage.fit                    **->** **Fullimage for ETH WAN/PON WAN.**

prplos-intel_x86-lgm-PRPL_MB_URX-641_wav700_kernel_dtb.fit                   **->** **kernel+dtb.**

ext4.fs                                                                      **->** **ext4 file system.**

u-boot.itb, u-boot-plus-spl-emmc.bin                                         **->** **U-Boot binary file.**

u-boot-recovery.asc                                                          **->** **U-Boot recovery file.**
