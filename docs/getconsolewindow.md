---
title: GetConsoleWindow-Funktion
description: Ruft das Fenster Handle ab, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: c74fe1a29b9ba2ea721e874eb624ea2f8517094c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038808"
---
# <a name="getconsolewindow-function"></a>GetConsoleWindow-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft das Fenster Handle ab, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.

## <a name="syntax"></a>Syntax

```C
HWND WINAPI GetConsoleWindow(void);
```

## <a name="parameters"></a>Parameter

Diese Funktion besitzt keine Parameter.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert ist ein Handle für das Fenster, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist, oder **null** , wenn keine solche zugeordnete Konsole vorhanden ist.

## <a name="remarks"></a>Bemerkungen

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0500 sein oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

Für eine Anwendung, die in einer [**pseudoconsole**](pseudoconsoles.md) -Sitzung gehostet wird, gibt diese Funktion ein Fenster Handle nur für Nachrichten Warteschlangen-Zwecke zurück. Das zugehörige Fenster wird nicht lokal angezeigt, da die _pseudoconsole_ alle Aktionen in einen Stream für die Darstellung in einem anderen Terminalfenster an anderer Stelle serialisiert.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

</table>

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)
