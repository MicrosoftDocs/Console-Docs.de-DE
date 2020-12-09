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
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="1a194-104">Virtuelle Konsolenterminalsequenzen</span><span class="sxs-lookup"><span data-stu-id="1a194-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="1a194-105">Virtuelle Terminalsequenzen sind Steuerzeichenfolgen, die beim Schreiben in den Ausgabestream die Cursorbewegung, Farb-/Schriftartmodus und andere Vorgänge steuern können.</span><span class="sxs-lookup"><span data-stu-id="1a194-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="1a194-106">Sequenzen können im Eingabestream auch als Antwort auf eine Ausgabestream-Abfrageinformationssequenz oder als Codierung von Benutzereingaben empfangen werden, wenn der entsprechende Modus eingestellt ist.</span><span class="sxs-lookup"><span data-stu-id="1a194-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="1a194-107">Mit den Funktionen [**GetConsoleMode**](getconsolemode.md) und [**SetConsoleMode**](setconsolemode.md) können Sie dieses Verhalten konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="1a194-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="1a194-108">Am Ende dieses Dokuments finden Sie ein Beispiel für die vorgeschlagene Methode zur Aktivierung des Verhaltens virtueller Terminals.</span><span class="sxs-lookup"><span data-stu-id="1a194-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="1a194-109">Das Verhalten der folgenden Sequenzen basiert auf den VT100- und abgeleiteten Terminalemulatortechnologien, insbesondere dem xterm-Terminalemulator.</span><span class="sxs-lookup"><span data-stu-id="1a194-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="1a194-110">Weitere Informationen zu Terminalsequenzen finden Sie unter <http://vt100.net> und unter <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span><span class="sxs-lookup"><span data-stu-id="1a194-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="1a194-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Ausgabesequenzen</span><span class="sxs-lookup"><span data-stu-id="1a194-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="1a194-112">Die folgenden Terminalsequenzen werden beim Schreiben in den Ausgabestream vom Konsolenhost abgefangen, wenn das Flag „ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING“ auf dem Bildschirmpufferhandle mit der Funktion [**SetConsoleMode**](setconsolemode.md) festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="1a194-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="1a194-113">Beachten Sie, dass das Flag „DISABLE\_NEWLINE\_AUTO\_RETURN“ auch bei der Emulation des Cursorpositionierungs- und Bildlaufverhaltens anderer Terminalemulatoren in Bezug auf Zeichen nützlich sein kann, die in die letzte Spalte einer beliebigen Zeile geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="1a194-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="1a194-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Einfache Cursorpositionierung</span><span class="sxs-lookup"><span data-stu-id="1a194-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="1a194-115">In allen folgenden Beschreibungen ist ESC immer der hexadezimale Wert 0x1B.</span><span class="sxs-lookup"><span data-stu-id="1a194-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="1a194-116">In Terminalsequenzen dürfen keine Leerzeichen enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="1a194-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="1a194-117">Ein Beispiel dafür, wie diese Sequenzen in der Praxis verwendet werden, finden Sie im [Beispiel](#example) am Ende dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="1a194-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="1a194-118">Die folgende Tabelle beschreibt einfache Escapesequenzen mit einem einzigen Aktionsbefehl direkt nach dem ESC-Zeichen.</span><span class="sxs-lookup"><span data-stu-id="1a194-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="1a194-119">Diese Sequenzen haben keine Parameter und werden sofort wirksam.</span><span class="sxs-lookup"><span data-stu-id="1a194-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="1a194-120">Alle Befehle in dieser Tabelle entsprechen im Allgemeinen dem Aufruf der Konsolen-API [**SetConsoleCursorPosition**](setconsolecursorposition.md) zum Platzieren des Cursors.</span><span class="sxs-lookup"><span data-stu-id="1a194-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="1a194-121">Die Cursorbewegung wird durch den aktuellen Viewport im Puffer begrenzt.</span><span class="sxs-lookup"><span data-stu-id="1a194-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="1a194-122">Es erfolgt kein Bildlauf (falls verfügbar).</span><span class="sxs-lookup"><span data-stu-id="1a194-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="1a194-123">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-123">Sequence</span></span> | <span data-ttu-id="1a194-124">Kompakt</span><span class="sxs-lookup"><span data-stu-id="1a194-124">Shorthand</span></span> | <span data-ttu-id="1a194-125">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-125">Behavior</span></span> |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a194-126">ESC A</span><span class="sxs-lookup"><span data-stu-id="1a194-126">ESC A</span></span> | <span data-ttu-id="1a194-127">CUU</span><span class="sxs-lookup"><span data-stu-id="1a194-127">CUU</span></span> | <span data-ttu-id="1a194-128">Cursor um 1 nach oben</span><span class="sxs-lookup"><span data-stu-id="1a194-128">Cursor Up by 1</span></span> |
| <span data-ttu-id="1a194-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="1a194-129">ESC B</span></span> | <span data-ttu-id="1a194-130">CUD</span><span class="sxs-lookup"><span data-stu-id="1a194-130">CUD</span></span> | <span data-ttu-id="1a194-131">Cursor um 1 nach unten</span><span class="sxs-lookup"><span data-stu-id="1a194-131">Cursor Down by 1</span></span> |
| <span data-ttu-id="1a194-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="1a194-132">ESC C</span></span> | <span data-ttu-id="1a194-133">CUF</span><span class="sxs-lookup"><span data-stu-id="1a194-133">CUF</span></span> | <span data-ttu-id="1a194-134">Cursor um 1 vorwärts (nach rechts)</span><span class="sxs-lookup"><span data-stu-id="1a194-134">Cursor Forward (Right) by 1</span></span> |
| <span data-ttu-id="1a194-135">ESC D</span><span class="sxs-lookup"><span data-stu-id="1a194-135">ESC D</span></span> | <span data-ttu-id="1a194-136">CUB</span><span class="sxs-lookup"><span data-stu-id="1a194-136">CUB</span></span> | <span data-ttu-id="1a194-137">Cursor um 1 zurück (nach links)</span><span class="sxs-lookup"><span data-stu-id="1a194-137">Cursor Backward (Left) by 1</span></span> |
| <span data-ttu-id="1a194-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="1a194-138">ESC M</span></span> | <span data-ttu-id="1a194-139">RI</span><span class="sxs-lookup"><span data-stu-id="1a194-139">RI</span></span> | <span data-ttu-id="1a194-140">Umgekehrter Index: Führt den Umkehrvorgang von \\n aus, bewegt den Cursor eine Zeile nach oben, behält die horizontale Position bei, scrollt im Puffer, falls erforderlich\*</span><span class="sxs-lookup"><span data-stu-id="1a194-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="1a194-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="1a194-141">ESC 7</span></span> | <span data-ttu-id="1a194-142">DECSC</span><span class="sxs-lookup"><span data-stu-id="1a194-142">DECSC</span></span> | <span data-ttu-id="1a194-143">Cursorposition im Arbeitsspeicher speichern\*\*</span><span class="sxs-lookup"><span data-stu-id="1a194-143">Save Cursor Position in Memory\*\*</span></span> |
| <span data-ttu-id="1a194-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="1a194-144">ESC 8</span></span> | <span data-ttu-id="1a194-145">DECSR</span><span class="sxs-lookup"><span data-stu-id="1a194-145">DECSR</span></span> | <span data-ttu-id="1a194-146">Cursorposition aus dem Arbeitsspeicher wiederherstellen\*\*</span><span class="sxs-lookup"><span data-stu-id="1a194-146">Restore Cursor Position from Memory\*\*</span></span> |



