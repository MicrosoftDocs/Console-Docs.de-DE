---
title: Getconsoletitle-Funktion
description: Ruft den Titel und die Größe des Titels für das aktuelle Konsolenfenster ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 23b52ba1d5dde40ef842297249fdd2f87cebcb12
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037878"
---
# <a name="getconsoletitle-function"></a>Getconsoletitle-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft den Titel für das aktuelle Konsolenfenster ab.

## <a name="syntax"></a>Syntax

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a>Parameter

*lpconsoletitle* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge mit dem Titel empfängt. Wenn der Puffer zu klein ist, um den Titel zu speichern, speichert die Funktion so viele Zeichen des Titels, wie Sie in den Puffer passt, und endet mit einem NULL-Terminator.

*nSize* \[ in\]  
Die Größe des Puffers, auf den der *lpconsoletitle* -Parameter zeigt (in Zeichen).

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, entspricht der Rückgabewert der Länge des Konsolenfenster Titels in Zeichen.

Wenn die Funktion fehlschlägt, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt den Fehlercode zurück.

## <a name="remarks"></a>Bemerkungen

Um den Titel für ein Konsolenfenster festzulegen, verwenden Sie die [**setconsoletitle**](setconsoletitle.md) -Funktion. Um die ursprüngliche Titel Zeichenfolge abzurufen, verwenden Sie die [**getconsoleoriginaltitle**](getconsoleoriginaltitle.md) -Funktion.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** . Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus. Anwendungen, die Remoting über plattformübergreifende Hilfsprogramme und Transporte wie ssh verwenden, funktionieren möglicherweise nicht wie erwartet, wenn Sie diese API verwenden.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [**setconsoletitle**](setconsoletitle.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | **Getconsoletitlew** (Unicode) und **getconsoletitlea** (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTitle**](setconsoletitle.md)
