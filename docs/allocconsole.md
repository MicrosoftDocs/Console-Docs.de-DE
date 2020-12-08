---
title: AllocConsole-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur AllocConsole-Funktion, die eine neue Konsole für den aufrufenden Prozess zuordnet.
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
ms.localizationpriority: high
ms.openlocfilehash: c63c9a176c0d8ca2ef4342f7bee1b427eae00014
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420169"
---
# <a name="allocconsole-function"></a>AllocConsole-Funktion

Ordnet eine neue Konsole für den aufrufenden Prozess zu.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a>Parameter

Diese Funktion besitzt keine Parameter.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) auf.

## <a name="remarks"></a>Bemerkungen

Ein Prozess kann nur einer Konsole zugeordnet sein, sodass die **AllocConsole**-Funktion fehlschlägt, wenn der aufrufende Prozess bereits über eine Konsole verfügt. Ein Prozess kann die [**FreeConsole**](freeconsole.md)-Funktion verwenden, um sich selbst von seiner aktuellen Konsole zu trennen. Anschließend kann er dann **AllocConsole** aufrufen, um eine neue Konsole zu erstellen, oder [**AttachConsole**](attachconsole.md), um eine andere Konsole anzufügen.

Wenn der aufrufenden Prozess einen untergeordneten Prozess erstellt, erbt der untergeordnete Prozess die neue Konsole.

**AllocConsole** initialisiert die Standardhandles für Eingabe, Ausgabe und Fehler für die neue Konsole. Das Standardeingabehandle ist ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe- und Standardfehlerhandles sind Handles für den Bildschirmpuffer der Konsole. Um diese Handles abzurufen, verwenden Sie die Funktion [**GetStdHandle**](getstdhandle.md).

Diese Funktion wird hauptsächlich von einer grafischen Benutzeroberflächenanwendung (GUI) zum Erstellen eines Konsolenfensters verwendet. GUI-Anwendungen werden ohne eine-Konsole initialisiert. Konsolenanwendungen werden mit einer Konsole initialisiert, es sei denn, sie werden als getrennte Prozesse erstellt (durch Aufrufen der [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)-Funktion mit dem **DETACHED\_PROCESS**-Flag).

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 2000 Professional \[nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Windows 2000 Server \[nur Desktop-Apps\] |
| Header | ConsoleApi.h (über WinCon.h, Windows.h einschließen) |
| Bibliothek | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Siehe auch

[Konsolenfunktionen](console-functions.md)

[Konsolen](consoles.md)

[**AttachConsole**](attachconsole.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**FreeConsole**](freeconsole.md)

[**GetStdHandle**](getstdhandle.md)
