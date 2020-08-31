---
title: Getconsolemode-Funktion
description: Ruft den aktuellen Eingabemodus für den Eingabepuffer einer Konsole oder den aktuellen Ausgabemodus eines Konsolenbildschirm Puffers ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a2d18ed191d1d82cc54c3277aa38badb0aedb630
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059739"
---
# <a name="getconsolemode-function"></a><span data-ttu-id="06573-104">Getconsolemode-Funktion</span><span class="sxs-lookup"><span data-stu-id="06573-104">GetConsoleMode function</span></span>


<span data-ttu-id="06573-105">Ruft den aktuellen Eingabemodus für den Eingabepuffer einer Konsole oder den aktuellen Ausgabemodus eines Konsolenbildschirm Puffers ab.</span><span class="sxs-lookup"><span data-stu-id="06573-105">Retrieves the current input mode of a console's input buffer or the current output mode of a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="06573-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="06573-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

<a name="parameters"></a><span data-ttu-id="06573-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="06573-107">Parameters</span></span>
----------

<span data-ttu-id="06573-108">*hconsolehandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="06573-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="06573-109">Ein Handle des Konsolen Eingabe Puffers oder des Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="06573-109">A handle to the console input buffer or the console screen buffer.</span></span> <span data-ttu-id="06573-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="06573-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="06573-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="06573-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="06573-112">*lpmode* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="06573-112">*lpMode* \[out\]</span></span>  
<span data-ttu-id="06573-113">Ein Zeiger auf eine Variable, die den aktuellen Modus des angegebenen Puffers empfängt.</span><span class="sxs-lookup"><span data-stu-id="06573-113">A pointer to a variable that receives the current mode of the specified buffer.</span></span>

