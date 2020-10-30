---
title: CONSOLE_READCONSOLE_CONTROL-Struktur
description: Siehe Referenzinformationen zur CONSOLE_READCONSOLE_CONTROL Struktur, die Informationen zu einem Konsolen Lesevorgang enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- base.console\_readconsole\_control
- consoles.console\_readconsole\_control
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8a703a1eaa370e16095e1b10eb146a0718f332e9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039188"
---
# <a name="console_readconsole_control-structure"></a>\_ \_ Steuerelement Struktur der Konsole

Enthält Informationen zu einem Konsolen Lesevorgang.

## <a name="syntax"></a>Syntax

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

## <a name="members"></a>Member

**nlength**  
Die Größe der-Struktur. Legen Sie diesen Member auf fest `sizeof(CONSOLE_READCONSOLE_CONTROL)` .

**ninitialchars**  
Die Anzahl der zu über springenden Zeichen (und somit beibehalten), bevor neue Lese Eingaben in den Puffer geschrieben werden, der an die Funktion der Schreib [**Konsole**](readconsole.md) weitergegeben wurde. Dieser Wert muss kleiner als der *nnumofcharstoread* -Parameter der Read **Console** -Funktion sein.

**dwctrlwakeupmask**  
Eine Maske, die angibt, welche Steuerzeichen zwischen `0x00` und `0x1F` verwendet werden sollen, um zu signalisieren, dass der Lesevorgang beendet ist. Jedes Bit entspricht einem Zeichen mit dem am wenigsten signifikanten Bit, das `0x00` oder entspricht, `NUL` und dem signifikantesten Bit, das `0x1F` oder entspricht `US` . Es können mehrere Bits (Steuerzeichen) angegeben werden.

**dwcontrolkeystate**  
Der Zustand der Steuerelement Schlüssel. Dieser Member kann einen oder mehrere der folgenden Werte aufweisen.

| Wert | Bedeutung |
|-|-|
| **CAPSLOCK_ON** 0x0080 | Die Feststell Sperre ist auf on. |
| **ENHANCED_KEY** 0x0100 | Der Schlüssel ist erweitert. Siehe [Hinweise](key-event-record-str.md#remarks). |
| **LEFT_ALT_PRESSED** 0x0002 | Die linke ALT-Taste wird gedrückt. |
| **LEFT_CTRL_PRESSED** 0x0008 | Die linke STRG-Taste wird gedrückt. |
| **NUMLOCK_ON** 0x0020 | Der NUM-Sperr Licht ist on. |
| **RIGHT_ALT_PRESSED** 0x0001 | Die Rechte ALT-Taste wird gedrückt. |
| **RIGHT_CTRL_PRESSED** 0x0004 | Die Rechte STRG-Taste wird gedrückt. |
| **SCROLLLOCK_ON** 0x0040 | Das Licht der Scrollsperre ist on. |
| **SHIFT_PRESSED** 0x0010 | Die UMSCHALTTASTE wird gedrückt. |

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows Vista \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2008 \[ -Desktop-Apps\] |
| Header | Consoleapi. h (über WinCon. h, Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**ReadConsole**](readconsole.md)
