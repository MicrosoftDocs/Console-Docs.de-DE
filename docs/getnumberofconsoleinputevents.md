---
title: Getnumofconsoleinputevents-Funktion
description: Ruft die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: b4cad78d35114c509f4e810a858e6ae3b8bfb644
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038688"
---
# <a name="getnumberofconsoleinputevents-function"></a>Getnumofconsoleinputevents-Funktion

Ruft die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole ab.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a>Parameter

*hconsoleinput* \[ in\]  
Ein Handle für den Konsolen Eingabepuffer. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpcnumofevents* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole empfängt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Die **getnumofconsoleinputevents** -Funktion meldet die Gesamtzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer, einschließlich der Tastatur-, Maus-und Fenstergröße für Eingabedaten Sätze. Prozesse, die die Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](readconsole.md) " verwenden, können nur Tastatureingaben lesen. Prozesse, die die Funktion " [**leseconsoleinput**](readconsoleinput.md) " verwenden, können alle Typen von Eingabedaten Sätzen lesen.

Ein Prozess kann ein Konsolen Eingabepuffer Handle in einer der Wait- [Funktionen](https://msdn.microsoft.com/library/windows/desktop/ms687069) angeben, um zu bestimmen, wann eine ungelesene Konsolen Eingabe vorhanden ist. Wenn der Eingabepuffer nicht leer ist, wird der Status eines Konsolen Eingabepuffer-Handles signalisiert.

Um Eingabedaten Sätze aus einem Konsolen Eingabepuffer zu lesen, ohne die Anzahl der ungelesenen Datensätze zu beeinträchtigen, verwenden Sie die Funktion " [**Peer**](peekconsoleinput.md) . Verwenden Sie die [**flushconsoleinputbuffer**](flushconsoleinputbuffer.md) -Funktion, um alle ungelesenen Datensätze im Eingabepuffer einer Konsole zu verwerfen.

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

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[Konsolen Eingabefunktionen auf niedriger Ebene](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)
