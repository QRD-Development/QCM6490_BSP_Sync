# Qualcomm Products Board Support Package (BSP) HLOS Sync scripts

## Why was these scripts created?
1. These scripts was created to automate the process of syncing the Qualcomm Products Board Support Package (BSP) sources.
2. Qualcomm had released the "Release Note" for every Software Product (SP), but sometimes it's hard to find the correct sources or hard to use for the SP.
3. These scripts helps to sync the Qualcomm Products BSP sources easily.

## How to use?
1. Clone this repository
2. Run the scripts with the following command

#### Sync all Sources (QSSI & Vendor Open Source parts)
```bash
$ bash setup.sh
```

#### Sync Qualcomm private code (QSSI & Vendor Closed Source parts)
###### Note: You need to have access to the Qualcomm ChipCode website to download the private code.
- Download the Qualcomm private code from the Qualcomm ChipCode Website or use Git to clone the private code repository.
- For example, the QCM6490 BSP private code is located at `https://chipcode.qti.qualcomm.com/qualcomm/qcm6490-la-3-0_ap_standard_oem`
- So clone the private code repository using the following command
```bash
$ git clone -b r00082.2 --depth 1 https://qpm-git.qualcomm.com/home2/git/qualcomm/qcm6490-la-3-0_ap_standard_oem.git
```
- Notes: 
  1. The `r00082.2` is the tag name of the private code. You can use the latest tag name.
  2. The `--depth 1` is used to clone the latest commit only. You can remove it to clone the full repository.
  3. Don't place the private code directory inside the OpenSources repository directory. Keep it separate.
  - For example, the directory structure should be like this:
  ```bash
  ├── QCM6490_BSP_Sync
  │   ├── .gitignore
  │   ├── build.sh
  │   ├── qssi.xml
  │   ├── README.md
  │   ├── setup.sh
  │   └── target.xml
  └── qcm6490-la-3-0_ap_standard_oem
      ├── about.html
      ├── ADSP.HT.5.5
      ├── adsp_proc
      ├── AOP.HO.3.0
      ├── aop_proc
      ├── boot_images
      ├── BOOT.MXF.1.0
      ├── BTFW.HSP.2.0.0
      ├── BTFW.HSP.2.1.0
      ├── BTFW.MOSELLE.1.1.0
      ├── btfw_proc
      ├── CDSP.HT.2.5
      ├── cdsp_proc
      ├── common
      ├── contents.xml
      ├── CPUCP.FW.1.0
      ├── cpucp_proc
      ├── LA.QSSI.11.0
      ├── LA.UM.9.14.1
      ├── LINUX
      ├── MPSS.HI.4.3.3
      ├── QCM6490_apps_qssi
      ├── QCM6490_apps_qssi13
      ├── QCM6490_btfm
      ├── QCM6490_btfm_hsp
      ├── QCM6490_modem
      ├── QCM6490_wlan_hsp
      ├── qtee_tas
      ├── trustzone_images
      ├── TZ.APPS.2.0
      ├── TZ.XF.5.11
      ├── WLAN.MSL.1.0.1
      └── wlan_proc
  ```

- Copy the private code to the `vendor/qcom/proprietary` directory.
```bash
$ /bin/cp -rf qcm6490-la-3-0_ap_standard_oem/QCM6490_apps_qssi13/LINUX/android/vendor/qcom/proprietary QCM6490_BSP_Sync/LA.QSSI.13.0/vendor/qcom

$ /bin/cp -r qcm6490-la-3-0_ap_standard_oem/QCM6490_apps_qssi/LINUX/android/vendor/qcom/proprietary QCM6490_BSP_Sync/LA.UM.9.14.1/vendor/qcom

$ /bin/cp -rf qcm6490-la-3-0_ap_standard_oem/LINUX/android/vendor/qcom/proprietary/* QCM6490_BSP_Sync/LA.UM.9.14.1/vendor/qcom/proprietary/
```

#### Build/Compile QCM6490 HLOS
```bash
$ bash build.sh
```

## License
These scripts is licensed under the GPL-3.0 License. See the [LICENSE](LICENSE) file for details.

## Credits
- [Qualcomm Technologies, Inc.](https://www.qualcomm.com/)
- [Qualcomm Chipcode](https://chipcode.qti.qualcomm.com)
- [CodeLinaro](https://git.codelinaro.org/)
- [Jyotiraditya](https://github.com/imjyotiraditya)
- [EdwardWu](https://github.com/bluehomewu)
- [QRD-Development](https://github.com/QRD-Development)

