---
title: "\"Read consoleoutputcharacter\"-Funktion"
description: Kopiert eine Anzahl von Zeichen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/ReadConsoleOutputCharacter
- wincon/ReadConsoleOutputCharacter
- ReadConsoleOutputCharacter
- consoleapi2/ReadConsoleOutputCharacterA
- wincon/ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterA
- consoleapi2/ReadConsoleOutputCharacterW
- wincon/ReadConsoleOutputCharacterW
- ReadConsoleOutputCharacterW
MS-HAID:
- '\_win32\_readconsoleoutputcharacter'
- base.readconsoleoutputcharacter
- consoles.readconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f47464a9-6c59-4f15-abd0-be29ab515698
topic_type:
- apiref
api_name:
- ReadConsoleOutputCharacter
- ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: fa70841d5dccf3289807d29c67fab86e3b445279
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037722"
---
# <a name="readconsoleoutputcharacter-function"></a>"Read consoleoutputcharacter"-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Kopiert eine Anzahl von Zeichen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpcharacter* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der die aus dem Konsolenbildschirm Puffer gelesenen Zeichen empfängt.

*nlength* \[ in\]  
Die Anzahl der zu lesenden Zeichen Zellen des Bildschirm Puffers. Die Größe des Puffers, auf den der *lpcharacter* -Parameter verweist, sollte lauten `nLength * sizeof(TCHAR)` .

*dwumkoord* \[ in\]  
Die Koordinaten der ersten Zelle im Konsolenbildschirm Puffer, von der in Zeichen gelesen werden soll. Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die-Spalte, und der **Y** -Member ist die Zeile.

*lpnumofcharsread* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich gelesenen Zeichen empfängt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Wenn sich die Anzahl der zu lesenden Zeichen über das Ende der angegebenen Bildschirm Puffer Zeile hinaus erstreckt, werden Zeichen aus der nächsten Zeile gelesen. Wenn die Anzahl der zu lesenden Zeichen über das Ende des Konsolenbildschirm Puffers hinausgeht, werden Zeichen bis zum Ende des Konsolenbildschirm Puffers gelesen.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | "Read **consoleoutputcharakteriw** (Unicode)" und "read **consoleoutputcharaka** (ANSI)" |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**Koord**](coord-str.md)

[Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