<span data-ttu-id="06573-114">Wenn der *hconsolehandle* -Parameter ein Eingabe Handle ist, kann der Modus einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="06573-114">If the *hConsoleHandle* parameter is an input handle, the mode can be one or more of the following values.</span></span> <span data-ttu-id="06573-115">Wenn eine-Konsole erstellt wird, sind alle Eingabemodi mit Ausnahme von \*\* \_ Fenster \_ Eingabe aktivieren\*\* standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="06573-115">When a console is created, all input modes except **ENABLE\_WINDOW\_INPUT** are enabled by default.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="06573-116">Wert</span><span class="sxs-lookup"><span data-stu-id="06573-116">Value</span></span></th>
<th><span data-ttu-id="06573-117">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="06573-117">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="06573-118"><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="06573-118"><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="06573-119">Zeichen, die von der Funktion "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder "read <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>Console</strong></a> " gelesen werden, werden beim Lesen in den aktiven Bildschirm Puffer geschrieben.</span><span class="sxs-lookup"><span data-stu-id="06573-119">Characters read by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function are written to the active screen buffer as they are read.</span></span> <span data-ttu-id="06573-120">Dieser Modus kann nur verwendet werden, wenn der <strong>ENABLE_LINE_INPUT</strong> Modus ebenfalls aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="06573-120">This mode can be used only if the <strong>ENABLE_LINE_INPUT</strong> mode is also enabled.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="06573-121"><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="06573-121"><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="06573-122">Wenn diese Option aktiviert ist, wird der in einem Konsolenfenster eingegebene Text an der aktuellen Cursorposition eingefügt, und der gesamte Text, der diesem Speicherort folgt, wird nicht überschrieben.</span><span class="sxs-lookup"><span data-stu-id="06573-122">When enabled, text entered in a console window will be inserted at the current cursor location and all text following that location will not be overwritten.</span></span> <span data-ttu-id="06573-123">Wenn diese Option deaktiviert ist, wird der gesamte folgende Text überschrieben.</span><span class="sxs-lookup"><span data-stu-id="06573-123">When disabled, all following text will be overwritten.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="06573-124"><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="06573-124"><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="06573-125">Die Funktion "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder "read <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>Console</strong></a> " gibt nur zurück, wenn ein Wagen Rücklauf Zeichen gelesen wird.</span><span class="sxs-lookup"><span data-stu-id="06573-125">The <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function returns only when a carriage return character is read.</span></span> <span data-ttu-id="06573-126">Wenn dieser Modus deaktiviert ist, geben die Funktionen zurück, wenn ein oder mehrere Zeichen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="06573-126">If this mode is disabled, the functions return when one or more characters are available.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="06573-127"><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="06573-127"><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="06573-128">Wenn sich der Mauszeiger innerhalb der Rahmen des Konsolenfensters befindet und das Fenster den Tastaturfokus besitzt, werden Mausereignisse, die durch Mausbewegung und Schaltflächen drückt werden, im Eingabepuffer platziert.</span><span class="sxs-lookup"><span data-stu-id="06573-128">If the mouse pointer is within the borders of the console window and the window has the keyboard focus, mouse events generated by mouse movement and button presses are placed in the input buffer.</span></span> <span data-ttu-id="06573-129">Diese Ereignisse werden von "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder " <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>infoconsole</strong></a>" verworfen, auch wenn dieser Modus aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="06573-129">These events are discarded by <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, even when this mode is enabled.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="06573-130"><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="06573-130"><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="06573-131">STRG + C wird vom System verarbeitet und nicht im Eingabepuffer platziert.</span><span class="sxs-lookup"><span data-stu-id="06573-131">CTRL+C is processed by the system and is not placed in the input buffer.</span></span> <span data-ttu-id="06573-132">Wenn der Eingabepuffer von " <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>Infofile</strong></a> " oder " <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>infoconsole</strong></a>" gelesen wird, werden andere Steuerungs Schlüssel vom System verarbeitet und nicht im <strong>lesefile</strong> -oder <strong>leseconsole</strong> -Puffer zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="06573-132">If the input buffer is being read by <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, other control keys are processed by the system and are not returned in the <strong>ReadFile</strong> or <strong>ReadConsole</strong> buffer.</span></span> <span data-ttu-id="06573-133">Wenn der <strong>ENABLE_LINE_INPUT</strong> Modus ebenfalls aktiviert ist, werden Rücktaste, Wagen Rücklauf und Zeilenvorschub Zeichen vom System behandelt.</span><span class="sxs-lookup"><span data-stu-id="06573-133">If the <strong>ENABLE_LINE_INPUT</strong> mode is also enabled, backspace, carriage return, and line feed characters are handled by the system.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="06573-134"><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="06573-134"><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="06573-135">Dieses Flag ermöglicht dem Benutzer die Verwendung der Maus, um Text auszuwählen und zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="06573-135">This flag enables the user to use the mouse to select and edit text.</span></span></p>
<p><span data-ttu-id="06573-136">Verwenden Sie, um diesen Modus zu aktivieren <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code> .</span><span class="sxs-lookup"><span data-stu-id="06573-136">To enable this mode, use <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code>.</span></span> <span data-ttu-id="06573-137">Verwenden Sie <strong>ENABLE_EXTENDED_FLAGS</strong> ohne dieses Flag, um diesen Modus zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="06573-137">To disable this mode, use <strong>ENABLE_EXTENDED_FLAGS</strong> without this flag.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="06573-138"><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="06573-138"><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="06573-139">Benutzerinteraktionen, die die Größe des Konsolenbildschirm Puffers ändern, werden im Eingabepuffer der Konsole&#39;s angezeigt.</span><span class="sxs-lookup"><span data-stu-id="06573-139">User interactions that change the size of the console screen buffer are reported in the console&#39;s input buffer.</span></span> <span data-ttu-id="06573-140">Informationen zu diesen Ereignissen können von Anwendungen, die die Funktion " <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>leseconsoleinput</strong></a> " verwenden, aus dem Eingabepuffer gelesen werden, aber nicht von denjenigen, die "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder " <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>infoconsole</strong></a>" verwenden.</span><span class="sxs-lookup"><span data-stu-id="06573-140">Information about these events can be read from the input buffer by applications using the <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> function, but not by those using <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="06573-141"><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</span><span class="sxs-lookup"><span data-stu-id="06573-141"><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</span></span></td>
<td><p><span data-ttu-id="06573-142">Das Festlegen dieses Flags bewirkt, dass die Engine für die virtuelle terminalverarbeitungs-Engine Benutzereingaben, die vom Konsolenfenster empfangen werden, in <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Konsolen-virtuelle Terminal Sequenzen</a> konvertieren, die von einer unterstützenden Anwendung <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>durch Funktionen vom</strong></a> <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>Typ</strong></a> "schreiben" oder "schreiben" abgerufen werden</span><span class="sxs-lookup"><span data-stu-id="06573-142">Setting this flag directs the Virtual Terminal processing engine to convert user input received by the console window into <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a> that can be retrieved by a supporting application through <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> functions.</span></span></p>
<p><span data-ttu-id="06573-143">Die typische Verwendung dieses Flags ist in Verbindung mit ENABLE_VIRTUAL_TERMINAL_PROCESSING des Ausgabe Handles zum Herstellen einer Verbindung mit einer Anwendung vorgesehen, die ausschließlich über virtuelle Terminal Sequenzen kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="06573-143">The typical usage of this flag is intended in conjunction with ENABLE_VIRTUAL_TERMINAL_PROCESSING on the output handle to connect to an application that communicates exclusively via virtual terminal sequences.</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="06573-144">Wenn der *hconsolehandle* -Parameter ein Bildschirm Puffer Handle ist, kann der Modus einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="06573-144">If the *hConsoleHandle* parameter is a screen buffer handle, the mode can be one or more of the following values.</span></span> <span data-ttu-id="06573-145">Beim Erstellen eines Bildschirm Puffers sind beide Ausgabe Modi standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="06573-145">When a screen buffer is created, both output modes are enabled by default.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="06573-146">Wert</span><span class="sxs-lookup"><span data-stu-id="06573-146">Value</span></span></th>
<th><span data-ttu-id="06573-147">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="06573-147">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="06573-148"><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="06573-148"><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="06573-149">Zeichen, die von der Funktion " <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>Write File</strong></a> " oder der Funktion " <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>Write-Console</strong></a> " geschrieben oder von der Funktion "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder "read <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>Console</strong></a> " wiederholt werden, werden für ASCII-Steuersequenzen analysiert</span><span class="sxs-lookup"><span data-stu-id="06573-149">Characters written by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> function or echoed by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function are parsed for ASCII control sequences, and the correct action is performed.</span></span> <span data-ttu-id="06573-150">Rücktaste, Tabulator, Glocken Zeichen, Wagen Rücklauf und Zeilenvorschub Zeichen werden verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="06573-150">Backspace, tab, bell, carriage return, and line feed characters are processed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="06573-151"><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="06573-151"><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="06573-152">Beim Schreiben mit " <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> " oder " <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>writeconsole</strong></a> " oder "Echo" mit " <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>Infofile</strong></a> " oder " <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>infoconsole</strong></a>" wechselt der Cursor zum Anfang der nächsten Zeile, wenn er das Ende der aktuellen Zeile erreicht.</span><span class="sxs-lookup"><span data-stu-id="06573-152">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> or echoing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, the cursor moves to the beginning of the next row when it reaches the end of the current row.</span></span> <span data-ttu-id="06573-153">Dies bewirkt, dass die im Konsolenfenster angezeigten Zeilen automatisch nach oben scrollen, wenn der Cursor die letzte Zeile im Fenster überschreitet.</span><span class="sxs-lookup"><span data-stu-id="06573-153">This causes the rows displayed in the console window to scroll up automatically when the cursor advances beyond the last row in the window.</span></span> <span data-ttu-id="06573-154">Außerdem bewirkt dies, dass der Inhalt des Konsolenbildschirm Puffers nach oben bewegt wird (wobei die obere Zeile des Konsolenbildschirm Puffers verworfen wird), wenn der Cursor die letzte Zeile des Konsolenbildschirm Puffers überschreitet.</span><span class="sxs-lookup"><span data-stu-id="06573-154">It also causes the contents of the console screen buffer to scroll up (discarding the top row of the console screen buffer) when the cursor advances beyond the last row in the console screen buffer.</span></span> <span data-ttu-id="06573-155">Wenn dieser Modus deaktiviert ist, wird das letzte Zeichen in der Zeile mit allen nachfolgenden Zeichen überschrieben.</span><span class="sxs-lookup"><span data-stu-id="06573-155">If this mode is disabled, the last character in the row is overwritten with any subsequent characters.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="06573-156"><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="06573-156"><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="06573-157">Beim Schreiben mit <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> oder <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>writeconsole</strong></a>werden Zeichen für VT100 und ähnliche Steuerzeichen Sequenzen analysiert, die die Cursor Bewegung, den Farb-/schriftmodus und andere Vorgänge steuern, die auch über die vorhandenen Konsolen-APIs ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="06573-157">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, characters are parsed for VT100 and similar control character sequences that control cursor movement, color/font mode, and other operations that can also be performed via the existing Console APIs.</span></span> <span data-ttu-id="06573-158">Weitere Informationen finden Sie unter <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Konsolen virtuelle Terminal Sequenzen</a>.</span><span class="sxs-lookup"><span data-stu-id="06573-158">For more information, see <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a>.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="06573-159"><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="06573-159"><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="06573-160">Wenn Sie mit <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> oder <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>writeconsole</strong></a>schreiben, fügt dies einen zusätzlichen Zustand zum Zeilen umschließen hinzu, der den Cursor Verschiebe-und Puffer scrollvorgang verzögern kann.</span><span class="sxs-lookup"><span data-stu-id="06573-160">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, this adds an additional state to end-of-line wrapping that can delay the cursor move and buffer scroll operations.</span></span></p>
<p><span data-ttu-id="06573-161">Wenn ENABLE_WRAP_AT_EOL_OUTPUT festgelegt ist und Text das Ende der Zeile erreicht, wird der Cursor normalerweise in die nächste Zeile verschoben, und der Inhalt des Puffers wird um eine Zeile nach oben verschoben.</span><span class="sxs-lookup"><span data-stu-id="06573-161">Normally when ENABLE_WRAP_AT_EOL_OUTPUT is set and text reaches the end of the line, the cursor will immediately move to the next line and the contents of the buffer will scroll up by one line.</span></span> <span data-ttu-id="06573-162">Im Gegensatz zu diesem Flag wird der scrollvorgang und die Cursor Verschiebung verzögert, bis das nächste Zeichen eintrifft.</span><span class="sxs-lookup"><span data-stu-id="06573-162">In contrast with this flag set, the scroll operation and cursor move is delayed until the next character arrives.</span></span> <span data-ttu-id="06573-163">Das geschriebene Zeichen wird an der endgültigen Position in der Zeile gedruckt, und der Cursor bleibt über diesem Zeichen, als wäre ENABLE_WRAP_AT_EOL_OUTPUT deaktiviert, aber das nächste Druck bare Zeichen wird gedruckt, als ob ENABLE_WRAP_AT_EOL_OUTPUT on ist.</span><span class="sxs-lookup"><span data-stu-id="06573-163">The written character will be printed in the final position on the line and the cursor will remain above this character as if ENABLE_WRAP_AT_EOL_OUTPUT was off, but the next printable character will be printed as if ENABLE_WRAP_AT_EOL_OUTPUT is on.</span></span> <span data-ttu-id="06573-164">Es erfolgt kein überschreiben.</span><span class="sxs-lookup"><span data-stu-id="06573-164">No overwrite will occur.</span></span> <span data-ttu-id="06573-165">Insbesondere wechselt der Cursor schnell zur folgenden Zeile, ein Bildlauf wird bei Bedarf ausgeführt, das Zeichen wird gedruckt, und der Cursor verschiebt eine weitere Position.</span><span class="sxs-lookup"><span data-stu-id="06573-165">Specifically, the cursor quickly advances down to the following line, a scroll is performed if necessary, the character is printed, and the cursor advances one more position.</span></span></p>
<p><span data-ttu-id="06573-166">Die typische Verwendung dieses Flags ist in Verbindung mit der Festlegung ENABLE_VIRTUAL_TERMINAL_PROCESSING vorgesehen, um einen Terminal Emulator besser zu emulieren, bei dem das abschließende Zeichen auf dem Bildschirm (in der unteren rechten Ecke) geschrieben wird, ohne dass ein sofortiger scrollvorgang ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="06573-166">The typical usage of this flag is intended in conjunction with setting ENABLE_VIRTUAL_TERMINAL_PROCESSING to better emulate a terminal emulator where writing the final character on the screen (in the bottom right corner) without triggering an immediate scroll is the desired behavior.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="06573-167"><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="06573-167"><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="06573-168">Die APIs zum Schreiben von Zeichen Attributen einschließlich <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>writeconsoleoutput</strong></a> und <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>writeconsoleoutputattribute</strong></a> ermöglichen die Verwendung von Flags aus <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">Zeichen Attributen</a> , um die Farbe des Vordergrunds und des Hintergrunds von Text anzupassen.</span><span class="sxs-lookup"><span data-stu-id="06573-168">The APIs for writing character attributes including <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> and <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> allow the usage of flags from <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">character attributes</a> to adjust the color of the foreground and background of text.</span></span> <span data-ttu-id="06573-169">Außerdem wurde ein Bereich von DBCS-Flags mit dem COMMON_LVB-Präfix angegeben.</span><span class="sxs-lookup"><span data-stu-id="06573-169">Additionally, a range of DBCS flags was specified with the COMMON_LVB prefix.</span></span> <span data-ttu-id="06573-170">In der Vergangenheit wurden diese Flags nur in DBCS-Codepages für Chinesisch, Japanisch und Koreanisch unterbunden.</span><span class="sxs-lookup"><span data-stu-id="06573-170">Historically, these flags only functioned in DBCS code pages for Chinese, Japanese, and Korean languages.</span></span></p>
<p><span data-ttu-id="06573-171">Mit Ausnahme der führenden Byte-und nachfolgenden byteflags können die restlichen Flags, die das Zeichnen von Zeilen und das umgekehrte Video beschreiben (austauschen von Vordergrund-und Hintergrundfarben), nützlich sein, damit andere Sprachen Teile der Ausgabe hervorheben können.</span><span class="sxs-lookup"><span data-stu-id="06573-171">With exception of the leading byte and trailing byte flags, the remaining flags describing line drawing and reverse video (swap foreground and background colors) can be useful for other languages to emphasize portions of output.</span></span></p>
<p><span data-ttu-id="06573-172">Durch Festlegen dieses Konsolenmodus-Flags können diese Attribute in jeder Codepage in jeder Sprache verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="06573-172">Setting this console mode flag will allow these attributes to be used in every code page on every language.</span></span></p>
<p><span data-ttu-id="06573-173">Sie ist standardmäßig deaktiviert, um die Kompatibilität mit bekannten Anwendungen zu gewährleisten, die in der Vergangenheit die-Konsole genutzt haben, um diese Flags auf nicht-cjk-Computern zu speichern, um Bits in diesen Feldern für Ihre eigenen Zwecke oder versehentlich zu speichern.</span><span class="sxs-lookup"><span data-stu-id="06573-173">It is off by default to maintain compatibility with known applications that have historically taken advantage of the console ignoring these flags on non-CJK machines to store bits in these fields for their own purposes or by accident.</span></span></p>
<p><span data-ttu-id="06573-174">Beachten Sie, dass das Verwenden des ENABLE_VIRTUAL_TERMINAL_PROCESSING Modus dazu führen kann, dass LVB-Raster-und Reverse-videoflags festgelegt werden, während dieses Flag immer noch deaktiviert ist, wenn die angefügte Anwendung ein-oder-umgekehrtes Video über <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">virtuelle Konsolen</a></span><span class="sxs-lookup"><span data-stu-id="06573-174">Note that using the ENABLE_VIRTUAL_TERMINAL_PROCESSING mode can result in LVB grid and reverse video flags being set while this flag is still off if the attached application requests underlining or inverse video via <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a>.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="06573-175">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="06573-175">Return value</span></span>
------------

