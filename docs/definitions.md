---
title: Windows-Konsolen-und Terminal Definitionen
description: Stellt Definitionen von Wörtern und Ausdrücken bereit, die in diesem Bereich häufig verwendet werden, und die auf die Konsole und das Terminal System bezogen werden.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Terminal, virtuelles Terminal, Konsolen Host, Befehlszeile, Subsystem, Definitionen
ms.prod: console
ms.openlocfilehash: 763421a25d5ecaa2291b68b0370644af152622a9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039620"
---
# <a name="definitions"></a>Definitionen

Dieses Dokument enthält die Definitionen bestimmter Wörter und Ausdrücke in diesem Bereich und wird in diesem Dokument Satz als Verweis verwendet.

## <a name="command-line-applications"></a>Befehlszeilen Anwendungen

Befehlszeilen Anwendungen, die auch als "Konsolen Anwendungen" bezeichnet werden und/oder als "Clients" des Konsolen Subsystems bezeichnet werden, sind Programme, die hauptsächlich in einem Stream von Text-oder Zeichen Informationen arbeiten. Sie enthalten in der Regel keine eigenen Benutzeroberflächen Elemente und delegieren sowohl die Ausgabe-/Anzeige-als auch die Eingabe-/interaktionsrollen an eine Hosting-Anwendung. Befehlszeilen Anwendungen empfangen einen Stream von Text in Ihrem Standardeingabe `STDIN` handle, der die Tastatureingabe eines Benutzers darstellt, diese Informationen verarbeitet und dann mit einem Stream von Text in der Standardausgabe antwortet, `STDOUT` damit Sie wieder im Benutzer Monitor angezeigt werden. Dies hat sich im Laufe der Zeit für zusätzliche Eingabegeräte und Remote Szenarien entwickelt, aber die gleiche grundlegende Philosophie bleibt unverändert: Befehlszeilen Clients arbeiten mit Text, und eine andere Person verwaltet die Anzeige/Eingabe.

## <a name="standard-handles"></a>Standard Handles

Die Standard Handles sind eine Reihe, `STDIN` , `STDOUT` und `STDERR` , die als Teil eines Prozess Raums beim Start eingeführt werden. Sie stellen einen Ort dar, an dem Informationen auf dem Weg akzeptiert und zurückgesendet werden (einschließlich eines speziellen Orts zum Melden von Fehlern). Bei Befehlszeilen Anwendungen müssen diese immer vorhanden sein, wenn die Anwendung gestartet wird. Sie werden entweder automatisch vom übergeordneten Element geerbt, explizit durch das übergeordnete Element festgelegt oder automatisch vom Betriebssystem erstellt, wenn weder angegeben noch zulässig. Bei klassischen Windows-Anwendungen sind diese beim Start möglicherweise leer. Allerdings können Sie von der Anwendung selbst implizit oder explizit vom übergeordneten Element geerbt oder zugewiesen, angefügt und freigegeben werden.

Standard Handles implizieren keinen bestimmten Typ von angehängtem Gerät. Im Fall von Befehlszeilen Anwendungen ist das Gerät jedoch am häufigsten ein Konsolen Gerät, eine Datei (von der Umleitung in einer Shell) oder eine Pipe (von einer Shell, die die Ausgabe eines Dienstprogramms mit der Eingabe der nächsten Verbindung verbindet). Möglicherweise handelt es sich auch um einen Socket oder einen beliebigen anderen Gerätetyp.

## <a name="ttypty"></a>TTY/Pty

Auf nicht-Windows-Plattformen stellen die TTY-und Pty-Geräte entweder ein echtes physisches Gerät oder ein von der Software erstelltes Pseudo Gerät dar, das das gleiche Konzept wie eine Windows-Konsolen Sitzung darstellt: ein Kanal, in dem die Kommunikation zwischen einer Befehlszeilen-Client Anwendung und einer interaktivierten Server Host Anwendung oder einem physischen Tastatur-und Anzeigegerät textbasierte Informationen austauschen kann

## <a name="clients-and-servers"></a>Clients und Server

