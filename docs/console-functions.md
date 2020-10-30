---
title: Konsolenfunktionen
description: Beschreibt eine vollständige Liste aller Funktionen, die für den Zugriff auf eine-Konsole verwendet werden.
author: miniksa
ms.author: miniksa
ms.topic: hub-page
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_functions'
- base.console\_functions
- consoles.console\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2a0e5dcc-be48-42ab-a05a-96f68d012a67
ms.openlocfilehash: 0ee2dde2c14a3d827aa2bc5e14f3cc65cf5fdc0f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039238"
---
# <a name="console-functions"></a>Konsolenfunktionen

Die folgenden Funktionen werden verwendet, um auf eine Konsole zuzugreifen.

| Funktion | BESCHREIBUNG |
|-|-|
| [**AddConsoleAlias**](addconsolealias.md) | Definiert einen konsolenalias für die angegebene ausführbare Datei. |
| [**AllocConsole**](allocconsole.md) | Weist eine neue Konsole für den aufrufenden Prozess zu. |
| [**AttachConsole**](attachconsole.md) | Fügt den aufrufenden Prozess an die Konsole des angegebenen Prozesses an. |
| [**ClosePseudoConsole**](closepseudoconsole.md) | Schließt eine pseudoconsole aus dem angegebenen Handle. |
| [**CreatePseudoConsole**](createpseudoconsole.md) | Weist eine neue Pseudo Konsole für den aufrufenden Prozess zu. |
| [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) | Erstellt einen Konsolenbildschirm Puffer. |
| [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) | Legt die Attribute für Text und Hintergrundfarbe für eine angegebene Anzahl von Zeichen Zellen fest. |
| [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) | Schreibt ein Zeichen so oft wie angegeben in den Konsolenbildschirm Puffer. |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) | Leert den Konsolen Eingabepuffer. |
| [**FreeConsole**](freeconsole.md) | Trennt den aufrufenden Prozess von seiner Konsole aus. |
| [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) | Sendet ein angegebenes Signal an eine Konsolen Prozessgruppe, die die dem aufrufenden Prozess zugeordnete Konsole freigibt. |
| [**GetConsoleAlias**](getconsolealias.md) | Ruft den angegebenen Alias für die angegebene ausführbare Datei ab. |
| [**GetConsoleAliases**](getconsolealiases.md) | Ruft alle definierten Konsolen Aliase für die angegebene ausführbare Datei ab. |
| [**Getconsolealiaseslength**](getconsolealiaseslength.md) | Gibt die Größe (in Bytes) des Puffers zurück, der zum Speichern aller Konsolen Aliase für die angegebene ausführbare Datei erforderlich ist. |
| [**GetConsoleAliasExes**](getconsolealiasexes.md) | Ruft die Namen aller ausführbaren Dateien mit definierten Konsolen Aliasen ab. |
| [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) | Gibt die Größe (in Bytes) des Puffers zurück, der zum Speichern der Namen aller ausführbaren Dateien benötigt wird, für die Konsolen Aliase definiert sind. |
| [**GetConsoleCP**](getconsolecp.md) | Ruft die Eingabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist. |
| [**GetConsoleCursorInfo**](getconsolecursorinfo.md) | Ruft Informationen über die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer ab. |
| [**GetConsoleDisplayMode**](getconsoledisplaymode.md) | Ruft den Anzeigemodus der aktuellen Konsole ab. |
| [**GetConsoleFontSize**](getconsolefontsize.md) | Ruft die Größe der Schriftart ab, die vom angegebenen Konsolenbildschirm Puffer verwendet wird. |
| [**GetConsoleHistoryInfo**](getconsolehistoryinfo.md) | Ruft die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses ab. |
| [**GetConsoleMode**](getconsolemode.md) | Ruft den aktuellen Eingabemodus für den Eingabepuffer einer Konsole oder den aktuellen Ausgabemodus eines Konsolenbildschirm Puffers ab. |
| [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) | Ruft den ursprünglichen Titel für das aktuelle Konsolenfenster ab. |
| [**GetConsoleOutputCP**](getconsoleoutputcp.md) | Ruft die Ausgabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist. |
| [**GetConsoleProcessList**](getconsoleprocesslist.md) | Ruft eine Liste der Prozesse ab, die an die aktuelle Konsole angefügt sind. |
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Ruft Informationen zum angegebenen Konsolenbildschirm Puffer ab. |
| [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) | Ruft erweiterte Informationen zum angegebenen Bildschirm Puffer der Konsole ab. |
| [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) | Ruft Informationen über die aktuelle Konsolen Auswahl ab. |
| [**GetConsoleTitle**](getconsoletitle.md) | Ruft den Titel für das aktuelle Konsolenfenster ab. |
| [**GetConsoleWindow**](getconsolewindow.md) | Ruft das Fenster Handle ab, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist. |
| [**GetCurrentConsoleFont**](getcurrentconsolefont.md) | Ruft Informationen über die aktuelle Konsolen Schriftart ab. |
| [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) | Ruft erweiterte Informationen über die aktuelle Konsolen Schriftart ab. |
| [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) | Ruft die Größe des größtmöglichen Konsolenfensters ab. |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) | Ruft die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole ab. |
| [**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md) | Ruft die Anzahl der Schaltflächen auf der Maus ab, die von der aktuellen Konsole verwendet werden. |
| [**GetStdHandle**](getstdhandle.md) | Ruft ein Handle für die Standardeingabe, Standardausgabe oder das Standardfehler Gerät ab. |
| [**HandlerRoutine**](handlerroutine.md) | Eine Anwendungs definierte Funktion, die mit der [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion verwendet wird. |
| [**PeekConsoleInput**](peekconsoleinput.md) | Liest Daten aus dem angegebenen Konsolen Eingabepuffer, ohne Sie aus dem Puffer zu entfernen. |
| [**ReadConsole**](readconsole.md) | Liest Zeichen Eingaben aus dem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer. |
| [**ReadConsoleInput**](readconsoleinput.md) | Liest Daten aus einem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer. |
| [**ReadConsoleOutput**](readconsoleoutput.md) | Liest Zeichen-und Farb Attributdaten aus einem rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer. |
| [**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md) | Kopiert eine angegebene Anzahl von Vordergrund-und Hintergrundfarben Attributen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers. |
| [**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md) | Kopiert eine Anzahl von Zeichen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers. |
| [**ResizePseudoConsole**](resizepseudoconsole.md) | Ändert die Größe der internen Puffer für eine pseudoconsole auf die angegebene Größe. |
| [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) | Verschiebt einen Datenblock in einem Bildschirm Puffer. |
| [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) | Legt den angegebenen Bildschirm Puffer auf den aktuell angezeigten Konsolenbildschirm Puffer fest. |
| [**SetConsoleCP**](setconsolecp.md) | Legt die Eingabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist. |
| [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) | Fügt eine von der Anwendung definierte Handlerroutine aus der Liste der [**Handlerfunktionen**](handlerroutine.md) für den aufrufenden Prozess hinzu oder entfernt Sie. |
| [**SetConsoleCursorInfo**](setconsolecursorinfo.md) | Legt die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer fest. |
| [**SetConsoleCursorPosition**](setconsolecursorposition.md) | Legt die Cursorposition im angegebenen Konsolenbildschirm Puffer fest. |
| [**SetConsoleDisplayMode**](setconsoledisplaymode.md) | Legt den Anzeigemodus des angegebenen Konsolenbildschirm Puffers fest. |
| [**SetConsoleHistoryInfo**](setconsolehistoryinfo.md) | Legt die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses fest. |
| [**SetConsoleMode**](setconsolemode.md) | Legt den Eingabemodus für den Eingabepuffer einer Konsole oder den Ausgabemodus eines Konsolenbildschirm Puffers fest. |
| [**SetConsoleOutputCP**](setconsoleoutputcp.md) | Legt die Ausgabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist. |
| [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) | Legt erweiterte Informationen zum angegebenen Konsolenbildschirm Puffer fest. |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Ändert die Größe des angegebenen Konsolenbildschirm Puffers. |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | Legt die Attribute für Vordergrund (Text) und die Hintergrundfarbe von Zeichen fest, die in den Konsolenbildschirm Puffer geschrieben werden. |
| [**SetConsoleTitle**](setconsoletitle.md) | Legt den Titel für das aktuelle Konsolenfenster fest. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md) | Legt die aktuelle Größe und Position des Fensters eines Konsolenbildschirm Puffers fest. |
| [**SetCurrentConsoleFontEx**](setcurrentconsolefontex.md) | Legt erweiterte Informationen über die aktuelle Konsolen Schriftart fest. |
| [**SetStdHandle**](setstdhandle.md) | Legt das Handle für die Standardeingabe, Standardausgabe oder das Standard fehlergerät fest. |
| [**WriteConsole**](writeconsole.md) | Schreibt eine Zeichenfolge in einen Konsolenbildschirm Puffer, beginnend an der aktuellen Cursorposition. |
| [**WriteConsoleInput**](writeconsoleinput.md) | Schreibt Daten direkt in den Konsolen Eingabepuffer. |
| [**WriteConsoleOutput**](writeconsoleoutput.md) | Schreibt Zeichen-und Farb Attributdaten in einen angegebenen rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer. |
| [**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md) | Kopiert eine Anzahl von Attributen für Vordergrund-und Hintergrundfarben in aufeinander folgende Zellen eines Konsolenbildschirm Puffers. |
| [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) | Kopiert eine Anzahl von Zeichen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers. |
