---
title: CONSOLE_FONT_INFOEX Struktur
description: Siehe Referenzinformationen zur CONSOLE_FONT_INFOEX Struktur, die erweiterte Informationen für eine Konsolen Schriftart enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: ef89d1bf47a4153d44140d3f9f4845bb7496680e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039258"
---
# <a name="console_font_infoex-structure"></a>Konsolen \_ Schriftart \_ INFOEX-Struktur

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Enthält erweiterte Informationen für eine Konsolen Schriftart.

## <a name="syntax"></a>Syntax

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

## <a name="members"></a>Member

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

## <a name="remarks"></a>Bemerkungen

Um die Größe der Schriftart zu erhalten, übergeben Sie den Schriftart Index an die [**getconsolefontsize**](getconsolefontsize.md) -Funktion.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows Vista \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2008 \[ -Desktop-Apps\] |
| Header | WinCon. h (Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md)
