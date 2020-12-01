---
title: Klassische Konsolen-APIs im Vergleich zu virtuellen Terminalsequenzen
description: Beschreibt den Unterschied zwischen der API-Oberfläche der klassischen Win32-Konsole und dem Konzept der virtuellen Terminal Sequenzen, die manchmal auch als Escapesequenzen bezeichnet werden, zum Schreiben von Befehlszeilen Anwendungen.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Terminal, virtuelles Terminal, Escape-Sequenzen, VT, VT100, Konsolen-API
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: 541300b50521909b22ceaccb595f1945fbfc7e6d
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420179"
---
# <a name="classic-console-apis-versus-virtual-terminal-sequences"></a>Klassische Konsolen-APIs im Vergleich zu virtuellen Terminalsequenzen

Unsere Empfehlung besteht darin, die klassische **Windows-Konsolen-API** durch **virtuelle Terminal Sequenzen** zu ersetzen. In diesem Artikel werden die Unterschiede zwischen den beiden erläutert und die Gründe für unsere Empfehlung erörtert.

## <a name="definitions"></a>Definitionen

Die klassische **[API](console-functions.md)** -Oberfläche der Windows-Konsole wird als eine Reihe von funktionsfähigen C-Sprachschnittstellen `kernel32.dll` in mit "Console" im Namen definiert.

**[Virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md)** werden als Sprache von Befehlen definiert, die in die standardmäßigen Eingabe-und Standardausgabestreams eingebettet sind. Virtuelle Terminal Sequenzen verwenden nicht druckbare Escapezeichen für Signal Befehle, die mit normalem Druck barem Text verschachtelt sind.

## <a name="history"></a>Verlauf

Die **Windows-Konsole** bietet eine umfassende API-Oberfläche für Client Befehlszeilen Anwendungen, um sowohl den Ausgabe Anzeige Puffer als auch den Benutzereingabe Puffer zu bearbeiten. Andere nicht-Windows-Plattformen haben diese spezielle API-gesteuerte Vorgehensweise jedoch nie für Ihre Befehlszeilen Umgebungen gewährt, indem Sie stattdessen virtuelle Terminal Sequenzen verwenden, die in den standardmäßigen Eingabe-und Standardausgabestreams eingebettet sind. *(Für einen Zeitraum hat Microsoft dieses Verhalten auch in frühen Editionen von DOS und Windows über einen Treiber namens "ANSI.SYS" unterstützt.)*