<span data-ttu-id="06573-176">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="06573-176">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="06573-177">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="06573-177">If the function fails, the return value is zero.</span></span> <span data-ttu-id="06573-178">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="06573-178">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="06573-179">Hinweise</span><span class="sxs-lookup"><span data-stu-id="06573-179">Remarks</span></span>
-------

<span data-ttu-id="06573-180">Eine-Konsole besteht aus einem Eingabepuffer und mindestens einem Bildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="06573-180">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="06573-181">Der Modus eines Konsolen Puffers bestimmt, wie sich die Konsole bei Eingabe-oder Ausgabe Vorgängen verhält.</span><span class="sxs-lookup"><span data-stu-id="06573-181">The mode of a console buffer determines how the console behaves during input or output (I/O) operations.</span></span> <span data-ttu-id="06573-182">Ein Satz von flagkonstanten wird mit Eingabe Handles verwendet, und ein anderer Satz wird mit Bildschirm Puffer (Ausgabe) Handles verwendet.</span><span class="sxs-lookup"><span data-stu-id="06573-182">One set of flag constants is used with input handles, and another set is used with screen buffer (output) handles.</span></span> <span data-ttu-id="06573-183">Das Festlegen der Ausgabe Modi eines Bildschirm Puffers wirkt sich nicht auf die Ausgabe Modi anderer Bildschirm Puffer aus.</span><span class="sxs-lookup"><span data-stu-id="06573-183">Setting the output modes of one screen buffer does not affect the output modes of other screen buffers.</span></span>

