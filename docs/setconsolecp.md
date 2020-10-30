---
title: Setconsolecp-Funktion
description: Legt die Eingabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 644f4d925b31da94f42a465d4bce21bb2dc2ecf9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039408"
---
# <a name="setconsolecp-function"></a>Setconsolecp-Funktion

Legt die Eingabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist. Eine-Konsole verwendet die Eingabe Codepage, um Tastatureingaben in den entsprechenden Zeichen Wert zu übersetzen.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a>Parameter

*wcodepageid* \[ in\]  
Der Bezeichner der festzulegenden Codepage. Weitere Informationen finden Sie in den Hinweisen.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Eine Codepage ordnet 256 Zeichen Codes einzelnen Zeichen zu. Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.

Verwenden Sie die Funktion " [**enumsystemcodepages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) ", um die Codepages zu suchen, die vom Betriebssystem installiert oder unterstützt werden. Die Bezeichner der auf dem lokalen Computer verfügbaren Codepages werden auch in der Registrierung unter folgendem Schlüssel gespeichert:

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

Es ist jedoch besser, mit [**enumsystemcodepages Codepages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) aufzuzählen, da sich die Registrierung in verschiedenen Versionen von Windows unterscheiden kann.

Verwenden Sie die [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) -Funktion, um zu bestimmen, ob eine bestimmte Codepage gültig ist. Verwenden Sie die [**getcpinfoex**](https://msdn.microsoft.com/library/windows/desktop/dd318081) -Funktion, um weitere Informationen über eine Codepage einschließlich Ihres Namens abzurufen. Eine Liste der verfügbaren Code Page Bezeichner finden Sie unter [Code Page Identifier](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Verwenden Sie die [**getconsolecp**](getconsolecp.md) -Funktion, um die aktuelle Eingabe Codepage einer Konsole zu ermitteln. Zum Festlegen und Abrufen der Ausgabe Codepage einer Konsole verwenden Sie die Funktionen [**setconsoleoutputcp**](setconsoleoutputcp.md) und [**getconsoleoutputcp**](getconsoleoutputcp.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolen-Codepages](console-code-pages.md)

[Konsolenfunktionen](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)
