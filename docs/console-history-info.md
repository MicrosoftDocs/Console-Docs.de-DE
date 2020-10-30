---
title: CONSOLE_HISTORY_INFO-Struktur
description: Siehe Referenzinformationen zur CONSOLE_HISTORY_INFO Struktur, die Informationen über den Konsolen Verlauf enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
MS-HAID:
- base.console\_history\_info
- consoles.console\_history\_info
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b
topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 24d41dca61146cc3e835f405889400ae0d168e7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039218"
---
# <a name="console_history_info-structure"></a>Struktur der Konsolen \_ Verlauf- \_ Informationen

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Enthält Informationen über den Konsolen Verlauf.

## <a name="syntax"></a>Syntax

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

## <a name="members"></a>Member

**CBSIZE**  
Die Größe der-Struktur in Bytes. Legen Sie diesen Member auf fest `sizeof(CONSOLE_HISTORY_INFO)` .

**Historybuffersize**  
Die Anzahl der Befehle, die in jedem Verlaufs Puffer aufbewahrt werden.

**"Numofhistorybuffers"**  
Die Anzahl der Verlaufs Puffer, die für diesen Konsolen Prozess aufbewahrt werden.

**dwFlags**  
Dieser Parameter kann NULL oder der folgende Wert sein.

| Wert | Bedeutung |
|-|-|
| **HISTORY_NO_DUP_FLAG** 0x1 | Doppelte Einträge werden nicht im Verlaufs Puffer gespeichert.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows Vista \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2008 \[ -Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)
