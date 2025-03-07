---
description: Power setting GUIDs identify power change events.
ms.assetid: 39D432A7-54F8-4135-B98C-7290F95B054A
title: Power Setting GUIDs (WinNT.h)
ms.topic: reference
ms.date: 05/31/2018
---

# Power Setting GUIDs

Power setting **GUID**s identify power change events. This topic lists power setting **GUID**s for notifications that are most useful to applications. An application should register for each power change event that might impact its behavior. Notification is sent each time a setting changes.

Power setting **GUID**s are defined in WinNT.h.

---

<span id="GUID_ACDC_POWER_SOURCE"></span>
<span id="guid_acdc_power_source"></span>
**GUID\_ACDC\_POWER\_SOURCE** (5D3E9A59-E9D5-4B00-A6BD-FF34FF516548)

The system power source has changed.

The **Data** member is a **DWORD** with a value from the [**SYSTEM\_POWER\_CONDITION**](/windows/desktop/api/WinNT/ne-winnt-system_power_condition) enumeration that indicates the current power source:

**PoAc** (0) - The computer is powered by an AC power source (or similar, such as a laptop powered by a 12V automotive adapter).

**PoDc** (1) - The computer is powered by an onboard battery power source.

**PoHot** (2) - The computer is powered by a short-term power source such as a UPS device.

---

<span id="GUID_BATTERY_PERCENTAGE_REMAINING"></span>
<span id="guid_battery_percentage_remaining"></span>
**GUID\_BATTERY\_PERCENTAGE\_REMAINING** (A7AD8041-B45A-4CAE-87A3-EECBB468A9E1)

The remaining battery capacity has changed. The granularity varies from system to system but the finest granularity is 1 percent.

The **Data** member is a **DWORD** that indicates the current battery capacity remaining as a percentage from 0 through 100.

---

<span id="GUID_CONSOLE_DISPLAY_STATE"></span>
<span id="guid_console_display_state"></span>
**GUID\_CONSOLE\_DISPLAY\_STATE** (6FE69556-704A-47A0-8F24-C28D936FDA47)

The current monitor's display state has changed.

**Windows 7, Windows Server 2008 R2, Windows Vista and Windows Server 2008:** This notification is available starting with Windows 8 and Windows Server 2012.

The **Data** member is a **DWORD** with a value from the **MONITOR_DISPLAY_STATE** enumeration:

**PowerMonitorOff** (0) - The display is off.

**PowerMonitorOn** (1) - The display is on.

**PowerMonitorDim** (2) - The display is dimmed.

---

<span id="GUID_GLOBAL_USER_PRESENCE"></span>
<span id="guid_global_user_presence"></span>
**GUID\_GLOBAL\_USER\_PRESENCE** (786E8A1D-B427-4344-9207-09E70BDCBEA9)

The user status associated with any session has changed. This represents the combined status of user presence across all local and remote sessions on the system.

This notification is sent only services and other programs running in session 0. User-mode applications should register for **GUID\_SESSION\_USER\_PRESENCE** instead.

**Windows 7, Windows Server 2008 R2, Windows Vista and Windows Server 2008:** This notification is available starting with Windows 8 and Windows Server 2012.

The **Data** member is a **DWORD** with one of the following values from the **USER_ACTIVITY_PRESENCE** enumeration:

**PowerUserPresent** (0) - The user is present in any local or remote session on the system.

**PowerUserInactive** (2) - The user is not present in any local or remote session on the system.

---

<span id="GUID_IDLE_BACKGROUND_TASK"></span>
<span id="guid_idle_background_task"></span>
**GUID\_IDLE\_BACKGROUND\_TASK** (515C31D8-F734-163D-A0FD-11A08C91E8F1)

The system is busy. This indicates that the system will not be moving into an idle state in the near future and that the current time is a good time for components to perform background or idle tasks that would otherwise prevent the computer from entering an idle state.

There is no notification when the system is able to move into an idle state. The idle background task notification does not indicate whether a user is present at the computer.

The **Data** member has no information and can be ignored.

---

<span id="GUID_LIDSWITCH_STATE_CHANGE"></span>
<span id="guid_lidswitch_state_change"></span>
**GUID\_LIDSWITCH\_STATE\_CHANGE** (BA3E0F4D-B817-4094-A2D1-D56379E6A0F3)

The state of the lid has changed (open vs. closed). The callback won't be called until a lid device is found and its current state is known.

0x0 - The lid is closed.

0x1 - The lid is opened.

---

<span id="GUID_MONITOR_POWER_ON"></span>
<span id="guid_monitor_power_on"></span>
**GUID\_MONITOR\_POWER\_ON** (02731015-4510-4526-99E6-E5A17EBD1AEA)

The primary system monitor has been powered on or off. This notification is useful for components that actively render content to the display device, such as media visualization. Applications should register for this notification and stop rendering graphics content when the monitor is off to reduce system power consumption.

The **Data** member is a **DWORD** that indicates the current monitor state:

0x0 - The monitor is off.

0x1 - The monitor is on.

**Windows 8 and Windows Server 2012:** New applications should use **GUID\_CONSOLE\_DISPLAY\_STATE** instead of this notification.

