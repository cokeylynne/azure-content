<properties
   pageTitle="Install Update 2 on your StorSimple device | Microsoft Azure"
   description="Explains how to install StorSimple 8000 Series Update 2 on your StorSimple 8000 series device."
   services="storsimple"
   documentationCenter="NA"
   authors="alkohli"
   manager="carmonm"
   editor="" />
<tags
   ms.service="storsimple"
   ms.devlang="NA"
   ms.topic="article"
   ms.tgt_pltfrm="NA"
   ms.workload="TBD"
   ms.date="03/21/2016"
   ms.author="alkohli" />

# Install Update 2 on your StorSimple device

## Overview

This tutorial explains how to install Update 2 on a StorSimple device running an earlier software version via the Azure classic portal. The tutorial also covers the steps required for the update when a gateway is configured on a network interface other than DATA 0 of the StorSimple device and you are trying to update from a pre-Update 1 software version.

Update 2 includes device software updates, LSI driver updates, and disk firmware updates. The device software and LSI updates are non-disruptive updates and can be applied via the Azure classic portal. The disk firmware updates are disruptive updates and can only be applied via the Windows PowerShell interface of the device.

> [AZURE.IMPORTANT]

> -  You may not see Update 2 immediately because we do a phased rollout of the updates. Scan for updates in a few days again as this Update will become available soon.
> - A set of manual and automatic pre-checks are done prior to the install to determine the device health in terms of hardware state and network connectivity. These pre-checks are performed only if you apply the updates from the Azure classic portal.
> - We recommend that you install the software and driver updates via the Azure  classic portal. You should only go to the Windows PowerShell interface of the device (to install updates) if the pre-update gateway check fails in the portal. The updates may take 4-7 hours to install (including the Windows Updates). The maintenance mode updates must be installed via the Windows PowerShell interface of the device. As maintenance mode updates are disruptive updates, these will result in a down time for your device.
> - If running the optional StorSimple Snapshot Manager, ensure that you have upgraded your Snapshot Manager version to Update 2 prior to updating the device.

[AZURE.INCLUDE [storsimple-preparing-for-update](../../includes/storsimple-preparing-for-updates.md)]

## Install Update 2 via the Azure classic portal

Perform the following steps to update your device to [Update 2](storsimple-update2-release-notes.md).


> [AZURE.NOTE]
Update 2 enables Microsoft to pull additional diagnostic information from the device. As a result, when our operations team identifies devices that are having problems, we are better equipped to collect information from the device and diagnose issues. By accepting Update 2, you allow us to provide this proactive support.

[AZURE.INCLUDE [storsimple-install-update2-via-portal](../../includes/storsimple-install-update2-via-portal.md)]

12. Verify that your device is running **StorSimple 8000 Series Update 2 (6.3.9600.17673)**. The **Last updated date** should also be modified. You'll also see that Maintenance mode updates are available (this message might continue to be displayed for up to 24 hours after you install the updates).

    Maintenance mode updates are disruptive updates that result in device downtime and can only be applied via the Windows PowerShell interface of your device. In some cases when you are running Update 1.2, your disk firmware might already be up-to-date, in which case you don't need to install any maintenance mode updates.

13. Download the maintenance mode updates by using the steps listed in [To download hotfixes](#to-download-hotfixes) to search for and download KB3121899, which installs disk firmware updates (the other updates should already be installed by now).

13. Follow the steps listed in [install and verify maintenance mode hotfixes](#to-install-and-verify-maintenance-mode-hotfixes) to install the maintenance mode updates.


## Install Update 2 as a hotfix

Use this procedure if you fail the gateway check when trying to install the updates through the Azure classic portal. The check fails as you have a gateway assigned to a non-DATA 0 network interface and your device is running a software version prior to Update 1.

The software versions that can be upgraded using the hotfix method are Update 0.1, Update 0.2, and Update 0.3, Update 1, Update 1.1, and Update 1.2. The hotfix method involves the following three steps:

- Download the hotfixes from the Microsoft Update Catalog.
- Install and verify the regular mode hotfixes.
- Install and verify the maintenance mode hotfix.

To install Update 2 as a hotfix, you must download and install the following hotfixes:

| Order  | KB        | Description                    | Update type  |
|--------|-----------|-------------------------|------------- |
| 1      | KB3121901 | Software update         |  Regular     |
| 2      | KB3121900 | LSI driver              |  Regular     |
| 3      | KB3080728 | Storport fix </br> Windows Server 2012 R2 |  Regular     |
| 4      | KB3090322 | Spaceport fix </br> Windows Server 2012 R2 |  Regular     |
| 5      | KB3121899 | Disk firmware           | Maintenance  |


> [AZURE.IMPORTANT]
>
> - If your device is running Release (GA) version, please contact [Microsoft Support](storsimple-contact-microsoft-support.md) to assist you with the update.
> - This procedure needs to be performed only once to apply Update 2. You can use the Azure classic portal to apply subsequent updates.
> - Each hotfix installation can take about 20 minutes to complete. Total install time is close to 2 hours.
> - Before using this procedure to apply the update, make sure that both device controllers are online and all the hardware components are healthy.

Perform the following steps to apply this update as a hotfix.

[AZURE.INCLUDE [storsimple-install-update2-hotfix](../../includes/storsimple-install-update2-hotfix.md)]

[AZURE.INCLUDE [storsimple-install-troubleshooting](../../includes/storsimple-install-troubleshooting.md)]



## Next steps

Learn more about the [Update 2 release](storsimple-update2-release-notes.md).
