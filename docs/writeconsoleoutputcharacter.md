---
title: Schreibconsoleoutputcharacter-Funktion
description: Kopiert eine Anzahl von Zeichen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/WriteConsoleOutputCharacter
- wincon/WriteConsoleOutputCharacter
- WriteConsoleOutputCharacter
- consoleapi2/WriteConsoleOutputCharacterA
- wincon/WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterA
- consoleapi2/WriteConsoleOutputCharacterW
- wincon/WriteConsoleOutputCharacterW
- WriteConsoleOutputCharacterW
MS-HAID:
- '\_win32\_writeconsoleoutputcharacter'
- base.writeconsoleoutputcharacter
- consoles.writeconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7cc935ea-6b19-4494-b746-259aa7aaa9cc
topic_type:
- apiref
api_name:
- WriteConsoleOutputCharacter
- WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 462ebfaed09a5c18fa9a075227a5568a789685bd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037208"
---
# <a name="writeconsoleoutputcharacter-function"></a>Schreibconsoleoutputcharacter-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Kopiert eine Anzahl von Zeichen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpcharacter* \[ in\]  
Die Zeichen, die in den Konsolenbildschirm Puffer geschrieben werden sollen.

*nlength* \[ in\]  
Die Anzahl der zu schreibenden Zeichen.

*dwschreitecoord* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle im Konsolenbildschirm Puffer angibt, in die Zeichen geschrieben werden.

*lpnumofcharswritten* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Zeichen empfängt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Wenn die Anzahl der Zeichen, in die geschrieben werden soll, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden Zeichen in die nächste Zeile geschrieben. Wenn die Anzahl der Zeichen, in die geschrieben werden soll, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden Zeichen bis zum Ende des Bildschirm Puffers der Konsole geschrieben.

Die Attributwerte an den Positionen, die in geschrieben werden, werden nicht geändert.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent in den Positions Sequenzen für **[Textformatierung](console-virtual-terminal-sequences.md#text-formatting)** und **[Cursor](console-virtual-terminal-sequences.md#cursor-positioning)** . Bewegen Sie den Cursor an den einzufügenden Speicherort, wenden Sie die gewünschte Formatierung an, und schreiben Sie Text, um ihn auszufüllen. Es gibt keine Entsprechung für das Ausgeben von Text in einem Bereich, ohne auch die aktive Farb Formatierung anzuwenden. Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus, bei denen die jeweilige Client Anwendung ihren eigenen gezeichneten Zustand zur weiteren Bearbeitung merken soll.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | " **Schreibconsoleoutputcharakteriw** (Unicode)" und " **Write Message consoleoutputcharakteria** (ANSI)" |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**Koord**](coord-str.md)

[Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)
