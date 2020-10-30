---
title: Getnumofconfiguration Manager-Funktion
description: Ruft die Anzahl der Schaltflächen auf der Maus ab, die von der aktuellen Konsole verwendet werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 96a63f3d35170ed419ceb90a063044a93c0b1951
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037828"
---
# <a name="getnumberofconsolemousebuttons-function"></a>Getnumofconfiguration Manager-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft die Anzahl der Schaltflächen auf der Maus ab, die von der aktuellen Konsole verwendet werden.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

## <a name="parameters"></a>Parameter

*lpnumofmoulbuttons* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der Maustasten empfängt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Wenn eine Konsole eine Mauseingabe empfängt, wird eine [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur, die eine [**\_ \_ Daten Satzstruktur des Maus Ereignisses**](mouse-event-record-str.md) enthält, in den Eingabepuffer der Konsole eingefügt. Der **dwbuttonstate** -Member des **Maus \_ Ereignis \_ Datensatzes** weist ein Bit auf, das den Zustand der einzelnen Maustasten angibt. Das Bit ist 1, wenn die Schaltfläche nicht gedrückt ist, und 0, wenn die Schaltfläche aktiv ist. Um die Anzahl der wichtigen Bits zu ermitteln, verwenden Sie **getnumofansolemousebuttons** .

> [!TIP]
> Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** . Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus. Dieser Status ist nur für den lokalen Benutzer-, Sitzungs-und Berechtigungs Kontext relevant. Anwendungen, die Remoting über plattformübergreifende Hilfsprogramme und Transporte wie ssh verwenden, funktionieren möglicherweise nicht wie erwartet, wenn Sie diese API verwenden.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[Konsoleneingabepuffer](console-input-buffer.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**Eingabe \_ Daten Satz**](input-record-str.md)

[**\_Ereignis \_ Daten Satz für Maus**](mouse-event-record-str.md)
