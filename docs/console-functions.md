---
title: Konsolenfunktionen
description: Beschreibt eine vollständige Liste aller Funktionen, die für den Zugriff auf eine-Konsole verwendet werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_functions'
- base.console\_functions
- consoles.console\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2a0e5dcc-be48-42ab-a05a-96f68d012a67
ms.openlocfilehash: 5b7d5e0c050f30b0f834322617b9631c24f620f8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060450"
---
# <a name="console-functions"></a>Konsolenfunktionen


Die folgenden Funktionen werden verwendet, um auf eine Konsole zuzugreifen.


|                                Funktion                                 |                                                                Beschreibung                                                                 |
|-------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
|                [**Addconsolealias**](addconsolealias.md)                |                                           Definiert einen konsolenalias für die angegebene ausführbare Datei.                                            |
|                   [**"Zuweisung"-Konsole**](allocconsole.md)                   |                                              Weist eine neue Konsole für den aufrufenden Prozess zu.                                              |
|                  [**Attachconsole**](attachconsole.md)                  |                                   Fügt den aufrufenden Prozess an die Konsole des angegebenen Prozesses an.                                    |
|      [**Closepseudoconsole**](closepseudoconsole.md)      |                                                      Schließt eine pseudoconsole aus dem angegebenen Handle.                                                     |
|      [**"Kreatepseudoconsole"**](createpseudoconsole.md)      |                                                      Weist eine neue Pseudo Konsole für den aufrufenden Prozess zu.                                                      |
|      [**"Kreateconsoleskreenbuffer"**](createconsolescreenbuffer.md)      |                                                      Erstellt einen Konsolenbildschirm Puffer.                                                      |
|     [**Fillconsoleoutputattribute**](fillconsoleoutputattribute.md)     |                          Legt die Attribute für Text und Hintergrundfarbe für eine angegebene Anzahl von Zeichen Zellen fest.                          |
|     [**Fillconsoleoutputcharacter**](fillconsoleoutputcharacter.md)     |                                Schreibt ein Zeichen so oft wie angegeben in den Konsolenbildschirm Puffer.                                |
|        [**Flushconsolinput Buffer**](flushconsoleinputbuffer.md)        |                                                     Leert den Konsolen Eingabepuffer.                                                      |
|                    [**Freeconsole**](freeconsole.md)                    |                                               Trennt den aufrufenden Prozess von seiner Konsole aus.                                               |
|       [**Generateconsolectrlevent**](generateconsolectrlevent.md)       |              Sendet ein angegebenes Signal an eine Konsolen Prozessgruppe, die die dem aufrufenden Prozess zugeordnete Konsole freigibt.              |
|                [**Getconsolealias**](getconsolealias.md)                |                                        Ruft den angegebenen Alias für die angegebene ausführbare Datei ab.                                         |
|              [**Getconsolealiases**](getconsolealiases.md)              |                                    Ruft alle definierten Konsolen Aliase für die angegebene ausführbare Datei ab.                                     |
|        [**Getconsolealiaseslength**](getconsolealiaseslength.md)        |             Gibt die Größe (in Bytes) des Puffers zurück, der zum Speichern aller Konsolen Aliase für die angegebene ausführbare Datei erforderlich ist.             |
|            [**Getconsolealiasexes**](getconsolealiasexes.md)            |                                    Ruft die Namen aller ausführbaren Dateien mit definierten Konsolen Aliasen ab.                                    |
|      [**Getconsolealiasexeslength**](getconsolealiasexeslength.md)      |         Gibt die Größe (in Bytes) des Puffers zurück, der zum Speichern der Namen aller ausführbaren Dateien benötigt wird, für die Konsolen Aliase definiert sind.          |
|                   [**Getconsolecp**](getconsolecp.md)                   |                           Ruft die Eingabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.                           |
|           [**Getconsolecursorinfo**](getconsolecursorinfo.md)           |                 Ruft Informationen über die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer ab.                 |
|          [**Getconsoledisplaymode**](getconsoledisplaymode.md)          |                                             Ruft den Anzeigemodus der aktuellen Konsole ab.                                             |
|             [**Getconsolefontsize**](getconsolefontsize.md)             |                                Ruft die Größe der Schriftart ab, die vom angegebenen Konsolenbildschirm Puffer verwendet wird.                                 |
|          [**Getconsolehistoryinfo**](getconsolehistoryinfo.md)          |                                     Ruft die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses ab.                                      |
|                 [**Getconsolemode**](getconsolemode.md)                 |            Ruft den aktuellen Eingabemodus für den Eingabepuffer einer Konsole oder den aktuellen Ausgabemodus eines Konsolenbildschirm Puffers ab.             |
|        [**Getconsoleoriginaltitle**](getconsoleoriginaltitle.md)        |                                        Ruft den ursprünglichen Titel für das aktuelle Konsolenfenster ab.                                        |
|             [**Getconsoleoutputcp**](getconsoleoutputcp.md)             |                          Ruft die Ausgabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.                           |
|          [**Getconsoleprocesslist**](getconsoleprocesslist.md)          |                                     Ruft eine Liste der Prozesse ab, die an die aktuelle Konsole angefügt sind.                                     |
|     [**Getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md)     |                                      Ruft Informationen zum angegebenen Konsolenbildschirm Puffer ab.                                      |
|   [**Getconsoleskreenbufferinfoex**](getconsolescreenbufferinfoex.md)   |                                 Ruft erweiterte Informationen zum angegebenen Bildschirm Puffer der Konsole ab.                                  |
|        [**Getconsoleselectioninfo**](getconsoleselectioninfo.md)        |                                         Ruft Informationen über die aktuelle Konsolen Auswahl ab.                                         |
|                [**Getconsoletitle**](getconsoletitle.md)                |                                            Ruft den Titel für das aktuelle Konsolenfenster ab.                                             |
|               [**GetConsoleWindow**](getconsolewindow.md)               |                            Ruft das Fenster Handle ab, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.                            |
|          [**Getcurrentconsolefont**](getcurrentconsolefont.md)          |                                           Ruft Informationen über die aktuelle Konsolen Schriftart ab.                                            |
|        [**Getcurrentconsolefontex**](getcurrentconsolefontex.md)        |                                       Ruft erweiterte Informationen über die aktuelle Konsolen Schriftart ab.                                       |
|    [**Getlargestconsolewindowsize**](getlargestconsolewindowsize.md)    |                                         Ruft die Größe des größtmöglichen Konsolenfensters ab.                                         |
|  [**Getnumofconsoleinputevents**](getnumberofconsoleinputevents.md)  |                                Ruft die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole ab.                                 |
| [**Getnumofansolemouanschaltflächen**](getnumberofconsolemousebuttons.md) |                                 Ruft die Anzahl der Schaltflächen auf der Maus ab, die von der aktuellen Konsole verwendet werden.                                  |
|                   [**Getstdhandle**](getstdhandle.md)                   |                           Ruft ein Handle für die Standardeingabe, Standardausgabe oder das Standardfehler Gerät ab.                            |
|                 [**Handlerroutine**](handlerroutine.md)                 |               Eine Anwendungs definierte Funktion, die mit der [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion verwendet wird.                |
|               [**"Etekconsoleinput"**](peekconsoleinput.md)               |                          Liest Daten aus dem angegebenen Konsolen Eingabepuffer, ohne Sie aus dem Puffer zu entfernen.                           |
|                    [**"Read Console"**](readconsole.md)                    |                            Liest Zeichen Eingaben aus dem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.                             |
|               [**Read ConsoleInput**](readconsoleinput.md)               |                                   Liest Daten aus einem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.                                   |
|              [**"Read consoleoutput"**](readconsoleoutput.md)              |              Liest Zeichen-und Farb Attributdaten aus einem rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer.              |
|     [**"Read consoleoutputattribute"**](readconsoleoutputattribute.md)     |         Kopiert eine angegebene Anzahl von Vordergrund-und Hintergrundfarben Attributen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers.         |
|     [**"Read consoleoutputcharacter"**](readconsoleoutputcharacter.md)     |                              Kopiert eine Anzahl von Zeichen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers.                              |
|      [**Resizepseudoconsole**](resizepseudoconsole.md)      |                                                      Ändert die Größe der internen Puffer für eine pseudoconsole auf die angegebene Größe.                                                     |
|      [**Scrollconsoleskreenbuffer**](scrollconsolescreenbuffer.md)      |                                                 Verschiebt einen Datenblock in einem Bildschirm Puffer.                                                  |
|   [**Setconsoleactiveskreenbuffer**](setconsoleactivescreenbuffer.md)   |                           Legt den angegebenen Bildschirm Puffer auf den aktuell angezeigten Konsolenbildschirm Puffer fest.                            |
|                   [**Setconsolecp**](setconsolecp.md)                   |                             Legt die Eingabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.                              |
|          [**SetConsoleCtrlHandler**](setconsolectrlhandler.md)          | Fügt eine von der Anwendung definierte Handlerroutine aus der Liste der [**Handlerfunktionen**](handlerroutine.md) für den aufrufenden Prozess hinzu oder entfernt Sie. |
|           [**Setconsolecursorinfo**](setconsolecursorinfo.md)           |                            Legt die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer fest.                             |
|       [**SetConsoleCursorPosition**](setconsolecursorposition.md)       |                                      Legt die Cursorposition im angegebenen Konsolenbildschirm Puffer fest.                                      |
|          [**Setconsoledisplaymode**](setconsoledisplaymode.md)          |                                       Legt den Anzeigemodus des angegebenen Konsolenbildschirm Puffers fest.                                        |
|          [**Setconsolehistoryinfo**](setconsolehistoryinfo.md)          |                                        Legt die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses fest.                                        |
|                 [**Setconsolemode**](setconsolemode.md)                 |                       Legt den Eingabemodus für den Eingabepuffer einer Konsole oder den Ausgabemodus eines Konsolenbildschirm Puffers fest.                       |
|             [**Setconsoleoutputcp**](setconsoleoutputcp.md)             |                             Legt die Ausgabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.                             |
|   [**Setconsoleskreenbufferinfoex**](setconsolescreenbufferinfoex.md)   |                                    Legt erweiterte Informationen zum angegebenen Konsolenbildschirm Puffer fest.                                    |
|     [**Setconsoleskreenbuffersize**](setconsolescreenbuffersize.md)     |                                          Ändert die Größe des angegebenen Konsolenbildschirm Puffers.                                          |
|        [**SetConsoleTextAttribute**](setconsoletextattribute.md)        |               Legt die Attribute für Vordergrund (Text) und die Hintergrundfarbe von Zeichen fest, die in den Konsolenbildschirm Puffer geschrieben werden.               |
|                [**Setconsoletitle**](setconsoletitle.md)                |                                               Legt den Titel für das aktuelle Konsolenfenster fest.                                               |
|           [**Setconsolewindowinfo**](setconsolewindowinfo.md)           |                                  Legt die aktuelle Größe und Position des Fensters eines Konsolenbildschirm Puffers fest.                                   |
|        [**Setcurrentconsolefontex**](setcurrentconsolefontex.md)        |                                         Legt erweiterte Informationen über die aktuelle Konsolen Schriftart fest.                                          |
|                   [**Setstdhandle**](setstdhandle.md)                   |                             Legt das Handle für die Standardeingabe, Standardausgabe oder das Standard fehlergerät fest.                             |
|                   [**Schreib Konsole**](writeconsole.md)                   |                       Schreibt eine Zeichenfolge in einen Konsolenbildschirm Puffer, beginnend an der aktuellen Cursorposition.                       |
|              [**Schreibconsoleinput**](writeconsoleinput.md)              |                                             Schreibt Daten direkt in den Konsolen Eingabepuffer.                                              |
|             [**Schreibconsoleoutput**](writeconsoleoutput.md)             |         Schreibt Zeichen-und Farb Attributdaten in einen angegebenen rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer.          |
|    [**"Schreibconsoleoutputattribute"**](writeconsoleoutputattribute.md)    |               Kopiert eine Anzahl von Attributen für Vordergrund-und Hintergrundfarben in aufeinander folgende Zellen eines Konsolenbildschirm Puffers.               |
|    [**Schreibconsoleoutputcharacter**](writeconsoleoutputcharacter.md)    |                               Kopiert eine Anzahl von Zeichen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers.                               |

