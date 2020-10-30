---
title: Fillconsoleoutputattribute-Funktion
description: Legt die Zeichen Attribute für eine angegebene Anzahl von Zeichen Zellen fest, beginnend bei den angegebenen Koordinaten in einem Bildschirm Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 40eb97e43e406d68ff625db110998ebf69eb26f7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039068"
---
# <a name="fillconsoleoutputattribute-function"></a>Fillconsoleoutputattribute-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Legt die Zeichen Attribute für eine angegebene Anzahl von Zeichen Zellen fest, beginnend bei den angegebenen Koordinaten in einem Bildschirm Puffer.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*wattribute* \[ in\]  
Die Attribute, die beim Schreiben in den Konsolenbildschirm Puffer verwendet werden sollen. Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#character-attributes).

*nlength* \[ in\]  
Die Anzahl der Zeichen Zellen, die auf die angegebenen Farb Attribute festgelegt werden sollen.

*dwschreitecoord* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle angibt, deren Attribute festgelegt werden sollen.

*lpnumofattrswritten* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der Zeichen Zellen empfängt, deren Attribute tatsächlich festgelegt wurden.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Wenn die Anzahl der Zeichen Zellen, deren Attribute festgelegt werden sollen, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden die Zellen der nächsten Zeile festgelegt. Wenn die Anzahl der Zellen, die in geschrieben werden sollen, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Zellen bis zum Ende des Konsolenbildschirm Puffers geschrieben.

Die Zeichen Werte an den Positionen, die in geschrieben werden, werden nicht geändert.

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

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**Koord**](coord-str.md)

[**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)

[Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)
