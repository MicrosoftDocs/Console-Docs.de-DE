---
title: Getconsoleoriginaltitle-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur getconsoleoriginaltitle-Funktion, die den ursprünglichen Titel für das aktuelle Konsolenfenster abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: ad12ff7b931b6bbc36a7fb0e9e0ee2ac3512a1f5
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037998"
---
# <a name="getconsoleoriginaltitle-function"></a>Getconsoleoriginaltitle-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft den ursprünglichen Titel für das aktuelle Konsolenfenster ab.

## <a name="syntax"></a>Syntax

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a>Parameter

*lpconsoletitle* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge mit dem ursprünglichen Titel empfängt.

*nSize* \[ in\]  
Die Größe des *lpconsoletitle* -Puffers in Zeichen.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert die Länge der Zeichenfolge, die in den Puffer kopiert wird (in Zeichen).

Wenn der Puffer nicht groß genug ist, um den Titel zu speichern, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt eine **\_ erfolgreiche Fehlermeldung** zurück.

Wenn die Funktion fehlschlägt, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt den Fehlercode zurück.

## <a name="remarks"></a>Bemerkungen

Um den Titel für ein Konsolenfenster festzulegen, verwenden Sie die [**setconsoletitle**](setconsoletitle.md) -Funktion. Um die aktuelle Titel Zeichenfolge abzurufen, verwenden Sie die [**getconsoletitle**](getconsoletitle.md) -Funktion.

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0600 sein oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).

> [!TIP]
> Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** . Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus. Anwendungen, die Remoting über plattformübergreifende Hilfsprogramme und Transporte wie ssh verwenden, funktionieren möglicherweise nicht wie erwartet, wenn Sie diese API verwenden.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows Vista \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2008 \[ -Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | **Getconsoleoriginaltitlew** (Unicode) und **getconsoleoriginaltitlea** (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleTitle**](setconsoletitle.md)