<span data-ttu-id="06573-184">Das **aktivieren \_ von Zeilen \_ Eingaben** und **Aktivieren von \_ Echo \_ Eingabe** Modi wirkt sich nur auf Prozesse aus, bei denen die [**Datei**](https://msdn.microsoft.com/library/windows/desktop/aa365467) oder die Schreib [**Konsole**](readconsole.md) zum Lesen aus dem Eingabepuffer der Konsole verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="06573-184">The **ENABLE\_LINE\_INPUT** and **ENABLE\_ECHO\_INPUT** modes only affect processes that use [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) to read from the console's input buffer.</span></span> <span data-ttu-id="06573-185">Ebenso wirkt sich der **aktivierten \_ \_ Eingabe** Modus in erster Linie auf die Benutzer " **Infofile** " und " **infoconsole** " aus, mit der Ausnahme, dass Sie auch bestimmt, ob die STRG + C-Eingabe im Eingabepuffer (von der Funktion "read [**ConsoleInput**](readconsoleinput.md) ") gemeldet wird oder an eine von der Anwendung definierte Funktion weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="06573-185">Similarly, the **ENABLE\_PROCESSED\_INPUT** mode primarily affects **ReadFile** and **ReadConsole** users, except that it also determines whether CTRL+C input is reported in the input buffer (to be read by the [**ReadConsoleInput**](readconsoleinput.md) function) or is passed to a function defined by the application.</span></span>

<span data-ttu-id="06573-186">Die **Modi \_ Fenster \_ Eingabe aktivieren** und \*\* \_ Maus \_ Eingabe aktivieren\*\* legen fest, ob Benutzerinteraktionen mit Fenstergröße und Mausaktionen im Eingabepuffer gemeldet oder verworfen werden.</span><span class="sxs-lookup"><span data-stu-id="06573-186">The **ENABLE\_WINDOW\_INPUT** and **ENABLE\_MOUSE\_INPUT** modes determine whether user interactions involving window resizing and mouse actions are reported in the input buffer or discarded.</span></span> <span data-ttu-id="06573-187">Diese Ereignisse können von " [**infoconsoleinput**](readconsoleinput.md)" gelesen werden, Sie werden jedoch immer nach " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**infoconsole**](readconsole.md)" gefiltert.</span><span class="sxs-lookup"><span data-stu-id="06573-187">These events can be read by [**ReadConsoleInput**](readconsoleinput.md), but they are always filtered by [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md).</span></span>

<span data-ttu-id="06573-188">Die Ausgabe Modi " \*\* \_ verarbeitete \_ Ausgabe aktivieren\*\* " und " \*\* \_ Wrap \_ in \_ EOL \_ aktivieren\*\* " wirken sich nur auf die Prozesse aus, die "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](readconsole.md) " und [**"Write-**](writeconsole.md) [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) "</span><span class="sxs-lookup"><span data-stu-id="06573-188">The **ENABLE\_PROCESSED\_OUTPUT** and **ENABLE\_WRAP\_AT\_EOL\_OUTPUT** modes only affect processes using [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md).</span></span>

<span data-ttu-id="06573-189">Um die e/a-Modi einer Konsole zu ändern, müssen Sie die Funktion [**setconsolemode**](setconsolemode.md) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="06573-189">To change a console's I/O modes, call [**SetConsoleMode**](setconsolemode.md) function.</span></span>

<a name="examples"></a><span data-ttu-id="06573-190">Beispiele</span><span class="sxs-lookup"><span data-stu-id="06573-190">Examples</span></span>
--------

<span data-ttu-id="06573-191">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="06573-191">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="06573-192">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="06573-192">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="06573-193">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="06573-193">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="06573-194">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="06573-194">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="06573-195">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="06573-195">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="06573-196">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="06573-196">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="06573-197">Header</span><span class="sxs-lookup"><span data-stu-id="06573-197">Header</span></span></p></td>
<td><span data-ttu-id="06573-198">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="06573-198">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="06573-199">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="06573-199">Library</span></span></p></td>
<td><span data-ttu-id="06573-200">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="06573-200">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="06573-201">DLL</span><span class="sxs-lookup"><span data-stu-id="06573-201">DLL</span></span></p></td>
<td><span data-ttu-id="06573-202">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="06573-202">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="06573-203"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="06573-203"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="06573-204">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="06573-204">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="06573-205">Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="06573-205">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="06573-206">**"Read Console"**</span><span class="sxs-lookup"><span data-stu-id="06573-206">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="06573-207">**Read ConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="06573-207">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="06573-208">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="06573-208">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="06573-209">**Setconsolemode**</span><span class="sxs-lookup"><span data-stu-id="06573-209">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="06573-210">**Schreib Konsole**</span><span class="sxs-lookup"><span data-stu-id="06573-210">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="06573-211">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="06573-211">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




