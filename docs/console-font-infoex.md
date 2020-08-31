---
title: CONSOLE_FONT_INFOEX Struktur
description: Siehe Referenzinformationen zur CONSOLE_FONT_INFOEX Struktur, die erweiterte Informationen für eine Konsolen Schriftart enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- base.console\_font\_infoex
- consoles.console\_font\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 12977e288a63397c581143683047239e4d410eec
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060099"
---
# <a name="console_font_infoex-structure"></a>Konsolen \_ Schriftart \_ INFOEX-Struktur


Enthält erweiterte Informationen für eine Konsolen Schriftart.

<a name="syntax"></a>Syntax
------

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

<a name="members"></a>Member
-------

**CBSIZE**  
Die Größe der-Struktur in Bytes. Dieser Member muss auf festgelegt werden, `sizeof(CONSOLE_FONT_INFOEX)` bevor [**getcurrentconsolefontex**](getcurrentconsolefontex.md) aufgerufen wird. andernfalls tritt ein Fehler auf.

**nschriftart**  
Der Index der Schriftart in der Konsolen Schriftart Tabelle des Systems.

**dwfontsize**  
Eine [**Koord**](coord-str.md) -Struktur, die die Breite und Höhe jedes Zeichens in der Schriftart in logischen Einheiten enthält. Der **X** -Member enthält die Breite, während das **Y** -Element die Höhe enthält.

**FontFamily**  
Der Schrift Schnitt und die Familie. Informationen zu den möglichen Werten für diesen Member finden Sie in der Beschreibung des **tmpitchandfamily** -Members der [**TextMetric**](https://msdn.microsoft.com/library/windows/desktop/dd145132) -Struktur.

**Schriftbreite**  
Die Schrift Breite. Die Gewichtung kann zwischen 100 und 1000 liegen, in Vielfachen von 100. Beispielsweise ist das normale Gewicht 400, während 700 fett formatiert ist.

**Fakename**  
Der Name der Schriftart (z. b. Courier oder Arial).

<a name="remarks"></a>Hinweise
-------

Um die Größe der Schriftart zu erhalten, übergeben Sie den Schriftart Index an die [**getconsolefontsize**](getconsolefontsize.md) -Funktion.

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
<td>WinCon. h (Include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[**Getcurrentconsolefontex**](getcurrentconsolefontex.md)

 

 




