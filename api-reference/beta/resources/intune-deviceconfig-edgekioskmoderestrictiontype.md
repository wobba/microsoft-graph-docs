---
title: "edgeKioskModeRestrictionType enum type"
description: "Specify how the Microsoft Edge settings are restricted based on kiosk mode."
author: "tfitzmac"
localization_priority: Normal
ms.prod: "Intune"
---

# edgeKioskModeRestrictionType enum type

> **Important:** Microsoft Graph APIs under the /beta version are subject to change; production use is not supported.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Specify how the Microsoft Edge settings are restricted based on kiosk mode.

## Members
|Member|Value|Description|
|:---|:---|:---|
|notConfigured|0|Not configured (unrestricted).|
|digitalSignage|1|Interactive/Digital signage in single-app mode.|
|normalMode|2|Normal mode (full version of Microsoft Edge).|
|publicBrowsingSingleApp|3|Public browsing in single-app mode.|
|publicBrowsingMultiApp|4|Public browsing (inPrivate) in multi-app mode.|



