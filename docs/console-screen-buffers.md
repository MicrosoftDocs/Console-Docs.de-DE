---
title: Konsolenbildschirmpuffer
description: Ein Bildschirmpuffer ist ein zweidimensionales Array aus Zeichen- und Farbdaten für die Ausgabe in einem Konsolenfenster.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_screen\_buffers'
- base.console\_screen\_buffers
- consoles.console\_screen\_buffers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f94995fc-5f5f-4fcd-969d-7e10020634c2
ms.localizationpriority: high
ms.openlocfilehash: 4c5740be3b60d54f9e7b586b41e962a4102222a0
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420199"
---
# <a name="console-screen-buffers"></a>Konsolenbildschirmpuffer

Ein *Bildschirmpuffer* ist ein zweidimensionales Array aus Zeichen- und Farbdaten für die Ausgabe in einem Konsolenfenster. Eine Konsole kann über mehrere Bildschirmpuffer verfügen. Der *aktive Bildschirmpuffer* ist derjenige, der auf dem Bildschirm angezeigt wird.

Ein Bildschirmpuffer wird vom System immer beim Erstellen einer neuen Konsole erstellt. Zum Öffnen eines Handles zum aktiven Bildschirmpuffer einer Konsole geben Sie den **CONOUT$** -Wert in einem Aufruf der Funktion [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) an. Ein Prozess kann die Funktion [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) verwenden, um zusätzliche Bildschirmpuffer für seine Konsole zu erstellen. Ein neuer Bildschirmpuffer ist nicht aktiv, bis sein Handle in einem Aufruf der Funktion [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) angegeben wird. Allerdings kann auf Bildschirmpuffer lesend und schreibend zugegriffen werden, gleich, ob sie aktiv oder inaktiv sind.

Jeder Bildschirmpuffer weist sein eigenes zweidimensionales Array aus Zeicheninformations-Datensätzen auf. Die Daten für jedes Zeichen sind in einer [**CHAR\_INFO**](char-info-str.md)-Struktur gespeichert, die das Unicode- oder ANSI-Zeichen und die Vordergrund- und Hintergrundfarben angibt, in denen das betreffende Zeichen angezeigt wird.

Eine Reihe von Eigenschaften, die einem Bildschirmpuffer zugeordnet sind, kann für jeden Bildschirmpuffer unabhängig festgelegt werden. Das bedeutet, dass ein Wechsel des aktiven Bildschirmpuffers dramatische Auswirkungen auf die Darstellung des Konsolenfensters haben kann. Zu den Eigenschaften, die einem Bildschirm Puffer zugeordnet sind, gehören:

- Die Größe des Bildschirmpuffers in Zeichenzeilen und -spalten.
- Textattribute (Vordergrund- und Hintergrundfarben zum Anzeigen von Text, der von der [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)- oder [**WriteConsole**](writeconsole.md)-Funktion geschrieben werden soll).
- Fenstergröße und -position (der rechteckige Bereich des Konsolenbildschirmpuffers, der im Konsolenfenster angezeigt wird).
- Position, Darstellung und Sichtbarkeit des Cursors.
- Ausgabemodi (**ENABLE\_PROCESSED\_OUTPUT** and **ENABLE\_WRAP\_AT\_EOL\_OUTPUT**). Weitere Informationen zu Ausgabemodi von Konsolen finden Sie unter [Allgemeine Konsolenmodi](high-level-console-modes.md).

Wenn ein Bildschirmpuffer erstellt wird, enthält er an jeder Position Leerzeichen. Sein Cursor ist sichtbar und am Ursprung (0,0) des Puffers positioniert, ebenso ist die linke obere Ecke des Fensters am Ursprung des Puffers positioniert. Die Größe des Konsolenbildschirmpuffers, die Fenstergröße, die Textattribute und die Darstellung des Cursors werden durch den Benutzer oder die Standardwerte des Systems bestimmt. Verwenden Sie zum Abrufen der aktuellen Werte der verschiedenen Eigenschaften, die dem Konsolenbildschirmpuffer zugeordnet sind, die Funktionen [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md), [**GetConsoleCursorInfo**](getconsolecursorinfo.md) und [**GetConsoleMode**](getconsolemode.md).

Anwendungen, die Eigenschaften des Konsolenbildschirmpuffers ändern, sollten entweder einen eigenen Bildschirmpuffer erstellen oder den Zustand des geerbten Bildschirmpuffers beim Starten speichern und ihn beim Beenden wiederherstellen. Dieses kooperative Verhalten ist erforderlich, um sicherzustellen, dass andere Anwendungen, die dieselbe Konsolensitzung nutzen, von den Änderungen nicht betroffen sind.

