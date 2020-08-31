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
# <a name="high-level-console-modes"></a><span data-ttu-id="642f7-104">Allgemeine Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="642f7-104">High-Level Console Modes</span></span>


<span data-ttu-id="642f7-105">Das Verhalten der hauptkonsolen Funktionen ist von den Konsolen Eingabe-und Ausgabe Modi betroffen.</span><span class="sxs-lookup"><span data-stu-id="642f7-105">The behavior of the high-level console functions is affected by the console input and output modes.</span></span> <span data-ttu-id="642f7-106">Alle folgenden Konsolen Eingabemodi werden bei der Erstellung einer-Konsole für den Eingabepuffer einer Konsole aktiviert:</span><span class="sxs-lookup"><span data-stu-id="642f7-106">All of the following console input modes are enabled for a console's input buffer when a console is created:</span></span>

- <span data-ttu-id="642f7-107">Zeilen Eingabemodus</span><span class="sxs-lookup"><span data-stu-id="642f7-107">Line input mode</span></span>
- <span data-ttu-id="642f7-108">Verarbeiteter Eingabemodus</span><span class="sxs-lookup"><span data-stu-id="642f7-108">Processed input mode</span></span>
- <span data-ttu-id="642f7-109">Echo Eingabemodus</span><span class="sxs-lookup"><span data-stu-id="642f7-109">Echo input mode</span></span>

<span data-ttu-id="642f7-110">Beide der folgenden Konsolenausgabe Modi sind bei der Erstellung für einen Konsolenbildschirm Puffer aktiviert:</span><span class="sxs-lookup"><span data-stu-id="642f7-110">Both of the following console output modes are enabled for a console screen buffer when it is created:</span></span>

- <span data-ttu-id="642f7-111">Verarbeiteter Ausgabemodus</span><span class="sxs-lookup"><span data-stu-id="642f7-111">Processed output mode</span></span>
- <span data-ttu-id="642f7-112">Umwickeln im EOL-Ausgabemodus</span><span class="sxs-lookup"><span data-stu-id="642f7-112">Wrapping at EOL output mode</span></span>

<span data-ttu-id="642f7-113">Alle drei Eingabemodi, zusammen mit dem verarbeiteten Ausgabemodus, sind so konzipiert, dass Sie zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="642f7-113">All three input modes, along with processed output mode, are designed to work together.</span></span> <span data-ttu-id="642f7-114">Es empfiehlt sich, alle diese Modi als Gruppe zu aktivieren oder zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="642f7-114">It is best to either enable or disable all of these modes as a group.</span></span> <span data-ttu-id="642f7-115">Wenn alle aktiviert sind, wird die Anwendung als "gekochter" Modus bezeichnet, was bedeutet, dass der meiste Teil der Verarbeitung für die Anwendung verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="642f7-115">When all are enabled, the application is said to be in "cooked" mode, which means that most of the processing is handled for the application.</span></span> <span data-ttu-id="642f7-116">Wenn alle deaktiviert sind, befindet sich die Anwendung im RAW-Modus, was bedeutet, dass die Eingabe ungefiltert und jede Verarbeitung an die Anwendung übertragen wird.</span><span class="sxs-lookup"><span data-stu-id="642f7-116">When all are disabled, the application is in "raw" mode, which means that input is unfiltered and any processing is left to the application.</span></span>

