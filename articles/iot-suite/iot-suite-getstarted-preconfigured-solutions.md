<properties
	pageTitle="Get started with preconfigured solutions | Microsoft Azure"
	description="Follow this tutorial to learn how to deploy an Azure IoT Suite preconfigured solution."
	services=""
    suite="iot-suite"
	documentationCenter=""
	authors="dominicbetts"
	manager="timlt"
	editor=""/>

<tags
     ms.service="iot-suite"
     ms.devlang="na"
     ms.topic="hero-article"
     ms.tgt_pltfrm="na"
     ms.workload="na"
     ms.date="03/02/2016"
     ms.author="dobett"/>

# Tutorial: Get started with the IoT preconfigured solutions

## Introduction

Azure IoT Suite [preconfigured solutions][lnk-preconfigured-solutions] combine multiple Azure IoT services to deliver end-to-end solutions that implement common IoT business scenarios.

This tutorial shows you how to provision the *remote monitoring* preconfigured solution. It also walks you through the basic features of the remote monitoring preconfigured solution.

In order to complete this tutorial, you’ll need an active Azure subscription.

> [AZURE.NOTE]  If you don’t have an account, you can create a free trial account in just a couple of minutes. For details, see [Azure Free Trial][lnk_free_trial].

## Provision the remote monitoring preconfigured solution

1.  Log on to [azureiotsuite.com][lnk-azureiotsuite] using your Azure account credentials, and click **+** to create a new solution.

    > [AZURE.NOTE] If you're having trouble with the permissions required to provision a solution, take a look at [Permissions on the azureiotsuite.com site][lnk-permissions] for guidance.

2.  Click **Select** on the **Remote monitoring** tile.

3.  Enter a **Solution name** for your remote monitoring preconfigured solution.

4.  Select the **Region** and **Subscription** you want to use to provision the solution.

5.  Click **Create Solution** to begin the provisioning process. This typically takes several minutes to run.

## Wait for the provisioning process to complete

1. Click on the tile for your solution with **Provisioning** status.
 
2. Notice the **Provisioning states** as Azure services are deployed in your Azure subscription.

3. Once provisioning completes, the status changes to **Ready**.

4. Click on the tile and you'll see the details of your solution in the right-hand pane.

> [AZURE.NOTE] If you are encountering issues deploying the pre-configured solution, take a look at [Permissions on the azureiotsuite.com site][lnk-permissions] and the [FAQ][lnk-faq]. If the issues persist, please create a service ticket on the [portal][lnk-portal].

