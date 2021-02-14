---
title: Attachconsole-Funktion
description: Siehe Referenzinformationen über die attachconsole-Funktion, die den aufrufenden Prozess an die Konsole des angegebenen Prozesses anfügt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: a1be050dccc0c77b6ad448cc45e87906a115d82c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357840"
---
# <a name="attachconsole-function"></a>Attachconsole-Funktion

Fügt den aufrufenden Prozess an die Konsole des angegebenen Prozesses als Client Anwendung an.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## <a name="parameters"></a>Parameter

*dwProcessId* \[ in\]  
Der Bezeichner des Prozesses, dessen-Konsole verwendet werden soll. Dieser Parameter kann einen der folgenden Werte annehmen.

| Wert | Bedeutung |
|-|-|
| *pid* | Verwenden Sie die Konsole des angegebenen Prozesses. |
| **Anfügen \_ übergeordneter \_ Prozess**`(DWORD)-1` | Verwenden Sie die Konsole des übergeordneten Elements des aktuellen Prozesses. |

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.

## <a name="remarks"></a>Bemerkungen

Ein Prozess kann höchstens an eine Konsole angefügt werden. Wenn der Aufrufprozess bereits an eine Konsole angefügt ist, lautet der zurückgegebene Fehlercode **Error \_ Access \_ denied** ( `5` ). Wenn der angegebene Prozess über keine Konsole verfügt, wird der zurückgegebene Fehlercode **als \_ ungültiges \_ handle** () zurückgegeben `6` . Wenn der angegebene Prozess nicht vorhanden ist, wird der Fehlercode " **\_ ungültiger \_ Parameter** ()" zurückgegeben `87` .

Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich von seiner Konsole zu trennen. Wenn andere Prozesse die-Konsole gemeinsam nutzen, wird die Konsole nicht zerstört, aber der Prozess, der **freeconsole** aufgerufen hat, kann nicht darauf verweisen. Eine Konsole wird geschlossen, wenn der letzte daran angefügte Prozess beendet wird oder **freeconsole** aufruft. Nachdem ein Prozess **freeconsole** aufgerufen hat, kann er die Funktion " [**Zuweisung**](allocconsole.md) " aufrufen, um eine neue Konsole **oder eine** anfügekonsole zum Anfügen an eine andere Konsole zu erstellen.

Diese Funktion ist in erster Linie für Anwendungen nützlich, die mit [**/Subsystem: Windows**](/cpp/build/reference/subsystem-specify-subsystem)verknüpft waren, was dem Betriebssystem impliziert, dass eine Konsole nicht benötigt wird, bevor die Hauptmethode des Programms eingegeben wird. In dieser Instanz sind die Standard Handles, die mit [**getstdhandle**](getstdhandle.md) abgerufen werden, beim Start wahrscheinlich ungültig, bis **attachconsole** aufgerufen wird. Eine Ausnahme besteht darin, dass die Anwendung mit der Handle-Vererbung durch ihren übergeordneten Prozess gestartet wird.

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als `0x0501` oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows XP \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2003 \[ -Desktop-Apps\] |
| Header | ConsoleApi.h (über WinCon.h, Windows.h einschließen) |
| Bibliothek | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Siehe auch

[Konsolenfunktionen](console-functions.md)

[Konsolen](consoles.md)

[**AllocConsole**](allocconsole.md)

[**FreeConsole**](freeconsole.md)

[**GetConsoleProcessList**](getconsoleprocesslist.md)