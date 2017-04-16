dump-android-partitions
=======================

## Overview
Dump all partitions on an Android device from PC via adb

## Description
(REQUIRES ROOT maybe on your Android device)
A list of partitions is gotten from the device's /dev/block/**/by-name by default.


## Demo
    $ adb devices -l
    List of devices attached
    XXXXXXXXXX             device product:shamu model:Nexus_6 device:shamu
    
    $ dump-android-partitions -a
    (1/42)aboot:
    (2/42)abootBackup:
    (3/42)boot:
    (4/42)cache:
    (5/42)cid:
    (6/42)ddr: excluded.
    (7/42)frp: excluded.
    (8/42)keystore:
    (9/42)kpan:
    (10/42)logo:
    (11/42)logs:
    (12/42)mdm1dhob:
    (13/42)mdm1hob:
    (14/42)mdm1m9kefs1:
    (15/42)mdm1m9kefs2:
    (16/42)mdm1m9kefs3:
    (17/42)mdm1m9kefsc:
    (18/42)metadata: excluded.
    (19/42)misc: excluded.
    (20/42)modem:
    (21/42)oem:
    (22/42)padA:
    (23/42)padB:
    (24/42)padC:
    (25/42)padD:
    (26/42)persist: excluded.
    (27/42)recovery:
    (28/42)rpm:
    (29/42)rpmBackup:
    (30/42)sbl1:
    (31/42)sbl1bak:
    (32/42)sdi:
    (33/42)sec: excluded.
    (34/42)sp:
    (35/42)ssd: excluded.
    (36/42)system:
    (37/42)tz:
    (38/42)tzBackup:
    (39/42)userdata: excluded.
    (40/42)utags:
    (41/42)utagsBackup:
    (42/42)versions:
    $ ls
    aboot.img
    abootBackup.img
    boot.img
    cache.img
    cid.img
    keystore.img
    kpan.img
    logo.img
    logs.img
    mdm1dhob.img
    mdm1hob.img
    mdm1m9kefs1.img
    mdm1m9kefs2.img
    mdm1m9kefs3.img
    mdm1m9kefsc.img
    modem.img
    oem.img
    padA.img
    padB.img
    padC.img
    padD.img
    recovery.img
    rpm.img
    rpmBackup.img
    sbl1.img
    sbl1bak.img
    sdi.img
    sp.img
    system.img
    tz.img
    tzBackup.img
    utags.img
    utagsBackup.img
    versions.img


## Requirement
* adb command on your PC
* adb debug switch is ON on your Android device.
* read permissions for partitions-device-file's directory (/dev/block/**/by-name by default) on your Android device
* white permissions for working directory (/data/local/tmp by default) on your Android device

## Usage
    dump-android-partitions [-lvnt] [-p GLOB] [-s SERIAL] [-x EXCLUDE] [-w WORKDIR] {-a|PARTITION ...}
    dump-android-partitions -l {-a|PARTITION ...}
    dump-android-partitions -h
      -a
        dump all partitions except those designated with -x option
      -l
        list partition names on a device and exit
      -p GLOB
        A shell glob pattern to search directories that includes partition names as file(node) names
        example: dump-android-partitions -p /dev/block/platform/*/msm_sdcc.1/by-name
        To use multiple globs, you can repeat -p options.
        default: /dev/block/*/*/by-name /dev/block/*/*/*/by-name /dev/block/*/*/by-num /dev/block/*/*/*/by-num
      -s SERIAL
        use device with given serial number (overrides $ANDROID_SERIAL), same as adb command
      -t
        TEST mode.
        Get dumped images by both a traditional dd method and a cat method (dump-android-partitions is normailly used this),
        and compare both images by cmp command. If two images differ, perhaps the cat method is buggy.
      -w WORKDIR
        a working directory path on a remote adb device, used only on TEST mode.
        default: /data/local/tmp
      -x EXCLUDE
        A file includes partition names to be excluded from dumping
        default: dump.exclude
      -h
        print this message and exit
      -v
        verbosely echoing information messages
      -n
        dry-run
      PARTITION
        a partition name to be dumped


## Example


## Install
    sudo mkdir -p /usr/local/bin
    sudo cp dump-android-partitions /usr/local/bin

## Contribution
(now working)


## Licence
[GPL v3](https://www.gnu.org/licenses/lgpl.txt)


## Author
[for2ando/forzando](https://github.com/for2ando)


