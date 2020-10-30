---
title: Virtuelle Konsolenterminalsequenzen
description: Virtuelle Terminal Sequenzen sind Steuerungs Zeichenfolgen, die beim Schreiben in den Ausgabestream die Cursor Bewegung, den Farb-/schriftmodus und andere Vorgänge steuern können.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: 45ee5518ec8ea2da840d2a4442efd9e0d4346526
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039148"
---
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="abd6c-104">Virtuelle Konsolenterminalsequenzen</span><span class="sxs-lookup"><span data-stu-id="abd6c-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="abd6c-105">Virtuelle Terminal Sequenzen sind Steuerungs Zeichenfolgen, die beim Schreiben in den Ausgabestream die Cursor Bewegung, den Farb-/schriftmodus und andere Vorgänge steuern können.</span><span class="sxs-lookup"><span data-stu-id="abd6c-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="abd6c-106">Sequenzen können auch als Antwort auf eine Abfrage Informations Sequenz für den Ausgabestream oder als Codierung von Benutzereingaben im Eingabedaten Strom empfangen werden, wenn der entsprechende Modus festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="abd6c-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="abd6c-107">Sie können dieses Verhalten mit [**getconsolemode**](getconsolemode.md) -und [**setconsolemode**](setconsolemode.md) -Funktionen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="abd6c-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="abd6c-108">Ein Beispiel für die empfohlene Vorgehensweise zum Aktivieren des Verhaltens von virtuellen Endgeräten finden Sie am Ende dieses Dokuments.</span><span class="sxs-lookup"><span data-stu-id="abd6c-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="abd6c-109">Das Verhalten der folgenden Sequenzen basiert auf den VT100-und abgeleiteten terminalemulatortechnologien, insbesondere dem xterm-Terminal Emulator.</span><span class="sxs-lookup"><span data-stu-id="abd6c-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="abd6c-110">Weitere Informationen zu Terminal Sequenzen finden Sie unter <http://vt100.net> und unter <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html> .</span><span class="sxs-lookup"><span data-stu-id="abd6c-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="abd6c-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Ausgabe Sequenzen</span><span class="sxs-lookup"><span data-stu-id="abd6c-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="abd6c-112">Die folgenden Terminal Sequenzen werden vom Konsolen Host abgefangen, wenn Sie in den Ausgabestream geschrieben werden, wenn das Flag zum Aktivieren der \_ virtuellen \_ Terminal \_ Verarbeitung auf dem Bildschirm Puffer Handle mithilfe der [**setconsolemode**](setconsolemode.md) -Funktion festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="abd6c-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="abd6c-113">Beachten Sie, dass das \_ \_ automatische \_ rückgabeflag zum Deaktivieren von Zeilen Vorgängen auch nützlich sein kann, um das Cursor Positions-und Bild Laufverhalten anderer Terminalemulatoren in Bezug auf Zeichen zu emulieren, die in der letzten Spalte in einer Zeile</span><span class="sxs-lookup"><span data-stu-id="abd6c-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="abd6c-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Einfache Cursor Positionierung</span><span class="sxs-lookup"><span data-stu-id="abd6c-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="abd6c-115">Bei allen folgenden Beschreibungen ist ESC immer der hexadezimale Wert 0x1B.</span><span class="sxs-lookup"><span data-stu-id="abd6c-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="abd6c-116">Es sind keine Leerzeichen in Terminal Sequenzen enthalten.</span><span class="sxs-lookup"><span data-stu-id="abd6c-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="abd6c-117">Ein Beispiel für die Verwendung dieser Sequenzen in der Praxis finden Sie im [Beispiel](#example) am Ende dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="abd6c-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="abd6c-118">In der folgenden Tabelle werden einfache Escapesequenzen mit einem einzelnen Action-Befehl direkt nach dem ESC-Zeichen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="abd6c-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="abd6c-119">Diese Sequenzen verfügen über keine Parameter und treten sofort in Kraft.</span><span class="sxs-lookup"><span data-stu-id="abd6c-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="abd6c-120">Alle Befehle in dieser Tabelle entsprechen in der Regel dem Aufrufen der [**SetConsoleCursorPosition**](setconsolecursorposition.md) -Konsolen-API, um den Cursor zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="abd6c-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="abd6c-121">Die Cursor Bewegung wird vom aktuellen Viewport in den Puffer gebunden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="abd6c-122">Der Bildlauf (falls verfügbar) erfolgt nicht.</span><span class="sxs-lookup"><span data-stu-id="abd6c-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="abd6c-123">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-123">Sequence</span></span> | <span data-ttu-id="abd6c-124">Kurzform</span><span class="sxs-lookup"><span data-stu-id="abd6c-124">Shorthand</span></span> | <span data-ttu-id="abd6c-125">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-125">Behavior</span></span> |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="abd6c-126">ESC A</span><span class="sxs-lookup"><span data-stu-id="abd6c-126">ESC A</span></span> | <span data-ttu-id="abd6c-127">Cuu</span><span class="sxs-lookup"><span data-stu-id="abd6c-127">CUU</span></span> | <span data-ttu-id="abd6c-128">Cursor nach oben um 1</span><span class="sxs-lookup"><span data-stu-id="abd6c-128">Cursor Up by 1</span></span> |
| <span data-ttu-id="abd6c-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="abd6c-129">ESC B</span></span> | <span data-ttu-id="abd6c-130">CUD</span><span class="sxs-lookup"><span data-stu-id="abd6c-130">CUD</span></span> | <span data-ttu-id="abd6c-131">Cursor nach unten um 1</span><span class="sxs-lookup"><span data-stu-id="abd6c-131">Cursor Down by 1</span></span> |
| <span data-ttu-id="abd6c-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="abd6c-132">ESC C</span></span> | <span data-ttu-id="abd6c-133">CUF</span><span class="sxs-lookup"><span data-stu-id="abd6c-133">CUF</span></span> | <span data-ttu-id="abd6c-134">Cursor vorwärts (rechts) um 1</span><span class="sxs-lookup"><span data-stu-id="abd6c-134">Cursor Forward (Right) by 1</span></span> |
| <span data-ttu-id="abd6c-135">ESC D</span><span class="sxs-lookup"><span data-stu-id="abd6c-135">ESC D</span></span> | <span data-ttu-id="abd6c-136">Cub</span><span class="sxs-lookup"><span data-stu-id="abd6c-136">CUB</span></span> | <span data-ttu-id="abd6c-137">Cursor nach hinten (links) um 1</span><span class="sxs-lookup"><span data-stu-id="abd6c-137">Cursor Backward (Left) by 1</span></span> |
| <span data-ttu-id="abd6c-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="abd6c-138">ESC M</span></span> | <span data-ttu-id="abd6c-139">RI</span><span class="sxs-lookup"><span data-stu-id="abd6c-139">RI</span></span> | <span data-ttu-id="abd6c-140">Umgekehrter Index – führt den umgekehrten Vorgang von \\ n aus, verschiebt den Cursor um eine Zeile nach oben, behält die horizontale Position bei Bedarf und scrollt den Puffer.\*</span><span class="sxs-lookup"><span data-stu-id="abd6c-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="abd6c-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="abd6c-141">ESC 7</span></span> | <span data-ttu-id="abd6c-142">Entschlüsseln</span><span class="sxs-lookup"><span data-stu-id="abd6c-142">DECSC</span></span> | <span data-ttu-id="abd6c-143">Cursor Position im Arbeitsspeicher speichern\*\*</span><span class="sxs-lookup"><span data-stu-id="abd6c-143">Save Cursor Position in Memory\*\*</span></span> |
| <span data-ttu-id="abd6c-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="abd6c-144">ESC 8</span></span> | <span data-ttu-id="abd6c-145">Decsr</span><span class="sxs-lookup"><span data-stu-id="abd6c-145">DECSR</span></span> | <span data-ttu-id="abd6c-146">Cursor Position aus dem Arbeitsspeicher wiederherstellen\*\*</span><span class="sxs-lookup"><span data-stu-id="abd6c-146">Restore Cursor Position from Memory\*\*</span></span> |