---

<span id="GUID_POWER_SAVING_STATUS"></span>
<span id="guid_power_saving_status"></span>
**GUID\_POWER\_SAVING\_STATUS** (E00958C0-C213-4ACE-AC77-FECCED2EEEA5)

Battery saver has been turned off or on in response to changing power conditions. This notification is useful for components that participate in energy conservation. Applications should register for this notification and save power when battery saver is on.

The **Data** member is a **DWORD** that indicates battery saver state:

0x0 - Battery saver is off.

0x1 - Battery saver is on. Save energy where possible.

For general information about battery saver, see [battery saver (in the hardware component guidelines)](/windows-hardware/design/component-guidelines/battery-saver).

---

<span id="GUID_ENERGY_SAVER_STATUS"></span>
<span id="guid_energy_saver_status"></span>
**GUID\_ENERGY\_SAVER\_STATUS** (550E8400-E29B-41D4-A716-446655440000)

> [!IMPORTANT]
> This information relates to a prerelease product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Energy saver status has changed. This notification is useful for components that participate in energy conservation. Applications that register for this notification can save varying degrees of power depending on what energy-saver mode is in effect.

The **Data** member is a **DWORD** with values from the ENERGY_SAVER_STATUS enumeration that indicate the current energy saver status.

ENERGY_SAVER_OFF - Energy saver is off.

ENERGY_SAVER_STANDARD - Energy saver is in standard mode. Save energy if the user experience impact is minimal. 

ENERGY_SAVER_HIGH_SAVINGS - Energy saver is in high savings mode. Save energy where possible. 

---

<span id="GUID_POWERSCHEME_PERSONALITY"></span>
<span id="guid_powerscheme_personality"></span>
**GUID\_POWERSCHEME\_PERSONALITY** (245D8541-3943-4422-B025-13A784F679B7)

The active power scheme personality has changed. All power schemes map to one of these personalities.

The **Data** member is a **GUID** that indicates the new active power scheme personality:

**GUID\_MIN\_POWER\_SAVINGS** (8C5E7FDA-E8BF-4A96-9A85-A6E23A8C635C)

High Performance - The scheme is designed to deliver maximum performance at the expense of power consumption savings.

**GUID\_MAX\_POWER\_SAVINGS** (A1841308-3541-4FAB-BC81-F71556F20B4A)

Power Saver - The scheme is designed to deliver maximum power consumption savings at the expense of system performance and responsiveness.

**GUID\_TYPICAL\_POWER\_SAVINGS** (381B4222-F694-41F0-9685-FF5BB260DF2E)

Automatic - The scheme is designed to automatically balance performance and power consumption savings.

---

<span id="GUID_SESSION_DISPLAY_STATUS"></span>
<span id="guid_session_display_status"></span>
**GUID\_SESSION\_DISPLAY\_STATUS** (2B84C20E-AD23-4DDF-93DB-05FFBD7EFCA5)

The display associated with the application's session has been powered on or off.

**Windows 7, Windows Server 2008 R2, Windows Vista and Windows Server 2008:** This notification is available starting with Windows 8 and Windows Server 2012.

This notification is sent only to user-mode applications. Services and other programs running in session 0 do not receive this notification.

The **Data** member is a **DWORD** with a value from the **MONITOR_DISPLAY_STATE** enumeration:

**PowerMonitorOff** (0) - The display is off.

**PowerMonitorOn** (1) - The display is on.

**PowerMonitorDim** (2) - The display is dimmed.

> [!Note]
> All applications that run in an interactive user-mode session should use this setting. When kernel-mode applications register for monitoring the status, they should use **GUID\_CONSOLE\_DISPLAY\_STATUS** instead.

---

<span id="GUID_SESSION_USER_PRESENCE"></span>
<span id="guid_session_user_presence"></span>
**GUID\_SESSION\_USER\_PRESENCE** (3C0F4548-C03F-4C4D-B9F2-237EDE686376)

The user status associated with the application's session has changed.

**Windows 7, Windows Server 2008 R2, Windows Vista and Windows Server 2008:** This notification is available starting with Windows 8 and Windows Server 2012.

This notification is sent only to user-mode applications running in an interactive session. Services and other programs running in session 0 should register for **GUID\_GLOBAL\_USER\_PRESENCE**.

The **Data** member is a **DWORD** with one of the following values from the **USER_ACTIVITY_PRESENCE** enumeration:

**PowerUserPresent** (0) - The user is providing input to the session.

**PowerUserInactive** (2) - The user activity timeout has elapsed with no interaction from the user.

---

<span id="GUID_SYSTEM_AWAYMODE"></span>
<span id="guid_system_awaymode"></span>
**GUID\_SYSTEM\_AWAYMODE** (98A7F580-01F7-48AA-9C0F-44352C29E5C0)

The system is entering or exiting away-mode.

The **Data** member is a **DWORD** that indicates the current away-mode state:

0x0 - The computer is exiting away-mode.

0x1 - The computer is entering away-mode.

## Requirements

| Requirement | Value                       |
|-------------|-----------------------------|
| Header<br/> | <dl> <dt>WinNT.h</dt> </dl> |
