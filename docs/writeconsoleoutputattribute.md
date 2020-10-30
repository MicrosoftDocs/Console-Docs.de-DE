---
title: Funktion "schreiteconsoleoutputattribute"
description: Kopiert eine Reihe von Zeichen Attributen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 04c7799cd98479d3b776b1933994b60f5ed9fc9f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039278"
---
# <a name="writeconsoleoutputattribute-function"></a>Funktion "schreiteconsoleoutputattribute"

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Kopiert eine Reihe von Zeichen Attributen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpattribute* \[ in\]  
Die Attribute, die beim Schreiben in den Konsolenbildschirm Puffer verwendet werden sollen. Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#character-attributes).

*nlength* \[ in\]  
Die Anzahl der Zellen des Bildschirm Puffers, in die die Attribute kopiert werden.

*dwschreitecoord* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle im Konsolenbildschirm Puffer angibt, in die die Attribute geschrieben werden.

*lpnumofattrswritten* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der Attribute empfängt, die tatsächlich in den Konsolenbildschirm Puffer geschrieben wurden.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Wenn die Anzahl der Attribute, in die geschrieben werden soll, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden Attribute in die nächste Zeile geschrieben. Wenn die Anzahl der Attribute, in die geschrieben werden soll, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Attribute bis zum Ende des Bildschirm Puffers der Konsole geschrieben.

Die Zeichen Werte an den Positionen, die in geschrieben werden, werden nicht geändert.

> [!TIP]
> Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent in den Positions Sequenzen für **[Textformatierung](console-virtual-terminal-sequences.md#text-formatting)** und **[Cursor](console-virtual-terminal-sequences.md#cursor-positioning)** . Bewegen Sie den Cursor an den einzufügenden Speicherort, wenden Sie die gewünschte Formatierung an, und schreiben Sie Text, um ihn auszufüllen. Es gibt keine Entsprechung für das Anwenden von Farben auf einen Bereich, ohne dass auch Text ausgegeben wird. Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus, bei denen die jeweilige Client Anwendung ihren eigenen gezeichneten Zustand zur weiteren Bearbeitung merken soll.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**Koord**](coord-str.md)

[Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
