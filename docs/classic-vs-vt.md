---
title: Klassische Konsolen-APIs im Vergleich zu virtuellen Terminalsequenzen
description: Beschreibt den Unterschied zwischen der Oberfläche der klassischen Win32-Konsolen-API und dem Konzept der virtuellen Terminalsequenzen, manchmal auch als Escapesequenzen bezeichnet, zum Schreiben von Befehlszeilenanwendungen.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Terminal, virtuelles Terminal, Escapesequenzen, vt, vt100, Konsolen-API
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: 541300b50521909b22ceaccb595f1945fbfc7e6d
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420179"
---
# <a name="classic-console-apis-versus-virtual-terminal-sequences"></a>Klassische Konsolen-APIs im Vergleich zu virtuellen Terminalsequenzen

Unsere Empfehlung besteht darin, die klassische **Windows-Konsolen-API** durch **virtuelle Terminalsequenzen** zu ersetzen. In diesem Artikel werden die Unterschiede zwischen beiden erläutert und die Gründe für unsere Empfehlung erörtert.

## <a name="definitions"></a>Definitionen

Die klassische **[Windows-Konsolen-API](console-functions.md)** -Oberfläche ist als die Reihe funktionaler Schnittstellen der C-Sprache in `kernel32.dll` mit „Console“ im Namen definiert.

**[Virtuelle Terminalsequenzen](console-virtual-terminal-sequences.md)** sind definiert als Sprache von Befehlen, die in die Standardein- und Standardausgabestreams eingebettet ist. Virtuelle Terminalsequenzen verwenden nicht druckbare Escapezeichen für Signalbefehle, die mit normalem druckbarem Text kombiniert sind.

## <a name="history"></a>Verlauf

Die **Windows-Konsole** bietet eine umfassende API-Oberfläche für Client-Befehlszeilenanwendungen, um sowohl den Ausgabeanzeigepuffer als auch den Benutzereingabepuffer zu manipulieren. Andere Nicht-Windows-Plattformen haben diesen speziellen, API-gesteuerten Ansatz jedoch nie für Ihre Befehlszeilenumgebungen umgesetzt und sich stattdessen für die Verwendung von virtuellen Terminalsequenzen entschieden, die in die Standardein- und Standardausgabestreams eingebettet werden. *(Eine Zeit lang hat Microsoft dieses Verhalten auch noch in frühen Versionen von DOS und Windows über einen Treiber namens ANSI.SYS unterstützt.)*

