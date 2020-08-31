---
title: Setconsolemode-Funktion
description: Legt den Eingabemodus für den Eingabepuffer einer Konsole oder den Ausgabemodus eines Konsolenbildschirm Puffers fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a524a9f730d53efd331a70693aadfeddeaad4cc0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060515"
---
# <a name="setconsolemode-function"></a>Setconsolemode-Funktion


Legt den Eingabemodus für den Eingabepuffer einer Konsole oder den Ausgabemodus eines Konsolenbildschirm Puffers fest.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

<a name="parameters"></a>Parameter
----------

*hconsolehandle* \[ in\]  
Ein Handle des Konsolen Eingabe Puffers oder eines Konsolenbildschirm Puffers. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*dwmode* \[ in\]  
Der Eingabe-oder Ausgabemodus, der festgelegt werden soll. Wenn der *hconsolehandle* -Parameter ein Eingabe Handle ist, kann der Modus einen oder mehrere der folgenden Werte aufweisen. Wenn eine-Konsole erstellt wird, sind alle Eingabemodi mit Ausnahme von ** \_ Fenster \_ Eingabe aktivieren** standardmäßig aktiviert.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</td>
<td><p>Zeichen, die von der Funktion "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder "read <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>Console</strong></a> " gelesen werden, werden beim Lesen in den aktiven Bildschirm Puffer geschrieben. Dieser Modus kann nur verwendet werden, wenn der <strong>ENABLE_LINE_INPUT</strong> Modus ebenfalls aktiviert ist.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_EXTENDED_FLAGS"></span><span id="enable_extended_flags"></span>
<strong>ENABLE_EXTENDED_FLAGS</strong> 0x0080</td>
<td><p>Erforderlich, um erweiterte Flags zu aktivieren oder zu deaktivieren. Siehe <strong>ENABLE_INSERT_MODE</strong> und <strong>ENABLE_QUICK_EDIT_MODE</strong>.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</td>
<td><p>Wenn diese Option aktiviert ist, wird der in einem Konsolenfenster eingegebene Text an der aktuellen Cursorposition eingefügt, und der gesamte Text, der diesem Speicherort folgt, wird nicht überschrieben. Wenn diese Option deaktiviert ist, wird der gesamte folgende Text überschrieben.</p>
<p>Verwenden Sie, um diesen Modus zu aktivieren <code>ENABLE_INSERT_MODE | ENABLE_EXTENDED_FLAGS</code> . Verwenden Sie <strong>ENABLE_EXTENDED_FLAGS</strong> ohne dieses Flag, um diesen Modus zu deaktivieren.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</td>
<td><p>Die Funktion "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder "read <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>Console</strong></a> " gibt nur zurück, wenn ein Wagen Rücklauf Zeichen gelesen wird. Wenn dieser Modus deaktiviert ist, geben die Funktionen zurück, wenn ein oder mehrere Zeichen verfügbar sind.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</td>
<td><p>Wenn sich der Mauszeiger innerhalb der Rahmen des Konsolenfensters befindet und das Fenster den Tastaturfokus besitzt, werden Mausereignisse, die durch Mausbewegung und Schaltflächen drückt werden, im Eingabepuffer platziert. Diese Ereignisse werden von "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder " <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>infoconsole</strong></a>" verworfen, auch wenn dieser Modus aktiviert ist.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</td>
<td><p>STRG + C wird vom System verarbeitet und nicht im Eingabepuffer platziert. Wenn der Eingabepuffer von " <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>Infofile</strong></a> " oder " <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>infoconsole</strong></a>" gelesen wird, werden andere Steuerungs Schlüssel vom System verarbeitet und nicht im <strong>lesefile</strong> -oder <strong>leseconsole</strong> -Puffer zurückgegeben. Wenn der <strong>ENABLE_LINE_INPUT</strong> Modus ebenfalls aktiviert ist, werden Rücktaste, Wagen Rücklauf und Zeilenvorschub Zeichen vom System behandelt.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</td>
<td><p>Dieses Flag ermöglicht dem Benutzer die Verwendung der Maus, um Text auszuwählen und zu bearbeiten.</p>
<p>Verwenden Sie, um diesen Modus zu aktivieren <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code> . Verwenden Sie <strong>ENABLE_EXTENDED_FLAGS</strong> ohne dieses Flag, um diesen Modus zu deaktivieren.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</td>
<td><p>Benutzerinteraktionen, die die Größe des Konsolenbildschirm Puffers ändern, werden im Eingabepuffer der Konsole&#39;s angezeigt. Informationen zu diesen Ereignissen können von Anwendungen, die die Funktion " <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>leseconsoleinput</strong></a> " verwenden, aus dem Eingabepuffer gelesen werden, aber nicht von denjenigen, die "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder " <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>infoconsole</strong></a>" verwenden.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</td>
<td><p>Das Festlegen dieses Flags bewirkt, dass die Engine für die virtuelle terminalverarbeitungs-Engine Benutzereingaben, die vom Konsolenfenster empfangen werden, in Konsolen-virtuelle Terminal Sequenzen konvertieren, die durch eine unterstützende Anwendung über die Funktionen "Infofile" oder "Read</p>
<p>Die typische Verwendung dieses Flags ist in Verbindung mit ENABLE_VIRTUAL_TERMINAL_PROCESSING des Ausgabe Handles zum Herstellen einer Verbindung mit einer Anwendung vorgesehen, die ausschließlich über virtuelle Terminal Sequenzen kommuniziert.</p></td>
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
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