<span data-ttu-id="642f7-117">Eine Anwendung kann die [**getconsolemode**](getconsolemode.md) -Funktion verwenden, um den aktuellen Modus des Eingabe Puffers oder Bildschirm Puffers einer Konsole zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="642f7-117">An application can use the [**GetConsoleMode**](getconsolemode.md) function to determine the current mode of a console's input buffer or screen buffer.</span></span> <span data-ttu-id="642f7-118">Sie können jeden dieser Modi aktivieren oder deaktivieren, indem Sie die folgenden Werte in der [**setconsolemode**](setconsolemode.md) -Funktion verwenden.</span><span class="sxs-lookup"><span data-stu-id="642f7-118">You can enable or disable any of these modes by using the following values in the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="642f7-119">Beachten Sie, dass sich das Festlegen des Ausgabemodus eines Bildschirm Puffers nicht auf den Ausgabemodus anderer Bildschirm Puffer auswirkt.</span><span class="sxs-lookup"><span data-stu-id="642f7-119">Note that setting the output mode of one screen buffer does not affect the output mode of other screen buffers.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="642f7-120">Mode</span><span class="sxs-lookup"><span data-stu-id="642f7-120">Mode</span></span></th>
<th><span data-ttu-id="642f7-121">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="642f7-121">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="642f7-122"><strong>ENABLE_PROCESSED_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="642f7-122"><strong>ENABLE_PROCESSED_INPUT</strong></span></span></td>
<td><span data-ttu-id="642f7-123">Wird mit einem Konsolen Eingabe Handle verwendet, um zu bewirken, dass das System alle systembearbeitungs-oder Steuerelement Schlüssel Eingaben verarbeitet, anstatt Sie als Eingabe im Lesevorgang&#39;s-Puffer zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="642f7-123">Used with a console input handle to cause the system to process any system editing or control key input rather than returning it as input in the read operation&#39;s buffer.</span></span> <span data-ttu-id="642f7-124">Wenn die Zeilen Eingabe ebenfalls aktiviert ist, werden backspaces und Wagen Rückläufe ordnungsgemäß verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="642f7-124">If line input is also enabled, backspaces and carriage returns are handled correctly.</span></span> <span data-ttu-id="642f7-125">Ein Rückraum bewirkt, dass der Cursor ein Leerzeichen zurückbewegt, ohne das Zeichen an der Cursorposition zu beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="642f7-125">A backspace causes the cursor to move back one space without affecting the character at the cursor position.</span></span> <span data-ttu-id="642f7-126">Ein Wagen Rücklauf wird in die Kombination aus Wagen Rücklauf – Zeilenvorschub Zeichen konvertiert.</span><span class="sxs-lookup"><span data-stu-id="642f7-126">A carriage return is converted to carriage return – line feed character combination.</span></span> <span data-ttu-id="642f7-127">Wenn der Echo Eingabemodus aktiviert ist und die Ausgabe die System Bearbeitung widerspiegeln soll, muss die verarbeitete Ausgabe für den aktiven Bildschirm Puffer aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="642f7-127">If echo input mode is enabled and the output should reflect system editing, processed output must be enabled for the active screen buffer.</span></span> <span data-ttu-id="642f7-128">Wenn die verarbeitete Eingabe aktiviert ist, wird die Tastenkombination STRG + C unabhängig davon, ob die Zeilen Eingabe aktiviert ist, an den entsprechenden Handler weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="642f7-128">If processed input is enabled, the CTRL+C key combination is passed on to the appropriate handler regardless of whether line input is enabled.</span></span> <span data-ttu-id="642f7-129">Weitere Informationen zu Steuerelement Handlern finden Sie unter <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">Konsolen Steuerungs Handler</a>.</span><span class="sxs-lookup"><span data-stu-id="642f7-129">For more information about control handlers, see <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">Console Control Handlers</a>.</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="642f7-130"><strong>ENABLE_LINE_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="642f7-130"><strong>ENABLE_LINE_INPUT</strong></span></span></td>
<td><span data-ttu-id="642f7-131">Wird mit einem Konsolen Eingabe Handle verwendet, damit die Funktionen von "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " und "read <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>Console</strong></a> " zurückgegeben werden, wenn die EINGABETASTE gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="642f7-131">Used with a console input handle to cause the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> and <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> functions to return when the ENTER key is pressed.</span></span> <span data-ttu-id="642f7-132">Wenn der Zeilen Eingabemodus deaktiviert ist, geben die Funktionen zurück, wenn ein oder mehrere Zeichen im Eingabepuffer verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="642f7-132">If line input mode is disabled, the functions return when one or more characters are available in the input buffer.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="642f7-133"><strong>ENABLE_ECHO_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="642f7-133"><strong>ENABLE_ECHO_INPUT</strong></span></span></td>
<td><span data-ttu-id="642f7-134">Wird mit einem Konsolen Eingabe Handle verwendet, um die von der Funktion "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder "read <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>Console</strong></a> " gelesenen Tastatureingaben in den aktiven Bildschirm Puffer zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="642f7-134">Used with a console input handle to cause keyboard input read by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function to be echoed to the active screen buffer.</span></span> <span data-ttu-id="642f7-135">Zeichen werden nur dann angezeigt, wenn der Prozess, der " <strong>Infofile</strong> " oder " <strong>infoconsole</strong> " aufruft, ein geöffnetes Handle für den aktiven Bildschirm Puffer aufweist</span><span class="sxs-lookup"><span data-stu-id="642f7-135">Characters are echoed only if the process that calls <strong>ReadFile</strong> or <strong>ReadConsole</strong> has an open handle to the active screen buffer.</span></span> <span data-ttu-id="642f7-136">Der Echo Modus kann nur aktiviert werden, wenn die Zeilen Eingabe ebenfalls aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="642f7-136">Echo mode cannot be enabled unless line input is also enabled.</span></span> <span data-ttu-id="642f7-137">Der Ausgabemodus des aktiven Bildschirm Puffers wirkt sich auf die Anzeige von ECHO Eingaben aus.</span><span class="sxs-lookup"><span data-stu-id="642f7-137">The output mode of the active screen buffer affects the way echoed input is displayed.</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="642f7-138"><strong>ENABLE_PROCESSED_OUTPUT</strong></span><span class="sxs-lookup"><span data-stu-id="642f7-138"><strong>ENABLE_PROCESSED_OUTPUT</strong></span></span></td>
<td><span data-ttu-id="642f7-139">Wird mit einem Konsolenbildschirm Puffer Handle verwendet, um zu bewirken, dass das System die entsprechende Aktion für ANSI-Steuerzeichen ausführt, die in einen Bildschirm Puffer geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="642f7-139">Used with a console screen buffer handle to cause the system to perform the appropriate action for ANSI control characters that are written to a screen buffer.</span></span> <span data-ttu-id="642f7-140">Die RÜCKTASTE, Tab, Glocken, Wagen Rücklauf-und Zeilenvorschub Zeichen werden verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="642f7-140">The backspace, tab, bell, carriage return, and line feed characters are processed.</span></span> <span data-ttu-id="642f7-141">Ein Tabstopp Zeichen verschiebt den Cursor an den nächsten Tabstopp, der alle acht Zeichen umfasst.</span><span class="sxs-lookup"><span data-stu-id="642f7-141">A tab character moves the cursor to the next tab stop, which occurs every eight characters.</span></span> <span data-ttu-id="642f7-142">Ein Glocken Zeichen klingt ein kurzes Ton.</span><span class="sxs-lookup"><span data-stu-id="642f7-142">A bell character sounds a short tone.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="642f7-143"><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></span><span class="sxs-lookup"><span data-stu-id="642f7-143"><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></span></span></td>
<td><span data-ttu-id="642f7-144">Wird mit einem Konsolenbildschirm Puffer Handle verwendet, um zu bewirken, dass die aktuelle Ausgabe Position (Cursorposition) zur ersten Spalte in der nächsten Zeile (Zeile) wechselt, wenn das Ende der aktuellen Zeile erreicht ist.</span><span class="sxs-lookup"><span data-stu-id="642f7-144">Used with a console screen buffer handle to cause the current output position (cursor position) to move to the first column in the next row (line) when the end of the current row is reached.</span></span> <span data-ttu-id="642f7-145">Wenn der untere Rand des Fenster Bereichs erreicht ist, wird der Fenster Ursprung um eine Zeile nach unten verschoben.</span><span class="sxs-lookup"><span data-stu-id="642f7-145">If the bottom of the window region is reached, the window origin is moved down one row.</span></span> <span data-ttu-id="642f7-146">Diese Bewegung hat den Effekt, dass der Inhalt des Fensters eine Zeile nach oben durchführt.</span><span class="sxs-lookup"><span data-stu-id="642f7-146">This movement has the effect of scrolling the contents of the window up one row.</span></span> <span data-ttu-id="642f7-147">Wenn das Ende des Konsolenbildschirm Puffers erreicht ist, wird der Inhalt des Bildschirm Puffers der Konsole um eine Zeile nach oben gescrollt, und die obere Zeile des Konsolenbildschirm Puffers wird verworfen.</span><span class="sxs-lookup"><span data-stu-id="642f7-147">If the bottom of the console screen buffer is reached, the contents of the console screen buffer are scrolled up one row, and the top row of the console screen buffer is discarded.</span></span>
<p><span data-ttu-id="642f7-148">Wenn dieser Modus deaktiviert ist, wird das letzte Zeichen in der Zeile mit allen nachfolgenden Zeichen überschrieben.</span><span class="sxs-lookup"><span data-stu-id="642f7-148">If this mode is disabled, the last character in the row is overwritten with any subsequent characters.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

 

 




