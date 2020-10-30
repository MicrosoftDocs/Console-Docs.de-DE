---
title: "\"Zuweisung\"-Funktion"
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "Zuweisung", die eine neue Konsole für den aufrufenden Prozess zugeordnet.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: db010f60f1661d67e77de841fc243c24f32e2d1f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037508"
---
# <a name="allocconsole-function"></a>"Zuweisung"-Funktion

Weist eine neue Konsole für den aufrufenden Prozess zu.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a>Parameter

Diese Funktion besitzt keine Parameter.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Ein Prozess kann nur mit einer Konsole verknüpft werden, sodass die Funktion " **Zuordnungs Konsole** " fehlschlägt, wenn der aufrufende Prozess bereits über eine Konsole verfügt. Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich von der aktuellen Konsole zu trennen, und dann kann die Zuweisung von "- **Konsole** " zum Erstellen einer neuen Konsole oder einer [**attachconsole**](attachconsole.md) zum Anfügen an eine andere Konsole durchführen.

Wenn der aufrufenden Prozess einen untergeordneten Prozess erstellt, erbt das untergeordnete Element die neue Konsole.

" **Zugskonsole** " initialisiert Standard Eingaben, Standardausgabe und Standardfehler Handles für die neue Konsole. Das Standardeingabe Handle ist ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe und Standardfehler Handles sind Handles für den Bildschirm Puffer der Konsole. Um diese Handles abzurufen, verwenden Sie die [**getstdhandle**](getstdhandle.md) -Funktion.

Diese Funktion wird hauptsächlich von einer grafischen Benutzeroberflächen Anwendung (GUI) zum Erstellen eines Konsolenfensters verwendet. GUI-Anwendungen werden ohne eine-Konsole initialisiert. Konsolen Anwendungen werden mit einer-Konsole initialisiert, es sei denn, Sie werden als getrennte Prozesse erstellt (durch Aufrufen der [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) -Funktion mit dem getrennten **\_ prozessflag** ).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | Consoleapi. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[Trö](consoles.md)

[**AttachConsole**](attachconsole.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**FreeConsole**](freeconsole.md)

[**GetStdHandle**](getstdhandle.md)