Im Gegensatz dazu steuern **virtuelle Terminalsequenzen** (in einer Vielzahl von Dialekten) die Vorgänge in der Befehlszeilenumgebung für alle anderen Plattformen. Diese Sequenzen basieren auf einem [ECMA-Standard](https://www.ecma-international.org/publications/standards/Ecma-048.htm) und einer Reihe von Erweiterungen von vielen Anbietern, die sich zurückverfolgen lassen bis zu Terminals von DEC (Digital Equipment Corporation) und Tektronix, bis hin zu moderneren und gängigeren Softwareterminals wie [xterm](https://invisible-island.net/xterm/). Es gibt viele Erweiterungen innerhalb der Domäne virtueller Terminalsequenzen, und einige Sequenzen werden weiter verbreitet unterstützt als andere. Es lässt sich aber mit Sicherheit sagen, dass sich die Welt auf diesen Standard als Befehlssprache für Befehlszeilenerfahrungen geeinigt hat, wobei es eine bekannte Teilmenge gibt, die von praktisch jeder Terminal- und Befehlszeilen-Clientanwendung unterstützt wird.

## <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

**Virtuelle Terminalsequenzen** werden nativ plattformübergreifend unterstützt, sodass sich Terminalanwendungen und Befehlszeilen-Hilfsprogramme leicht zwischen Versionen und Varianten von Betriebssystemen portieren lassen, mit Ausnahme von Windows.

Im Gegensatz dazu werden **Windows-Konsolen-APIs** nur unter Windows unterstützt. Eine umfangreiche Adapter- oder Übersetzungsbibliothek muss für den Einsatz zwischen Windows und dem virtuellen Terminal geschrieben werden, oder umgekehrt, wenn versucht wird, Befehlszeilen-Hilfsprogramme von der einen oder anderen Plattform zu portieren.

### <a name="remote-access"></a>Remotezugriff

**Virtuelle Terminalsequenzen** besitzen einen großen Vorteil für den Remotezugriff. Sie benötigen keine zusätzliche Arbeit zu dem, was für das Einrichten einer standardmäßigen Remotebefehlszeilen-Verbindung erforderlich ist, um Remoteprozeduraufrufe zu transportieren oder auszuführen. Es reicht aus, einen ausgehenden mit einem eingehenden Transportkanal (oder einen einzelnen bidirektionalen Kanal) über eine Pipe, einen Socket, eine Datei, einen seriellen Anschluss oder ein beliebiges anderes Gerät zu verbinden, um alle Informationen, die für eine Anwendung erforderlich sind, die diese Sequenzen sendet, vollständig zu einem Remotehost zu transportieren.

Im Gegensatz dazu konnte man nur auf dem lokalen Computer auf die **Windows-Konsolen-APIs** zugreifen, und für alle Bemühungen, sie remote zu steuern, wäre es erforderlich, über einen einfachen Kanal hinaus eine vollständige Remoteaufruf- und -transport-Schnittstellenschicht zu erstellen.

### <a name="separation-of-concerns"></a>Trennung von Zuständigkeiten

Einige **Windows-Konsolen-APIs** bieten Zugriff auf niedriger Ebene auf die Ein- und Ausgabepuffer oder Komfortfunktionen für interaktive Befehlszeilen. Dazu können Aliase und Befehlsverläufe zählen, die innerhalb des Konsolensubsystems und der Hostumgebung programmiert sind, anstatt innerhalb der Befehlszeilen-Clientanwendung selbst.

Im Gegensatz dazu übertragen **andere Plattformen** die Verantwortung für das Speichern des aktuellen Zustands der Anwendung und für Komfortfunktionen auf das Befehlszeilen-Hilfsprogramm oder die Shell selbst.

Die Art, in der die **Windows-Konsole** diese Aufgabe im Konsolenhost und der API handhabt, beschleunigt und vereinfacht das Schreiben einer Befehlszeilenanwendung mit diesen Funktionen und beseitigt die Notwendigkeit, den Zeichenzustand zu speichern oder Komfortfunktionen für die Bearbeitung zu handhaben. Dadurch wird es aber auch aufgrund von Abweichungen bei Implementierungen und Verfügbarkeit nahezu unmöglich, diese Aktivitäten remote platfform-, versions- oder szenarioübergreifend zu verbinden. Durch diese Art der Verwaltung der Verantwortlichkeiten wird die endgültige interaktive Erfahrung dieser Windows-Befehlszeilenanwendungen auch vollständig abhängig von der Implementierung, den Prioritäten und dem Releasezyklus des Konsolenhosts.

Beispielsweise sind erweiterte Funktionen zur Zeilenbearbeitung wie Syntaxhervorhebung und komplexe Auswahl nur möglich, wenn eine Befehlszeilenanwendung die Bearbeitungsaspekte selbst verwaltet. Die Konsole könnte nie über genug Kontext verfügen, um diese Szenarien auf eine allgemeine Weise zu verstehen, wie dies die Clientanwendung kann.

Im Gegensatz dazu verwenden andere Plattformen **virtuelle Terminalsequenzen**, um diese Aktivitäten und die virtuelle Terminalkommunikation selbst durch wiederverwendbare clientseitige Bibliotheken wie [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) und [ncurses](https://invisible-island.net/ncurses/ncurses.html) zu verarbeiten. Das abschließende Terminal ist nur für die Anzeige von Informationen und das Empfangen von Eingaben über diesen bidirektionalen Kommunikationskanal verantwortlich.

### <a name="wrong-way-verbs"></a>Gegenläufige Verben

Bei **Windows-Konsolen** können einige Aktionen in den Ein- und Ausgabestreams in (zur natürlichen Richtung) umgekehrter Richtung durchgeführt werden. Dadurch können Windows-Befehlszeilenanwendungen die Verwaltung ihrer eigenen Puffer vermeiden. Außerdem können Windows-Befehlszeilen-Apps erweiterte Vorgänge ausführen, wie z. B. das Simulieren/Einfügen von Eingaben im Auftrag eines Benutzers oder das Zurücklesen des Verlaufs dessen, was geschrieben wurde.

Während dies zusätzliche Leistungsfähigkeit für Windows-Anwendungen bietet, die in einem bestimmten Benutzerkontext auf einem einzelnen Computer arbeiten, bietet es darüber hinaus einen Vektor, um Sicherheits- und Berechtigungsebenen oder Domänen zu überschreiten, wenn sie in bestimmten Szenarien verwendet werden. Zu diesen Szenarien gehören das Arbeiten zwischen Kontexten auf demselben Computer oder kontextübergreifend auf einem anderen Computer oder in einer anderen Umgebung.

Andere Plattformen, die **virtuelle Terminalsequenzen** verwenden, lassen diese Aktivität nicht zu. Die Absicht unserer Empfehlung, von der klassischen Windows-Konsole zu virtuellen Terminalsequenzen zu wechseln, ist es, mit dieser Strategie sowohl Interoperabilität als auch Sicherheitserwägungen zu verbinden.

### <a name="direct-window-access"></a>Direkter Fensterzugriff

Die **Windows-Konsolen-API-Oberfläche** stellt das exakte Fensterhandle für das Hostingfenster bereit. Dies erlaubt es einem Befehlszeilen-Hilfsprogramm, erweiterte Fenstervorgänge auszuführen, indem die breite Palette von Win32-APIs verwendet wird, die für ein Fensterhandle zulässig sind. Diese Win32-APIs können den Fensterzustand, den Rahmen, das Symbol und andere Eigenschaften des Fensters bearbeiten.

Im Gegensatz dazu gibt es auf anderen Plattformen mit **virtuellen Terminalsequenzen** eine kleine Gruppe von Befehlen, die mit Fenstern ausgeführt werden können. Mit diesen Befehlen können z. B. die Fenstergröße geändert oder der Fenstertitel angezeigt werden. Aber sie müssen im selben Band und unter derselben Kontrolle wie der Rest des Streams ausgeführt werden.

Mit der Weiterentwicklung von Windows haben sich die Sicherheitskontrollen und -einschränkungen für Fensterhandles erhöht. Außerdem hat sich die Art und das Vorhandensein eines von Anwendungen adressierbaren Fensterhandles für jedes spezifische Benutzeroberflächenelement entwickelt, insbesondere durch die gestiegene Unterstützung von Geräteformfaktoren und Plattformen. Dadurch wird der direkte Fensterzugriff auf Befehlszeilenanwendungen anfällig, wenn sich die Plattform und die Erfahrungen weiterentwickeln.

### <a name="unicode"></a>Unicode

UTF-8 ist die akzeptierte Codierung für Unicode-Daten auf fast allen modernen Plattformen, da sie das richtige Gleichgewicht zwischen Portabilität, Speichergröße und Verarbeitungszeit hält. Historisch hat Windows allerdings UTF-16 als primäre Codierung für Unicode-Daten gewählt. Die Unterstützung für UTF-8 in Windows wächst beständig, und die Verwendung dieser Unicode-Formate schließt die Verwendung anderer Codierungen nicht aus.

Die **Windows-Konsolen** plattform hat alle vorhandenen Codepages und Codierungen unterstützt und wird diese weiterhin unterstützen. Verwenden Sie UTF-16 für maximale Kompatibilität in Windows-Versionen, und führen Sie bei Bedarf eine algorithmische Übersetzungen mit UTF-8 durch. Die Unterstützung von UTF-8 für das Konsolensystem wird zurzeit stetig verbessert.

Die UTF-16-Unterstützung in der Konsole kann ohne zusätzliche Konfiguration über die _W_-Variante aller Konsolen-APIs verwendet werden. Außerdem ist dies die wahrscheinlichere Wahl bei Anwendungen, die bereits im Umgang mit UTF-16 versiert sind, durch die Kommunikation mit der `wchar_t`- und _W_-Variante anderer Microsoft- und Windows-Plattformfunktionen und -produkte.

Die UTF-8-Unterstützung in der Konsole kann über die _A_-Variante von Konsolen-APIs für Konsolenhandles verwendet werden, nachdem die Codepage je nachdem mit der Methode [**SetConsoleOutputCP**](setconsoleoutputcp.md) oder [**SetConsoleCP**](setconsolecp.md) auf `65001` oder `CP_UTF8` festgelegt wurde. Das Festlegen der Codepages im Voraus ist nur erforderlich, wenn der Computer in den Einstellungen für Nicht-Unicode-Anwendungen im Abschnitt „Region“ der Systemsteuerung nicht die Option „Unicode UTF-8 für weltweite Sprachunterstützung verwenden“ ausgewählt hat.

>[!NOTE]
> Ab sofort wird UTF-8 vollständig für den Standardausgabestream mit den Methoden [**WriteConsole**](writeconsole.md) und [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) unterstützt. Die Unterstützung für den Eingabestream variiert abhängig vom Eingabemodus und wird im Laufe der Zeit weiter verbessert. Insbesondere die standardmäßigen **[„gekocht“](high-level-console-modes.md)** -Modi (cooked) bei Eingaben unterstützen UTF-8 noch nicht vollständig. Den aktuellen Status dieser Arbeit finden Sie unter [**microsoft/terminal#7777**](https://github.com/microsoft/terminal/issues/7777) auf GitHub. Die Problemumgehung besteht darin, dass Sie den algorithmisch übersetzbaren UTF-16-Code zum Lesen von Eingaben über [**ReadConsoleW**](readconsole.md) oder [**ReadConsoleInputW**](readconsoleinput.md) verwenden, bis die ausstehenden Probleme behoben sind.

## <a name="recommendations"></a>Empfehlungen

Für alle neuen und fortdauernden Entwicklungen unter Windows werden **virtuelle Terminalsequenzen** als Interaktionsmethode mit dem Terminal empfohlen. Dadurch konvergieren Windows-Befehlszeilen-Clientanwendungen mit dem Stil der Anwendungsprogrammierung auf allen anderen Plattformen.

### <a name="exceptions-for-using-windows-console-apis"></a>Ausnahmen für die Verwendung von Windows-Konsolen-APIs

Es ist **immer noch eine begrenzte Teilmenge der Windows-Konsolen-APIs erforderlich**, um die anfängliche Umgebung einzurichten. Die Windows-Plattform unterscheidet sich weiterhin von anderen hinsichtlich der Handhabung von Prozessen, Signalen, Geräten und Codierungen:

- Die Standardhandles für einen Prozess werden weiterhin mit **[GetStdHandle](getstdhandle.md)** und **[SetStdHandle](setstdhandle.md)** gesteuert.

- Die Konfiguration der Konsolenmodi eines Handles zum Abonnieren der Unterstützung für virtuelle Terminalsequenzen wird von **[GetConsoleMode](getconsolemode.md)** und **[SetConsoleMode](setconsolemode.md)** verarbeitet.

- Die Deklaration der Codepage- oder UTF-8-Unterstützung wird mit den Methoden [**SetConsoleOutputCP**](setconsoleoutputcp.md) und [**SetConsoleCP**](setconsolecp.md) durchgeführt.

- [**AllocConsole**](allocconsole.md), [**AttachConsole**](attachconsole.md) und [**FreeConsole**](freeconsole.md) benötigen möglicherweise eine gewisse Ebene der übergreifenden Prozessverwaltung, um einer Konsolengerätesitzung beizutreten oder sie zu verlassen.

- Signale und Signalverarbeitung werden weiterhin mit [**SetConsoleCtrlHandler**](setconsolectrlhandler.md), [**HandlerRoutine**](handlerroutine.md) und [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) durchgeführt.

- Die Kommunikation mit den Konsolengerätehandles kann mit [**WriteConsoleKonsole**](writeconsole.md) und [**ReadConsole**](readconsole.md) erfolgen. Diese können auch durch Laufzeiten von Programmiersprachen in den Formen von: -C Runtime (CRT) genutzt werden: [Stream-E/A](https://docs.microsoft.com/cpp/c-runtime-library/stream-i-o) wie **printf**, **scanf**, **putc**, **getc** oder [anderen Ebenen von E/A-Funktionen](https://docs.microsoft.com/cpp/c-runtime-library/input-and-output).
        - C++-Standardbibliothek (STL): [iostream](https://docs.microsoft.com/cpp/standard-library/iostream) wie **cout** und **cin**.
        - .NET-Runtime: [System.Console](https://docs.microsoft.com/dotnet/api/system.console) wie **Console.WriteLine**.

- Anwendungen, die über Änderungen der Fenstergröße informiert sein müssen, müssen weiterhin [**ReadConsoleInput**](readconsoleinput.md) verwenden, um sie kombiniert mit Schlüsselereignissen zu empfangen, da **ReadConsole** alleine sie verwirft.

- Das Herausfinden der Fenstergröße muss weiterhin mit [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) für Anwendungen erfolgen, die versuchen, Spalten oder Raster zu zeichnen oder die Anzeige zu füllen. Fenster- und Puffergröße stimmen in einer [Pseudokonsolen](pseudoconsoles.md)sitzung überein.

## <a name="future-planning-and-pseudoconsole"></a>Zukünftige Planung und Pseudokonsole

Es ist nicht geplant, die Windows-Konsolen-APIs von der Plattform zu entfernen.

Im Gegensatz dazu hat der Windows-Konsolenhost die **[Pseudokonsolen](pseudoconsoles.md)** technologie bereitgestellt, um Aufrufe vorhandener Windows-Befehlszeilenanwendungen in virtuelle Terminalsequenzen zu übersetzen und diese remote oder plattformübergreifend an eine andere Hostingumgebung weiterzuleiten.

Diese Übersetzung ist nicht perfekt. Sie erfordert, dass das Konsolenhostfenster eine simulierte Umgebung dessen aufrechterhält, was Windows dem Benutzer angezeigt hätte. Anschließend wird ein Replikat dieser simulierten Umgebung in den **Pseudokonsolen** host projiziert. Alle Aufrufe der Windows-Konsolen-API werden innerhalb der simulierten Umgebung betrieben, um die Anforderungen der Legacy-Befehlszeilen-Clientanwendung zu erfüllen. Nur die Effekte werden an den letzten Host weitergegeben.

Einer Befehlszeilenanwendung, die vollständige plattformübergreifende Kompatibilität sowie vollständige Unterstützung aller neuen Funktionen und Szenarien sowohl unter Windows als auch an anderer Stelle wünscht, wird daher empfohlen, zu virtuellen Terminalsequenzen zu wechseln und die Architektur der Befehlszeilenanwendungen an alle Plattformen anzupassen.

Weitere Informationen zu diesem Windows-Übergang für Befehlszeilenanwendungen finden Sie in unserer [Ökosystemroadmap](ecosystem-roadmap.md).
