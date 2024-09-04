# TWRP Device Tree for Motorola Edge 30 Neo (miami)

## Setup repo tool
Setup repo tool from here https://source.android.com/setup/develop#installing-repo

## Compile

Sync TWRP manifest:

```
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
```

Create a manifest file `.repo/local_manifests/moto-miami.xml` with the following content:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
<project path="device/motorola/miami"
	name="moto-miami/twrp_device_motorola_miami"
	remote="github"
	revision="android-12.1" />
</manifest>
```
You might need to pick a few patches from https://gerrit.twrp.me to get some stuff working.

Sync the sources with:

```
repo sync -j$(nproc --all)
```

To build, execute this command:

```
. build/envsetup.sh; lunch twrp_miami-eng; mka bootimage
```

## Test

To temporarily boot it:

```
fastboot boot out/target/product/miami/boot.img
```

## Flash

To make twrp replace stock recovery, temporarily boot twrp and navigate
to advanced menu and select Flash Current TWRP option.

## Copyright

```
#
# Copyright (C) 2024 The Android Open Source Project
#
# SPDX-License-Identifier: Apache-2.0
#
```
