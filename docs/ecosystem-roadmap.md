---
title: Roadmap für die Windows-Konsole und das Terminalökosystem
description: Bietet eine allgemeine Übersicht über die Interaktionen zwischen und Plänen für den Windows-Konsolen Host, Konsolen-APIs, Konsolen Subsystem und Terminal Produkt.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Terminal, virtuelles Terminal, Konsolen Host, Befehlszeile, Subsystem, Roadmap, Ökosystem
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: e5d28a06789f230943d70a49e7c89642b17fdb5c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420259"
---
# <a name="windows-console-and-terminal-ecosystem-roadmap"></a>Roadmap für die Windows-Konsole und das Terminalökosystem

Dieses Dokument ist eine allgemeine Roadmap der Windows-Konsole und der Windows-Terminal Produkte. Folgendes wird behandelt:


- Wie die Windows-Konsole und das Windows-Terminal in das Ökosystem von Befehlszeilen Anwendungen über Windows und andere Betriebssysteme abgestimmt werden.

- Einen Verlauf und einen zukünftigen Überblick über die Produkte, Features und Strategien, die Bestandteil der Entwicklung der Plattform sind, sowie die Entwicklung für diese Plattform.

Der Schwerpunkt des aktuellen Konsolen-/Terminal-Zeitraums bei Microsoft besteht darin, den Entwicklern auf der Windows-Plattform eine erstklassige Terminal Darstellung [direkt hinzu zubringen und klassische Windows](classic-vs-vt.md) -Konsolen-APIs zu migrieren, indem Sie mit der [pseudoconsole](pseudoconsoles.md)durch [virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md) ersetzt werden. Das **[Windows-Terminal](/terminal/get-started)** zeigt diesen Übergang in eine erstklassige Umgebung, die die [Open Source-Zusammenarbeit](https://github.com/microsoft/terminal) aus der Entwickler Community lädt und ein vollständiges Spektrum an Vermischung und Abgleich der Client-Befehlszeilen-und terminalhostinganwendungen unterstützt sowie das Windows-Ökosystem mit allen anderen Plattformen vereinheitlicht.

## <a name="definitions"></a>Definitionen

Es wird empfohlen, sich mit den [Definitionen](definitions.md) der allgemeinen Terminologie vertraut zu machen, die in diesem Bereich verwendet wird, bevor Sie fortfahren. Gängige Terminologie: [Befehlszeilen Anwendungen (oder Konsolen Anwendungen)](definitions.md#command-line-applications), [Standard Handles ( `STDIN` , `STDOUT` , `STDERR` )](definitions.md#standard-handles), [TTY-und Pty-Geräte](definitions.md#ttypty), [Clients und Server](definitions.md#clients-and-servers), [Konsolen Subsystem](definitions.md#console-subsystem), [Konsolen Host](definitions.md#console-host), [pseudoconsole](definitions.md#pseudoconsole)und [Terminal](definitions.md#terminal).

## <a name="architecture"></a>Architektur

Die allgemeine Architektur des Systems besteht aus vier Teilen: Client, Gerät, Server und Terminal.

![Flussdiagramm Quelle für die Befehlszeilen Verbindung zwischen Client und Gerät und Server zu Terminal](images/command-line-communication.png)

### <a name="client"></a>Client

Der Client ist eine Befehlszeilen Anwendung, die eine textbasierte Benutzeroberfläche verwendet, um dem Benutzer die Eingabe von Befehlen (anstatt einer Maus basierten Benutzeroberfläche) zu ermöglichen, und eine Textdarstellung des Ergebnisses zurückgibt. Unter Windows stellt die Konsolen-API eine Kommunikationsschicht zwischen dem Client und dem Gerät bereit. (Dies kann auch ein Standard-Konsolen Handle mit Geräte Steuerungs-APIs sein).

### <a name="device"></a>Sicherungsmedium

Bei dem Gerät handelt es sich um eine zwischengeschaltete Kommunikationsschicht zwischen zwei Prozessen, dem Client und dem Server. Unter Windows ist dies der Konsolentreiber. Auf anderen Plattformen ist dies das TTY-oder Pty-Gerät. Andere Geräte, wie z. b. Dateien, Pipes und Sockets, können als dieser Kommunikationskanal verwendet werden, wenn die gesamte Transaktion als Klartext oder [virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md)enthalten ist, aber nicht mit [Windows-Konsolen-APIs](console-functions.md).

### <a name="server"></a>Server

Der Server interpretiert die angeforderten API-Aufrufe oder-Nachrichten vom Client. Unter Windows im klassischen Betriebsmodus erstellt der Server auch eine Benutzeroberfläche, um die Ausgabe auf dem Bildschirm anzuzeigen. Der Server sammelt zusätzlich Eingaben, die in Antwort Nachrichten an den Client über den Treiber zurückgesendet werden, wie z. b. ein Terminal, das im selben Modul gebündelt ist. Mit dem [pseudoconsole](pseudoconsoles.md) -Modus ist es vielmehr nur ein Konvertierer, diese Informationen in [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md) an ein angefügtes Terminal zu präsentieren.

### <a name="terminal"></a>Terminal

Das Terminal ist die endgültige Ebene, die dem Benutzer grafische Anzeige-und Interaktivitäts Dienste bereitstellt. Er ist dafür verantwortlich, Eingaben zu erfassen und als [virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md)zu codieren, die letztendlich den des Clients erreichen `STDIN` . Außerdem werden die *virtuellen Terminal Sequenzen* , die Sie `STDOUT` für die Darstellung auf dem Bildschirm vom Client empfängt, empfangen und decodiert.

#### <a name="further-connections"></a>Weitere Verbindungen

Als Nachtrag können weitere Verbindungen durch Verkettung von Anwendungen, die mehrere Rollen erfüllen, zu einem der Endpunkte erfolgen. Beispielsweise verfügt eine SSH-Sitzung über zwei Rollen: Es handelt sich um ein **Terminal** für die Befehlszeilen Anwendung, die auf einem Gerät ausgeführt wird, aber alle empfangenen Informationen an eine **Client** Rolle auf einem anderen Gerät weiterleitet. Diese Verkettung kann unbegrenzt auf Geräten und Kontexten erfolgen, die eine umfassende szenarioflexibilität bieten.

Auf nicht-Windows-Plattformen sind die **Server** -und **Terminal** Rollen eine einzelne Einheit, da keine Übersetzungs Kompatibilitätsschicht zwischen einem API-Satz und [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md)erforderlich ist.

## <a name="microsoft-products"></a>Microsoft-Produkte

Alle Microsoft Windows-Befehlszeilen Produkte sind jetzt auf GitHub in einem Open Source-Repository, [Microsoft/Terminal](https://github.com/microsoft/terminal), verfügbar.

### <a name="windows-console-host"></a>Windows-Konsolen Host

Dies ist die herkömmliche Windows-Benutzeroberfläche für Befehlszeilen Anwendungen. Er verarbeitet alle Konsolen-API-Wartungsarbeiten, die von allen angefügten Befehlszeilen Anwendungen aufgerufen werden. In der Windows-Konsole wird auch die grafische Darstellung der Benutzeroberfläche (GUI) für alle diese Anwendungen behandelt. Sie befindet sich im System Verzeichnis als `conhost.exe` oder `openconsole.exe` im Open Source-Formular. Dies ist das Windows-Betriebssystem. Sie finden Sie auch in anderen Microsoft-Produkten, die aus dem Open-Source-Repository erstellt wurden, um eine aktuellere Implementierung der [pseudoconsole](pseudoconsoles.md) -Infrastruktur zu erhalten. Gemäß den oben beschriebenen Definitionen funktioniert Sie entweder in einer kombinierten Server-und terminalrolle oder einer Server Rolle über die bevorzugte _pseudoconsole_ -Infrastruktur.

### <a name="windows-terminal"></a>Windows-Terminal

Dies ist die neue Windows-Benutzeroberfläche für Befehlszeilen Anwendungen. Das Windows-Terminal fungiert als erstes Beispiel für die Verwendung von [pseudoconsole](pseudoconsoles.md) , um die Probleme zwischen der API-Wartung und der textbasierten Anwendungsübergreifende Kommunikation zu trennen, ähnlich wie bei allen nicht-Windows-Plattformen.


Das Windows-Terminal ist die Oberfläche für den Text Modus für Windows. Es veranschaulicht die Funktionen des Ökosystems und treibt die Windows-Entwicklung in Richtung der Vereinheitlichung mit anderen Plattformen. Das Windows-Terminal ist auch ein Beispiel dafür, wie eine robuste und komplexe moderne Anwendung erstellt wird, die den Verlauf und die Palette von Windows-APIs und-Frameworks umfasst. Gemäß den oben aufgeführten Definitionen arbeitet dieses Produkt in einer Terminal Rolle.

## <a name="major-historical-milestones"></a>Wichtige Meilensteine der Vergangenheit

Die wichtigsten Verlaufs Meilensteine für das Konsolen Subsystem sind in der Implementierung vor 2014 unterteilt und werden dann in eine Übersicht über die seit 2014 ausgeführten Arbeiten verschoben, wenn der erneuerte Fokus auf der Befehlszeile im Windows 10-Zeitraum gebildet wurde.

### <a name="initial-implementation"></a>Anfängliche Implementierung

**\[ 1989-90er Jahre]** das anfängliche Konsolen Host System wurde als Emulation der DOS-Umgebung innerhalb des Windows-Betriebssystems implementiert. Der Code ist entkoppelt und kooperativ an der [Eingabeaufforderung](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd), `cmd.exe` , die eine Darstellung dieser DOS-Umgebung darstellt. Der Systemcode des Konsolen Hosts teilt Verantwortlichkeiten und Berechtigungen mit der Eingabeaufforderung-Interpreter/Shell. Außerdem bietet es eine grundlegende Dienst Ebene für andere Befehlszeilen-Hilfsprogramme, um Dienste auf cmd-ähnliche Weise auszuführen.

### <a name="dbcs-for-cjk"></a>DBCS für cjk

**\[ 1997-1999 \]** zu diesem Zeitpunkt wird die [DBCS](https://docs.microsoft.com/windows/win32/intl/double-byte-character-sets) -Unterstützung ("Doppelbyte-Zeichensatz") eingeführt, um cjk-Märkte (Chinesisch, Japanisch und Koreanisch) zu unterstützen. Dieser Aufwand führt zu einer Vielzahl von Schreib-und Lesemethoden in der Konsole, um sowohl "westliche" Versionen als auch Einzel Byte-Zeichen und eine Alternative Darstellung für "Ost"-Versionen bereitzustellen, in denen zwei Bytes erforderlich sind, um das große Array von Zeichen darzustellen. Diese bizierung enthielt die erweiternde Darstellung einer Zelle in der Konsolen Umgebung, sodass Sie entweder 1 oder 2 Zellen breit ist, wobei 1 Zelle schmale (größer als breit ist) und 2 Zellen breit, vollständig oder anderweitig ein Quadrat ist, in dem typische chinesische, japanische und koreanische Ideographen eingefügt werden können.

### <a name="securityisolation"></a>Sicherheit/Isolation

**\[ 2005-2009 \]** mit dem Konsolen Subsystem, das innerhalb des kritischen System Prozesses ausgeführt wird, `csrss.exe` wurde das Verbinden von verschiedenen Client Anwendungen mit unterschiedlichen Zugriffsebenen zu einem einzigen, äußerst kritischen und privilegierten Prozess als besonders gefährlich festgestellt. In diesem Zeitraum wurde das Konsolen Subsystem in Client-, Treiber-und Server Anwendungen aufgeteilt. Jede Anwendung kann in einem eigenen Kontext ausgeführt werden, wodurch die Verantwortlichkeiten und Berechtigungen in den einzelnen Anwendungen verringert werden. Diese Isolation hat die allgemeine Stabilität des Systems gesteigert, da sich jeder Fehler im Konsolen Subsystem nicht mehr auf andere wichtige Prozessfunktionen auswirkt.

### <a name="user-experience-improvements"></a>Verbesserung der Benutzer Leistung

**\[ 2014-2016 \]** nachdem eine lange Zeit für die Verwaltung des Konsolen Subsystems durch verschiedene Teams in der Organisation festgestellt wurde, wurde ein neues Entwickler orientiertes Team erstellt, um Verbesserungen in der-Konsole zu verwalten und zu steigern. Zu den Verbesserungen während dieses Zeitraums zählen: Zeilenauswahl, Glättung von Fenstern im Fenster, Weiterleitungs Text, kopieren und einfügen, hohe dpi-Unterstützung und der Schwerpunkt auf Unicode, einschließlich der Konvergenz der Aufteilung zwischen "West"-und "Eastern"-Speicher und Stream-Manipulations Algorithmen.

### <a name="virtual-terminal-client"></a>Virtueller Terminal Client

**\[ 2015-2017 \]** mit der Ankunft des [Windows-Subsystems für Linux](https://docs.microsoft.com/windows/wsl/)versucht Microsoft, die Leistung von [docker unter Windows](https://docs.microsoft.com/dotnet/architecture/microservices/container-docker-introduction/docker-defined)zu verbessern, und die Übernahme von [OpenSSH](https://docs.microsoft.com/windows-server/administration/openssh/openssh_overview) als Premier-Befehlszeilen-Remote Ausführungs Technologie, die anfänglichen Implementierungen von [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md) wurden in den Konsolen Host eingeführt. Dadurch konnte die vorhandene Konsole als Terminal fungieren, direkt an diese Linux-systemeigenen Anwendungen in ihren jeweiligen Umgebungen angefügt werden, um die grafische und Text Attribute in die Anzeige zu rendern und die Benutzereingaben im entsprechenden Dialekt zurückzugeben.

### <a name="virtual-terminal-server"></a>Virtueller Terminal Server

**\[ 2018 \]** in den letzten 20 Jahren wurden Drittanbieter Alternativen für den Eingangsbox-Konsolen Host erstellt, um eine weitere Entwickler Produktivität zu bieten, die sich hervorgehoben in umfangreichen Anpassungen und Schnittstellen im Registerkarten Format befand. Diese Anwendungen müssen nach wie vor ausgeführt werden, um das Konsolen Host Fenster auszuführen und auszublenden. Sie werden als sekundäre "Client"-Anwendung angefügt, um Puffer Informationen in Abruf Schleifen zu verscheiften, wenn die primäre Befehlszeilen Client Anwendung ausgeführt wird. Ihr Ziel bestand darin, ein Terminal zu sein, z. b. auf anderen Plattformen, aber in der Windows-Welt, wo Terminals nicht ersetzbar waren.

In diesem Zeitraum wurde die [pseudoconsole](pseudoconsoles.md) -Infrastruktur eingeführt. Mit pseudoconsole können alle Anwendungen den Konsolen Host in einem nicht interaktiven Modus starten und die endgültige Terminal Schnittstelle des Benutzers werden. Die Haupteinschränkung bei diesem Aufwand war die fortgesetzte Kompatibilitäts Zusage von Windows bei der Wartung aller veröffentlichten [Windows-Konsolen-APIs](console-functions.md) für die unbestimmte Zeit, während gleichzeitig eine Ersatz-Server Host Schnittstelle bereitgestellt wird, die mit den Erwartungen auf allen anderen Plattformen übereinstimmte: [virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md). Daher hat dieser Aufwand das Spiegelbild der Client Phase durchgeführt: die _pseudoconsole_ -Projekte, die als _virtuelle Terminal Sequenzen_ für einen Delegierten Host auf dem Bildschirm angezeigt werden, und interpretieren Antworten auf Eingabe Sequenzen im Windows-Format für den Verbrauch von Client Anwendungen.

## <a name="roadmap-for-the-future"></a>Roadmap für die Zukunft

### <a name="terminal-applications"></a>Terminal Anwendungen

**\[ 2019-nun \]** ist dies der Open Source-Zeitraum für das Konsolen Subsystem, das sich auf das neue Windows-Terminal konzentriert. Das Windows-Terminal wurde während der Microsoft Build-Konferenz im Mai 2019 angekündigt und ist auf GitHub bei [Microsoft/Terminal](https://github.com/microsoft/terminal)verfügbar. Das Entwickeln der Windows-Terminal Anwendung, die auf der optimierten Plattform für [pseudoconsole](pseudoconsoles.md) aufbaut, ist der Schwerpunkt dieses Zeitraums und bietet Entwicklern auf der Windows-Plattform eine erstklassige Terminal-Oberfläche.

Das **[Windows-Terminal](/terminal/get-started)** soll nicht nur die Plattform vorstellen – einschließlich der [WinUI](/apps/winui/) -Schnittstellen Technologie, des [msix](/msix/) -Verpackungs Modells und der [C++/WinRT](/uwp/cpp-and-winrt-apis/) -Komponentenarchitektur – sondern auch die Überprüfung der Plattform selbst. Das Windows-Terminal treibt die Windows-Organisation an, die APP-Plattform nach Bedarf zu öffnen und weiterzuentwickeln, um die Produktivität von Entwicklern weiter zu steigern. Mit dem eindeutigen Windows-Terminal Satz von Poweruser-und Developer-Anforderungen werden die modernen Windows-Platt Form Anforderungen für die tatsächlich von Windows benötigten Anforderungen erfüllt.

Innerhalb des Windows-Betriebssystems umfasst dies das außer Kraft setzen [der Benutzeroberfläche des klassischen Konsolen Hosts](./classic-vs-vt.md) von der Standardposition aus zugunsten von [Windows-Terminal](/terminal/get-started)Sequenzen [,-Verbindungen und](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/) [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md).

Schließlich soll dieser Zeitraum eine vollständige Auswahl der Standardeinstellung bieten, egal, ob es sich um das Windows-Terminal Produkt oder um alternative Terminals handelt.

### <a name="client-support-library"></a>Client Unterstützungs Bibliothek

In **\[ Zukunft \]** mit der Unterstützung und Dokumentation von [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md) auf der Clientseite empfehlen wir den Entwicklern des Windows-Befehlszeilen Programms, virtuelle Terminal Sequenzen zunächst über die klassischen Windows-APIs zu verwenden, um den Vorteil eines vereinheitlichten Ökosystems mit allen Plattformen zu erhalten. Ein signifikanter fehlendes Element besteht jedoch darin, dass andere Plattformen über eine Vielzahl von Client seitigen Hilfsbibliotheken verfügen, um Eingaben wie z. b. die [Zeilen](https://tiswww.case.edu/php/chet/readline/rltop.html) -und Grafik Anzeige wie [ncurrses](https://invisible-island.net/ncurses/ncurses.html)zu verarbeiten. Dieses spezielle Road Map-Element stellt die Untersuchung der Möglichkeiten des Ökosystems dar und erläutert, wie wir die Übernahme virtueller Terminal Sequenzen in Windows-Befehlszeilen Anwendungen über die klassische Konsolen-API beschleunigen können.

### <a name="sequence-passthrough"></a>Sequenz Passthrough

In **\[ Zukunft \]** ermöglicht die Kombination aus virtuellen Terminal Client-und Server Implementierungen die vollständige Mischung und die Übereinstimmung von Client-Befehlszeilen-und terminalhostinganwendungen. Diese Kombination kann sowohl für die klassischen [Windows-Konsolen-APIs](console-functions.md) als auch für [virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md)sprechen. es fallen jedoch Kosten für die Übersetzung in die klassische kompatible Windows-Methode und dann zurück in die mehr universelle virtuelle Terminal Methode an.

Nachdem der Markt die _virtuellen Terminal Sequenzen_ und UTF-8 unter Windows ausreichend übernommen hat, kann die Konvertierung/Interpretation des Konsolen Hosts optional deaktiviert werden. Der Konsolen Host wird dann zu einem einfachen API-Aufruf Dienst, der über die [pseudoconsole](pseudoconsoles.md)von Geräte Aufrufen an die Host Anwendung übertragen wird. Diese Änderung erhöht die Leistung und maximiert den Dialekt von Sequenzen, die zwischen der Client Anwendung und dem Terminal gesprochen werden können. Durch diese Änderung werden weitere interaktivitätsszenarios aktiviert und *(schließlich)* die Windows-Welt in Einklang mit der Familie aller anderen Plattformen im Befehlszeilen-Anwendungsbereich gebracht.
