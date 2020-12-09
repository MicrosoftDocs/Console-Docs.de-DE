---
title: Virtuelle Konsolenterminalsequenzen
description: Virtuelle Terminalsequenzen sind Steuerzeichenfolgen, die beim Schreiben in den Ausgabestream die Cursorbewegung, Farb-/Schriftartmodus und andere Vorgänge steuern können.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: 45ee5518ec8ea2da840d2a4442efd9e0d4346526
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "93039148"
---
# <a name="console-virtual-terminal-sequences"></a>Virtuelle Konsolenterminalsequenzen


Virtuelle Terminalsequenzen sind Steuerzeichenfolgen, die beim Schreiben in den Ausgabestream die Cursorbewegung, Farb-/Schriftartmodus und andere Vorgänge steuern können. Sequenzen können im Eingabestream auch als Antwort auf eine Ausgabestream-Abfrageinformationssequenz oder als Codierung von Benutzereingaben empfangen werden, wenn der entsprechende Modus eingestellt ist.

Mit den Funktionen [**GetConsoleMode**](getconsolemode.md) und [**SetConsoleMode**](setconsolemode.md) können Sie dieses Verhalten konfigurieren. Am Ende dieses Dokuments finden Sie ein Beispiel für die vorgeschlagene Methode zur Aktivierung des Verhaltens virtueller Terminals.

Das Verhalten der folgenden Sequenzen basiert auf den VT100- und abgeleiteten Terminalemulatortechnologien, insbesondere dem xterm-Terminalemulator. Weitere Informationen zu Terminalsequenzen finden Sie unter <http://vt100.net> und unter <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Ausgabesequenzen


Die folgenden Terminalsequenzen werden beim Schreiben in den Ausgabestream vom Konsolenhost abgefangen, wenn das Flag „ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING“ auf dem Bildschirmpufferhandle mit der Funktion [**SetConsoleMode**](setconsolemode.md) festgelegt wurde. Beachten Sie, dass das Flag „DISABLE\_NEWLINE\_AUTO\_RETURN“ auch bei der Emulation des Cursorpositionierungs- und Bildlaufverhaltens anderer Terminalemulatoren in Bezug auf Zeichen nützlich sein kann, die in die letzte Spalte einer beliebigen Zeile geschrieben werden.

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Einfache Cursorpositionierung


