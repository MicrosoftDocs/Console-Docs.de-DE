---
title: Konsolenbildschirmpuffer
description: Ein Bildschirm Puffer ist ein zweidimensionales Array von Zeichen-und Farbdaten für die Ausgabe in einem Konsolenfenster.
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
ms.openlocfilehash: c3121a53f654bd2fa85fa140c2efc6d6217b7796
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039168"
---
# <a name="console-screen-buffers"></a>Konsolenbildschirmpuffer

Ein *Bildschirm Puffer* ist ein zweidimensionales Array von Zeichen-und Farbdaten für die Ausgabe in einem Konsolenfenster. Eine Konsole kann über mehrere Bildschirm Puffer verfügen. Der *aktive Bildschirm Puffer* ist der auf dem Bildschirm angezeigte Puffer.

Das System erstellt immer dann einen Bildschirm Puffer, wenn eine neue Konsole erstellt wird. Wenn Sie ein Handle für den aktiven Bildschirm Puffer einer Konsole öffnen möchten, geben Sie den Wert " **$** " in einem aufrufen [**der Funktion "**](https://msdn.microsoft.com/library/windows/desktop/aa363858) Funktion" an. Ein Prozess kann die Funktion " [**kreateconsoleskreenbuffer**](createconsolescreenbuffer.md) " verwenden, um zusätzliche Bildschirm Puffer für die Konsole zu erstellen. Ein neuer Bildschirm Puffer ist erst dann aktiv, wenn sein Handle in einem Aufrufen der [**setconsoleactiveskreenbuffer**](setconsoleactivescreenbuffer.md) -Funktion angegeben wird. Allerdings können Sie auf Bildschirm Puffer zugreifen, um zu lesen und zu schreiben, ob Sie aktiv oder inaktiv sind.

Jeder Bildschirm Puffer verfügt über ein eigenes zweidimensionales Array von Zeichen Informationsdaten Sätzen. Die Daten für jedes Zeichen werden in einer [**Char \_ Info**](char-info-str.md) -Struktur gespeichert, die das Unicode-oder ANSI-Zeichen sowie die Vordergrund-und Hintergrundfarben angibt, in denen das Zeichen angezeigt wird.

Eine Reihe von Eigenschaften, die einem Bildschirm Puffer zugeordnet sind, können für jeden Bildschirm Puffer unabhängig festgelegt werden. Dies bedeutet, dass das Ändern des aktiven Bildschirm Puffers die Darstellung des Konsolenfensters drastisch beeinflussen kann. Zu den Eigenschaften, die einem Bildschirm Puffer zugeordnet sind, gehören:

- Bildschirm Puffergröße in Zeichen Zeilen und Spalten.
- Text Attribute (Vordergrund-und Hintergrundfarben zum Anzeigen von Text, der von der Funktion " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder " [**Write-Console**](writeconsole.md) " geschrieben werden soll).
- Fenstergröße und-Position (der rechteckige Bereich des Konsolenbildschirm Puffers, der im Konsolenfenster angezeigt wird).
- Cursor Position, Darstellung und Sichtbarkeit.
- Ausgabe Modi ( **die \_ verarbeitete \_ Ausgabe aktivieren** und **\_ Wrap \_ bei \_ EOL- \_ Ausgabe aktivieren** ). Weitere Informationen zu Konsolenausgabe Modi finden Sie unter allgemeine [Konsolen Modi](high-level-console-modes.md).

Wenn ein Bildschirm Puffer erstellt wird, enthält er Leerzeichen an jeder Position. Der Cursor ist sichtbar und wird am Ursprung des Puffers (0,0) positioniert, und das Fenster wird mit seiner oberen linken Ecke am Ursprungs des Puffers positioniert. Die Größe des Konsolenbildschirm Puffers, die Fenstergröße, die Text Attribute und die Darstellung des Cursors werden durch den Benutzer oder die System Standardwerte bestimmt. Zum Abrufen der aktuellen Werte der verschiedenen Eigenschaften, die dem Konsolenbildschirm Puffer zugeordnet sind, verwenden Sie die Funktionen [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md), [**getconsolecursorinfo**](getconsolecursorinfo.md)und [**getconsolemode**](getconsolemode.md) .

Anwendungen, die die Eigenschaften des Konsolenbildschirm Puffers ändern, sollten entweder einen eigenen Bildschirm Puffer erstellen oder den Zustand des geerbten Bildschirm Puffers während des Starts speichern und beim Beenden wiederherstellen. Dieses kooperative Verhalten ist erforderlich, um sicherzustellen, dass andere Anwendungen, die dieselbe Konsolen Sitzung gemeinsam nutzen, nicht von den Änderungen betroffen sind.

> [!TIP]
> Es wird empfohlen, den [**Alternativen Puffer Modus**](console-virtual-terminal-sequences.md#alternate-screen-buffer) zu verwenden, wenn möglich, anstatt für diesen Zweck einen zweiten Bildschirm Puffer zu erstellen. Der **Alternative Puffer Modus** bietet mehr Kompatibilität über Remote Geräte hinweg und mit anderen Plattformen. Weitere Informationen finden Sie in unserer Diskussion über [**klassische Konsolen-APIs im Vergleich zum Virtual Terminal**](classic-vs-vt.md) .

## <a name="cursor-appearance-and-position"></a>Cursor Darstellung und-Position

Der Cursor eines Bildschirm Puffers kann sichtbar oder ausgeblendet sein. Wenn es sichtbar ist, kann seine Darstellung variieren und reicht von der vollständigen Füllung einer Zeichen Zelle bis zum erscheinen als horizontale Linie am unteren Rand der Zelle. Zum Abrufen von Informationen über die Darstellung und Sichtbarkeit des Cursors verwenden Sie die [**getconsolecursorinfo**](getconsolecursorinfo.md) -Funktion. Diese Funktion meldet, ob der Cursor sichtbar ist, und beschreibt die Darstellung des Cursors als Prozentsatz einer ausgefüllten Zeichen Zelle. Verwenden Sie die [**setconsolecursorinfo**](setconsolecursorinfo.md) -Funktion, um die Darstellung und Sichtbarkeit des Cursors festzulegen.

Zeichen, die von den e [/a-Funktionen auf hoher Ebene](high-level-console-i-o.md) geschrieben werden, werden an der aktuellen Cursorposition geschrieben, sodass der Cursor auf die nächste Position verschoben wird. Verwenden Sie [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md), um die aktuelle Cursorposition im Koordinatensystem eines Bildschirm Puffers zu bestimmen. Sie können [**SetConsoleCursorPosition**](setconsolecursorposition.md) verwenden, um die Cursorposition festzulegen, und damit die Platzierung von Text steuern, der von den e/a-Funktionen auf hoher Ebene geschrieben oder wiederholt wird. Wenn Sie den Cursor bewegen, wird der Text an der neuen Cursorposition überschrieben.

> [!NOTE]
> Die Verwendung der Funktionen auf niedriger Ebene zum Ermitteln der Cursorposition ist nicht empfehlenswert. Es wird empfohlen, [virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md) zu verwenden, um diese Position bei Bedarf für erweiterte Layouts abzufragen. Weitere Informationen zum bevorzugen virtueller Terminal Sequenzen finden Sie im Dokument " **[klassische Funktionen im Vergleich zum virtuellen Terminal](classic-vs-vt.md)** ".

Die Position, das Aussehen und die Sichtbarkeit des Cursors werden für jeden Bildschirm Puffer unabhängig festgelegt.

## <a name="character-attributes"></a>Zeichen Attribute

Zeichen Attribute können in zwei Klassen unterteilt werden: Farbe und DBCS. Die folgenden Attribute sind in der `WinCon.h` Header Datei definiert.

| attribute | Bedeutung |
|-|-|
| **Vordergrund \_ blau** | Textfarbe enthält blau. |
| **Vordergrund \_ grün** | Textfarbe enthält grün. |
| **Vordergrund \_ rot** | Textfarbe enthält rot. |
| **Vordergrund \_ Intensität** | Die Textfarbe wird verstärkt. |
| **Hintergrund \_ blau** | Hintergrundfarbe enthält blau. |
| **Hintergrund \_ grün** | Hintergrundfarbe enthält grün. |
| **\_Roter Hintergrund** | Die Hintergrundfarbe enthält rot. |
| **Hintergrund \_ Intensität** | Die Hintergrundfarbe wird verstärkt. |
| **häufiges \_ LVB- \_ führendes \_ Byte** | Führendes Byte. |
| **häufiges \_ LVB- \_ nachfolgendes \_ Byte** | Nachfolgendes Byte. |
| **häufiges \_ LVB- \_ Raster \_ Horizontal** | Obere horizontale. |
| **Common \_ LVB- \_ Raster \_ lvertical** | Links vertikal. |
| **allgemeine \_ LVB- \_ Raster \_ rvertical** | Rechts vertikal. |
| **gängiges \_ LVB- \_ Reverse- \_ Video** | Umgekehrte Vordergrund-und Hintergrund Attribute. |
| **allgemeiner \_ LVB-unter \_ Strich** | Unterstrich. |

Die Vordergrund Attribute geben die Textfarbe an. Die Hintergrund Attribute geben die Farbe an, die zum Ausfüllen des Hintergrunds der Zelle verwendet wird. Die anderen Attribute werden mit [DBCS](https://msdn.microsoft.com/library/windows/desktop/dd317794)verwendet.

Eine Anwendung kann die Vordergrund-und Hintergrund Konstanten kombinieren, um unterschiedliche Farben zu erzielen. Die folgende Kombination führt z. b. zu einem hellen Zyan-Text auf einem blauen Hintergrund.

`FOREGROUND_BLUE | FOREGROUND_GREEN | FOREGROUND_INTENSITY | BACKGROUND_BLUE`

Wenn keine Hintergrund Konstante angegeben wird, ist der Hintergrund schwarz, und wenn keine Vordergrund Konstante angegeben wird, ist der Text schwarz. Die folgende Kombination erzeugt z. b. schwarzen Text auf einem weißen Hintergrund.

`BACKGROUND_BLUE | BACKGROUND_GREEN | BACKGROUND_RED`

In jeder Bildschirm Puffer-Zeichen Zelle werden die Farb Attribute für die Farben gespeichert, die zum Zeichnen des Vordergrunds (Text) und des Hintergrunds der Zelle verwendet werden. Eine Anwendung kann die Farbdaten für jede Zeichen Zelle einzeln festlegen und speichert die Daten im **Attributmember** der [**Char \_ Info**](char-info-str.md) -Struktur für jede Zelle. Die aktuellen Text Attribute jedes Bildschirm Puffers werden für Zeichen verwendet, die anschließend von den Funktionen auf hoher Ebene geschrieben oder wiederholt werden.

Eine Anwendung kann [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) zum Bestimmen der aktuellen Text Attribute eines Bildschirm Puffers und der [**SetConsoleTextAttribute**](setconsoletextattribute.md) -Funktion verwenden, um die Zeichen Attribute festzulegen. Das Ändern der Attribute eines Bildschirm Puffers wirkt sich nicht auf die Anzeige von Zeichen aus, die zuvor geschrieben wurden. Diese Text Attribute wirken sich nicht auf von den e/a-Funktionen auf niedriger Ebene geschriebene Zeichen (z. b. die Funktion " [**Write-consoleoutput**](writeconsoleoutput.md) " oder " [**Write-consoleoutputcharacter**](writeconsoleoutputcharacter.md) ") aus, die entweder die Attribute für jede geschriebene Zelle explizit angeben oder die Attribute unverändert lassen.

> [!NOTE]
> Die Verwendung der Low-Level-Funktionen zum Bearbeiten von Standard-und bestimmten Textattributen ist nicht empfehlenswert. Es wird empfohlen, [virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md) zum Festlegen von Textattributen zu verwenden. Weitere Informationen zum bevorzugen virtueller Terminal Sequenzen finden Sie im Dokument " **[klassische Funktionen im Vergleich zum virtuellen Terminal](classic-vs-vt.md)** ".

## <a name="font-attributes"></a>Schriftart Attribute

Die [**getcurrentconsolefont**](getcurrentconsolefont.md) -Funktion Ruft Informationen über die aktuelle Konsolen Schriftart ab. Die in der [**Konsolen \_ Schriftart \_ Info**](console-font-info-str.md) -Struktur gespeicherten Informationen enthalten die Breite und Höhe jedes Zeichens in der Schriftart.

Die [**getconsolefontsize**](getconsolefontsize.md) -Funktion Ruft die Größe der Schriftart ab, die vom angegebenen Konsolenbildschirm Puffer verwendet wird.

> [!NOTE]
> Die Verwendung von Funktionen zum Suchen und Bearbeiten von Schriftart Informationen wird nicht empfohlen. Es wird empfohlen, Befehlszeilen Anwendungen auf Schriftart neutrale Weise zu betreiben, um die plattformübergreifende Kompatibilität sowie die Kompatibilität mit Host Umgebungen sicherzustellen, die es dem Benutzer ermöglichen, die Schriftart anzupassen. Weitere Informationen zu Benutzereinstellungen und Host Umgebungen, einschließlich Terminals, finden Sie in der Roadmap für das **[Ökosystem](ecosystem-roadmap.md)** .
