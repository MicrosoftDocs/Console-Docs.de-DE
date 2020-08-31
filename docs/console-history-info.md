---
title: CONSOLE_HISTORY_INFO Struktur
description: Siehe Referenzinformationen zur CONSOLE_HISTORY_INFO Struktur, die Informationen über den Konsolen Verlauf enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: ee0161f0c4aac5a280fd18260ebbb1f7ca57d54a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060459"
---
# <a name="console_history_info-structure"></a>Struktur der Konsolen \_ Verlauf- \_ Informationen


Enthält Informationen über den Konsolen Verlauf.

<a name="syntax"></a>Syntax
------

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

<a name="members"></a>Member
-------

**CBSIZE**  
Die Größe der-Struktur in Bytes. Legen Sie diesen Member auf fest `sizeof(CONSOLE_HISTORY_INFO)` .

**Historybuffersize**  
Die Anzahl der Befehle, die in jedem Verlaufs Puffer aufbewahrt werden.

**"Numofhistorybuffers"**  
Die Anzahl der Verlaufs Puffer, die für diesen Konsolen Prozess aufbewahrt werden.

**dwFlags**  
Dieser Parameter kann NULL oder der folgende Wert sein.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</td>
<td><p>Doppelte Einträge werden nicht im Verlaufs Puffer gespeichert.</p></td>
</tr>
</tbody>
</table>

 

<a name="requirements"></a>Anforderungen
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Unterstützte Mindestversion (Client)</p></td>
<td><p>Windows Vista [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows Server 2008 [nur Desktop-Apps]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>ConsoleApi3. h (über WinCon. h, Include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[**Getconsolehistoryinfo**](getconsolehistoryinfo.md)

[**Setconsolehistoryinfo**](setconsolehistoryinfo.md)

 

 




