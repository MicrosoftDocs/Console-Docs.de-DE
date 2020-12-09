---
title: Roadmap für die Windows-Konsole und das Terminalökosystem
description: Bietet eine allgemeine Übersicht über die Interaktionen zwischen dem Windows-Konsolenhost, Konsolen-APIs, dem Konsolensubsystem und dem Terminal-Produkt sowie über Pläne für diese.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Terminal, virtuelles Terminal, Konsolenhost, Befehlszeile, Subsystem, Roadmap, Ökosystem
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: e5d28a06789f230943d70a49e7c89642b17fdb5c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420259"
---
# <a name="windows-console-and-terminal-ecosystem-roadmap"></a>Roadmap für die Windows-Konsole und das Terminalökosystem

Dieses Dokument ist eine allgemeine Roadmap der Produkte Windows-Konsole und Windows-Terminal. Folgendes wird behandelt:


- Einordnung der Position von Windows-Konsole und Windows-Terminal im Ökosystem der Befehlszeilenanwendungen in Windows und anderen Betriebssystemen.

- Roadmap der vergangenen und zukünftigen Entwicklung der Produkte, Funktionen und Strategien, die Bestandteil bei der Konstruktion der Plattform sowie beim Entwickeln für diese Plattform sind.

Der Schwerpunkt der aktuellen Konsolen-/Terminal-Ära bei Microsoft besteht darin, Entwicklern auf der Windows-Plattform unmittelbar eine erstklassige Terminalerfahrung zu verschaffen und klassische Windows-Konsolen-APIs [auslaufen zu lassen](classic-vs-vt.md) und diese unter Verwendung von [Pseudokonsolen](pseudoconsoles.md) durch [virtuelle Terminalsequenzen](console-virtual-terminal-sequences.md) zu ersetzen. **[Windows-Terminal](/terminal/get-started)** ist ein gutes Beispiel für diesen Übergang zu einer erstklassigen Erfahrung, der [Open-Source-Zusammenarbeit](https://github.com/microsoft/terminal) aus der Entwicklercommunity fördert, das vollständige Spektrum an Kombinations- und Abgleichmöglichkeiten für Clientbefehlszeilen- und Terminalhostinganwendungen unterstützt sowie das Windows-Ökosystem mit allen anderen Plattformen vereinheitlicht.

## <a name="definitions"></a>Definitionen

Es wird empfohlen, sich mit den [Definitionen](definitions.md) der in diesem Bereich verwendeten gängigen Terminologie vertraut zu machen, bevor Sie fortfahren. Die gängige Terminologie umfasst unter anderem: [Befehlszeilen- oder Konsolenanwendungen](definitions.md#command-line-applications), [Standardhandles (`STDIN`, `STDOUT`, `STDERR`)](definitions.md#standard-handles), [TTY- und PTY-Geräte](definitions.md#ttypty), [Clients und Server](definitions.md#clients-and-servers), [Konsolensubsystem](definitions.md#console-subsystem), [Konsolenhost](definitions.md#console-host), [Pseudokonsole](definitions.md#pseudoconsole)und [Terminal](definitions.md#terminal).

## <a name="architecture"></a>Aufbau

Die allgemeine Architektur des Systems besteht aus vier Teilen: Client, Gerät, Server und Terminal.

![Flussdiagramm der Befehlszeilenkommunikation von der Quelle zum Ziel, vom Client zum Gerät zum Server zum Terminal](images/command-line-communication.png)

### <a name="client"></a>Client

Der Client ist eine Befehlszeilenanwendung, die eine textbasierte Oberfläche verwendet, um dem Benutzer die Eingabe von Befehlen zu ermöglichen (anstelle einer mausbasierten Benutzeroberfläche), die eine Textdarstellung des Ergebnisses zurückgibt. Unter Windows stellt die Konsolen-API eine Kommunikationsschicht zwischen dem Client und dem Gerät bereit. (Dies kann auch ein Standardkonsolenhandle mit Gerätesteuerungs-APIs sein.)

### <a name="device"></a>Sicherungsmedium

Das Gerät ist eine Kommunikationszwischenschicht für die Nachrichtenverarbeitung zwischen zwei Prozessen, dem Client und dem Server. Unter Windows ist dies der Konsolentreiber. Auf anderen Plattformen ist dies das TTY-oder PTY-Gerät. Andere Geräte wie Dateien, Pipes und Sockets können auch als dieser Kommunikationskanal verwendet werden, wenn die gesamte Transaktion als reiner Text stattfindet oder [virtuelle Terminalsequenzen](console-virtual-terminal-sequences.md) enthält, aber nicht mit [Windows-Konsolen-APIs](console-functions.md).

### <a name="server"></a>Server

Der Server interpretiert die angeforderten API-Aufrufe oder Nachrichten vom Client. Unter Windows im klassischen Betriebsmodus erstellt der Server auch eine Benutzeroberfläche, um die Ausgabe auf dem Bildschirm anzuzeigen. Der Server erfasst zusätzlich Eingaben, um über den Treiber Nachrichten als Antwort an den Client zurückzusenden, wie ein im selben Modul gebündeltes Terminal. Bei Verwendung des [Pseudokonsolen](pseudoconsoles.md)modus handelt es sich stattdessen nur um einen Übersetzer, der diese Informationen als [virtuelle Terminalsequenzen](console-virtual-terminal-sequences.md) einem angeschlossenen Terminal präsentiert.

### <a name="terminal"></a>Terminal

Das Terminal ist die letzte Schicht, die dem Benutzer grafische Anzeige- und Interaktivitätsdienste bereitstellt. Es ist für die Erfassung von Eingaben und deren Codierung als [virtuelle Terminalsequenzen](console-virtual-terminal-sequences.md) verantwortlich, die schließlich das `STDIN`-Handle des Clients erreichen. Es empfängt und decodiert außerdem die *virtuellen Terminalsequenzen*, die es umgekehrt vom `STDOUT`-Handle des Clients für die Darstellung auf dem Bildschirm empfängt.

#### <a name="further-connections"></a>Weitere Verbindungen

Ergänzend können weitere Verbindungen hergestellt werden, indem Anwendungen, die mehrere Rollen erfüllen, zu einem der Endpunkte verkettet werden. Beispielsweise verfügt eine SSH-Sitzung über zwei Rollen: Sie ist ein **Terminal** für die Befehlszeilenanwendung, die auf einem Gerät ausgeführt wird, leitet aber alle empfangenen Informationen an eine **Client** rolle auf einem anderen Gerät weiter. Diese Verkettung kann unendlich über Geräte und Kontexte hinweg erfolgen, was große Flexibilität hinsichtlich der möglichen Szenarien bietet.

Auf Nicht-Windows-Plattformen sind die **Server**- und **Terminal** rollen eine einzige Einheit, weil zwischen einem API-Satz und den [virtuellen Terminalsequenzen](console-virtual-terminal-sequences.md) keine Übersetzungskompatibilitätsschicht erforderlich ist.

## <a name="microsoft-products"></a>Microsoft-Produkte

Alle Microsoft Windows-Befehlszeilenprodukte sind nun auf GitHub in einem Open-Source-Repository namens [microsoft/terminal](https://github.com/microsoft/terminal) verfügbar.

### <a name="windows-console-host"></a>Windows-Konsolenhost

Dies ist die herkömmliche Windows-Benutzeroberfläche für Befehlszeilenanwendungen. Er verarbeitet alle Konsolen-API-Versorgungsanforderungen, die von allen angefügten Befehlszeilenanwendungen aufgerufen werden. In der Windows-Konsole wird auch die Darstellung der grafischen Benutzeroberfläche (GUI) im Auftrag aller dieser Anwendungen behandelt. Sie befindet sich im Systemverzeichnis als `conhost.exe` oder `openconsole.exe` in ihrer Open-Source-Ausführung. Sie ist im Lieferumfang des Windows-Betriebssystems enthalten. Sie finden sie auch in anderen Microsoft-Produkten, die aus dem Open-Source-Repository erstellt wurden, um eine aktuellere Implementierung der [Pseudokonsolen](pseudoconsoles.md)infrastruktur zu erhalten. Gemäß den oben aufgeführten Definitionen funktioniert sie entweder in einer kombinierten Server-/Terminalrolle oder in einer reinen Serverrolle über die bevorzugte _Pseudokonsolen_ infrastruktur.

### <a name="windows-terminal"></a>Windows-Terminal

Dies ist die neue Windows-Oberfläche für Befehlszeilenanwendungen. Das Windows-Terminal fungiert als Erstanbieterbeispiel für die Verwendung der [Pseudokonsole](pseudoconsoles.md), um die Zuständigkeiten zwischen der API-Versorgung und der textbasierten Anwendungsschnittstellen-Anbindung zu trennen, ähnlich wie bei allen Nicht-Windows-Plattformen.


Windows-Terminal ist das Flaggschiff der Textmodus-Benutzeroberflächen für Windows. Es veranschaulicht die Funktionen des Ökosystems und treibt die Windows-Entwicklung in Richtung Vereinheitlichung mit anderen Plattformen voran. Das Windows-Terminal ist außerdem ein Beispiel dafür, wie man eine robuste und komplexe moderne Anwendung erstellt, die die Historie und das gesamte Spektrum von Windows-APIs und -Frameworks umfasst. Gemäß den oben aufgeführten Definitionen wird dieses Produkt in einer Terminalrolle betrieben.

## <a name="major-historical-milestones"></a>Wichtige historische Meilensteine

Die wichtigsten historischen Meilensteine für das Konsolensubsystem gliedern sich in die Implementierung vor 2014 und fahren dann mit einer Übersicht der seit 2014 geleisteten Arbeit fort, wo sich in der Windows 10-Ära der neuerliche Schwerpunkt auf der Befehlszeile gebildet hat.

### <a name="initial-implementation"></a>Erste Implementierung

**\[1989–1990er Jahre]** Das ursprüngliche Konsolenhostsystem wurde als Emulation der DOS-Umgebung innerhalb des Windows-Betriebssystems implementiert. Sein Code ist verflochten und kooperiert mit der [Eingabeaufforderung](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) (`cmd.exe`), die eine Repräsentation dieser DOS-Umgebung ist. Der Systemcode des Konsolenhosts teilt sich Verantwortlichkeiten und Berechtigungen mit dem/der Eingabeaufforderungs-Interpreter/-Shell. Er bietet außerdem eine grundlegende Diensteschicht für andere Befehlszeilen-Hilfsprogramme, um Dienste in einer CMD-ähnlichen Weise auszuführen.

### <a name="dbcs-for-cjk"></a>DBCS für CJK

**\[1997–1999\]** Zu diesem Zeitpunkt wird [DBCS](https://docs.microsoft.com/windows/win32/intl/double-byte-character-sets)-Unterstützung („Doppelbyte-Zeichensatz“) eingeführt, um CJK-Märkte (Chinesisch, Japanisch und Koreanisch) zu unterstützen. Diese Anstrengung führt zu einer Zweiteilung zahlreicher Schreib- und Lesemethoden in der Konsole, um sowohl „westliche“ Versionen für die Verarbeitung von Einzelbytezeichen als auch eine Alternativdarstellung für „östliche“ Versionen bereitzustellen, bei denen zwei Bytes erforderlich sind, um deren umfangreichen Zeichensatz darzustellen. Diese Zweiteilung beinhaltete die erweiternde Darstellung einer Zelle in der Konsolenumgebung auf eine Breite von entweder 1 oder 2 Zellen, wobei 1 Zelle schmal (höher als breit) und 2 Zellen breit (volle Breite) oder anderweitig ein Quadrat sind, in dem typische chinesische, japanische und koreanische Ideogramme eingetragen werden können.

### <a name="securityisolation"></a>Sicherheit/Isolation

**\[2005–2009\]** Die Konsolensubsystem-Erfahrung, die innerhalb des kritischen Systemprozesses (`csrss.exe`) ausgeführt wird und verschiedene Clientanwendungen auf unterschiedlichen Zugriffsebenen zu einem einzigen, äußerst kritischen und privilegierten Prozess verbindet, wurde als besonders gefährlich erkannt. In dieser Ära wurde das Konsolensubsystem in Client-, Treiber- und Serveranwendungen aufgeteilt. Jede Anwendung konnte in ihrem eigenen Kontext ausgeführt werden, wodurch die jeweiligen Verantwortlichkeiten und Berechtigungen verringert wurden. Diese Isolation erhöhte die allgemeine Stabilität des Systems, da sich kein Fehler im Konsolensubsystem mehr auf andere kritische Prozessfunktionen auswirkte.

### <a name="user-experience-improvements"></a>Verbesserungen der Benutzererfahrung

**\[2014–2016\]** Nach einem längeren Zeitraum generell sporadischer Wartung des Konsolensubsystems durch verschiedene Teams aus der gesamten Organisation wurde ein neues, entwicklerorientiertes Team erstellt, das dediziert für Verbesserungen an der Konsole verantwortlich sein sollte. Zu den Verbesserungen während dieses Zeitraums zählten: Zeilenauswahl, übergangslose Anpassung der Fenstergröße, Neuanordnen von Text, Kopieren und Einfügen, Unterstützung für hohe DPI und ein Schwerpunkt auf Unicode, einschließlich der Konvergenz der Zweiteilung zwischen „westlichen“ und „östlichen“ Speicher- sowie Streammanipulationsalgorithmen.

### <a name="virtual-terminal-client"></a>Virtueller Terminalclient

**\[2015–2017\]** Mit der Ankunft des [Windows-Subsystems für Linux](https://docs.microsoft.com/windows/wsl/), Microsofts Anstrengungen zur Verbesserung der Erfahrung von [Docker unter Windows](https://docs.microsoft.com/dotnet/architecture/microservices/container-docker-introduction/docker-defined) und der Einführung von [OpenSSH](https://docs.microsoft.com/windows-server/administration/openssh/openssh_overview) als bedeutendster Remoteausführungstechnologie für Befehlszeilen wurden die ersten Implementierungen von [virtuellen Terminalsequenzen](console-virtual-terminal-sequences.md) in den Konsolenhost eingeführt. Dadurch konnte die vorhandene Konsole als Terminal fungieren, direkt an diese nativen Linux-Anwendungen in ihrer jeweiligen Umgebung angeschlossen, und dabei die Grafik- und Textattribute an der Anzeige rendern und Benutzereingaben im geeigneten Dialekt zurückgeben.

### <a name="virtual-terminal-server"></a>Virtueller Terminalserver

**\[2018\]** In den letzten 20 Jahren wurden Drittanbieteralternativen für den produktinternen Konsolenhost erstellt, um zusätzliche Entwicklerproduktivität zu bieten, die sich insbesondere auf funktionsreiche Anpassungen und Schnittstellen im Registerkartenformat konzentrierten. Diese Anwendungen mussten nach wie vor ausgeführt werden und das Konsolenhostfenster ausblenden. Sie werden als sekundäre „Client“anwendung angefügt, um Pufferinformationen in Abrufschleifen zu gewinnen, während die primäre Befehlszeilen-Clientanwendung ausgeführt wurde. Ihr Ziel war es, ein Terminal zu sein, wie auf anderen Plattformen, außer in der Windows-Welt, wo Terminals nicht ersetzbar waren.

In diesem Zeitraum wurde die [Pseudokonsolen](pseudoconsoles.md)infrastruktur eingeführt. Mit der Pseudokonsole können alle Anwendungen den Konsolenhost in einem nicht interaktiven Modus starten und zur letzten Terminalschnittstelle des Benutzers werden. Die Haupteinschränkung dabei war die fortgesetzte Kompatibilitätszusage seitens Windows zur Versorgung aller veröffentlichten [Windows-Konsolen-APIs](console-functions.md) auf unbestimmte Zeit bei gleichzeitiger Bereitstellung einer Serverhost-Ersatzschnittstelle, die die auf allen anderen Plattformen gehegten Erwartungen erfüllte: [virtuelle Terminalsequenzen](console-virtual-terminal-sequences.md). Eigentlich bildete dieser Vorgang das Spiegelbild der Clientphase: Die _Pseudokonsole_ projiziert, was auf dem Bildschirm als _virtuelle Terminalsequenzen_ für einen delegierten Host angezeigt werden sollte, und interpretiert Antworten in Eingabesequenzen im Windows-Format für die Nutzung durch Clientanwendungen.

## <a name="roadmap-for-the-future"></a>Roadmap der Zukunft

### <a name="terminal-applications"></a>Terminalanwendungen

**\[2019–Heute\]** Dies ist die Open-Source-Ära für das Konsolensubsystem, die sich auf neue Windows-Terminal konzentriert. Angekündigt während der Microsoft Build-Konferenz im Mai 2019, ist Windows-Terminal vollständig auf GitHub unter [microsoft/terminal](https://github.com/microsoft/terminal) zu finden. Der Fokus dieser Ära wird auf der Entwicklung der Windows-Terminalanwendung auf Basis der optimierten Plattform für die [Pseudokonsole](pseudoconsoles.md) liegen und Entwicklern auf der Windows-Plattform direkt eine erstklassige Terminalerfahrung bereitstellen.

**[Windows-Terminal](/terminal/get-started)** soll nicht nur die Plattform vorstellen – einschließlich der [WinUI](/apps/winui/)-Schnittstellentechnologie, des [MSIX](/msix/)-Verpackungsmodells und der [C++/WinRT](/uwp/cpp-and-winrt-apis/)-Komponentenarchitektur – sondern auch die Plattform selbst validieren. Windows-Terminal treibt die Windows-Organisation an, die App-Plattform nach Bedarf zu öffnen und weiterzuentwickeln, um die Produktivität von Entwicklern weiter zu steigern. Mit dem einzigartigen Satz von Poweruser- und Entwickleranforderungen treibt Windows-Terminal die modernen Windows-Plattformanforderungen in die Richtung, die diese Märkte wirklich von Windows brauchen.

Innerhalb des Windows-Betriebssystems umfasst dies das [Einstellen der klassischen Benutzeroberfläche des Konsolenhosts](./classic-vs-vt.md) zugunsten von [Windows-Terminal](/terminal/get-started), [ConPTY](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/) und [virtuellen Terminalsequenzen](console-virtual-terminal-sequences.md).

Schließlich soll diese Ära die vollständige Auswahlmöglichkeit für die Standarderfahrung bieten, egal, ob es sich um das Windows-Terminalprodukt oder um alternative Terminals handelt.

### <a name="client-support-library"></a>Clientunterstützungsbibliothek

**\[Zukunft\]** Mit der Unterstützung und Dokumentation der [virtuellen Terminalsequenzen](console-virtual-terminal-sequences.md) auf Clientseite empfehlen wir Entwicklern von Hilfsprogrammen für die Windows-Befehlszeilen dringend, bevorzugt virtuelle Terminalsequenzen gegenüber den klassischen Windows-APIs zu verwenden, um die Vorteile eines einheitlichen Ökosystems mit allen Plattformen nutzen zu können. Ein signifikantes Stück, das fehlt, ist jedoch, dass andere Plattformen über eine breite Vielzahl von clientseitigen Hilfsbibliotheken verfügen, um Eingaben wie [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) und grafische Anzeigen wie [ncurses](https://invisible-island.net/ncurses/ncurses.html) zu verarbeiten. Dieses spezifische Roadmapelement stellt die Erforschung dessen dar, was das Ökosystem zu bieten hat und wie wir die Einführung virtueller Terminalsequenzen in Windows-Befehlszeilenanwendungen anstelle der klassischen Konsolen-API beschleunigen können.

### <a name="sequence-passthrough"></a>Sequenz-Passthrough

**\[Zukunft\]** Die Kombination aus Implementierungen virtueller Terminalclients und -server gestattet sämtliche Kombinations- und Abgleichmöglichkeiten zwischen Client-Befehlszeilen- und Terminalhostinganwendungen. Diese Kombination kann entweder mit den klassischen [Windows-Konsolen-APIs](console-functions.md) oder den [virtuellen Terminalsequenzen](console-virtual-terminal-sequences.md) kommunizieren, wobei es jedoch einen zusätzlichen Aufwand bedeutet, diese erst in die klassische kompatible Windows-Methode und dann wieder zurück in die universellere virtuelle Terminalmethode zu übersetzen.

Sobald der Markt _virtuelle Terminalsequenzen_ und UTF-8 unter Windows ausreichend angenommen hat, kann der Konvertierungs-/Interpretationsauftrag des Konsolenhosts optional deaktiviert werden. Der Konsolenhost würde dann ein einfacher Versorger von API-Aufrufen sowie ein Relay von Geräteaufrufen an die Hostinganwendung über die [Pseudokonsole](pseudoconsoles.md) werden. Diese Änderung wird die Leistung erhöhen und die Dialekte von Sequenzen maximieren, die zwischen der Clientanwendung und dem Terminal gesprochen werden können. Durch diese Änderung würden weitere Interaktivitätsszenarios ermöglicht und *(schließlich)* die Windows-Welt in Einklang mit der Familie aller anderen Plattformen im Bereich der Befehlszeilenanwendungen gebracht.