Innerhalb dieses Raums verweisen wir auf "Clients" als Anwendungen, die die Verarbeitung von Informationen und das Ausführen von Befehlen durchführen. Die "Server"-Anwendungen sind diejenigen, die für die Benutzeroberfläche zuständig sind und Mitarbeiter sind, die Eingaben und Ausgaben für die Clients in Standardformulare übersetzen.

## <a name="console-subsystem"></a>Konsolen Subsystem

Dies ist ein catch-all-Begriff, der alle Module darstellt, die sich auf Konsolen-und Befehlszeilen Vorgänge auswirken. Er bezieht sich speziell auf ein Flag, das Teil des portablen ausführbaren Headers ist, der angibt, ob es sich bei der Start Anwendung entweder um eine Befehlszeilen-/Konsolen Anwendung handelt (und ob Sie über Standard Handles verfügen müssen) oder eine Windows-Anwendung (die Sie nicht benötigt).

Der Konsolen Host, die Befehlszeilen-Client Anwendungen, der Konsolentreiber, die API-Oberfläche der Konsole, die pseudoconsole-Infrastruktur, die Terminals, die Konfigurations Eigenschaften Blätter, die Mechanismen und Stub innerhalb des Prozess Lade Moduls sowie alle Hilfsprogramme im Zusammenhang mit der Funktionsweise dieser Formular Anwendungen werden als zu dieser Gruppe gehören.

## <a name="console-host"></a>Konsolen Host

Der Windows-Konsolen Host (oder) `conhost.exe` ist sowohl die Serveranwendung für alle Windows-Konsolen-APIs als auch die klassische Windows-Benutzeroberfläche für die Arbeit mit Befehlszeilen Anwendungen. Der gesamte Inhalt dieser Binärdatei, sowohl der API-Server als auch die Benutzeroberfläche, gehörte in der Vergangenheit zu Windows `csrss.exe` , einem kritischen System Prozess und wurde aus Sicherheits-und Isolations Gründen unterschieden. In Zukunft ist `conhost.exe` weiterhin für die Wartung und Übersetzung von API-aufrufen zuständig, aber die Benutzeroberflächen Komponenten sind für die Delegierung über eine Pseudo Konsole an ein Terminal vorgesehen.

## <a name="pseudoconsole"></a>Pseudoconsole

Dies ist die Windows-Simulation eines Pseudo Terminals oder "Pty" von anderen Plattformen. Es wird versucht, der allgemeinen Schnittstellen Philosophie von PTYs zu entsprechen und einen einfachen bidirektionalen Kanal der textbasierten Kommunikation bereitzustellen. Er ergänzt ihn jedoch unter Windows mit einer großen Kompatibilitätsschicht, um die Breite von Windows-Anwendungen zu übersetzen, die vor dieser Entwurfs Philosophie von der klassischen Konsolen-API-Oberfläche in die einfache Text Kanal-Kommunikationsform geschrieben wurden. Terminals können mithilfe der pseudoconsole den Besitz der Benutzeroberflächen Elemente vom Konsolen Host aus übernehmen, `conhost.exe` während Sie für die API-Wartung,-Übersetzung und-Kompatibilität zuständig sind.

## <a name="terminal"></a>Terminal

Ein Terminal ist das Benutzeroberflächen-und Interaktions Modul für eine Befehlszeilen Anwendung. Heute handelt es sich um eine Software Darstellung der in der Vergangenheit verwendeten physischen Geräte mit einem Anzeige Monitor, einer Tastatur und einem bidirektionalen seriellen Kommunikationskanal. Er ist dafür verantwortlich, Eingaben vom Benutzer in einer Vielzahl von Formularen zu erfassen, ihn zu übersetzen und zu codieren und alle speziellen Befehls Informationen in einen einzelnen Textstream zu übermitteln und ihn an den Pty zu senden, um die Übertragung an den `STDIN` Kanal der Befehlszeilen Client Anwendung zu übermitteln. Außerdem ist er für den Empfang von Informationen über den Pty verantwortlich, der aus dem Kanal einer Client Anwendung stammt `STDOUT` , alle besonderen Informationen in der Nutzlast decodiert, den gesamten Text und die zusätzlichen Befehle anordnen und diese grafisch dem Endbenutzer präsentieren.