Im Gegensatz dazu Steuern **virtuelle Terminal Sequenzen** (in einer Vielzahl von Dialekten) die Befehlszeilen-Umgebungs Vorgänge für alle anderen Plattformen. Diese Sequenzen basieren auf einem [ECMA-Standard](https://www.ecma-international.org/publications/standards/Ecma-048.htm) und einer Reihe von Erweiterungen, die von vielen Anbietern zurück zur Digital Equipment Corporation und den Tektronix-Terminals, bis hin zu moderneren und allgemeinen Software Terminals, wie [xterm](https://invisible-island.net/xterm/) Viele Erweiterungen sind innerhalb der virtuellen Terminal Sequenz Domäne vorhanden, und einige Sequenzen werden besser unterstützt als andere. es ist jedoch sicher zu sagen, dass die Welt auf diese Weise als Befehlssprache für die Befehlszeilen Umgebung standardisiert ist, bei der eine bekannte Teilmenge von praktisch jeder Terminal-und Befehlszeilen-Client Anwendung unterstützt wird.

## <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

**Virtuelle Terminal Sequenzen** werden plattformübergreifend unterstützt, sodass Terminalanwendungen und Befehlszeilen Programme Zwischenversionen und Variationen von Betriebssystemen mit Ausnahme von Windows leicht portierbar sind.

Im Gegensatz dazu werden **Windows-Konsolen-APIs** nur unter Windows unterstützt. Ein umfangreicher Adapter oder eine Übersetzungs Bibliothek muss zwischen Windows und dem virtuellen Terminal geschrieben werden, oder umgekehrt, wenn versucht wird, Befehlszeilen-Hilfsprogramme von einer Plattform oder einer anderen Plattform zu portieren.

### <a name="remote-access"></a>Remotezugriff

**Virtuelle Terminal Sequenzen** haben einen großen Vorteil für den Remote Zugriff. Sie benötigen keine zusätzliche Arbeit zum transportieren oder Ausführen von Remote Prozedur aufrufen über das, was zum Einrichten einer standardmäßigen Remote-Befehlszeilen Verbindung erforderlich ist. Die einfache Verbindung eines ausgehenden und eines eingehenden Transport Kanals (oder eines einzelnen bidirektionalen Kanals) über eine Pipe, einen Socket, eine Datei, einen seriellen Anschluss oder ein anderes Gerät reicht aus, um alle Informationen vollständig zu übertragen, die für eine Anwendung erforderlich sind, die diese Sequenzen in einem Remote Host meldet

Im Gegensatz dazu konnten auf die **Windows-Konsolen-APIs** nur auf dem lokalen Computer zugegriffen werden, und alle Bemühungen, Sie zu Remote machen, mussten eine gesamte Remote Aufruf-und transportschnittstellenschicht über einen einfachen Kanal hinaus entwickeln.

### <a name="separation-of-concerns"></a>Trennung von Zuständigkeiten

Einige **Windows-Konsolen-APIs** bieten Zugriff auf niedriger Ebene auf die Eingabe-und Ausgabepuffer oder die Hilfsfunktionen für interaktive Befehlszeilen. Dazu zählen möglicherweise Aliase und Befehlsverlauf, die innerhalb des Konsolen Subsystems und der Host Umgebung programmiert sind, anstatt innerhalb der Befehlszeilen Client Anwendung selbst.

Im Gegensatz dazu machen **andere Plattformen** den Arbeitsspeicher des aktuellen Anwendungs Zustands und die praktische Funktionalität der Aufgabe des Befehlszeilen Dienstprogramms oder der Shell selbst.

Die **Windows-Konsole** , die diese Verantwortung im Konsolen Host und in der API behandelt, vereinfacht das Schreiben einer Befehlszeilen Anwendung mit diesen Features, sodass sich der Zeichnungs Zustand und die Bearbeitung von Bearbeitungsfunktionen nicht mehr in der Verantwortung befinden. Dadurch ist es jedoch nahezu unmöglich, diese Aktivitäten Remote über Plattformen, Versionen oder Szenarien hinweg zu verbinden, aufgrund von Abweichungen in Implementierungen und Verfügbarkeit. Durch diese Art der Verwaltung der Verantwortlichkeiten wird die endgültige interaktive Darstellung dieser Windows-Befehlszeilen Anwendungen auch vollständig von der Implementierung, den Prioritäten und dem releasecycle des Konsolen Hosts abhängig gemacht.

Beispielsweise sind erweiterte Funktionen zur Zeilen Bearbeitung, wie Syntax Hervorhebung und komplexe Auswahl, nur möglich, wenn eine Befehlszeilen Anwendung selbst Bearbeitungs Probleme behandelt. Die Konsole könnte nie genug Kontext haben, um diese Szenarien auf eine weitreichende Weise wie die Client Anwendung vollständig zu verstehen.

Im Gegensatz dazu werden von anderen Plattformen **virtuelle Terminal Sequenzen** verwendet, um diese Aktivitäten und die virtuelle Terminal Kommunikation selbst durch wiederverwendbare Client seitige Bibliotheken, wie z. b. "read [Line](https://tiswww.case.edu/php/chet/readline/rltop.html) " und [ncurrses](https://invisible-island.net/ncurses/ncurses.html), Das abschließende Terminal ist nur für die Anzeige von Informationen und das Empfangen von Eingaben über den bidirektionalen Kommunikationskanal verantwortlich.

### <a name="wrong-way-verbs"></a>Wrong-Way Verben

Mit der **Windows-Konsole** können einige Aktionen in der Richtung der Eingabe-und Ausgabedaten Ströme in umgekehrter Richtung durchgeführt werden. Dadurch können Windows-Befehlszeilen Anwendungen die Verwaltung Ihrer eigenen Puffer vermeiden. Außerdem können Windows-Befehlszeilen-apps Erweiterte Vorgänge ausführen, wie z. b. das simulieren/Einfügen von Eingaben im Namen eines Benutzers oder das zurück Lesen eines Teils der geschriebenen Änderungen.

Dies bietet zusätzliche Leistungsfähigkeit für Windows-Anwendungen, die in einem bestimmten Benutzer Kontext auf einem einzelnen Computer ausgeführt werden. Darüber hinaus bietet Sie einen Vektor für Sicherheits-und Berechtigungsebenen oder Domänen, wenn Sie in bestimmten Szenarien verwendet werden. Zu diesen Szenarien gehören das Arbeiten zwischen Kontexten auf demselben Computer oder zwischen Kontexten und einem anderen Computer oder einer anderen Umgebung.

Diese Aktivität wird von anderen Plattformen, von denen **virtuelle Terminal Sequenzen** verwendet werden, nicht zugelassen. Der Zweck unserer Empfehlung, von der klassischen Windows-Konsole zu virtuellen Terminal Sequenzen zu wechseln, besteht darin, mit dieser Strategie sowohl für Interoperabilität als auch für Sicherheitszwecke zu konvergieren.

### <a name="direct-window-access"></a>Direkter Fenster Zugriff

Die **Windows-Konsolen-API-Oberfläche** bietet das genaue Fenster Handle für das Hostingfenster. Dadurch kann ein Befehlszeilen-Hilfsprogramm erweiterte Fenster Vorgänge durchführen, indem es in den weiten Umfang von Win32-APIs gelangt, die für ein Fenster Handle zulässig sind. Diese Win32-APIs können den Fenster Zustand, den Frame, das Symbol oder andere Eigenschaften des Fensters bearbeiten.

Im Gegensatz dazu gibt es auf anderen Plattformen mit **virtuellen Terminal Sequenzen** einen schmalen Satz von Befehlen, die für das Fenster ausgeführt werden können. Diese Befehle können Dinge wie das Ändern der Fenstergröße oder des angezeigten Titels ausführen. Sie müssen jedoch im gleichen Band und unter dem gleichen Steuerelement wie der Rest des Streams ausgeführt werden.

Wenn sich Windows entwickelt hat, haben sich die Sicherheitskontrollen und-Einschränkungen für Fenster Handles verbessert. Außerdem wurde die Art und das vorhanden sein eines von der Anwendung adressierbaren Fenster Handles für ein bestimmtes Benutzeroberflächen Element weiterentwickelt, insbesondere bei erhöhter Unterstützung von Geräte Formular Faktoren und-Plattformen. Dadurch wird direkter Fenster Zugriff auf Befehlszeilen Anwendungen anfällig, wenn sich die Plattform und die Erfahrungen weiterentwickeln.

### <a name="unicode"></a>Unicode

UTF-8 ist die akzeptierte Codierung für Unicode-Daten in fast allen modernen Plattformen, da Sie das richtige Gleichgewicht zwischen Portabilität, Speichergröße und Verarbeitungszeit trifft. Allerdings wählte Windows in der Vergangenheit UTF-16 als primäre Codierung für Unicode-Daten. Die Unterstützung für UTF-8 wird in Windows gesteigert, und die Verwendung dieser Unicode-Formate schließt die Verwendung anderer Codierungen nicht aus.

Die **Windows-Konsolen** Plattform wird unterstützt und unterstützt weiterhin alle vorhandenen Codepages und Codierungen. Verwenden Sie UTF-16 für die maximale Kompatibilität in Windows-Versionen, und führen Sie bei Bedarf algorithmische Übersetzungen mit UTF-8 aus. Die Unterstützung von UTF-8 wird für das Konsolensystem zurzeit ausgeführt.

Die UTF-16-Unterstützung in der-Konsole kann ohne zusätzliche Konfiguration über die Variante " _W_ " aller Konsolen-APIs verwendet werden. Außerdem ist es wahrscheinlicher, dass Anwendungen, die sich in UTF-16 über die Kommunikation mit der `wchar_t` und _W_ -Variante anderer Microsoft-und Windows-Plattformfunktionen und-Produkte gut auskennen.

UTF-8-Unterstützung in der-Konsole kann über _eine_ Variante der Konsolen-APIs für Konsolen Handles verwendet werden, nachdem die Codepage auf `65001` oder `CP_UTF8` mit den Methoden [**setconsoleoutputcp**](setconsoleoutputcp.md) und [**setconsolecp**](setconsolecp.md) festgelegt wurde. Das Festlegen der Codepages im Voraus ist nur erforderlich, wenn der Computer in den Einstellungen für nicht-Unicode-Anwendungen im Bereich Region der Systemsteuerung nicht die Option "Unicode UTF-8 für die Unterstützung für die weltweite Sprache verwenden" ausgewählt hat.

>[!NOTE]
> Ab jetzt wird UTF-8 vollständig für den Standardausgabestream mit den Methoden " [**Write Console**](writeconsole.md) " und " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " unterstützt. Die Unterstützung für den Eingabestream variiert abhängig vom Eingabemodus und wird im Laufe der Zeit weiter verbessert. Insbesondere werden UTF-8 noch nicht vollständig von den Standard Modi **["gekocht"](high-level-console-modes.md)** unterstützt. Den aktuellen Status dieser Arbeit finden Sie unter [**Microsoft/Terminal # 7777**](https://github.com/microsoft/terminal/issues/7777) auf GitHub. Die Problem Umgehung besteht darin, dass Sie das algorithmisch übersetzbare UTF-16-Element verwenden, um Eingaben über [**readconsolew**](readconsole.md) oder [**readconsoleinputw**](readconsoleinput.md) zu lesen, bis die ausstehenden Probleme behoben werden.

## <a name="recommendations"></a>Empfehlungen

Für alle neuen und fortlaufenden Entwicklungen unter Windows **werden virtuelle Terminal Sequenzen** als Methode für die Interaktion mit dem Terminal empfohlen. Dadurch werden Windows-Befehlszeilen Client Anwendungen mit dem Stil der Anwendungsprogrammierung auf allen anderen Plattformen zusammengeführt.

### <a name="exceptions-for-using-windows-console-apis"></a>Ausnahmen für die Verwendung von Windows-Konsolen-APIs

**Es ist immer noch eine begrenzte Teilmenge der Windows-Konsolen-APIs erforderlich** , um die anfängliche Umgebung einzurichten. Die Windows-Plattform unterscheidet sich weiterhin von anderen in Verarbeitung, Signal, Gerät und Codierung:

- Die Standard Handles für einen Prozess werden weiterhin mit " **[getstdhandle](getstdhandle.md)** " und " **[setstdhandle](setstdhandle.md)**" gesteuert.

- Die Konfiguration der Konsolen Modi eines Handles zum Abonnieren der Unterstützung virtueller Terminal Sequenzen wird mit **[getconsolemode](getconsolemode.md)** und **[setconsolemode](setconsolemode.md)** behandelt.

- Deklaration der Codepage-oder UTF-8-Unterstützung wird mit den Methoden [**setconsoleoutputcp**](setconsoleoutputcp.md) und [**setconsolecp**](setconsolecp.md) durchgeführt.

- Möglicherweise ist ein gewisses Maß an Prozess Verwaltung erforderlich, wenn die [**zuordenkonsole**](allocconsole.md), [**attachconsole**](attachconsole.md) und [**freeconsole**](freeconsole.md) einer Konsolen Geräte Sitzung beitreten oder diese verlassen.

- Signale und die Signalverarbeitung werden weiterhin mit [**SetConsoleCtrlHandler**](setconsolectrlhandler.md), [**Handlerroutine**](handlerroutine.md)und [**generateconsolectrlevent**](generateconsolectrlevent.md)durchgeführt.

- Die Kommunikation mit den Geräte Handles der Konsole kann mit " [**Write Console**](writeconsole.md) " und "read [**Console**](readconsole.md)" durchgeführt werden. Diese können auch über Laufzeiten der Programmiersprache in den folgenden Formen genutzt werden:-C Runtime (CRT): [Stream](https://docs.microsoft.com/cpp/c-runtime-library/stream-i-o) -e/a wie **printf**, **scanf**, **putc**, **getc** oder [andere Ebenen von e/a-Funktionen](https://docs.microsoft.com/cpp/c-runtime-library/input-and-output).
        -C++-Standard Bibliothek (STL): [iostream](https://docs.microsoft.com/cpp/standard-library/iostream) wie **cout** und **CIN**.
        -.NET-Runtime: [System. Console](https://docs.microsoft.com/dotnet/api/system.console) wie **Console. Write teline**.

- Anwendungen, die sich auf Änderungen der Fenstergröße beziehen müssen, müssen weiterhin " [**leconsoleinput**](readconsoleinput.md) " verwenden, um Sie mit Schlüsselereignissen zu überlappen, da diese von der "read **Console** " allein verworfen werden.

- Das Auffinden der Fenstergröße muss immer noch mit [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) für Anwendungen erfolgen, die versuchen, Spalten, Raster oder die Anzeige zu zeichnen. Die Fenster-und Puffergröße wird in einer [pseudoconsole](pseudoconsoles.md) -Sitzung abgeglichen.

## <a name="future-planning-and-pseudoconsole"></a>Zukünftige Planung und pseudoconsole

Es ist nicht geplant, die Windows-Konsolen-APIs von der Plattform zu entfernen.

Im Gegensatz dazu hat der Windows-Konsolen Host die **[pseudoconsole](pseudoconsoles.md)** -Technologie bereitgestellt, um vorhandene Windows-Befehlszeilen Anwendungs Aufrufe in virtuelle Terminal Sequenzen zu übersetzen und diese Remote oder plattformübergreifend an eine andere Host Umgebung weiterzuleiten.

Diese Übersetzung ist nicht perfekt. Hierfür ist es erforderlich, dass das Konsolen Host Fenster eine simulierte Umgebung beibehält, welche Fenster dem Benutzer angezeigt werden. Anschließend wird ein Replikat dieser simulierten Umgebung auf den **pseudoconsole** -Host projiziert. Alle Aufrufe der Windows-Konsolen-API werden innerhalb der simulierten Umgebung betrieben, um die Anforderungen der Legacy-Befehlszeilen Client Anwendung zu erfüllen. Nur die Effekte werden auf den letzten Host weitergegeben.

Eine Befehlszeilen Anwendung, die eine plattformübergreifende vollständige Kompatibilität und vollständige Unterstützung aller neuen Features und Szenarien sowohl unter Windows als auch an anderer Stelle unterstützt, wird daher empfohlen, um zu virtuellen Terminal Sequenzen zu wechseln und die Architektur der Befehlszeilen Anwendungen an alle Plattformen anzupassen.

Weitere Informationen zu diesem Windows-Übergang für Befehlszeilen Anwendungen finden Sie in unserer Roadmap für das [Ökosystem](ecosystem-roadmap.md).