> [!TIP]
> Es empfiehlt sich, zukünftig nach Möglichkeit den [**alternativen Puffermodus**](console-virtual-terminal-sequences.md#alternate-screen-buffer) zu verwenden, statt für diesen Zweck einen zweiten Bildschirmpuffer zu erstellen. Der **alternative Puffermodus** bietet übergreifend bessere Kompatibilität für Remotegeräte und andere Plattformen. Weitere Informationen finden Sie in unserer Erörterung von [**klassischen Konsolen-APIs im Vergleich mit virtuellen Terminals**](classic-vs-vt.md).

## <a name="cursor-appearance-and-position"></a>Darstellung und Position des Cursors

Der Cursor eines Bildschirmpuffers kann sichtbar oder ausgeblendet sein. Wenn er sichtbar ist, kann seine Darstellung abweichen, beginnend mit dem vollständigen Ausfüllen einer Zeichenzelle bis hin zur Darstellung als horizontale Linie an der Zellunterkante. Verwenden Sie zum Abrufen von Informationen zu Darstellung und Sichtbarkeit des Cursors die Funktion [**GetConsoleCursorInfo**](getconsolecursorinfo.md). Diese Funktion meldet, ob der Cursor sichtbar ist, und beschreibt die Darstellung des Cursors als Prozentsatz einer Zeichenzelle, die von ihm ausgefüllt wird. Verwenden Sie zum Festlegen von Darstellung und Sichtbarkeit des Cursors die Funktion [**SetConsoleCursorInfo**](setconsolecursorinfo.md).

Zeichen, die von den [allgemeinen E/A-Konsolenfunktionen](high-level-console-i-o.md) geschrieben werden, werden an der aktuellen Cursorposition geschrieben und bewegen den Cursor vorwärts an die nächste Position. Verwenden Sie [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) zum Bestimmen der aktuellen Cursorposition im Koordinatensystem eines Bildschirmpuffers. Sie können [**SetConsoleCursorPosition**](setconsolecursorposition.md) verwenden, um die Cursorposition festzulegen und auf diese Weise die Platzierung von Text zu steuern, die von den allgemeinen E/A-Funktionen geschrieben oder wiederholt werden. Wenn Sie den Cursor bewegen, wird der Text an der neuen Cursorposition überschrieben.

> [!NOTE]
> Vom Verwenden der Low-Level-Funktionen zum Ermitteln der Cursorposition wird abgeraten. Wir empfehlen, zum Abfragen dieser Position für erweiterte Layouts bei Bedarf [virtuelle Terminalsequenzen](console-virtual-terminal-sequences.md) zu verwenden. Weitere Informationen zu den Vorzügen von virtuellen Terminalsequenzen finden Sie im Dokument zu den **[klassischen Funktionen im Vergleich mit virtuellen Terminals](classic-vs-vt.md)** .

Die Position, Darstellung und Sichtbarkeit des Cursors werden für jeden Bildschirmpuffer unabhängig festgelegt.

## <a name="character-attributes"></a>Zeichenattribute

Zeichenattribute lassen sich nach zwei Klassen unterscheiden: Farbe und DBCS. In der `WinCon.h`-Headerdatei sind die folgenden Attribute definiert.

| attribute | Bedeutung |
|-|-|
| **FOREGROUND\_BLUE** | Die Textfarbe enthält Blau. |
| **FOREGROUND\_GREEN** | Die Textfarbe enthält Grün. |
| **FOREGROUND\_RED** | Die Textfarbe enthält Rot. |
| **FOREGROUND\_INTENSITY** | Die Textfarbe wird verstärkt. |
| **BACKGROUND\_BLUE** | Die Hintergrundfarbe enthält Blau. |
| **BACKGROUND\_GREEN** | Die Hintergrundfarbe enthält Grün. |
| **BACKGROUND\_RED** | Die Hintergrundfarbe enthält Rot. |
| **BACKGROUND\_INTENSITY** | Die Hintergrundfarbe wird verstärkt. |
| **COMMON\_LVB\_LEADING\_BYTE** | Führendes Byte. |
| **COMMON\_LVB\_TRAILING\_BYTE** | Schließendes Byte. |
| **COMMON\_LVB\_GRID\_HORIZONTAL** | Oben horizontal. |
| **COMMON\_LVB\_GRID\_LVERTICAL** | Links vertikal. |
| **COMMON\_LVB\_GRID\_RVERTICAL** | Rechts vertikal. |
| **COMMON\_LVB\_REVERSE\_VIDEO** | Vertausche Vordergrund- und Hintergrundattribute. |
| **COMMON\_LVB\_UNDERSCORE** | Unterstrich. |

Die Vordergrundattribute geben die Textfarbe an. Die Hintergrundattribute geben die Farbe an, die zum Auffüllen des Zellenhintergrunds verwendet wird. Die anderen Attribute werden im Zusammenhang von [DBCS](https://msdn.microsoft.com/library/windows/desktop/dd317794)verwendet.

Anwendungen können die Vordergrund- und Hintergrundkonstanten kombinieren, um verschiedene Farben zu erzielen. Beispielsweise ergibt die folgende Kombination hellblaugrünen Text auf einem blauen Hintergrund.

`FOREGROUND_BLUE | FOREGROUND_GREEN | FOREGROUND_INTENSITY | BACKGROUND_BLUE`

Wenn keine Hintergrundkonstante angegeben wird, ist der Hintergrund schwarz, und wenn keine Vordergrundkonstante angegeben wird, ist der Text schwarz. Beispielsweise ergibt die folgende Kombination schwarzen Text auf einem weißen Hintergrund.

`BACKGROUND_BLUE | BACKGROUND_GREEN | BACKGROUND_RED`

Jede Zeichenzelle eines Bildschirmpuffers speichert die Farbattribute für die zum Zeichnen des Vordergrunds (Text) und Hintergrunds der betreffenden Zelle verwendeten Farben. Eine Anwendung kann die Farbdaten für jede Zeichenzelle individuell festlegen und sie im Element **Attributes** der [**CHAR\_INFO**](char-info-str.md)-Struktur für die einzelnen Zellen speichern. Die aktuellen Textattribute jedes Bildschirmpuffers werden für die anschließend von den allgemeinen Funktionen geschriebenen oder wiederholten Zeichen verwendet.

Eine Anwendung kann [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) zum Bestimmen der aktuellen Textattribute eines Bildschirmpuffers und die Funktion [**SetConsoleTextAttribute**](setconsoletextattribute.md) zum Festlegen der Zeichenattribute verwenden. Das Ändern der Attribute eines Bildschirmpuffers wirkt sich nicht auf die Darstellung der zuvor geschriebenen Zeichen aus. Diese Textattribute wirken sich nicht auf Zeichen aus, die von den Low-Level-E/A-Konsolenfunktionen (wie etwa [**WriteConsoleOutput**](writeconsoleoutput.md) oder [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)) geschrieben werden, die entweder explizit die Attribute für jede geschriebene Zelle angeben oder die Attribute unverändert lassen.

> [!NOTE]
> Es wird davon abgeraten, die Low-Level-Funktionen zum Ändern der standardmäßigen und spezifischen Textattribute zu verwenden. Es empfiehlt sich, [virtuelle Terminalsequenzen](console-virtual-terminal-sequences.md) zum Festlegen von Textattributen zu verwenden. Weitere Informationen zu den Vorzügen von virtuellen Terminalsequenzen finden Sie im Dokument zu den **[klassischen Funktionen im Vergleich mit virtuellen Terminals](classic-vs-vt.md)** .

## <a name="font-attributes"></a>Schriftartattribute

Die Funktion [**GetCurrentConsoleFont**](getcurrentconsolefont.md) ruft Informationen zur aktuellen Konsolenschriftart ab. Zu den in der Struktur [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) gespeicherten Informationen gehören auch die Breite und Höhe der einzelnen Zeichen der Schriftart.

Die Funktion [**GetConsoleFontSize**](getconsolefontsize.md) ruft die Größe der vom angegebenen Konsolenbildschirmpuffer verwendeten Schriftart ab.

> [!NOTE]
> Von der Verwendung von Funktionen zum Suchen und Ändern von Schriftartinformationen wird abgeraten. Es empfiehlt sich, Befehlszeilenanwendungen in schriftartneutraler Weise zu betreiben, um Plattformkompatibilität sowie Kompatibilität mit Hostumgebungen sicherzustellen, die dem Benutzer die Anpassung der Schriftart erlauben. Weitere Informationen zu Benutzereinstellungen und Hostumgebungen, einschließlich Terminals, finden Sie in der **[Roadmap für das Ökosystem](ecosystem-roadmap.md)** .