Wenn der *hconsolehandle* -Parameter ein Bildschirm Puffer Handle ist, kann der Modus einen oder mehrere der folgenden Werte aufweisen. Beim Erstellen eines Bildschirm Puffers sind beide Ausgabe Modi standardmäßig aktiviert.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</td>
<td><p>Zeichen, die von der Funktion " <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>Write File</strong></a> " oder " <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>Write-Console</strong></a> " geschrieben oder von der Funktion "read <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>File</strong></a> " oder "read <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>Console</strong></a> " zurückgegeben werden, werden auf ASCII-Steuersequenzen überprüft, und die richtige Aktion Rücktaste, Tabulator, Glocken Zeichen, Wagen Rücklauf und Zeilenvorschub Zeichen werden verarbeitet.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</td>
<td><p>Beim Schreiben mit " <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> " oder " <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>writeconsole</strong></a> " oder "Echo" mit " <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>Infofile</strong></a> " oder " <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>infoconsole</strong></a>" wechselt der Cursor zum Anfang der nächsten Zeile, wenn er das Ende der aktuellen Zeile erreicht. Dies bewirkt, dass die im Konsolenfenster angezeigten Zeilen automatisch nach oben scrollen, wenn der Cursor die letzte Zeile im Fenster überschreitet. Außerdem bewirkt dies, dass der Inhalt des Konsolenbildschirm Puffers nach oben bewegt wird (wobei die obere Zeile des Konsolenbildschirm Puffers verworfen wird), wenn der Cursor die letzte Zeile des Konsolenbildschirm Puffers überschreitet. Wenn dieser Modus deaktiviert ist, wird das letzte Zeichen in der Zeile mit allen nachfolgenden Zeichen überschrieben.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</td>
<td><p>Beim Schreiben mit <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> oder <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>writeconsole</strong></a>werden Zeichen für VT100 und ähnliche Steuerzeichen Sequenzen analysiert, die die Cursor Bewegung, den Farb-/schriftmodus und andere Vorgänge steuern, die auch über die vorhandenen Konsolen-APIs ausgeführt werden können. Weitere Informationen finden Sie unter <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Konsolen virtuelle Terminal Sequenzen</a>.</p></td>
</tr>
<tr class="even">
<td><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</td>
<td><p>Wenn Sie mit <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> oder <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>writeconsole</strong></a>schreiben, fügt dies einen zusätzlichen Zustand zum Zeilen umschließen hinzu, der den Cursor Verschiebe-und Puffer scrollvorgang verzögern kann.</p>
<p>Wenn ENABLE_WRAP_AT_EOL_OUTPUT festgelegt ist und Text das Ende der Zeile erreicht, wird der Cursor normalerweise in die nächste Zeile verschoben, und der Inhalt des Puffers wird um eine Zeile nach oben verschoben. Im Gegensatz zu diesem Flag wird der scrollvorgang und die Cursor Verschiebung verzögert, bis das nächste Zeichen eintrifft. Das geschriebene Zeichen wird an der endgültigen Position in der Zeile gedruckt, und der Cursor bleibt über diesem Zeichen, als wäre ENABLE_WRAP_AT_EOL_OUTPUT deaktiviert, aber das nächste Druck bare Zeichen wird gedruckt, als ob ENABLE_WRAP_AT_EOL_OUTPUT on ist. Es erfolgt kein überschreiben. Insbesondere wechselt der Cursor schnell zur folgenden Zeile, ein Bildlauf wird bei Bedarf ausgeführt, das Zeichen wird gedruckt, und der Cursor verschiebt eine weitere Position.</p>
<p>Die typische Verwendung dieses Flags ist in Verbindung mit der Festlegung ENABLE_VIRTUAL_TERMINAL_PROCESSING vorgesehen, um einen Terminal Emulator besser zu emulieren, bei dem das abschließende Zeichen auf dem Bildschirm (in der unteren rechten Ecke) geschrieben wird, ohne dass ein sofortiger scrollvorgang ausgelöst wird.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</td>
<td><p>Die APIs zum Schreiben von Zeichen Attributen einschließlich <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>writeconsoleoutput</strong></a> und <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>writeconsoleoutputattribute</strong></a> ermöglichen die Verwendung von Flags aus <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">Zeichen Attributen</a> , um die Farbe des Vordergrunds und des Hintergrunds von Text anzupassen. Außerdem wurde ein Bereich von DBCS-Flags mit dem COMMON_LVB-Präfix angegeben. In der Vergangenheit wurden diese Flags nur in DBCS-Codepages für Chinesisch, Japanisch und Koreanisch unterbunden.</p>
<p>Mit Ausnahme der führenden Byte-und nachfolgenden byteflags können die restlichen Flags, die das Zeichnen von Zeilen und das umgekehrte Video beschreiben (austauschen von Vordergrund-und Hintergrundfarben), nützlich sein, damit andere Sprachen Teile der Ausgabe hervorheben können.</p>
<p>Durch Festlegen dieses Konsolenmodus-Flags können diese Attribute in jeder Codepage in jeder Sprache verwendet werden.</p>
<p>Sie ist standardmäßig deaktiviert, um die Kompatibilität mit bekannten Anwendungen zu gewährleisten, die in der Vergangenheit die-Konsole genutzt haben, um diese Flags auf nicht-cjk-Computern zu speichern, um Bits in diesen Feldern für Ihre eigenen Zwecke oder versehentlich zu speichern.</p>
<p>Beachten Sie, dass das Verwenden des ENABLE_VIRTUAL_TERMINAL_PROCESSING Modus dazu führen kann, dass LVB-Raster-und Reverse-videoflags festgelegt werden, während dieses Flag immer noch deaktiviert ist, wenn die angefügte Anwendung ein-oder-umgekehrtes Video über <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">virtuelle Konsolen</a></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Eine-Konsole besteht aus einem Eingabepuffer und mindestens einem Bildschirm Puffer. Der Modus eines Konsolen Puffers bestimmt, wie sich die Konsole bei Eingabe-und Ausgabe Vorgängen verhält. Ein Satz von flagkonstanten wird mit Eingabe Handles verwendet, und ein anderer Satz wird mit Bildschirm Puffer (Ausgabe) Handles verwendet. Das Festlegen der Ausgabe Modi eines Bildschirm Puffers wirkt sich nicht auf die Ausgabe Modi anderer Bildschirm Puffer aus.

