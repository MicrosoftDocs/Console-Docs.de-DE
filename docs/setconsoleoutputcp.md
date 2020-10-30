---
title: Setconsoleoutputcp-Funktion
description: Legt die Ausgabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 85b6ba4d829b86b99138efbdaa14284429d2aa81
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039338"
---
# <a name="setconsoleoutputcp-function"></a>Setconsoleoutputcp-Funktion

Legt die Ausgabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist. Eine-Konsole verwendet Ihre Ausgabe Codepage, um die von den verschiedenen Ausgabefunktionen geschriebenen Zeichen Werte in die im Konsolenfenster angezeigten Bilder zu übersetzen.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI SetConsoleOutputCP(
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

Wenn die aktuelle Schriftart eine Unicode-Schriftart mit fester Größe ist, ändert **setconsoleoutputcp** die Zuordnung der Zeichen Werte in den Glyphe-Satz der Schriftart, anstatt jedes Mal, wenn Sie aufgerufen wird, eine separate Schriftart zu laden. Dies wirkt sich darauf aus, wie erweiterte Zeichen (ASCII-Wert größer als 127) in einem Konsolenfenster angezeigt werden. Wenn es sich bei der aktuellen Schriftart jedoch um eine Raster Schriftart handelt, wirkt sich **setconsoleoutputcp** nicht darauf aus, wie erweiterte Zeichen angezeigt werden.

Verwenden Sie die Funktion " [enumsystemcodepages](https://go.microsoft.com/fwlink/p/?linkid=178051) ", um die Codepages zu suchen, die vom Betriebssystem installiert oder unterstützt werden. Die Bezeichner der auf dem lokalen Computer verfügbaren Codepages werden auch in der Registrierung unter folgendem Schlüssel gespeichert:

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

Es ist jedoch besser, mit [enumsystemcodepages Codepages](https://go.microsoft.com/fwlink/p/?linkid=178051) aufzuzählen, da sich die Registrierung in verschiedenen Versionen von Windows unterscheiden kann.
Verwenden Sie die [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) -Funktion, um zu bestimmen, ob eine bestimmte Codepage gültig ist. Verwenden Sie die [**getcpinfoex**](https://msdn.microsoft.com/library/windows/desktop/dd318081) -Funktion, um weitere Informationen über eine Codepage einschließlich Ihres Namens abzurufen. Eine Liste der verfügbaren Code Page Bezeichner finden Sie unter [Code Page Identifier](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Verwenden Sie die [**getconsoleoutputcp**](getconsoleoutputcp.md) -Funktion, um die aktuelle Ausgabe Codepage einer Konsole zu ermitteln. Um die Eingabe Codepage einer Konsole festzulegen und abzurufen, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) und [**getconsolecp**](getconsolecp.md) .

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

[**SetConsoleCP**](setconsolecp.md)