Are there details you'd expect to see that aren't listed for your solution? Give us feature suggestions on [User Voice](https://feedback.azure.com/forums/321918-azure-iot).

## View remote monitoring solution dashboard

The solution dashboard enables you to manage the deployed solution. For example, you can view telemetry, add devices, and configure rules.

1.  When the provisioning is complete and the tile for your preconfigured solution indicates **Ready**, click **Launch** to open your remote monitoring solution portal in a new tab.

    ![][img-launch-solution]

2.  By default, the solution portal shows the *solution dashboard*. You can select other views using the left-hand menu.

    ![][img-dashboard]

The dashboard displays the following information:

- The map displays the location of each device connected to the solution. When you first run the solution, there are four simulated devices. The simulated devices are implemented as Azure WebJobs, and the solution uses the Bing Maps API to plot information on the map.
- The **Telemetry History** panel plots humidity and temperature telemetry from a selected device in near real time and displays aggregate data such as maximum, minimum, and average humidity.
- The **Alarm History** panel shows recent alarm events when a telemetry value has exceeded a threshold. You can define your own alarms in addition to the examples created by the preconfigured solution.

## View solution device list

The device list shows all the registered devices in the solution. You view and edit device metadata, add or remove devices, and send commands to devices.

1.  Click **Devices** in the left-hand menu to show the *device list* for this solution.

    ![][img-devicelist]

2.  The device list shows that there are four simulated devices created by the provisioning process.

3.  Click on a device in the device list to view the device details.

    ![][img-devicedetails]

The **Device Details** panel contains three sections:

- The **Actions** section lists the actions you can perform on the device. If you disable the device it will no longer be allowed to send telemetry or receive commands. If you disable a device, you can then enable it again. You can add a rule associated with the device that triggers an alarm when a telemetry value exceeds a threshold. You can also send a command to a device. When a device first connects it tells the solution the commands it can respond to.
- The **Device Properties** section lists the device metadata. Some of this metadata comes from the device itself (such as the manufacturer) and some is generated by the solution (such as the created time). You can edit the device metadata from here.
- The **Authentication Keys** section lists the keys the device can use to authenticate with the solution.

## Send a command to a device

The device details pane shows all of the commands that a specific device supports and enables you to send commands to a device. When a device first starts, it sends information about the commands it supports to the solution.

1.  Click **Commands** in the device details pane for the selected device.

    ![][img-devicecommands]

2.  Select **PingDevice** from the command list.

3.  Click **Send Command**.

4.  You can see the status of the command in the command history.

    ![][img-pingcommand]

The solution tracks the status of each command it sends. Initially the result is **Pending**. When the device reports that it has executed the command, the result is set to **Success**.

## Add a new simulated device

1.  Navigate back to the device list.

2.  Click **+ Add A Device** in the bottom left corner to add a new device.

    ![][img-adddevice]

3.  Click **Add New** on the **Simulated Device** tile.

    ![][img-addnew]
    
    In addition to creating a new simulated device, you can also add a physical device if you choose to create a **Custom Device**. To learn more about this, see [Connect your device to the IoT Suite remote monitoring preconfigured solution][lnk-connecting-devices].

4.  Select **Let me define my own Device ID**, and enter a unique device ID name such as **mydevice_01**.

5.  Click **Create**.

    ![][img-definedevice]

6. In step 3 of **Add a simulated device** click **Done** to return to the device list.

7. You can view your device **Running** in the device list.

    ![][img-runningnew]

8. You can also view the simulated telemetry from your new device on the dashboard:

    ![][img-runningnew-2]

## Edit the device metadata

1.  Navigate back to the device list.

2.  Select your new device in the **Devices List**, and then click **Edit** to edit the **Device Properties**:

    ![][img-editdevice]

3. Scroll down and make a change to the latitude and longitude vales. Then click **Save changes to device registry**.

    ![][img-editdevice2]

4. Navigate back to the dashboard, the location of device has changed on the map:

    ![][img-editdevice3]

## Add a rule for the new device

There are no rules for the new device you just added. In this section you'll add a rule that triggers an alarm when the temperature reported by the new device exceeds 47 degrees. Before you start, notice that the telemetry history for the new device on the dashboard shows the device temperature never exceeds 45 degrees.

1.  Navigate back to the device list.

2.  Select your new device in the **Devices List**, and then click **Add rule** to add a new rule for the device.

3. Create a rule that uses **Temperature** as the data field and uses **AlarmTemp** as the output when the temperature exceeds 47 degrees:

    ![][img-adddevicerule]

4. Click **Save and View Rules** to save your changes.

5.  Click **Commands** in the device details pane for the new device.

    ![][img-adddevicerule2]

6.  Select **ChangeSetPointTemp** from the command list and set **SetPointTemp** to 45. Then click **Send Command**:

    ![][img-adddevicerule3]

7.  Navigate back to the solution dashboard. After a short time, you will see a new entry in the **Alarm History** pane when the temperature reported by your new device exceeds the 47 degree threshold:

    ![][img-adddevicerule4]

8. You can review and edit all your rules on the **Rules** page of the dashboard:

    ![][img-rules]

9. You can review and edit all the actions that can be taken in response to a rule on the **Actions** page of the dashboard:

    ![][img-actions]

> [AZURE.NOTE] It is possible to define actions that can send an email message or SMS in response to a rule or integrate with a line-of-business system through a [Logic App][lnk-logic-apps].

## Behind the scenes

When you deploy a preconfigured solution, the deployment process creates multiple resources in the Azure subscription you selected. You can view these resources in the Azure [portal][lnk-portal]. The deployment process creates a **resource group** with a name based on the name you chose for your preconfigured solution:

![][img-portal]

You can view the settings of each resource by selecting it in the list of resources in the resource group. The screenshot above shows the settings for the IoT hub used in the preconfigured solution.

You can also view the source code for the preconfigured solution. The remote monitoring preconfigured solution source code is in the [azure-iot-remote-monitoring][lnk-rmgithub]:

- The **DeviceAdministration** folder contains the source code for the dashboard.
- The **Simulator** folder contains the source code for the simulated device.
- The **EventProcessor** folder contains the source code for the back-end process that handles the incoming telemetry.

When you are done, you can delete the preconfigured solution from your Azure subscription on the [azureiotsuite.com][lnk-azureiotsuite] site - this enables you to easily delete all the resources that were provisioned when you created the preconfigured solution.

> [AZURE.NOTE] To ensure that you delete everything related to the preconfigured solution, delete it from m [azureiotsuite.com][lnk-azureiotsuite] and do not simply delete the resource group in the portal.

## Next Steps

Now that you’ve built a working preconfigured solution, you can move on to the following walkthroughs:

-   [Guidance on customizing preconfigured solutions][lnk-customize]
-   [Predictive maintenance preconfigured solution overview][lnk-predictive]

[img-launch-solution]: media/iot-suite-getstarted-preconfigured-solutions/launch.png
[img-dashboard]: media/iot-suite-getstarted-preconfigured-solutions/dashboard.png
[img-devicelist]: media/iot-suite-getstarted-preconfigured-solutions/devicelist.png
[img-devicedetails]: media/iot-suite-getstarted-preconfigured-solutions/devicedetails.png
[img-devicecommands]: media/iot-suite-getstarted-preconfigured-solutions/devicecommands.png
[img-pingcommand]: media/iot-suite-getstarted-preconfigured-solutions/pingcommand.png
[img-adddevice]: media/iot-suite-getstarted-preconfigured-solutions/adddevice.png
[img-addnew]: media/iot-suite-getstarted-preconfigured-solutions/addnew.png
[img-definedevice]: media/iot-suite-getstarted-preconfigured-solutions/definedevice.png
[img-runningnew]: media/iot-suite-getstarted-preconfigured-solutions/runningnew.png
[img-runningnew-2]: media/iot-suite-getstarted-preconfigured-solutions/runningnew2.png
[img-rules]: media/iot-suite-getstarted-preconfigured-solutions/rules.png
[img-editdevice]: media/iot-suite-getstarted-preconfigured-solutions/editdevice.png
[img-editdevice2]: media/iot-suite-getstarted-preconfigured-solutions/editdevice2.png
[img-editdevice3]: media/iot-suite-getstarted-preconfigured-solutions/editdevice3.png
[img-adddevicerule]: media/iot-suite-getstarted-preconfigured-solutions/addrule.png
[img-adddevicerule2]: media/iot-suite-getstarted-preconfigured-solutions/addrule2.png
[img-adddevicerule3]: media/iot-suite-getstarted-preconfigured-solutions/addrule3.png
[img-adddevicerule4]: media/iot-suite-getstarted-preconfigured-solutions/addrule4.png
[img-actions]: media/iot-suite-getstarted-preconfigured-solutions/actions.png
[img-portal]: media/iot-suite-getstarted-preconfigured-solutions/portal.png

[lnk_free_trial]: http://azure.microsoft.com/pricing/free-trial/
[lnk-preconfigured-solutions]: iot-suite-what-are-preconfigured-solutions.md
[lnk-azureiotsuite]: https://www.azureiotsuite.com
[lnk-customize]: iot-suite-guidance-on-customizing-preconfigured-solutions.md
[lnk-predictive]: iot-suite-predictive-overview.md
[lnk-connecting-devices]: iot-suite-connecting-devices.md
[lnk-permissions]: iot-suite-permissions.md
[lnk-logic-apps]: https://azure.microsoft.com/documentation/services/app-service/logic/
[lnk-portal]: http://portal.azure.com/
[lnk-rmgithub]: https://github.com/Azure/azure-iot-remote-monitoring
[lnk-faq]: iot-suite-faq.md
