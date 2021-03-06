---
title: Microsoft Bluetooth Test Platform - BTP battery tests
description: Bluetooth Test Platform (BTP) Battery tests.
ms.assetid: 19caf4db-9303-47d1-be12-5ff4b2710bc8
ms.date: 2/14/2020
ms.localizationpriority: medium

---

# BTP Battery Tests #

The BTP battery tests will test the ability of the local system to observe battery level changes on a paired remote device.

## Setting up for testing ##

When using a radio with the Traduci, first check that the green power indicator, an optional yellow test LED, and 3 orange LEDs on the Traduci are on. Confirm that the SUT's Bluetooth radio is powered on and that the appropriate radio(s) are correctly plugged in to the Traduci. Currently the Bluefruit radio can **only** be plugged into JC. More detailed information on setting up can be found at [Setting up BTP](testing-BTP-setup.md).

Features and purchasing information for supported radios can be found at [Supported BTP Hardware](testing-BTP-hw.md).

## Running the battery tests ##

Navigate to the folder where the BTP package was extracted. It will typically be under `C:\BTP`. In a folder named after the version of the package, you will find the scripts referenced below. Then run either:

- `RunBatteryTests.bat <radio name>` from an elevated command prompt or
- `RunBatteryTests.ps1 <radio name>` from an elevated PowerShell console

Information on available radio name parameters can be found in [here](testing-BTP-hw.md#supported-radios).

You can also include the optional parameter `-VerboseLogs` at the end to get a more verbose output of inner operations of BTP.

When using the Traduci, as a test starts the red LED next to the 12 pin adapter will turn on once the command from the test to power the radio has been sent. This LED will be turned off at the end of every test. If it is on at the start of the next test due the previous test failing, we will attempt to power it down and power it back on to return it to a known state. If the power cycle fails, the test will fail due to the radio being in an unknown state.

## Capturing logs ##

To capture the Bluetooth logs follow the instructions for the [busiotools for Windows Repo on GitHub](https://github.com/microsoft/busiotools/blob/master/bluetooth/tracing/readme.md).