> [!NOTE]
><span data-ttu-id="1a194-147">\* Wenn Bildlaufränder festgelegt sind, scrollt RI innerhalb der Ränder nur den Inhalt und lässt den Viewport unverändert.</span><span class="sxs-lookup"><span data-stu-id="1a194-147">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="1a194-148">(Siehe Bildlaufränder)</span><span class="sxs-lookup"><span data-stu-id="1a194-148">(See Scrolling Margins)</span></span>
>
><span data-ttu-id="1a194-149">\*\*Es wird kein Wert im Arbeitsspeicher gespeichert, bis der Befehl zum Speichern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1a194-149">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="1a194-150">Die einzige Möglichkeit, auf den gespeicherten Wert zuzugreifen, ist der Befehl zum Wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="1a194-150">The only way to access the saved value is with the restore command.</span></span>

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="1a194-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursorposition</span><span class="sxs-lookup"><span data-stu-id="1a194-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="1a194-152">Die folgenden Tabellen umfassen Sequenzen vom Typ „Einführungszeichen für Steuerungssequenz“ (CSI).</span><span class="sxs-lookup"><span data-stu-id="1a194-152">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="1a194-153">Alle CSI-Sequenzen beginnen mit ESC (0x1B), gefolgt von \[ (linke eckige Klammer, 0x5b) und können Parameter variabler Länge enthalten, um für jeden Vorgang weitere Informationen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="1a194-153">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="1a194-154">Dies wird durch das kompakte &lt;n&gt; dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1a194-154">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="1a194-155">Die Tabellen unten sind nach Funktionalität gruppiert, wobei Hinweise unter den einzelnen Tabellen die Funktionsweise der Gruppe erläutern.</span><span class="sxs-lookup"><span data-stu-id="1a194-155">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="1a194-156">Für alle Parameter gelten die folgenden Regeln, sofern nichts anderes angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="1a194-156">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="1a194-157">&lt;n&gt; stellt den Abstand der Verschiebung dar und ist ein optionaler Parameter.</span><span class="sxs-lookup"><span data-stu-id="1a194-157">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="1a194-158">Wenn &lt;n&gt; ausgelassen wird oder „0“ (null) ist, wird es wie „1“ behandelt.</span><span class="sxs-lookup"><span data-stu-id="1a194-158">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="1a194-159">&lt;n&gt; darf nicht größer als 32.767 (maximaler kurzer Wert) sein.</span><span class="sxs-lookup"><span data-stu-id="1a194-159">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="1a194-160">&lt;n&gt; darf nicht negativ sein.</span><span class="sxs-lookup"><span data-stu-id="1a194-160">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="1a194-161">Alle Befehle in diesem Abschnitt entsprechen im Allgemeinen dem Aufruf der Konsolen-API [**SetConsoleCursorPosition**](setconsolecursorposition.md).</span><span class="sxs-lookup"><span data-stu-id="1a194-161">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="1a194-162">Die Cursorbewegung wird durch den aktuellen Viewport im Puffer begrenzt.</span><span class="sxs-lookup"><span data-stu-id="1a194-162">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="1a194-163">Es erfolgt kein Bildlauf (falls verfügbar).</span><span class="sxs-lookup"><span data-stu-id="1a194-163">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="1a194-164">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-164">Sequence</span></span> | <span data-ttu-id="1a194-165">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-165">Code</span></span> | <span data-ttu-id="1a194-166">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-166">Description</span></span> | <span data-ttu-id="1a194-167">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-167">Behavior</span></span> |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a194-168">ESC \[ &lt;n&gt; A</span><span class="sxs-lookup"><span data-stu-id="1a194-168">ESC \[ &lt;n&gt; A</span></span> | <span data-ttu-id="1a194-169">CUU</span><span class="sxs-lookup"><span data-stu-id="1a194-169">CUU</span></span> | <span data-ttu-id="1a194-170">Cursor nach oben</span><span class="sxs-lookup"><span data-stu-id="1a194-170">Cursor Up</span></span> | <span data-ttu-id="1a194-171">Cursor wird um &lt;n&gt; nach oben bewegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-171">Cursor up by &lt;n&gt;</span></span> |
| <span data-ttu-id="1a194-172">ESC \[ &lt;n&gt; B</span><span class="sxs-lookup"><span data-stu-id="1a194-172">ESC \[ &lt;n&gt; B</span></span> | <span data-ttu-id="1a194-173">CUD</span><span class="sxs-lookup"><span data-stu-id="1a194-173">CUD</span></span> | <span data-ttu-id="1a194-174">Cursor nach unten</span><span class="sxs-lookup"><span data-stu-id="1a194-174">Cursor Down</span></span> | <span data-ttu-id="1a194-175">Cursor wird um &lt;n&gt; nach unten bewegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-175">Cursor down by &lt;n&gt;</span></span> |
| <span data-ttu-id="1a194-176">ESC \[ &lt;n&gt; C</span><span class="sxs-lookup"><span data-stu-id="1a194-176">ESC \[ &lt;n&gt; C</span></span> | <span data-ttu-id="1a194-177">CUF</span><span class="sxs-lookup"><span data-stu-id="1a194-177">CUF</span></span> | <span data-ttu-id="1a194-178">Cursor vorwärts</span><span class="sxs-lookup"><span data-stu-id="1a194-178">Cursor Forward</span></span> | <span data-ttu-id="1a194-179">Cursor wird um &lt;n&gt; vorwärts (nach rechts) bewegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-179">Cursor forward (Right) by &lt;n&gt;</span></span> |
| <span data-ttu-id="1a194-180">ESC \[ &lt;n&gt; D</span><span class="sxs-lookup"><span data-stu-id="1a194-180">ESC \[ &lt;n&gt; D</span></span> | <span data-ttu-id="1a194-181">CUB</span><span class="sxs-lookup"><span data-stu-id="1a194-181">CUB</span></span> | <span data-ttu-id="1a194-182">Cursor zurück</span><span class="sxs-lookup"><span data-stu-id="1a194-182">Cursor Backward</span></span> | <span data-ttu-id="1a194-183">Cursor wird um &lt;n&gt; zurück (nach links) bewegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-183">Cursor backward (Left) by &lt;n&gt;</span></span> |
| <span data-ttu-id="1a194-184">ESC \[ &lt;n&gt; E</span><span class="sxs-lookup"><span data-stu-id="1a194-184">ESC \[ &lt;n&gt; E</span></span> | <span data-ttu-id="1a194-185">CNL</span><span class="sxs-lookup"><span data-stu-id="1a194-185">CNL</span></span> | <span data-ttu-id="1a194-186">Cursor nächste Zeile</span><span class="sxs-lookup"><span data-stu-id="1a194-186">Cursor Next Line</span></span> | <span data-ttu-id="1a194-187">Cursor wird von der aktuellen Position aus &lt;n&gt; Zeilen nach unten bewegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-187">Cursor down &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="1a194-188">ESC \[ &lt;n&gt; F</span><span class="sxs-lookup"><span data-stu-id="1a194-188">ESC \[ &lt;n&gt; F</span></span> | <span data-ttu-id="1a194-189">CPL</span><span class="sxs-lookup"><span data-stu-id="1a194-189">CPL</span></span> | <span data-ttu-id="1a194-190">Cursor vorherige Zeile</span><span class="sxs-lookup"><span data-stu-id="1a194-190">Cursor Previous Line</span></span> | <span data-ttu-id="1a194-191">Cursor wird von der aktuellen Position aus &lt;n&gt; Zeilen nach oben bewegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-191">Cursor up &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="1a194-192">ESC \[ &lt;n&gt; G</span><span class="sxs-lookup"><span data-stu-id="1a194-192">ESC \[ &lt;n&gt; G</span></span> | <span data-ttu-id="1a194-193">CHA</span><span class="sxs-lookup"><span data-stu-id="1a194-193">CHA</span></span> | <span data-ttu-id="1a194-194">Cursor horizontal absolut</span><span class="sxs-lookup"><span data-stu-id="1a194-194">Cursor Horizontal Absolute</span></span> | <span data-ttu-id="1a194-195">Cursor wird horizontal in der aktuellen Zeile zur &lt;n&gt;-ten Position bewegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-195">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span> |
| <span data-ttu-id="1a194-196">ESC \[ &lt;n&gt; d</span><span class="sxs-lookup"><span data-stu-id="1a194-196">ESC \[ &lt;n&gt; d</span></span> | <span data-ttu-id="1a194-197">VPA</span><span class="sxs-lookup"><span data-stu-id="1a194-197">VPA</span></span> | <span data-ttu-id="1a194-198">Vertikale Zeile Position absolut</span><span class="sxs-lookup"><span data-stu-id="1a194-198">Vertical Line Position Absolute</span></span> | <span data-ttu-id="1a194-199">Cursor wird vertikal in der aktuellen Spalte zur &lt;n&gt;-ten Position bewegt</span><span class="sxs-lookup"><span data-stu-id="1a194-199">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span> |
| <span data-ttu-id="1a194-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span><span class="sxs-lookup"><span data-stu-id="1a194-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="1a194-201">CUP</span><span class="sxs-lookup"><span data-stu-id="1a194-201">CUP</span></span> | <span data-ttu-id="1a194-202">Cursorposition</span><span class="sxs-lookup"><span data-stu-id="1a194-202">Cursor Position</span></span> | <span data-ttu-id="1a194-203">\*Cursor wird zu &lt;x&gt;; &lt;y&gt;-Koordinate innerhalb des Viewports bewegt, wobei &lt;x&gt; die Spalte der Zeile &lt;y&gt; ist.</span><span class="sxs-lookup"><span data-stu-id="1a194-203">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="1a194-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span><span class="sxs-lookup"><span data-stu-id="1a194-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="1a194-205">HVP</span><span class="sxs-lookup"><span data-stu-id="1a194-205">HVP</span></span> | <span data-ttu-id="1a194-206">Horizontale vertikale Position</span><span class="sxs-lookup"><span data-stu-id="1a194-206">Horizontal Vertical Position</span></span> | <span data-ttu-id="1a194-207">\*Cursor wird zu &lt;x&gt;; &lt;y&gt;-Koordinate innerhalb des Viewports bewegt, wobei &lt;x&gt; die Spalte der Zeile &lt;y&gt; ist.</span><span class="sxs-lookup"><span data-stu-id="1a194-207">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="1a194-208">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="1a194-208">ESC \[ s</span></span> | <span data-ttu-id="1a194-209">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="1a194-209">ANSISYSSC</span></span> | <span data-ttu-id="1a194-210">Cursor speichern – Ansi.sys-Emulation</span><span class="sxs-lookup"><span data-stu-id="1a194-210">Save Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="1a194-211">\*\*Ohne Parameter; führt einen Vorgang zum Speichern des Cursors aus, z. B. DECSC</span><span class="sxs-lookup"><span data-stu-id="1a194-211">\*\*With no parameters, performs a save cursor operation like DECSC</span></span> |
| <span data-ttu-id="1a194-212">ESC \[ u</span><span class="sxs-lookup"><span data-stu-id="1a194-212">ESC \[ u</span></span> | <span data-ttu-id="1a194-213">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="1a194-213">ANSISYSSC</span></span> | <span data-ttu-id="1a194-214">Cursor wiederherstellen – Ansi.sys-Emulation</span><span class="sxs-lookup"><span data-stu-id="1a194-214">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="1a194-215">\*\*Ohne Parameter; führt einen Vorgang zum Wiederherstellen des Cursors aus, z. B. DECRC</span><span class="sxs-lookup"><span data-stu-id="1a194-215">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span> |



> [!NOTE]
><span data-ttu-id="1a194-216">\*Parameter &lt;x&gt; und &lt;y&gt; weisen die gleichen Begrenzungen wie &lt;n&gt; oben auf.</span><span class="sxs-lookup"><span data-stu-id="1a194-216">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="1a194-217">Wenn &lt;x&gt; und &lt;y&gt; weggelassen werden, werden sie auf „1;1“ festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-217">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>
>
><span data-ttu-id="1a194-218">\*\*Die historische Dokumentation von ANSI.sys ist unter <https://msdn.microsoft.com/library/cc722862.aspx> zu finden und wurde zur Hilfe/Kompatibilität implementiert.</span><span class="sxs-lookup"><span data-stu-id="1a194-218">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="1a194-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursorsichtbarkeit</span><span class="sxs-lookup"><span data-stu-id="1a194-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="1a194-220">Die folgenden Befehle steuern die Sichtbarkeit des Cursors und seinen blinkenden Zustand.</span><span class="sxs-lookup"><span data-stu-id="1a194-220">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="1a194-221">Die DECTCEM-Sequenzen entsprechen in der Regel dem Aufruf der Konsolen-API [**SetConsoleCursorInfo**](setconsolecursorinfo.md) zum Aktivieren/Deaktivieren der Cursorsichtbarkeit.</span><span class="sxs-lookup"><span data-stu-id="1a194-221">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="1a194-222">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-222">Sequence</span></span> | <span data-ttu-id="1a194-223">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-223">Code</span></span> | <span data-ttu-id="1a194-224">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-224">Description</span></span> | <span data-ttu-id="1a194-225">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-225">Behavior</span></span> |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="1a194-226">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="1a194-226">ESC \[ ?</span></span> <span data-ttu-id="1a194-227">12 Stunden</span><span class="sxs-lookup"><span data-stu-id="1a194-227">12 h</span></span> | <span data-ttu-id="1a194-228">ATT160</span><span class="sxs-lookup"><span data-stu-id="1a194-228">ATT160</span></span> | <span data-ttu-id="1a194-229">Blinken des Textcursors aktivieren</span><span class="sxs-lookup"><span data-stu-id="1a194-229">Text Cursor Enable Blinking</span></span> | <span data-ttu-id="1a194-230">Cursor blinkt.</span><span class="sxs-lookup"><span data-stu-id="1a194-230">Start the cursor blinking</span></span> |
| <span data-ttu-id="1a194-231">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="1a194-231">ESC \[ ?</span></span> <span data-ttu-id="1a194-232">12 l</span><span class="sxs-lookup"><span data-stu-id="1a194-232">12 l</span></span> | <span data-ttu-id="1a194-233">ATT160</span><span class="sxs-lookup"><span data-stu-id="1a194-233">ATT160</span></span> | <span data-ttu-id="1a194-234">Blinken des Textcursors deaktivieren</span><span class="sxs-lookup"><span data-stu-id="1a194-234">Text Cursor Disable Blinking</span></span> | <span data-ttu-id="1a194-235">Cursor blinkt nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="1a194-235">Stop blinking the cursor</span></span> |
| <span data-ttu-id="1a194-236">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="1a194-236">ESC \[ ?</span></span> <span data-ttu-id="1a194-237">25 h</span><span class="sxs-lookup"><span data-stu-id="1a194-237">25 h</span></span> | <span data-ttu-id="1a194-238">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="1a194-238">DECTCEM</span></span> | <span data-ttu-id="1a194-239">Anzeigen-Modus des Textcursors aktivieren</span><span class="sxs-lookup"><span data-stu-id="1a194-239">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="1a194-240">Cursor wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1a194-240">Show the cursor</span></span> |
| <span data-ttu-id="1a194-241">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="1a194-241">ESC \[ ?</span></span> <span data-ttu-id="1a194-242">25 l</span><span class="sxs-lookup"><span data-stu-id="1a194-242">25 l</span></span> | <span data-ttu-id="1a194-243">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="1a194-243">DECTCEM</span></span> | <span data-ttu-id="1a194-244">Ausblenden-Modus des Textcursors aktivieren</span><span class="sxs-lookup"><span data-stu-id="1a194-244">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="1a194-245">Cursor wird ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="1a194-245">Hide the cursor</span></span> |

> [!TIP]
> <span data-ttu-id="1a194-246">Aktivierungssequenzen enden mit dem Kleinbuchstaben `h`, und Deaktivierungssequenzen enden mit dem Kleinbuchstaben `l`.</span><span class="sxs-lookup"><span data-stu-id="1a194-246">The enable sequences end in a lowercase H character (`h`) and the disable sequences end in a lowercase L character (`l`).</span></span>

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="1a194-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewportpositionierung</span><span class="sxs-lookup"><span data-stu-id="1a194-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="1a194-248">Alle Befehle in diesem Abschnitt entsprechen im Allgemeinen dem Aufruf der Konsolen-API [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) zum Verschieben des Inhalts des Konsolenpuffers.</span><span class="sxs-lookup"><span data-stu-id="1a194-248">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="1a194-249">**Vorsicht** Die Befehlsnamen sind irreführend.</span><span class="sxs-lookup"><span data-stu-id="1a194-249">**Caution** The command names are misleading.</span></span> <span data-ttu-id="1a194-250">Bildlauf (bzw. Scrollen) bezieht sich darauf, in welche Richtung sich der Text während des Vorgangs bewegt, nicht darauf, in welche Richtung sich der Viewport zu bewegen scheint.</span><span class="sxs-lookup"><span data-stu-id="1a194-250">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="1a194-251">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-251">Sequence</span></span> | <span data-ttu-id="1a194-252">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-252">Code</span></span> | <span data-ttu-id="1a194-253">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-253">Description</span></span> | <span data-ttu-id="1a194-254">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-254">Behavior</span></span> |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a194-255">ESC \[ &lt;n&gt; S</span><span class="sxs-lookup"><span data-stu-id="1a194-255">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="1a194-256">SU</span><span class="sxs-lookup"><span data-stu-id="1a194-256">SU</span></span> | <span data-ttu-id="1a194-257">Bildlauf nach oben</span><span class="sxs-lookup"><span data-stu-id="1a194-257">Scroll Up</span></span> | <span data-ttu-id="1a194-258">Text wird um &lt;n&gt; nach oben gescrollt.</span><span class="sxs-lookup"><span data-stu-id="1a194-258">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="1a194-259">Auch als „Nach unten schwenken“ bezeichnet; der Bildschirm wird von unten her mit neuen Zeilen gefüllt.</span><span class="sxs-lookup"><span data-stu-id="1a194-259">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="1a194-260">ESC \[ &lt;n&gt; T</span><span class="sxs-lookup"><span data-stu-id="1a194-260">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="1a194-261">SD</span><span class="sxs-lookup"><span data-stu-id="1a194-261">SD</span></span> | <span data-ttu-id="1a194-262">Bildlauf nach unten</span><span class="sxs-lookup"><span data-stu-id="1a194-262">Scroll Down</span></span> | <span data-ttu-id="1a194-263">Text wird um &lt;n&gt; nach unten gescrollt.</span><span class="sxs-lookup"><span data-stu-id="1a194-263">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="1a194-264">Auch als „Nach oben schwenken“ bezeichnet; der Bildschirm wird von oben her mit neuen Zeilen gefüllt.</span><span class="sxs-lookup"><span data-stu-id="1a194-264">Also known as pan up, new lines fill in from the top of the screen</span></span> |



<span data-ttu-id="1a194-265">Der Text wird beginnend mit der Zeile, in der sich der Cursor befindet, verschoben.</span><span class="sxs-lookup"><span data-stu-id="1a194-265">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="1a194-266">Wenn sich der Cursor in der mittleren Zeile des Viewports befindet, verschiebt der „Nach oben scrollen“ die untere Hälfte des Viewports und fügt unten leere Zeilen ein.</span><span class="sxs-lookup"><span data-stu-id="1a194-266">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="1a194-267">„Nach unten scrollen“ verschiebt die obere Hälfte der Zeilen des Viewports, und fügt oben neue Zeilen ein.</span><span class="sxs-lookup"><span data-stu-id="1a194-267">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="1a194-268">Wichtig zu beachten ist zudem, dass „Nach oben scrollen“ und „Nach unten scrollen“ auch durch die Bildlaufränder betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="1a194-268">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="1a194-269">Die Aktionen „Nach oben scrollen“ und „Nach unten scrollen“ wirken sich nicht auf Zeilen außerhalb der Bildlaufränder aus.</span><span class="sxs-lookup"><span data-stu-id="1a194-269">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="1a194-270">Der Standardwert für &lt;n&gt; ist „1“, und der Wert kann optional weggelassen werden.</span><span class="sxs-lookup"><span data-stu-id="1a194-270">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="1a194-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Textänderung</span><span class="sxs-lookup"><span data-stu-id="1a194-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="1a194-272">Alle Befehle in diesem Abschnitt entsprechen im Allgemeinen dem Aufruf der Konsolen-APIs [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) und [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) zum Ändern des Textpufferinhalts.</span><span class="sxs-lookup"><span data-stu-id="1a194-272">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="1a194-273">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-273">Sequence</span></span> | <span data-ttu-id="1a194-274">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-274">Code</span></span> | <span data-ttu-id="1a194-275">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-275">Description</span></span> | <span data-ttu-id="1a194-276">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-276">Behavior</span></span> |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a194-277">ESC \[ &lt;n&gt; @</span><span class="sxs-lookup"><span data-stu-id="1a194-277">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="1a194-278">ICH</span><span class="sxs-lookup"><span data-stu-id="1a194-278">ICH</span></span> | <span data-ttu-id="1a194-279">Zeichen einfügen</span><span class="sxs-lookup"><span data-stu-id="1a194-279">Insert Character</span></span> | <span data-ttu-id="1a194-280">Fügt &lt;n&gt; Leerzeichen an der aktuellen Cursorposition ein und verschiebt den gesamten vorhandenen Text nach rechts.</span><span class="sxs-lookup"><span data-stu-id="1a194-280">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="1a194-281">Text, der den Bildschirm rechts verlässt, wird entfernt.</span><span class="sxs-lookup"><span data-stu-id="1a194-281">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="1a194-282">ESC \[ &lt;n&gt; P</span><span class="sxs-lookup"><span data-stu-id="1a194-282">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="1a194-283">DCH</span><span class="sxs-lookup"><span data-stu-id="1a194-283">DCH</span></span> | <span data-ttu-id="1a194-284">Zeichen löschen</span><span class="sxs-lookup"><span data-stu-id="1a194-284">Delete Character</span></span> | <span data-ttu-id="1a194-285">Löscht &lt;n&gt; Zeichen an der aktuellen Cursorposition und schiebt vom rechten Bildschirmrand aus Leerzeichen hinein.</span><span class="sxs-lookup"><span data-stu-id="1a194-285">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span> |
| <span data-ttu-id="1a194-286">ESC \[ &lt;n&gt; X</span><span class="sxs-lookup"><span data-stu-id="1a194-286">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="1a194-287">ECH</span><span class="sxs-lookup"><span data-stu-id="1a194-287">ECH</span></span> | <span data-ttu-id="1a194-288">Zeichen überschreiben</span><span class="sxs-lookup"><span data-stu-id="1a194-288">Erase Character</span></span> | <span data-ttu-id="1a194-289">Überschreibt &lt;n&gt; Zeichen von der aktuellen Cursorposition mit einem Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="1a194-289">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span> |
| <span data-ttu-id="1a194-290">ESC \[ &lt;n&gt; L</span><span class="sxs-lookup"><span data-stu-id="1a194-290">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="1a194-291">IL</span><span class="sxs-lookup"><span data-stu-id="1a194-291">IL</span></span> | <span data-ttu-id="1a194-292">Zeile einfügen</span><span class="sxs-lookup"><span data-stu-id="1a194-292">Insert Line</span></span> | <span data-ttu-id="1a194-293">Fügt an der Cursorposition &lt;n&gt; Zeilen in den Puffer ein.</span><span class="sxs-lookup"><span data-stu-id="1a194-293">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="1a194-294">Die Zeile, in der sich der Cursor befindet, und die darunter liegenden Zeilen werden nach unten verschoben.</span><span class="sxs-lookup"><span data-stu-id="1a194-294">The line the cursor is on, and lines below it, will be shifted downwards.</span></span> |
| <span data-ttu-id="1a194-295">ESC \[ &lt;n&gt; M</span><span class="sxs-lookup"><span data-stu-id="1a194-295">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="1a194-296">DL</span><span class="sxs-lookup"><span data-stu-id="1a194-296">DL</span></span> | <span data-ttu-id="1a194-297">Zeile löschen</span><span class="sxs-lookup"><span data-stu-id="1a194-297">Delete Line</span></span> | <span data-ttu-id="1a194-298">Löscht &lt;n&gt; Zeilen aus dem Puffer, beginnend mit der Zeile, in der sich der Cursor befindet.</span><span class="sxs-lookup"><span data-stu-id="1a194-298">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span> |



> [!NOTE]
><span data-ttu-id="1a194-299">Bei IL und DL sind nur die Zeilen innerhalb der Bildlaufränder (siehe „Bildlaufränder“) betroffen.</span><span class="sxs-lookup"><span data-stu-id="1a194-299">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="1a194-300">Sind keine Ränder festgelegt, sind die Rahmen des Standardrands der aktuelle Viewport.</span><span class="sxs-lookup"><span data-stu-id="1a194-300">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="1a194-301">Werden Zeilen unter die Ränder verschoben, werden Sie verworfen.</span><span class="sxs-lookup"><span data-stu-id="1a194-301">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="1a194-302">Werden Zeilen gelöscht, werden am unteren Rand leere Zeilen eingefügt; Zeilen außerhalb des Viewports sind davon nie betroffen.</span><span class="sxs-lookup"><span data-stu-id="1a194-302">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="1a194-303">Der Standardwert für &lt;n&gt; ist „0“, wenn kein Wert festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="1a194-303">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="1a194-304">Für die folgenden Befehle hat der Parameter &lt;n&gt; 3 gültige Werte:</span><span class="sxs-lookup"><span data-stu-id="1a194-304">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="1a194-305">0 löscht von der aktuellen Cursorposition (einschließlich) bis zum Ende der Zeile/Anzeige.</span><span class="sxs-lookup"><span data-stu-id="1a194-305">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="1a194-306">1 löscht vom Anfang der Zeile/Anzeige bis zur aktuellen Cursorposition (einschließlich).</span><span class="sxs-lookup"><span data-stu-id="1a194-306">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="1a194-307">2 löscht die gesamte Zeile/Anzeige.</span><span class="sxs-lookup"><span data-stu-id="1a194-307">2 erases the entire line/display</span></span>


| <span data-ttu-id="1a194-308">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-308">Sequence</span></span> | <span data-ttu-id="1a194-309">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-309">Code</span></span> | <span data-ttu-id="1a194-310">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-310">Description</span></span> | <span data-ttu-id="1a194-311">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-311">Behavior</span></span> |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a194-312">ESC \[ &lt;n&gt; J</span><span class="sxs-lookup"><span data-stu-id="1a194-312">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="1a194-313">ED</span><span class="sxs-lookup"><span data-stu-id="1a194-313">ED</span></span> | <span data-ttu-id="1a194-314">In Anzeige überschreiben</span><span class="sxs-lookup"><span data-stu-id="1a194-314">Erase in Display</span></span> | <span data-ttu-id="1a194-315">Ersetzt den gesamten durch &lt;n&gt; angegebenen Text im aktuellen Viewport/Bildschirm durch Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="1a194-315">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="1a194-316">ESC \[ &lt;n&gt; K</span><span class="sxs-lookup"><span data-stu-id="1a194-316">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="1a194-317">EL</span><span class="sxs-lookup"><span data-stu-id="1a194-317">EL</span></span> | <span data-ttu-id="1a194-318">In Zeile überschreiben</span><span class="sxs-lookup"><span data-stu-id="1a194-318">Erase in Line</span></span> | <span data-ttu-id="1a194-319">Ersetzt den gesamten Text in der Zeile mit dem durch &lt;n&gt; angegebenen Cursor durch Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="1a194-319">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span> |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="1a194-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Textformatierung</span><span class="sxs-lookup"><span data-stu-id="1a194-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="1a194-321">Alle Befehle in diesem Abschnitt entsprechen im Allgemeinen dem Aufruf der Konsolen-API [**SetConsoleTextAttribute**](setconsoletextattribute.md) zum Anpassen der Formatierung aller zukünftigen Schreibvorgänge im Textpuffer der Konsolenausgabe.</span><span class="sxs-lookup"><span data-stu-id="1a194-321">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="1a194-322">Dieser Befehl ist insofern speziell, als dass die Position &lt;n&gt; unten zwischen 0 und 16 durch Semikolons getrennte Parameter annehmen kann.</span><span class="sxs-lookup"><span data-stu-id="1a194-322">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="1a194-323">Werden keine Parameter angegeben, wird der Befehl so behandelt, als ob als einziges der 0-Parameter angegeben wäre.</span><span class="sxs-lookup"><span data-stu-id="1a194-323">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="1a194-324">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-324">Sequence</span></span> | <span data-ttu-id="1a194-325">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-325">Code</span></span> | <span data-ttu-id="1a194-326">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-326">Description</span></span> | <span data-ttu-id="1a194-327">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-327">Behavior</span></span> |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="1a194-328">ESC \[ &lt;n&gt; m</span><span class="sxs-lookup"><span data-stu-id="1a194-328">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="1a194-329">SGR</span><span class="sxs-lookup"><span data-stu-id="1a194-329">SGR</span></span> | <span data-ttu-id="1a194-330">Grafikwiedergabe festlegen</span><span class="sxs-lookup"><span data-stu-id="1a194-330">Set Graphics Rendition</span></span> | <span data-ttu-id="1a194-331">Legt das Format des Bildschirms und des Texts wie durch &lt;n&gt; angegeben fest.</span><span class="sxs-lookup"><span data-stu-id="1a194-331">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="1a194-332">Die folgende Tabelle mit Werten kann in &lt;n&gt; verwendet werden, um verschiedene Formatierungsmodi darzustellen.</span><span class="sxs-lookup"><span data-stu-id="1a194-332">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="1a194-333">Formatierungsmodi werden von links nach rechts angewendet.</span><span class="sxs-lookup"><span data-stu-id="1a194-333">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="1a194-334">Wenn Sie konkurrierende Formatierungsoptionen anwenden, führt dies dazu, dass jeweils die Option Vorrang hat, die am weitesten rechts angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="1a194-334">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="1a194-335">Für Optionen, die Farben angeben, werden die Farben entsprechend der Definition in der Konsolenfarbtabelle verwendet, die mithilfe der [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)-API geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="1a194-335">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="1a194-336">Wenn die Tabelle so geändert wird, dass die „blaue“ Position in der Tabelle einen RGB-Rotton anzeigt, dann werden alle Aufrufe von **Foreground Blue** diesen Rotton anzeigen, bis sie anderweitig geändert werden.</span><span class="sxs-lookup"><span data-stu-id="1a194-336">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="1a194-337">Wert</span><span class="sxs-lookup"><span data-stu-id="1a194-337">Value</span></span> | <span data-ttu-id="1a194-338">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-338">Description</span></span> | <span data-ttu-id="1a194-339">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-339">Behavior</span></span> |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="1a194-340">0</span><span class="sxs-lookup"><span data-stu-id="1a194-340">0</span></span> | <span data-ttu-id="1a194-341">Standard</span><span class="sxs-lookup"><span data-stu-id="1a194-341">Default</span></span> | <span data-ttu-id="1a194-342">Setzt alle Attribute auf den Standardzustand vor der Änderung zurück.</span><span class="sxs-lookup"><span data-stu-id="1a194-342">Returns all attributes to the default state prior to modification</span></span> |
| <span data-ttu-id="1a194-343">1</span><span class="sxs-lookup"><span data-stu-id="1a194-343">1</span></span> | <span data-ttu-id="1a194-344">Intensiv/leuchtend</span><span class="sxs-lookup"><span data-stu-id="1a194-344">Bold/Bright</span></span> | <span data-ttu-id="1a194-345">Wendet das Flag für Helligkeit/Intensität auf Vordergrundfarbe an.</span><span class="sxs-lookup"><span data-stu-id="1a194-345">Applies brightness/intensity flag to foreground color</span></span> |
| <span data-ttu-id="1a194-346">4</span><span class="sxs-lookup"><span data-stu-id="1a194-346">4</span></span> | <span data-ttu-id="1a194-347">Underline</span><span class="sxs-lookup"><span data-stu-id="1a194-347">Underline</span></span> | <span data-ttu-id="1a194-348">Fügt eine Unterstreichung hinzu.</span><span class="sxs-lookup"><span data-stu-id="1a194-348">Adds underline</span></span> |
| <span data-ttu-id="1a194-349">24</span><span class="sxs-lookup"><span data-stu-id="1a194-349">24</span></span> | <span data-ttu-id="1a194-350">Keine Unterstreichung</span><span class="sxs-lookup"><span data-stu-id="1a194-350">No underline</span></span> | <span data-ttu-id="1a194-351">Entfernt die Unterstreichung.</span><span class="sxs-lookup"><span data-stu-id="1a194-351">Removes underline</span></span> |
| <span data-ttu-id="1a194-352">7</span><span class="sxs-lookup"><span data-stu-id="1a194-352">7</span></span> | <span data-ttu-id="1a194-353">Negativ</span><span class="sxs-lookup"><span data-stu-id="1a194-353">Negative</span></span> | <span data-ttu-id="1a194-354">Tauscht Vordergrund- und Hintergrundfarbe.</span><span class="sxs-lookup"><span data-stu-id="1a194-354">Swaps foreground and background colors</span></span> |
| <span data-ttu-id="1a194-355">27</span><span class="sxs-lookup"><span data-stu-id="1a194-355">27</span></span> | <span data-ttu-id="1a194-356">Positiv (kein Negativ)</span><span class="sxs-lookup"><span data-stu-id="1a194-356">Positive (No negative)</span></span> | <span data-ttu-id="1a194-357">Setzt Vordergrund-/Hintergrundfarbe wieder auf normal zurück.</span><span class="sxs-lookup"><span data-stu-id="1a194-357">Returns foreground/background to normal</span></span> |
| <span data-ttu-id="1a194-358">30</span><span class="sxs-lookup"><span data-stu-id="1a194-358">30</span></span> | <span data-ttu-id="1a194-359">Vordergrund Schwarz</span><span class="sxs-lookup"><span data-stu-id="1a194-359">Foreground Black</span></span> | <span data-ttu-id="1a194-360">Wendet Schwarz (nicht intensiv/leuchtend) auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-360">Applies non-bold/bright black to foreground</span></span> |
| <span data-ttu-id="1a194-361">31</span><span class="sxs-lookup"><span data-stu-id="1a194-361">31</span></span> | <span data-ttu-id="1a194-362">Vordergrund Rot</span><span class="sxs-lookup"><span data-stu-id="1a194-362">Foreground Red</span></span> | <span data-ttu-id="1a194-363">Wendet Rot (nicht intensiv/leuchtend) auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-363">Applies non-bold/bright red to foreground</span></span> |
| <span data-ttu-id="1a194-364">32</span><span class="sxs-lookup"><span data-stu-id="1a194-364">32</span></span> | <span data-ttu-id="1a194-365">Vordergrund Grün</span><span class="sxs-lookup"><span data-stu-id="1a194-365">Foreground Green</span></span> | <span data-ttu-id="1a194-366">Wendet Grün (nicht intensiv/leuchtend) auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-366">Applies non-bold/bright green to foreground</span></span> |
| <span data-ttu-id="1a194-367">33</span><span class="sxs-lookup"><span data-stu-id="1a194-367">33</span></span> | <span data-ttu-id="1a194-368">Vordergrund Gelb</span><span class="sxs-lookup"><span data-stu-id="1a194-368">Foreground Yellow</span></span> | <span data-ttu-id="1a194-369">Wendet Gelb (nicht intensiv/leuchtend) auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-369">Applies non-bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="1a194-370">34</span><span class="sxs-lookup"><span data-stu-id="1a194-370">34</span></span> | <span data-ttu-id="1a194-371">Vordergrund Blau</span><span class="sxs-lookup"><span data-stu-id="1a194-371">Foreground Blue</span></span> | <span data-ttu-id="1a194-372">Wendet Blau (nicht intensiv/leuchtend) auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-372">Applies non-bold/bright blue to foreground</span></span> |
| <span data-ttu-id="1a194-373">35</span><span class="sxs-lookup"><span data-stu-id="1a194-373">35</span></span> | <span data-ttu-id="1a194-374">Vordergrund Magenta</span><span class="sxs-lookup"><span data-stu-id="1a194-374">Foreground Magenta</span></span> | <span data-ttu-id="1a194-375">Wendet Magenta (nicht intensiv/leuchtend) auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-375">Applies non-bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="1a194-376">36</span><span class="sxs-lookup"><span data-stu-id="1a194-376">36</span></span> | <span data-ttu-id="1a194-377">Vordergrund Cyan</span><span class="sxs-lookup"><span data-stu-id="1a194-377">Foreground Cyan</span></span> | <span data-ttu-id="1a194-378">Wendet Cyan (nicht intensiv/leuchtend) auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-378">Applies non-bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="1a194-379">37</span><span class="sxs-lookup"><span data-stu-id="1a194-379">37</span></span> | <span data-ttu-id="1a194-380">Vordergrund Weiß</span><span class="sxs-lookup"><span data-stu-id="1a194-380">Foreground White</span></span> | <span data-ttu-id="1a194-381">Wendet Weiß (nicht intensiv/leuchtend) auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-381">Applies non-bold/bright white to foreground</span></span> |
| <span data-ttu-id="1a194-382">38</span><span class="sxs-lookup"><span data-stu-id="1a194-382">38</span></span> | <span data-ttu-id="1a194-383">Vordergrund Erweitert</span><span class="sxs-lookup"><span data-stu-id="1a194-383">Foreground Extended</span></span> | <span data-ttu-id="1a194-384">Wendet den erweiterten Farbwert auf den Vordergrund an (weitere Informationen finden Sie unten).</span><span class="sxs-lookup"><span data-stu-id="1a194-384">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="1a194-385">39</span><span class="sxs-lookup"><span data-stu-id="1a194-385">39</span></span> | <span data-ttu-id="1a194-386">Vordergrund Standard</span><span class="sxs-lookup"><span data-stu-id="1a194-386">Foreground Default</span></span> | <span data-ttu-id="1a194-387">Wendet nur den Vordergrund-Teil der Standardwerte an (siehe 0).</span><span class="sxs-lookup"><span data-stu-id="1a194-387">Applies only the foreground portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="1a194-388">40</span><span class="sxs-lookup"><span data-stu-id="1a194-388">40</span></span> | <span data-ttu-id="1a194-389">Hintergrund Schwarz</span><span class="sxs-lookup"><span data-stu-id="1a194-389">Background Black</span></span> | <span data-ttu-id="1a194-390">Wendet Schwarz (nicht intensiv/leuchtend) auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-390">Applies non-bold/bright black to background</span></span> |
| <span data-ttu-id="1a194-391">41</span><span class="sxs-lookup"><span data-stu-id="1a194-391">41</span></span> | <span data-ttu-id="1a194-392">Hintergrund Rot</span><span class="sxs-lookup"><span data-stu-id="1a194-392">Background Red</span></span> | <span data-ttu-id="1a194-393">Wendet Rot (nicht intensiv/leuchtend) auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-393">Applies non-bold/bright red to background</span></span> |
| <span data-ttu-id="1a194-394">42</span><span class="sxs-lookup"><span data-stu-id="1a194-394">42</span></span> | <span data-ttu-id="1a194-395">Hintergrund Grün</span><span class="sxs-lookup"><span data-stu-id="1a194-395">Background Green</span></span> | <span data-ttu-id="1a194-396">Wendet Grün (nicht intensiv/leuchtend) auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-396">Applies non-bold/bright green to background</span></span> |
| <span data-ttu-id="1a194-397">43</span><span class="sxs-lookup"><span data-stu-id="1a194-397">43</span></span> | <span data-ttu-id="1a194-398">Hintergrund Gelb</span><span class="sxs-lookup"><span data-stu-id="1a194-398">Background Yellow</span></span> | <span data-ttu-id="1a194-399">Wendet Gelb (nicht intensiv/leuchtend) auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-399">Applies non-bold/bright yellow to background</span></span> |
| <span data-ttu-id="1a194-400">44</span><span class="sxs-lookup"><span data-stu-id="1a194-400">44</span></span> | <span data-ttu-id="1a194-401">Hintergrund Blau</span><span class="sxs-lookup"><span data-stu-id="1a194-401">Background Blue</span></span> | <span data-ttu-id="1a194-402">Wendet (nicht intensiv/leuchtend) auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-402">Applies non-bold/bright blue to background</span></span> |
| <span data-ttu-id="1a194-403">45</span><span class="sxs-lookup"><span data-stu-id="1a194-403">45</span></span> | <span data-ttu-id="1a194-404">Hintergrund Magenta</span><span class="sxs-lookup"><span data-stu-id="1a194-404">Background Magenta</span></span> | <span data-ttu-id="1a194-405">Wendet Magenta (nicht intensiv/leuchtend) auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-405">Applies non-bold/bright magenta to background</span></span> |
| <span data-ttu-id="1a194-406">46</span><span class="sxs-lookup"><span data-stu-id="1a194-406">46</span></span> | <span data-ttu-id="1a194-407">Hintergrund Cyan</span><span class="sxs-lookup"><span data-stu-id="1a194-407">Background Cyan</span></span> | <span data-ttu-id="1a194-408">Wendet Cyan (nicht intensiv/leuchtend) auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-408">Applies non-bold/bright cyan to background</span></span> |
| <span data-ttu-id="1a194-409">47</span><span class="sxs-lookup"><span data-stu-id="1a194-409">47</span></span> | <span data-ttu-id="1a194-410">Hintergrund Weiß</span><span class="sxs-lookup"><span data-stu-id="1a194-410">Background White</span></span> | <span data-ttu-id="1a194-411">Wendet Weiß (nicht intensiv/leuchtend) auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-411">Applies non-bold/bright white to background</span></span> |
| <span data-ttu-id="1a194-412">48</span><span class="sxs-lookup"><span data-stu-id="1a194-412">48</span></span> | <span data-ttu-id="1a194-413">Hintergrund Erweitert</span><span class="sxs-lookup"><span data-stu-id="1a194-413">Background Extended</span></span> | <span data-ttu-id="1a194-414">Wendet den erweiterten Farbwert auf den Hintergrund an (weitere Informationen finden Sie unten).</span><span class="sxs-lookup"><span data-stu-id="1a194-414">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="1a194-415">49</span><span class="sxs-lookup"><span data-stu-id="1a194-415">49</span></span> | <span data-ttu-id="1a194-416">Hintergrund Standard</span><span class="sxs-lookup"><span data-stu-id="1a194-416">Background Default</span></span> | <span data-ttu-id="1a194-417">Wendet nur den Hintergrund-Teil der Standardwerte an (siehe 0).</span><span class="sxs-lookup"><span data-stu-id="1a194-417">Applies only the background portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="1a194-418">90</span><span class="sxs-lookup"><span data-stu-id="1a194-418">90</span></span> | <span data-ttu-id="1a194-419">Vordergrund leuchtend Schwarz</span><span class="sxs-lookup"><span data-stu-id="1a194-419">Bright Foreground Black</span></span> | <span data-ttu-id="1a194-420">Wendet ein intensives/leuchtendes Schwarz auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-420">Applies bold/bright black to foreground</span></span> |
| <span data-ttu-id="1a194-421">91</span><span class="sxs-lookup"><span data-stu-id="1a194-421">91</span></span> | <span data-ttu-id="1a194-422">Vordergrund leuchtend Rot</span><span class="sxs-lookup"><span data-stu-id="1a194-422">Bright Foreground Red</span></span> | <span data-ttu-id="1a194-423">Wendet ein intensives/leuchtendes Rot auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-423">Applies bold/bright red to foreground</span></span> |
| <span data-ttu-id="1a194-424">92</span><span class="sxs-lookup"><span data-stu-id="1a194-424">92</span></span> | <span data-ttu-id="1a194-425">Vordergrund leuchtend Grün</span><span class="sxs-lookup"><span data-stu-id="1a194-425">Bright Foreground Green</span></span> | <span data-ttu-id="1a194-426">Wendet ein intensives/leuchtendes Grün auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-426">Applies bold/bright green to foreground</span></span> |
| <span data-ttu-id="1a194-427">93</span><span class="sxs-lookup"><span data-stu-id="1a194-427">93</span></span> | <span data-ttu-id="1a194-428">Vordergrund leuchtend Gelb</span><span class="sxs-lookup"><span data-stu-id="1a194-428">Bright Foreground Yellow</span></span> | <span data-ttu-id="1a194-429">Wendet ein intensives/leuchtendes Gelb auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-429">Applies bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="1a194-430">94</span><span class="sxs-lookup"><span data-stu-id="1a194-430">94</span></span> | <span data-ttu-id="1a194-431">Vordergrund leuchtend Blau</span><span class="sxs-lookup"><span data-stu-id="1a194-431">Bright Foreground Blue</span></span> | <span data-ttu-id="1a194-432">Wendet ein intensives/leuchtendes Blau auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-432">Applies bold/bright blue to foreground</span></span> |
| <span data-ttu-id="1a194-433">95</span><span class="sxs-lookup"><span data-stu-id="1a194-433">95</span></span> | <span data-ttu-id="1a194-434">Vordergrund leuchtend Magenta</span><span class="sxs-lookup"><span data-stu-id="1a194-434">Bright Foreground Magenta</span></span> | <span data-ttu-id="1a194-435">Wendet ein intensives/leuchtendes Magenta auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-435">Applies bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="1a194-436">96</span><span class="sxs-lookup"><span data-stu-id="1a194-436">96</span></span> | <span data-ttu-id="1a194-437">Vordergrund leuchtend Cyan</span><span class="sxs-lookup"><span data-stu-id="1a194-437">Bright Foreground Cyan</span></span> | <span data-ttu-id="1a194-438">Wendet ein intensives/leuchtendes Cyan auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-438">Applies bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="1a194-439">97</span><span class="sxs-lookup"><span data-stu-id="1a194-439">97</span></span> | <span data-ttu-id="1a194-440">Vordergrund leuchtend Weiß</span><span class="sxs-lookup"><span data-stu-id="1a194-440">Bright Foreground White</span></span> | <span data-ttu-id="1a194-441">Wendet ein intensives/leuchtendes Weiß auf den Vordergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-441">Applies bold/bright white to foreground</span></span> |
| <span data-ttu-id="1a194-442">100</span><span class="sxs-lookup"><span data-stu-id="1a194-442">100</span></span> | <span data-ttu-id="1a194-443">Hintergrund leuchtend Schwarz</span><span class="sxs-lookup"><span data-stu-id="1a194-443">Bright Background Black</span></span> | <span data-ttu-id="1a194-444">Wendet ein intensives/leuchtendes Schwarz auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-444">Applies bold/bright black to background</span></span> |
| <span data-ttu-id="1a194-445">101</span><span class="sxs-lookup"><span data-stu-id="1a194-445">101</span></span> | <span data-ttu-id="1a194-446">Hintergrund leuchtend Rot</span><span class="sxs-lookup"><span data-stu-id="1a194-446">Bright Background Red</span></span> | <span data-ttu-id="1a194-447">Wendet ein intensives/leuchtendes Rot auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-447">Applies bold/bright red to background</span></span> |
| <span data-ttu-id="1a194-448">102</span><span class="sxs-lookup"><span data-stu-id="1a194-448">102</span></span> | <span data-ttu-id="1a194-449">Hintergrund leuchtend Grün</span><span class="sxs-lookup"><span data-stu-id="1a194-449">Bright Background Green</span></span> | <span data-ttu-id="1a194-450">Wendet ein intensives/leuchtendes Grün auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-450">Applies bold/bright green to background</span></span> |
| <span data-ttu-id="1a194-451">103</span><span class="sxs-lookup"><span data-stu-id="1a194-451">103</span></span> | <span data-ttu-id="1a194-452">Hintergrund leuchtend Gelb</span><span class="sxs-lookup"><span data-stu-id="1a194-452">Bright Background Yellow</span></span> | <span data-ttu-id="1a194-453">Wendet ein intensives/leuchtendes Gelb auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-453">Applies bold/bright yellow to background</span></span> |
| <span data-ttu-id="1a194-454">104</span><span class="sxs-lookup"><span data-stu-id="1a194-454">104</span></span> | <span data-ttu-id="1a194-455">Hintergrund leuchtend Blau</span><span class="sxs-lookup"><span data-stu-id="1a194-455">Bright Background Blue</span></span> | <span data-ttu-id="1a194-456">Wendet ein intensives/leuchtendes Blau auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-456">Applies bold/bright blue to background</span></span> |
| <span data-ttu-id="1a194-457">105</span><span class="sxs-lookup"><span data-stu-id="1a194-457">105</span></span> | <span data-ttu-id="1a194-458">Hintergrund leuchtend Magenta</span><span class="sxs-lookup"><span data-stu-id="1a194-458">Bright Background Magenta</span></span> | <span data-ttu-id="1a194-459">Wendet ein intensives/leuchtendes Magenta auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-459">Applies bold/bright magenta to background</span></span> |
| <span data-ttu-id="1a194-460">106</span><span class="sxs-lookup"><span data-stu-id="1a194-460">106</span></span> | <span data-ttu-id="1a194-461">Hintergrund leuchtend Cyan</span><span class="sxs-lookup"><span data-stu-id="1a194-461">Bright Background Cyan</span></span> | <span data-ttu-id="1a194-462">Wendet ein intensives/leuchtendes Cyan auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-462">Applies bold/bright cyan to background</span></span> |
| <span data-ttu-id="1a194-463">107</span><span class="sxs-lookup"><span data-stu-id="1a194-463">107</span></span> | <span data-ttu-id="1a194-464">Hintergrund leuchtend Weiß</span><span class="sxs-lookup"><span data-stu-id="1a194-464">Bright Background White</span></span> | <span data-ttu-id="1a194-465">Wendet ein intensives/leuchtendes Weiß auf den Hintergrund an.</span><span class="sxs-lookup"><span data-stu-id="1a194-465">Applies bold/bright white to background</span></span> |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="1a194-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Erweiterte Farben</span><span class="sxs-lookup"><span data-stu-id="1a194-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="1a194-467">Einige virtuelle Terminalemulatoren unterstützen eine Farbpalette mit mehr als den von der Windows-Konsole bereitgestellten 16 Farben.</span><span class="sxs-lookup"><span data-stu-id="1a194-467">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="1a194-468">Für diese erweiterten Farben wählt die Windows-Konsole die nächstmögliche passende Farbe aus der vorhandenen 16er-Farbtabelle zur Anzeige aus.</span><span class="sxs-lookup"><span data-stu-id="1a194-468">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="1a194-469">Im Gegensatz zu den oben genannten typischen SGR-Werten verwenden die erweiterten Werte zusätzliche Parameter nach dem Anfangsindikator gemäß der nachstehenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="1a194-469">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="1a194-470">SGR-Untersequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-470">SGR Subsequence</span></span> | <span data-ttu-id="1a194-471">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-471">Description</span></span> |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a194-472">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="1a194-472">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="1a194-473">Legt die Vordergrundfarbe auf den in den Parametern &lt;r&gt;, &lt;g&gt;, &lt;b&gt; angegebenen RGB-Wert fest\*</span><span class="sxs-lookup"><span data-stu-id="1a194-473">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="1a194-474">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="1a194-474">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="1a194-475">Legt die Hintergrundfarbe auf den in den Parametern &lt;r&gt;, &lt;g&gt;, &lt;b&gt; angegebenen RGB-Wert fest\*</span><span class="sxs-lookup"><span data-stu-id="1a194-475">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="1a194-476">38 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="1a194-476">38 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="1a194-477">Legt die Vordergrundfarbe auf den &lt;s&gt;-Index in der 88er- oder 256er-Farbtabelle fest\*</span><span class="sxs-lookup"><span data-stu-id="1a194-477">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |
| <span data-ttu-id="1a194-478">48 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="1a194-478">48 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="1a194-479">Legt die Hintergrundfarbe auf den &lt;s&gt;-Index in der 88er- oder 256er-Farbtabelle fest\*</span><span class="sxs-lookup"><span data-stu-id="1a194-479">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |



<span data-ttu-id="1a194-480">\* Die 88er- und 256er-Farbpaletten, die intern zum Vergleich verwaltet werden, basieren auf dem xterm-Terminalemulator.</span><span class="sxs-lookup"><span data-stu-id="1a194-480">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="1a194-481">Die Vergleichs-/Rundungstabellen können zurzeit nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="1a194-481">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="1a194-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Bildschirmfarben</span><span class="sxs-lookup"><span data-stu-id="1a194-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="1a194-483">Der folgende Befehl ermöglicht es der Anwendung, die Werte der Bildschirmfarbpalette auf einen beliebigen RGB-Wert festzulegen.</span><span class="sxs-lookup"><span data-stu-id="1a194-483">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="1a194-484">Die RGB-Werte sollten hexadezimal Werte zwischen `0` und `ff` sein und durch den Schrägstrich getrennt werden (z. B. `rgb:1/24/86`).</span><span class="sxs-lookup"><span data-stu-id="1a194-484">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="1a194-485">Beachten Sie, dass es sich bei dieser Sequenz um eine „Betriebssystembefehls“-Sequenz (OSC), und nicht, wie bei vielen der anderen aufgelisteten Sequenzen, um eine CSI-Sequenz handelt, und dass sie als solche mit „\\x1b\]“ und nicht mit „\\x1b\[“ beginnt.</span><span class="sxs-lookup"><span data-stu-id="1a194-485">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="1a194-486">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-486">Sequence</span></span> | <span data-ttu-id="1a194-487">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-487">Description</span></span> | <span data-ttu-id="1a194-488">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-488">Behavior</span></span> |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a194-489">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span><span class="sxs-lookup"><span data-stu-id="1a194-489">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="1a194-490">Bildschirmfarben ändern</span><span class="sxs-lookup"><span data-stu-id="1a194-490">Modify Screen Colors</span></span> | <span data-ttu-id="1a194-491">Legt den Bildschirmfarbpaletten-Index &lt;i&gt; auf die in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; angegebenen RGB-Werte fest.</span><span class="sxs-lookup"><span data-stu-id="1a194-491">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="1a194-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modusänderungen</span><span class="sxs-lookup"><span data-stu-id="1a194-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="1a194-493">Hierbei handelt es sich um Sequenzen, die die Eingabemodi steuern.</span><span class="sxs-lookup"><span data-stu-id="1a194-493">These are sequences that control the input modes.</span></span> <span data-ttu-id="1a194-494">Es gibt zwei unterschiedliche Sätze von Eingabemodi: den Pfeiltasten- und den Zehnertastaturtasten-Modus.</span><span class="sxs-lookup"><span data-stu-id="1a194-494">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="1a194-495">Der Pfeiltastenmodus steuert die Sequenzen, die von den Pfeiltasten und den Tasten POS1 und ENDE ausgegeben werden, während der Zehnertastaturtasten-Modus in erster Linie die von den Tasten auf der numerischen Tastatur ausgegebene Sequenzen sowie die Funktionstasten steuert.</span><span class="sxs-lookup"><span data-stu-id="1a194-495">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="1a194-496">Jeder dieser Modi ist eine einfache boolesche Einstellung – der Pfeiltastenmodus ist entweder auf „Normal“ (Standard) oder „Anwendung“ und der Zehnertastaturtasten-Modus entweder auf „Numerisch“ (Standard) oder „Anwendung“ festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-496">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="1a194-497">Weitere Informationen zu den in diesen Modi ausgegebenen Sequenzen finden Sie in den Abschnitten „Pfeiltasten“ und „Numerische Tastatur und Funktionstasten“.</span><span class="sxs-lookup"><span data-stu-id="1a194-497">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="1a194-498">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-498">Sequence</span></span> | <span data-ttu-id="1a194-499">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-499">Code</span></span> | <span data-ttu-id="1a194-500">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-500">Description</span></span> | <span data-ttu-id="1a194-501">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-501">Behavior</span></span> |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="1a194-502">ESC =</span><span class="sxs-lookup"><span data-stu-id="1a194-502">ESC =</span></span> | <span data-ttu-id="1a194-503">DECKPAM</span><span class="sxs-lookup"><span data-stu-id="1a194-503">DECKPAM</span></span> | <span data-ttu-id="1a194-504">Aktiviert den Modus „Anwendung“ für die Zehnertastatur.</span><span class="sxs-lookup"><span data-stu-id="1a194-504">Enable Keypad Application Mode</span></span> | <span data-ttu-id="1a194-505">Über Zehnertastaturtasten werden Sequenzen im Modus „Anwendung“ ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="1a194-505">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="1a194-506">ESC &gt;</span><span class="sxs-lookup"><span data-stu-id="1a194-506">ESC &gt;</span></span> | <span data-ttu-id="1a194-507">DECKPNM</span><span class="sxs-lookup"><span data-stu-id="1a194-507">DECKPNM</span></span> | <span data-ttu-id="1a194-508">Aktiviert den Modus „Numerisch“ für die Zehnertastatur.</span><span class="sxs-lookup"><span data-stu-id="1a194-508">Enable Keypad Numeric Mode</span></span> | <span data-ttu-id="1a194-509">Über Zehnertastaturtasten werden Sequenzen im Modus „Numerisch“ ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="1a194-509">Keypad keys will emit their Numeric Mode sequences.</span></span> |
| <span data-ttu-id="1a194-510">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="1a194-510">ESC \[ ?</span></span> <span data-ttu-id="1a194-511">1 Stunde</span><span class="sxs-lookup"><span data-stu-id="1a194-511">1 h</span></span> | <span data-ttu-id="1a194-512">DECCKM</span><span class="sxs-lookup"><span data-stu-id="1a194-512">DECCKM</span></span> | <span data-ttu-id="1a194-513">Aktiviert den Modus „Anwendung“ für die Pfeiltasten.</span><span class="sxs-lookup"><span data-stu-id="1a194-513">Enable Cursor Keys Application Mode</span></span> | <span data-ttu-id="1a194-514">Über Zehnertastaturtasten werden Sequenzen im Modus „Anwendung“ ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="1a194-514">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="1a194-515">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="1a194-515">ESC \[ ?</span></span> <span data-ttu-id="1a194-516">1 l</span><span class="sxs-lookup"><span data-stu-id="1a194-516">1 l</span></span> | <span data-ttu-id="1a194-517">DECCKM</span><span class="sxs-lookup"><span data-stu-id="1a194-517">DECCKM</span></span> | <span data-ttu-id="1a194-518">Deaktiviert den Modus „Anwendung“ für Pfeiltasten (Modus „Normal“ verwenden).</span><span class="sxs-lookup"><span data-stu-id="1a194-518">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="1a194-519">Über Zehnertastaturtasten werden Sequenzen im Modus „Numerisch“ ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="1a194-519">Keypad keys will emit their Numeric Mode sequences.</span></span> |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="1a194-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Abfragestatus</span><span class="sxs-lookup"><span data-stu-id="1a194-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="1a194-521">Alle Befehle in diesem Abschnitt entsprechen im Allgemeinen dem Aufruf der Get\*-Konsolen-APIs zum Abrufen von Statusinformationen über den aktuellen Zustand des Konsolenpuffers.</span><span class="sxs-lookup"><span data-stu-id="1a194-521">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

> [!NOTE]
><span data-ttu-id="1a194-522">Diese Abfragen geben ihre Antworten unmittelbar nach ihrer Erkennung im Ausgabestream in den Konsoleneingabestream ab, während „ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING“ festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1a194-522">These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="1a194-523">Das Flag „ENABLE\_VIRTUAL\_TERMINAL\_INPUT“ gilt nicht für Abfragebefehle, da davon ausgegangen wird, dass die Anwendung, die eine Abfrage erstellt, immer die Antwort erhalten soll.</span><span class="sxs-lookup"><span data-stu-id="1a194-523">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="1a194-524">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-524">Sequence</span></span> | <span data-ttu-id="1a194-525">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-525">Code</span></span> | <span data-ttu-id="1a194-526">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-526">Description</span></span> | <span data-ttu-id="1a194-527">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-527">Behavior</span></span> |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a194-528">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="1a194-528">ESC \[ 6 n</span></span> | <span data-ttu-id="1a194-529">DECXCPR</span><span class="sxs-lookup"><span data-stu-id="1a194-529">DECXCPR</span></span> | <span data-ttu-id="1a194-530">Cursorposition melden</span><span class="sxs-lookup"><span data-stu-id="1a194-530">Report Cursor Position</span></span> | <span data-ttu-id="1a194-531">Gibt die Cursorposition wie folgt aus: ESC \[ &lt;r&gt; ; &lt;c&gt; R, wobei &lt;r&gt; = Cursorzeile und &lt;c&gt; = Cursorspalte</span><span class="sxs-lookup"><span data-stu-id="1a194-531">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="1a194-532">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="1a194-532">ESC \[ 0 c</span></span> | <span data-ttu-id="1a194-533">DA</span><span class="sxs-lookup"><span data-stu-id="1a194-533">DA</span></span> | <span data-ttu-id="1a194-534">Geräteattribute</span><span class="sxs-lookup"><span data-stu-id="1a194-534">Device Attributes</span></span> | <span data-ttu-id="1a194-535">Meldet die Terminalidentität.</span><span class="sxs-lookup"><span data-stu-id="1a194-535">Report the terminal identity.</span></span> <span data-ttu-id="1a194-536">Gibt „\\x1b\[?1;0c“ aus, was „VT101 ohne Optionen“ bedeutet.</span><span class="sxs-lookup"><span data-stu-id="1a194-536">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span> |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="1a194-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabstopps</span><span class="sxs-lookup"><span data-stu-id="1a194-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="1a194-538">Während die Windows-Konsole traditionell erwartet, dass Tabstopps immer acht Zeichen breit sind, können \*nix-Anwendungen, die bestimmte Sequenzen verwenden, die Position der Tabstopps innerhalb der Konsolenfenster ändern, um die Cursorbewegung durch die Anwendung zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="1a194-538">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="1a194-539">Die folgenden Sequenzen ermöglichen es einer Anwendung, die Positionen der Tabstopps innerhalb des Konsolenfensters festzulegen, sie zu entfernen und zwischen ihnen zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="1a194-539">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="1a194-540">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-540">Sequence</span></span> | <span data-ttu-id="1a194-541">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-541">Code</span></span> | <span data-ttu-id="1a194-542">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-542">Description</span></span> | <span data-ttu-id="1a194-543">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-543">Behavior</span></span> |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a194-544">ESC H</span><span class="sxs-lookup"><span data-stu-id="1a194-544">ESC H</span></span> | <span data-ttu-id="1a194-545">HTS</span><span class="sxs-lookup"><span data-stu-id="1a194-545">HTS</span></span> | <span data-ttu-id="1a194-546">Horizontalen Tabstopp festlegen</span><span class="sxs-lookup"><span data-stu-id="1a194-546">Horizontal Tab Set</span></span> | <span data-ttu-id="1a194-547">Legt einen Tabstopp in der aktuellen Spalte fest, in der sich der Cursor befindet.</span><span class="sxs-lookup"><span data-stu-id="1a194-547">Sets a tab stop in the current column the cursor is in.</span></span> |
| <span data-ttu-id="1a194-548">ESC \[ &lt;n&gt; I</span><span class="sxs-lookup"><span data-stu-id="1a194-548">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="1a194-549">CHT</span><span class="sxs-lookup"><span data-stu-id="1a194-549">CHT</span></span> | <span data-ttu-id="1a194-550">Tabulator Cursor horizontal (vorwärts)</span><span class="sxs-lookup"><span data-stu-id="1a194-550">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="1a194-551">Bewegt den Cursor zur nächsten Spalte (in derselben Zeile) mit einem Tabstopp.</span><span class="sxs-lookup"><span data-stu-id="1a194-551">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="1a194-552">Wenn keine weiteren Tabstopps vorhanden sind, wird der Cursor in die letzte Spalte der Zeile bewegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-552">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="1a194-553">Befindet sich der Cursor in der letzten Spalte, wird er zur ersten Spalte der nächsten Zeile bewegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-553">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="1a194-554">ESC \[ &lt;n&gt; Z</span><span class="sxs-lookup"><span data-stu-id="1a194-554">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="1a194-555">CBT</span><span class="sxs-lookup"><span data-stu-id="1a194-555">CBT</span></span> | <span data-ttu-id="1a194-556">Tabulator Cursor rückwärts</span><span class="sxs-lookup"><span data-stu-id="1a194-556">Cursor Backwards Tab</span></span> | <span data-ttu-id="1a194-557">Bewegt den Cursor zur vorherigen Spalte (in derselben Zeile) mit einem Tabstopp.</span><span class="sxs-lookup"><span data-stu-id="1a194-557">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="1a194-558">Wenn keine weiteren Tabstopps vorhanden sind, wird der Cursor in die erste Spalte bewegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-558">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="1a194-559">Befindet sich der Cursor in der ersten Spalte, wird der Cursor nicht bewegt.</span><span class="sxs-lookup"><span data-stu-id="1a194-559">If the cursor is in the first column, doesn’t move the cursor.</span></span> |
| <span data-ttu-id="1a194-560">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="1a194-560">ESC \[ 0 g</span></span> | <span data-ttu-id="1a194-561">TBC</span><span class="sxs-lookup"><span data-stu-id="1a194-561">TBC</span></span> | <span data-ttu-id="1a194-562">Tabstopp löschen (aktuelle Spalte)</span><span class="sxs-lookup"><span data-stu-id="1a194-562">Tab Clear (current column)</span></span> | <span data-ttu-id="1a194-563">Löscht den Tabstopp in der aktuellen Spalte, sofern vorhanden.</span><span class="sxs-lookup"><span data-stu-id="1a194-563">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="1a194-564">Andernfalls geschieht nichts.</span><span class="sxs-lookup"><span data-stu-id="1a194-564">Otherwise does nothing.</span></span> |
| <span data-ttu-id="1a194-565">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="1a194-565">ESC \[ 3 g</span></span> | <span data-ttu-id="1a194-566">TBC</span><span class="sxs-lookup"><span data-stu-id="1a194-566">TBC</span></span> | <span data-ttu-id="1a194-567">Tabstopp löschen (alle Spalten)</span><span class="sxs-lookup"><span data-stu-id="1a194-567">Tab Clear (all columns)</span></span> | <span data-ttu-id="1a194-568">Löscht alle momentan festgelegten Tabstopps.</span><span class="sxs-lookup"><span data-stu-id="1a194-568">Clears all currently set tab stops.</span></span> |



- <span data-ttu-id="1a194-569">Sowohl für CHT als auch für CBT ist &lt;n&gt; ein optionaler Parameter (Standardwert = 1), der angibt, wie oft der Cursor in der angegebenen Richtung vorwärts bewegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="1a194-569">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="1a194-570">Wenn keine Tabstopps über HTS festgelegt sind, werden die erste und die letzte Spalte des Fensters von CHT und CBT als die einzigen beiden Tabstopps behandelt.</span><span class="sxs-lookup"><span data-stu-id="1a194-570">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="1a194-571">Wird ein Tabstopp mit HTS gesetzt, bewirkt dies zudem, dass die Konsole bei der Ausgabe eines TAB-Zeichens (0x09, '\\t') auf die gleiche Weise wie bei CHT zum nächsten Tabulatorstopp navigiert.</span><span class="sxs-lookup"><span data-stu-id="1a194-571">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="1a194-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Zeichensatz festlegen</span><span class="sxs-lookup"><span data-stu-id="1a194-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="1a194-573">Mit den folgenden Sequenzen können Programme die Zuordnung des aktiven Zeichensatzes ändern.</span><span class="sxs-lookup"><span data-stu-id="1a194-573">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="1a194-574">Dadurch kann ein Programm 7-Bit-ASCII-Zeichen ausgeben, diese auf dem Terminalbildschirm selbst aber als andere Glyphen anzeigen lassen.</span><span class="sxs-lookup"><span data-stu-id="1a194-574">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="1a194-575">Gegenwärtig sind die einzigen zwei unterstützten Zeichensätze ASCII (Standard) und der DEC Special Graphics-Zeichensatz.</span><span class="sxs-lookup"><span data-stu-id="1a194-575">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="1a194-576">Unter <http://vt100.net/docs/vt220-rm/table2-4.html> finden Sie eine Auflistung aller Zeichen, die durch den DEC Special Graphics-Zeichensatz dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="1a194-576">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="1a194-577">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-577">Sequence</span></span> | <span data-ttu-id="1a194-578">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-578">Description</span></span> | <span data-ttu-id="1a194-579">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-579">Behavior</span></span> |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="1a194-580">ESC ( 0</span><span class="sxs-lookup"><span data-stu-id="1a194-580">ESC ( 0</span></span> | <span data-ttu-id="1a194-581">Zeichensatz festlegen – DEC Line Drawing</span><span class="sxs-lookup"><span data-stu-id="1a194-581">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="1a194-582">Aktiviert den Modus „DEC Line Drawing“.</span><span class="sxs-lookup"><span data-stu-id="1a194-582">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="1a194-583">ESC ( B</span><span class="sxs-lookup"><span data-stu-id="1a194-583">ESC ( B</span></span> | <span data-ttu-id="1a194-584">Zeichensatz festlegen – US ASCII</span><span class="sxs-lookup"><span data-stu-id="1a194-584">Designate Character Set – US ASCII</span></span> | <span data-ttu-id="1a194-585">Aktiviert den ASCII-Modus (Standard).</span><span class="sxs-lookup"><span data-stu-id="1a194-585">Enables ASCII Mode (Default)</span></span> |



<span data-ttu-id="1a194-586">Der Modus „DEC Line Drawing“ wird insbesondere zum Zeichnen von Rahmen in Konsolenanwendungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="1a194-586">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="1a194-587">In der folgenden Tabelle ist dargestellt, welche ASCII-Zeichen welchen Linienzeichnungszeichen zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="1a194-587">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="1a194-588">Hex</span><span class="sxs-lookup"><span data-stu-id="1a194-588">Hex</span></span> | <span data-ttu-id="1a194-589">ASCII</span><span class="sxs-lookup"><span data-stu-id="1a194-589">ASCII</span></span> | <span data-ttu-id="1a194-590">DEC Line Drawing</span><span class="sxs-lookup"><span data-stu-id="1a194-590">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="1a194-591">0x6a</span><span class="sxs-lookup"><span data-stu-id="1a194-591">0x6a</span></span> | <span data-ttu-id="1a194-592">j</span><span class="sxs-lookup"><span data-stu-id="1a194-592">j</span></span> | <span data-ttu-id="1a194-593">┘</span><span class="sxs-lookup"><span data-stu-id="1a194-593">┘</span></span> |
| <span data-ttu-id="1a194-594">0x6b</span><span class="sxs-lookup"><span data-stu-id="1a194-594">0x6b</span></span> | <span data-ttu-id="1a194-595">k</span><span class="sxs-lookup"><span data-stu-id="1a194-595">k</span></span> | <span data-ttu-id="1a194-596">┐</span><span class="sxs-lookup"><span data-stu-id="1a194-596">┐</span></span> |
| <span data-ttu-id="1a194-597">0x6c</span><span class="sxs-lookup"><span data-stu-id="1a194-597">0x6c</span></span> | <span data-ttu-id="1a194-598">l</span><span class="sxs-lookup"><span data-stu-id="1a194-598">l</span></span> | <span data-ttu-id="1a194-599">┌</span><span class="sxs-lookup"><span data-stu-id="1a194-599">┌</span></span> |
| <span data-ttu-id="1a194-600">0x6d</span><span class="sxs-lookup"><span data-stu-id="1a194-600">0x6d</span></span> | <span data-ttu-id="1a194-601">m</span><span class="sxs-lookup"><span data-stu-id="1a194-601">m</span></span> | <span data-ttu-id="1a194-602">└</span><span class="sxs-lookup"><span data-stu-id="1a194-602">└</span></span> |
| <span data-ttu-id="1a194-603">0x6e</span><span class="sxs-lookup"><span data-stu-id="1a194-603">0x6e</span></span> | <span data-ttu-id="1a194-604">n</span><span class="sxs-lookup"><span data-stu-id="1a194-604">n</span></span> | <span data-ttu-id="1a194-605">┼</span><span class="sxs-lookup"><span data-stu-id="1a194-605">┼</span></span> |
| <span data-ttu-id="1a194-606">0x71</span><span class="sxs-lookup"><span data-stu-id="1a194-606">0x71</span></span> | <span data-ttu-id="1a194-607">q</span><span class="sxs-lookup"><span data-stu-id="1a194-607">q</span></span> | <span data-ttu-id="1a194-608">─</span><span class="sxs-lookup"><span data-stu-id="1a194-608">─</span></span> |
| <span data-ttu-id="1a194-609">0x74</span><span class="sxs-lookup"><span data-stu-id="1a194-609">0x74</span></span> | <span data-ttu-id="1a194-610">t</span><span class="sxs-lookup"><span data-stu-id="1a194-610">t</span></span> | <span data-ttu-id="1a194-611">├</span><span class="sxs-lookup"><span data-stu-id="1a194-611">├</span></span> |
| <span data-ttu-id="1a194-612">0x75</span><span class="sxs-lookup"><span data-stu-id="1a194-612">0x75</span></span> | <span data-ttu-id="1a194-613">u</span><span class="sxs-lookup"><span data-stu-id="1a194-613">u</span></span> | <span data-ttu-id="1a194-614">┤</span><span class="sxs-lookup"><span data-stu-id="1a194-614">┤</span></span> |
| <span data-ttu-id="1a194-615">0x76</span><span class="sxs-lookup"><span data-stu-id="1a194-615">0x76</span></span> | <span data-ttu-id="1a194-616">v</span><span class="sxs-lookup"><span data-stu-id="1a194-616">v</span></span> | <span data-ttu-id="1a194-617">┴</span><span class="sxs-lookup"><span data-stu-id="1a194-617">┴</span></span> |
| <span data-ttu-id="1a194-618">0x77</span><span class="sxs-lookup"><span data-stu-id="1a194-618">0x77</span></span> | <span data-ttu-id="1a194-619">w</span><span class="sxs-lookup"><span data-stu-id="1a194-619">w</span></span> | <span data-ttu-id="1a194-620">┬</span><span class="sxs-lookup"><span data-stu-id="1a194-620">┬</span></span> |
| <span data-ttu-id="1a194-621">0x78</span><span class="sxs-lookup"><span data-stu-id="1a194-621">0x78</span></span> | <span data-ttu-id="1a194-622">w</span><span class="sxs-lookup"><span data-stu-id="1a194-622">x</span></span> | <span data-ttu-id="1a194-623">│</span><span class="sxs-lookup"><span data-stu-id="1a194-623">│</span></span> |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="1a194-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Bildlaufränder</span><span class="sxs-lookup"><span data-stu-id="1a194-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="1a194-625">Mit den folgenden Sequenzen können Programme den „Bildlaufbereich“ des Bildschirms konfigurieren, der von Bildlaufvorgängen betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="1a194-625">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="1a194-626">Hierbei handelt es sich um eine Teilmenge der Zeilen, die angepasst werden, wenn der Bildschirm ansonsten gescrollt würde, z. B. auf einem '\\n' oder RI.</span><span class="sxs-lookup"><span data-stu-id="1a194-626">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="1a194-627">Diese Ränder wirken sich auch auf die Zeilen aus, die durch „Zeile einfügen“ (IL) und „Zeile löschen“ (DL), „Nach oben scrollen“ (SU) und „Nach unten scrollen“ (SD) geändert werden.</span><span class="sxs-lookup"><span data-stu-id="1a194-627">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="1a194-628">Die Bildlaufränder können besonders nützlich sein, wenn ein Teil des Bildschirms nicht gescrollt werden soll, wenn der Rest des Bildschirms gefüllt wird, wie z. B. eine Titelleiste am oberen Rand oder eine Statusleiste am unteren Rand Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="1a194-628">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="1a194-629">Für DECSTBM gibt es zwei optionale Parameter, &lt;t&gt; und &lt;b&gt;, mit denen die Zeilen angegeben werden, die die oberen und unteren Zeilen des Bildlaufbereichs (einschließlich) darstellen.</span><span class="sxs-lookup"><span data-stu-id="1a194-629">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="1a194-630">Wenn die Parameter weggelassen werden, ist &lt;t&gt; standardmäßig auf 1 und &lt;b&gt; auf die aktuelle Viewporthöhe voreingestellt.</span><span class="sxs-lookup"><span data-stu-id="1a194-630">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="1a194-631">Bildlaufränder gelten pro Puffer, daher ist zu beachten, dass der alternative Puffer und der Hauptpuffer getrennte Einstellungen für die Bildlaufränder aufweisen (damit eine Vollbildanwendung im alternativen Puffer die Ränder des Hauptpuffers nicht beeinträchtigen kann).</span><span class="sxs-lookup"><span data-stu-id="1a194-631">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="1a194-632">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-632">Sequence</span></span> | <span data-ttu-id="1a194-633">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-633">Code</span></span> | <span data-ttu-id="1a194-634">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-634">Description</span></span> | <span data-ttu-id="1a194-635">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-635">Behavior</span></span> |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="1a194-636">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span><span class="sxs-lookup"><span data-stu-id="1a194-636">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="1a194-637">DECSTBM</span><span class="sxs-lookup"><span data-stu-id="1a194-637">DECSTBM</span></span> | <span data-ttu-id="1a194-638">Bildlaufbereich festlegen</span><span class="sxs-lookup"><span data-stu-id="1a194-638">Set Scrolling Region</span></span> | <span data-ttu-id="1a194-639">Legt die VT-Bildlaufränder des Viewports fest.</span><span class="sxs-lookup"><span data-stu-id="1a194-639">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="1a194-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Fenstertitel</span><span class="sxs-lookup"><span data-stu-id="1a194-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="1a194-641">Mit den folgenden Befehlen kann die Anwendung den Titel des Konsolenfensters auf den angegebenen Parameter &lt;string&gt; festlegen.</span><span class="sxs-lookup"><span data-stu-id="1a194-641">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="1a194-642">Die Zeichenfolge muss weniger als 255 Zeichen umfassen, um akzeptiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="1a194-642">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="1a194-643">Dies entspricht dem Aufrufen von „SetConsoleTitle“ mit der angegebenen Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="1a194-643">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="1a194-644">Beachten Sie, dass es sich bei diesen Sequenzen um „Betriebssystembefehls“-Sequenzen (OSC), und nicht, wie bei vielen der anderen aufgelisteten Sequenzen, um CSI-Sequenzen handelt, und dass sie als solche mit „\\x1b\]“ und nicht mit „\\x1b\[“ beginnen.</span><span class="sxs-lookup"><span data-stu-id="1a194-644">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="1a194-645">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-645">Sequence</span></span> | <span data-ttu-id="1a194-646">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-646">Description</span></span> | <span data-ttu-id="1a194-647">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-647">Behavior</span></span> |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="1a194-648">ESC \] 0 ; &lt;Zeichenfolge&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="1a194-648">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="1a194-649">Symbol und Fenstertitel festlegen</span><span class="sxs-lookup"><span data-stu-id="1a194-649">Set Icon and Window Title</span></span> | <span data-ttu-id="1a194-650">Legt den Titel des Konsolenfensters auf &lt;Zeichenfolge&gt; fest.</span><span class="sxs-lookup"><span data-stu-id="1a194-650">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="1a194-651">ESC \] 2 ; &lt;Zeichenfolge&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="1a194-651">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="1a194-652">Window_Title</span><span class="sxs-lookup"><span data-stu-id="1a194-652">Set Window Title</span></span> | <span data-ttu-id="1a194-653">Legt den Titel des Konsolenfensters auf &lt;Zeichenfolge&gt; fest.</span><span class="sxs-lookup"><span data-stu-id="1a194-653">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="1a194-654">Das abschließende Zeichen hier ist das Glocken-Zeichen, „\\x07“.</span><span class="sxs-lookup"><span data-stu-id="1a194-654">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="1a194-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternativer Bildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="1a194-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="1a194-656">\*Anwendungen vom Nix-Typ verwenden oft einen alternativen Bildschirmpuffer, um den gesamten Inhalt des Puffers ändern zu können, ohne die Anwendung, von der sie gestartet wurden, zu beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="1a194-656">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="1a194-657">Der alternative Puffer beschreibt genau die Abmessungen des Fensters ohne Scrollbackbereich.</span><span class="sxs-lookup"><span data-stu-id="1a194-657">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="1a194-658">Beispiel für dieses Verhalten: Angenommen, „vim“ wird von „bash“ gestartet.</span><span class="sxs-lookup"><span data-stu-id="1a194-658">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="1a194-659">„Vim“ verwendet den gesamten Bildschirm, um die Datei zu bearbeiten, kehrt dann zu „bash“ zurück und lässt dabei den Originalpuffer unverändert.</span><span class="sxs-lookup"><span data-stu-id="1a194-659">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="1a194-660">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-660">Sequence</span></span> | <span data-ttu-id="1a194-661">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-661">Description</span></span> | <span data-ttu-id="1a194-662">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-662">Behavior</span></span> |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="1a194-663">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="1a194-663">ESC \[ ?</span></span> <span data-ttu-id="1a194-664">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="1a194-664">1 0 4 9 h</span></span> | <span data-ttu-id="1a194-665">Alternativen Bildschirmpuffer verwenden</span><span class="sxs-lookup"><span data-stu-id="1a194-665">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="1a194-666">Wechselt zu einem neuen alternativen Bildschirmpuffer.</span><span class="sxs-lookup"><span data-stu-id="1a194-666">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="1a194-667">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="1a194-667">ESC \[ ?</span></span> <span data-ttu-id="1a194-668">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="1a194-668">1 0 4 9 l</span></span> | <span data-ttu-id="1a194-669">Hauptbildschirmpuffer verwenden</span><span class="sxs-lookup"><span data-stu-id="1a194-669">Use Main Screen Buffer</span></span> | <span data-ttu-id="1a194-670">Wechselt zum Hauptpuffer.</span><span class="sxs-lookup"><span data-stu-id="1a194-670">Switches to the main buffer.</span></span> |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="1a194-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Fensterbreite</span><span class="sxs-lookup"><span data-stu-id="1a194-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="1a194-672">Mit den folgenden Sequenzen kann die Breite des Konsolenfensters gesteuert werden.</span><span class="sxs-lookup"><span data-stu-id="1a194-672">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="1a194-673">Sie entsprechen in etwa dem Aufruf der Konsolen-API „SetConsoleScreenBufferInfoEx“ zum Festlegen der Fensterbreite.</span><span class="sxs-lookup"><span data-stu-id="1a194-673">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="1a194-674">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-674">Sequence</span></span> | <span data-ttu-id="1a194-675">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-675">Code</span></span> | <span data-ttu-id="1a194-676">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-676">Description</span></span> | <span data-ttu-id="1a194-677">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-677">Behavior</span></span> |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="1a194-678">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="1a194-678">ESC \[ ?</span></span> <span data-ttu-id="1a194-679">3 h</span><span class="sxs-lookup"><span data-stu-id="1a194-679">3 h</span></span> | <span data-ttu-id="1a194-680">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="1a194-680">DECCOLM</span></span> | <span data-ttu-id="1a194-681">Anzahl der Spalten auf 132 festlegen</span><span class="sxs-lookup"><span data-stu-id="1a194-681">Set Number of Columns to 132</span></span> | <span data-ttu-id="1a194-682">Legt die Konsolenbreite auf 132 Spalten fest.</span><span class="sxs-lookup"><span data-stu-id="1a194-682">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="1a194-683">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="1a194-683">ESC \[ ?</span></span> <span data-ttu-id="1a194-684">3 l</span><span class="sxs-lookup"><span data-stu-id="1a194-684">3 l</span></span> | <span data-ttu-id="1a194-685">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="1a194-685">DECCOLM</span></span> | <span data-ttu-id="1a194-686">Anzahl der Spalten auf 80 festlegen</span><span class="sxs-lookup"><span data-stu-id="1a194-686">Set Number of Columns to 80</span></span> | <span data-ttu-id="1a194-687">Legt die Konsolenbreite auf 80 Spalten fest.</span><span class="sxs-lookup"><span data-stu-id="1a194-687">Sets the console width to 80 columns wide.</span></span> |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="1a194-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Vorläufiges Zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="1a194-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="1a194-689">Die folgende Sequenz kann verwendet werden, um bestimmte Eigenschaften auf ihre Standardwerte zurückzusetzen. Die folgenden Eigenschaften werden auf die folgenden Standardwerte zurückgesetzt (außerdem sind die Sequenzen aufgelistet, die diese Eigenschaften steuern):</span><span class="sxs-lookup"><span data-stu-id="1a194-689">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="1a194-690">Cursorsichtbarkeit: sichtbar (DECTEM)</span><span class="sxs-lookup"><span data-stu-id="1a194-690">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="1a194-691">Numerische Tastatur: Numerischer Modus (DECNKM)</span><span class="sxs-lookup"><span data-stu-id="1a194-691">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="1a194-692">Pfeiltasten-Modus: Normaler Modus (DECCKM)</span><span class="sxs-lookup"><span data-stu-id="1a194-692">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="1a194-693">Obere und untere Ränder: Top=1, Bottom=Konsolenhöhe (DECSTBM)</span><span class="sxs-lookup"><span data-stu-id="1a194-693">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="1a194-694">Zeichensatz: US ASCII</span><span class="sxs-lookup"><span data-stu-id="1a194-694">Character Set: US ASCII</span></span>
- <span data-ttu-id="1a194-695">Grafikwiedergabe: Standard/Aus(SGR)</span><span class="sxs-lookup"><span data-stu-id="1a194-695">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="1a194-696">Cursorzustand speichern: Startposition (0,0) (DECSC)</span><span class="sxs-lookup"><span data-stu-id="1a194-696">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="1a194-697">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-697">Sequence</span></span> | <span data-ttu-id="1a194-698">Code</span><span class="sxs-lookup"><span data-stu-id="1a194-698">Code</span></span> | <span data-ttu-id="1a194-699">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1a194-699">Description</span></span> | <span data-ttu-id="1a194-700">Verhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-700">Behavior</span></span> |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="1a194-701">ESC \[ !</span><span class="sxs-lookup"><span data-stu-id="1a194-701">ESC \[ !</span></span> <span data-ttu-id="1a194-702">p</span><span class="sxs-lookup"><span data-stu-id="1a194-702">p</span></span> | <span data-ttu-id="1a194-703">DECSTR</span><span class="sxs-lookup"><span data-stu-id="1a194-703">DECSTR</span></span> | <span data-ttu-id="1a194-704">Vorläufiges Zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="1a194-704">Soft Reset</span></span> | <span data-ttu-id="1a194-705">Setzt bestimmte Terminaleinstellungen auf ihre Standardeinstellungen zurück.</span><span class="sxs-lookup"><span data-stu-id="1a194-705">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="1a194-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Eingabesequenzen</span><span class="sxs-lookup"><span data-stu-id="1a194-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="1a194-707">Die folgenden Terminalsequenzen werden vom Konsolenhost im Eingabestream ausgegeben, wenn das Flag „ENABLE\_VIRTUAL\_TERMINAL\_INPUT“ auf dem Eingabepufferhandle mit dem Flag „SetConsoleMode“ festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="1a194-707">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="1a194-708">Es gibt zwei interne Modi, die steuern, welche Sequenzen für bestimmte Eingabetasten ausgegeben werden, den Pfeiltasten-Modus und den Zehnertastaturtasten-Modus.</span><span class="sxs-lookup"><span data-stu-id="1a194-708">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="1a194-709">Diese werden im Abschnitt „Modusänderungen“ beschrieben.</span><span class="sxs-lookup"><span data-stu-id="1a194-709">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="1a194-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span></span><span class="sxs-lookup"><span data-stu-id="1a194-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="1a194-711">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="1a194-711">Key</span></span> | <span data-ttu-id="1a194-712">Normaler Modus</span><span class="sxs-lookup"><span data-stu-id="1a194-712">Normal Mode</span></span> | <span data-ttu-id="1a194-713">Anwendungsmodus</span><span class="sxs-lookup"><span data-stu-id="1a194-713">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="1a194-714">NACH-OBEN</span><span class="sxs-lookup"><span data-stu-id="1a194-714">Up Arrow</span></span> | <span data-ttu-id="1a194-715">ESC \[ A</span><span class="sxs-lookup"><span data-stu-id="1a194-715">ESC \[ A</span></span> | <span data-ttu-id="1a194-716">ESC O A</span><span class="sxs-lookup"><span data-stu-id="1a194-716">ESC O A</span></span> |
| <span data-ttu-id="1a194-717">NACH-UNTEN</span><span class="sxs-lookup"><span data-stu-id="1a194-717">Down Arrow</span></span> | <span data-ttu-id="1a194-718">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="1a194-718">ESC \[ B</span></span> | <span data-ttu-id="1a194-719">ESC O B</span><span class="sxs-lookup"><span data-stu-id="1a194-719">ESC O B</span></span> |
| <span data-ttu-id="1a194-720">NACH-RECHTS</span><span class="sxs-lookup"><span data-stu-id="1a194-720">Right Arrow</span></span> | <span data-ttu-id="1a194-721">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="1a194-721">ESC \[ C</span></span> | <span data-ttu-id="1a194-722">ESC O C</span><span class="sxs-lookup"><span data-stu-id="1a194-722">ESC O C</span></span> |
| <span data-ttu-id="1a194-723">NACH-LINKS-TASTE</span><span class="sxs-lookup"><span data-stu-id="1a194-723">Left Arrow</span></span> | <span data-ttu-id="1a194-724">ESC \[ D</span><span class="sxs-lookup"><span data-stu-id="1a194-724">ESC \[ D</span></span> | <span data-ttu-id="1a194-725">ESC O D</span><span class="sxs-lookup"><span data-stu-id="1a194-725">ESC O D</span></span> |
| <span data-ttu-id="1a194-726">Startseite</span><span class="sxs-lookup"><span data-stu-id="1a194-726">Home</span></span> | <span data-ttu-id="1a194-727">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="1a194-727">ESC \[ H</span></span> | <span data-ttu-id="1a194-728">ESC O H</span><span class="sxs-lookup"><span data-stu-id="1a194-728">ESC O H</span></span> |
| <span data-ttu-id="1a194-729">Ende</span><span class="sxs-lookup"><span data-stu-id="1a194-729">End</span></span> | <span data-ttu-id="1a194-730">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="1a194-730">ESC \[ F</span></span> | <span data-ttu-id="1a194-731">ESC O F</span><span class="sxs-lookup"><span data-stu-id="1a194-731">ESC O F</span></span> |



<span data-ttu-id="1a194-732">Außerdem gilt Folgendes: Wenn die STRG-Taste mit einer dieser Tasten gedrückt wird, werden unabhängig vom Pfeiltasten-Modus stattdessen die folgenden Sequenzen ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="1a194-732">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="1a194-733">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="1a194-733">Key</span></span> | <span data-ttu-id="1a194-734">Beliebiger Modus</span><span class="sxs-lookup"><span data-stu-id="1a194-734">Any Mode</span></span> |
|--------------------|----------------|
| <span data-ttu-id="1a194-735">STRG+NACH-OBEN-TASTE</span><span class="sxs-lookup"><span data-stu-id="1a194-735">Ctrl + Up Arrow</span></span> | <span data-ttu-id="1a194-736">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="1a194-736">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="1a194-737">STRG+NACH-UNTEN-TASTE</span><span class="sxs-lookup"><span data-stu-id="1a194-737">Ctrl + Down Arrow</span></span> | <span data-ttu-id="1a194-738">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="1a194-738">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="1a194-739">ALT+NACH-RECHTS-TASTE</span><span class="sxs-lookup"><span data-stu-id="1a194-739">Ctrl + Right Arrow</span></span> | <span data-ttu-id="1a194-740">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="1a194-740">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="1a194-741">ALT+NACH-LINKS-TASTE</span><span class="sxs-lookup"><span data-stu-id="1a194-741">Ctrl + Left Arrow</span></span> | <span data-ttu-id="1a194-742">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="1a194-742">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="1a194-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numerische Tastatur und Funktionstasten</span><span class="sxs-lookup"><span data-stu-id="1a194-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="1a194-744">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="1a194-744">Key</span></span> | <span data-ttu-id="1a194-745">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-745">Sequence</span></span> |
|-----------|--------------|
| <span data-ttu-id="1a194-746">Rückschritt</span><span class="sxs-lookup"><span data-stu-id="1a194-746">Backspace</span></span> | <span data-ttu-id="1a194-747">0x7f (DEL)</span><span class="sxs-lookup"><span data-stu-id="1a194-747">0x7f (DEL)</span></span> |
| <span data-ttu-id="1a194-748">Anhalten</span><span class="sxs-lookup"><span data-stu-id="1a194-748">Pause</span></span> | <span data-ttu-id="1a194-749">0x1a (SUB)</span><span class="sxs-lookup"><span data-stu-id="1a194-749">0x1a (SUB)</span></span> |
| <span data-ttu-id="1a194-750">Escape</span><span class="sxs-lookup"><span data-stu-id="1a194-750">Escape</span></span> | <span data-ttu-id="1a194-751">0x1b (ESC)</span><span class="sxs-lookup"><span data-stu-id="1a194-751">0x1b (ESC)</span></span> |
| <span data-ttu-id="1a194-752">Einfügen</span><span class="sxs-lookup"><span data-stu-id="1a194-752">Insert</span></span> | <span data-ttu-id="1a194-753">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-753">ESC \[ 2 ~</span></span> |
| <span data-ttu-id="1a194-754">Löschen</span><span class="sxs-lookup"><span data-stu-id="1a194-754">Delete</span></span> | <span data-ttu-id="1a194-755">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-755">ESC \[ 3 ~</span></span> |
| <span data-ttu-id="1a194-756">BILD-AUF</span><span class="sxs-lookup"><span data-stu-id="1a194-756">Page Up</span></span> | <span data-ttu-id="1a194-757">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-757">ESC \[ 5 ~</span></span> |
| <span data-ttu-id="1a194-758">BILD-AB</span><span class="sxs-lookup"><span data-stu-id="1a194-758">Page Down</span></span> | <span data-ttu-id="1a194-759">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-759">ESC \[ 6 ~</span></span> |
| <span data-ttu-id="1a194-760">F1</span><span class="sxs-lookup"><span data-stu-id="1a194-760">F1</span></span> | <span data-ttu-id="1a194-761">ESC O P</span><span class="sxs-lookup"><span data-stu-id="1a194-761">ESC O P</span></span> |
| <span data-ttu-id="1a194-762">F2</span><span class="sxs-lookup"><span data-stu-id="1a194-762">F2</span></span> | <span data-ttu-id="1a194-763">ESC O Q</span><span class="sxs-lookup"><span data-stu-id="1a194-763">ESC O Q</span></span> |
| <span data-ttu-id="1a194-764">F3</span><span class="sxs-lookup"><span data-stu-id="1a194-764">F3</span></span> | <span data-ttu-id="1a194-765">ESC O R</span><span class="sxs-lookup"><span data-stu-id="1a194-765">ESC O R</span></span> |
| <span data-ttu-id="1a194-766">F4</span><span class="sxs-lookup"><span data-stu-id="1a194-766">F4</span></span> | <span data-ttu-id="1a194-767">ESC O S</span><span class="sxs-lookup"><span data-stu-id="1a194-767">ESC O S</span></span> |
| <span data-ttu-id="1a194-768">F5</span><span class="sxs-lookup"><span data-stu-id="1a194-768">F5</span></span> | <span data-ttu-id="1a194-769">ESC \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-769">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="1a194-770">F6</span><span class="sxs-lookup"><span data-stu-id="1a194-770">F6</span></span> | <span data-ttu-id="1a194-771">ESC \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-771">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="1a194-772">F7</span><span class="sxs-lookup"><span data-stu-id="1a194-772">F7</span></span> | <span data-ttu-id="1a194-773">ESC \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-773">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="1a194-774">F8</span><span class="sxs-lookup"><span data-stu-id="1a194-774">F8</span></span> | <span data-ttu-id="1a194-775">ESC \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-775">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="1a194-776">F9</span><span class="sxs-lookup"><span data-stu-id="1a194-776">F9</span></span> | <span data-ttu-id="1a194-777">ESC \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-777">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="1a194-778">F10</span><span class="sxs-lookup"><span data-stu-id="1a194-778">F10</span></span> | <span data-ttu-id="1a194-779">ESC \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-779">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="1a194-780">F11</span><span class="sxs-lookup"><span data-stu-id="1a194-780">F11</span></span> | <span data-ttu-id="1a194-781">ESC \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-781">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="1a194-782">F12</span><span class="sxs-lookup"><span data-stu-id="1a194-782">F12</span></span> | <span data-ttu-id="1a194-783">ESC \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="1a194-783">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="1a194-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifizierer</span><span class="sxs-lookup"><span data-stu-id="1a194-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="1a194-785">ALT wird behandelt, indem der Sequenz ein Escapezeichen vorangestellt wird: ESC &lt;c&gt; wobei &lt;c&gt; das vom Betriebssystem übergegebene Zeichen ist.</span><span class="sxs-lookup"><span data-stu-id="1a194-785">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="1a194-786">ALT+STRG wird auf die gleiche Weise behandelt, außer dass das Betriebssystem die Taste &lt;c&gt; vorab auf das entsprechende Steuerzeichen umgeschaltet hat, das an die Anwendung umgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="1a194-786">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="1a194-787">STRG wird im allgemeinen genau so weitergeleitet, wie vom System empfangen.</span><span class="sxs-lookup"><span data-stu-id="1a194-787">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="1a194-788">Dabei handelt es sich in der Regel um ein einzelnes Zeichen, das in den reservierten Speicherbereich (0x0-0x1F) des Steuerzeichens umgeschaltet wird.</span><span class="sxs-lookup"><span data-stu-id="1a194-788">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="1a194-789">STRG+@ (0x40) wird beispielsweise zu NUL (0x00), STRG+\[ (0x5b) zu ESC (0x1B) usw. Einige STRG-Tastenkombinationen werden entsprechend der folgenden Tabelle speziell behandelt:</span><span class="sxs-lookup"><span data-stu-id="1a194-789">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="1a194-790">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="1a194-790">Key</span></span> | <span data-ttu-id="1a194-791">Sequenz</span><span class="sxs-lookup"><span data-stu-id="1a194-791">Sequence</span></span> |
|--------------------|----------------|
| <span data-ttu-id="1a194-792">STRG+LEERTASTE</span><span class="sxs-lookup"><span data-stu-id="1a194-792">Ctrl + Space</span></span> | <span data-ttu-id="1a194-793">0x00 (NUL)</span><span class="sxs-lookup"><span data-stu-id="1a194-793">0x00 (NUL)</span></span> |
| <span data-ttu-id="1a194-794">STRG+NACH-OBEN-TASTE</span><span class="sxs-lookup"><span data-stu-id="1a194-794">Ctrl + Up Arrow</span></span> | <span data-ttu-id="1a194-795">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="1a194-795">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="1a194-796">STRG+NACH-UNTEN-TASTE</span><span class="sxs-lookup"><span data-stu-id="1a194-796">Ctrl + Down Arrow</span></span> | <span data-ttu-id="1a194-797">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="1a194-797">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="1a194-798">ALT+NACH-RECHTS-TASTE</span><span class="sxs-lookup"><span data-stu-id="1a194-798">Ctrl + Right Arrow</span></span> | <span data-ttu-id="1a194-799">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="1a194-799">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="1a194-800">ALT+NACH-LINKS-TASTE</span><span class="sxs-lookup"><span data-stu-id="1a194-800">Ctrl + Left Arrow</span></span> | <span data-ttu-id="1a194-801">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="1a194-801">ESC \[ 1 ; 5 D</span></span> |



> [!NOTE]
><span data-ttu-id="1a194-802">Links <kbd>STRG</kbd>+Rechts <kbd>ALT</kbd> wird wie ALTGR behandelt.</span><span class="sxs-lookup"><span data-stu-id="1a194-802">Left <kbd>Ctrl</kbd> + Right <kbd>Alt</kbd> is treated as AltGr.</span></span> <span data-ttu-id="1a194-803">Werden beide zusammen festgestellt, werden sie entfernt, und der Unicodewert des vom System dargestellten Zeichens wird in das Ziel übergeben.</span><span class="sxs-lookup"><span data-stu-id="1a194-803">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="1a194-804">Das System übersetzt ALTGR-Werte entsprechend den aktuellen Systemeingabeeinstellungen vor.</span><span class="sxs-lookup"><span data-stu-id="1a194-804">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="1a194-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Beispiele</span><span class="sxs-lookup"><span data-stu-id="1a194-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="1a194-806"><span id="example"></span><span id="EXAMPLE"></span>Beispiel für SGR-Terminalsequenzen</span><span class="sxs-lookup"><span data-stu-id="1a194-806"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="1a194-807">Der folgende Code enthält mehrere Beispiele für die Textformatierung.</span><span class="sxs-lookup"><span data-stu-id="1a194-807">The following code provides several examples of text formatting.</span></span>

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
><span data-ttu-id="1a194-808">Im vorhergehenden Beispiel ist die Zeichenfolge „`\x1b[31m`“ die Implementierung von **ESC \[ &lt;n&gt; m**, wobei &lt;n&gt; gleich „31“ ist.</span><span class="sxs-lookup"><span data-stu-id="1a194-808">In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="1a194-809">Die folgende Grafik zeigt die Ausgabe des vorherigen Codebeispiels.</span><span class="sxs-lookup"><span data-stu-id="1a194-809">The following graphic shows the output of the previous code example.</span></span>

![Ausgabe der Konsole mit dem SGR-Befehl](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="1a194-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Beispiel für das Aktivieren der virtuellen Terminalverarbeitung</span><span class="sxs-lookup"><span data-stu-id="1a194-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="1a194-812">Der folgende Code enthält ein Beispiel für die empfohlene Vorgehensweise zum Aktivieren der virtuellen Terminalverarbeitung für eine Anwendung.</span><span class="sxs-lookup"><span data-stu-id="1a194-812">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="1a194-813">Das Beispiel soll Folgendes veranschaulichen:</span><span class="sxs-lookup"><span data-stu-id="1a194-813">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="1a194-814">Der bestehende Modus sollte immer über „GetConsoleMode“ abgerufen und analysiert werden, bevor der Modus mit „SetConsoleMode“ festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="1a194-814">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="1a194-815">Die Überprüfung, ob „SetConsoleMode“ `0` und „GetLastError“ STATUS\_INVALID\_PARAMETER zurückgibt, ist der aktuelle Bestimmungsmechanismus bei der Ausführung auf einem System mit einer Vorgängerversion.</span><span class="sxs-lookup"><span data-stu-id="1a194-815">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="1a194-816">Eine Anwendung, die STATUS\_INVALID\_PARAMETER mit einem der neueren Konsolenmodusflags im Bitfeld empfängt, sollte das Verhalten ordnungsgemäß herabstufen und den Vorgang wiederholen.</span><span class="sxs-lookup"><span data-stu-id="1a194-816">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="1a194-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Beispiel für ausgewählte Anniversary Update-Features</span><span class="sxs-lookup"><span data-stu-id="1a194-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="1a194-818">Im Folgenden sehen Sie ein robusteres Beispiel für Code, der eine Vielzahl von Escapesequenzen verwendet, um den Puffer zu bearbeiten, wobei der Schwerpunkt auf den Features liegt, die im Anniversary Update für Windows 10 hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="1a194-818">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="1a194-819">In diesem Beispiel wird der alternative Bildschirmpuffer verwendet, es werden Tabstopps bearbeitet und Bildlaufränder festgelegt und der Zeichensatz wird geändert.</span><span class="sxs-lookup"><span data-stu-id="1a194-819">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

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