Das **aktivieren \_ von Zeilen \_ Eingaben** und **Aktivieren von \_ Echo \_ Eingabe** Modi wirkt sich nur auf Prozesse aus, bei denen die [**Datei**](https://msdn.microsoft.com/library/windows/desktop/aa365467) oder die Schreib [**Konsole**](readconsole.md) zum Lesen aus dem Eingabepuffer der Konsole verwendet wird. Ebenso wirkt sich der **aktivierten \_ \_ Eingabe** Modus in erster Linie auf die Benutzer " **Infofile** " und " **infoconsole** " aus, mit der Ausnahme, dass Sie auch bestimmt, ob die STRG + C-Eingabe im Eingabepuffer (von der Funktion "read [**ConsoleInput**](readconsoleinput.md) ") gemeldet wird oder an eine von der Anwendung definierte [**Handlerroutine**](handlerroutine.md) -Funktion übergeben wird

Die **Modi \_ Fenster \_ Eingabe aktivieren** und ** \_ Maus \_ Eingabe aktivieren** legen fest, ob Benutzerinteraktionen mit Fenstergröße und Mausaktionen im Eingabepuffer gemeldet oder verworfen werden. Diese Ereignisse können von " [**infoconsoleinput**](readconsoleinput.md)" gelesen werden, Sie werden jedoch immer nach " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**infoconsole**](readconsole.md)" gefiltert.

Die Ausgabe Modi " ** \_ verarbeitete \_ Ausgabe aktivieren** " und " ** \_ Wrap \_ in \_ EOL \_ aktivieren** " wirken sich nur auf die Prozesse aus, die "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](readconsole.md) " und [**"Write-**](writeconsole.md) [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) "

Verwenden Sie die [**getconsolemode**](getconsolemode.md) -Funktion, um den aktuellen Modus eines Konsolen Eingabe Puffers oder Bildschirm Puffers zu bestimmen.

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).

<a name="requirements"></a>Anforderungen
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Unterstützte Mindestversion (Client)</p></td>
<td><p>Windows 2000 Professional [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows 2000 Server [nur Desktop-Apps]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Consoleapi. h (über WinCon. h, Include Windows. h)</td>
</tr>
<tr class="even">
<td><p>Bibliothek</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[Konsolenfunktionen](console-functions.md)

[Konsolen Modi](console-modes.md)

[**Getconsolemode**](getconsolemode.md)

[**Handlerroutine**](handlerroutine.md)

[**"Read Console"**](readconsole.md)

[**Read ConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**Schreib Konsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