In allen folgenden Beschreibungen ist ESC immer der hexadezimale Wert 0x1B. In Terminalsequenzen dürfen keine Leerzeichen enthalten sein. Ein Beispiel dafür, wie diese Sequenzen in der Praxis verwendet werden, finden Sie im [Beispiel](#example) am Ende dieses Themas.

Die folgende Tabelle beschreibt einfache Escapesequenzen mit einem einzigen Aktionsbefehl direkt nach dem ESC-Zeichen. Diese Sequenzen haben keine Parameter und werden sofort wirksam.

Alle Befehle in dieser Tabelle entsprechen im Allgemeinen dem Aufruf der Konsolen-API [**SetConsoleCursorPosition**](setconsolecursorposition.md) zum Platzieren des Cursors.

Die Cursorbewegung wird durch den aktuellen Viewport im Puffer begrenzt. Es erfolgt kein Bildlauf (falls verfügbar).


| Sequenz | Kompakt | Verhalten |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| ESC A | CUU | Cursor um 1 nach oben |
| ESC B | CUD | Cursor um 1 nach unten |
| ESC C | CUF | Cursor um 1 vorwärts (nach rechts) |
| ESC D | CUB | Cursor um 1 zurück (nach links) |
| ESC M | RI | Umgekehrter Index: Führt den Umkehrvorgang von \\n aus, bewegt den Cursor eine Zeile nach oben, behält die horizontale Position bei, scrollt im Puffer, falls erforderlich\* |
| ESC 7 | DECSC | Cursorposition im Arbeitsspeicher speichern\*\* |
| ESC 8 | DECSR | Cursorposition aus dem Arbeitsspeicher wiederherstellen\*\* |



> [!NOTE]
>\* Wenn Bildlaufränder festgelegt sind, scrollt RI innerhalb der Ränder nur den Inhalt und lässt den Viewport unverändert. (Siehe Bildlaufränder)
>
>\*\*Es wird kein Wert im Arbeitsspeicher gespeichert, bis der Befehl zum Speichern verwendet wird. Die einzige Möglichkeit, auf den gespeicherten Wert zuzugreifen, ist der Befehl zum Wiederherstellen.

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursorposition


Die folgenden Tabellen umfassen Sequenzen vom Typ „Einführungszeichen für Steuerungssequenz“ (CSI). Alle CSI-Sequenzen beginnen mit ESC (0x1B), gefolgt von \[ (linke eckige Klammer, 0x5b) und können Parameter variabler Länge enthalten, um für jeden Vorgang weitere Informationen anzugeben. Dies wird durch das kompakte &lt;n&gt; dargestellt. Die Tabellen unten sind nach Funktionalität gruppiert, wobei Hinweise unter den einzelnen Tabellen die Funktionsweise der Gruppe erläutern.

Für alle Parameter gelten die folgenden Regeln, sofern nichts anderes angegeben ist:

- &lt;n&gt; stellt den Abstand der Verschiebung dar und ist ein optionaler Parameter.
- Wenn &lt;n&gt; ausgelassen wird oder „0“ (null) ist, wird es wie „1“ behandelt.
- &lt;n&gt; darf nicht größer als 32.767 (maximaler kurzer Wert) sein.
- &lt;n&gt; darf nicht negativ sein.

Alle Befehle in diesem Abschnitt entsprechen im Allgemeinen dem Aufruf der Konsolen-API [**SetConsoleCursorPosition**](setconsolecursorposition.md).

Die Cursorbewegung wird durch den aktuellen Viewport im Puffer begrenzt. Es erfolgt kein Bildlauf (falls verfügbar).


| Sequenz | Code | BESCHREIBUNG | Verhalten |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; A | CUU | Cursor nach oben | Cursor wird um &lt;n&gt; nach oben bewegt. |
| ESC \[ &lt;n&gt; B | CUD | Cursor nach unten | Cursor wird um &lt;n&gt; nach unten bewegt. |
| ESC \[ &lt;n&gt; C | CUF | Cursor vorwärts | Cursor wird um &lt;n&gt; vorwärts (nach rechts) bewegt. |
| ESC \[ &lt;n&gt; D | CUB | Cursor zurück | Cursor wird um &lt;n&gt; zurück (nach links) bewegt. |
| ESC \[ &lt;n&gt; E | CNL | Cursor nächste Zeile | Cursor wird von der aktuellen Position aus &lt;n&gt; Zeilen nach unten bewegt. |
| ESC \[ &lt;n&gt; F | CPL | Cursor vorherige Zeile | Cursor wird von der aktuellen Position aus &lt;n&gt; Zeilen nach oben bewegt. |
| ESC \[ &lt;n&gt; G | CHA | Cursor horizontal absolut | Cursor wird horizontal in der aktuellen Zeile zur &lt;n&gt;-ten Position bewegt. |
| ESC \[ &lt;n&gt; d | VPA | Vertikale Zeile Position absolut | Cursor wird vertikal in der aktuellen Spalte zur &lt;n&gt;-ten Position bewegt |
| ESC \[ &lt;y&gt; ; &lt;x&gt; H | CUP | Cursorposition | \*Cursor wird zu &lt;x&gt;; &lt;y&gt;-Koordinate innerhalb des Viewports bewegt, wobei &lt;x&gt; die Spalte der Zeile &lt;y&gt; ist. |
| ESC \[ &lt;y&gt; ; &lt;x&gt; f | HVP | Horizontale vertikale Position | \*Cursor wird zu &lt;x&gt;; &lt;y&gt;-Koordinate innerhalb des Viewports bewegt, wobei &lt;x&gt; die Spalte der Zeile &lt;y&gt; ist. |
| ESC \[ s | ANSISYSSC | Cursor speichern – Ansi.sys-Emulation | \*\*Ohne Parameter; führt einen Vorgang zum Speichern des Cursors aus, z. B. DECSC |
| ESC \[ u | ANSISYSSC | Cursor wiederherstellen – Ansi.sys-Emulation | \*\*Ohne Parameter; führt einen Vorgang zum Wiederherstellen des Cursors aus, z. B. DECRC |



> [!NOTE]
>\*Parameter &lt;x&gt; und &lt;y&gt; weisen die gleichen Begrenzungen wie &lt;n&gt; oben auf. Wenn &lt;x&gt; und &lt;y&gt; weggelassen werden, werden sie auf „1;1“ festgelegt.
>
>\*\*Die historische Dokumentation von ANSI.sys ist unter <https://msdn.microsoft.com/library/cc722862.aspx> zu finden und wurde zur Hilfe/Kompatibilität implementiert.



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursorsichtbarkeit


Die folgenden Befehle steuern die Sichtbarkeit des Cursors und seinen blinkenden Zustand. Die DECTCEM-Sequenzen entsprechen in der Regel dem Aufruf der Konsolen-API [**SetConsoleCursorInfo**](setconsolecursorinfo.md) zum Aktivieren/Deaktivieren der Cursorsichtbarkeit.


| Sequenz | Code | BESCHREIBUNG | Verhalten |
|---------------|---------|------------------------------|---------------------------|
| ESC \[ ? 12 Stunden | ATT160 | Blinken des Textcursors aktivieren | Cursor blinkt. |
| ESC \[ ? 12 l | ATT160 | Blinken des Textcursors deaktivieren | Cursor blinkt nicht mehr. |
| ESC \[ ? 25 h | DECTCEM | Anzeigen-Modus des Textcursors aktivieren | Cursor wird angezeigt. |
| ESC \[ ? 25 l | DECTCEM | Ausblenden-Modus des Textcursors aktivieren | Cursor wird ausgeblendet. |

> [!TIP]
> Aktivierungssequenzen enden mit dem Kleinbuchstaben `h`, und Deaktivierungssequenzen enden mit dem Kleinbuchstaben `l`.

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewportpositionierung


Alle Befehle in diesem Abschnitt entsprechen im Allgemeinen dem Aufruf der Konsolen-API [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) zum Verschieben des Inhalts des Konsolenpuffers.

**Vorsicht** Die Befehlsnamen sind irreführend. Bildlauf (bzw. Scrollen) bezieht sich darauf, in welche Richtung sich der Text während des Vorgangs bewegt, nicht darauf, in welche Richtung sich der Viewport zu bewegen scheint.




| Sequenz | Code | BESCHREIBUNG | Verhalten |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; S | SU | Bildlauf nach oben | Text wird um &lt;n&gt; nach oben gescrollt. Auch als „Nach unten schwenken“ bezeichnet; der Bildschirm wird von unten her mit neuen Zeilen gefüllt. |
| ESC \[ &lt;n&gt; T | SD | Bildlauf nach unten | Text wird um &lt;n&gt; nach unten gescrollt. Auch als „Nach oben schwenken“ bezeichnet; der Bildschirm wird von oben her mit neuen Zeilen gefüllt. |



Der Text wird beginnend mit der Zeile, in der sich der Cursor befindet, verschoben. Wenn sich der Cursor in der mittleren Zeile des Viewports befindet, verschiebt der „Nach oben scrollen“ die untere Hälfte des Viewports und fügt unten leere Zeilen ein. „Nach unten scrollen“ verschiebt die obere Hälfte der Zeilen des Viewports, und fügt oben neue Zeilen ein.

Wichtig zu beachten ist zudem, dass „Nach oben scrollen“ und „Nach unten scrollen“ auch durch die Bildlaufränder betroffen sind. Die Aktionen „Nach oben scrollen“ und „Nach unten scrollen“ wirken sich nicht auf Zeilen außerhalb der Bildlaufränder aus.

Der Standardwert für &lt;n&gt; ist „1“, und der Wert kann optional weggelassen werden.

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Textänderung


Alle Befehle in diesem Abschnitt entsprechen im Allgemeinen dem Aufruf der Konsolen-APIs [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) und [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) zum Ändern des Textpufferinhalts.


| Sequenz | Code | BESCHREIBUNG | Verhalten |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; @ | ICH | Zeichen einfügen | Fügt &lt;n&gt; Leerzeichen an der aktuellen Cursorposition ein und verschiebt den gesamten vorhandenen Text nach rechts. Text, der den Bildschirm rechts verlässt, wird entfernt. |
| ESC \[ &lt;n&gt; P | DCH | Zeichen löschen | Löscht &lt;n&gt; Zeichen an der aktuellen Cursorposition und schiebt vom rechten Bildschirmrand aus Leerzeichen hinein. |
| ESC \[ &lt;n&gt; X | ECH | Zeichen überschreiben | Überschreibt &lt;n&gt; Zeichen von der aktuellen Cursorposition mit einem Leerzeichen. |
| ESC \[ &lt;n&gt; L | IL | Zeile einfügen | Fügt an der Cursorposition &lt;n&gt; Zeilen in den Puffer ein. Die Zeile, in der sich der Cursor befindet, und die darunter liegenden Zeilen werden nach unten verschoben. |
| ESC \[ &lt;n&gt; M | DL | Zeile löschen | Löscht &lt;n&gt; Zeilen aus dem Puffer, beginnend mit der Zeile, in der sich der Cursor befindet. |



> [!NOTE]
>Bei IL und DL sind nur die Zeilen innerhalb der Bildlaufränder (siehe „Bildlaufränder“) betroffen. Sind keine Ränder festgelegt, sind die Rahmen des Standardrands der aktuelle Viewport. Werden Zeilen unter die Ränder verschoben, werden Sie verworfen. Werden Zeilen gelöscht, werden am unteren Rand leere Zeilen eingefügt; Zeilen außerhalb des Viewports sind davon nie betroffen.

Der Standardwert für &lt;n&gt; ist „0“, wenn kein Wert festgelegt wird.



Für die folgenden Befehle hat der Parameter &lt;n&gt; 3 gültige Werte:

- 0 löscht von der aktuellen Cursorposition (einschließlich) bis zum Ende der Zeile/Anzeige.
- 1 löscht vom Anfang der Zeile/Anzeige bis zur aktuellen Cursorposition (einschließlich).
- 2 löscht die gesamte Zeile/Anzeige.


| Sequenz | Code | BESCHREIBUNG | Verhalten |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; J | ED | In Anzeige überschreiben | Ersetzt den gesamten durch &lt;n&gt; angegebenen Text im aktuellen Viewport/Bildschirm durch Leerzeichen. |
| ESC \[ &lt;n&gt; K | EL | In Zeile überschreiben | Ersetzt den gesamten Text in der Zeile mit dem durch &lt;n&gt; angegebenen Cursor durch Leerzeichen. |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Textformatierung


Alle Befehle in diesem Abschnitt entsprechen im Allgemeinen dem Aufruf der Konsolen-API [**SetConsoleTextAttribute**](setconsoletextattribute.md) zum Anpassen der Formatierung aller zukünftigen Schreibvorgänge im Textpuffer der Konsolenausgabe.

Dieser Befehl ist insofern speziell, als dass die Position &lt;n&gt; unten zwischen 0 und 16 durch Semikolons getrennte Parameter annehmen kann.

Werden keine Parameter angegeben, wird der Befehl so behandelt, als ob als einziges der 0-Parameter angegeben wäre.


| Sequenz | Code | BESCHREIBUNG | Verhalten |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| ESC \[ &lt;n&gt; m | SGR | Grafikwiedergabe festlegen | Legt das Format des Bildschirms und des Texts wie durch &lt;n&gt; angegeben fest. |



Die folgende Tabelle mit Werten kann in &lt;n&gt; verwendet werden, um verschiedene Formatierungsmodi darzustellen.

Formatierungsmodi werden von links nach rechts angewendet. Wenn Sie konkurrierende Formatierungsoptionen anwenden, führt dies dazu, dass jeweils die Option Vorrang hat, die am weitesten rechts angegeben ist.

Für Optionen, die Farben angeben, werden die Farben entsprechend der Definition in der Konsolenfarbtabelle verwendet, die mithilfe der [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)-API geändert werden kann. Wenn die Tabelle so geändert wird, dass die „blaue“ Position in der Tabelle einen RGB-Rotton anzeigt, dann werden alle Aufrufe von **Foreground Blue** diesen Rotton anzeigen, bis sie anderweitig geändert werden.


| Wert | BESCHREIBUNG | Verhalten |
|-------|---------------------------|--------------------------------------------------------------------|
| 0 | Standard | Setzt alle Attribute auf den Standardzustand vor der Änderung zurück. |
| 1 | Intensiv/leuchtend | Wendet das Flag für Helligkeit/Intensität auf Vordergrundfarbe an. |
| 4 | Underline | Fügt eine Unterstreichung hinzu. |
| 24 | Keine Unterstreichung | Entfernt die Unterstreichung. |
| 7 | Negativ | Tauscht Vordergrund- und Hintergrundfarbe. |
| 27 | Positiv (kein Negativ) | Setzt Vordergrund-/Hintergrundfarbe wieder auf normal zurück. |
| 30 | Vordergrund Schwarz | Wendet Schwarz (nicht intensiv/leuchtend) auf den Vordergrund an. |
| 31 | Vordergrund Rot | Wendet Rot (nicht intensiv/leuchtend) auf den Vordergrund an. |
| 32 | Vordergrund Grün | Wendet Grün (nicht intensiv/leuchtend) auf den Vordergrund an. |
| 33 | Vordergrund Gelb | Wendet Gelb (nicht intensiv/leuchtend) auf den Vordergrund an. |
| 34 | Vordergrund Blau | Wendet Blau (nicht intensiv/leuchtend) auf den Vordergrund an. |
| 35 | Vordergrund Magenta | Wendet Magenta (nicht intensiv/leuchtend) auf den Vordergrund an. |
| 36 | Vordergrund Cyan | Wendet Cyan (nicht intensiv/leuchtend) auf den Vordergrund an. |
| 37 | Vordergrund Weiß | Wendet Weiß (nicht intensiv/leuchtend) auf den Vordergrund an. |
| 38 | Vordergrund Erweitert | Wendet den erweiterten Farbwert auf den Vordergrund an (weitere Informationen finden Sie unten). |
| 39 | Vordergrund Standard | Wendet nur den Vordergrund-Teil der Standardwerte an (siehe 0). |
| 40 | Hintergrund Schwarz | Wendet Schwarz (nicht intensiv/leuchtend) auf den Hintergrund an. |
| 41 | Hintergrund Rot | Wendet Rot (nicht intensiv/leuchtend) auf den Hintergrund an. |
| 42 | Hintergrund Grün | Wendet Grün (nicht intensiv/leuchtend) auf den Hintergrund an. |
| 43 | Hintergrund Gelb | Wendet Gelb (nicht intensiv/leuchtend) auf den Hintergrund an. |
| 44 | Hintergrund Blau | Wendet (nicht intensiv/leuchtend) auf den Hintergrund an. |
| 45 | Hintergrund Magenta | Wendet Magenta (nicht intensiv/leuchtend) auf den Hintergrund an. |
| 46 | Hintergrund Cyan | Wendet Cyan (nicht intensiv/leuchtend) auf den Hintergrund an. |
| 47 | Hintergrund Weiß | Wendet Weiß (nicht intensiv/leuchtend) auf den Hintergrund an. |
| 48 | Hintergrund Erweitert | Wendet den erweiterten Farbwert auf den Hintergrund an (weitere Informationen finden Sie unten). |
| 49 | Hintergrund Standard | Wendet nur den Hintergrund-Teil der Standardwerte an (siehe 0). |
| 90 | Vordergrund leuchtend Schwarz | Wendet ein intensives/leuchtendes Schwarz auf den Vordergrund an. |
| 91 | Vordergrund leuchtend Rot | Wendet ein intensives/leuchtendes Rot auf den Vordergrund an. |
| 92 | Vordergrund leuchtend Grün | Wendet ein intensives/leuchtendes Grün auf den Vordergrund an. |
| 93 | Vordergrund leuchtend Gelb | Wendet ein intensives/leuchtendes Gelb auf den Vordergrund an. |
| 94 | Vordergrund leuchtend Blau | Wendet ein intensives/leuchtendes Blau auf den Vordergrund an. |
| 95 | Vordergrund leuchtend Magenta | Wendet ein intensives/leuchtendes Magenta auf den Vordergrund an. |
| 96 | Vordergrund leuchtend Cyan | Wendet ein intensives/leuchtendes Cyan auf den Vordergrund an. |
| 97 | Vordergrund leuchtend Weiß | Wendet ein intensives/leuchtendes Weiß auf den Vordergrund an. |
| 100 | Hintergrund leuchtend Schwarz | Wendet ein intensives/leuchtendes Schwarz auf den Hintergrund an. |
| 101 | Hintergrund leuchtend Rot | Wendet ein intensives/leuchtendes Rot auf den Hintergrund an. |
| 102 | Hintergrund leuchtend Grün | Wendet ein intensives/leuchtendes Grün auf den Hintergrund an. |
| 103 | Hintergrund leuchtend Gelb | Wendet ein intensives/leuchtendes Gelb auf den Hintergrund an. |
| 104 | Hintergrund leuchtend Blau | Wendet ein intensives/leuchtendes Blau auf den Hintergrund an. |
| 105 | Hintergrund leuchtend Magenta | Wendet ein intensives/leuchtendes Magenta auf den Hintergrund an. |
| 106 | Hintergrund leuchtend Cyan | Wendet ein intensives/leuchtendes Cyan auf den Hintergrund an. |
| 107 | Hintergrund leuchtend Weiß | Wendet ein intensives/leuchtendes Weiß auf den Hintergrund an. |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Erweiterte Farben

Einige virtuelle Terminalemulatoren unterstützen eine Farbpalette mit mehr als den von der Windows-Konsole bereitgestellten 16 Farben. Für diese erweiterten Farben wählt die Windows-Konsole die nächstmögliche passende Farbe aus der vorhandenen 16er-Farbtabelle zur Anzeige aus. Im Gegensatz zu den oben genannten typischen SGR-Werten verwenden die erweiterten Werte zusätzliche Parameter nach dem Anfangsindikator gemäß der nachstehenden Tabelle.


| SGR-Untersequenz | BESCHREIBUNG |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| 38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt; | Legt die Vordergrundfarbe auf den in den Parametern &lt;r&gt;, &lt;g&gt;, &lt;b&gt; angegebenen RGB-Wert fest\* |
| 48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt; | Legt die Hintergrundfarbe auf den in den Parametern &lt;r&gt;, &lt;g&gt;, &lt;b&gt; angegebenen RGB-Wert fest\* |
| 38 ; 5 ; &lt;s&gt; | Legt die Vordergrundfarbe auf den &lt;s&gt;-Index in der 88er- oder 256er-Farbtabelle fest\* |
| 48 ; 5 ; &lt;s&gt; | Legt die Hintergrundfarbe auf den &lt;s&gt;-Index in der 88er- oder 256er-Farbtabelle fest\* |



\* Die 88er- und 256er-Farbpaletten, die intern zum Vergleich verwaltet werden, basieren auf dem xterm-Terminalemulator. Die Vergleichs-/Rundungstabellen können zurzeit nicht geändert werden.


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Bildschirmfarben


Der folgende Befehl ermöglicht es der Anwendung, die Werte der Bildschirmfarbpalette auf einen beliebigen RGB-Wert festzulegen.

Die RGB-Werte sollten hexadezimal Werte zwischen `0` und `ff` sein und durch den Schrägstrich getrennt werden (z. B. `rgb:1/24/86`).

Beachten Sie, dass es sich bei dieser Sequenz um eine „Betriebssystembefehls“-Sequenz (OSC), und nicht, wie bei vielen der anderen aufgelisteten Sequenzen, um eine CSI-Sequenz handelt, und dass sie als solche mit „\\x1b\]“ und nicht mit „\\x1b\[“ beginnt.


| Sequenz | BESCHREIBUNG | Verhalten |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC | Bildschirmfarben ändern | Legt den Bildschirmfarbpaletten-Index &lt;i&gt; auf die in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; angegebenen RGB-Werte fest. |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modusänderungen


Hierbei handelt es sich um Sequenzen, die die Eingabemodi steuern. Es gibt zwei unterschiedliche Sätze von Eingabemodi: den Pfeiltasten- und den Zehnertastaturtasten-Modus. Der Pfeiltastenmodus steuert die Sequenzen, die von den Pfeiltasten und den Tasten POS1 und ENDE ausgegeben werden, während der Zehnertastaturtasten-Modus in erster Linie die von den Tasten auf der numerischen Tastatur ausgegebene Sequenzen sowie die Funktionstasten steuert.

Jeder dieser Modi ist eine einfache boolesche Einstellung – der Pfeiltastenmodus ist entweder auf „Normal“ (Standard) oder „Anwendung“ und der Zehnertastaturtasten-Modus entweder auf „Numerisch“ (Standard) oder „Anwendung“ festgelegt.

Weitere Informationen zu den in diesen Modi ausgegebenen Sequenzen finden Sie in den Abschnitten „Pfeiltasten“ und „Numerische Tastatur und Funktionstasten“.


| Sequenz | Code | BESCHREIBUNG | Verhalten |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| ESC = | DECKPAM | Aktiviert den Modus „Anwendung“ für die Zehnertastatur. | Über Zehnertastaturtasten werden Sequenzen im Modus „Anwendung“ ausgegeben. |
| ESC &gt; | DECKPNM | Aktiviert den Modus „Numerisch“ für die Zehnertastatur. | Über Zehnertastaturtasten werden Sequenzen im Modus „Numerisch“ ausgegeben. |
| ESC \[ ? 1 Stunde | DECCKM | Aktiviert den Modus „Anwendung“ für die Pfeiltasten. | Über Zehnertastaturtasten werden Sequenzen im Modus „Anwendung“ ausgegeben. |
| ESC \[ ? 1 l | DECCKM | Deaktiviert den Modus „Anwendung“ für Pfeiltasten (Modus „Normal“ verwenden). | Über Zehnertastaturtasten werden Sequenzen im Modus „Numerisch“ ausgegeben. |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Abfragestatus


Alle Befehle in diesem Abschnitt entsprechen im Allgemeinen dem Aufruf der Get\*-Konsolen-APIs zum Abrufen von Statusinformationen über den aktuellen Zustand des Konsolenpuffers.

> [!NOTE]
>Diese Abfragen geben ihre Antworten unmittelbar nach ihrer Erkennung im Ausgabestream in den Konsoleneingabestream ab, während „ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING“ festgelegt ist. Das Flag „ENABLE\_VIRTUAL\_TERMINAL\_INPUT“ gilt nicht für Abfragebefehle, da davon ausgegangen wird, dass die Anwendung, die eine Abfrage erstellt, immer die Antwort erhalten soll.




| Sequenz | Code | BESCHREIBUNG | Verhalten |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| ESC \[ 6 n | DECXCPR | Cursorposition melden | Gibt die Cursorposition wie folgt aus: ESC \[ &lt;r&gt; ; &lt;c&gt; R, wobei &lt;r&gt; = Cursorzeile und &lt;c&gt; = Cursorspalte |
| ESC \[ 0 c | DA | Geräteattribute | Meldet die Terminalidentität. Gibt „\\x1b\[?1;0c“ aus, was „VT101 ohne Optionen“ bedeutet. |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabstopps


Während die Windows-Konsole traditionell erwartet, dass Tabstopps immer acht Zeichen breit sind, können \*nix-Anwendungen, die bestimmte Sequenzen verwenden, die Position der Tabstopps innerhalb der Konsolenfenster ändern, um die Cursorbewegung durch die Anwendung zu optimieren.

Die folgenden Sequenzen ermöglichen es einer Anwendung, die Positionen der Tabstopps innerhalb des Konsolenfensters festzulegen, sie zu entfernen und zwischen ihnen zu navigieren.


| Sequenz | Code | BESCHREIBUNG | Verhalten |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC H | HTS | Horizontalen Tabstopp festlegen | Legt einen Tabstopp in der aktuellen Spalte fest, in der sich der Cursor befindet. |
| ESC \[ &lt;n&gt; I | CHT | Tabulator Cursor horizontal (vorwärts) | Bewegt den Cursor zur nächsten Spalte (in derselben Zeile) mit einem Tabstopp. Wenn keine weiteren Tabstopps vorhanden sind, wird der Cursor in die letzte Spalte der Zeile bewegt. Befindet sich der Cursor in der letzten Spalte, wird er zur ersten Spalte der nächsten Zeile bewegt. |
| ESC \[ &lt;n&gt; Z | CBT | Tabulator Cursor rückwärts | Bewegt den Cursor zur vorherigen Spalte (in derselben Zeile) mit einem Tabstopp. Wenn keine weiteren Tabstopps vorhanden sind, wird der Cursor in die erste Spalte bewegt. Befindet sich der Cursor in der ersten Spalte, wird der Cursor nicht bewegt. |
| ESC \[ 0 g | TBC | Tabstopp löschen (aktuelle Spalte) | Löscht den Tabstopp in der aktuellen Spalte, sofern vorhanden. Andernfalls geschieht nichts. |
| ESC \[ 3 g | TBC | Tabstopp löschen (alle Spalten) | Löscht alle momentan festgelegten Tabstopps. |



- Sowohl für CHT als auch für CBT ist &lt;n&gt; ein optionaler Parameter (Standardwert = 1), der angibt, wie oft der Cursor in der angegebenen Richtung vorwärts bewegt werden soll.
- Wenn keine Tabstopps über HTS festgelegt sind, werden die erste und die letzte Spalte des Fensters von CHT und CBT als die einzigen beiden Tabstopps behandelt.
- Wird ein Tabstopp mit HTS gesetzt, bewirkt dies zudem, dass die Konsole bei der Ausgabe eines TAB-Zeichens (0x09, '\\t') auf die gleiche Weise wie bei CHT zum nächsten Tabulatorstopp navigiert.

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Zeichensatz festlegen


Mit den folgenden Sequenzen können Programme die Zuordnung des aktiven Zeichensatzes ändern. Dadurch kann ein Programm 7-Bit-ASCII-Zeichen ausgeben, diese auf dem Terminalbildschirm selbst aber als andere Glyphen anzeigen lassen. Gegenwärtig sind die einzigen zwei unterstützten Zeichensätze ASCII (Standard) und der DEC Special Graphics-Zeichensatz. Unter <http://vt100.net/docs/vt220-rm/table2-4.html> finden Sie eine Auflistung aller Zeichen, die durch den DEC Special Graphics-Zeichensatz dargestellt werden.


| Sequenz | BESCHREIBUNG | Verhalten |
|----------|--------------------------------------------|-------------------------------|
| ESC ( 0 | Zeichensatz festlegen – DEC Line Drawing | Aktiviert den Modus „DEC Line Drawing“. |
| ESC ( B | Zeichensatz festlegen – US ASCII | Aktiviert den ASCII-Modus (Standard). |



Der Modus „DEC Line Drawing“ wird insbesondere zum Zeichnen von Rahmen in Konsolenanwendungen verwendet. In der folgenden Tabelle ist dargestellt, welche ASCII-Zeichen welchen Linienzeichnungszeichen zugeordnet sind.


| Hex | ASCII | DEC Line Drawing |
|------|-------|------------------|
| 0x6a | j | ┘ |
| 0x6b | k | ┐ |
| 0x6c | l | ┌ |
| 0x6d | m | └ |
| 0x6e | n | ┼ |
| 0x71 | q | ─ |
| 0x74 | t | ├ |
| 0x75 | u | ┤ |
| 0x76 | v | ┴ |
| 0x77 | w | ┬ |
| 0x78 | w | │ |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Bildlaufränder


Mit den folgenden Sequenzen können Programme den „Bildlaufbereich“ des Bildschirms konfigurieren, der von Bildlaufvorgängen betroffen ist. Hierbei handelt es sich um eine Teilmenge der Zeilen, die angepasst werden, wenn der Bildschirm ansonsten gescrollt würde, z. B. auf einem '\\n' oder RI. Diese Ränder wirken sich auch auf die Zeilen aus, die durch „Zeile einfügen“ (IL) und „Zeile löschen“ (DL), „Nach oben scrollen“ (SU) und „Nach unten scrollen“ (SD) geändert werden.

Die Bildlaufränder können besonders nützlich sein, wenn ein Teil des Bildschirms nicht gescrollt werden soll, wenn der Rest des Bildschirms gefüllt wird, wie z. B. eine Titelleiste am oberen Rand oder eine Statusleiste am unteren Rand Ihrer Anwendung.

Für DECSTBM gibt es zwei optionale Parameter, &lt;t&gt; und &lt;b&gt;, mit denen die Zeilen angegeben werden, die die oberen und unteren Zeilen des Bildlaufbereichs (einschließlich) darstellen. Wenn die Parameter weggelassen werden, ist &lt;t&gt; standardmäßig auf 1 und &lt;b&gt; auf die aktuelle Viewporthöhe voreingestellt.

Bildlaufränder gelten pro Puffer, daher ist zu beachten, dass der alternative Puffer und der Hauptpuffer getrennte Einstellungen für die Bildlaufränder aufweisen (damit eine Vollbildanwendung im alternativen Puffer die Ränder des Hauptpuffers nicht beeinträchtigen kann).


| Sequenz | Code | BESCHREIBUNG | Verhalten |
|--------------------------------|---------|----------------------|------------------------------------------------|
| ESC \[ &lt;t&gt; ; &lt;b&gt; r | DECSTBM | Bildlaufbereich festlegen | Legt die VT-Bildlaufränder des Viewports fest. |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Fenstertitel


Mit den folgenden Befehlen kann die Anwendung den Titel des Konsolenfensters auf den angegebenen Parameter &lt;string&gt; festlegen. Die Zeichenfolge muss weniger als 255 Zeichen umfassen, um akzeptiert zu werden. Dies entspricht dem Aufrufen von „SetConsoleTitle“ mit der angegebenen Zeichenfolge.

Beachten Sie, dass es sich bei diesen Sequenzen um „Betriebssystembefehls“-Sequenzen (OSC), und nicht, wie bei vielen der anderen aufgelisteten Sequenzen, um CSI-Sequenzen handelt, und dass sie als solche mit „\\x1b\]“ und nicht mit „\\x1b\[“ beginnen.


| Sequenz | BESCHREIBUNG | Verhalten |
|-------------------------------|---------------------------|----------------------------------------------------|
| ESC \] 0 ; &lt;Zeichenfolge&gt; BEL | Symbol und Fenstertitel festlegen | Legt den Titel des Konsolenfensters auf &lt;Zeichenfolge&gt; fest. |
| ESC \] 2 ; &lt;Zeichenfolge&gt; BEL | Window_Title | Legt den Titel des Konsolenfensters auf &lt;Zeichenfolge&gt; fest. |



Das abschließende Zeichen hier ist das Glocken-Zeichen, „\\x07“.

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternativer Bildschirmpuffer


\*Anwendungen vom Nix-Typ verwenden oft einen alternativen Bildschirmpuffer, um den gesamten Inhalt des Puffers ändern zu können, ohne die Anwendung, von der sie gestartet wurden, zu beeinträchtigen. Der alternative Puffer beschreibt genau die Abmessungen des Fensters ohne Scrollbackbereich.

Beispiel für dieses Verhalten: Angenommen, „vim“ wird von „bash“ gestartet. „Vim“ verwendet den gesamten Bildschirm, um die Datei zu bearbeiten, kehrt dann zu „bash“ zurück und lässt dabei den Originalpuffer unverändert.


| Sequenz | BESCHREIBUNG | Verhalten |
|--------------------|-----------------------------|--------------------------------------------|
| ESC \[ ? 1 0 4 9 h | Alternativen Bildschirmpuffer verwenden | Wechselt zu einem neuen alternativen Bildschirmpuffer. |
| ESC \[ ? 1 0 4 9 l | Hauptbildschirmpuffer verwenden | Wechselt zum Hauptpuffer. |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Fensterbreite


Mit den folgenden Sequenzen kann die Breite des Konsolenfensters gesteuert werden. Sie entsprechen in etwa dem Aufruf der Konsolen-API „SetConsoleScreenBufferInfoEx“ zum Festlegen der Fensterbreite.


| Sequenz | Code | BESCHREIBUNG | Verhalten |
|--------------|---------|------------------------------|---------------------------------------------|
| ESC \[ ? 3 h | DECCOLM | Anzahl der Spalten auf 132 festlegen | Legt die Konsolenbreite auf 132 Spalten fest. |
| ESC \[ ? 3 l | DECCOLM | Anzahl der Spalten auf 80 festlegen | Legt die Konsolenbreite auf 80 Spalten fest. |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Vorläufiges Zurücksetzen


Die folgende Sequenz kann verwendet werden, um bestimmte Eigenschaften auf ihre Standardwerte zurückzusetzen. Die folgenden Eigenschaften werden auf die folgenden Standardwerte zurückgesetzt (außerdem sind die Sequenzen aufgelistet, die diese Eigenschaften steuern):

- Cursorsichtbarkeit: sichtbar (DECTEM)
- Numerische Tastatur: Numerischer Modus (DECNKM)
- Pfeiltasten-Modus: Normaler Modus (DECCKM)
- Obere und untere Ränder: Top=1, Bottom=Konsolenhöhe (DECSTBM)
- Zeichensatz: US ASCII
- Grafikwiedergabe: Standard/Aus(SGR)
- Cursorzustand speichern: Startposition (0,0) (DECSC)


| Sequenz | Code | BESCHREIBUNG | Verhalten |
|------------|--------|-------------|----------------------------------------------------|
| ESC \[ ! p | DECSTR | Vorläufiges Zurücksetzen | Setzt bestimmte Terminaleinstellungen auf ihre Standardeinstellungen zurück. |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Eingabesequenzen


Die folgenden Terminalsequenzen werden vom Konsolenhost im Eingabestream ausgegeben, wenn das Flag „ENABLE\_VIRTUAL\_TERMINAL\_INPUT“ auf dem Eingabepufferhandle mit dem Flag „SetConsoleMode“ festgelegt wurde.

Es gibt zwei interne Modi, die steuern, welche Sequenzen für bestimmte Eingabetasten ausgegeben werden, den Pfeiltasten-Modus und den Zehnertastaturtasten-Modus. Diese werden im Abschnitt „Modusänderungen“ beschrieben.

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>


| Schlüssel | Normaler Modus | Anwendungsmodus |
|-------------|-------------|------------------|
| NACH-OBEN | ESC \[ A | ESC O A |
| NACH-UNTEN | ESC \[ B | ESC O B |
| NACH-RECHTS | ESC \[ C | ESC O C |
| NACH-LINKS-TASTE | ESC \[ D | ESC O D |
| Startseite | ESC \[ H | ESC O H |
| Ende | ESC \[ F | ESC O F |



Außerdem gilt Folgendes: Wenn die STRG-Taste mit einer dieser Tasten gedrückt wird, werden unabhängig vom Pfeiltasten-Modus stattdessen die folgenden Sequenzen ausgegeben:


| Schlüssel | Beliebiger Modus |
|--------------------|----------------|
| STRG+NACH-OBEN-TASTE | ESC \[ 1 ; 5 A |
| STRG+NACH-UNTEN-TASTE | ESC \[ 1 ; 5 B |
| ALT+NACH-RECHTS-TASTE | ESC \[ 1 ; 5 C |
| ALT+NACH-LINKS-TASTE | ESC \[ 1 ; 5 D |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numerische Tastatur und Funktionstasten


| Schlüssel | Sequenz |
|-----------|--------------|
| Rückschritt | 0x7f (DEL) |
| Anhalten | 0x1a (SUB) |
| Escape | 0x1b (ESC) |
| Einfügen | ESC \[ 2 ~ |
| Löschen | ESC \[ 3 ~ |
| BILD-AUF | ESC \[ 5 ~ |
| BILD-AB | ESC \[ 6 ~ |
| F1 | ESC O P |
| F2 | ESC O Q |
| F3 | ESC O R |
| F4 | ESC O S |
| F5 | ESC \[ 1 5 ~ |
| F6 | ESC \[ 1 7 ~ |
| F7 | ESC \[ 1 8 ~ |
| F8 | ESC \[ 1 9 ~ |
| F9 | ESC \[ 2 0 ~ |
| F10 | ESC \[ 2 1 ~ |
| F11 | ESC \[ 2 3 ~ |
| F12 | ESC \[ 2 4 ~ |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifizierer

ALT wird behandelt, indem der Sequenz ein Escapezeichen vorangestellt wird: ESC &lt;c&gt; wobei &lt;c&gt; das vom Betriebssystem übergegebene Zeichen ist. ALT+STRG wird auf die gleiche Weise behandelt, außer dass das Betriebssystem die Taste &lt;c&gt; vorab auf das entsprechende Steuerzeichen umgeschaltet hat, das an die Anwendung umgeleitet wird.

STRG wird im allgemeinen genau so weitergeleitet, wie vom System empfangen. Dabei handelt es sich in der Regel um ein einzelnes Zeichen, das in den reservierten Speicherbereich (0x0-0x1F) des Steuerzeichens umgeschaltet wird. STRG+@ (0x40) wird beispielsweise zu NUL (0x00), STRG+\[ (0x5b) zu ESC (0x1B) usw. Einige STRG-Tastenkombinationen werden entsprechend der folgenden Tabelle speziell behandelt:


| Schlüssel | Sequenz |
|--------------------|----------------|
| STRG+LEERTASTE | 0x00 (NUL) |
| STRG+NACH-OBEN-TASTE | ESC \[ 1 ; 5 A |
| STRG+NACH-UNTEN-TASTE | ESC \[ 1 ; 5 B |
| ALT+NACH-RECHTS-TASTE | ESC \[ 1 ; 5 C |
| ALT+NACH-LINKS-TASTE | ESC \[ 1 ; 5 D |



> [!NOTE]
>Links <kbd>STRG</kbd>+Rechts <kbd>ALT</kbd> wird wie ALTGR behandelt. Werden beide zusammen festgestellt, werden sie entfernt, und der Unicodewert des vom System dargestellten Zeichens wird in das Ziel übergeben. Das System übersetzt ALTGR-Werte entsprechend den aktuellen Systemeingabeeinstellungen vor.



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Beispiele


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span id="example"></span><span id="EXAMPLE"></span>Beispiel für SGR-Terminalsequenzen

Der folgende Code enthält mehrere Beispiele für die Textformatierung.

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return GetLastError();
 }

 DWORD dwMode = 0;
 if (!GetConsoleMode(hOut, &dwMode))
 {
 return GetLastError();
 }

 dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 if (!SetConsoleMode(hOut, dwMode))
 {
 return GetLastError();
 }

 // Try some Set Graphics Rendition (SGR) terminal escape sequences
 wprintf(L"\x1b[31mThis text has a red foreground using SGR.31.\r\n");
 wprintf(L"\x1b[1mThis text has a bright (bold) red foreground using SGR.1 to affect the previous color setting.\r\n");
 wprintf(L"\x1b[mThis text has returned to default colors using SGR.0 implicitly.\r\n");
 wprintf(L"\x1b[34;46mThis text shows the foreground and background change at the same time.\r\n");
 wprintf(L"\x1b[0mThis text has returned to default colors using SGR.0 explicitly.\r\n");
 wprintf(L"\x1b[31;32;33;34;35;36;101;102;103;104;105;106;107mThis text attempts to apply many colors in the same command. Note the colors are applied from left to right so only the right-most option of foreground cyan (SGR.36) and background bright white (SGR.107) is effective.\r\n");
 wprintf(L"\x1b[39mThis text has restored the foreground color only.\r\n");
 wprintf(L"\x1b[49mThis text has restored the background color only.\r\n");

 return 0;
}
```

> [!NOTE]
>Im vorhergehenden Beispiel ist die Zeichenfolge „`\x1b[31m`“ die Implementierung von **ESC \[ &lt;n&gt; m**, wobei &lt;n&gt; gleich „31“ ist.



Die folgende Grafik zeigt die Ausgabe des vorherigen Codebeispiels.

![Ausgabe der Konsole mit dem SGR-Befehl](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Beispiel für das Aktivieren der virtuellen Terminalverarbeitung

Der folgende Code enthält ein Beispiel für die empfohlene Vorgehensweise zum Aktivieren der virtuellen Terminalverarbeitung für eine Anwendung. Das Beispiel soll Folgendes veranschaulichen:

1. Der bestehende Modus sollte immer über „GetConsoleMode“ abgerufen und analysiert werden, bevor der Modus mit „SetConsoleMode“ festgelegt wird.

2. Die Überprüfung, ob „SetConsoleMode“ `0` und „GetLastError“ STATUS\_INVALID\_PARAMETER zurückgibt, ist der aktuelle Bestimmungsmechanismus bei der Ausführung auf einem System mit einer Vorgängerversion. Eine Anwendung, die STATUS\_INVALID\_PARAMETER mit einem der neueren Konsolenmodusflags im Bitfeld empfängt, sollte das Verhalten ordnungsgemäß herabstufen und den Vorgang wiederholen.

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return false;
 }
 HANDLE hIn = GetStdHandle(STD_INPUT_HANDLE);
 if (hIn == INVALID_HANDLE_VALUE)
 {
 return false;
 }

 DWORD dwOriginalOutMode = 0;
 DWORD dwOriginalInMode = 0;
 if (!GetConsoleMode(hOut, &dwOriginalOutMode))
 {
 return false;
 }
 if (!GetConsoleMode(hIn, &dwOriginalInMode))
 {
 return false;
 }

 DWORD dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING | DISABLE_NEWLINE_AUTO_RETURN;
 DWORD dwRequestedInModes = ENABLE_VIRTUAL_TERMINAL_INPUT;

 DWORD dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
 if (!SetConsoleMode(hOut, dwOutMode))
 {
 // we failed to set both modes, try to step down mode gracefully.
 dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
 if (!SetConsoleMode(hOut, dwOutMode))
 {
 // Failed to set any VT mode, can't do anything here.
 return -1;
 }
 }

 DWORD dwInMode = dwOriginalInMode | ENABLE_VIRTUAL_TERMINAL_INPUT;
 if (!SetConsoleMode(hIn, dwInMode))
 {
 // Failed to set VT input mode, can't do anything here.
 return -1;
 }

 return 0;
}
```

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Beispiel für ausgewählte Anniversary Update-Features

Im Folgenden sehen Sie ein robusteres Beispiel für Code, der eine Vielzahl von Escapesequenzen verwendet, um den Puffer zu bearbeiten, wobei der Schwerpunkt auf den Features liegt, die im Anniversary Update für Windows 10 hinzugefügt wurden.

In diesem Beispiel wird der alternative Bildschirmpuffer verwendet, es werden Tabstopps bearbeitet und Bildlaufränder festgelegt und der Zeichensatz wird geändert.

```C
//
// Copyright (C) Microsoft. All rights reserved.
//
#define DEFINE_CONSOLEV2_PROPERTIES

// System headers
#include <windows.h>

// Standard library C-style
#include <wchar.h>
#include <stdlib.h>
#include <stdio.h>

#define ESC "\x1b"
#define CSI "\x1b["

bool EnableVTMode()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return false;
 }

 DWORD dwMode = 0;
 if (!GetConsoleMode(hOut, &dwMode))
 {
 return false;
 }

 dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 if (!SetConsoleMode(hOut, dwMode))
 {
 return false;
 }
 return true;
}

void PrintVerticalBorder()
{
 printf(ESC "(0"); // Enter Line drawing mode
 printf(CSI "104;93m"); // bright yellow on bright blue
 printf("x"); // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
 printf(CSI "0m"); // restore color
 printf(ESC "(B"); // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
 printf(ESC "(0"); // Enter Line drawing mode
 printf(CSI "104;93m"); // Make the border bright yellow on bright blue
 printf(fIsTop? "l" : "m"); // print left corner 

 for (int i = 1; i < Size.X - 1; i++) 
 printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

 printf(fIsTop? "k" : "j"); // print right corner
 printf(CSI "0m");
 printf(ESC "(B"); // exit line drawing mode
}

void PrintStatusLine(char* const pszMessage, COORD const Size)
{
 printf(CSI "%d;1H", Size.Y);
 printf(CSI "K"); // clear the line
 printf(pszMessage); 
}

int __cdecl wmain(int argc, WCHAR* argv[])
{ 
 argc; // unused
 argv; // unused
 //First, enable VT mode
 bool fSuccess = EnableVTMode();
 if (!fSuccess)
 {
 printf("Unable to enter VT processing mode. Quitting.\n");
 return -1;
 }
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 printf("Couldn't get the console handle. Quitting.\n");
 return -1;
 }

 CONSOLE_SCREEN_BUFFER_INFO ScreenBufferInfo;
 GetConsoleScreenBufferInfo(hOut, &ScreenBufferInfo);
 COORD Size;
 Size.X = ScreenBufferInfo.srWindow.Right - ScreenBufferInfo.srWindow.Left + 1;
 Size.Y = ScreenBufferInfo.srWindow.Bottom - ScreenBufferInfo.srWindow.Top + 1;

 // Enter the alternate buffer
 printf(CSI "?1049h");

 // Clear screen, tab stops, set, stop at columns 16, 32
 printf(CSI "1;1H");
 printf(CSI "2J"); // Clear screen

 int iNumTabStops = 4; // (0, 20, 40, width)
 printf(CSI "3g"); // clear all tab stops
 printf(CSI "1;20H"); // Move to column 20
 printf(ESC "H"); // set a tab stop

 printf(CSI "1;40H"); // Move to column 40
 printf(ESC "H"); // set a tab stop

 // Set scrolling margins to 3, h-2
 printf(CSI "3;%dr", Size.Y-2);
 int iNumLines = Size.Y - 4;

 printf(CSI "1;1H");
 printf(CSI "102;30m");
 printf("Windows 10 Anniversary Update - VT Example"); 
 printf(CSI "0m");

 // Print a top border - Yellow
 printf(CSI "2;1H");
 PrintHorizontalBorder(Size, true);

 // // Print a bottom border
 printf(CSI "%d;1H", Size.Y-1);
 PrintHorizontalBorder(Size, false);

 wchar_t wch;

 // draw columns
 printf(CSI "3;1H"); 
 int line = 0;
 for (line = 0; line < iNumLines * iNumTabStops; line++)
 {
 PrintVerticalBorder();
 if (line + 1 != iNumLines * iNumTabStops) // don't advance to next line if this is the last line
 printf("\t"); // advance to next tab stop

 }

 PrintStatusLine("Press any key to see text printed between tab stops.", Size);
 wch = _getwch();

 // Fill columns with output
 printf(CSI "3;1H"); 
 for (line = 0; line < iNumLines; line++)
 {
 int tab = 0;
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder();// print border at right side
 if (line+1 != iNumLines)
 printf("\t"); // advance to next tab stop, (on the next line)
 }

 PrintStatusLine("Press any key to demonstrate scroll margins", Size);
 wch = _getwch();

 printf(CSI "3;1H"); 
 for (line = 0; line < iNumLines * 2; line++)
 {
 printf(CSI "K"); // clear the line
 int tab = 0;
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder(); // print border at right side
 if (line+1 != iNumLines * 2)
 {
 printf("\n"); //Advance to next line. If we're at the bottom of the margins, the text will scroll.
 printf("\r"); //return to first col in buffer
 }
 }

 PrintStatusLine("Press any key to exit", Size);
 wch = _getwch();

 // Exit the alternate buffer
 printf(CSI "?1049l");

}
```








