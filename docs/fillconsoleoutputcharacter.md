---
title: Fillconsoleoutputcharacter-Funktion
description: Schreibt ein Zeichen so oft wie angegeben in den Konsolenbildschirm Puffer, beginnend bei den angegebenen Koordinaten.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8860a1feab39bc83f28a867fa9acc491cc00e4b7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038188"
---
# <a name="fillconsoleoutputcharacter-function"></a>Fillconsoleoutputcharacter-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Schreibt ein Zeichen so oft wie angegeben in den Konsolenbildschirm Puffer, beginnend bei den angegebenen Koordinaten.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*ccharacter* \[ in\]  
Das Zeichen, das in den Konsolenbildschirm Puffer geschrieben werden soll.

*nlength* \[ in\]  
Die Anzahl der Zeichen Zellen, in die das Zeichen geschrieben werden soll.

*dwschreitecoord* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle angibt, in die das Zeichen geschrieben werden soll.

*lpnumofcharswritten* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der Zeichen empfängt, die tatsächlich in den Konsolenbildschirm Puffer geschrieben wurden.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Wenn die Anzahl der Zeichen, die in geschrieben werden sollen, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden Zeichen in die nächste Zeile geschrieben. Wenn die Anzahl der Zeichen, in die geschrieben wird, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Zeichen bis zum Ende des Bildschirm Puffers der Konsole geschrieben.

Die Attributwerte an den geschriebenen Positionen werden nicht geändert.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Diese API wird nicht empfohlen und weist keine bestimmte **[virtuelle Terminal](console-virtual-terminal-sequences.md)** Entsprechung auf. Das Ausfüllen des Bereichs außerhalb des Anzeige Fensters wird nicht unterstützt und ist für den Verlaufs Bereich des Terminal reserviert. Das Ausfüllen eines sichtbaren Bereichs mit neuem Text oder einer Farbe erfolgt durch **[das Verschieben des Cursors](console-virtual-terminal-sequences.md#cursor-positioning)** , **[das Festlegen der neuen Attribute](console-virtual-terminal-sequences.md#text-formatting)** , das anschließende Schreiben des gewünschten Texts für diesen Bereich und das Wiederholen von Zeichen, wenn dies für die Länge der Füllungs Ausführung erforderlich ist. Möglicherweise ist eine zusätzliche Cursor Bewegung erforderlich, gefolgt von dem Schreiben des gewünschten Texts zum Ausfüllen eines rechteckigen Bereichs. Es wird erwartet, dass die Client Anwendung ihren eigenen Arbeitsspeicher auf dem Bildschirm hält und den Remote Status nicht Abfragen kann. Weitere Informationen finden Sie in der **[klassischen Konsole im Vergleich](classic-vs-vt.md)** zu der Dokumentation zu virtuellen Terminals.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | **Fillconsoleoutputcharakteriw** (Unicode) und **fillconsoleoutputcharakteria** (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**Koord**](coord-str.md)

[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)

[Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
