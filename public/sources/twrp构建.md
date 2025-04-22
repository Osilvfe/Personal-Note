添加ALLOW_MISSING_DEPENDENCIES := true以便使用minimal manifest进行编译工作


# 初始化

```shell
repo init --depth=1 -u [https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git](https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git) -b twrp-12.1
repo sync --force-sync
git clone --depth=1 -b twrp-12.1 [https://github.com/QRD-Development/twrp_device_qcom_lahaina.git](https://github.com/QRD-Development/twrp_device_qcom_lahaina.git) device/qcom/lahaina
. build/envsetup.sh
```

# 编译示例

```bash
lunch twrp_caihong-eng #一定要添加编译类型(user,userdebug,eng)
mka recoveryimage
```

# Errors

1.
```
Could not find ui.xml for TW_THEME: not set  
Set TARGET_SCREEN_WIDTH and TARGET_SCREEN_HEIGHT to automatically select  
an appropriate theme, or set TW_THEME to one of the following:  
landscape_hdpi landscape_mdpi portrait_hdpi portrait_mdpi watch_mdpi
```
添加编译类型