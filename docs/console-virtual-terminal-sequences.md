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
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="51d00-104">Konsolen virtuelle Terminal Sequenzen</span><span class="sxs-lookup"><span data-stu-id="51d00-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="51d00-105">Virtuelle Terminal Sequenzen sind Steuerungs Zeichenfolgen, die beim Schreiben in den Ausgabestream die Cursor Bewegung, den Farb-/schriftmodus und andere Vorgänge steuern können.</span><span class="sxs-lookup"><span data-stu-id="51d00-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="51d00-106">Sequenzen können auch als Antwort auf eine Abfrage Informations Sequenz für den Ausgabestream oder als Codierung von Benutzereingaben im Eingabedaten Strom empfangen werden, wenn der entsprechende Modus festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="51d00-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="51d00-107">Sie können dieses Verhalten mit [**getconsolemode**](getconsolemode.md) -und [**setconsolemode**](setconsolemode.md) -Funktionen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="51d00-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="51d00-108">Ein Beispiel für die empfohlene Vorgehensweise zum Aktivieren des Verhaltens von virtuellen Endgeräten finden Sie am Ende dieses Dokuments.</span><span class="sxs-lookup"><span data-stu-id="51d00-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="51d00-109">Das Verhalten der folgenden Sequenzen basiert auf den VT100-und abgeleiteten terminalemulatortechnologien, insbesondere dem xterm-Terminal Emulator.</span><span class="sxs-lookup"><span data-stu-id="51d00-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="51d00-110">Weitere Informationen zu Terminal Sequenzen finden Sie unter <http://vt100.net> und unter <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html> .</span><span class="sxs-lookup"><span data-stu-id="51d00-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="51d00-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Ausgabe Sequenzen</span><span class="sxs-lookup"><span data-stu-id="51d00-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="51d00-112">Die folgenden Terminal Sequenzen werden vom Konsolen Host abgefangen, wenn Sie in den Ausgabestream geschrieben werden, wenn das Flag zum Aktivieren der \_ virtuellen \_ Terminal \_ Verarbeitung auf dem Bildschirm Puffer Handle mithilfe der [**setconsolemode**](setconsolemode.md) -Funktion festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="51d00-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="51d00-113">Beachten Sie, dass das \_ \_ automatische \_ rückgabeflag zum Deaktivieren von Zeilen Vorgängen auch nützlich sein kann, um das Cursor Positions-und Bild Laufverhalten anderer Terminalemulatoren in Bezug auf Zeichen zu emulieren, die in der letzten Spalte in einer Zeile</span><span class="sxs-lookup"><span data-stu-id="51d00-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="51d00-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Einfache Cursor Positionierung</span><span class="sxs-lookup"><span data-stu-id="51d00-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="51d00-115">Bei allen folgenden Beschreibungen ist ESC immer der hexadezimale Wert 0x1B.</span><span class="sxs-lookup"><span data-stu-id="51d00-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="51d00-116">Es sind keine Leerzeichen in Terminal Sequenzen enthalten.</span><span class="sxs-lookup"><span data-stu-id="51d00-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="51d00-117">Ein Beispiel für die Verwendung dieser Sequenzen in der Praxis finden Sie im [Beispiel](#example) am Ende dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="51d00-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="51d00-118">In der folgenden Tabelle werden einfache Escapesequenzen mit einem einzelnen Action-Befehl direkt nach dem ESC-Zeichen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="51d00-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="51d00-119">Diese Sequenzen verfügen über keine Parameter und treten sofort in Kraft.</span><span class="sxs-lookup"><span data-stu-id="51d00-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="51d00-120">Alle Befehle in dieser Tabelle entsprechen in der Regel dem Aufrufen der [**SetConsoleCursorPosition**](setconsolecursorposition.md) -Konsolen-API, um den Cursor zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="51d00-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="51d00-121">Die Cursor Bewegung wird vom aktuellen Viewport in den Puffer gebunden.</span><span class="sxs-lookup"><span data-stu-id="51d00-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="51d00-122">Der Bildlauf (falls verfügbar) erfolgt nicht.</span><span class="sxs-lookup"><span data-stu-id="51d00-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="51d00-123">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-123">Sequence</span></span> | <span data-ttu-id="51d00-124">Kurzform</span><span class="sxs-lookup"><span data-stu-id="51d00-124">Shorthand</span></span> | <span data-ttu-id="51d00-125">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-125">Behavior</span></span>                                                                                                                                      |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="51d00-126">ESC A</span><span class="sxs-lookup"><span data-stu-id="51d00-126">ESC A</span></span>    | <span data-ttu-id="51d00-127">Cuu</span><span class="sxs-lookup"><span data-stu-id="51d00-127">CUU</span></span>       | <span data-ttu-id="51d00-128">Cursor nach oben um 1</span><span class="sxs-lookup"><span data-stu-id="51d00-128">Cursor Up by 1</span></span>                                                                                                                                |
| <span data-ttu-id="51d00-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="51d00-129">ESC B</span></span>    | <span data-ttu-id="51d00-130">CUD</span><span class="sxs-lookup"><span data-stu-id="51d00-130">CUD</span></span>       | <span data-ttu-id="51d00-131">Cursor nach unten um 1</span><span class="sxs-lookup"><span data-stu-id="51d00-131">Cursor Down by 1</span></span>                                                                                                                              |
| <span data-ttu-id="51d00-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="51d00-132">ESC C</span></span>    | <span data-ttu-id="51d00-133">CUF</span><span class="sxs-lookup"><span data-stu-id="51d00-133">CUF</span></span>       | <span data-ttu-id="51d00-134">Cursor vorwärts (rechts) um 1</span><span class="sxs-lookup"><span data-stu-id="51d00-134">Cursor Forward (Right) by 1</span></span>                                                                                                                   |
| <span data-ttu-id="51d00-135">ESC D</span><span class="sxs-lookup"><span data-stu-id="51d00-135">ESC D</span></span>    | <span data-ttu-id="51d00-136">Cub</span><span class="sxs-lookup"><span data-stu-id="51d00-136">CUB</span></span>       | <span data-ttu-id="51d00-137">Cursor nach hinten (links) um 1</span><span class="sxs-lookup"><span data-stu-id="51d00-137">Cursor Backward (Left) by 1</span></span>                                                                                                                   |
| <span data-ttu-id="51d00-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="51d00-138">ESC M</span></span>    | <span data-ttu-id="51d00-139">RI</span><span class="sxs-lookup"><span data-stu-id="51d00-139">RI</span></span>        | <span data-ttu-id="51d00-140">Umgekehrter Index – führt den umgekehrten Vorgang von \\ n aus, verschiebt den Cursor um eine Zeile nach oben, behält die horizontale Position bei Bedarf und scrollt den Puffer.\*</span><span class="sxs-lookup"><span data-stu-id="51d00-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="51d00-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="51d00-141">ESC 7</span></span>    | <span data-ttu-id="51d00-142">Entschlüsseln</span><span class="sxs-lookup"><span data-stu-id="51d00-142">DECSC</span></span>     | <span data-ttu-id="51d00-143">Cursor Position im Arbeitsspeicher speichern\*\*</span><span class="sxs-lookup"><span data-stu-id="51d00-143">Save Cursor Position in Memory\*\*</span></span>                                                                                                            |
| <span data-ttu-id="51d00-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="51d00-144">ESC 8</span></span>    | <span data-ttu-id="51d00-145">Decsr</span><span class="sxs-lookup"><span data-stu-id="51d00-145">DECSR</span></span>     | <span data-ttu-id="51d00-146">Cursor Position aus dem Arbeitsspeicher wiederherstellen\*\*</span><span class="sxs-lookup"><span data-stu-id="51d00-146">Restore Cursor Position from Memory\*\*</span></span>                                                                                                       |



<span data-ttu-id="51d00-147">**Hinweis**</span><span class="sxs-lookup"><span data-stu-id="51d00-147">**Note**</span></span>  
<span data-ttu-id="51d00-148">\* Wenn Bild Lauf Ränder festgelegt sind, führt RI innerhalb der Ränder nur einen Bildlauf durch den Inhalt der Ränder durch und lässt den Viewport unverändert.</span><span class="sxs-lookup"><span data-stu-id="51d00-148">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="51d00-149">(Siehe scrollränder)</span><span class="sxs-lookup"><span data-stu-id="51d00-149">(See Scrolling Margins)</span></span>

<span data-ttu-id="51d00-150">\*\*Es wird kein Wert im Arbeitsspeicher gespeichert, bis der Befehl zum Speichern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="51d00-150">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="51d00-151">Die einzige Möglichkeit, auf den gespeicherten Wert zuzugreifen, ist der Restore-Befehl.</span><span class="sxs-lookup"><span data-stu-id="51d00-151">The only way to access the saved value is with the restore command.</span></span>



## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="51d00-152"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positionierung</span><span class="sxs-lookup"><span data-stu-id="51d00-152"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="51d00-153">In den folgenden Tabellen sind die typsequenzen von "Control Sequence Introduction" (CSI).</span><span class="sxs-lookup"><span data-stu-id="51d00-153">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="51d00-154">Alle CSI-Sequenzen beginnen mit ESC (0x1B), gefolgt von \[ (linker Klammer, 0x5b) und können Parameter der Variablen Länge enthalten, um für jeden Vorgang Weitere Informationen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="51d00-154">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="51d00-155">Dies wird durch die kurzzeitangabe &lt; dargestellt &gt; .</span><span class="sxs-lookup"><span data-stu-id="51d00-155">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="51d00-156">Jede Tabelle unten ist nach Funktionalität gruppiert, wobei die einzelnen Tabellen die Funktionsweise der Gruppe erläutern.</span><span class="sxs-lookup"><span data-stu-id="51d00-156">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="51d00-157">Für alle Parameter gelten die folgenden Regeln, sofern nichts anderes angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="51d00-157">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="51d00-158">&lt;n &gt; stellt den zu verschiebende Abstand dar und ist ein optionaler Parameter.</span><span class="sxs-lookup"><span data-stu-id="51d00-158">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="51d00-159">Wenn &lt; n &gt; weggelassen wird oder 0 (null) ist, wird er als 1 behandelt.</span><span class="sxs-lookup"><span data-stu-id="51d00-159">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="51d00-160">&lt;n &gt; kann nicht größer als 32.767 (maximaler Kurzwert) sein.</span><span class="sxs-lookup"><span data-stu-id="51d00-160">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="51d00-161">&lt;n &gt; darf nicht negativ sein.</span><span class="sxs-lookup"><span data-stu-id="51d00-161">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="51d00-162">Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufrufen der Konsolen-API [**SetConsoleCursorPosition**](setconsolecursorposition.md) .</span><span class="sxs-lookup"><span data-stu-id="51d00-162">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="51d00-163">Die Cursor Bewegung wird vom aktuellen Viewport in den Puffer gebunden.</span><span class="sxs-lookup"><span data-stu-id="51d00-163">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="51d00-164">Der Bildlauf (falls verfügbar) erfolgt nicht.</span><span class="sxs-lookup"><span data-stu-id="51d00-164">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="51d00-165">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-165">Sequence</span></span>                       | <span data-ttu-id="51d00-166">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-166">Code</span></span>      | <span data-ttu-id="51d00-167">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-167">Description</span></span>                         | <span data-ttu-id="51d00-168">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-168">Behavior</span></span>                                                                                                                   |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="51d00-169">ESC \[ &lt; n &gt; A</span><span class="sxs-lookup"><span data-stu-id="51d00-169">ESC \[ &lt;n&gt; A</span></span>             | <span data-ttu-id="51d00-170">Cuu</span><span class="sxs-lookup"><span data-stu-id="51d00-170">CUU</span></span>       | <span data-ttu-id="51d00-171">Cursor nach oben</span><span class="sxs-lookup"><span data-stu-id="51d00-171">Cursor Up</span></span>                           | <span data-ttu-id="51d00-172">Cursor nach oben um &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="51d00-172">Cursor up by &lt;n&gt;</span></span>                                                                                                     |
| <span data-ttu-id="51d00-173">ESC \[ &lt; n &gt; B</span><span class="sxs-lookup"><span data-stu-id="51d00-173">ESC \[ &lt;n&gt; B</span></span>             | <span data-ttu-id="51d00-174">CUD</span><span class="sxs-lookup"><span data-stu-id="51d00-174">CUD</span></span>       | <span data-ttu-id="51d00-175">Cursor nach unten</span><span class="sxs-lookup"><span data-stu-id="51d00-175">Cursor Down</span></span>                         | <span data-ttu-id="51d00-176">Cursor nach unten um &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="51d00-176">Cursor down by &lt;n&gt;</span></span>                                                                                                   |
| <span data-ttu-id="51d00-177">ESC \[ &lt; n &gt; C</span><span class="sxs-lookup"><span data-stu-id="51d00-177">ESC \[ &lt;n&gt; C</span></span>             | <span data-ttu-id="51d00-178">CUF</span><span class="sxs-lookup"><span data-stu-id="51d00-178">CUF</span></span>       | <span data-ttu-id="51d00-179">Cursor vorwärts</span><span class="sxs-lookup"><span data-stu-id="51d00-179">Cursor Forward</span></span>                      | <span data-ttu-id="51d00-180">Cursor vorwärts (rechts) durch &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="51d00-180">Cursor forward (Right) by &lt;n&gt;</span></span>                                                                                        |
| <span data-ttu-id="51d00-181">ESC \[ &lt; n &gt; D</span><span class="sxs-lookup"><span data-stu-id="51d00-181">ESC \[ &lt;n&gt; D</span></span>             | <span data-ttu-id="51d00-182">Cub</span><span class="sxs-lookup"><span data-stu-id="51d00-182">CUB</span></span>       | <span data-ttu-id="51d00-183">Cursor rückwärts</span><span class="sxs-lookup"><span data-stu-id="51d00-183">Cursor Backward</span></span>                     | <span data-ttu-id="51d00-184">Cursor rückwärts (links) durch &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="51d00-184">Cursor backward (Left) by &lt;n&gt;</span></span>                                                                                        |
| <span data-ttu-id="51d00-185">ESC \[ &lt; n &gt; E</span><span class="sxs-lookup"><span data-stu-id="51d00-185">ESC \[ &lt;n&gt; E</span></span>             | <span data-ttu-id="51d00-186">CNL</span><span class="sxs-lookup"><span data-stu-id="51d00-186">CNL</span></span>       | <span data-ttu-id="51d00-187">Cursor-nächste Zeile</span><span class="sxs-lookup"><span data-stu-id="51d00-187">Cursor Next Line</span></span>                    | <span data-ttu-id="51d00-188">Cursor bis zum Anfang der &lt; n-ten &gt; Zeile im Viewport</span><span class="sxs-lookup"><span data-stu-id="51d00-188">Cursor down to beginning of &lt;n&gt;th line in the viewport</span></span>                                                               |
| <span data-ttu-id="51d00-189">ESC \[ &lt; n &gt; F</span><span class="sxs-lookup"><span data-stu-id="51d00-189">ESC \[ &lt;n&gt; F</span></span>             | <span data-ttu-id="51d00-190">CPL</span><span class="sxs-lookup"><span data-stu-id="51d00-190">CPL</span></span>       | <span data-ttu-id="51d00-191">Vorherige Cursor Zeile</span><span class="sxs-lookup"><span data-stu-id="51d00-191">Cursor Previous Line</span></span>                | <span data-ttu-id="51d00-192">Cursor bis zum Anfang der &lt; n-ten &gt; Zeile im Viewport</span><span class="sxs-lookup"><span data-stu-id="51d00-192">Cursor up to beginning of &lt;n&gt;th line in the viewport</span></span>                                                                 |
| <span data-ttu-id="51d00-193">ESC \[ &lt; n &gt; G</span><span class="sxs-lookup"><span data-stu-id="51d00-193">ESC \[ &lt;n&gt; G</span></span>             | <span data-ttu-id="51d00-194">CHA</span><span class="sxs-lookup"><span data-stu-id="51d00-194">CHA</span></span>       | <span data-ttu-id="51d00-195">Cursor horizontal absolut</span><span class="sxs-lookup"><span data-stu-id="51d00-195">Cursor Horizontal Absolute</span></span>          | <span data-ttu-id="51d00-196">Der Cursor wechselt an &lt; die n-te &gt; Position horizontal in der aktuellen Zeile.</span><span class="sxs-lookup"><span data-stu-id="51d00-196">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span>                                                      |
| <span data-ttu-id="51d00-197">ESC \[ &lt; n &gt; d</span><span class="sxs-lookup"><span data-stu-id="51d00-197">ESC \[ &lt;n&gt; d</span></span>             | <span data-ttu-id="51d00-198">VPA</span><span class="sxs-lookup"><span data-stu-id="51d00-198">VPA</span></span>       | <span data-ttu-id="51d00-199">Vertikale Zeilen Position absolut</span><span class="sxs-lookup"><span data-stu-id="51d00-199">Vertical Line Position Absolute</span></span>     | <span data-ttu-id="51d00-200">Der Cursor wechselt an die n-te &lt; &gt; Position vertikal in der aktuellen Spalte.</span><span class="sxs-lookup"><span data-stu-id="51d00-200">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span>                                                  |
| <span data-ttu-id="51d00-201">ESC \[ &lt; y &gt; ; &lt; x &gt; H</span><span class="sxs-lookup"><span data-stu-id="51d00-201">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="51d00-202">Pokalsieg</span><span class="sxs-lookup"><span data-stu-id="51d00-202">CUP</span></span>       | <span data-ttu-id="51d00-203">Cursor Position</span><span class="sxs-lookup"><span data-stu-id="51d00-203">Cursor Position</span></span>                     | <span data-ttu-id="51d00-204">\*Cursor wechselt zu &lt; x &gt; ; &lt; y- &gt; Koordinate innerhalb des Viewports, wobei &lt; x für &gt; die Spalte der &lt; y- &gt; Zeile steht.</span><span class="sxs-lookup"><span data-stu-id="51d00-204">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="51d00-205">ESC \[ &lt; y &gt; ; &lt; × &gt; f</span><span class="sxs-lookup"><span data-stu-id="51d00-205">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="51d00-206">HVP</span><span class="sxs-lookup"><span data-stu-id="51d00-206">HVP</span></span>       | <span data-ttu-id="51d00-207">Horizontale vertikale Position</span><span class="sxs-lookup"><span data-stu-id="51d00-207">Horizontal Vertical Position</span></span>        | <span data-ttu-id="51d00-208">\*Cursor wechselt zu &lt; x &gt; ; &lt; y- &gt; Koordinate innerhalb des Viewports, wobei &lt; x für &gt; die Spalte der &lt; y- &gt; Zeile steht.</span><span class="sxs-lookup"><span data-stu-id="51d00-208">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="51d00-209">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="51d00-209">ESC \[ s</span></span>                       | <span data-ttu-id="51d00-210">Ansisyssc</span><span class="sxs-lookup"><span data-stu-id="51d00-210">ANSISYSSC</span></span> | <span data-ttu-id="51d00-211">Cursor – Ansi.sys Emulation speichern</span><span class="sxs-lookup"><span data-stu-id="51d00-211">Save Cursor – Ansi.sys emulation</span></span>    | <span data-ttu-id="51d00-212">\*\*Ohne Parameter führt einen Vorgang zum Speichern eines Cursors aus, z. b. decsc.</span><span class="sxs-lookup"><span data-stu-id="51d00-212">\*\*With no parameters, performs a save cursor operation like DECSC</span></span>                                                        |
| <span data-ttu-id="51d00-213">ESC \[ u</span><span class="sxs-lookup"><span data-stu-id="51d00-213">ESC \[ u</span></span>                       | <span data-ttu-id="51d00-214">Ansisyssc</span><span class="sxs-lookup"><span data-stu-id="51d00-214">ANSISYSSC</span></span> | <span data-ttu-id="51d00-215">Restore Cursor – Ansi.sys Emulation</span><span class="sxs-lookup"><span data-stu-id="51d00-215">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="51d00-216">\*\*Ohne Parameter führt einen Restore-Cursor Vorgang wie decrc aus.</span><span class="sxs-lookup"><span data-stu-id="51d00-216">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span>                                                     |



<span data-ttu-id="51d00-217">**Hinweis**</span><span class="sxs-lookup"><span data-stu-id="51d00-217">**Note**</span></span>  
<span data-ttu-id="51d00-218">\*&lt;x &gt; -und &lt; y- &gt; Parameter haben dieselben Einschränkungen wie &lt; n &gt; oben.</span><span class="sxs-lookup"><span data-stu-id="51d00-218">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="51d00-219">Wenn &lt; x &gt; und &lt; y &gt; ausgelassen werden, werden Sie auf 1 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="51d00-219">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>

<span data-ttu-id="51d00-220">\*\*ANSI.sys Verlaufs Dokumentation finden Sie unter <https://msdn.microsoft.com/library/cc722862.aspx> und wird aus Gründen der Handhabung und Kompatibilität implementiert.</span><span class="sxs-lookup"><span data-stu-id="51d00-220">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="51d00-221"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Sichtbarkeit</span><span class="sxs-lookup"><span data-stu-id="51d00-221"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="51d00-222">Die folgenden Befehle steuern die Sichtbarkeit des Cursors und den blinkende Zustand.</span><span class="sxs-lookup"><span data-stu-id="51d00-222">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="51d00-223">Die dectcem-Sequenzen entsprechen in der Regel der aufrufenden [**setconsolecursorinfo**](setconsolecursorinfo.md) -Konsolen-API zum Umschalten der Cursor Sichtbarkeit.</span><span class="sxs-lookup"><span data-stu-id="51d00-223">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="51d00-224">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-224">Sequence</span></span>      | <span data-ttu-id="51d00-225">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-225">Code</span></span>    | <span data-ttu-id="51d00-226">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-226">Description</span></span>                  | <span data-ttu-id="51d00-227">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-227">Behavior</span></span>                  |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="51d00-228">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="51d00-228">ESC \[ ?</span></span> <span data-ttu-id="51d00-229">12 Stunden</span><span class="sxs-lookup"><span data-stu-id="51d00-229">12 h</span></span> | <span data-ttu-id="51d00-230">ATT160</span><span class="sxs-lookup"><span data-stu-id="51d00-230">ATT160</span></span>  | <span data-ttu-id="51d00-231">Text Cursor Aktivierung blinkt</span><span class="sxs-lookup"><span data-stu-id="51d00-231">Text Cursor Enable Blinking</span></span>  | <span data-ttu-id="51d00-232">Cursor blinkt</span><span class="sxs-lookup"><span data-stu-id="51d00-232">Start the cursor blinking</span></span> |
| <span data-ttu-id="51d00-233">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="51d00-233">ESC \[ ?</span></span> <span data-ttu-id="51d00-234">12 l</span><span class="sxs-lookup"><span data-stu-id="51d00-234">12 l</span></span> | <span data-ttu-id="51d00-235">ATT160</span><span class="sxs-lookup"><span data-stu-id="51d00-235">ATT160</span></span>  | <span data-ttu-id="51d00-236">Blinken des Text Cursors deaktivieren</span><span class="sxs-lookup"><span data-stu-id="51d00-236">Text Cursor Disable Blinking</span></span>  | <span data-ttu-id="51d00-237">Blinkt den Cursor nicht mehr</span><span class="sxs-lookup"><span data-stu-id="51d00-237">Stop blinking the cursor</span></span>  |
| <span data-ttu-id="51d00-238">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="51d00-238">ESC \[ ?</span></span> <span data-ttu-id="51d00-239">25 h</span><span class="sxs-lookup"><span data-stu-id="51d00-239">25 h</span></span> | <span data-ttu-id="51d00-240">Dectcem</span><span class="sxs-lookup"><span data-stu-id="51d00-240">DECTCEM</span></span> | <span data-ttu-id="51d00-241">Text Cursor Aktivierungs Modus anzeigen</span><span class="sxs-lookup"><span data-stu-id="51d00-241">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="51d00-242">Cursor anzeigen</span><span class="sxs-lookup"><span data-stu-id="51d00-242">Show the cursor</span></span>           |
| <span data-ttu-id="51d00-243">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="51d00-243">ESC \[ ?</span></span> <span data-ttu-id="51d00-244">25 l</span><span class="sxs-lookup"><span data-stu-id="51d00-244">25 l</span></span> | <span data-ttu-id="51d00-245">Dectcem</span><span class="sxs-lookup"><span data-stu-id="51d00-245">DECTCEM</span></span> | <span data-ttu-id="51d00-246">Modus "Text Cursor aktivieren" ausblenden</span><span class="sxs-lookup"><span data-stu-id="51d00-246">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="51d00-247">Cursor ausblenden</span><span class="sxs-lookup"><span data-stu-id="51d00-247">Hide the cursor</span></span>           |



## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="51d00-248"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Positionieren von Viewports</span><span class="sxs-lookup"><span data-stu-id="51d00-248"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="51d00-249">Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufrufen der [**scrollconsolescreenbuffer**](scrollconsolescreenbuffer.md) -Konsolen-API, um den Inhalt des Konsolen Puffers zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="51d00-249">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="51d00-250">**Vorsicht**  Die Befehlsnamen sind irreführend.</span><span class="sxs-lookup"><span data-stu-id="51d00-250">**Caution**  The command names are misleading.</span></span> <span data-ttu-id="51d00-251">Scroll bezieht sich auf die Richtung, in die der Text während des Vorgangs verschoben wird, nicht auf die Art und Weise, in der der Viewport verschoben werden würde</span><span class="sxs-lookup"><span data-stu-id="51d00-251">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="51d00-252">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-252">Sequence</span></span>           | <span data-ttu-id="51d00-253">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-253">Code</span></span> | <span data-ttu-id="51d00-254">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-254">Description</span></span> | <span data-ttu-id="51d00-255">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-255">Behavior</span></span>                                                                                             |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="51d00-256">ESC \[ &lt; n &gt; S</span><span class="sxs-lookup"><span data-stu-id="51d00-256">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="51d00-257">SU</span><span class="sxs-lookup"><span data-stu-id="51d00-257">SU</span></span>   | <span data-ttu-id="51d00-258">Bildlauf nach oben</span><span class="sxs-lookup"><span data-stu-id="51d00-258">Scroll Up</span></span>   | <span data-ttu-id="51d00-259">Bildlauf nach oben um &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="51d00-259">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="51d00-260">Auch als "Pan Down" bezeichnet, werden neue Zeilen unten auf dem Bildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="51d00-260">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="51d00-261">ESC \[ &lt; n &gt; T</span><span class="sxs-lookup"><span data-stu-id="51d00-261">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="51d00-262">SD</span><span class="sxs-lookup"><span data-stu-id="51d00-262">SD</span></span>   | <span data-ttu-id="51d00-263">Bildlauf nach unten</span><span class="sxs-lookup"><span data-stu-id="51d00-263">Scroll Down</span></span> | <span data-ttu-id="51d00-264">Scrollen Sie nach unten um &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="51d00-264">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="51d00-265">Auch als "schwenken" bezeichnet, werden neue Zeilen am oberen Rand des Bildschirms angezeigt.</span><span class="sxs-lookup"><span data-stu-id="51d00-265">Also known as pan up, new lines fill in from the top of the screen</span></span>         |



<span data-ttu-id="51d00-266">Der Text wird beginnend mit der Zeile verschoben, in der sich der Cursor befindet.</span><span class="sxs-lookup"><span data-stu-id="51d00-266">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="51d00-267">Wenn sich der Cursor in der mittleren Zeile des Viewports befindet, verschiebt der Bildlauf nach oben die untere Hälfte des Viewports und fügt unten leere Zeilen ein.</span><span class="sxs-lookup"><span data-stu-id="51d00-267">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="51d00-268">Scrollen Sie nach unten, um die obere Hälfte der Zeilen des Viewports zu verschieben, und fügen Sie oben neue Zeilen ein.</span><span class="sxs-lookup"><span data-stu-id="51d00-268">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="51d00-269">Wichtig zu beachten ist, dass der Bildlauf nach oben und unten auch durch die scrollränder beeinträchtigt wird.</span><span class="sxs-lookup"><span data-stu-id="51d00-269">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="51d00-270">Ein Bildlauf nach oben und unten wirkt sich nicht auf Zeilen außerhalb der scrollränder aus.</span><span class="sxs-lookup"><span data-stu-id="51d00-270">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="51d00-271">Der Standardwert für &lt; n &gt; ist 1, und der Wert kann optional ausgelassen werden.</span><span class="sxs-lookup"><span data-stu-id="51d00-271">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="51d00-272"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Änderung</span><span class="sxs-lookup"><span data-stu-id="51d00-272"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="51d00-273">Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufruf von [**fillconsoleoutputcharacter**](fillconsoleoutputcharacter.md)-, [**fillconsoleoutputattribute**](fillconsoleoutputattribute.md)-und [**scrollconsolescreenbuffer**](scrollconsolescreenbuffer.md) -Konsolen-APIs, um den Inhalt des Text Puffers zu ändern.</span><span class="sxs-lookup"><span data-stu-id="51d00-273">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="51d00-274">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-274">Sequence</span></span>           | <span data-ttu-id="51d00-275">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-275">Code</span></span> | <span data-ttu-id="51d00-276">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-276">Description</span></span>      | <span data-ttu-id="51d00-277">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-277">Behavior</span></span>                                                                                                                                          |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="51d00-278">ESC \[ &lt; n&gt; @</span><span class="sxs-lookup"><span data-stu-id="51d00-278">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="51d00-279">Reichen</span><span class="sxs-lookup"><span data-stu-id="51d00-279">ICH</span></span>  | <span data-ttu-id="51d00-280">Zeichen einfügen</span><span class="sxs-lookup"><span data-stu-id="51d00-280">Insert Character</span></span> | <span data-ttu-id="51d00-281">Fügen &lt; &gt; Sie n Leerzeichen an der aktuellen Cursorposition ein, und verschieben Sie den gesamten vorhandenen Text nach rechts.</span><span class="sxs-lookup"><span data-stu-id="51d00-281">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="51d00-282">Der Text, der den Bildschirm rechts verlässt, wird entfernt.</span><span class="sxs-lookup"><span data-stu-id="51d00-282">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="51d00-283">ESC \[ &lt; n &gt; P</span><span class="sxs-lookup"><span data-stu-id="51d00-283">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="51d00-284">DCH</span><span class="sxs-lookup"><span data-stu-id="51d00-284">DCH</span></span>  | <span data-ttu-id="51d00-285">Zeichen löschen</span><span class="sxs-lookup"><span data-stu-id="51d00-285">Delete Character</span></span> | <span data-ttu-id="51d00-286">Löschen Sie &lt; n &gt; Zeichen an der aktuellen Cursorposition, und verschieben Sie die Leerzeichen vom rechten Rand des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="51d00-286">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span>                       |
| <span data-ttu-id="51d00-287">ESC \[ &lt; n &gt; X</span><span class="sxs-lookup"><span data-stu-id="51d00-287">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="51d00-288">E</span><span class="sxs-lookup"><span data-stu-id="51d00-288">ECH</span></span>  | <span data-ttu-id="51d00-289">Löschzeichen</span><span class="sxs-lookup"><span data-stu-id="51d00-289">Erase Character</span></span>  | <span data-ttu-id="51d00-290">Löschen &lt; &gt; Sie n Zeichen aus der aktuellen Cursorposition, indem Sie Sie mit einem Leerzeichen überschreiben.</span><span class="sxs-lookup"><span data-stu-id="51d00-290">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span>                                           |
| <span data-ttu-id="51d00-291">ESC \[ &lt; n &gt; L</span><span class="sxs-lookup"><span data-stu-id="51d00-291">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="51d00-292">BY</span><span class="sxs-lookup"><span data-stu-id="51d00-292">IL</span></span>   | <span data-ttu-id="51d00-293">Zeile einfügen</span><span class="sxs-lookup"><span data-stu-id="51d00-293">Insert Line</span></span>      | <span data-ttu-id="51d00-294">Fügt &lt; n &gt; Zeilen an der Cursorposition in den Puffer ein.</span><span class="sxs-lookup"><span data-stu-id="51d00-294">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="51d00-295">Die Zeile, in der sich der Cursor befindet, und die darunter liegenden Zeilen werden nach unten verschoben.</span><span class="sxs-lookup"><span data-stu-id="51d00-295">The line the cursor is on, and lines below it, will be shifted downwards.</span></span>         |
| <span data-ttu-id="51d00-296">ESC \[ &lt; n &gt; M</span><span class="sxs-lookup"><span data-stu-id="51d00-296">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="51d00-297">DL</span><span class="sxs-lookup"><span data-stu-id="51d00-297">DL</span></span>   | <span data-ttu-id="51d00-298">Zeile löschen</span><span class="sxs-lookup"><span data-stu-id="51d00-298">Delete Line</span></span>      | <span data-ttu-id="51d00-299">Löscht &lt; n &gt; Zeilen aus dem Puffer, beginnend mit der Zeile, in der sich der Cursor befindet.</span><span class="sxs-lookup"><span data-stu-id="51d00-299">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span>                                                                  |



<span data-ttu-id="51d00-300">**Hinweis**</span><span class="sxs-lookup"><span data-stu-id="51d00-300">**Note**</span></span>  
<span data-ttu-id="51d00-301">Für Il und DL sind nur die Zeilen in den scrollrändern betroffen (siehe scrollränder).</span><span class="sxs-lookup"><span data-stu-id="51d00-301">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="51d00-302">Wenn keine Ränder festgelegt sind, sind die Standardrand Ränder der aktuelle Viewport.</span><span class="sxs-lookup"><span data-stu-id="51d00-302">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="51d00-303">Wenn Linien unter die Ränder verschoben werden, werden Sie verworfen.</span><span class="sxs-lookup"><span data-stu-id="51d00-303">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="51d00-304">Wenn Zeilen gelöscht werden, werden am unteren Rand der Ränder leere Zeilen eingefügt, ohne dass Zeilen von außerhalb des Viewports betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="51d00-304">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="51d00-305">Der Standardwert für n, wenn der Wert &lt; &gt; weggelassen wird, ist 0 (null).</span><span class="sxs-lookup"><span data-stu-id="51d00-305">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="51d00-306">Für die folgenden Befehle weist der Parameter &lt; n &gt; drei gültige Werte auf:</span><span class="sxs-lookup"><span data-stu-id="51d00-306">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="51d00-307">0 löscht von der aktuellen Cursorposition (einschließlich) bis zum Ende der Zeile/Anzeige.</span><span class="sxs-lookup"><span data-stu-id="51d00-307">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="51d00-308">1 löscht am Anfang der Zeile/Anzeige bis einschließlich der aktuellen Cursorposition.</span><span class="sxs-lookup"><span data-stu-id="51d00-308">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="51d00-309">2 löscht die gesamte Zeile/Anzeige.</span><span class="sxs-lookup"><span data-stu-id="51d00-309">2 erases the entire line/display</span></span>


| <span data-ttu-id="51d00-310">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-310">Sequence</span></span>           | <span data-ttu-id="51d00-311">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-311">Code</span></span> | <span data-ttu-id="51d00-312">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-312">Description</span></span>      | <span data-ttu-id="51d00-313">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-313">Behavior</span></span>                                                                                     |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="51d00-314">ESC \[ &lt; n &gt; J</span><span class="sxs-lookup"><span data-stu-id="51d00-314">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="51d00-315">ED</span><span class="sxs-lookup"><span data-stu-id="51d00-315">ED</span></span>   | <span data-ttu-id="51d00-316">In Anzeige löschen</span><span class="sxs-lookup"><span data-stu-id="51d00-316">Erase in Display</span></span> | <span data-ttu-id="51d00-317">Ersetzt den gesamten Text im aktuellen Viewport/Bildschirm, der durch n angegeben ist, &lt; &gt; durch Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="51d00-317">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="51d00-318">ESC \[ &lt; n &gt; K</span><span class="sxs-lookup"><span data-stu-id="51d00-318">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="51d00-319">Tanken</span><span class="sxs-lookup"><span data-stu-id="51d00-319">EL</span></span>   | <span data-ttu-id="51d00-320">In Zeile löschen</span><span class="sxs-lookup"><span data-stu-id="51d00-320">Erase in Line</span></span>    | <span data-ttu-id="51d00-321">Ersetzt den gesamten Text in der Zeile durch den durch n angegebenen Cursor &lt; &gt; mit Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="51d00-321">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span>    |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="51d00-322"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatierung</span><span class="sxs-lookup"><span data-stu-id="51d00-322"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="51d00-323">Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufrufen von [**SetConsoleTextAttribute**](setconsoletextattribute.md) -Konsolen-APIs, um die Formatierung aller zukünftigen Schreibvorgänge in den Konsolenausgabe Text Puffer anzupassen.</span><span class="sxs-lookup"><span data-stu-id="51d00-323">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="51d00-324">Dieser Befehl ist ein besonderes Zeichen, da die &lt; n &gt; -Position unten zwischen 0 und 16 durch Semikolons getrennte Parameter annehmen kann.</span><span class="sxs-lookup"><span data-stu-id="51d00-324">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="51d00-325">Wenn keine Parameter angegeben werden, wird diese wie ein einzelner 0-Parameter behandelt.</span><span class="sxs-lookup"><span data-stu-id="51d00-325">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="51d00-326">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-326">Sequence</span></span>           | <span data-ttu-id="51d00-327">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-327">Code</span></span> | <span data-ttu-id="51d00-328">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-328">Description</span></span>            | <span data-ttu-id="51d00-329">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-329">Behavior</span></span>                                                        |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="51d00-330">ESC \[ &lt; n &gt; m</span><span class="sxs-lookup"><span data-stu-id="51d00-330">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="51d00-331">SGR</span><span class="sxs-lookup"><span data-stu-id="51d00-331">SGR</span></span>  | <span data-ttu-id="51d00-332">Grafikwiedergabe festlegen</span><span class="sxs-lookup"><span data-stu-id="51d00-332">Set Graphics Rendition</span></span> | <span data-ttu-id="51d00-333">Legen Sie das Format des Bildschirms und des Texts gemäß Angabe durch n fest. &lt;&gt;</span><span class="sxs-lookup"><span data-stu-id="51d00-333">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="51d00-334">Die folgende Tabelle mit Werten kann in &lt; n &gt; zur Darstellung unterschiedlicher Formatierungs Modi verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="51d00-334">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="51d00-335">Formatierungs Modi werden von links nach rechts angewendet.</span><span class="sxs-lookup"><span data-stu-id="51d00-335">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="51d00-336">Wenn Sie konkurrierende Formatierungsoptionen anwenden, führt dies dazu, dass die Rechte Option Vorrang hat.</span><span class="sxs-lookup"><span data-stu-id="51d00-336">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="51d00-337">Für Optionen, die Farben angeben, werden die Farben entsprechend der Definition in der Konsolen Farbtabelle verwendet, die mit der [**setconsoleskreenbufferinfoex**](setconsolescreenbufferinfoex.md) -API geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="51d00-337">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="51d00-338">Wenn die Tabelle so geändert wird, dass die "Blaue" Position in der Tabelle den RGB-Farbton rot anzeigt, werden alle Aufrufe an **Vordergrund blau** die rote Farbe anzeigen, bis Sie anderweitig geändert werden.</span><span class="sxs-lookup"><span data-stu-id="51d00-338">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="51d00-339">Wert</span><span class="sxs-lookup"><span data-stu-id="51d00-339">Value</span></span> | <span data-ttu-id="51d00-340">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-340">Description</span></span>               | <span data-ttu-id="51d00-341">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-341">Behavior</span></span>                                                           |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="51d00-342">0</span><span class="sxs-lookup"><span data-stu-id="51d00-342">0</span></span>     | <span data-ttu-id="51d00-343">Standard</span><span class="sxs-lookup"><span data-stu-id="51d00-343">Default</span></span>                   | <span data-ttu-id="51d00-344">Gibt vor der Änderung alle Attribute in den Standardzustand zurück.</span><span class="sxs-lookup"><span data-stu-id="51d00-344">Returns all attributes to the default state prior to modification</span></span>  |
| <span data-ttu-id="51d00-345">1</span><span class="sxs-lookup"><span data-stu-id="51d00-345">1</span></span>     | <span data-ttu-id="51d00-346">Fett/hell</span><span class="sxs-lookup"><span data-stu-id="51d00-346">Bold/Bright</span></span>               | <span data-ttu-id="51d00-347">Wendet das Flag für Helligkeit/Intensität auf Vordergrundfarbe an</span><span class="sxs-lookup"><span data-stu-id="51d00-347">Applies brightness/intensity flag to foreground color</span></span>              |
| <span data-ttu-id="51d00-348">4</span><span class="sxs-lookup"><span data-stu-id="51d00-348">4</span></span>     | <span data-ttu-id="51d00-349">Underline</span><span class="sxs-lookup"><span data-stu-id="51d00-349">Underline</span></span>                 | <span data-ttu-id="51d00-350">Fügt Unterstreichung hinzu</span><span class="sxs-lookup"><span data-stu-id="51d00-350">Adds underline</span></span>                                                     |
| <span data-ttu-id="51d00-351">24</span><span class="sxs-lookup"><span data-stu-id="51d00-351">24</span></span>    | <span data-ttu-id="51d00-352">Keine Unterstreichung</span><span class="sxs-lookup"><span data-stu-id="51d00-352">No underline</span></span>              | <span data-ttu-id="51d00-353">Entfernt Unterstreichung</span><span class="sxs-lookup"><span data-stu-id="51d00-353">Removes underline</span></span>                                                  |
| <span data-ttu-id="51d00-354">7</span><span class="sxs-lookup"><span data-stu-id="51d00-354">7</span></span>     | <span data-ttu-id="51d00-355">Negativ</span><span class="sxs-lookup"><span data-stu-id="51d00-355">Negative</span></span>                  | <span data-ttu-id="51d00-356">Vertauscht Vordergrund-und Hintergrundfarben</span><span class="sxs-lookup"><span data-stu-id="51d00-356">Swaps foreground and background colors</span></span>                             |
| <span data-ttu-id="51d00-357">27</span><span class="sxs-lookup"><span data-stu-id="51d00-357">27</span></span>    | <span data-ttu-id="51d00-358">Positiv (keine negative)</span><span class="sxs-lookup"><span data-stu-id="51d00-358">Positive (No negative)</span></span>    | <span data-ttu-id="51d00-359">Gibt Vordergrund/Hintergrund für normal zurück</span><span class="sxs-lookup"><span data-stu-id="51d00-359">Returns foreground/background to normal</span></span>                            |
| <span data-ttu-id="51d00-360">30</span><span class="sxs-lookup"><span data-stu-id="51d00-360">30</span></span>    | <span data-ttu-id="51d00-361">Vordergrund schwarz</span><span class="sxs-lookup"><span data-stu-id="51d00-361">Foreground Black</span></span>          | <span data-ttu-id="51d00-362">Gilt für den Vordergrund ohne Fett/Hellschwarz.</span><span class="sxs-lookup"><span data-stu-id="51d00-362">Applies non-bold/bright black to foreground</span></span>                        |
| <span data-ttu-id="51d00-363">31</span><span class="sxs-lookup"><span data-stu-id="51d00-363">31</span></span>    | <span data-ttu-id="51d00-364">Vordergrund rot</span><span class="sxs-lookup"><span data-stu-id="51d00-364">Foreground Red</span></span>            | <span data-ttu-id="51d00-365">Gilt für den Vordergrund ohne Fett/hellrot.</span><span class="sxs-lookup"><span data-stu-id="51d00-365">Applies non-bold/bright red to foreground</span></span>                          |
| <span data-ttu-id="51d00-366">32</span><span class="sxs-lookup"><span data-stu-id="51d00-366">32</span></span>    | <span data-ttu-id="51d00-367">Vordergrund grün</span><span class="sxs-lookup"><span data-stu-id="51d00-367">Foreground Green</span></span>          | <span data-ttu-id="51d00-368">Gilt für den Vordergrund ohne Fett/hellgrün.</span><span class="sxs-lookup"><span data-stu-id="51d00-368">Applies non-bold/bright green to foreground</span></span>                        |
| <span data-ttu-id="51d00-369">33</span><span class="sxs-lookup"><span data-stu-id="51d00-369">33</span></span>    | <span data-ttu-id="51d00-370">Vordergrund gelb</span><span class="sxs-lookup"><span data-stu-id="51d00-370">Foreground Yellow</span></span>         | <span data-ttu-id="51d00-371">Gilt für den Vordergrund ohne Fett/hellgelb.</span><span class="sxs-lookup"><span data-stu-id="51d00-371">Applies non-bold/bright yellow to foreground</span></span>                       |
| <span data-ttu-id="51d00-372">34</span><span class="sxs-lookup"><span data-stu-id="51d00-372">34</span></span>    | <span data-ttu-id="51d00-373">Vordergrund blau</span><span class="sxs-lookup"><span data-stu-id="51d00-373">Foreground Blue</span></span>           | <span data-ttu-id="51d00-374">Gilt für den Vordergrund ohne Fett/hellblau.</span><span class="sxs-lookup"><span data-stu-id="51d00-374">Applies non-bold/bright blue to foreground</span></span>                         |
| <span data-ttu-id="51d00-375">35</span><span class="sxs-lookup"><span data-stu-id="51d00-375">35</span></span>    | <span data-ttu-id="51d00-376">Vordergrund Magenta</span><span class="sxs-lookup"><span data-stu-id="51d00-376">Foreground Magenta</span></span>        | <span data-ttu-id="51d00-377">Wendet nicht Fett/hellgrün auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-377">Applies non-bold/bright magenta to foreground</span></span>                      |
| <span data-ttu-id="51d00-378">36</span><span class="sxs-lookup"><span data-stu-id="51d00-378">36</span></span>    | <span data-ttu-id="51d00-379">Vordergrund-Cyan</span><span class="sxs-lookup"><span data-stu-id="51d00-379">Foreground Cyan</span></span>           | <span data-ttu-id="51d00-380">Wendet nicht Fett/hell Zyan auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-380">Applies non-bold/bright cyan to foreground</span></span>                         |
| <span data-ttu-id="51d00-381">37</span><span class="sxs-lookup"><span data-stu-id="51d00-381">37</span></span>    | <span data-ttu-id="51d00-382">Vordergrund weiß</span><span class="sxs-lookup"><span data-stu-id="51d00-382">Foreground White</span></span>          | <span data-ttu-id="51d00-383">Wendet nicht Fett/hell weiß auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-383">Applies non-bold/bright white to foreground</span></span>                        |
| <span data-ttu-id="51d00-384">38</span><span class="sxs-lookup"><span data-stu-id="51d00-384">38</span></span>    | <span data-ttu-id="51d00-385">Vordergrund erweitert</span><span class="sxs-lookup"><span data-stu-id="51d00-385">Foreground Extended</span></span>       | <span data-ttu-id="51d00-386">Wendet den erweiterten Farbwert auf den Vordergrund an (Weitere Informationen finden Sie unten).</span><span class="sxs-lookup"><span data-stu-id="51d00-386">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="51d00-387">39</span><span class="sxs-lookup"><span data-stu-id="51d00-387">39</span></span>    | <span data-ttu-id="51d00-388">Vordergrund Standard</span><span class="sxs-lookup"><span data-stu-id="51d00-388">Foreground Default</span></span>        | <span data-ttu-id="51d00-389">Wendet nur den Vordergrund-Teil der Standardwerte an (siehe 0).</span><span class="sxs-lookup"><span data-stu-id="51d00-389">Applies only the foreground portion of the defaults (see 0)</span></span>        |
| <span data-ttu-id="51d00-390">40</span><span class="sxs-lookup"><span data-stu-id="51d00-390">40</span></span>    | <span data-ttu-id="51d00-391">Hintergrund schwarz</span><span class="sxs-lookup"><span data-stu-id="51d00-391">Background Black</span></span>          | <span data-ttu-id="51d00-392">Gilt für den Hintergrund "nicht Fett/Hellschwarz".</span><span class="sxs-lookup"><span data-stu-id="51d00-392">Applies non-bold/bright black to background</span></span>                        |
| <span data-ttu-id="51d00-393">41</span><span class="sxs-lookup"><span data-stu-id="51d00-393">41</span></span>    | <span data-ttu-id="51d00-394">Roter Hintergrund</span><span class="sxs-lookup"><span data-stu-id="51d00-394">Background Red</span></span>            | <span data-ttu-id="51d00-395">Gilt für den Hintergrund "nicht Fett/hell"</span><span class="sxs-lookup"><span data-stu-id="51d00-395">Applies non-bold/bright red to background</span></span>                          |
| <span data-ttu-id="51d00-396">42</span><span class="sxs-lookup"><span data-stu-id="51d00-396">42</span></span>    | <span data-ttu-id="51d00-397">Hintergrund grün</span><span class="sxs-lookup"><span data-stu-id="51d00-397">Background Green</span></span>          | <span data-ttu-id="51d00-398">Gilt für den Hintergrund "nicht Fett/hellgrün"</span><span class="sxs-lookup"><span data-stu-id="51d00-398">Applies non-bold/bright green to background</span></span>                        |
| <span data-ttu-id="51d00-399">43</span><span class="sxs-lookup"><span data-stu-id="51d00-399">43</span></span>    | <span data-ttu-id="51d00-400">Hintergrund Gelb</span><span class="sxs-lookup"><span data-stu-id="51d00-400">Background Yellow</span></span>         | <span data-ttu-id="51d00-401">Gilt für den Hintergrund "nicht Fett/hell gelb"</span><span class="sxs-lookup"><span data-stu-id="51d00-401">Applies non-bold/bright yellow to background</span></span>                       |
| <span data-ttu-id="51d00-402">44</span><span class="sxs-lookup"><span data-stu-id="51d00-402">44</span></span>    | <span data-ttu-id="51d00-403">Hintergrund blau</span><span class="sxs-lookup"><span data-stu-id="51d00-403">Background Blue</span></span>           | <span data-ttu-id="51d00-404">Gilt für den Hintergrund "nicht Fett/hellblau".</span><span class="sxs-lookup"><span data-stu-id="51d00-404">Applies non-bold/bright blue to background</span></span>                         |
| <span data-ttu-id="51d00-405">45</span><span class="sxs-lookup"><span data-stu-id="51d00-405">45</span></span>    | <span data-ttu-id="51d00-406">Hintergrund Magenta</span><span class="sxs-lookup"><span data-stu-id="51d00-406">Background Magenta</span></span>        | <span data-ttu-id="51d00-407">Wendet nicht Fett/hell auf den Hintergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-407">Applies non-bold/bright magenta to background</span></span>                      |
| <span data-ttu-id="51d00-408">46</span><span class="sxs-lookup"><span data-stu-id="51d00-408">46</span></span>    | <span data-ttu-id="51d00-409">Background Cyan</span><span class="sxs-lookup"><span data-stu-id="51d00-409">Background Cyan</span></span>           | <span data-ttu-id="51d00-410">Wendet nicht Fett/hell Zyan auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="51d00-410">Applies non-bold/bright cyan to background</span></span>                         |
| <span data-ttu-id="51d00-411">47</span><span class="sxs-lookup"><span data-stu-id="51d00-411">47</span></span>    | <span data-ttu-id="51d00-412">Hintergrund weiß</span><span class="sxs-lookup"><span data-stu-id="51d00-412">Background White</span></span>          | <span data-ttu-id="51d00-413">Gilt für den Hintergrund "nicht Fett/hell weiß".</span><span class="sxs-lookup"><span data-stu-id="51d00-413">Applies non-bold/bright white to background</span></span>                        |
| <span data-ttu-id="51d00-414">48</span><span class="sxs-lookup"><span data-stu-id="51d00-414">48</span></span>    | <span data-ttu-id="51d00-415">Erweiterter Hintergrund</span><span class="sxs-lookup"><span data-stu-id="51d00-415">Background Extended</span></span>       | <span data-ttu-id="51d00-416">Wendet den erweiterten Farbwert auf den Hintergrund an (Weitere Informationen finden Sie unten).</span><span class="sxs-lookup"><span data-stu-id="51d00-416">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="51d00-417">49</span><span class="sxs-lookup"><span data-stu-id="51d00-417">49</span></span>    | <span data-ttu-id="51d00-418">Standard Hintergrund</span><span class="sxs-lookup"><span data-stu-id="51d00-418">Background Default</span></span>        | <span data-ttu-id="51d00-419">Wendet nur den Hintergrund Teil der Standardwerte an (siehe 0).</span><span class="sxs-lookup"><span data-stu-id="51d00-419">Applies only the background portion of the defaults (see 0)</span></span>        |
| <span data-ttu-id="51d00-420">90</span><span class="sxs-lookup"><span data-stu-id="51d00-420">90</span></span>    | <span data-ttu-id="51d00-421">Heller Vordergrund schwarz</span><span class="sxs-lookup"><span data-stu-id="51d00-421">Bright Foreground Black</span></span>   | <span data-ttu-id="51d00-422">Wendet Fett/Hellschwarz auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-422">Applies bold/bright black to foreground</span></span>                            |
| <span data-ttu-id="51d00-423">91</span><span class="sxs-lookup"><span data-stu-id="51d00-423">91</span></span>    | <span data-ttu-id="51d00-424">Heller Vordergrund rot</span><span class="sxs-lookup"><span data-stu-id="51d00-424">Bright Foreground Red</span></span>     | <span data-ttu-id="51d00-425">Wendet Fett/hell rot auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-425">Applies bold/bright red to foreground</span></span>                              |
| <span data-ttu-id="51d00-426">92</span><span class="sxs-lookup"><span data-stu-id="51d00-426">92</span></span>    | <span data-ttu-id="51d00-427">Heller Vordergrund grün</span><span class="sxs-lookup"><span data-stu-id="51d00-427">Bright Foreground Green</span></span>   | <span data-ttu-id="51d00-428">Wendet Fett/hellgrün auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-428">Applies bold/bright green to foreground</span></span>                            |
| <span data-ttu-id="51d00-429">93</span><span class="sxs-lookup"><span data-stu-id="51d00-429">93</span></span>    | <span data-ttu-id="51d00-430">Heller Vordergrund gelb</span><span class="sxs-lookup"><span data-stu-id="51d00-430">Bright Foreground Yellow</span></span>  | <span data-ttu-id="51d00-431">Wendet Fett/hell gelb auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-431">Applies bold/bright yellow to foreground</span></span>                           |
| <span data-ttu-id="51d00-432">94</span><span class="sxs-lookup"><span data-stu-id="51d00-432">94</span></span>    | <span data-ttu-id="51d00-433">Heller Vordergrund blau</span><span class="sxs-lookup"><span data-stu-id="51d00-433">Bright Foreground Blue</span></span>    | <span data-ttu-id="51d00-434">Wendet Fett/hell blau auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-434">Applies bold/bright blue to foreground</span></span>                             |
| <span data-ttu-id="51d00-435">95</span><span class="sxs-lookup"><span data-stu-id="51d00-435">95</span></span>    | <span data-ttu-id="51d00-436">Heller Vordergrund Magenta</span><span class="sxs-lookup"><span data-stu-id="51d00-436">Bright Foreground Magenta</span></span> | <span data-ttu-id="51d00-437">Wendet Bold/hellmagenta auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-437">Applies bold/bright magenta to foreground</span></span>                          |
| <span data-ttu-id="51d00-438">96</span><span class="sxs-lookup"><span data-stu-id="51d00-438">96</span></span>    | <span data-ttu-id="51d00-439">Heller Vordergrund-Cyan</span><span class="sxs-lookup"><span data-stu-id="51d00-439">Bright Foreground Cyan</span></span>    | <span data-ttu-id="51d00-440">Wendet Bold/hell Zyan auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-440">Applies bold/bright cyan to foreground</span></span>                             |
| <span data-ttu-id="51d00-441">97</span><span class="sxs-lookup"><span data-stu-id="51d00-441">97</span></span>    | <span data-ttu-id="51d00-442">Heller Vordergrund weiß</span><span class="sxs-lookup"><span data-stu-id="51d00-442">Bright Foreground White</span></span>   | <span data-ttu-id="51d00-443">Wendet Fett/hell weiß auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-443">Applies bold/bright white to foreground</span></span>                            |
| <span data-ttu-id="51d00-444">100</span><span class="sxs-lookup"><span data-stu-id="51d00-444">100</span></span>   | <span data-ttu-id="51d00-445">Heller Hintergrund schwarz</span><span class="sxs-lookup"><span data-stu-id="51d00-445">Bright Background Black</span></span>   | <span data-ttu-id="51d00-446">Wendet Fett/Hellschwarz auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="51d00-446">Applies bold/bright black to background</span></span>                            |
| <span data-ttu-id="51d00-447">101</span><span class="sxs-lookup"><span data-stu-id="51d00-447">101</span></span>   | <span data-ttu-id="51d00-448">Heller Hintergrund rot</span><span class="sxs-lookup"><span data-stu-id="51d00-448">Bright Background Red</span></span>     | <span data-ttu-id="51d00-449">Wendet Fett/hell rot auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="51d00-449">Applies bold/bright red to background</span></span>                              |
| <span data-ttu-id="51d00-450">102</span><span class="sxs-lookup"><span data-stu-id="51d00-450">102</span></span>   | <span data-ttu-id="51d00-451">Heller Hintergrund grün</span><span class="sxs-lookup"><span data-stu-id="51d00-451">Bright Background Green</span></span>   | <span data-ttu-id="51d00-452">Wendet Fett/hellgrün auf Hintergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-452">Applies bold/bright green to background</span></span>                            |
| <span data-ttu-id="51d00-453">103</span><span class="sxs-lookup"><span data-stu-id="51d00-453">103</span></span>   | <span data-ttu-id="51d00-454">Heller Hintergrund Gelb</span><span class="sxs-lookup"><span data-stu-id="51d00-454">Bright Background Yellow</span></span>  | <span data-ttu-id="51d00-455">Wendet Fett/hell gelb auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="51d00-455">Applies bold/bright yellow to background</span></span>                           |
| <span data-ttu-id="51d00-456">104</span><span class="sxs-lookup"><span data-stu-id="51d00-456">104</span></span>   | <span data-ttu-id="51d00-457">Heller Hintergrund blau</span><span class="sxs-lookup"><span data-stu-id="51d00-457">Bright Background Blue</span></span>    | <span data-ttu-id="51d00-458">Wendet Fett/hellblau auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="51d00-458">Applies bold/bright blue to background</span></span>                             |
| <span data-ttu-id="51d00-459">105</span><span class="sxs-lookup"><span data-stu-id="51d00-459">105</span></span>   | <span data-ttu-id="51d00-460">Heller Hintergrund Magenta</span><span class="sxs-lookup"><span data-stu-id="51d00-460">Bright Background Magenta</span></span> | <span data-ttu-id="51d00-461">Wendet Bold/hellmagenta auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="51d00-461">Applies bold/bright magenta to background</span></span>                          |
| <span data-ttu-id="51d00-462">106</span><span class="sxs-lookup"><span data-stu-id="51d00-462">106</span></span>   | <span data-ttu-id="51d00-463">Heller Hintergrund Cyan</span><span class="sxs-lookup"><span data-stu-id="51d00-463">Bright Background Cyan</span></span>    | <span data-ttu-id="51d00-464">Wendet Bold/hell Zyan auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="51d00-464">Applies bold/bright cyan to background</span></span>                             |
| <span data-ttu-id="51d00-465">107</span><span class="sxs-lookup"><span data-stu-id="51d00-465">107</span></span>   | <span data-ttu-id="51d00-466">Heller Hintergrund weiß</span><span class="sxs-lookup"><span data-stu-id="51d00-466">Bright Background White</span></span>   | <span data-ttu-id="51d00-467">Wendet Fett/hell weiß auf Hintergrund an</span><span class="sxs-lookup"><span data-stu-id="51d00-467">Applies bold/bright white to background</span></span>                            |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="51d00-468"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Erweiterte Farben</span><span class="sxs-lookup"><span data-stu-id="51d00-468"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="51d00-469">Einige virtuelle Terminal Emulatoren unterstützen eine Palette von Farben, die größer sind als die von der Windows-Konsole bereitgestellten Farben.</span><span class="sxs-lookup"><span data-stu-id="51d00-469">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="51d00-470">Für diese erweiterten Farben wählt die Windows-Konsole die nächstgelegene Farbe aus der vorhandenen 16-Farbtabelle zum Anzeigen aus.</span><span class="sxs-lookup"><span data-stu-id="51d00-470">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="51d00-471">Im Gegensatz zu typischen SGR-Werten verbrauchen die erweiterten Werte nach dem anfänglichen Indikator gemäß der folgenden Tabelle zusätzliche Parameter.</span><span class="sxs-lookup"><span data-stu-id="51d00-471">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="51d00-472">SGR-unter Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-472">SGR Subsequence</span></span>                            | <span data-ttu-id="51d00-473">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="51d00-473">Description</span></span>                                                                                 |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="51d00-474">38; 2,2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="51d00-474">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="51d00-475">Festlegen der Vordergrundfarbe auf RGB-Wert in &lt; r- &gt; , &lt; g- &gt; , b- &lt; &gt; Parametern\*</span><span class="sxs-lookup"><span data-stu-id="51d00-475">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="51d00-476">48; 2,2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="51d00-476">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="51d00-477">Legen Sie die Hintergrundfarbe auf den in &lt; r- &gt; , &lt; g- &gt; , b- &lt; &gt; Parametern\*</span><span class="sxs-lookup"><span data-stu-id="51d00-477">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="51d00-478">38; 5@@ &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="51d00-478">38 ; 5 ; &lt;s&gt;</span></span>                         | <span data-ttu-id="51d00-479">Festlegen der Vordergrundfarbe auf den &lt; s- &gt; Index in 88-oder 256-Farbtabelle\*</span><span class="sxs-lookup"><span data-stu-id="51d00-479">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span>                          |
| <span data-ttu-id="51d00-480">48; 5@@ &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="51d00-480">48 ; 5 ; &lt;s&gt;</span></span>                         | <span data-ttu-id="51d00-481">Festlegen der Hintergrundfarbe auf den &lt; s- &gt; Index in der 88-oder 256-Farbtabelle\*</span><span class="sxs-lookup"><span data-stu-id="51d00-481">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span>                          |



<span data-ttu-id="51d00-482">\*Die Farbpaletten 88 und 256, die intern für Vergleiche verwaltet werden, basieren auf dem xterm-Terminal Emulator.</span><span class="sxs-lookup"><span data-stu-id="51d00-482">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="51d00-483">Die Vergleichs-/Rundungs Tabellen können zu diesem Zeitpunkt nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="51d00-483">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="51d00-484"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Bildschirmfarben</span><span class="sxs-lookup"><span data-stu-id="51d00-484"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="51d00-485">Der folgende Befehl ermöglicht es der Anwendung, die Farbpalette-Werte der Bildschirmfarben auf einen beliebigen RGB-Wert festzulegen.</span><span class="sxs-lookup"><span data-stu-id="51d00-485">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="51d00-486">Die RGB-Werte sollten hexadezimal Werte zwischen `0` und sein `ff` und durch den Schrägstrich (z. b. `rgb:1/24/86` ) getrennt werden.</span><span class="sxs-lookup"><span data-stu-id="51d00-486">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="51d00-487">Beachten Sie, dass es sich bei dieser Sequenz um eine "Command"-Sequenz vom Typ "osc" handelt, nicht um ein CSI wie viele der anderen aufgelisteten Sequenzen, und beginnen Sie mit " \\ x1B \] " und nicht mit " \\ x1B \[ ".</span><span class="sxs-lookup"><span data-stu-id="51d00-487">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="51d00-488">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-488">Sequence</span></span>                                                           | <span data-ttu-id="51d00-489">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-489">Description</span></span>          | <span data-ttu-id="51d00-490">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-490">Behavior</span></span>                                                                                                     |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="51d00-491">ESC \] 4; &lt; i &gt; ; RGB: &lt; r &gt;  /  &lt; g &gt;  /  &lt; b &gt; ESC</span><span class="sxs-lookup"><span data-stu-id="51d00-491">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="51d00-492">Ändern der Bildschirmfarben</span><span class="sxs-lookup"><span data-stu-id="51d00-492">Modify Screen Colors</span></span> | <span data-ttu-id="51d00-493">Legt den Bildschirm Farbpalette-Index &lt; i &gt; auf die RGB-Werte fest, die in &lt; r &gt; , &lt; g &gt; , &lt; b angegeben sind.&gt;</span><span class="sxs-lookup"><span data-stu-id="51d00-493">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="51d00-494"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modusänderungen</span><span class="sxs-lookup"><span data-stu-id="51d00-494"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="51d00-495">Dabei handelt es sich um Sequenzen, die die Eingabemodi steuern.</span><span class="sxs-lookup"><span data-stu-id="51d00-495">These are sequences that control the input modes.</span></span> <span data-ttu-id="51d00-496">Es gibt zwei unterschiedliche Sätze von Eingabemodi: den Cursor Schlüssel Modus und den Keypad-Schlüssel Modus.</span><span class="sxs-lookup"><span data-stu-id="51d00-496">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="51d00-497">Der Cursor Schlüssel Modus steuert die Sequenzen, die von den Pfeiltasten sowie von Start-und Endzeichen ausgegeben werden, während der Keypad-Schlüssel Modus die von den Schlüsseln im NumPad ausgegebene Sequenzen und die Funktionstasten steuert.</span><span class="sxs-lookup"><span data-stu-id="51d00-497">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="51d00-498">Jeder dieser Modi ist eine einfache boolesche Einstellung – der Cursor Schlüssel Modus ist entweder normal (Standard) oder Anwendung, und der Keypad-Schlüssel Modus ist entweder numerisch (Standard) oder Anwendung.</span><span class="sxs-lookup"><span data-stu-id="51d00-498">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="51d00-499">Weitere Informationen zu den in diesen Modi ausgegebenen Sequenzen finden Sie in den Abschnitten Cursor Schlüssel und Numpad &-Funktions Schlüsseln.</span><span class="sxs-lookup"><span data-stu-id="51d00-499">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="51d00-500">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-500">Sequence</span></span>     | <span data-ttu-id="51d00-501">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-501">Code</span></span>    | <span data-ttu-id="51d00-502">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-502">Description</span></span>                                            | <span data-ttu-id="51d00-503">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-503">Behavior</span></span>                                                |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="51d00-504">ESC =</span><span class="sxs-lookup"><span data-stu-id="51d00-504">ESC =</span></span>        | <span data-ttu-id="51d00-505">Deckpam</span><span class="sxs-lookup"><span data-stu-id="51d00-505">DECKPAM</span></span> | <span data-ttu-id="51d00-506">Aktivieren des Keypad-Anwendungsmodus</span><span class="sxs-lookup"><span data-stu-id="51d00-506">Enable Keypad Application Mode</span></span>                         | <span data-ttu-id="51d00-507">Keypad-Schlüssel geben Ihre anwendungsmodussequenzen aus.</span><span class="sxs-lookup"><span data-stu-id="51d00-507">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="51d00-508">Dor &gt;</span><span class="sxs-lookup"><span data-stu-id="51d00-508">ESC &gt;</span></span>     | <span data-ttu-id="51d00-509">Deckpnm</span><span class="sxs-lookup"><span data-stu-id="51d00-509">DECKPNM</span></span> | <span data-ttu-id="51d00-510">Aktivieren des numerischen Keypad-Modus</span><span class="sxs-lookup"><span data-stu-id="51d00-510">Enable Keypad Numeric Mode</span></span>                             | <span data-ttu-id="51d00-511">Keypad-Schlüssel geben ihre numerischen modussequenzen aus.</span><span class="sxs-lookup"><span data-stu-id="51d00-511">Keypad keys will emit their Numeric Mode sequences.</span></span>     |
| <span data-ttu-id="51d00-512">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="51d00-512">ESC \[ ?</span></span> <span data-ttu-id="51d00-513">1 Stunde</span><span class="sxs-lookup"><span data-stu-id="51d00-513">1 h</span></span> | <span data-ttu-id="51d00-514">Decckm</span><span class="sxs-lookup"><span data-stu-id="51d00-514">DECCKM</span></span>  | <span data-ttu-id="51d00-515">Aktivieren des Anwendungsmodus für Cursor Tasten</span><span class="sxs-lookup"><span data-stu-id="51d00-515">Enable Cursor Keys Application Mode</span></span>                    | <span data-ttu-id="51d00-516">Keypad-Schlüssel geben Ihre anwendungsmodussequenzen aus.</span><span class="sxs-lookup"><span data-stu-id="51d00-516">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="51d00-517">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="51d00-517">ESC \[ ?</span></span> <span data-ttu-id="51d00-518">1 l</span><span class="sxs-lookup"><span data-stu-id="51d00-518">1 l</span></span> | <span data-ttu-id="51d00-519">Decckm</span><span class="sxs-lookup"><span data-stu-id="51d00-519">DECCKM</span></span>  | <span data-ttu-id="51d00-520">Deaktivieren Sie den Anwendungsmodus für Cursor Tasten (normaler Modus verwenden).</span><span class="sxs-lookup"><span data-stu-id="51d00-520">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="51d00-521">Keypad-Schlüssel geben ihre numerischen modussequenzen aus.</span><span class="sxs-lookup"><span data-stu-id="51d00-521">Keypad keys will emit their Numeric Mode sequences.</span></span>     |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="51d00-522"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Abfrage Status</span><span class="sxs-lookup"><span data-stu-id="51d00-522"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="51d00-523">Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufruf von get \* Console-APIs zum Abrufen von Statusinformationen zum aktuellen Zustand der Konsolen Puffer.</span><span class="sxs-lookup"><span data-stu-id="51d00-523">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

<span data-ttu-id="51d00-524">**Hinweis**  Diese Abfragen geben Ihre Antworten sofort in den Konsolen Eingabestream aus, wenn Sie im Ausgabestream erkannt werden, während die \_ virtuelle \_ Terminal \_ Verarbeitung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="51d00-524">**Note**  These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="51d00-525">Das \_ \_ eingabeflag "virtuelles Terminal aktivieren" \_ gilt nicht für Abfrage Befehle, da davon ausgegangen wird, dass eine Anwendung, die die Abfrage erstellt, die Antwort immer empfangen möchte.</span><span class="sxs-lookup"><span data-stu-id="51d00-525">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="51d00-526">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-526">Sequence</span></span>   | <span data-ttu-id="51d00-527">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-527">Code</span></span>    | <span data-ttu-id="51d00-528">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-528">Description</span></span>            | <span data-ttu-id="51d00-529">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-529">Behavior</span></span>                                                                                                               |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="51d00-530">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="51d00-530">ESC \[ 6 n</span></span> | <span data-ttu-id="51d00-531">Decxcpr</span><span class="sxs-lookup"><span data-stu-id="51d00-531">DECXCPR</span></span> | <span data-ttu-id="51d00-532">Cursor Position des Berichts</span><span class="sxs-lookup"><span data-stu-id="51d00-532">Report Cursor Position</span></span> | <span data-ttu-id="51d00-533">Geben Sie die Cursorposition wie folgt aus: Esc \[ &lt; r &gt; ; &lt; c &gt; r Where &lt; R &gt; = Cursor Zeile und &lt; c &gt; = Cursor Spalte</span><span class="sxs-lookup"><span data-stu-id="51d00-533">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="51d00-534">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="51d00-534">ESC \[ 0 c</span></span> | <span data-ttu-id="51d00-535">De</span><span class="sxs-lookup"><span data-stu-id="51d00-535">DA</span></span>      | <span data-ttu-id="51d00-536">Geräte Attribute</span><span class="sxs-lookup"><span data-stu-id="51d00-536">Device Attributes</span></span>      | <span data-ttu-id="51d00-537">Melden Sie die Terminal Identität.</span><span class="sxs-lookup"><span data-stu-id="51d00-537">Report the terminal identity.</span></span> <span data-ttu-id="51d00-538">Gibt " \\ x1B \[ ? 1; 0C" aus, was "VT101 ohne Optionen" angibt.</span><span class="sxs-lookup"><span data-stu-id="51d00-538">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span>                            |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="51d00-539"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tafeln</span><span class="sxs-lookup"><span data-stu-id="51d00-539"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="51d00-540">Obwohl die Windows-Konsole normalerweise davon ausgeht, dass Registerkarten ausschließlich acht Zeichen umfassen, \* können nix-Anwendungen, die bestimmte Sequenzen verwenden, bearbeiten, wo sich die Tabstopps innerhalb der Konsolenfenster befinden, um die Cursor Bewegung durch die Anwendung zu optimieren</span><span class="sxs-lookup"><span data-stu-id="51d00-540">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="51d00-541">Die folgenden Sequenzen ermöglichen es einer Anwendung, die Position der Tabstopps innerhalb des Konsolenfensters festzulegen, Sie zu entfernen und zwischen Ihnen zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="51d00-541">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="51d00-542">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-542">Sequence</span></span>           | <span data-ttu-id="51d00-543">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-543">Code</span></span> | <span data-ttu-id="51d00-544">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-544">Description</span></span>                     | <span data-ttu-id="51d00-545">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-545">Behavior</span></span>                                                                                                                                                                                                                    |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="51d00-546">ESC H</span><span class="sxs-lookup"><span data-stu-id="51d00-546">ESC H</span></span>              | <span data-ttu-id="51d00-547">HTS</span><span class="sxs-lookup"><span data-stu-id="51d00-547">HTS</span></span>  | <span data-ttu-id="51d00-548">Horizontaler Registerkarten Satz</span><span class="sxs-lookup"><span data-stu-id="51d00-548">Horizontal Tab Set</span></span>              | <span data-ttu-id="51d00-549">Legt einen Tabstopp in der aktuellen Spalte fest, in der sich der Cursor befindet.</span><span class="sxs-lookup"><span data-stu-id="51d00-549">Sets a tab stop in the current column the cursor is in.</span></span>                                                                                                                                                                     |
| <span data-ttu-id="51d00-550">ESC \[ &lt; n &gt; I</span><span class="sxs-lookup"><span data-stu-id="51d00-550">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="51d00-551">CHT</span><span class="sxs-lookup"><span data-stu-id="51d00-551">CHT</span></span>  | <span data-ttu-id="51d00-552">Horizontale Cursor Registerkarte (vorwärts)</span><span class="sxs-lookup"><span data-stu-id="51d00-552">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="51d00-553">Bewegen Sie den Cursor mit einer Tabstopp Taste zur nächsten Spalte (in derselben Zeile).</span><span class="sxs-lookup"><span data-stu-id="51d00-553">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="51d00-554">Wenn keine weiteren Tabstopps vorhanden sind, fahren Sie mit der letzten Spalte in der Zeile fort.</span><span class="sxs-lookup"><span data-stu-id="51d00-554">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="51d00-555">Wenn sich der Cursor in der letzten Spalte befindet, wechseln Sie zur ersten Spalte der nächsten Zeile.</span><span class="sxs-lookup"><span data-stu-id="51d00-555">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="51d00-556">ESC \[ &lt; n &gt; Z</span><span class="sxs-lookup"><span data-stu-id="51d00-556">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="51d00-557">CBT</span><span class="sxs-lookup"><span data-stu-id="51d00-557">CBT</span></span>  | <span data-ttu-id="51d00-558">Cursor Registerkarte rückwärts</span><span class="sxs-lookup"><span data-stu-id="51d00-558">Cursor Backwards Tab</span></span>            | <span data-ttu-id="51d00-559">Bewegen Sie den Cursor in die vorherige Spalte (in derselben Zeile) mit einer Tabstopp Taste.</span><span class="sxs-lookup"><span data-stu-id="51d00-559">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="51d00-560">Wenn keine weiteren Tabstopps vorhanden sind, verschiebt den Cursor zur ersten Spalte.</span><span class="sxs-lookup"><span data-stu-id="51d00-560">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="51d00-561">Wenn sich der Cursor in der ersten Spalte befindet, verschiebt den Cursor nicht.</span><span class="sxs-lookup"><span data-stu-id="51d00-561">If the cursor is in the first column, doesn’t move the cursor.</span></span>              |
| <span data-ttu-id="51d00-562">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="51d00-562">ESC \[ 0 g</span></span>         | <span data-ttu-id="51d00-563">TBC</span><span class="sxs-lookup"><span data-stu-id="51d00-563">TBC</span></span>  | <span data-ttu-id="51d00-564">Tab Clear (aktuelle Spalte)</span><span class="sxs-lookup"><span data-stu-id="51d00-564">Tab Clear (current column)</span></span>      | <span data-ttu-id="51d00-565">Löscht den Tabstopp in der aktuellen Spalte, sofern vorhanden.</span><span class="sxs-lookup"><span data-stu-id="51d00-565">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="51d00-566">Andernfalls geschieht nichts.</span><span class="sxs-lookup"><span data-stu-id="51d00-566">Otherwise does nothing.</span></span>                                                                                                                                         |
| <span data-ttu-id="51d00-567">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="51d00-567">ESC \[ 3 g</span></span>         | <span data-ttu-id="51d00-568">TBC</span><span class="sxs-lookup"><span data-stu-id="51d00-568">TBC</span></span>  | <span data-ttu-id="51d00-569">Tab Clear (alle Spalten)</span><span class="sxs-lookup"><span data-stu-id="51d00-569">Tab Clear (all columns)</span></span>         | <span data-ttu-id="51d00-570">Löscht alle momentan festgelegten Tabstopps.</span><span class="sxs-lookup"><span data-stu-id="51d00-570">Clears all currently set tab stops.</span></span>                                                                                                                                                                                         |



- <span data-ttu-id="51d00-571">Bei n und CBT &lt; &gt; ist n ein optionaler Parameter, der (Standardwert = 1) angibt, wie oft der Cursor in der angegebenen Richtung vorwärts bewegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="51d00-571">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="51d00-572">Wenn keine Tabstopps über HTS festgelegt sind, werden die erste und die letzte Spalte des Fensters von cht und CBT als die einzigen beiden Tabstopps behandelt.</span><span class="sxs-lookup"><span data-stu-id="51d00-572">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="51d00-573">Die Verwendung von HTS zum Festlegen eines Tabstopps bewirkt auch, dass die Konsole in der Ausgabe eines Tabstopps (0x09, " \\ t") auf die gleiche Weise wie bei cht zum nächsten Tabstopp navigiert.</span><span class="sxs-lookup"><span data-stu-id="51d00-573">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="51d00-574"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Zeichensatz festlegen</span><span class="sxs-lookup"><span data-stu-id="51d00-574"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="51d00-575">Die folgenden Sequenzen ermöglichen einem Programm, die Zuordnung des aktiven Zeichensatzes zu ändern.</span><span class="sxs-lookup"><span data-stu-id="51d00-575">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="51d00-576">Dies ermöglicht es einem Programm, 7-Bit-ASCII-Zeichen auszugeben, Sie aber als andere Symbole auf dem Terminalbildschirm selbst anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="51d00-576">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="51d00-577">Zurzeit sind die einzigen beiden unterstützten Zeichensätze ASCII (Standard) und der besondere Grafik Zeichensatz für Dec.</span><span class="sxs-lookup"><span data-stu-id="51d00-577">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="51d00-578">Unter finden Sie <http://vt100.net/docs/vt220-rm/table2-4.html> eine Liste aller Zeichen, die durch den speziellen Dec-Grafik Zeichensatz dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="51d00-578">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="51d00-579">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-579">Sequence</span></span> | <span data-ttu-id="51d00-580">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-580">Description</span></span>                                | <span data-ttu-id="51d00-581">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-581">Behavior</span></span>                      |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="51d00-582">ESC (0</span><span class="sxs-lookup"><span data-stu-id="51d00-582">ESC ( 0</span></span>  | <span data-ttu-id="51d00-583">Zeichensatz festlegen – Dec-Zeichnungs Linie</span><span class="sxs-lookup"><span data-stu-id="51d00-583">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="51d00-584">Aktiviert den Modus "Dec Line Drawing"</span><span class="sxs-lookup"><span data-stu-id="51d00-584">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="51d00-585">ESC (B</span><span class="sxs-lookup"><span data-stu-id="51d00-585">ESC ( B</span></span>  | <span data-ttu-id="51d00-586">Festlegen des Zeichensatzes – US-ASCII</span><span class="sxs-lookup"><span data-stu-id="51d00-586">Designate Character Set – US ASCII</span></span>         | <span data-ttu-id="51d00-587">Aktiviert den ASCII-Modus (Standard)</span><span class="sxs-lookup"><span data-stu-id="51d00-587">Enables ASCII Mode (Default)</span></span>  |



<span data-ttu-id="51d00-588">Insbesondere wird der Dec-Zeichnungsmodus zum Zeichnen von Rahmen in Konsolen Anwendungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="51d00-588">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="51d00-589">In der folgenden Tabelle ist dargestellt, welche ASCII-Zeichen mit welchem Zeilen Zeichnungs Zeichen zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="51d00-589">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="51d00-590">Hex</span><span class="sxs-lookup"><span data-stu-id="51d00-590">Hex</span></span>  | <span data-ttu-id="51d00-591">ASCII</span><span class="sxs-lookup"><span data-stu-id="51d00-591">ASCII</span></span> | <span data-ttu-id="51d00-592">Zeilen Zeichnung mit Dec</span><span class="sxs-lookup"><span data-stu-id="51d00-592">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="51d00-593">0x6a</span><span class="sxs-lookup"><span data-stu-id="51d00-593">0x6a</span></span> | <span data-ttu-id="51d00-594">j</span><span class="sxs-lookup"><span data-stu-id="51d00-594">j</span></span>     | <span data-ttu-id="51d00-595">┘</span><span class="sxs-lookup"><span data-stu-id="51d00-595">┘</span></span>                |
| <span data-ttu-id="51d00-596">0x6b</span><span class="sxs-lookup"><span data-stu-id="51d00-596">0x6b</span></span> | <span data-ttu-id="51d00-597">k</span><span class="sxs-lookup"><span data-stu-id="51d00-597">k</span></span>     | <span data-ttu-id="51d00-598">┐</span><span class="sxs-lookup"><span data-stu-id="51d00-598">┐</span></span>                |
| <span data-ttu-id="51d00-599">0x6C</span><span class="sxs-lookup"><span data-stu-id="51d00-599">0x6c</span></span> | <span data-ttu-id="51d00-600">l</span><span class="sxs-lookup"><span data-stu-id="51d00-600">l</span></span>     | <span data-ttu-id="51d00-601">┌</span><span class="sxs-lookup"><span data-stu-id="51d00-601">┌</span></span>                |
| <span data-ttu-id="51d00-602">0x6d</span><span class="sxs-lookup"><span data-stu-id="51d00-602">0x6d</span></span> | <span data-ttu-id="51d00-603">m</span><span class="sxs-lookup"><span data-stu-id="51d00-603">m</span></span>     | <span data-ttu-id="51d00-604">└</span><span class="sxs-lookup"><span data-stu-id="51d00-604">└</span></span>                |
| <span data-ttu-id="51d00-605">0x6e</span><span class="sxs-lookup"><span data-stu-id="51d00-605">0x6e</span></span> | <span data-ttu-id="51d00-606">n</span><span class="sxs-lookup"><span data-stu-id="51d00-606">n</span></span>     | <span data-ttu-id="51d00-607">┼</span><span class="sxs-lookup"><span data-stu-id="51d00-607">┼</span></span>                |
| <span data-ttu-id="51d00-608">0x71</span><span class="sxs-lookup"><span data-stu-id="51d00-608">0x71</span></span> | <span data-ttu-id="51d00-609">q</span><span class="sxs-lookup"><span data-stu-id="51d00-609">q</span></span>     | <span data-ttu-id="51d00-610">─</span><span class="sxs-lookup"><span data-stu-id="51d00-610">─</span></span>                |
| <span data-ttu-id="51d00-611">0x74</span><span class="sxs-lookup"><span data-stu-id="51d00-611">0x74</span></span> | <span data-ttu-id="51d00-612">t</span><span class="sxs-lookup"><span data-stu-id="51d00-612">t</span></span>     | <span data-ttu-id="51d00-613">├</span><span class="sxs-lookup"><span data-stu-id="51d00-613">├</span></span>                |
| <span data-ttu-id="51d00-614">0x75</span><span class="sxs-lookup"><span data-stu-id="51d00-614">0x75</span></span> | <span data-ttu-id="51d00-615">u</span><span class="sxs-lookup"><span data-stu-id="51d00-615">u</span></span>     | <span data-ttu-id="51d00-616">┤</span><span class="sxs-lookup"><span data-stu-id="51d00-616">┤</span></span>                |
| <span data-ttu-id="51d00-617">0x76</span><span class="sxs-lookup"><span data-stu-id="51d00-617">0x76</span></span> | <span data-ttu-id="51d00-618">v</span><span class="sxs-lookup"><span data-stu-id="51d00-618">v</span></span>     | <span data-ttu-id="51d00-619">┴</span><span class="sxs-lookup"><span data-stu-id="51d00-619">┴</span></span>                |
| <span data-ttu-id="51d00-620">0x77</span><span class="sxs-lookup"><span data-stu-id="51d00-620">0x77</span></span> | <span data-ttu-id="51d00-621">w</span><span class="sxs-lookup"><span data-stu-id="51d00-621">w</span></span>     | <span data-ttu-id="51d00-622">┬</span><span class="sxs-lookup"><span data-stu-id="51d00-622">┬</span></span>                |
| <span data-ttu-id="51d00-623">0x78</span><span class="sxs-lookup"><span data-stu-id="51d00-623">0x78</span></span> | <span data-ttu-id="51d00-624">x</span><span class="sxs-lookup"><span data-stu-id="51d00-624">x</span></span>     | <span data-ttu-id="51d00-625">│</span><span class="sxs-lookup"><span data-stu-id="51d00-625">│</span></span>                |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="51d00-626"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrollränder</span><span class="sxs-lookup"><span data-stu-id="51d00-626"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="51d00-627">Die folgenden Sequenzen ermöglichen einem Programm, den "scrollbereich" des Bildschirms zu konfigurieren, der von scrollvorgängen betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="51d00-627">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="51d00-628">Dabei handelt es sich um eine Teilmenge der Zeilen, die angepasst werden, wenn auf dem Bildschirm ein anderer Bildlauf durchführt, z. b. auf einem \\ n-oder RI-.</span><span class="sxs-lookup"><span data-stu-id="51d00-628">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="51d00-629">Diese Ränder wirken sich auch auf die Zeilen aus, die durch Einfügezeile (IL) und Delete Line (DL) geändert werden, Scrollen nach oben (su) und Scrollen nach unten (SD).</span><span class="sxs-lookup"><span data-stu-id="51d00-629">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="51d00-630">Die scrollränder können besonders nützlich sein, wenn ein Teil des Bildschirms angezeigt wird, wenn der restliche Bildschirm nicht angezeigt wird, z. b. eine Titelleiste am oberen Rand oder eine Statusleiste am unteren Rand der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="51d00-630">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="51d00-631">Für decstbm gibt es zwei optionale Parameter: &lt; t &gt; und &lt; b &gt; , die verwendet werden, um die Zeilen anzugeben, die den oberen und unteren Rand des Bild Lauf Bereichs darstellen (einschließlich).</span><span class="sxs-lookup"><span data-stu-id="51d00-631">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="51d00-632">Wenn die Parameter ausgelassen werden, lautet der Standardwert 1, wobei &lt; &gt; &lt; b &gt; standardmäßig die aktuelle VIEWPORTHÖHE verwendet.</span><span class="sxs-lookup"><span data-stu-id="51d00-632">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="51d00-633">Scrollränder sind pro Puffer, was wichtig ist, dass der Alternative Puffer und der Hauptpuffer separate Einstellungen für die scrollränder behalten (sodass eine Vollbild-Anwendung im alternativen Puffer die Ränder des Haupt Puffers nicht verbleibt).</span><span class="sxs-lookup"><span data-stu-id="51d00-633">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="51d00-634">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-634">Sequence</span></span>                       | <span data-ttu-id="51d00-635">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-635">Code</span></span>    | <span data-ttu-id="51d00-636">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-636">Description</span></span>          | <span data-ttu-id="51d00-637">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-637">Behavior</span></span>                                       |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="51d00-638">ESC \[ &lt; t &gt; ; &lt; b &gt; r</span><span class="sxs-lookup"><span data-stu-id="51d00-638">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="51d00-639">Decstbm</span><span class="sxs-lookup"><span data-stu-id="51d00-639">DECSTBM</span></span> | <span data-ttu-id="51d00-640">Scrollbereich festlegen</span><span class="sxs-lookup"><span data-stu-id="51d00-640">Set Scrolling Region</span></span> | <span data-ttu-id="51d00-641">Legt die VT-scrollränder des Viewports fest.</span><span class="sxs-lookup"><span data-stu-id="51d00-641">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="51d00-642"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Fenstertitel</span><span class="sxs-lookup"><span data-stu-id="51d00-642"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="51d00-643">Mit den folgenden Befehlen kann die Anwendung den Titel des Konsolenfensters auf den angegebenen Zeichen folgen &lt; &gt; Parameter festlegen.</span><span class="sxs-lookup"><span data-stu-id="51d00-643">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="51d00-644">Die Zeichenfolge muss weniger als 255 Zeichen annehmen, um akzeptiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="51d00-644">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="51d00-645">Dies entspricht dem Aufrufen von setconsoletitle mit der angegebenen Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="51d00-645">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="51d00-646">Beachten Sie, dass es sich bei diesen Sequenzen um die Befehle "Betriebssystem Befehl" des Befehls "osc" handelt, nicht um ein CSI-wie viele der anderen aufgelisteten Sequenzen, und damit beginnt " \\ x1B \] ", nicht " \\ x1B \[ ".</span><span class="sxs-lookup"><span data-stu-id="51d00-646">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="51d00-647">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-647">Sequence</span></span>                      | <span data-ttu-id="51d00-648">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-648">Description</span></span>               | <span data-ttu-id="51d00-649">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-649">Behavior</span></span>                                           |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="51d00-650">ESC \] 0; &lt; Zeichenfolge &gt; Bel</span><span class="sxs-lookup"><span data-stu-id="51d00-650">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="51d00-651">Symbol und Fenstertitel festlegen</span><span class="sxs-lookup"><span data-stu-id="51d00-651">Set Icon and Window Title</span></span> | <span data-ttu-id="51d00-652">Legt den Titel des Konsolenfensters auf &lt; String fest &gt; .</span><span class="sxs-lookup"><span data-stu-id="51d00-652">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="51d00-653">ESC \] 2; &lt; Zeichenfolge &gt; Bel</span><span class="sxs-lookup"><span data-stu-id="51d00-653">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="51d00-654">Fenstertitel festlegen</span><span class="sxs-lookup"><span data-stu-id="51d00-654">Set Window Title</span></span>          | <span data-ttu-id="51d00-655">Legt den Titel des Konsolenfensters auf &lt; String fest &gt; .</span><span class="sxs-lookup"><span data-stu-id="51d00-655">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="51d00-656">Das abschließende Zeichen hier ist das "Glocken Zeichen", " \\ x07".</span><span class="sxs-lookup"><span data-stu-id="51d00-656">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="51d00-657"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternativer Bildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="51d00-657"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="51d00-658">\*Anwendungen im Stil von nix nutzen häufig einen alternativen Bildschirm Puffer, damit Sie den gesamten Inhalt des Puffers ändern können, ohne die Anwendung zu beeinträchtigen, von der Sie gestartet wurden.</span><span class="sxs-lookup"><span data-stu-id="51d00-658">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="51d00-659">Der Alternative Puffer ist genau die Abmessungen des Fensters, ohne einen scrollbackfunktionalität Bereich.</span><span class="sxs-lookup"><span data-stu-id="51d00-659">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="51d00-660">Ein Beispiel für dieses Verhalten ist, wenn vim von bash gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="51d00-660">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="51d00-661">Vim verwendet den gesamten Bildschirm, um die Datei zu bearbeiten. Wenn Sie zu bash zurückkehren, bleibt der ursprüngliche Puffer unverändert.</span><span class="sxs-lookup"><span data-stu-id="51d00-661">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="51d00-662">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-662">Sequence</span></span>           | <span data-ttu-id="51d00-663">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-663">Description</span></span>                 | <span data-ttu-id="51d00-664">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-664">Behavior</span></span>                                   |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="51d00-665">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="51d00-665">ESC \[ ?</span></span> <span data-ttu-id="51d00-666">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="51d00-666">1 0 4 9 h</span></span> | <span data-ttu-id="51d00-667">Alternativen Bildschirm Puffer verwenden</span><span class="sxs-lookup"><span data-stu-id="51d00-667">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="51d00-668">Wechselt zu einem neuen alternativen Bildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="51d00-668">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="51d00-669">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="51d00-669">ESC \[ ?</span></span> <span data-ttu-id="51d00-670">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="51d00-670">1 0 4 9 l</span></span> | <span data-ttu-id="51d00-671">Hauptbildschirm Puffer verwenden</span><span class="sxs-lookup"><span data-stu-id="51d00-671">Use Main Screen Buffer</span></span>      | <span data-ttu-id="51d00-672">Wechselt zum Hauptpuffer.</span><span class="sxs-lookup"><span data-stu-id="51d00-672">Switches to the main buffer.</span></span>               |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="51d00-673"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Fensterbreite</span><span class="sxs-lookup"><span data-stu-id="51d00-673"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="51d00-674">Die folgenden Sequenzen können verwendet werden, um die Breite des Konsolenfensters zu steuern.</span><span class="sxs-lookup"><span data-stu-id="51d00-674">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="51d00-675">Sie sind ungefähr gleichwertig mit dem Aufruf der Konsolen-API setconsolescreenbufferinfoex zum Festlegen der Fensterbreite.</span><span class="sxs-lookup"><span data-stu-id="51d00-675">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="51d00-676">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-676">Sequence</span></span>     | <span data-ttu-id="51d00-677">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-677">Code</span></span>    | <span data-ttu-id="51d00-678">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-678">Description</span></span>                  | <span data-ttu-id="51d00-679">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-679">Behavior</span></span>                                    |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="51d00-680">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="51d00-680">ESC \[ ?</span></span> <span data-ttu-id="51d00-681">3 h</span><span class="sxs-lookup"><span data-stu-id="51d00-681">3 h</span></span> | <span data-ttu-id="51d00-682">Deccolm</span><span class="sxs-lookup"><span data-stu-id="51d00-682">DECCOLM</span></span> | <span data-ttu-id="51d00-683">Festlegen der Anzahl von Spalten auf 132</span><span class="sxs-lookup"><span data-stu-id="51d00-683">Set Number of Columns to 132</span></span> | <span data-ttu-id="51d00-684">Legt die Konsolen Breite auf 132 Spalten breit fest.</span><span class="sxs-lookup"><span data-stu-id="51d00-684">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="51d00-685">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="51d00-685">ESC \[ ?</span></span> <span data-ttu-id="51d00-686">3 l</span><span class="sxs-lookup"><span data-stu-id="51d00-686">3 l</span></span> | <span data-ttu-id="51d00-687">Deccolm</span><span class="sxs-lookup"><span data-stu-id="51d00-687">DECCOLM</span></span> | <span data-ttu-id="51d00-688">Festlegen der Anzahl von Spalten auf 80</span><span class="sxs-lookup"><span data-stu-id="51d00-688">Set Number of Columns to 80</span></span>  | <span data-ttu-id="51d00-689">Legt die Konsolen Breite auf 80 Spalten breit fest.</span><span class="sxs-lookup"><span data-stu-id="51d00-689">Sets the console width to 80 columns wide.</span></span>  |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="51d00-690"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Vorläufiges zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="51d00-690"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="51d00-691">Die folgende Sequenz kann verwendet werden, um bestimmte Eigenschaften auf ihre Standardwerte zurückzusetzen. Die folgenden Eigenschaften werden auf die folgenden Standardwerte zurückgesetzt (Außerdem sind die Sequenzen aufgelistet, die diese Eigenschaften steuern):</span><span class="sxs-lookup"><span data-stu-id="51d00-691">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="51d00-692">Cursor Sichtbarkeit: sichtbar (dectem)</span><span class="sxs-lookup"><span data-stu-id="51d00-692">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="51d00-693">Numerische Keypad: numerischer Modus (decnkm)</span><span class="sxs-lookup"><span data-stu-id="51d00-693">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="51d00-694">Cursor Schlüssel Modus: normaler Modus (decckm)</span><span class="sxs-lookup"><span data-stu-id="51d00-694">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="51d00-695">Obere und untere Ränder: Top = 1, Bottom = Console Height (decstbm)</span><span class="sxs-lookup"><span data-stu-id="51d00-695">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="51d00-696">Zeichensatz: US-ASCII</span><span class="sxs-lookup"><span data-stu-id="51d00-696">Character Set: US ASCII</span></span>
- <span data-ttu-id="51d00-697">Grafikwiedergabe: Standard/Off (SGR)</span><span class="sxs-lookup"><span data-stu-id="51d00-697">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="51d00-698">Cursor Zustand speichern: Startposition (0,0) (decsc)</span><span class="sxs-lookup"><span data-stu-id="51d00-698">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="51d00-699">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-699">Sequence</span></span>   | <span data-ttu-id="51d00-700">Code</span><span class="sxs-lookup"><span data-stu-id="51d00-700">Code</span></span>   | <span data-ttu-id="51d00-701">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="51d00-701">Description</span></span> | <span data-ttu-id="51d00-702">Verhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-702">Behavior</span></span>                                           |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="51d00-703">ESC \[ !</span><span class="sxs-lookup"><span data-stu-id="51d00-703">ESC \[ !</span></span> <span data-ttu-id="51d00-704">p</span><span class="sxs-lookup"><span data-stu-id="51d00-704">p</span></span> | <span data-ttu-id="51d00-705">Decstr</span><span class="sxs-lookup"><span data-stu-id="51d00-705">DECSTR</span></span> | <span data-ttu-id="51d00-706">Vorläufiges zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="51d00-706">Soft Reset</span></span>  | <span data-ttu-id="51d00-707">Setzen Sie bestimmte Terminal Einstellungen auf ihre Standardeinstellungen zurück.</span><span class="sxs-lookup"><span data-stu-id="51d00-707">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="51d00-708"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Eingabe Sequenzen</span><span class="sxs-lookup"><span data-stu-id="51d00-708"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="51d00-709">Die folgenden Terminal Sequenzen werden vom Konsolen Host im Eingabestream ausgegeben, wenn das eingabeflag zum Aktivieren des \_ virtuellen \_ Terminals \_ für das Eingabepuffer Handle mit dem setconsolemode-Flag festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="51d00-709">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="51d00-710">Es gibt zwei interne Modi, die Steuern, welche Sequenzen für die angegebenen Eingabetasten, den Cursor Schlüssel Modus und den Keypad-Schlüssel Modus ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="51d00-710">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="51d00-711">Diese werden im Abschnitt Modusänderungen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="51d00-711">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="51d00-712"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Tasten</span><span class="sxs-lookup"><span data-stu-id="51d00-712"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="51d00-713">Key</span><span class="sxs-lookup"><span data-stu-id="51d00-713">Key</span></span>         | <span data-ttu-id="51d00-714">Normaler Modus</span><span class="sxs-lookup"><span data-stu-id="51d00-714">Normal Mode</span></span> | <span data-ttu-id="51d00-715">Anwendungsmodus</span><span class="sxs-lookup"><span data-stu-id="51d00-715">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="51d00-716">NACH-OBEN</span><span class="sxs-lookup"><span data-stu-id="51d00-716">Up Arrow</span></span>    | <span data-ttu-id="51d00-717">ESC \[ A</span><span class="sxs-lookup"><span data-stu-id="51d00-717">ESC \[ A</span></span>    | <span data-ttu-id="51d00-718">ESC O A</span><span class="sxs-lookup"><span data-stu-id="51d00-718">ESC O A</span></span>          |
| <span data-ttu-id="51d00-719">NACH-UNTEN</span><span class="sxs-lookup"><span data-stu-id="51d00-719">Down Arrow</span></span>  | <span data-ttu-id="51d00-720">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="51d00-720">ESC \[ B</span></span>    | <span data-ttu-id="51d00-721">ESC O B</span><span class="sxs-lookup"><span data-stu-id="51d00-721">ESC O B</span></span>          |
| <span data-ttu-id="51d00-722">NACH-RECHTS</span><span class="sxs-lookup"><span data-stu-id="51d00-722">Right Arrow</span></span> | <span data-ttu-id="51d00-723">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="51d00-723">ESC \[ C</span></span>    | <span data-ttu-id="51d00-724">ESC O C</span><span class="sxs-lookup"><span data-stu-id="51d00-724">ESC O C</span></span>          |
| <span data-ttu-id="51d00-725">NACH-LINKS-TASTE</span><span class="sxs-lookup"><span data-stu-id="51d00-725">Left Arrow</span></span>  | <span data-ttu-id="51d00-726">ESC \[ D</span><span class="sxs-lookup"><span data-stu-id="51d00-726">ESC \[ D</span></span>    | <span data-ttu-id="51d00-727">ESC O D</span><span class="sxs-lookup"><span data-stu-id="51d00-727">ESC O D</span></span>          |
| <span data-ttu-id="51d00-728">Startseite</span><span class="sxs-lookup"><span data-stu-id="51d00-728">Home</span></span>        | <span data-ttu-id="51d00-729">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="51d00-729">ESC \[ H</span></span>    | <span data-ttu-id="51d00-730">ESC O H</span><span class="sxs-lookup"><span data-stu-id="51d00-730">ESC O H</span></span>          |
| <span data-ttu-id="51d00-731">Ende</span><span class="sxs-lookup"><span data-stu-id="51d00-731">End</span></span>         | <span data-ttu-id="51d00-732">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="51d00-732">ESC \[ F</span></span>    | <span data-ttu-id="51d00-733">ESC O F</span><span class="sxs-lookup"><span data-stu-id="51d00-733">ESC O F</span></span>          |



<span data-ttu-id="51d00-734">Wenn außerdem STRG mit einem dieser Tasten gedrückt wird, werden stattdessen die folgenden Sequenzen ausgegeben, unabhängig vom Cursor Schlüssel Modus:</span><span class="sxs-lookup"><span data-stu-id="51d00-734">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="51d00-735">Key</span><span class="sxs-lookup"><span data-stu-id="51d00-735">Key</span></span>                | <span data-ttu-id="51d00-736">Beliebiger Modus</span><span class="sxs-lookup"><span data-stu-id="51d00-736">Any Mode</span></span>       |
|--------------------|----------------|
| <span data-ttu-id="51d00-737">STRG + nach-oben-Taste</span><span class="sxs-lookup"><span data-stu-id="51d00-737">Ctrl + Up Arrow</span></span>    | <span data-ttu-id="51d00-738">ESC \[ 1; 5 A</span><span class="sxs-lookup"><span data-stu-id="51d00-738">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="51d00-739">STRG + nach-unten-Taste</span><span class="sxs-lookup"><span data-stu-id="51d00-739">Ctrl + Down Arrow</span></span>  | <span data-ttu-id="51d00-740">ESC \[ 1; 5 B</span><span class="sxs-lookup"><span data-stu-id="51d00-740">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="51d00-741">STRG + nach-rechts-Taste</span><span class="sxs-lookup"><span data-stu-id="51d00-741">Ctrl + Right Arrow</span></span> | <span data-ttu-id="51d00-742">ESC \[ 1; 5 C</span><span class="sxs-lookup"><span data-stu-id="51d00-742">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="51d00-743">STRG + nach-links-Taste</span><span class="sxs-lookup"><span data-stu-id="51d00-743">Ctrl + Left Arrow</span></span>  | <span data-ttu-id="51d00-744">ESC \[ 1; 5 D</span><span class="sxs-lookup"><span data-stu-id="51d00-744">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="51d00-745"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad-& Funktionstasten</span><span class="sxs-lookup"><span data-stu-id="51d00-745"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="51d00-746">Key</span><span class="sxs-lookup"><span data-stu-id="51d00-746">Key</span></span>       | <span data-ttu-id="51d00-747">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-747">Sequence</span></span>     |
|-----------|--------------|
| <span data-ttu-id="51d00-748">Rückschritt</span><span class="sxs-lookup"><span data-stu-id="51d00-748">Backspace</span></span> | <span data-ttu-id="51d00-749">0x7F (Entf)</span><span class="sxs-lookup"><span data-stu-id="51d00-749">0x7f (DEL)</span></span>   |
| <span data-ttu-id="51d00-750">Anhalten</span><span class="sxs-lookup"><span data-stu-id="51d00-750">Pause</span></span>     | <span data-ttu-id="51d00-751">0x1A (Sub)</span><span class="sxs-lookup"><span data-stu-id="51d00-751">0x1a (SUB)</span></span>   |
| <span data-ttu-id="51d00-752">Escape</span><span class="sxs-lookup"><span data-stu-id="51d00-752">Escape</span></span>    | <span data-ttu-id="51d00-753">0x1B (ESC)</span><span class="sxs-lookup"><span data-stu-id="51d00-753">0x1b (ESC)</span></span>   |
| <span data-ttu-id="51d00-754">Einfügen</span><span class="sxs-lookup"><span data-stu-id="51d00-754">Insert</span></span>    | <span data-ttu-id="51d00-755">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-755">ESC \[ 2 ~</span></span>   |
| <span data-ttu-id="51d00-756">Löschen</span><span class="sxs-lookup"><span data-stu-id="51d00-756">Delete</span></span>    | <span data-ttu-id="51d00-757">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-757">ESC \[ 3 ~</span></span>   |
| <span data-ttu-id="51d00-758">BILD-AUF</span><span class="sxs-lookup"><span data-stu-id="51d00-758">Page Up</span></span>   | <span data-ttu-id="51d00-759">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-759">ESC \[ 5 ~</span></span>   |
| <span data-ttu-id="51d00-760">BILD-AB</span><span class="sxs-lookup"><span data-stu-id="51d00-760">Page Down</span></span> | <span data-ttu-id="51d00-761">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-761">ESC \[ 6 ~</span></span>   |
| <span data-ttu-id="51d00-762">F1</span><span class="sxs-lookup"><span data-stu-id="51d00-762">F1</span></span>        | <span data-ttu-id="51d00-763">ESC O P</span><span class="sxs-lookup"><span data-stu-id="51d00-763">ESC O P</span></span>      |
| <span data-ttu-id="51d00-764">F2</span><span class="sxs-lookup"><span data-stu-id="51d00-764">F2</span></span>        | <span data-ttu-id="51d00-765">ESC O Q</span><span class="sxs-lookup"><span data-stu-id="51d00-765">ESC O Q</span></span>      |
| <span data-ttu-id="51d00-766">F3</span><span class="sxs-lookup"><span data-stu-id="51d00-766">F3</span></span>        | <span data-ttu-id="51d00-767">ESC O R</span><span class="sxs-lookup"><span data-stu-id="51d00-767">ESC O R</span></span>      |
| <span data-ttu-id="51d00-768">F4</span><span class="sxs-lookup"><span data-stu-id="51d00-768">F4</span></span>        | <span data-ttu-id="51d00-769">ESC O S</span><span class="sxs-lookup"><span data-stu-id="51d00-769">ESC O S</span></span>      |
| <span data-ttu-id="51d00-770">F5</span><span class="sxs-lookup"><span data-stu-id="51d00-770">F5</span></span>        | <span data-ttu-id="51d00-771">ESC \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-771">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="51d00-772">F6</span><span class="sxs-lookup"><span data-stu-id="51d00-772">F6</span></span>        | <span data-ttu-id="51d00-773">ESC \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-773">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="51d00-774">F7</span><span class="sxs-lookup"><span data-stu-id="51d00-774">F7</span></span>        | <span data-ttu-id="51d00-775">ESC \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-775">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="51d00-776">F8</span><span class="sxs-lookup"><span data-stu-id="51d00-776">F8</span></span>        | <span data-ttu-id="51d00-777">ESC \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-777">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="51d00-778">F9</span><span class="sxs-lookup"><span data-stu-id="51d00-778">F9</span></span>        | <span data-ttu-id="51d00-779">ESC \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-779">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="51d00-780">F10</span><span class="sxs-lookup"><span data-stu-id="51d00-780">F10</span></span>       | <span data-ttu-id="51d00-781">ESC \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-781">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="51d00-782">F11</span><span class="sxs-lookup"><span data-stu-id="51d00-782">F11</span></span>       | <span data-ttu-id="51d00-783">ESC \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-783">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="51d00-784">F12</span><span class="sxs-lookup"><span data-stu-id="51d00-784">F12</span></span>       | <span data-ttu-id="51d00-785">ESC \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="51d00-785">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="51d00-786"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifizierer</span><span class="sxs-lookup"><span data-stu-id="51d00-786"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="51d00-787">Alt wird behandelt, indem die Sequenz mit einem Escapezeichen versehen wird: Esc &lt; c, &gt; wobei &lt; c &gt; das vom Betriebssystem über gegebene Zeichen ist.</span><span class="sxs-lookup"><span data-stu-id="51d00-787">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="51d00-788">Alt + Strg wird auf die gleiche Weise behandelt, außer dass das Betriebssystem den &lt; c-Schlüssel vorab &gt; in das entsprechende Steuerzeichen verschoben hat, das an die Anwendung weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="51d00-788">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="51d00-789">STRG wird im allgemeinen genau so durchlaufen, wie vom System empfangen.</span><span class="sxs-lookup"><span data-stu-id="51d00-789">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="51d00-790">Dabei handelt es sich in der Regel um ein einzelnes Zeichen, das in den reservierten Leerraum des Steuer Zeichens (0x0-0x1F) verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="51d00-790">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="51d00-791">Beispielsweise wird STRG + @ (0x40) zu NUL (0x00), STRG + \[ (0x5b) wird ESC (0x1B) usw. Einige Tastenkombinationen für STRG werden in der folgenden Tabelle speziell behandelt:</span><span class="sxs-lookup"><span data-stu-id="51d00-791">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="51d00-792">Key</span><span class="sxs-lookup"><span data-stu-id="51d00-792">Key</span></span>                | <span data-ttu-id="51d00-793">Sequenz</span><span class="sxs-lookup"><span data-stu-id="51d00-793">Sequence</span></span>       |
|--------------------|----------------|
| <span data-ttu-id="51d00-794">STRG+LEERTASTE</span><span class="sxs-lookup"><span data-stu-id="51d00-794">Ctrl + Space</span></span>       | <span data-ttu-id="51d00-795">0x00 (NUL)</span><span class="sxs-lookup"><span data-stu-id="51d00-795">0x00 (NUL)</span></span>     |
| <span data-ttu-id="51d00-796">STRG + nach-oben-Taste</span><span class="sxs-lookup"><span data-stu-id="51d00-796">Ctrl + Up Arrow</span></span>    | <span data-ttu-id="51d00-797">ESC \[ 1; 5 A</span><span class="sxs-lookup"><span data-stu-id="51d00-797">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="51d00-798">STRG + nach-unten-Taste</span><span class="sxs-lookup"><span data-stu-id="51d00-798">Ctrl + Down Arrow</span></span>  | <span data-ttu-id="51d00-799">ESC \[ 1; 5 B</span><span class="sxs-lookup"><span data-stu-id="51d00-799">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="51d00-800">STRG + nach-rechts-Taste</span><span class="sxs-lookup"><span data-stu-id="51d00-800">Ctrl + Right Arrow</span></span> | <span data-ttu-id="51d00-801">ESC \[ 1; 5 C</span><span class="sxs-lookup"><span data-stu-id="51d00-801">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="51d00-802">STRG + nach-links-Taste</span><span class="sxs-lookup"><span data-stu-id="51d00-802">Ctrl + Left Arrow</span></span>  | <span data-ttu-id="51d00-803">ESC \[ 1; 5 D</span><span class="sxs-lookup"><span data-stu-id="51d00-803">ESC \[ 1 ; 5 D</span></span> |



<span data-ttu-id="51d00-804">**Hinweis**  Left STRG + Right Alt wird als AltGr behandelt.</span><span class="sxs-lookup"><span data-stu-id="51d00-804">**Note**  Left Ctrl + Right Alt is treated as AltGr.</span></span> <span data-ttu-id="51d00-805">Wenn beide angezeigt werden, werden Sie entfernt, und der Unicode-Wert des vom System dargestellten Zeichens wird an das Ziel übermittelt.</span><span class="sxs-lookup"><span data-stu-id="51d00-805">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="51d00-806">Das System übersetzt AltGr-Werte vorab gemäß den aktuellen System Eingabeeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="51d00-806">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="51d00-807"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Stich</span><span class="sxs-lookup"><span data-stu-id="51d00-807"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="51d00-808"><span id="example"></span><span id="EXAMPLE"></span>Beispiel für SGR-Terminal Sequenzen</span><span class="sxs-lookup"><span data-stu-id="51d00-808"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="51d00-809">Der folgende Code enthält mehrere Beispiele für die Textformatierung.</span><span class="sxs-lookup"><span data-stu-id="51d00-809">The following code provides several examples of text formatting.</span></span>

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

<span data-ttu-id="51d00-810">**Hinweis**  Im vorherigen Beispiel ist die Zeichenfolge " `\x1b[31m` " die Implementierung von **ESC \[ &lt; n &gt; m** mit &lt; n &gt; 31.</span><span class="sxs-lookup"><span data-stu-id="51d00-810">**Note**  In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="51d00-811">Die folgende Grafik zeigt die Ausgabe des vorherigen Code Beispiels.</span><span class="sxs-lookup"><span data-stu-id="51d00-811">The following graphic shows the output of the previous code example.</span></span>

![Ausgabe der Konsole mit dem SGR-Befehl](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="51d00-813"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Beispiel für das Aktivieren der virtuellen Terminal Verarbeitung</span><span class="sxs-lookup"><span data-stu-id="51d00-813"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="51d00-814">Der folgende Code enthält ein Beispiel für die empfohlene Vorgehensweise zum Aktivieren der virtuellen Terminal Verarbeitung für eine Anwendung.</span><span class="sxs-lookup"><span data-stu-id="51d00-814">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="51d00-815">Das Beispiel soll Folgendes veranschaulichen:</span><span class="sxs-lookup"><span data-stu-id="51d00-815">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="51d00-816">Der vorhandene Modus sollte immer über getconsolemode abgerufen und analysiert werden, bevor er mit setconsolemode festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="51d00-816">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="51d00-817">Überprüfen, ob setconsolemode zurückgibt `0` und GetLastError den Status " \_ Ungültiger Parameter" zurückgibt \_ , ist der aktuelle Mechanismus zum Bestimmen der Ausführung auf einem System mit einer Ebene</span><span class="sxs-lookup"><span data-stu-id="51d00-817">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="51d00-818">Eine Anwendung, die den Status \_ ungültige Parameter empfängt, \_ und eine der neueren Konsolenmodus-Flags im Bitfeld, sollte das Verhalten ordnungsgemäß herabstufen und den Vorgang wiederholen.</span><span class="sxs-lookup"><span data-stu-id="51d00-818">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="51d00-819"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Beispiel für die SELECT Anniversary Update-Features</span><span class="sxs-lookup"><span data-stu-id="51d00-819"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="51d00-820">Das folgende Beispiel soll ein stabileres Codebeispiel sein, bei dem eine Reihe von Escapesequenzen zum Bearbeiten des Puffers verwendet werden, wobei der Schwerpunkt auf den Features liegt, die im Anniversary Update für Windows 10 hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="51d00-820">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="51d00-821">In diesem Beispiel wird der Alternative Bildschirm Puffer verwendet, Tabstopps werden bearbeitet, scrollränder werden festgelegt, und der Zeichensatz wird geändert.</span><span class="sxs-lookup"><span data-stu-id="51d00-821">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

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








