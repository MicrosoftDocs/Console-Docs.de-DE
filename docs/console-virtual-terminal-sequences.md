---
title: Konsolen virtuelle Terminal Sequenzen
description: Virtuelle Terminal Sequenzen sind Steuerungs Zeichenfolgen, die beim Schreiben in den Ausgabestream die Cursor Bewegung, den Farb-/schriftmodus und andere Vorgänge steuern können.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: d05aa6f44cc97478d4eb2aba25587b2506e84a98
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059970"
---
# <a name="console-virtual-terminal-sequences"></a>Konsolen virtuelle Terminal Sequenzen


Virtuelle Terminal Sequenzen sind Steuerungs Zeichenfolgen, die beim Schreiben in den Ausgabestream die Cursor Bewegung, den Farb-/schriftmodus und andere Vorgänge steuern können. Sequenzen können auch als Antwort auf eine Abfrage Informations Sequenz für den Ausgabestream oder als Codierung von Benutzereingaben im Eingabedaten Strom empfangen werden, wenn der entsprechende Modus festgelegt ist.

Sie können dieses Verhalten mit [**getconsolemode**](getconsolemode.md) -und [**setconsolemode**](setconsolemode.md) -Funktionen konfigurieren. Ein Beispiel für die empfohlene Vorgehensweise zum Aktivieren des Verhaltens von virtuellen Endgeräten finden Sie am Ende dieses Dokuments.

Das Verhalten der folgenden Sequenzen basiert auf den VT100-und abgeleiteten terminalemulatortechnologien, insbesondere dem xterm-Terminal Emulator. Weitere Informationen zu Terminal Sequenzen finden Sie unter <http://vt100.net> und unter <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html> .

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Ausgabe Sequenzen


Die folgenden Terminal Sequenzen werden vom Konsolen Host abgefangen, wenn Sie in den Ausgabestream geschrieben werden, wenn das Flag zum Aktivieren der \_ virtuellen \_ Terminal \_ Verarbeitung auf dem Bildschirm Puffer Handle mithilfe der [**setconsolemode**](setconsolemode.md) -Funktion festgelegt wird. Beachten Sie, dass das \_ \_ automatische \_ rückgabeflag zum Deaktivieren von Zeilen Vorgängen auch nützlich sein kann, um das Cursor Positions-und Bild Laufverhalten anderer Terminalemulatoren in Bezug auf Zeichen zu emulieren, die in der letzten Spalte in einer Zeile

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Einfache Cursor Positionierung