> [!NOTE]
><span data-ttu-id="abd6c-147">\* Wenn Bild Lauf Ränder festgelegt sind, führt RI innerhalb der Ränder nur einen Bildlauf durch den Inhalt der Ränder durch und lässt den Viewport unverändert.</span><span class="sxs-lookup"><span data-stu-id="abd6c-147">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="abd6c-148">(Siehe scrollränder)</span><span class="sxs-lookup"><span data-stu-id="abd6c-148">(See Scrolling Margins)</span></span>
>
><span data-ttu-id="abd6c-149">\*\*Es wird kein Wert im Arbeitsspeicher gespeichert, bis der Befehl zum Speichern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="abd6c-149">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="abd6c-150">Die einzige Möglichkeit, auf den gespeicherten Wert zuzugreifen, ist der Restore-Befehl.</span><span class="sxs-lookup"><span data-stu-id="abd6c-150">The only way to access the saved value is with the restore command.</span></span>

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="abd6c-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positionierung</span><span class="sxs-lookup"><span data-stu-id="abd6c-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="abd6c-152">In den folgenden Tabellen sind die typsequenzen von "Control Sequence Introduction" (CSI).</span><span class="sxs-lookup"><span data-stu-id="abd6c-152">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="abd6c-153">Alle CSI-Sequenzen beginnen mit ESC (0x1B), gefolgt von \[ (linker Klammer, 0x5b) und können Parameter der Variablen Länge enthalten, um für jeden Vorgang Weitere Informationen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="abd6c-153">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="abd6c-154">Dies wird durch die kurzzeitangabe &lt; dargestellt &gt; .</span><span class="sxs-lookup"><span data-stu-id="abd6c-154">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="abd6c-155">Jede Tabelle unten ist nach Funktionalität gruppiert, wobei die einzelnen Tabellen die Funktionsweise der Gruppe erläutern.</span><span class="sxs-lookup"><span data-stu-id="abd6c-155">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="abd6c-156">Für alle Parameter gelten die folgenden Regeln, sofern nichts anderes angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="abd6c-156">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="abd6c-157">&lt;n &gt; stellt den zu verschiebende Abstand dar und ist ein optionaler Parameter.</span><span class="sxs-lookup"><span data-stu-id="abd6c-157">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="abd6c-158">Wenn &lt; n &gt; weggelassen wird oder 0 (null) ist, wird er als 1 behandelt.</span><span class="sxs-lookup"><span data-stu-id="abd6c-158">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="abd6c-159">&lt;n &gt; kann nicht größer als 32.767 (maximaler Kurzwert) sein.</span><span class="sxs-lookup"><span data-stu-id="abd6c-159">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="abd6c-160">&lt;n &gt; darf nicht negativ sein.</span><span class="sxs-lookup"><span data-stu-id="abd6c-160">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="abd6c-161">Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufrufen der Konsolen-API [**SetConsoleCursorPosition**](setconsolecursorposition.md) .</span><span class="sxs-lookup"><span data-stu-id="abd6c-161">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="abd6c-162">Die Cursor Bewegung wird vom aktuellen Viewport in den Puffer gebunden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-162">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="abd6c-163">Der Bildlauf (falls verfügbar) erfolgt nicht.</span><span class="sxs-lookup"><span data-stu-id="abd6c-163">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="abd6c-164">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-164">Sequence</span></span> | <span data-ttu-id="abd6c-165">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-165">Code</span></span> | <span data-ttu-id="abd6c-166">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-166">Description</span></span> | <span data-ttu-id="abd6c-167">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-167">Behavior</span></span> |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="abd6c-168">ESC \[ &lt; n &gt; A</span><span class="sxs-lookup"><span data-stu-id="abd6c-168">ESC \[ &lt;n&gt; A</span></span> | <span data-ttu-id="abd6c-169">Cuu</span><span class="sxs-lookup"><span data-stu-id="abd6c-169">CUU</span></span> | <span data-ttu-id="abd6c-170">Cursor nach oben</span><span class="sxs-lookup"><span data-stu-id="abd6c-170">Cursor Up</span></span> | <span data-ttu-id="abd6c-171">Cursor nach oben um &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="abd6c-171">Cursor up by &lt;n&gt;</span></span> |
| <span data-ttu-id="abd6c-172">ESC \[ &lt; n &gt; B</span><span class="sxs-lookup"><span data-stu-id="abd6c-172">ESC \[ &lt;n&gt; B</span></span> | <span data-ttu-id="abd6c-173">CUD</span><span class="sxs-lookup"><span data-stu-id="abd6c-173">CUD</span></span> | <span data-ttu-id="abd6c-174">Cursor nach unten</span><span class="sxs-lookup"><span data-stu-id="abd6c-174">Cursor Down</span></span> | <span data-ttu-id="abd6c-175">Cursor nach unten um &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="abd6c-175">Cursor down by &lt;n&gt;</span></span> |
| <span data-ttu-id="abd6c-176">ESC \[ &lt; n &gt; C</span><span class="sxs-lookup"><span data-stu-id="abd6c-176">ESC \[ &lt;n&gt; C</span></span> | <span data-ttu-id="abd6c-177">CUF</span><span class="sxs-lookup"><span data-stu-id="abd6c-177">CUF</span></span> | <span data-ttu-id="abd6c-178">Cursor vorwärts</span><span class="sxs-lookup"><span data-stu-id="abd6c-178">Cursor Forward</span></span> | <span data-ttu-id="abd6c-179">Cursor vorwärts (rechts) durch &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="abd6c-179">Cursor forward (Right) by &lt;n&gt;</span></span> |
| <span data-ttu-id="abd6c-180">ESC \[ &lt; n &gt; D</span><span class="sxs-lookup"><span data-stu-id="abd6c-180">ESC \[ &lt;n&gt; D</span></span> | <span data-ttu-id="abd6c-181">Cub</span><span class="sxs-lookup"><span data-stu-id="abd6c-181">CUB</span></span> | <span data-ttu-id="abd6c-182">Cursor rückwärts</span><span class="sxs-lookup"><span data-stu-id="abd6c-182">Cursor Backward</span></span> | <span data-ttu-id="abd6c-183">Cursor rückwärts (links) durch &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="abd6c-183">Cursor backward (Left) by &lt;n&gt;</span></span> |
| <span data-ttu-id="abd6c-184">ESC \[ &lt; n &gt; E</span><span class="sxs-lookup"><span data-stu-id="abd6c-184">ESC \[ &lt;n&gt; E</span></span> | <span data-ttu-id="abd6c-185">CNL</span><span class="sxs-lookup"><span data-stu-id="abd6c-185">CNL</span></span> | <span data-ttu-id="abd6c-186">Cursor-nächste Zeile</span><span class="sxs-lookup"><span data-stu-id="abd6c-186">Cursor Next Line</span></span> | <span data-ttu-id="abd6c-187">Cursor nach unten &lt; n &gt; Zeilen von der aktuellen Position</span><span class="sxs-lookup"><span data-stu-id="abd6c-187">Cursor down &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="abd6c-188">ESC \[ &lt; n &gt; F</span><span class="sxs-lookup"><span data-stu-id="abd6c-188">ESC \[ &lt;n&gt; F</span></span> | <span data-ttu-id="abd6c-189">CPL</span><span class="sxs-lookup"><span data-stu-id="abd6c-189">CPL</span></span> | <span data-ttu-id="abd6c-190">Vorherige Cursor Zeile</span><span class="sxs-lookup"><span data-stu-id="abd6c-190">Cursor Previous Line</span></span> | <span data-ttu-id="abd6c-191">Cursor &lt; nach oben n &gt; Zeilen von der aktuellen Position</span><span class="sxs-lookup"><span data-stu-id="abd6c-191">Cursor up &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="abd6c-192">ESC \[ &lt; n &gt; G</span><span class="sxs-lookup"><span data-stu-id="abd6c-192">ESC \[ &lt;n&gt; G</span></span> | <span data-ttu-id="abd6c-193">CHA</span><span class="sxs-lookup"><span data-stu-id="abd6c-193">CHA</span></span> | <span data-ttu-id="abd6c-194">Cursor horizontal absolut</span><span class="sxs-lookup"><span data-stu-id="abd6c-194">Cursor Horizontal Absolute</span></span> | <span data-ttu-id="abd6c-195">Der Cursor wechselt an &lt; die n-te &gt; Position horizontal in der aktuellen Zeile.</span><span class="sxs-lookup"><span data-stu-id="abd6c-195">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span> |
| <span data-ttu-id="abd6c-196">ESC \[ &lt; n &gt; d</span><span class="sxs-lookup"><span data-stu-id="abd6c-196">ESC \[ &lt;n&gt; d</span></span> | <span data-ttu-id="abd6c-197">VPA</span><span class="sxs-lookup"><span data-stu-id="abd6c-197">VPA</span></span> | <span data-ttu-id="abd6c-198">Vertikale Zeilen Position absolut</span><span class="sxs-lookup"><span data-stu-id="abd6c-198">Vertical Line Position Absolute</span></span> | <span data-ttu-id="abd6c-199">Der Cursor wechselt an die n-te &lt; &gt; Position vertikal in der aktuellen Spalte.</span><span class="sxs-lookup"><span data-stu-id="abd6c-199">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span> |
| <span data-ttu-id="abd6c-200">ESC \[ &lt; y &gt; ; &lt; x &gt; H</span><span class="sxs-lookup"><span data-stu-id="abd6c-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="abd6c-201">Pokalsieg</span><span class="sxs-lookup"><span data-stu-id="abd6c-201">CUP</span></span> | <span data-ttu-id="abd6c-202">Cursor Position</span><span class="sxs-lookup"><span data-stu-id="abd6c-202">Cursor Position</span></span> | <span data-ttu-id="abd6c-203">\*Cursor wechselt zu &lt; x &gt; ; &lt; y- &gt; Koordinate innerhalb des Viewports, wobei &lt; x für &gt; die Spalte der &lt; y- &gt; Zeile steht.</span><span class="sxs-lookup"><span data-stu-id="abd6c-203">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="abd6c-204">ESC \[ &lt; y &gt; ; &lt; × &gt; f</span><span class="sxs-lookup"><span data-stu-id="abd6c-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="abd6c-205">HVP</span><span class="sxs-lookup"><span data-stu-id="abd6c-205">HVP</span></span> | <span data-ttu-id="abd6c-206">Horizontale vertikale Position</span><span class="sxs-lookup"><span data-stu-id="abd6c-206">Horizontal Vertical Position</span></span> | <span data-ttu-id="abd6c-207">\*Cursor wechselt zu &lt; x &gt; ; &lt; y- &gt; Koordinate innerhalb des Viewports, wobei &lt; x für &gt; die Spalte der &lt; y- &gt; Zeile steht.</span><span class="sxs-lookup"><span data-stu-id="abd6c-207">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="abd6c-208">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="abd6c-208">ESC \[ s</span></span> | <span data-ttu-id="abd6c-209">Ansisyssc</span><span class="sxs-lookup"><span data-stu-id="abd6c-209">ANSISYSSC</span></span> | <span data-ttu-id="abd6c-210">Cursor – Ansi.sys Emulation speichern</span><span class="sxs-lookup"><span data-stu-id="abd6c-210">Save Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="abd6c-211">\*\*Ohne Parameter führt einen Vorgang zum Speichern eines Cursors aus, z. b. decsc.</span><span class="sxs-lookup"><span data-stu-id="abd6c-211">\*\*With no parameters, performs a save cursor operation like DECSC</span></span> |
| <span data-ttu-id="abd6c-212">ESC \[ u</span><span class="sxs-lookup"><span data-stu-id="abd6c-212">ESC \[ u</span></span> | <span data-ttu-id="abd6c-213">Ansisyssc</span><span class="sxs-lookup"><span data-stu-id="abd6c-213">ANSISYSSC</span></span> | <span data-ttu-id="abd6c-214">Restore Cursor – Ansi.sys Emulation</span><span class="sxs-lookup"><span data-stu-id="abd6c-214">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="abd6c-215">\*\*Ohne Parameter führt einen Restore-Cursor Vorgang wie decrc aus.</span><span class="sxs-lookup"><span data-stu-id="abd6c-215">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span> |



> [!NOTE]
><span data-ttu-id="abd6c-216">\*&lt;x &gt; -und &lt; y- &gt; Parameter haben dieselben Einschränkungen wie &lt; n &gt; oben.</span><span class="sxs-lookup"><span data-stu-id="abd6c-216">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="abd6c-217">Wenn &lt; x &gt; und &lt; y &gt; ausgelassen werden, werden Sie auf 1 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="abd6c-217">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>
>
><span data-ttu-id="abd6c-218">\*\*ANSI.sys Verlaufs Dokumentation finden Sie unter <https://msdn.microsoft.com/library/cc722862.aspx> und wird aus Gründen der Handhabung und Kompatibilität implementiert.</span><span class="sxs-lookup"><span data-stu-id="abd6c-218">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="abd6c-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Sichtbarkeit</span><span class="sxs-lookup"><span data-stu-id="abd6c-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="abd6c-220">Die folgenden Befehle steuern die Sichtbarkeit des Cursors und den blinkende Zustand.</span><span class="sxs-lookup"><span data-stu-id="abd6c-220">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="abd6c-221">Die dectcem-Sequenzen entsprechen in der Regel der aufrufenden [**setconsolecursorinfo**](setconsolecursorinfo.md) -Konsolen-API zum Umschalten der Cursor Sichtbarkeit.</span><span class="sxs-lookup"><span data-stu-id="abd6c-221">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="abd6c-222">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-222">Sequence</span></span> | <span data-ttu-id="abd6c-223">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-223">Code</span></span> | <span data-ttu-id="abd6c-224">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-224">Description</span></span> | <span data-ttu-id="abd6c-225">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-225">Behavior</span></span> |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="abd6c-226">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="abd6c-226">ESC \[ ?</span></span> <span data-ttu-id="abd6c-227">12 Stunden</span><span class="sxs-lookup"><span data-stu-id="abd6c-227">12 h</span></span> | <span data-ttu-id="abd6c-228">ATT160</span><span class="sxs-lookup"><span data-stu-id="abd6c-228">ATT160</span></span> | <span data-ttu-id="abd6c-229">Text Cursor Aktivierung blinkt</span><span class="sxs-lookup"><span data-stu-id="abd6c-229">Text Cursor Enable Blinking</span></span> | <span data-ttu-id="abd6c-230">Cursor blinkt</span><span class="sxs-lookup"><span data-stu-id="abd6c-230">Start the cursor blinking</span></span> |
| <span data-ttu-id="abd6c-231">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="abd6c-231">ESC \[ ?</span></span> <span data-ttu-id="abd6c-232">12 l</span><span class="sxs-lookup"><span data-stu-id="abd6c-232">12 l</span></span> | <span data-ttu-id="abd6c-233">ATT160</span><span class="sxs-lookup"><span data-stu-id="abd6c-233">ATT160</span></span> | <span data-ttu-id="abd6c-234">Blinken des Text Cursors deaktivieren</span><span class="sxs-lookup"><span data-stu-id="abd6c-234">Text Cursor Disable Blinking</span></span> | <span data-ttu-id="abd6c-235">Blinkt den Cursor nicht mehr</span><span class="sxs-lookup"><span data-stu-id="abd6c-235">Stop blinking the cursor</span></span> |
| <span data-ttu-id="abd6c-236">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="abd6c-236">ESC \[ ?</span></span> <span data-ttu-id="abd6c-237">25 h</span><span class="sxs-lookup"><span data-stu-id="abd6c-237">25 h</span></span> | <span data-ttu-id="abd6c-238">Dectcem</span><span class="sxs-lookup"><span data-stu-id="abd6c-238">DECTCEM</span></span> | <span data-ttu-id="abd6c-239">Text Cursor Aktivierungs Modus anzeigen</span><span class="sxs-lookup"><span data-stu-id="abd6c-239">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="abd6c-240">Cursor anzeigen</span><span class="sxs-lookup"><span data-stu-id="abd6c-240">Show the cursor</span></span> |
| <span data-ttu-id="abd6c-241">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="abd6c-241">ESC \[ ?</span></span> <span data-ttu-id="abd6c-242">25 l</span><span class="sxs-lookup"><span data-stu-id="abd6c-242">25 l</span></span> | <span data-ttu-id="abd6c-243">Dectcem</span><span class="sxs-lookup"><span data-stu-id="abd6c-243">DECTCEM</span></span> | <span data-ttu-id="abd6c-244">Modus "Text Cursor aktivieren" ausblenden</span><span class="sxs-lookup"><span data-stu-id="abd6c-244">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="abd6c-245">Cursor ausblenden</span><span class="sxs-lookup"><span data-stu-id="abd6c-245">Hide the cursor</span></span> |

> [!TIP]
> <span data-ttu-id="abd6c-246">Die Aktivierungs Sequenzen enden in einem Kleinbuchstaben-H-Zeichen ( `h` ), und die Deaktivierungs Sequenzen enden in einem Kleinbuchstaben-L-Zeichen ( `l` ).</span><span class="sxs-lookup"><span data-stu-id="abd6c-246">The enable sequences end in a lowercase H character (`h`) and the disable sequences end in a lowercase L character (`l`).</span></span>

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="abd6c-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Positionieren von Viewports</span><span class="sxs-lookup"><span data-stu-id="abd6c-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="abd6c-248">Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufrufen der [**scrollconsolescreenbuffer**](scrollconsolescreenbuffer.md) -Konsolen-API, um den Inhalt des Konsolen Puffers zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="abd6c-248">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="abd6c-249">**Vorsicht** Die Befehlsnamen sind irreführend.</span><span class="sxs-lookup"><span data-stu-id="abd6c-249">**Caution** The command names are misleading.</span></span> <span data-ttu-id="abd6c-250">Scroll bezieht sich auf die Richtung, in die der Text während des Vorgangs verschoben wird, nicht auf die Art und Weise, in der der Viewport verschoben werden würde</span><span class="sxs-lookup"><span data-stu-id="abd6c-250">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="abd6c-251">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-251">Sequence</span></span> | <span data-ttu-id="abd6c-252">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-252">Code</span></span> | <span data-ttu-id="abd6c-253">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-253">Description</span></span> | <span data-ttu-id="abd6c-254">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-254">Behavior</span></span> |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="abd6c-255">ESC \[ &lt; n &gt; S</span><span class="sxs-lookup"><span data-stu-id="abd6c-255">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="abd6c-256">SU</span><span class="sxs-lookup"><span data-stu-id="abd6c-256">SU</span></span> | <span data-ttu-id="abd6c-257">Bildlauf nach oben</span><span class="sxs-lookup"><span data-stu-id="abd6c-257">Scroll Up</span></span> | <span data-ttu-id="abd6c-258">Bildlauf nach oben um &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="abd6c-258">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="abd6c-259">Auch als "Pan Down" bezeichnet, werden neue Zeilen unten auf dem Bildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="abd6c-259">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="abd6c-260">ESC \[ &lt; n &gt; T</span><span class="sxs-lookup"><span data-stu-id="abd6c-260">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="abd6c-261">SD</span><span class="sxs-lookup"><span data-stu-id="abd6c-261">SD</span></span> | <span data-ttu-id="abd6c-262">Bildlauf nach unten</span><span class="sxs-lookup"><span data-stu-id="abd6c-262">Scroll Down</span></span> | <span data-ttu-id="abd6c-263">Scrollen Sie nach unten um &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="abd6c-263">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="abd6c-264">Auch als "schwenken" bezeichnet, werden neue Zeilen am oberen Rand des Bildschirms angezeigt.</span><span class="sxs-lookup"><span data-stu-id="abd6c-264">Also known as pan up, new lines fill in from the top of the screen</span></span> |



<span data-ttu-id="abd6c-265">Der Text wird beginnend mit der Zeile verschoben, in der sich der Cursor befindet.</span><span class="sxs-lookup"><span data-stu-id="abd6c-265">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="abd6c-266">Wenn sich der Cursor in der mittleren Zeile des Viewports befindet, verschiebt der Bildlauf nach oben die untere Hälfte des Viewports und fügt unten leere Zeilen ein.</span><span class="sxs-lookup"><span data-stu-id="abd6c-266">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="abd6c-267">Scrollen Sie nach unten, um die obere Hälfte der Zeilen des Viewports zu verschieben, und fügen Sie oben neue Zeilen ein.</span><span class="sxs-lookup"><span data-stu-id="abd6c-267">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="abd6c-268">Wichtig zu beachten ist, dass der Bildlauf nach oben und unten auch durch die scrollränder beeinträchtigt wird.</span><span class="sxs-lookup"><span data-stu-id="abd6c-268">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="abd6c-269">Ein Bildlauf nach oben und unten wirkt sich nicht auf Zeilen außerhalb der scrollränder aus.</span><span class="sxs-lookup"><span data-stu-id="abd6c-269">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="abd6c-270">Der Standardwert für &lt; n &gt; ist 1, und der Wert kann optional ausgelassen werden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-270">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="abd6c-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Änderung</span><span class="sxs-lookup"><span data-stu-id="abd6c-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="abd6c-272">Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufruf von [**fillconsoleoutputcharacter**](fillconsoleoutputcharacter.md)-, [**fillconsoleoutputattribute**](fillconsoleoutputattribute.md)-und [**scrollconsolescreenbuffer**](scrollconsolescreenbuffer.md) -Konsolen-APIs, um den Inhalt des Text Puffers zu ändern.</span><span class="sxs-lookup"><span data-stu-id="abd6c-272">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="abd6c-273">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-273">Sequence</span></span> | <span data-ttu-id="abd6c-274">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-274">Code</span></span> | <span data-ttu-id="abd6c-275">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-275">Description</span></span> | <span data-ttu-id="abd6c-276">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-276">Behavior</span></span> |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="abd6c-277">ESC \[ &lt; n&gt; @</span><span class="sxs-lookup"><span data-stu-id="abd6c-277">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="abd6c-278">Reichen</span><span class="sxs-lookup"><span data-stu-id="abd6c-278">ICH</span></span> | <span data-ttu-id="abd6c-279">Zeichen einfügen</span><span class="sxs-lookup"><span data-stu-id="abd6c-279">Insert Character</span></span> | <span data-ttu-id="abd6c-280">Fügen &lt; &gt; Sie n Leerzeichen an der aktuellen Cursorposition ein, und verschieben Sie den gesamten vorhandenen Text nach rechts.</span><span class="sxs-lookup"><span data-stu-id="abd6c-280">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="abd6c-281">Der Text, der den Bildschirm rechts verlässt, wird entfernt.</span><span class="sxs-lookup"><span data-stu-id="abd6c-281">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="abd6c-282">ESC \[ &lt; n &gt; P</span><span class="sxs-lookup"><span data-stu-id="abd6c-282">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="abd6c-283">DCH</span><span class="sxs-lookup"><span data-stu-id="abd6c-283">DCH</span></span> | <span data-ttu-id="abd6c-284">Zeichen löschen</span><span class="sxs-lookup"><span data-stu-id="abd6c-284">Delete Character</span></span> | <span data-ttu-id="abd6c-285">Löschen Sie &lt; n &gt; Zeichen an der aktuellen Cursorposition, und verschieben Sie die Leerzeichen vom rechten Rand des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="abd6c-285">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span> |
| <span data-ttu-id="abd6c-286">ESC \[ &lt; n &gt; X</span><span class="sxs-lookup"><span data-stu-id="abd6c-286">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="abd6c-287">E</span><span class="sxs-lookup"><span data-stu-id="abd6c-287">ECH</span></span> | <span data-ttu-id="abd6c-288">Löschzeichen</span><span class="sxs-lookup"><span data-stu-id="abd6c-288">Erase Character</span></span> | <span data-ttu-id="abd6c-289">Löschen &lt; &gt; Sie n Zeichen aus der aktuellen Cursorposition, indem Sie Sie mit einem Leerzeichen überschreiben.</span><span class="sxs-lookup"><span data-stu-id="abd6c-289">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span> |
| <span data-ttu-id="abd6c-290">ESC \[ &lt; n &gt; L</span><span class="sxs-lookup"><span data-stu-id="abd6c-290">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="abd6c-291">IL</span><span class="sxs-lookup"><span data-stu-id="abd6c-291">IL</span></span> | <span data-ttu-id="abd6c-292">Zeile einfügen</span><span class="sxs-lookup"><span data-stu-id="abd6c-292">Insert Line</span></span> | <span data-ttu-id="abd6c-293">Fügt &lt; n &gt; Zeilen an der Cursorposition in den Puffer ein.</span><span class="sxs-lookup"><span data-stu-id="abd6c-293">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="abd6c-294">Die Zeile, in der sich der Cursor befindet, und die darunter liegenden Zeilen werden nach unten verschoben.</span><span class="sxs-lookup"><span data-stu-id="abd6c-294">The line the cursor is on, and lines below it, will be shifted downwards.</span></span> |
| <span data-ttu-id="abd6c-295">ESC \[ &lt; n &gt; M</span><span class="sxs-lookup"><span data-stu-id="abd6c-295">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="abd6c-296">DL</span><span class="sxs-lookup"><span data-stu-id="abd6c-296">DL</span></span> | <span data-ttu-id="abd6c-297">Zeile löschen</span><span class="sxs-lookup"><span data-stu-id="abd6c-297">Delete Line</span></span> | <span data-ttu-id="abd6c-298">Löscht &lt; n &gt; Zeilen aus dem Puffer, beginnend mit der Zeile, in der sich der Cursor befindet.</span><span class="sxs-lookup"><span data-stu-id="abd6c-298">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span> |



> [!NOTE]
><span data-ttu-id="abd6c-299">Für Il und DL sind nur die Zeilen in den scrollrändern betroffen (siehe scrollränder).</span><span class="sxs-lookup"><span data-stu-id="abd6c-299">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="abd6c-300">Wenn keine Ränder festgelegt sind, sind die Standardrand Ränder der aktuelle Viewport.</span><span class="sxs-lookup"><span data-stu-id="abd6c-300">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="abd6c-301">Wenn Linien unter die Ränder verschoben werden, werden Sie verworfen.</span><span class="sxs-lookup"><span data-stu-id="abd6c-301">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="abd6c-302">Wenn Zeilen gelöscht werden, werden am unteren Rand der Ränder leere Zeilen eingefügt, ohne dass Zeilen von außerhalb des Viewports betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="abd6c-302">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="abd6c-303">Der Standardwert für n, wenn der Wert &lt; &gt; weggelassen wird, ist 0 (null).</span><span class="sxs-lookup"><span data-stu-id="abd6c-303">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="abd6c-304">Für die folgenden Befehle weist der Parameter &lt; n &gt; drei gültige Werte auf:</span><span class="sxs-lookup"><span data-stu-id="abd6c-304">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="abd6c-305">0 löscht von der aktuellen Cursorposition (einschließlich) bis zum Ende der Zeile/Anzeige.</span><span class="sxs-lookup"><span data-stu-id="abd6c-305">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="abd6c-306">1 löscht am Anfang der Zeile/Anzeige bis einschließlich der aktuellen Cursorposition.</span><span class="sxs-lookup"><span data-stu-id="abd6c-306">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="abd6c-307">2 löscht die gesamte Zeile/Anzeige.</span><span class="sxs-lookup"><span data-stu-id="abd6c-307">2 erases the entire line/display</span></span>


| <span data-ttu-id="abd6c-308">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-308">Sequence</span></span> | <span data-ttu-id="abd6c-309">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-309">Code</span></span> | <span data-ttu-id="abd6c-310">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-310">Description</span></span> | <span data-ttu-id="abd6c-311">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-311">Behavior</span></span> |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="abd6c-312">ESC \[ &lt; n &gt; J</span><span class="sxs-lookup"><span data-stu-id="abd6c-312">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="abd6c-313">ED</span><span class="sxs-lookup"><span data-stu-id="abd6c-313">ED</span></span> | <span data-ttu-id="abd6c-314">In Anzeige löschen</span><span class="sxs-lookup"><span data-stu-id="abd6c-314">Erase in Display</span></span> | <span data-ttu-id="abd6c-315">Ersetzt den gesamten Text im aktuellen Viewport/Bildschirm, der durch n angegeben ist, &lt; &gt; durch Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="abd6c-315">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="abd6c-316">ESC \[ &lt; n &gt; K</span><span class="sxs-lookup"><span data-stu-id="abd6c-316">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="abd6c-317">Tanken</span><span class="sxs-lookup"><span data-stu-id="abd6c-317">EL</span></span> | <span data-ttu-id="abd6c-318">In Zeile löschen</span><span class="sxs-lookup"><span data-stu-id="abd6c-318">Erase in Line</span></span> | <span data-ttu-id="abd6c-319">Ersetzt den gesamten Text in der Zeile durch den durch n angegebenen Cursor &lt; &gt; mit Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="abd6c-319">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span> |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="abd6c-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatierung</span><span class="sxs-lookup"><span data-stu-id="abd6c-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="abd6c-321">Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufrufen von [**SetConsoleTextAttribute**](setconsoletextattribute.md) -Konsolen-APIs, um die Formatierung aller zukünftigen Schreibvorgänge in den Konsolenausgabe Text Puffer anzupassen.</span><span class="sxs-lookup"><span data-stu-id="abd6c-321">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="abd6c-322">Dieser Befehl ist ein besonderes Zeichen, da die &lt; n &gt; -Position unten zwischen 0 und 16 durch Semikolons getrennte Parameter annehmen kann.</span><span class="sxs-lookup"><span data-stu-id="abd6c-322">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="abd6c-323">Wenn keine Parameter angegeben werden, wird diese wie ein einzelner 0-Parameter behandelt.</span><span class="sxs-lookup"><span data-stu-id="abd6c-323">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="abd6c-324">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-324">Sequence</span></span> | <span data-ttu-id="abd6c-325">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-325">Code</span></span> | <span data-ttu-id="abd6c-326">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-326">Description</span></span> | <span data-ttu-id="abd6c-327">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-327">Behavior</span></span> |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="abd6c-328">ESC \[ &lt; n &gt; m</span><span class="sxs-lookup"><span data-stu-id="abd6c-328">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="abd6c-329">SGR</span><span class="sxs-lookup"><span data-stu-id="abd6c-329">SGR</span></span> | <span data-ttu-id="abd6c-330">Grafikwiedergabe festlegen</span><span class="sxs-lookup"><span data-stu-id="abd6c-330">Set Graphics Rendition</span></span> | <span data-ttu-id="abd6c-331">Legen Sie das Format des Bildschirms und des Texts gemäß Angabe durch n fest. &lt;&gt;</span><span class="sxs-lookup"><span data-stu-id="abd6c-331">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="abd6c-332">Die folgende Tabelle mit Werten kann in &lt; n &gt; zur Darstellung unterschiedlicher Formatierungs Modi verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-332">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="abd6c-333">Formatierungs Modi werden von links nach rechts angewendet.</span><span class="sxs-lookup"><span data-stu-id="abd6c-333">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="abd6c-334">Wenn Sie konkurrierende Formatierungsoptionen anwenden, führt dies dazu, dass die Rechte Option Vorrang hat.</span><span class="sxs-lookup"><span data-stu-id="abd6c-334">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="abd6c-335">Für Optionen, die Farben angeben, werden die Farben entsprechend der Definition in der Konsolen Farbtabelle verwendet, die mit der [**setconsoleskreenbufferinfoex**](setconsolescreenbufferinfoex.md) -API geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="abd6c-335">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="abd6c-336">Wenn die Tabelle so geändert wird, dass die "Blaue" Position in der Tabelle den RGB-Farbton rot anzeigt, werden alle Aufrufe an **Vordergrund blau** die rote Farbe anzeigen, bis Sie anderweitig geändert werden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-336">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="abd6c-337">Wert</span><span class="sxs-lookup"><span data-stu-id="abd6c-337">Value</span></span> | <span data-ttu-id="abd6c-338">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-338">Description</span></span> | <span data-ttu-id="abd6c-339">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-339">Behavior</span></span> |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="abd6c-340">0</span><span class="sxs-lookup"><span data-stu-id="abd6c-340">0</span></span> | <span data-ttu-id="abd6c-341">Standard</span><span class="sxs-lookup"><span data-stu-id="abd6c-341">Default</span></span> | <span data-ttu-id="abd6c-342">Gibt vor der Änderung alle Attribute in den Standardzustand zurück.</span><span class="sxs-lookup"><span data-stu-id="abd6c-342">Returns all attributes to the default state prior to modification</span></span> |
| <span data-ttu-id="abd6c-343">1</span><span class="sxs-lookup"><span data-stu-id="abd6c-343">1</span></span> | <span data-ttu-id="abd6c-344">Fett/hell</span><span class="sxs-lookup"><span data-stu-id="abd6c-344">Bold/Bright</span></span> | <span data-ttu-id="abd6c-345">Wendet das Flag für Helligkeit/Intensität auf Vordergrundfarbe an</span><span class="sxs-lookup"><span data-stu-id="abd6c-345">Applies brightness/intensity flag to foreground color</span></span> |
| <span data-ttu-id="abd6c-346">4</span><span class="sxs-lookup"><span data-stu-id="abd6c-346">4</span></span> | <span data-ttu-id="abd6c-347">Underline</span><span class="sxs-lookup"><span data-stu-id="abd6c-347">Underline</span></span> | <span data-ttu-id="abd6c-348">Fügt Unterstreichung hinzu</span><span class="sxs-lookup"><span data-stu-id="abd6c-348">Adds underline</span></span> |
| <span data-ttu-id="abd6c-349">24</span><span class="sxs-lookup"><span data-stu-id="abd6c-349">24</span></span> | <span data-ttu-id="abd6c-350">Keine Unterstreichung</span><span class="sxs-lookup"><span data-stu-id="abd6c-350">No underline</span></span> | <span data-ttu-id="abd6c-351">Entfernt Unterstreichung</span><span class="sxs-lookup"><span data-stu-id="abd6c-351">Removes underline</span></span> |
| <span data-ttu-id="abd6c-352">7</span><span class="sxs-lookup"><span data-stu-id="abd6c-352">7</span></span> | <span data-ttu-id="abd6c-353">Negativ</span><span class="sxs-lookup"><span data-stu-id="abd6c-353">Negative</span></span> | <span data-ttu-id="abd6c-354">Vertauscht Vordergrund-und Hintergrundfarben</span><span class="sxs-lookup"><span data-stu-id="abd6c-354">Swaps foreground and background colors</span></span> |
| <span data-ttu-id="abd6c-355">27</span><span class="sxs-lookup"><span data-stu-id="abd6c-355">27</span></span> | <span data-ttu-id="abd6c-356">Positiv (keine negative)</span><span class="sxs-lookup"><span data-stu-id="abd6c-356">Positive (No negative)</span></span> | <span data-ttu-id="abd6c-357">Gibt Vordergrund/Hintergrund für normal zurück</span><span class="sxs-lookup"><span data-stu-id="abd6c-357">Returns foreground/background to normal</span></span> |
| <span data-ttu-id="abd6c-358">30</span><span class="sxs-lookup"><span data-stu-id="abd6c-358">30</span></span> | <span data-ttu-id="abd6c-359">Vordergrund schwarz</span><span class="sxs-lookup"><span data-stu-id="abd6c-359">Foreground Black</span></span> | <span data-ttu-id="abd6c-360">Gilt für den Vordergrund ohne Fett/Hellschwarz.</span><span class="sxs-lookup"><span data-stu-id="abd6c-360">Applies non-bold/bright black to foreground</span></span> |
| <span data-ttu-id="abd6c-361">31</span><span class="sxs-lookup"><span data-stu-id="abd6c-361">31</span></span> | <span data-ttu-id="abd6c-362">Vordergrund rot</span><span class="sxs-lookup"><span data-stu-id="abd6c-362">Foreground Red</span></span> | <span data-ttu-id="abd6c-363">Gilt für den Vordergrund ohne Fett/hellrot.</span><span class="sxs-lookup"><span data-stu-id="abd6c-363">Applies non-bold/bright red to foreground</span></span> |
| <span data-ttu-id="abd6c-364">32</span><span class="sxs-lookup"><span data-stu-id="abd6c-364">32</span></span> | <span data-ttu-id="abd6c-365">Vordergrund grün</span><span class="sxs-lookup"><span data-stu-id="abd6c-365">Foreground Green</span></span> | <span data-ttu-id="abd6c-366">Gilt für den Vordergrund ohne Fett/hellgrün.</span><span class="sxs-lookup"><span data-stu-id="abd6c-366">Applies non-bold/bright green to foreground</span></span> |
| <span data-ttu-id="abd6c-367">33</span><span class="sxs-lookup"><span data-stu-id="abd6c-367">33</span></span> | <span data-ttu-id="abd6c-368">Vordergrund gelb</span><span class="sxs-lookup"><span data-stu-id="abd6c-368">Foreground Yellow</span></span> | <span data-ttu-id="abd6c-369">Gilt für den Vordergrund ohne Fett/hellgelb.</span><span class="sxs-lookup"><span data-stu-id="abd6c-369">Applies non-bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="abd6c-370">34</span><span class="sxs-lookup"><span data-stu-id="abd6c-370">34</span></span> | <span data-ttu-id="abd6c-371">Vordergrund blau</span><span class="sxs-lookup"><span data-stu-id="abd6c-371">Foreground Blue</span></span> | <span data-ttu-id="abd6c-372">Gilt für den Vordergrund ohne Fett/hellblau.</span><span class="sxs-lookup"><span data-stu-id="abd6c-372">Applies non-bold/bright blue to foreground</span></span> |
| <span data-ttu-id="abd6c-373">35</span><span class="sxs-lookup"><span data-stu-id="abd6c-373">35</span></span> | <span data-ttu-id="abd6c-374">Vordergrund Magenta</span><span class="sxs-lookup"><span data-stu-id="abd6c-374">Foreground Magenta</span></span> | <span data-ttu-id="abd6c-375">Wendet nicht Fett/hellgrün auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-375">Applies non-bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="abd6c-376">36</span><span class="sxs-lookup"><span data-stu-id="abd6c-376">36</span></span> | <span data-ttu-id="abd6c-377">Vordergrund-Cyan</span><span class="sxs-lookup"><span data-stu-id="abd6c-377">Foreground Cyan</span></span> | <span data-ttu-id="abd6c-378">Wendet nicht Fett/hell Zyan auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-378">Applies non-bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="abd6c-379">37</span><span class="sxs-lookup"><span data-stu-id="abd6c-379">37</span></span> | <span data-ttu-id="abd6c-380">Vordergrund weiß</span><span class="sxs-lookup"><span data-stu-id="abd6c-380">Foreground White</span></span> | <span data-ttu-id="abd6c-381">Wendet nicht Fett/hell weiß auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-381">Applies non-bold/bright white to foreground</span></span> |
| <span data-ttu-id="abd6c-382">38</span><span class="sxs-lookup"><span data-stu-id="abd6c-382">38</span></span> | <span data-ttu-id="abd6c-383">Vordergrund erweitert</span><span class="sxs-lookup"><span data-stu-id="abd6c-383">Foreground Extended</span></span> | <span data-ttu-id="abd6c-384">Wendet den erweiterten Farbwert auf den Vordergrund an (Weitere Informationen finden Sie unten).</span><span class="sxs-lookup"><span data-stu-id="abd6c-384">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="abd6c-385">39</span><span class="sxs-lookup"><span data-stu-id="abd6c-385">39</span></span> | <span data-ttu-id="abd6c-386">Vordergrund Standard</span><span class="sxs-lookup"><span data-stu-id="abd6c-386">Foreground Default</span></span> | <span data-ttu-id="abd6c-387">Wendet nur den Vordergrund-Teil der Standardwerte an (siehe 0).</span><span class="sxs-lookup"><span data-stu-id="abd6c-387">Applies only the foreground portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="abd6c-388">40</span><span class="sxs-lookup"><span data-stu-id="abd6c-388">40</span></span> | <span data-ttu-id="abd6c-389">Hintergrund schwarz</span><span class="sxs-lookup"><span data-stu-id="abd6c-389">Background Black</span></span> | <span data-ttu-id="abd6c-390">Gilt für den Hintergrund "nicht Fett/Hellschwarz".</span><span class="sxs-lookup"><span data-stu-id="abd6c-390">Applies non-bold/bright black to background</span></span> |
| <span data-ttu-id="abd6c-391">41</span><span class="sxs-lookup"><span data-stu-id="abd6c-391">41</span></span> | <span data-ttu-id="abd6c-392">Roter Hintergrund</span><span class="sxs-lookup"><span data-stu-id="abd6c-392">Background Red</span></span> | <span data-ttu-id="abd6c-393">Gilt für den Hintergrund "nicht Fett/hell"</span><span class="sxs-lookup"><span data-stu-id="abd6c-393">Applies non-bold/bright red to background</span></span> |
| <span data-ttu-id="abd6c-394">42</span><span class="sxs-lookup"><span data-stu-id="abd6c-394">42</span></span> | <span data-ttu-id="abd6c-395">Hintergrund grün</span><span class="sxs-lookup"><span data-stu-id="abd6c-395">Background Green</span></span> | <span data-ttu-id="abd6c-396">Gilt für den Hintergrund "nicht Fett/hellgrün"</span><span class="sxs-lookup"><span data-stu-id="abd6c-396">Applies non-bold/bright green to background</span></span> |
| <span data-ttu-id="abd6c-397">43</span><span class="sxs-lookup"><span data-stu-id="abd6c-397">43</span></span> | <span data-ttu-id="abd6c-398">Hintergrund Gelb</span><span class="sxs-lookup"><span data-stu-id="abd6c-398">Background Yellow</span></span> | <span data-ttu-id="abd6c-399">Gilt für den Hintergrund "nicht Fett/hell gelb"</span><span class="sxs-lookup"><span data-stu-id="abd6c-399">Applies non-bold/bright yellow to background</span></span> |
| <span data-ttu-id="abd6c-400">44</span><span class="sxs-lookup"><span data-stu-id="abd6c-400">44</span></span> | <span data-ttu-id="abd6c-401">Hintergrund blau</span><span class="sxs-lookup"><span data-stu-id="abd6c-401">Background Blue</span></span> | <span data-ttu-id="abd6c-402">Gilt für den Hintergrund "nicht Fett/hellblau".</span><span class="sxs-lookup"><span data-stu-id="abd6c-402">Applies non-bold/bright blue to background</span></span> |
| <span data-ttu-id="abd6c-403">45</span><span class="sxs-lookup"><span data-stu-id="abd6c-403">45</span></span> | <span data-ttu-id="abd6c-404">Hintergrund Magenta</span><span class="sxs-lookup"><span data-stu-id="abd6c-404">Background Magenta</span></span> | <span data-ttu-id="abd6c-405">Wendet nicht Fett/hell auf den Hintergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-405">Applies non-bold/bright magenta to background</span></span> |
| <span data-ttu-id="abd6c-406">46</span><span class="sxs-lookup"><span data-stu-id="abd6c-406">46</span></span> | <span data-ttu-id="abd6c-407">Background Cyan</span><span class="sxs-lookup"><span data-stu-id="abd6c-407">Background Cyan</span></span> | <span data-ttu-id="abd6c-408">Wendet nicht Fett/hell Zyan auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="abd6c-408">Applies non-bold/bright cyan to background</span></span> |
| <span data-ttu-id="abd6c-409">47</span><span class="sxs-lookup"><span data-stu-id="abd6c-409">47</span></span> | <span data-ttu-id="abd6c-410">Hintergrund weiß</span><span class="sxs-lookup"><span data-stu-id="abd6c-410">Background White</span></span> | <span data-ttu-id="abd6c-411">Gilt für den Hintergrund "nicht Fett/hell weiß".</span><span class="sxs-lookup"><span data-stu-id="abd6c-411">Applies non-bold/bright white to background</span></span> |
| <span data-ttu-id="abd6c-412">48</span><span class="sxs-lookup"><span data-stu-id="abd6c-412">48</span></span> | <span data-ttu-id="abd6c-413">Erweiterter Hintergrund</span><span class="sxs-lookup"><span data-stu-id="abd6c-413">Background Extended</span></span> | <span data-ttu-id="abd6c-414">Wendet den erweiterten Farbwert auf den Hintergrund an (Weitere Informationen finden Sie unten).</span><span class="sxs-lookup"><span data-stu-id="abd6c-414">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="abd6c-415">49</span><span class="sxs-lookup"><span data-stu-id="abd6c-415">49</span></span> | <span data-ttu-id="abd6c-416">Standard Hintergrund</span><span class="sxs-lookup"><span data-stu-id="abd6c-416">Background Default</span></span> | <span data-ttu-id="abd6c-417">Wendet nur den Hintergrund Teil der Standardwerte an (siehe 0).</span><span class="sxs-lookup"><span data-stu-id="abd6c-417">Applies only the background portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="abd6c-418">90</span><span class="sxs-lookup"><span data-stu-id="abd6c-418">90</span></span> | <span data-ttu-id="abd6c-419">Heller Vordergrund schwarz</span><span class="sxs-lookup"><span data-stu-id="abd6c-419">Bright Foreground Black</span></span> | <span data-ttu-id="abd6c-420">Wendet Fett/Hellschwarz auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-420">Applies bold/bright black to foreground</span></span> |
| <span data-ttu-id="abd6c-421">91</span><span class="sxs-lookup"><span data-stu-id="abd6c-421">91</span></span> | <span data-ttu-id="abd6c-422">Heller Vordergrund rot</span><span class="sxs-lookup"><span data-stu-id="abd6c-422">Bright Foreground Red</span></span> | <span data-ttu-id="abd6c-423">Wendet Fett/hell rot auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-423">Applies bold/bright red to foreground</span></span> |
| <span data-ttu-id="abd6c-424">92</span><span class="sxs-lookup"><span data-stu-id="abd6c-424">92</span></span> | <span data-ttu-id="abd6c-425">Heller Vordergrund grün</span><span class="sxs-lookup"><span data-stu-id="abd6c-425">Bright Foreground Green</span></span> | <span data-ttu-id="abd6c-426">Wendet Fett/hellgrün auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-426">Applies bold/bright green to foreground</span></span> |
| <span data-ttu-id="abd6c-427">93</span><span class="sxs-lookup"><span data-stu-id="abd6c-427">93</span></span> | <span data-ttu-id="abd6c-428">Heller Vordergrund gelb</span><span class="sxs-lookup"><span data-stu-id="abd6c-428">Bright Foreground Yellow</span></span> | <span data-ttu-id="abd6c-429">Wendet Fett/hell gelb auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-429">Applies bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="abd6c-430">94</span><span class="sxs-lookup"><span data-stu-id="abd6c-430">94</span></span> | <span data-ttu-id="abd6c-431">Heller Vordergrund blau</span><span class="sxs-lookup"><span data-stu-id="abd6c-431">Bright Foreground Blue</span></span> | <span data-ttu-id="abd6c-432">Wendet Fett/hell blau auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-432">Applies bold/bright blue to foreground</span></span> |
| <span data-ttu-id="abd6c-433">95</span><span class="sxs-lookup"><span data-stu-id="abd6c-433">95</span></span> | <span data-ttu-id="abd6c-434">Heller Vordergrund Magenta</span><span class="sxs-lookup"><span data-stu-id="abd6c-434">Bright Foreground Magenta</span></span> | <span data-ttu-id="abd6c-435">Wendet Bold/hellmagenta auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-435">Applies bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="abd6c-436">96</span><span class="sxs-lookup"><span data-stu-id="abd6c-436">96</span></span> | <span data-ttu-id="abd6c-437">Heller Vordergrund-Cyan</span><span class="sxs-lookup"><span data-stu-id="abd6c-437">Bright Foreground Cyan</span></span> | <span data-ttu-id="abd6c-438">Wendet Bold/hell Zyan auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-438">Applies bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="abd6c-439">97</span><span class="sxs-lookup"><span data-stu-id="abd6c-439">97</span></span> | <span data-ttu-id="abd6c-440">Heller Vordergrund weiß</span><span class="sxs-lookup"><span data-stu-id="abd6c-440">Bright Foreground White</span></span> | <span data-ttu-id="abd6c-441">Wendet Fett/hell weiß auf Vordergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-441">Applies bold/bright white to foreground</span></span> |
| <span data-ttu-id="abd6c-442">100</span><span class="sxs-lookup"><span data-stu-id="abd6c-442">100</span></span> | <span data-ttu-id="abd6c-443">Heller Hintergrund schwarz</span><span class="sxs-lookup"><span data-stu-id="abd6c-443">Bright Background Black</span></span> | <span data-ttu-id="abd6c-444">Wendet Fett/Hellschwarz auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="abd6c-444">Applies bold/bright black to background</span></span> |
| <span data-ttu-id="abd6c-445">101</span><span class="sxs-lookup"><span data-stu-id="abd6c-445">101</span></span> | <span data-ttu-id="abd6c-446">Heller Hintergrund rot</span><span class="sxs-lookup"><span data-stu-id="abd6c-446">Bright Background Red</span></span> | <span data-ttu-id="abd6c-447">Wendet Fett/hell rot auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="abd6c-447">Applies bold/bright red to background</span></span> |
| <span data-ttu-id="abd6c-448">102</span><span class="sxs-lookup"><span data-stu-id="abd6c-448">102</span></span> | <span data-ttu-id="abd6c-449">Heller Hintergrund grün</span><span class="sxs-lookup"><span data-stu-id="abd6c-449">Bright Background Green</span></span> | <span data-ttu-id="abd6c-450">Wendet Fett/hellgrün auf Hintergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-450">Applies bold/bright green to background</span></span> |
| <span data-ttu-id="abd6c-451">103</span><span class="sxs-lookup"><span data-stu-id="abd6c-451">103</span></span> | <span data-ttu-id="abd6c-452">Heller Hintergrund Gelb</span><span class="sxs-lookup"><span data-stu-id="abd6c-452">Bright Background Yellow</span></span> | <span data-ttu-id="abd6c-453">Wendet Fett/hell gelb auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="abd6c-453">Applies bold/bright yellow to background</span></span> |
| <span data-ttu-id="abd6c-454">104</span><span class="sxs-lookup"><span data-stu-id="abd6c-454">104</span></span> | <span data-ttu-id="abd6c-455">Heller Hintergrund blau</span><span class="sxs-lookup"><span data-stu-id="abd6c-455">Bright Background Blue</span></span> | <span data-ttu-id="abd6c-456">Wendet Fett/hellblau auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="abd6c-456">Applies bold/bright blue to background</span></span> |
| <span data-ttu-id="abd6c-457">105</span><span class="sxs-lookup"><span data-stu-id="abd6c-457">105</span></span> | <span data-ttu-id="abd6c-458">Heller Hintergrund Magenta</span><span class="sxs-lookup"><span data-stu-id="abd6c-458">Bright Background Magenta</span></span> | <span data-ttu-id="abd6c-459">Wendet Bold/hellmagenta auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="abd6c-459">Applies bold/bright magenta to background</span></span> |
| <span data-ttu-id="abd6c-460">106</span><span class="sxs-lookup"><span data-stu-id="abd6c-460">106</span></span> | <span data-ttu-id="abd6c-461">Heller Hintergrund Cyan</span><span class="sxs-lookup"><span data-stu-id="abd6c-461">Bright Background Cyan</span></span> | <span data-ttu-id="abd6c-462">Wendet Bold/hell Zyan auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="abd6c-462">Applies bold/bright cyan to background</span></span> |
| <span data-ttu-id="abd6c-463">107</span><span class="sxs-lookup"><span data-stu-id="abd6c-463">107</span></span> | <span data-ttu-id="abd6c-464">Heller Hintergrund weiß</span><span class="sxs-lookup"><span data-stu-id="abd6c-464">Bright Background White</span></span> | <span data-ttu-id="abd6c-465">Wendet Fett/hell weiß auf Hintergrund an</span><span class="sxs-lookup"><span data-stu-id="abd6c-465">Applies bold/bright white to background</span></span> |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="abd6c-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Erweiterte Farben</span><span class="sxs-lookup"><span data-stu-id="abd6c-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="abd6c-467">Einige virtuelle Terminal Emulatoren unterstützen eine Palette von Farben, die größer sind als die von der Windows-Konsole bereitgestellten Farben.</span><span class="sxs-lookup"><span data-stu-id="abd6c-467">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="abd6c-468">Für diese erweiterten Farben wählt die Windows-Konsole die nächstgelegene Farbe aus der vorhandenen 16-Farbtabelle zum Anzeigen aus.</span><span class="sxs-lookup"><span data-stu-id="abd6c-468">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="abd6c-469">Im Gegensatz zu typischen SGR-Werten verbrauchen die erweiterten Werte nach dem anfänglichen Indikator gemäß der folgenden Tabelle zusätzliche Parameter.</span><span class="sxs-lookup"><span data-stu-id="abd6c-469">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="abd6c-470">SGR-unter Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-470">SGR Subsequence</span></span> | <span data-ttu-id="abd6c-471">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-471">Description</span></span> |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="abd6c-472">38; 2,2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="abd6c-472">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="abd6c-473">Festlegen der Vordergrundfarbe auf RGB-Wert in &lt; r- &gt; , &lt; g- &gt; , b- &lt; &gt; Parametern\*</span><span class="sxs-lookup"><span data-stu-id="abd6c-473">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="abd6c-474">48; 2,2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="abd6c-474">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="abd6c-475">Legen Sie die Hintergrundfarbe auf den in &lt; r- &gt; , &lt; g- &gt; , b- &lt; &gt; Parametern\*</span><span class="sxs-lookup"><span data-stu-id="abd6c-475">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="abd6c-476">38; 5@@ &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="abd6c-476">38 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="abd6c-477">Festlegen der Vordergrundfarbe auf den &lt; s- &gt; Index in 88-oder 256-Farbtabelle\*</span><span class="sxs-lookup"><span data-stu-id="abd6c-477">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |
| <span data-ttu-id="abd6c-478">48; 5@@ &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="abd6c-478">48 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="abd6c-479">Festlegen der Hintergrundfarbe auf den &lt; s- &gt; Index in der 88-oder 256-Farbtabelle\*</span><span class="sxs-lookup"><span data-stu-id="abd6c-479">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |



<span data-ttu-id="abd6c-480">\*Die Farbpaletten 88 und 256, die intern für Vergleiche verwaltet werden, basieren auf dem xterm-Terminal Emulator.</span><span class="sxs-lookup"><span data-stu-id="abd6c-480">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="abd6c-481">Die Vergleichs-/Rundungs Tabellen können zu diesem Zeitpunkt nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-481">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="abd6c-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Bildschirmfarben</span><span class="sxs-lookup"><span data-stu-id="abd6c-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="abd6c-483">Der folgende Befehl ermöglicht es der Anwendung, die Farbpalette-Werte der Bildschirmfarben auf einen beliebigen RGB-Wert festzulegen.</span><span class="sxs-lookup"><span data-stu-id="abd6c-483">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="abd6c-484">Die RGB-Werte sollten hexadezimal Werte zwischen `0` und sein `ff` und durch den Schrägstrich (z. b. `rgb:1/24/86` ) getrennt werden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-484">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="abd6c-485">Beachten Sie, dass es sich bei dieser Sequenz um eine "Command"-Sequenz vom Typ "osc" handelt, nicht um ein CSI wie viele der anderen aufgelisteten Sequenzen, und beginnen Sie mit " \\ x1B \] " und nicht mit " \\ x1B \[ ".</span><span class="sxs-lookup"><span data-stu-id="abd6c-485">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="abd6c-486">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-486">Sequence</span></span> | <span data-ttu-id="abd6c-487">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-487">Description</span></span> | <span data-ttu-id="abd6c-488">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-488">Behavior</span></span> |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="abd6c-489">ESC \] 4; &lt; i &gt; ; RGB: &lt; r &gt;  /  &lt; g &gt;  /  &lt; b &gt; ESC</span><span class="sxs-lookup"><span data-stu-id="abd6c-489">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="abd6c-490">Ändern der Bildschirmfarben</span><span class="sxs-lookup"><span data-stu-id="abd6c-490">Modify Screen Colors</span></span> | <span data-ttu-id="abd6c-491">Legt den Bildschirm Farbpalette-Index &lt; i &gt; auf die RGB-Werte fest, die in &lt; r &gt; , &lt; g &gt; , &lt; b angegeben sind.&gt;</span><span class="sxs-lookup"><span data-stu-id="abd6c-491">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="abd6c-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modusänderungen</span><span class="sxs-lookup"><span data-stu-id="abd6c-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="abd6c-493">Dabei handelt es sich um Sequenzen, die die Eingabemodi steuern.</span><span class="sxs-lookup"><span data-stu-id="abd6c-493">These are sequences that control the input modes.</span></span> <span data-ttu-id="abd6c-494">Es gibt zwei unterschiedliche Sätze von Eingabemodi: den Cursor Schlüssel Modus und den Keypad-Schlüssel Modus.</span><span class="sxs-lookup"><span data-stu-id="abd6c-494">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="abd6c-495">Der Cursor Schlüssel Modus steuert die Sequenzen, die von den Pfeiltasten sowie von Start-und Endzeichen ausgegeben werden, während der Keypad-Schlüssel Modus die von den Schlüsseln im NumPad ausgegebene Sequenzen und die Funktionstasten steuert.</span><span class="sxs-lookup"><span data-stu-id="abd6c-495">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="abd6c-496">Jeder dieser Modi ist eine einfache boolesche Einstellung – der Cursor Schlüssel Modus ist entweder normal (Standard) oder Anwendung, und der Keypad-Schlüssel Modus ist entweder numerisch (Standard) oder Anwendung.</span><span class="sxs-lookup"><span data-stu-id="abd6c-496">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="abd6c-497">Weitere Informationen zu den in diesen Modi ausgegebenen Sequenzen finden Sie in den Abschnitten Cursor Schlüssel und Numpad &-Funktions Schlüsseln.</span><span class="sxs-lookup"><span data-stu-id="abd6c-497">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="abd6c-498">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-498">Sequence</span></span> | <span data-ttu-id="abd6c-499">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-499">Code</span></span> | <span data-ttu-id="abd6c-500">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-500">Description</span></span> | <span data-ttu-id="abd6c-501">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-501">Behavior</span></span> |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="abd6c-502">ESC =</span><span class="sxs-lookup"><span data-stu-id="abd6c-502">ESC =</span></span> | <span data-ttu-id="abd6c-503">Deckpam</span><span class="sxs-lookup"><span data-stu-id="abd6c-503">DECKPAM</span></span> | <span data-ttu-id="abd6c-504">Aktivieren des Keypad-Anwendungsmodus</span><span class="sxs-lookup"><span data-stu-id="abd6c-504">Enable Keypad Application Mode</span></span> | <span data-ttu-id="abd6c-505">Keypad-Schlüssel geben Ihre anwendungsmodussequenzen aus.</span><span class="sxs-lookup"><span data-stu-id="abd6c-505">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="abd6c-506">Dor &gt;</span><span class="sxs-lookup"><span data-stu-id="abd6c-506">ESC &gt;</span></span> | <span data-ttu-id="abd6c-507">Deckpnm</span><span class="sxs-lookup"><span data-stu-id="abd6c-507">DECKPNM</span></span> | <span data-ttu-id="abd6c-508">Aktivieren des numerischen Keypad-Modus</span><span class="sxs-lookup"><span data-stu-id="abd6c-508">Enable Keypad Numeric Mode</span></span> | <span data-ttu-id="abd6c-509">Keypad-Schlüssel geben ihre numerischen modussequenzen aus.</span><span class="sxs-lookup"><span data-stu-id="abd6c-509">Keypad keys will emit their Numeric Mode sequences.</span></span> |
| <span data-ttu-id="abd6c-510">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="abd6c-510">ESC \[ ?</span></span> <span data-ttu-id="abd6c-511">1 Stunde</span><span class="sxs-lookup"><span data-stu-id="abd6c-511">1 h</span></span> | <span data-ttu-id="abd6c-512">Decckm</span><span class="sxs-lookup"><span data-stu-id="abd6c-512">DECCKM</span></span> | <span data-ttu-id="abd6c-513">Aktivieren des Anwendungsmodus für Cursor Tasten</span><span class="sxs-lookup"><span data-stu-id="abd6c-513">Enable Cursor Keys Application Mode</span></span> | <span data-ttu-id="abd6c-514">Keypad-Schlüssel geben Ihre anwendungsmodussequenzen aus.</span><span class="sxs-lookup"><span data-stu-id="abd6c-514">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="abd6c-515">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="abd6c-515">ESC \[ ?</span></span> <span data-ttu-id="abd6c-516">1 l</span><span class="sxs-lookup"><span data-stu-id="abd6c-516">1 l</span></span> | <span data-ttu-id="abd6c-517">Decckm</span><span class="sxs-lookup"><span data-stu-id="abd6c-517">DECCKM</span></span> | <span data-ttu-id="abd6c-518">Deaktivieren Sie den Anwendungsmodus für Cursor Tasten (normaler Modus verwenden).</span><span class="sxs-lookup"><span data-stu-id="abd6c-518">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="abd6c-519">Keypad-Schlüssel geben ihre numerischen modussequenzen aus.</span><span class="sxs-lookup"><span data-stu-id="abd6c-519">Keypad keys will emit their Numeric Mode sequences.</span></span> |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="abd6c-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Abfrage Status</span><span class="sxs-lookup"><span data-stu-id="abd6c-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="abd6c-521">Alle Befehle in diesem Abschnitt entsprechen in der Regel dem Aufruf von get \* Console-APIs zum Abrufen von Statusinformationen zum aktuellen Zustand der Konsolen Puffer.</span><span class="sxs-lookup"><span data-stu-id="abd6c-521">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

> [!NOTE]
><span data-ttu-id="abd6c-522">Diese Abfragen geben Ihre Antworten sofort in den Konsolen Eingabestream aus, wenn Sie im Ausgabestream erkannt werden, während die \_ virtuelle \_ Terminal \_ Verarbeitung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="abd6c-522">These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="abd6c-523">Das \_ \_ eingabeflag "virtuelles Terminal aktivieren" \_ gilt nicht für Abfrage Befehle, da davon ausgegangen wird, dass eine Anwendung, die die Abfrage erstellt, die Antwort immer empfangen möchte.</span><span class="sxs-lookup"><span data-stu-id="abd6c-523">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="abd6c-524">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-524">Sequence</span></span> | <span data-ttu-id="abd6c-525">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-525">Code</span></span> | <span data-ttu-id="abd6c-526">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-526">Description</span></span> | <span data-ttu-id="abd6c-527">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-527">Behavior</span></span> |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="abd6c-528">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="abd6c-528">ESC \[ 6 n</span></span> | <span data-ttu-id="abd6c-529">Decxcpr</span><span class="sxs-lookup"><span data-stu-id="abd6c-529">DECXCPR</span></span> | <span data-ttu-id="abd6c-530">Cursor Position des Berichts</span><span class="sxs-lookup"><span data-stu-id="abd6c-530">Report Cursor Position</span></span> | <span data-ttu-id="abd6c-531">Geben Sie die Cursorposition wie folgt aus: Esc \[ &lt; r &gt; ; &lt; c &gt; r Where &lt; R &gt; = Cursor Zeile und &lt; c &gt; = Cursor Spalte</span><span class="sxs-lookup"><span data-stu-id="abd6c-531">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="abd6c-532">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="abd6c-532">ESC \[ 0 c</span></span> | <span data-ttu-id="abd6c-533">De</span><span class="sxs-lookup"><span data-stu-id="abd6c-533">DA</span></span> | <span data-ttu-id="abd6c-534">Geräte Attribute</span><span class="sxs-lookup"><span data-stu-id="abd6c-534">Device Attributes</span></span> | <span data-ttu-id="abd6c-535">Melden Sie die Terminal Identität.</span><span class="sxs-lookup"><span data-stu-id="abd6c-535">Report the terminal identity.</span></span> <span data-ttu-id="abd6c-536">Gibt " \\ x1B \[ ? 1; 0C" aus, was "VT101 ohne Optionen" angibt.</span><span class="sxs-lookup"><span data-stu-id="abd6c-536">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span> |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="abd6c-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tafeln</span><span class="sxs-lookup"><span data-stu-id="abd6c-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="abd6c-538">Obwohl die Windows-Konsole normalerweise davon ausgeht, dass Registerkarten ausschließlich acht Zeichen umfassen, \* können nix-Anwendungen, die bestimmte Sequenzen verwenden, bearbeiten, wo sich die Tabstopps innerhalb der Konsolenfenster befinden, um die Cursor Bewegung durch die Anwendung zu optimieren</span><span class="sxs-lookup"><span data-stu-id="abd6c-538">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="abd6c-539">Die folgenden Sequenzen ermöglichen es einer Anwendung, die Position der Tabstopps innerhalb des Konsolenfensters festzulegen, Sie zu entfernen und zwischen Ihnen zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="abd6c-539">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="abd6c-540">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-540">Sequence</span></span> | <span data-ttu-id="abd6c-541">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-541">Code</span></span> | <span data-ttu-id="abd6c-542">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-542">Description</span></span> | <span data-ttu-id="abd6c-543">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-543">Behavior</span></span> |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="abd6c-544">ESC H</span><span class="sxs-lookup"><span data-stu-id="abd6c-544">ESC H</span></span> | <span data-ttu-id="abd6c-545">HTS</span><span class="sxs-lookup"><span data-stu-id="abd6c-545">HTS</span></span> | <span data-ttu-id="abd6c-546">Horizontaler Registerkarten Satz</span><span class="sxs-lookup"><span data-stu-id="abd6c-546">Horizontal Tab Set</span></span> | <span data-ttu-id="abd6c-547">Legt einen Tabstopp in der aktuellen Spalte fest, in der sich der Cursor befindet.</span><span class="sxs-lookup"><span data-stu-id="abd6c-547">Sets a tab stop in the current column the cursor is in.</span></span> |
| <span data-ttu-id="abd6c-548">ESC \[ &lt; n &gt; I</span><span class="sxs-lookup"><span data-stu-id="abd6c-548">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="abd6c-549">CHT</span><span class="sxs-lookup"><span data-stu-id="abd6c-549">CHT</span></span> | <span data-ttu-id="abd6c-550">Horizontale Cursor Registerkarte (vorwärts)</span><span class="sxs-lookup"><span data-stu-id="abd6c-550">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="abd6c-551">Bewegen Sie den Cursor mit einer Tabstopp Taste zur nächsten Spalte (in derselben Zeile).</span><span class="sxs-lookup"><span data-stu-id="abd6c-551">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="abd6c-552">Wenn keine weiteren Tabstopps vorhanden sind, fahren Sie mit der letzten Spalte in der Zeile fort.</span><span class="sxs-lookup"><span data-stu-id="abd6c-552">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="abd6c-553">Wenn sich der Cursor in der letzten Spalte befindet, wechseln Sie zur ersten Spalte der nächsten Zeile.</span><span class="sxs-lookup"><span data-stu-id="abd6c-553">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="abd6c-554">ESC \[ &lt; n &gt; Z</span><span class="sxs-lookup"><span data-stu-id="abd6c-554">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="abd6c-555">CBT</span><span class="sxs-lookup"><span data-stu-id="abd6c-555">CBT</span></span> | <span data-ttu-id="abd6c-556">Cursor Registerkarte rückwärts</span><span class="sxs-lookup"><span data-stu-id="abd6c-556">Cursor Backwards Tab</span></span> | <span data-ttu-id="abd6c-557">Bewegen Sie den Cursor in die vorherige Spalte (in derselben Zeile) mit einer Tabstopp Taste.</span><span class="sxs-lookup"><span data-stu-id="abd6c-557">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="abd6c-558">Wenn keine weiteren Tabstopps vorhanden sind, verschiebt den Cursor zur ersten Spalte.</span><span class="sxs-lookup"><span data-stu-id="abd6c-558">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="abd6c-559">Wenn sich der Cursor in der ersten Spalte befindet, verschiebt den Cursor nicht.</span><span class="sxs-lookup"><span data-stu-id="abd6c-559">If the cursor is in the first column, doesn’t move the cursor.</span></span> |
| <span data-ttu-id="abd6c-560">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="abd6c-560">ESC \[ 0 g</span></span> | <span data-ttu-id="abd6c-561">TBC</span><span class="sxs-lookup"><span data-stu-id="abd6c-561">TBC</span></span> | <span data-ttu-id="abd6c-562">Tab Clear (aktuelle Spalte)</span><span class="sxs-lookup"><span data-stu-id="abd6c-562">Tab Clear (current column)</span></span> | <span data-ttu-id="abd6c-563">Löscht den Tabstopp in der aktuellen Spalte, sofern vorhanden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-563">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="abd6c-564">Andernfalls geschieht nichts.</span><span class="sxs-lookup"><span data-stu-id="abd6c-564">Otherwise does nothing.</span></span> |
| <span data-ttu-id="abd6c-565">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="abd6c-565">ESC \[ 3 g</span></span> | <span data-ttu-id="abd6c-566">TBC</span><span class="sxs-lookup"><span data-stu-id="abd6c-566">TBC</span></span> | <span data-ttu-id="abd6c-567">Tab Clear (alle Spalten)</span><span class="sxs-lookup"><span data-stu-id="abd6c-567">Tab Clear (all columns)</span></span> | <span data-ttu-id="abd6c-568">Löscht alle momentan festgelegten Tabstopps.</span><span class="sxs-lookup"><span data-stu-id="abd6c-568">Clears all currently set tab stops.</span></span> |



- <span data-ttu-id="abd6c-569">Bei n und CBT &lt; &gt; ist n ein optionaler Parameter, der (Standardwert = 1) angibt, wie oft der Cursor in der angegebenen Richtung vorwärts bewegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="abd6c-569">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="abd6c-570">Wenn keine Tabstopps über HTS festgelegt sind, werden die erste und die letzte Spalte des Fensters von cht und CBT als die einzigen beiden Tabstopps behandelt.</span><span class="sxs-lookup"><span data-stu-id="abd6c-570">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="abd6c-571">Die Verwendung von HTS zum Festlegen eines Tabstopps bewirkt auch, dass die Konsole in der Ausgabe eines Tabstopps (0x09, " \\ t") auf die gleiche Weise wie bei cht zum nächsten Tabstopp navigiert.</span><span class="sxs-lookup"><span data-stu-id="abd6c-571">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="abd6c-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Zeichensatz festlegen</span><span class="sxs-lookup"><span data-stu-id="abd6c-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="abd6c-573">Die folgenden Sequenzen ermöglichen einem Programm, die Zuordnung des aktiven Zeichensatzes zu ändern.</span><span class="sxs-lookup"><span data-stu-id="abd6c-573">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="abd6c-574">Dies ermöglicht es einem Programm, 7-Bit-ASCII-Zeichen auszugeben, Sie aber als andere Symbole auf dem Terminalbildschirm selbst anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="abd6c-574">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="abd6c-575">Zurzeit sind die einzigen beiden unterstützten Zeichensätze ASCII (Standard) und der besondere Grafik Zeichensatz für Dec.</span><span class="sxs-lookup"><span data-stu-id="abd6c-575">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="abd6c-576">Unter finden Sie <http://vt100.net/docs/vt220-rm/table2-4.html> eine Liste aller Zeichen, die durch den speziellen Dec-Grafik Zeichensatz dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-576">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="abd6c-577">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-577">Sequence</span></span> | <span data-ttu-id="abd6c-578">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-578">Description</span></span> | <span data-ttu-id="abd6c-579">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-579">Behavior</span></span> |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="abd6c-580">ESC (0</span><span class="sxs-lookup"><span data-stu-id="abd6c-580">ESC ( 0</span></span> | <span data-ttu-id="abd6c-581">Zeichensatz festlegen – Dec-Zeichnungs Linie</span><span class="sxs-lookup"><span data-stu-id="abd6c-581">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="abd6c-582">Aktiviert den Modus "Dec Line Drawing"</span><span class="sxs-lookup"><span data-stu-id="abd6c-582">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="abd6c-583">ESC (B</span><span class="sxs-lookup"><span data-stu-id="abd6c-583">ESC ( B</span></span> | <span data-ttu-id="abd6c-584">Festlegen des Zeichensatzes – US-ASCII</span><span class="sxs-lookup"><span data-stu-id="abd6c-584">Designate Character Set – US ASCII</span></span> | <span data-ttu-id="abd6c-585">Aktiviert den ASCII-Modus (Standard)</span><span class="sxs-lookup"><span data-stu-id="abd6c-585">Enables ASCII Mode (Default)</span></span> |



<span data-ttu-id="abd6c-586">Insbesondere wird der Dec-Zeichnungsmodus zum Zeichnen von Rahmen in Konsolen Anwendungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="abd6c-586">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="abd6c-587">In der folgenden Tabelle ist dargestellt, welche ASCII-Zeichen mit welchem Zeilen Zeichnungs Zeichen zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-587">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="abd6c-588">Hex</span><span class="sxs-lookup"><span data-stu-id="abd6c-588">Hex</span></span> | <span data-ttu-id="abd6c-589">ASCII</span><span class="sxs-lookup"><span data-stu-id="abd6c-589">ASCII</span></span> | <span data-ttu-id="abd6c-590">Zeilen Zeichnung mit Dec</span><span class="sxs-lookup"><span data-stu-id="abd6c-590">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="abd6c-591">0x6a</span><span class="sxs-lookup"><span data-stu-id="abd6c-591">0x6a</span></span> | <span data-ttu-id="abd6c-592">j</span><span class="sxs-lookup"><span data-stu-id="abd6c-592">j</span></span> | <span data-ttu-id="abd6c-593">┘</span><span class="sxs-lookup"><span data-stu-id="abd6c-593">┘</span></span> |
| <span data-ttu-id="abd6c-594">0x6b</span><span class="sxs-lookup"><span data-stu-id="abd6c-594">0x6b</span></span> | <span data-ttu-id="abd6c-595">k</span><span class="sxs-lookup"><span data-stu-id="abd6c-595">k</span></span> | <span data-ttu-id="abd6c-596">┐</span><span class="sxs-lookup"><span data-stu-id="abd6c-596">┐</span></span> |
| <span data-ttu-id="abd6c-597">0x6C</span><span class="sxs-lookup"><span data-stu-id="abd6c-597">0x6c</span></span> | <span data-ttu-id="abd6c-598">l</span><span class="sxs-lookup"><span data-stu-id="abd6c-598">l</span></span> | <span data-ttu-id="abd6c-599">┌</span><span class="sxs-lookup"><span data-stu-id="abd6c-599">┌</span></span> |
| <span data-ttu-id="abd6c-600">0x6d</span><span class="sxs-lookup"><span data-stu-id="abd6c-600">0x6d</span></span> | <span data-ttu-id="abd6c-601">m</span><span class="sxs-lookup"><span data-stu-id="abd6c-601">m</span></span> | <span data-ttu-id="abd6c-602">└</span><span class="sxs-lookup"><span data-stu-id="abd6c-602">└</span></span> |
| <span data-ttu-id="abd6c-603">0x6e</span><span class="sxs-lookup"><span data-stu-id="abd6c-603">0x6e</span></span> | <span data-ttu-id="abd6c-604">n</span><span class="sxs-lookup"><span data-stu-id="abd6c-604">n</span></span> | <span data-ttu-id="abd6c-605">┼</span><span class="sxs-lookup"><span data-stu-id="abd6c-605">┼</span></span> |
| <span data-ttu-id="abd6c-606">0x71</span><span class="sxs-lookup"><span data-stu-id="abd6c-606">0x71</span></span> | <span data-ttu-id="abd6c-607">q</span><span class="sxs-lookup"><span data-stu-id="abd6c-607">q</span></span> | <span data-ttu-id="abd6c-608">─</span><span class="sxs-lookup"><span data-stu-id="abd6c-608">─</span></span> |
| <span data-ttu-id="abd6c-609">0x74</span><span class="sxs-lookup"><span data-stu-id="abd6c-609">0x74</span></span> | <span data-ttu-id="abd6c-610">t</span><span class="sxs-lookup"><span data-stu-id="abd6c-610">t</span></span> | <span data-ttu-id="abd6c-611">├</span><span class="sxs-lookup"><span data-stu-id="abd6c-611">├</span></span> |
| <span data-ttu-id="abd6c-612">0x75</span><span class="sxs-lookup"><span data-stu-id="abd6c-612">0x75</span></span> | <span data-ttu-id="abd6c-613">u</span><span class="sxs-lookup"><span data-stu-id="abd6c-613">u</span></span> | <span data-ttu-id="abd6c-614">┤</span><span class="sxs-lookup"><span data-stu-id="abd6c-614">┤</span></span> |
| <span data-ttu-id="abd6c-615">0x76</span><span class="sxs-lookup"><span data-stu-id="abd6c-615">0x76</span></span> | <span data-ttu-id="abd6c-616">v</span><span class="sxs-lookup"><span data-stu-id="abd6c-616">v</span></span> | <span data-ttu-id="abd6c-617">┴</span><span class="sxs-lookup"><span data-stu-id="abd6c-617">┴</span></span> |
| <span data-ttu-id="abd6c-618">0x77</span><span class="sxs-lookup"><span data-stu-id="abd6c-618">0x77</span></span> | <span data-ttu-id="abd6c-619">w</span><span class="sxs-lookup"><span data-stu-id="abd6c-619">w</span></span> | <span data-ttu-id="abd6c-620">┬</span><span class="sxs-lookup"><span data-stu-id="abd6c-620">┬</span></span> |
| <span data-ttu-id="abd6c-621">0x78</span><span class="sxs-lookup"><span data-stu-id="abd6c-621">0x78</span></span> | <span data-ttu-id="abd6c-622">w</span><span class="sxs-lookup"><span data-stu-id="abd6c-622">x</span></span> | <span data-ttu-id="abd6c-623">│</span><span class="sxs-lookup"><span data-stu-id="abd6c-623">│</span></span> |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="abd6c-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrollränder</span><span class="sxs-lookup"><span data-stu-id="abd6c-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="abd6c-625">Die folgenden Sequenzen ermöglichen einem Programm, den "scrollbereich" des Bildschirms zu konfigurieren, der von scrollvorgängen betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="abd6c-625">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="abd6c-626">Dabei handelt es sich um eine Teilmenge der Zeilen, die angepasst werden, wenn auf dem Bildschirm ein anderer Bildlauf durchführt, z. b. auf einem \\ n-oder RI-.</span><span class="sxs-lookup"><span data-stu-id="abd6c-626">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="abd6c-627">Diese Ränder wirken sich auch auf die Zeilen aus, die durch Einfügezeile (IL) und Delete Line (DL) geändert werden, Scrollen nach oben (su) und Scrollen nach unten (SD).</span><span class="sxs-lookup"><span data-stu-id="abd6c-627">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="abd6c-628">Die scrollränder können besonders nützlich sein, wenn ein Teil des Bildschirms angezeigt wird, wenn der restliche Bildschirm nicht angezeigt wird, z. b. eine Titelleiste am oberen Rand oder eine Statusleiste am unteren Rand der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="abd6c-628">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="abd6c-629">Für decstbm gibt es zwei optionale Parameter: &lt; t &gt; und &lt; b &gt; , die verwendet werden, um die Zeilen anzugeben, die den oberen und unteren Rand des Bild Lauf Bereichs darstellen (einschließlich).</span><span class="sxs-lookup"><span data-stu-id="abd6c-629">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="abd6c-630">Wenn die Parameter ausgelassen werden, lautet der Standardwert 1, wobei &lt; &gt; &lt; b &gt; standardmäßig die aktuelle VIEWPORTHÖHE verwendet.</span><span class="sxs-lookup"><span data-stu-id="abd6c-630">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="abd6c-631">Scrollränder sind pro Puffer, was wichtig ist, dass der Alternative Puffer und der Hauptpuffer separate Einstellungen für die scrollränder behalten (sodass eine Vollbild-Anwendung im alternativen Puffer die Ränder des Haupt Puffers nicht verbleibt).</span><span class="sxs-lookup"><span data-stu-id="abd6c-631">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="abd6c-632">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-632">Sequence</span></span> | <span data-ttu-id="abd6c-633">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-633">Code</span></span> | <span data-ttu-id="abd6c-634">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-634">Description</span></span> | <span data-ttu-id="abd6c-635">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-635">Behavior</span></span> |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="abd6c-636">ESC \[ &lt; t &gt; ; &lt; b &gt; r</span><span class="sxs-lookup"><span data-stu-id="abd6c-636">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="abd6c-637">Decstbm</span><span class="sxs-lookup"><span data-stu-id="abd6c-637">DECSTBM</span></span> | <span data-ttu-id="abd6c-638">Scrollbereich festlegen</span><span class="sxs-lookup"><span data-stu-id="abd6c-638">Set Scrolling Region</span></span> | <span data-ttu-id="abd6c-639">Legt die VT-scrollränder des Viewports fest.</span><span class="sxs-lookup"><span data-stu-id="abd6c-639">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="abd6c-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Fenstertitel</span><span class="sxs-lookup"><span data-stu-id="abd6c-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="abd6c-641">Mit den folgenden Befehlen kann die Anwendung den Titel des Konsolenfensters auf den angegebenen Zeichen folgen &lt; &gt; Parameter festlegen.</span><span class="sxs-lookup"><span data-stu-id="abd6c-641">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="abd6c-642">Die Zeichenfolge muss weniger als 255 Zeichen annehmen, um akzeptiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-642">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="abd6c-643">Dies entspricht dem Aufrufen von setconsoletitle mit der angegebenen Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="abd6c-643">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="abd6c-644">Beachten Sie, dass es sich bei diesen Sequenzen um die Befehle "Betriebssystem Befehl" des Befehls "osc" handelt, nicht um ein CSI-wie viele der anderen aufgelisteten Sequenzen, und damit beginnt " \\ x1B \] ", nicht " \\ x1B \[ ".</span><span class="sxs-lookup"><span data-stu-id="abd6c-644">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="abd6c-645">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-645">Sequence</span></span> | <span data-ttu-id="abd6c-646">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-646">Description</span></span> | <span data-ttu-id="abd6c-647">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-647">Behavior</span></span> |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="abd6c-648">ESC \] 0; &lt; Zeichenfolge &gt; Bel</span><span class="sxs-lookup"><span data-stu-id="abd6c-648">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="abd6c-649">Symbol und Fenstertitel festlegen</span><span class="sxs-lookup"><span data-stu-id="abd6c-649">Set Icon and Window Title</span></span> | <span data-ttu-id="abd6c-650">Legt den Titel des Konsolenfensters auf &lt; String fest &gt; .</span><span class="sxs-lookup"><span data-stu-id="abd6c-650">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="abd6c-651">ESC \] 2; &lt; Zeichenfolge &gt; Bel</span><span class="sxs-lookup"><span data-stu-id="abd6c-651">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="abd6c-652">Fenstertitel festlegen</span><span class="sxs-lookup"><span data-stu-id="abd6c-652">Set Window Title</span></span> | <span data-ttu-id="abd6c-653">Legt den Titel des Konsolenfensters auf &lt; String fest &gt; .</span><span class="sxs-lookup"><span data-stu-id="abd6c-653">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="abd6c-654">Das abschließende Zeichen hier ist das "Glocken Zeichen", " \\ x07".</span><span class="sxs-lookup"><span data-stu-id="abd6c-654">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="abd6c-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternativer Bildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="abd6c-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="abd6c-656">\*Anwendungen im Stil von nix nutzen häufig einen alternativen Bildschirm Puffer, damit Sie den gesamten Inhalt des Puffers ändern können, ohne die Anwendung zu beeinträchtigen, von der Sie gestartet wurden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-656">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="abd6c-657">Der Alternative Puffer ist genau die Abmessungen des Fensters, ohne einen scrollbackfunktionalität Bereich.</span><span class="sxs-lookup"><span data-stu-id="abd6c-657">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="abd6c-658">Ein Beispiel für dieses Verhalten ist, wenn vim von bash gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="abd6c-658">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="abd6c-659">Vim verwendet den gesamten Bildschirm, um die Datei zu bearbeiten. Wenn Sie zu bash zurückkehren, bleibt der ursprüngliche Puffer unverändert.</span><span class="sxs-lookup"><span data-stu-id="abd6c-659">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="abd6c-660">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-660">Sequence</span></span> | <span data-ttu-id="abd6c-661">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-661">Description</span></span> | <span data-ttu-id="abd6c-662">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-662">Behavior</span></span> |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="abd6c-663">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="abd6c-663">ESC \[ ?</span></span> <span data-ttu-id="abd6c-664">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="abd6c-664">1 0 4 9 h</span></span> | <span data-ttu-id="abd6c-665">Alternativen Bildschirm Puffer verwenden</span><span class="sxs-lookup"><span data-stu-id="abd6c-665">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="abd6c-666">Wechselt zu einem neuen alternativen Bildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="abd6c-666">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="abd6c-667">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="abd6c-667">ESC \[ ?</span></span> <span data-ttu-id="abd6c-668">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="abd6c-668">1 0 4 9 l</span></span> | <span data-ttu-id="abd6c-669">Hauptbildschirm Puffer verwenden</span><span class="sxs-lookup"><span data-stu-id="abd6c-669">Use Main Screen Buffer</span></span> | <span data-ttu-id="abd6c-670">Wechselt zum Hauptpuffer.</span><span class="sxs-lookup"><span data-stu-id="abd6c-670">Switches to the main buffer.</span></span> |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="abd6c-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Fensterbreite</span><span class="sxs-lookup"><span data-stu-id="abd6c-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="abd6c-672">Die folgenden Sequenzen können verwendet werden, um die Breite des Konsolenfensters zu steuern.</span><span class="sxs-lookup"><span data-stu-id="abd6c-672">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="abd6c-673">Sie sind ungefähr gleichwertig mit dem Aufruf der Konsolen-API setconsolescreenbufferinfoex zum Festlegen der Fensterbreite.</span><span class="sxs-lookup"><span data-stu-id="abd6c-673">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="abd6c-674">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-674">Sequence</span></span> | <span data-ttu-id="abd6c-675">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-675">Code</span></span> | <span data-ttu-id="abd6c-676">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-676">Description</span></span> | <span data-ttu-id="abd6c-677">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-677">Behavior</span></span> |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="abd6c-678">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="abd6c-678">ESC \[ ?</span></span> <span data-ttu-id="abd6c-679">3 h</span><span class="sxs-lookup"><span data-stu-id="abd6c-679">3 h</span></span> | <span data-ttu-id="abd6c-680">Deccolm</span><span class="sxs-lookup"><span data-stu-id="abd6c-680">DECCOLM</span></span> | <span data-ttu-id="abd6c-681">Festlegen der Anzahl von Spalten auf 132</span><span class="sxs-lookup"><span data-stu-id="abd6c-681">Set Number of Columns to 132</span></span> | <span data-ttu-id="abd6c-682">Legt die Konsolen Breite auf 132 Spalten breit fest.</span><span class="sxs-lookup"><span data-stu-id="abd6c-682">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="abd6c-683">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="abd6c-683">ESC \[ ?</span></span> <span data-ttu-id="abd6c-684">3 l</span><span class="sxs-lookup"><span data-stu-id="abd6c-684">3 l</span></span> | <span data-ttu-id="abd6c-685">Deccolm</span><span class="sxs-lookup"><span data-stu-id="abd6c-685">DECCOLM</span></span> | <span data-ttu-id="abd6c-686">Festlegen der Anzahl von Spalten auf 80</span><span class="sxs-lookup"><span data-stu-id="abd6c-686">Set Number of Columns to 80</span></span> | <span data-ttu-id="abd6c-687">Legt die Konsolen Breite auf 80 Spalten breit fest.</span><span class="sxs-lookup"><span data-stu-id="abd6c-687">Sets the console width to 80 columns wide.</span></span> |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="abd6c-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Vorläufiges zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="abd6c-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="abd6c-689">Die folgende Sequenz kann verwendet werden, um bestimmte Eigenschaften auf ihre Standardwerte zurückzusetzen. Die folgenden Eigenschaften werden auf die folgenden Standardwerte zurückgesetzt (Außerdem sind die Sequenzen aufgelistet, die diese Eigenschaften steuern):</span><span class="sxs-lookup"><span data-stu-id="abd6c-689">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="abd6c-690">Cursor Sichtbarkeit: sichtbar (dectem)</span><span class="sxs-lookup"><span data-stu-id="abd6c-690">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="abd6c-691">Numerische Keypad: numerischer Modus (decnkm)</span><span class="sxs-lookup"><span data-stu-id="abd6c-691">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="abd6c-692">Cursor Schlüssel Modus: normaler Modus (decckm)</span><span class="sxs-lookup"><span data-stu-id="abd6c-692">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="abd6c-693">Obere und untere Ränder: Top = 1, Bottom = Console Height (decstbm)</span><span class="sxs-lookup"><span data-stu-id="abd6c-693">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="abd6c-694">Zeichensatz: US-ASCII</span><span class="sxs-lookup"><span data-stu-id="abd6c-694">Character Set: US ASCII</span></span>
- <span data-ttu-id="abd6c-695">Grafikwiedergabe: Standard/Off (SGR)</span><span class="sxs-lookup"><span data-stu-id="abd6c-695">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="abd6c-696">Cursor Zustand speichern: Startposition (0,0) (decsc)</span><span class="sxs-lookup"><span data-stu-id="abd6c-696">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="abd6c-697">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-697">Sequence</span></span> | <span data-ttu-id="abd6c-698">Code</span><span class="sxs-lookup"><span data-stu-id="abd6c-698">Code</span></span> | <span data-ttu-id="abd6c-699">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="abd6c-699">Description</span></span> | <span data-ttu-id="abd6c-700">Verhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-700">Behavior</span></span> |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="abd6c-701">ESC \[ !</span><span class="sxs-lookup"><span data-stu-id="abd6c-701">ESC \[ !</span></span> <span data-ttu-id="abd6c-702">p</span><span class="sxs-lookup"><span data-stu-id="abd6c-702">p</span></span> | <span data-ttu-id="abd6c-703">Decstr</span><span class="sxs-lookup"><span data-stu-id="abd6c-703">DECSTR</span></span> | <span data-ttu-id="abd6c-704">Vorläufiges zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="abd6c-704">Soft Reset</span></span> | <span data-ttu-id="abd6c-705">Setzen Sie bestimmte Terminal Einstellungen auf ihre Standardeinstellungen zurück.</span><span class="sxs-lookup"><span data-stu-id="abd6c-705">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="abd6c-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Eingabe Sequenzen</span><span class="sxs-lookup"><span data-stu-id="abd6c-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="abd6c-707">Die folgenden Terminal Sequenzen werden vom Konsolen Host im Eingabestream ausgegeben, wenn das eingabeflag zum Aktivieren des \_ virtuellen \_ Terminals \_ für das Eingabepuffer Handle mit dem setconsolemode-Flag festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="abd6c-707">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="abd6c-708">Es gibt zwei interne Modi, die Steuern, welche Sequenzen für die angegebenen Eingabetasten, den Cursor Schlüssel Modus und den Keypad-Schlüssel Modus ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-708">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="abd6c-709">Diese werden im Abschnitt Modusänderungen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="abd6c-709">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="abd6c-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Tasten</span><span class="sxs-lookup"><span data-stu-id="abd6c-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="abd6c-711">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="abd6c-711">Key</span></span> | <span data-ttu-id="abd6c-712">Normaler Modus</span><span class="sxs-lookup"><span data-stu-id="abd6c-712">Normal Mode</span></span> | <span data-ttu-id="abd6c-713">Anwendungsmodus</span><span class="sxs-lookup"><span data-stu-id="abd6c-713">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="abd6c-714">NACH-OBEN</span><span class="sxs-lookup"><span data-stu-id="abd6c-714">Up Arrow</span></span> | <span data-ttu-id="abd6c-715">ESC \[ A</span><span class="sxs-lookup"><span data-stu-id="abd6c-715">ESC \[ A</span></span> | <span data-ttu-id="abd6c-716">ESC O A</span><span class="sxs-lookup"><span data-stu-id="abd6c-716">ESC O A</span></span> |
| <span data-ttu-id="abd6c-717">NACH-UNTEN</span><span class="sxs-lookup"><span data-stu-id="abd6c-717">Down Arrow</span></span> | <span data-ttu-id="abd6c-718">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="abd6c-718">ESC \[ B</span></span> | <span data-ttu-id="abd6c-719">ESC O B</span><span class="sxs-lookup"><span data-stu-id="abd6c-719">ESC O B</span></span> |
| <span data-ttu-id="abd6c-720">NACH-RECHTS</span><span class="sxs-lookup"><span data-stu-id="abd6c-720">Right Arrow</span></span> | <span data-ttu-id="abd6c-721">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="abd6c-721">ESC \[ C</span></span> | <span data-ttu-id="abd6c-722">ESC O C</span><span class="sxs-lookup"><span data-stu-id="abd6c-722">ESC O C</span></span> |
| <span data-ttu-id="abd6c-723">NACH-LINKS-TASTE</span><span class="sxs-lookup"><span data-stu-id="abd6c-723">Left Arrow</span></span> | <span data-ttu-id="abd6c-724">ESC \[ D</span><span class="sxs-lookup"><span data-stu-id="abd6c-724">ESC \[ D</span></span> | <span data-ttu-id="abd6c-725">ESC O D</span><span class="sxs-lookup"><span data-stu-id="abd6c-725">ESC O D</span></span> |
| <span data-ttu-id="abd6c-726">Startseite</span><span class="sxs-lookup"><span data-stu-id="abd6c-726">Home</span></span> | <span data-ttu-id="abd6c-727">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="abd6c-727">ESC \[ H</span></span> | <span data-ttu-id="abd6c-728">ESC O H</span><span class="sxs-lookup"><span data-stu-id="abd6c-728">ESC O H</span></span> |
| <span data-ttu-id="abd6c-729">Ende</span><span class="sxs-lookup"><span data-stu-id="abd6c-729">End</span></span> | <span data-ttu-id="abd6c-730">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="abd6c-730">ESC \[ F</span></span> | <span data-ttu-id="abd6c-731">ESC O F</span><span class="sxs-lookup"><span data-stu-id="abd6c-731">ESC O F</span></span> |



<span data-ttu-id="abd6c-732">Wenn außerdem STRG mit einem dieser Tasten gedrückt wird, werden stattdessen die folgenden Sequenzen ausgegeben, unabhängig vom Cursor Schlüssel Modus:</span><span class="sxs-lookup"><span data-stu-id="abd6c-732">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="abd6c-733">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="abd6c-733">Key</span></span> | <span data-ttu-id="abd6c-734">Beliebiger Modus</span><span class="sxs-lookup"><span data-stu-id="abd6c-734">Any Mode</span></span> |
|--------------------|----------------|
| <span data-ttu-id="abd6c-735">STRG + nach-oben-Taste</span><span class="sxs-lookup"><span data-stu-id="abd6c-735">Ctrl + Up Arrow</span></span> | <span data-ttu-id="abd6c-736">ESC \[ 1; 5 A</span><span class="sxs-lookup"><span data-stu-id="abd6c-736">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="abd6c-737">STRG + nach-unten-Taste</span><span class="sxs-lookup"><span data-stu-id="abd6c-737">Ctrl + Down Arrow</span></span> | <span data-ttu-id="abd6c-738">ESC \[ 1; 5 B</span><span class="sxs-lookup"><span data-stu-id="abd6c-738">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="abd6c-739">STRG + nach-rechts-Taste</span><span class="sxs-lookup"><span data-stu-id="abd6c-739">Ctrl + Right Arrow</span></span> | <span data-ttu-id="abd6c-740">ESC \[ 1; 5 C</span><span class="sxs-lookup"><span data-stu-id="abd6c-740">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="abd6c-741">STRG + nach-links-Taste</span><span class="sxs-lookup"><span data-stu-id="abd6c-741">Ctrl + Left Arrow</span></span> | <span data-ttu-id="abd6c-742">ESC \[ 1; 5 D</span><span class="sxs-lookup"><span data-stu-id="abd6c-742">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="abd6c-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad-& Funktionstasten</span><span class="sxs-lookup"><span data-stu-id="abd6c-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="abd6c-744">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="abd6c-744">Key</span></span> | <span data-ttu-id="abd6c-745">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-745">Sequence</span></span> |
|-----------|--------------|
| <span data-ttu-id="abd6c-746">Rückschritt</span><span class="sxs-lookup"><span data-stu-id="abd6c-746">Backspace</span></span> | <span data-ttu-id="abd6c-747">0x7F (Entf)</span><span class="sxs-lookup"><span data-stu-id="abd6c-747">0x7f (DEL)</span></span> |
| <span data-ttu-id="abd6c-748">Anhalten</span><span class="sxs-lookup"><span data-stu-id="abd6c-748">Pause</span></span> | <span data-ttu-id="abd6c-749">0x1A (Sub)</span><span class="sxs-lookup"><span data-stu-id="abd6c-749">0x1a (SUB)</span></span> |
| <span data-ttu-id="abd6c-750">Escape</span><span class="sxs-lookup"><span data-stu-id="abd6c-750">Escape</span></span> | <span data-ttu-id="abd6c-751">0x1B (ESC)</span><span class="sxs-lookup"><span data-stu-id="abd6c-751">0x1b (ESC)</span></span> |
| <span data-ttu-id="abd6c-752">Einfügen</span><span class="sxs-lookup"><span data-stu-id="abd6c-752">Insert</span></span> | <span data-ttu-id="abd6c-753">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-753">ESC \[ 2 ~</span></span> |
| <span data-ttu-id="abd6c-754">Löschen</span><span class="sxs-lookup"><span data-stu-id="abd6c-754">Delete</span></span> | <span data-ttu-id="abd6c-755">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-755">ESC \[ 3 ~</span></span> |
| <span data-ttu-id="abd6c-756">BILD-AUF</span><span class="sxs-lookup"><span data-stu-id="abd6c-756">Page Up</span></span> | <span data-ttu-id="abd6c-757">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-757">ESC \[ 5 ~</span></span> |
| <span data-ttu-id="abd6c-758">BILD-AB</span><span class="sxs-lookup"><span data-stu-id="abd6c-758">Page Down</span></span> | <span data-ttu-id="abd6c-759">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-759">ESC \[ 6 ~</span></span> |
| <span data-ttu-id="abd6c-760">F1</span><span class="sxs-lookup"><span data-stu-id="abd6c-760">F1</span></span> | <span data-ttu-id="abd6c-761">ESC O P</span><span class="sxs-lookup"><span data-stu-id="abd6c-761">ESC O P</span></span> |
| <span data-ttu-id="abd6c-762">F2</span><span class="sxs-lookup"><span data-stu-id="abd6c-762">F2</span></span> | <span data-ttu-id="abd6c-763">ESC O Q</span><span class="sxs-lookup"><span data-stu-id="abd6c-763">ESC O Q</span></span> |
| <span data-ttu-id="abd6c-764">F3</span><span class="sxs-lookup"><span data-stu-id="abd6c-764">F3</span></span> | <span data-ttu-id="abd6c-765">ESC O R</span><span class="sxs-lookup"><span data-stu-id="abd6c-765">ESC O R</span></span> |
| <span data-ttu-id="abd6c-766">F4</span><span class="sxs-lookup"><span data-stu-id="abd6c-766">F4</span></span> | <span data-ttu-id="abd6c-767">ESC O S</span><span class="sxs-lookup"><span data-stu-id="abd6c-767">ESC O S</span></span> |
| <span data-ttu-id="abd6c-768">F5</span><span class="sxs-lookup"><span data-stu-id="abd6c-768">F5</span></span> | <span data-ttu-id="abd6c-769">ESC \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-769">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="abd6c-770">F6</span><span class="sxs-lookup"><span data-stu-id="abd6c-770">F6</span></span> | <span data-ttu-id="abd6c-771">ESC \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-771">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="abd6c-772">F7</span><span class="sxs-lookup"><span data-stu-id="abd6c-772">F7</span></span> | <span data-ttu-id="abd6c-773">ESC \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-773">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="abd6c-774">F8</span><span class="sxs-lookup"><span data-stu-id="abd6c-774">F8</span></span> | <span data-ttu-id="abd6c-775">ESC \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-775">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="abd6c-776">F9</span><span class="sxs-lookup"><span data-stu-id="abd6c-776">F9</span></span> | <span data-ttu-id="abd6c-777">ESC \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-777">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="abd6c-778">F10</span><span class="sxs-lookup"><span data-stu-id="abd6c-778">F10</span></span> | <span data-ttu-id="abd6c-779">ESC \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-779">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="abd6c-780">F11</span><span class="sxs-lookup"><span data-stu-id="abd6c-780">F11</span></span> | <span data-ttu-id="abd6c-781">ESC \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-781">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="abd6c-782">F12</span><span class="sxs-lookup"><span data-stu-id="abd6c-782">F12</span></span> | <span data-ttu-id="abd6c-783">ESC \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="abd6c-783">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="abd6c-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifizierer</span><span class="sxs-lookup"><span data-stu-id="abd6c-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="abd6c-785">Alt wird behandelt, indem die Sequenz mit einem Escapezeichen versehen wird: Esc &lt; c, &gt; wobei &lt; c &gt; das vom Betriebssystem über gegebene Zeichen ist.</span><span class="sxs-lookup"><span data-stu-id="abd6c-785">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="abd6c-786">Alt + Strg wird auf die gleiche Weise behandelt, außer dass das Betriebssystem den &lt; c-Schlüssel vorab &gt; in das entsprechende Steuerzeichen verschoben hat, das an die Anwendung weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="abd6c-786">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="abd6c-787">STRG wird im allgemeinen genau so durchlaufen, wie vom System empfangen.</span><span class="sxs-lookup"><span data-stu-id="abd6c-787">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="abd6c-788">Dabei handelt es sich in der Regel um ein einzelnes Zeichen, das in den reservierten Leerraum des Steuer Zeichens (0x0-0x1F) verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="abd6c-788">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="abd6c-789">Beispielsweise wird STRG + @ (0x40) zu NUL (0x00), STRG + \[ (0x5b) wird ESC (0x1B) usw. Einige Tastenkombinationen für STRG werden in der folgenden Tabelle speziell behandelt:</span><span class="sxs-lookup"><span data-stu-id="abd6c-789">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="abd6c-790">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="abd6c-790">Key</span></span> | <span data-ttu-id="abd6c-791">Sequenz</span><span class="sxs-lookup"><span data-stu-id="abd6c-791">Sequence</span></span> |
|--------------------|----------------|
| <span data-ttu-id="abd6c-792">STRG+LEERTASTE</span><span class="sxs-lookup"><span data-stu-id="abd6c-792">Ctrl + Space</span></span> | <span data-ttu-id="abd6c-793">0x00 (NUL)</span><span class="sxs-lookup"><span data-stu-id="abd6c-793">0x00 (NUL)</span></span> |
| <span data-ttu-id="abd6c-794">STRG + nach-oben-Taste</span><span class="sxs-lookup"><span data-stu-id="abd6c-794">Ctrl + Up Arrow</span></span> | <span data-ttu-id="abd6c-795">ESC \[ 1; 5 A</span><span class="sxs-lookup"><span data-stu-id="abd6c-795">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="abd6c-796">STRG + nach-unten-Taste</span><span class="sxs-lookup"><span data-stu-id="abd6c-796">Ctrl + Down Arrow</span></span> | <span data-ttu-id="abd6c-797">ESC \[ 1; 5 B</span><span class="sxs-lookup"><span data-stu-id="abd6c-797">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="abd6c-798">STRG + nach-rechts-Taste</span><span class="sxs-lookup"><span data-stu-id="abd6c-798">Ctrl + Right Arrow</span></span> | <span data-ttu-id="abd6c-799">ESC \[ 1; 5 C</span><span class="sxs-lookup"><span data-stu-id="abd6c-799">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="abd6c-800">STRG + nach-links-Taste</span><span class="sxs-lookup"><span data-stu-id="abd6c-800">Ctrl + Left Arrow</span></span> | <span data-ttu-id="abd6c-801">ESC \[ 1; 5 D</span><span class="sxs-lookup"><span data-stu-id="abd6c-801">ESC \[ 1 ; 5 D</span></span> |



> [!NOTE]
><span data-ttu-id="abd6c-802">Left <kbd>STRG</kbd> + right <kbd>alt</kbd> wird als AltGr behandelt.</span><span class="sxs-lookup"><span data-stu-id="abd6c-802">Left <kbd>Ctrl</kbd> + Right <kbd>Alt</kbd> is treated as AltGr.</span></span> <span data-ttu-id="abd6c-803">Wenn beide angezeigt werden, werden Sie entfernt, und der Unicode-Wert des vom System dargestellten Zeichens wird an das Ziel übermittelt.</span><span class="sxs-lookup"><span data-stu-id="abd6c-803">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="abd6c-804">Das System übersetzt AltGr-Werte vorab gemäß den aktuellen System Eingabeeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="abd6c-804">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="abd6c-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Stich</span><span class="sxs-lookup"><span data-stu-id="abd6c-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="abd6c-806"><span id="example"></span><span id="EXAMPLE"></span>Beispiel für SGR-Terminal Sequenzen</span><span class="sxs-lookup"><span data-stu-id="abd6c-806"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="abd6c-807">Der folgende Code enthält mehrere Beispiele für die Textformatierung.</span><span class="sxs-lookup"><span data-stu-id="abd6c-807">The following code provides several examples of text formatting.</span></span>

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
><span data-ttu-id="abd6c-808">Im vorherigen Beispiel ist die Zeichenfolge " `\x1b[31m` " die Implementierung von **ESC \[ &lt; n &gt; m** mit &lt; n &gt; 31.</span><span class="sxs-lookup"><span data-stu-id="abd6c-808">In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="abd6c-809">Die folgende Grafik zeigt die Ausgabe des vorherigen Code Beispiels.</span><span class="sxs-lookup"><span data-stu-id="abd6c-809">The following graphic shows the output of the previous code example.</span></span>

![Ausgabe der Konsole mit dem SGR-Befehl](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="abd6c-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Beispiel für das Aktivieren der virtuellen Terminal Verarbeitung</span><span class="sxs-lookup"><span data-stu-id="abd6c-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="abd6c-812">Der folgende Code enthält ein Beispiel für die empfohlene Vorgehensweise zum Aktivieren der virtuellen Terminal Verarbeitung für eine Anwendung.</span><span class="sxs-lookup"><span data-stu-id="abd6c-812">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="abd6c-813">Das Beispiel soll Folgendes veranschaulichen:</span><span class="sxs-lookup"><span data-stu-id="abd6c-813">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="abd6c-814">Der vorhandene Modus sollte immer über getconsolemode abgerufen und analysiert werden, bevor er mit setconsolemode festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="abd6c-814">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="abd6c-815">Überprüfen, ob setconsolemode zurückgibt `0` und GetLastError den Status " \_ Ungültiger Parameter" zurückgibt \_ , ist der aktuelle Mechanismus zum Bestimmen der Ausführung auf einem System mit einer Ebene</span><span class="sxs-lookup"><span data-stu-id="abd6c-815">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="abd6c-816">Eine Anwendung, die den Status \_ ungültige Parameter empfängt, \_ und eine der neueren Konsolenmodus-Flags im Bitfeld, sollte das Verhalten ordnungsgemäß herabstufen und den Vorgang wiederholen.</span><span class="sxs-lookup"><span data-stu-id="abd6c-816">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="abd6c-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Beispiel für die SELECT Anniversary Update-Features</span><span class="sxs-lookup"><span data-stu-id="abd6c-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="abd6c-818">Das folgende Beispiel soll ein stabileres Codebeispiel sein, bei dem eine Reihe von Escapesequenzen zum Bearbeiten des Puffers verwendet werden, wobei der Schwerpunkt auf den Features liegt, die im Anniversary Update für Windows 10 hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="abd6c-818">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="abd6c-819">In diesem Beispiel wird der Alternative Bildschirm Puffer verwendet, Tabstopps werden bearbeitet, scrollränder werden festgelegt, und der Zeichensatz wird geändert.</span><span class="sxs-lookup"><span data-stu-id="abd6c-819">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

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








