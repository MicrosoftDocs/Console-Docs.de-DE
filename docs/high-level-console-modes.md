---
title: Allgemeine Konsolen Modi
description: Das Verhalten der hauptkonsolen Funktionen ist von den Konsolen Eingabe-und Ausgabe Modi betroffen.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: b5b24056a1283d46cbfe21737bd930318042c039
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059627"
---
# <a name="high-level-console-modes"></a>Allgemeine Konsolen Modi


Das Verhalten der hauptkonsolen Funktionen ist von den Konsolen Eingabe-und Ausgabe Modi betroffen. Alle folgenden Konsolen Eingabemodi werden bei der Erstellung einer-Konsole für den Eingabepuffer einer Konsole aktiviert:

- Zeilen Eingabemodus
- Verarbeiteter Eingabemodus
- Echo Eingabemodus

Beide der folgenden Konsolenausgabe Modi sind bei der Erstellung für einen Konsolenbildschirm Puffer aktiviert:

- Verarbeiteter Ausgabemodus
- Umwickeln im EOL-Ausgabemodus

Alle drei Eingabemodi, zusammen mit dem verarbeiteten Ausgabemodus, sind so konzipiert, dass Sie zusammenarbeiten. Es empfiehlt sich, alle diese Modi als Gruppe zu aktivieren oder zu deaktivieren. Wenn alle aktiviert sind, wird die Anwendung als "gekochter" Modus bezeichnet, was bedeutet, dass der meiste Teil der Verarbeitung für die Anwendung verarbeitet wird. Wenn alle deaktiviert sind, befindet sich die Anwendung im RAW-Modus, was bedeutet, dass die Eingabe ungefiltert und jede Verarbeitung an die Anwendung übertragen wird.

Eine Anwendung kann die [**getconsolemode**](getconsolemode.md) -Funktion verwenden, um den aktuellen Modus des Eingabe Puffers oder Bildschirm Puffers einer Konsole zu ermitteln. Sie können jeden dieser Modi aktivieren oder deaktivieren, indem Sie die folgenden Werte in der [**setconsolemode**](setconsolemode.md) -Funktion verwenden. Beachten Sie, dass sich das Festlegen des Ausgabemodus eines Bildschirm Puffers nicht auf den Ausgabemodus anderer Bildschirm Puffer auswirkt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Mode</th>
<th>BESCHREIBUNG</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>ENABLE_PROCESSED_INPUT</strong></td>
<td>Wird mit einem Konsolen Eingabe Handle verwendet, um zu bewirken, dass das System alle systembearbeitungs-oder Steuerelement Schlüssel Eingaben verarbeitet, anstatt Sie als Eingabe im Lesevorgang&#39;s-Puffer zurückzugeben. Wenn die Zeilen Eingabe ebenfalls aktiviert ist, werden backspaces und Wagen Rückläufe ordnungsgemäß verarbeitet. Ein Rückraum bewirkt, dass der Cursor ein Leerzeichen zurückbewegt, ohne das Zeichen an der Cursorposition zu beeinflussen. Ein Wagen Rücklauf wird in die Kombination aus Wagen Rücklauf – Zeilenvorschub Zeichen konvertiert. Wenn der Echo Eingabemodus aktiviert ist und die Ausgabe die System Bearbeitung widerspiegeln soll, muss die verarbeitete Ausgabe für den aktiven Bildschirm Puffer aktiviert werden. Wenn die verarbeitete Eingabe aktiviert ist, wird die Tastenkombination STRG + C unabhängig davon, ob die Zeilen Eingabe aktiviert ist, an den entsprechenden Handler weitergegeben. Weitere Informationen zu Steuerelement Handlern finden Sie unter <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">Konsolen Steuerungs Handler</a>.</td>
</tr>
<tr class="even">
<td><strong>ENABLE_LINE_INPUT</strong></td>
<td>Wird mit einem Konsolen Eingabe Handle verwendet, damit die Funktionen von "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " und "read <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>Console</strong></a> " zurückgegeben werden, wenn die EINGABETASTE gedrückt wird. Wenn der Zeilen Eingabemodus deaktiviert ist, geben die Funktionen zurück, wenn ein oder mehrere Zeichen im Eingabepuffer verfügbar sind.</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_ECHO_INPUT</strong></td>
<td>Wird mit einem Konsolen Eingabe Handle verwendet, um die von der Funktion "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder "read <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>Console</strong></a> " gelesenen Tastatureingaben in den aktiven Bildschirm Puffer zu übertragen. Zeichen werden nur dann angezeigt, wenn der Prozess, der " <strong>Infofile</strong> " oder " <strong>infoconsole</strong> " aufruft, ein geöffnetes Handle für den aktiven Bildschirm Puffer aufweist Der Echo Modus kann nur aktiviert werden, wenn die Zeilen Eingabe ebenfalls aktiviert ist. Der Ausgabemodus des aktiven Bildschirm Puffers wirkt sich auf die Anzeige von ECHO Eingaben aus.</td>
</tr>
<tr class="even">
<td><strong>ENABLE_PROCESSED_OUTPUT</strong></td>
<td>Wird mit einem Konsolenbildschirm Puffer Handle verwendet, um zu bewirken, dass das System die entsprechende Aktion für ANSI-Steuerzeichen ausführt, die in einen Bildschirm Puffer geschrieben werden. Die RÜCKTASTE, Tab, Glocken, Wagen Rücklauf-und Zeilenvorschub Zeichen werden verarbeitet. Ein Tabstopp Zeichen verschiebt den Cursor an den nächsten Tabstopp, der alle acht Zeichen umfasst. Ein Glocken Zeichen klingt ein kurzes Ton.</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></td>
<td>Wird mit einem Konsolenbildschirm Puffer Handle verwendet, um zu bewirken, dass die aktuelle Ausgabe Position (Cursorposition) zur ersten Spalte in der nächsten Zeile (Zeile) wechselt, wenn das Ende der aktuellen Zeile erreicht ist. Wenn der untere Rand des Fenster Bereichs erreicht ist, wird der Fenster Ursprung um eine Zeile nach unten verschoben. Diese Bewegung hat den Effekt, dass der Inhalt des Fensters eine Zeile nach oben durchführt. Wenn das Ende des Konsolenbildschirm Puffers erreicht ist, wird der Inhalt des Bildschirm Puffers der Konsole um eine Zeile nach oben gescrollt, und die obere Zeile des Konsolenbildschirm Puffers wird verworfen.
<p>Wenn dieser Modus deaktiviert ist, wird das letzte Zeichen in der Zeile mit allen nachfolgenden Zeichen überschrieben.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

 

 