Bei allen folgenden Beschreibungen ist ESC immer der hexadezimale Wert 0x1B. Es sind keine Leerzeichen in Terminal Sequenzen enthalten. Ein Beispiel für die Verwendung dieser Sequenzen in der Praxis finden Sie im [Beispiel](#example) am Ende dieses Themas.

In der folgenden Tabelle werden einfache Escapesequenzen mit einem einzelnen Action-Befehl direkt nach dem ESC-Zeichen beschrieben. Diese Sequenzen verfügen über keine Parameter und treten sofort in Kraft.

Alle Befehle in dieser Tabelle entsprechen in der Regel dem Aufrufen der [**SetConsoleCursorPosition**](setconsolecursorposition.md) -Konsolen-API, um den Cursor zu platzieren.

Die Cursor Bewegung wird vom aktuellen Viewport in den Puffer gebunden. Der Bildlauf (falls verfügbar) erfolgt nicht.


| Sequenz | Kurzform | Verhalten                                                                                                                                      |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| ESC A    | Cuu       | Cursor nach oben um 1                                                                                                                                |
| ESC B    | CUD       | Cursor nach unten um 1                                                                                                                              |
| ESC C    | CUF       | Cursor vorwärts (rechts) um 1                                                                                                                   |
| ESC D    | Cub       | Cursor nach hinten (links) um 1                                                                                                                   |
| ESC M    | RI        | Umgekehrter Index – führt den umgekehrten Vorgang von \\ n aus, verschiebt den Cursor um eine Zeile nach oben, behält die horizontale Position bei Bedarf und scrollt den Puffer.\* |
| ESC 7    | Entschlüsseln     | Cursor Position im Arbeitsspeicher speichern\*\*                                                                                                            |
| ESC 8    | Decsr     | Cursor Position aus dem Arbeitsspeicher wiederherstellen\*\*                                                                                                       |



**Hinweis**  
\* Wenn Bild Lauf Ränder festgelegt sind, führt RI innerhalb der Ränder nur einen Bildlauf durch den Inhalt der Ränder durch und lässt den Viewport unverändert. (Siehe scrollränder)

\*\*Es wird kein Wert im Arbeitsspeicher gespeichert, bis der Befehl zum Speichern verwendet wird. Die einzige Möglichkeit, auf den gespeicherten Wert zuzugreifen, ist der Restore-Befehl.



## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positionierung


In den folgenden Tabellen sind die typsequenzen von "Control Sequence Introduction" (CSI). Alle CSI-Sequenzen beginnen mit ESC (0x1B), gefolgt von \[ (linker Klammer, 0x5b) und können Parameter der Variablen Länge enthalten, um für jeden Vorgang Weitere Informationen anzugeben. Dies wird durch die kurzzeitangabe &lt; dargestellt &gt; . Jede Tabelle unten ist nach Funktionalität gruppiert, wobei die einzelnen Tabellen die Funktionsweise der Gruppe erläutern.

Für alle Parameter gelten die folgenden Regeln, sofern nichts anderes angegeben ist:

- &lt;n &gt; stellt den zu verschiebende Abstand dar und ist ein optionaler Parameter.
- Wenn &lt; n &gt; weggelassen wird oder 0 (null) ist, wird er als 1 behandelt.
- &lt;n &gt; kann nicht größer als 32.767 (maximaler Kurzwert) sein.
- &lt;n &gt; darf nicht negativ sein.

Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufrufen der Konsolen-API [**SetConsoleCursorPosition**](setconsolecursorposition.md) .

Die Cursor Bewegung wird vom aktuellen Viewport in den Puffer gebunden. Der Bildlauf (falls verfügbar) erfolgt nicht.


| Sequenz                       | Code      | BESCHREIBUNG                         | Verhalten                                                                                                                   |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; A             | Cuu       | Cursor nach oben                           | Cursor nach oben um &lt; n&gt;                                                                                                     |
| ESC \[ &lt; n &gt; B             | CUD       | Cursor nach unten                         | Cursor nach unten um &lt; n&gt;                                                                                                   |
| ESC \[ &lt; n &gt; C             | CUF       | Cursor vorwärts                      | Cursor vorwärts (rechts) durch &lt; n&gt;                                                                                        |
| ESC \[ &lt; n &gt; D             | Cub       | Cursor rückwärts                     | Cursor rückwärts (links) durch &lt; n&gt;                                                                                        |
| ESC \[ &lt; n &gt; E             | CNL       | Cursor-nächste Zeile                    | Cursor bis zum Anfang der &lt; n-ten &gt; Zeile im Viewport                                                               |
| ESC \[ &lt; n &gt; F             | CPL       | Vorherige Cursor Zeile                | Cursor bis zum Anfang der &lt; n-ten &gt; Zeile im Viewport                                                                 |
| ESC \[ &lt; n &gt; G             | CHA       | Cursor horizontal absolut          | Der Cursor wechselt an &lt; die n-te &gt; Position horizontal in der aktuellen Zeile.                                                      |
| ESC \[ &lt; n &gt; d             | VPA       | Vertikale Zeilen Position absolut     | Der Cursor wechselt an die n-te &lt; &gt; Position vertikal in der aktuellen Spalte.                                                  |
| ESC \[ &lt; y &gt; ; &lt; x &gt; H | Pokalsieg       | Cursor Position                     | \*Cursor wechselt zu &lt; x &gt; ; &lt; y- &gt; Koordinate innerhalb des Viewports, wobei &lt; x für &gt; die Spalte der &lt; y- &gt; Zeile steht. |
| ESC \[ &lt; y &gt; ; &lt; × &gt; f | HVP       | Horizontale vertikale Position        | \*Cursor wechselt zu &lt; x &gt; ; &lt; y- &gt; Koordinate innerhalb des Viewports, wobei &lt; x für &gt; die Spalte der &lt; y- &gt; Zeile steht. |
| ESC \[ s                       | Ansisyssc | Cursor – Ansi.sys Emulation speichern    | \*\*Ohne Parameter führt einen Vorgang zum Speichern eines Cursors aus, z. b. decsc.                                                        |
| ESC \[ u                       | Ansisyssc | Restore Cursor – Ansi.sys Emulation | \*\*Ohne Parameter führt einen Restore-Cursor Vorgang wie decrc aus.                                                     |



**Hinweis**  
\*&lt;x &gt; -und &lt; y- &gt; Parameter haben dieselben Einschränkungen wie &lt; n &gt; oben. Wenn &lt; x &gt; und &lt; y &gt; ausgelassen werden, werden Sie auf 1 festgelegt.

\*\*ANSI.sys Verlaufs Dokumentation finden Sie unter <https://msdn.microsoft.com/library/cc722862.aspx> und wird aus Gründen der Handhabung und Kompatibilität implementiert.



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Sichtbarkeit


Die folgenden Befehle steuern die Sichtbarkeit des Cursors und den blinkende Zustand. Die dectcem-Sequenzen entsprechen in der Regel der aufrufenden [**setconsolecursorinfo**](setconsolecursorinfo.md) -Konsolen-API zum Umschalten der Cursor Sichtbarkeit.


| Sequenz      | Code    | BESCHREIBUNG                  | Verhalten                  |
|---------------|---------|------------------------------|---------------------------|
| ESC \[ ? 12 Stunden | ATT160  | Text Cursor Aktivierung blinkt  | Cursor blinkt |
| ESC \[ ? 12 l | ATT160  | Blinken des Text Cursors deaktivieren  | Blinkt den Cursor nicht mehr  |
| ESC \[ ? 25 h | Dectcem | Text Cursor Aktivierungs Modus anzeigen | Cursor anzeigen           |
| ESC \[ ? 25 l | Dectcem | Modus "Text Cursor aktivieren" ausblenden | Cursor ausblenden           |



## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Positionieren von Viewports


Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufrufen der [**scrollconsolescreenbuffer**](scrollconsolescreenbuffer.md) -Konsolen-API, um den Inhalt des Konsolen Puffers zu verschieben.

**Vorsicht**  Die Befehlsnamen sind irreführend. Scroll bezieht sich auf die Richtung, in die der Text während des Vorgangs verschoben wird, nicht auf die Art und Weise, in der der Viewport verschoben werden würde




| Sequenz           | Code | BESCHREIBUNG | Verhalten                                                                                             |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; S | SU   | Bildlauf nach oben   | Bildlauf nach oben um &lt; n &gt; . Auch als "Pan Down" bezeichnet, werden neue Zeilen unten auf dem Bildschirm angezeigt. |
| ESC \[ &lt; n &gt; T | SD   | Bildlauf nach unten | Scrollen Sie nach unten um &lt; n &gt; . Auch als "schwenken" bezeichnet, werden neue Zeilen am oberen Rand des Bildschirms angezeigt.         |



Der Text wird beginnend mit der Zeile verschoben, in der sich der Cursor befindet. Wenn sich der Cursor in der mittleren Zeile des Viewports befindet, verschiebt der Bildlauf nach oben die untere Hälfte des Viewports und fügt unten leere Zeilen ein. Scrollen Sie nach unten, um die obere Hälfte der Zeilen des Viewports zu verschieben, und fügen Sie oben neue Zeilen ein.

Wichtig zu beachten ist, dass der Bildlauf nach oben und unten auch durch die scrollränder beeinträchtigt wird. Ein Bildlauf nach oben und unten wirkt sich nicht auf Zeilen außerhalb der scrollränder aus.

Der Standardwert für &lt; n &gt; ist 1, und der Wert kann optional ausgelassen werden.

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Änderung


Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufruf von [**fillconsoleoutputcharacter**](fillconsoleoutputcharacter.md)-, [**fillconsoleoutputattribute**](fillconsoleoutputattribute.md)-und [**scrollconsolescreenbuffer**](scrollconsolescreenbuffer.md) -Konsolen-APIs, um den Inhalt des Text Puffers zu ändern.


| Sequenz           | Code | BESCHREIBUNG      | Verhalten                                                                                                                                          |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n&gt; @ | Reichen  | Zeichen einfügen | Fügen &lt; &gt; Sie n Leerzeichen an der aktuellen Cursorposition ein, und verschieben Sie den gesamten vorhandenen Text nach rechts. Der Text, der den Bildschirm rechts verlässt, wird entfernt. |
| ESC \[ &lt; n &gt; P | DCH  | Zeichen löschen | Löschen Sie &lt; n &gt; Zeichen an der aktuellen Cursorposition, und verschieben Sie die Leerzeichen vom rechten Rand des Bildschirms.                       |
| ESC \[ &lt; n &gt; X | E  | Löschzeichen  | Löschen &lt; &gt; Sie n Zeichen aus der aktuellen Cursorposition, indem Sie Sie mit einem Leerzeichen überschreiben.                                           |
| ESC \[ &lt; n &gt; L | BY   | Zeile einfügen      | Fügt &lt; n &gt; Zeilen an der Cursorposition in den Puffer ein. Die Zeile, in der sich der Cursor befindet, und die darunter liegenden Zeilen werden nach unten verschoben.         |
| ESC \[ &lt; n &gt; M | DL   | Zeile löschen      | Löscht &lt; n &gt; Zeilen aus dem Puffer, beginnend mit der Zeile, in der sich der Cursor befindet.                                                                  |



**Hinweis**  
Für Il und DL sind nur die Zeilen in den scrollrändern betroffen (siehe scrollränder). Wenn keine Ränder festgelegt sind, sind die Standardrand Ränder der aktuelle Viewport. Wenn Linien unter die Ränder verschoben werden, werden Sie verworfen. Wenn Zeilen gelöscht werden, werden am unteren Rand der Ränder leere Zeilen eingefügt, ohne dass Zeilen von außerhalb des Viewports betroffen sind.

Der Standardwert für n, wenn der Wert &lt; &gt; weggelassen wird, ist 0 (null).



Für die folgenden Befehle weist der Parameter &lt; n &gt; drei gültige Werte auf:

- 0 löscht von der aktuellen Cursorposition (einschließlich) bis zum Ende der Zeile/Anzeige.
- 1 löscht am Anfang der Zeile/Anzeige bis einschließlich der aktuellen Cursorposition.
- 2 löscht die gesamte Zeile/Anzeige.


| Sequenz           | Code | BESCHREIBUNG      | Verhalten                                                                                     |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; J | ED   | In Anzeige löschen | Ersetzt den gesamten Text im aktuellen Viewport/Bildschirm, der durch n angegeben ist, &lt; &gt; durch Leerzeichen. |
| ESC \[ &lt; n &gt; K | Tanken   | In Zeile löschen    | Ersetzt den gesamten Text in der Zeile durch den durch n angegebenen Cursor &lt; &gt; mit Leerzeichen.    |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatierung


Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufrufen von [**SetConsoleTextAttribute**](setconsoletextattribute.md) -Konsolen-APIs, um die Formatierung aller zukünftigen Schreibvorgänge in den Konsolenausgabe Text Puffer anzupassen.

Dieser Befehl ist ein besonderes Zeichen, da die &lt; n &gt; -Position unten zwischen 0 und 16 durch Semikolons getrennte Parameter annehmen kann.

Wenn keine Parameter angegeben werden, wird diese wie ein einzelner 0-Parameter behandelt.


| Sequenz           | Code | BESCHREIBUNG            | Verhalten                                                        |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| ESC \[ &lt; n &gt; m | SGR  | Grafikwiedergabe festlegen | Legen Sie das Format des Bildschirms und des Texts gemäß Angabe durch n fest. &lt;&gt; |



Die folgende Tabelle mit Werten kann in &lt; n &gt; zur Darstellung unterschiedlicher Formatierungs Modi verwendet werden.

Formatierungs Modi werden von links nach rechts angewendet. Wenn Sie konkurrierende Formatierungsoptionen anwenden, führt dies dazu, dass die Rechte Option Vorrang hat.

Für Optionen, die Farben angeben, werden die Farben entsprechend der Definition in der Konsolen Farbtabelle verwendet, die mit der [**setconsoleskreenbufferinfoex**](setconsolescreenbufferinfoex.md) -API geändert werden kann. Wenn die Tabelle so geändert wird, dass die "Blaue" Position in der Tabelle den RGB-Farbton rot anzeigt, werden alle Aufrufe an **Vordergrund blau** die rote Farbe anzeigen, bis Sie anderweitig geändert werden.


| Wert | BESCHREIBUNG               | Verhalten                                                           |
|-------|---------------------------|--------------------------------------------------------------------|
| 0     | Standard                   | Gibt vor der Änderung alle Attribute in den Standardzustand zurück.  |
| 1     | Fett/hell               | Wendet das Flag für Helligkeit/Intensität auf Vordergrundfarbe an              |
| 4     | Underline                 | Fügt Unterstreichung hinzu                                                     |
| 24    | Keine Unterstreichung              | Entfernt Unterstreichung                                                  |
| 7     | Negativ                  | Vertauscht Vordergrund-und Hintergrundfarben                             |
| 27    | Positiv (keine negative)    | Gibt Vordergrund/Hintergrund für normal zurück                            |
| 30    | Vordergrund schwarz          | Gilt für den Vordergrund ohne Fett/Hellschwarz.                        |
| 31    | Vordergrund rot            | Gilt für den Vordergrund ohne Fett/hellrot.                          |
| 32    | Vordergrund grün          | Gilt für den Vordergrund ohne Fett/hellgrün.                        |
| 33    | Vordergrund gelb         | Gilt für den Vordergrund ohne Fett/hellgelb.                       |
| 34    | Vordergrund blau           | Gilt für den Vordergrund ohne Fett/hellblau.                         |
| 35    | Vordergrund Magenta        | Wendet nicht Fett/hellgrün auf Vordergrund an                      |
| 36    | Vordergrund-Cyan           | Wendet nicht Fett/hell Zyan auf Vordergrund an                         |
| 37    | Vordergrund weiß          | Wendet nicht Fett/hell weiß auf Vordergrund an                        |
| 38    | Vordergrund erweitert       | Wendet den erweiterten Farbwert auf den Vordergrund an (Weitere Informationen finden Sie unten). |
| 39    | Vordergrund Standard        | Wendet nur den Vordergrund-Teil der Standardwerte an (siehe 0).        |
| 40    | Hintergrund schwarz          | Gilt für den Hintergrund "nicht Fett/Hellschwarz".                        |
| 41    | Roter Hintergrund            | Gilt für den Hintergrund "nicht Fett/hell"                          |
| 42    | Hintergrund grün          | Gilt für den Hintergrund "nicht Fett/hellgrün"                        |
| 43    | Hintergrund Gelb         | Gilt für den Hintergrund "nicht Fett/hell gelb"                       |
| 44    | Hintergrund blau           | Gilt für den Hintergrund "nicht Fett/hellblau".                         |
| 45    | Hintergrund Magenta        | Wendet nicht Fett/hell auf den Hintergrund an                      |
| 46    | Background Cyan           | Wendet nicht Fett/hell Zyan auf den Hintergrund an.                         |
| 47    | Hintergrund weiß          | Gilt für den Hintergrund "nicht Fett/hell weiß".                        |
| 48    | Erweiterter Hintergrund       | Wendet den erweiterten Farbwert auf den Hintergrund an (Weitere Informationen finden Sie unten). |
| 49    | Standard Hintergrund        | Wendet nur den Hintergrund Teil der Standardwerte an (siehe 0).        |
| 90    | Heller Vordergrund schwarz   | Wendet Fett/Hellschwarz auf Vordergrund an                            |
| 91    | Heller Vordergrund rot     | Wendet Fett/hell rot auf Vordergrund an                              |
| 92    | Heller Vordergrund grün   | Wendet Fett/hellgrün auf Vordergrund an                            |
| 93    | Heller Vordergrund gelb  | Wendet Fett/hell gelb auf Vordergrund an                           |
| 94    | Heller Vordergrund blau    | Wendet Fett/hell blau auf Vordergrund an                             |
| 95    | Heller Vordergrund Magenta | Wendet Bold/hellmagenta auf Vordergrund an                          |
| 96    | Heller Vordergrund-Cyan    | Wendet Bold/hell Zyan auf Vordergrund an                             |
| 97    | Heller Vordergrund weiß   | Wendet Fett/hell weiß auf Vordergrund an                            |
| 100   | Heller Hintergrund schwarz   | Wendet Fett/Hellschwarz auf den Hintergrund an.                            |
| 101   | Heller Hintergrund rot     | Wendet Fett/hell rot auf den Hintergrund an.                              |
| 102   | Heller Hintergrund grün   | Wendet Fett/hellgrün auf Hintergrund an                            |
| 103   | Heller Hintergrund Gelb  | Wendet Fett/hell gelb auf den Hintergrund an.                           |
| 104   | Heller Hintergrund blau    | Wendet Fett/hellblau auf den Hintergrund an.                             |
| 105   | Heller Hintergrund Magenta | Wendet Bold/hellmagenta auf den Hintergrund an.                          |
| 106   | Heller Hintergrund Cyan    | Wendet Bold/hell Zyan auf den Hintergrund an.                             |
| 107   | Heller Hintergrund weiß   | Wendet Fett/hell weiß auf Hintergrund an                            |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Erweiterte Farben

Einige virtuelle Terminal Emulatoren unterstützen eine Palette von Farben, die größer sind als die von der Windows-Konsole bereitgestellten Farben. Für diese erweiterten Farben wählt die Windows-Konsole die nächstgelegene Farbe aus der vorhandenen 16-Farbtabelle zum Anzeigen aus. Im Gegensatz zu typischen SGR-Werten verbrauchen die erweiterten Werte nach dem anfänglichen Indikator gemäß der folgenden Tabelle zusätzliche Parameter.


| SGR-unter Sequenz                            | Beschreibung                                                                                 |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| 38; 2,2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt; | Festlegen der Vordergrundfarbe auf RGB-Wert in &lt; r- &gt; , &lt; g- &gt; , b- &lt; &gt; Parametern\* |
| 48; 2,2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt; | Legen Sie die Hintergrundfarbe auf den in &lt; r- &gt; , &lt; g- &gt; , b- &lt; &gt; Parametern\* |
| 38; 5@@ &lt;s&gt;                         | Festlegen der Vordergrundfarbe auf den &lt; s- &gt; Index in 88-oder 256-Farbtabelle\*                          |
| 48; 5@@ &lt;s&gt;                         | Festlegen der Hintergrundfarbe auf den &lt; s- &gt; Index in der 88-oder 256-Farbtabelle\*                          |



\*Die Farbpaletten 88 und 256, die intern für Vergleiche verwaltet werden, basieren auf dem xterm-Terminal Emulator. Die Vergleichs-/Rundungs Tabellen können zu diesem Zeitpunkt nicht geändert werden.


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Bildschirmfarben


Der folgende Befehl ermöglicht es der Anwendung, die Farbpalette-Werte der Bildschirmfarben auf einen beliebigen RGB-Wert festzulegen.

Die RGB-Werte sollten hexadezimal Werte zwischen `0` und sein `ff` und durch den Schrägstrich (z. b. `rgb:1/24/86` ) getrennt werden.

Beachten Sie, dass es sich bei dieser Sequenz um eine "Command"-Sequenz vom Typ "osc" handelt, nicht um ein CSI wie viele der anderen aufgelisteten Sequenzen, und beginnen Sie mit " \\ x1B \] " und nicht mit " \\ x1B \[ ".


| Sequenz                                                           | BESCHREIBUNG          | Verhalten                                                                                                     |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| ESC \] 4; &lt; i &gt; ; RGB: &lt; r &gt;  /  &lt; g &gt;  /  &lt; b &gt; ESC | Ändern der Bildschirmfarben | Legt den Bildschirm Farbpalette-Index &lt; i &gt; auf die RGB-Werte fest, die in &lt; r &gt; , &lt; g &gt; , &lt; b angegeben sind.&gt; |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modusänderungen


Dabei handelt es sich um Sequenzen, die die Eingabemodi steuern. Es gibt zwei unterschiedliche Sätze von Eingabemodi: den Cursor Schlüssel Modus und den Keypad-Schlüssel Modus. Der Cursor Schlüssel Modus steuert die Sequenzen, die von den Pfeiltasten sowie von Start-und Endzeichen ausgegeben werden, während der Keypad-Schlüssel Modus die von den Schlüsseln im NumPad ausgegebene Sequenzen und die Funktionstasten steuert.

Jeder dieser Modi ist eine einfache boolesche Einstellung – der Cursor Schlüssel Modus ist entweder normal (Standard) oder Anwendung, und der Keypad-Schlüssel Modus ist entweder numerisch (Standard) oder Anwendung.

Weitere Informationen zu den in diesen Modi ausgegebenen Sequenzen finden Sie in den Abschnitten Cursor Schlüssel und Numpad &-Funktions Schlüsseln.


| Sequenz     | Code    | BESCHREIBUNG                                            | Verhalten                                                |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| ESC =        | Deckpam | Aktivieren des Keypad-Anwendungsmodus                         | Keypad-Schlüssel geben Ihre anwendungsmodussequenzen aus. |
| Dor &gt;     | Deckpnm | Aktivieren des numerischen Keypad-Modus                             | Keypad-Schlüssel geben ihre numerischen modussequenzen aus.     |
| ESC \[ ? 1 Stunde | Decckm  | Aktivieren des Anwendungsmodus für Cursor Tasten                    | Keypad-Schlüssel geben Ihre anwendungsmodussequenzen aus. |
| ESC \[ ? 1 l | Decckm  | Deaktivieren Sie den Anwendungsmodus für Cursor Tasten (normaler Modus verwenden). | Keypad-Schlüssel geben ihre numerischen modussequenzen aus.     |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Abfrage Status


Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufruf von get \* Console-APIs zum Abrufen von Statusinformationen zum aktuellen Zustand der Konsolen Puffer.

**Hinweis**  Diese Abfragen geben Ihre Antworten sofort in den Konsolen Eingabestream aus, wenn Sie im Ausgabestream erkannt werden, während die \_ virtuelle \_ Terminal \_ Verarbeitung aktiviert ist. Das \_ \_ eingabeflag "virtuelles Terminal aktivieren" \_ gilt nicht für Abfrage Befehle, da davon ausgegangen wird, dass eine Anwendung, die die Abfrage erstellt, die Antwort immer empfangen möchte.




| Sequenz   | Code    | BESCHREIBUNG            | Verhalten                                                                                                               |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| ESC \[ 6 n | Decxcpr | Cursor Position des Berichts | Geben Sie die Cursorposition wie folgt aus: Esc \[ &lt; r &gt; ; &lt; c &gt; r Where &lt; R &gt; = Cursor Zeile und &lt; c &gt; = Cursor Spalte |
| ESC \[ 0 c | De      | Geräte Attribute      | Melden Sie die Terminal Identität. Gibt " \\ x1B \[ ? 1; 0C" aus, was "VT101 ohne Optionen" angibt.                            |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tafeln


Obwohl die Windows-Konsole normalerweise davon ausgeht, dass Registerkarten ausschließlich acht Zeichen umfassen, \* können nix-Anwendungen, die bestimmte Sequenzen verwenden, bearbeiten, wo sich die Tabstopps innerhalb der Konsolenfenster befinden, um die Cursor Bewegung durch die Anwendung zu optimieren

Die folgenden Sequenzen ermöglichen es einer Anwendung, die Position der Tabstopps innerhalb des Konsolenfensters festzulegen, Sie zu entfernen und zwischen Ihnen zu navigieren.


| Sequenz           | Code | BESCHREIBUNG                     | Verhalten                                                                                                                                                                                                                    |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC H              | HTS  | Horizontaler Registerkarten Satz              | Legt einen Tabstopp in der aktuellen Spalte fest, in der sich der Cursor befindet.                                                                                                                                                                     |
| ESC \[ &lt; n &gt; I | CHT  | Horizontale Cursor Registerkarte (vorwärts) | Bewegen Sie den Cursor mit einer Tabstopp Taste zur nächsten Spalte (in derselben Zeile). Wenn keine weiteren Tabstopps vorhanden sind, fahren Sie mit der letzten Spalte in der Zeile fort. Wenn sich der Cursor in der letzten Spalte befindet, wechseln Sie zur ersten Spalte der nächsten Zeile. |
| ESC \[ &lt; n &gt; Z | CBT  | Cursor Registerkarte rückwärts            | Bewegen Sie den Cursor in die vorherige Spalte (in derselben Zeile) mit einer Tabstopp Taste. Wenn keine weiteren Tabstopps vorhanden sind, verschiebt den Cursor zur ersten Spalte. Wenn sich der Cursor in der ersten Spalte befindet, verschiebt den Cursor nicht.              |
| ESC \[ 0 g         | TBC  | Tab Clear (aktuelle Spalte)      | Löscht den Tabstopp in der aktuellen Spalte, sofern vorhanden. Andernfalls geschieht nichts.                                                                                                                                         |
| ESC \[ 3 g         | TBC  | Tab Clear (alle Spalten)         | Löscht alle momentan festgelegten Tabstopps.                                                                                                                                                                                         |



- Bei n und CBT &lt; &gt; ist n ein optionaler Parameter, der (Standardwert = 1) angibt, wie oft der Cursor in der angegebenen Richtung vorwärts bewegt werden soll.
- Wenn keine Tabstopps über HTS festgelegt sind, werden die erste und die letzte Spalte des Fensters von cht und CBT als die einzigen beiden Tabstopps behandelt.
- Die Verwendung von HTS zum Festlegen eines Tabstopps bewirkt auch, dass die Konsole in der Ausgabe eines Tabstopps (0x09, " \\ t") auf die gleiche Weise wie bei cht zum nächsten Tabstopp navigiert.

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Zeichensatz festlegen


Die folgenden Sequenzen ermöglichen einem Programm, die Zuordnung des aktiven Zeichensatzes zu ändern. Dies ermöglicht es einem Programm, 7-Bit-ASCII-Zeichen auszugeben, Sie aber als andere Symbole auf dem Terminalbildschirm selbst anzuzeigen. Zurzeit sind die einzigen beiden unterstützten Zeichensätze ASCII (Standard) und der besondere Grafik Zeichensatz für Dec. Unter finden Sie <http://vt100.net/docs/vt220-rm/table2-4.html> eine Liste aller Zeichen, die durch den speziellen Dec-Grafik Zeichensatz dargestellt werden.


| Sequenz | BESCHREIBUNG                                | Verhalten                      |
|----------|--------------------------------------------|-------------------------------|
| ESC (0  | Zeichensatz festlegen – Dec-Zeichnungs Linie | Aktiviert den Modus "Dec Line Drawing" |
| ESC (B  | Festlegen des Zeichensatzes – US-ASCII         | Aktiviert den ASCII-Modus (Standard)  |



Insbesondere wird der Dec-Zeichnungsmodus zum Zeichnen von Rahmen in Konsolen Anwendungen verwendet. In der folgenden Tabelle ist dargestellt, welche ASCII-Zeichen mit welchem Zeilen Zeichnungs Zeichen zugeordnet werden.


| Hex  | ASCII | Zeilen Zeichnung mit Dec |
|------|-------|------------------|
| 0x6a | j     | ┘                |
| 0x6b | k     | ┐                |
| 0x6C | l     | ┌                |
| 0x6d | m     | └                |
| 0x6e | n     | ┼                |
| 0x71 | q     | ─                |
| 0x74 | t     | ├                |
| 0x75 | u     | ┤                |
| 0x76 | v     | ┴                |
| 0x77 | w     | ┬                |
| 0x78 | x     | │                |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrollränder


Die folgenden Sequenzen ermöglichen einem Programm, den "scrollbereich" des Bildschirms zu konfigurieren, der von scrollvorgängen betroffen ist. Dabei handelt es sich um eine Teilmenge der Zeilen, die angepasst werden, wenn auf dem Bildschirm ein anderer Bildlauf durchführt, z. b. auf einem \\ n-oder RI-. Diese Ränder wirken sich auch auf die Zeilen aus, die durch Einfügezeile (IL) und Delete Line (DL) geändert werden, Scrollen nach oben (su) und Scrollen nach unten (SD).

Die scrollränder können besonders nützlich sein, wenn ein Teil des Bildschirms angezeigt wird, wenn der restliche Bildschirm nicht angezeigt wird, z. b. eine Titelleiste am oberen Rand oder eine Statusleiste am unteren Rand der Anwendung.

Für decstbm gibt es zwei optionale Parameter: &lt; t &gt; und &lt; b &gt; , die verwendet werden, um die Zeilen anzugeben, die den oberen und unteren Rand des Bild Lauf Bereichs darstellen (einschließlich). Wenn die Parameter ausgelassen werden, lautet der Standardwert 1, wobei &lt; &gt; &lt; b &gt; standardmäßig die aktuelle VIEWPORTHÖHE verwendet.

Scrollränder sind pro Puffer, was wichtig ist, dass der Alternative Puffer und der Hauptpuffer separate Einstellungen für die scrollränder behalten (sodass eine Vollbild-Anwendung im alternativen Puffer die Ränder des Haupt Puffers nicht verbleibt).


| Sequenz                       | Code    | BESCHREIBUNG          | Verhalten                                       |
|--------------------------------|---------|----------------------|------------------------------------------------|
| ESC \[ &lt; t &gt; ; &lt; b &gt; r | Decstbm | Scrollbereich festlegen | Legt die VT-scrollränder des Viewports fest. |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Fenstertitel


Mit den folgenden Befehlen kann die Anwendung den Titel des Konsolenfensters auf den angegebenen Zeichen folgen &lt; &gt; Parameter festlegen. Die Zeichenfolge muss weniger als 255 Zeichen annehmen, um akzeptiert zu werden. Dies entspricht dem Aufrufen von setconsoletitle mit der angegebenen Zeichenfolge.

Beachten Sie, dass es sich bei diesen Sequenzen um die Befehle "Betriebssystem Befehl" des Befehls "osc" handelt, nicht um ein CSI-wie viele der anderen aufgelisteten Sequenzen, und damit beginnt " \\ x1B \] ", nicht " \\ x1B \[ ".


| Sequenz                      | BESCHREIBUNG               | Verhalten                                           |
|-------------------------------|---------------------------|----------------------------------------------------|
| ESC \] 0; &lt; Zeichenfolge &gt; Bel | Symbol und Fenstertitel festlegen | Legt den Titel des Konsolenfensters auf &lt; String fest &gt; . |
| ESC \] 2; &lt; Zeichenfolge &gt; Bel | Fenstertitel festlegen          | Legt den Titel des Konsolenfensters auf &lt; String fest &gt; . |



Das abschließende Zeichen hier ist das "Glocken Zeichen", " \\ x07".

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternativer Bildschirm Puffer


\*Anwendungen im Stil von nix nutzen häufig einen alternativen Bildschirm Puffer, damit Sie den gesamten Inhalt des Puffers ändern können, ohne die Anwendung zu beeinträchtigen, von der Sie gestartet wurden. Der Alternative Puffer ist genau die Abmessungen des Fensters, ohne einen scrollbackfunktionalität Bereich.

Ein Beispiel für dieses Verhalten ist, wenn vim von bash gestartet wird. Vim verwendet den gesamten Bildschirm, um die Datei zu bearbeiten. Wenn Sie zu bash zurückkehren, bleibt der ursprüngliche Puffer unverändert.


| Sequenz           | BESCHREIBUNG                 | Verhalten                                   |
|--------------------|-----------------------------|--------------------------------------------|
| ESC \[ ? 1 0 4 9 h | Alternativen Bildschirm Puffer verwenden | Wechselt zu einem neuen alternativen Bildschirm Puffer. |
| ESC \[ ? 1 0 4 9 l | Hauptbildschirm Puffer verwenden      | Wechselt zum Hauptpuffer.               |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Fensterbreite


Die folgenden Sequenzen können verwendet werden, um die Breite des Konsolenfensters zu steuern. Sie sind ungefähr gleichwertig mit dem Aufruf der Konsolen-API setconsolescreenbufferinfoex zum Festlegen der Fensterbreite.


| Sequenz     | Code    | BESCHREIBUNG                  | Verhalten                                    |
|--------------|---------|------------------------------|---------------------------------------------|
| ESC \[ ? 3 h | Deccolm | Festlegen der Anzahl von Spalten auf 132 | Legt die Konsolen Breite auf 132 Spalten breit fest. |
| ESC \[ ? 3 l | Deccolm | Festlegen der Anzahl von Spalten auf 80  | Legt die Konsolen Breite auf 80 Spalten breit fest.  |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Vorläufiges zurücksetzen


Die folgende Sequenz kann verwendet werden, um bestimmte Eigenschaften auf ihre Standardwerte zurückzusetzen. Die folgenden Eigenschaften werden auf die folgenden Standardwerte zurückgesetzt (Außerdem sind die Sequenzen aufgelistet, die diese Eigenschaften steuern):

- Cursor Sichtbarkeit: sichtbar (dectem)
- Numerische Keypad: numerischer Modus (decnkm)
- Cursor Schlüssel Modus: normaler Modus (decckm)
- Obere und untere Ränder: Top = 1, Bottom = Console Height (decstbm)
- Zeichensatz: US-ASCII
- Grafikwiedergabe: Standard/Off (SGR)
- Cursor Zustand speichern: Startposition (0,0) (decsc)


| Sequenz   | Code   | BESCHREIBUNG | Verhalten                                           |
|------------|--------|-------------|----------------------------------------------------|
| ESC \[ ! p | Decstr | Vorläufiges zurücksetzen  | Setzen Sie bestimmte Terminal Einstellungen auf ihre Standardeinstellungen zurück. |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Eingabe Sequenzen


Die folgenden Terminal Sequenzen werden vom Konsolen Host im Eingabestream ausgegeben, wenn das eingabeflag zum Aktivieren des \_ virtuellen \_ Terminals \_ für das Eingabepuffer Handle mit dem setconsolemode-Flag festgelegt ist.

Es gibt zwei interne Modi, die Steuern, welche Sequenzen für die angegebenen Eingabetasten, den Cursor Schlüssel Modus und den Keypad-Schlüssel Modus ausgegeben werden. Diese werden im Abschnitt Modusänderungen beschrieben.

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Tasten


| Key         | Normaler Modus | Anwendungsmodus |
|-------------|-------------|------------------|
| NACH-OBEN    | ESC \[ A    | ESC O A          |
| NACH-UNTEN  | ESC \[ B    | ESC O B          |
| NACH-RECHTS | ESC \[ C    | ESC O C          |
| NACH-LINKS-TASTE  | ESC \[ D    | ESC O D          |
| Startseite        | ESC \[ H    | ESC O H          |
| Ende         | ESC \[ F    | ESC O F          |



Wenn außerdem STRG mit einem dieser Tasten gedrückt wird, werden stattdessen die folgenden Sequenzen ausgegeben, unabhängig vom Cursor Schlüssel Modus:


| Key                | Beliebiger Modus       |
|--------------------|----------------|
| STRG + nach-oben-Taste    | ESC \[ 1; 5 A |
| STRG + nach-unten-Taste  | ESC \[ 1; 5 B |
| STRG + nach-rechts-Taste | ESC \[ 1; 5 C |
| STRG + nach-links-Taste  | ESC \[ 1; 5 D |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad-& Funktionstasten


| Key       | Sequenz     |
|-----------|--------------|
| Rückschritt | 0x7F (Entf)   |
| Anhalten     | 0x1A (Sub)   |
| Escape    | 0x1B (ESC)   |
| Einfügen    | ESC \[ 2 ~   |
| Löschen    | ESC \[ 3 ~   |
| BILD-AUF   | ESC \[ 5 ~   |
| BILD-AB | ESC \[ 6 ~   |
| F1        | ESC O P      |
| F2        | ESC O Q      |
| F3        | ESC O R      |
| F4        | ESC O S      |
| F5        | ESC \[ 1 5 ~ |
| F6        | ESC \[ 1 7 ~ |
| F7        | ESC \[ 1 8 ~ |
| F8        | ESC \[ 1 9 ~ |
| F9        | ESC \[ 2 0 ~ |
| F10       | ESC \[ 2 1 ~ |
| F11       | ESC \[ 2 3 ~ |
| F12       | ESC \[ 2 4 ~ |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifizierer

Alt wird behandelt, indem die Sequenz mit einem Escapezeichen versehen wird: Esc &lt; c, &gt; wobei &lt; c &gt; das vom Betriebssystem über gegebene Zeichen ist. Alt + Strg wird auf die gleiche Weise behandelt, außer dass das Betriebssystem den &lt; c-Schlüssel vorab &gt; in das entsprechende Steuerzeichen verschoben hat, das an die Anwendung weitergeleitet wird.

STRG wird im allgemeinen genau so durchlaufen, wie vom System empfangen. Dabei handelt es sich in der Regel um ein einzelnes Zeichen, das in den reservierten Leerraum des Steuer Zeichens (0x0-0x1F) verschoben wird. Beispielsweise wird STRG + @ (0x40) zu NUL (0x00), STRG + \[ (0x5b) wird ESC (0x1B) usw. Einige Tastenkombinationen für STRG werden in der folgenden Tabelle speziell behandelt:


| Key                | Sequenz       |
|--------------------|----------------|
| STRG+LEERTASTE       | 0x00 (NUL)     |
| STRG + nach-oben-Taste    | ESC \[ 1; 5 A |
| STRG + nach-unten-Taste  | ESC \[ 1; 5 B |
| STRG + nach-rechts-Taste | ESC \[ 1; 5 C |
| STRG + nach-links-Taste  | ESC \[ 1; 5 D |



**Hinweis**  Left STRG + Right Alt wird als AltGr behandelt. Wenn beide angezeigt werden, werden Sie entfernt, und der Unicode-Wert des vom System dargestellten Zeichens wird an das Ziel übermittelt. Das System übersetzt AltGr-Werte vorab gemäß den aktuellen System Eingabeeinstellungen.



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Stich


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span id="example"></span><span id="EXAMPLE"></span>Beispiel für SGR-Terminal Sequenzen

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

**Hinweis**  Im vorherigen Beispiel ist die Zeichenfolge " `\x1b[31m` " die Implementierung von **ESC \[ &lt; n &gt; m** mit &lt; n &gt; 31.



Die folgende Grafik zeigt die Ausgabe des vorherigen Code Beispiels.

![Ausgabe der Konsole mit dem SGR-Befehl](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Beispiel für das Aktivieren der virtuellen Terminal Verarbeitung

Der folgende Code enthält ein Beispiel für die empfohlene Vorgehensweise zum Aktivieren der virtuellen Terminal Verarbeitung für eine Anwendung. Das Beispiel soll Folgendes veranschaulichen:

1. Der vorhandene Modus sollte immer über getconsolemode abgerufen und analysiert werden, bevor er mit setconsolemode festgelegt wird.

2. Überprüfen, ob setconsolemode zurückgibt `0` und GetLastError den Status " \_ Ungültiger Parameter" zurückgibt \_ , ist der aktuelle Mechanismus zum Bestimmen der Ausführung auf einem System mit einer Ebene Eine Anwendung, die den Status \_ ungültige Parameter empfängt, \_ und eine der neueren Konsolenmodus-Flags im Bitfeld, sollte das Verhalten ordnungsgemäß herabstufen und den Vorgang wiederholen.

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Beispiel für die SELECT Anniversary Update-Features

Das folgende Beispiel soll ein stabileres Codebeispiel sein, bei dem eine Reihe von Escapesequenzen zum Bearbeiten des Puffers verwendet werden, wobei der Schwerpunkt auf den Features liegt, die im Anniversary Update für Windows 10 hinzugefügt wurden.

In diesem Beispiel wird der Alternative Bildschirm Puffer verwendet, Tabstopps werden bearbeitet, scrollränder werden festgelegt, und der Zeichensatz wird geändert.

```C
//
//    Copyright (C) Microsoft.  All rights reserved.
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
    printf(ESC "(0");       // Enter Line drawing mode
    printf(CSI "104;93m");   // bright yellow on bright blue
    printf("x");            // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
    printf(CSI "0m");       // restore color
    printf(ESC "(B");       // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
    printf(ESC "(0");       // Enter Line drawing mode
    printf(CSI "104;93m");  // Make the border bright yellow on bright blue
    printf(fIsTop? "l" : "m"); // print left corner 

    for (int i = 1; i < Size.X - 1; i++) 
        printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

    printf(fIsTop? "k" : "j"); // print right corner
    printf(CSI "0m");
    printf(ESC "(B");       // exit line drawing mode
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
    Size.Y = ScreenBufferInfo.srWindow.Bottom -  ScreenBufferInfo.srWindow.Top + 1;

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








