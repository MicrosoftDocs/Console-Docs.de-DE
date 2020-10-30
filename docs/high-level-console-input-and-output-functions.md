---
title: High-Level Konsolen-Eingabe-und-Ausgabefunktionen
description: Die Funktionen "Infofile" und "Write file" bzw. die Funktionen "Read Console" und "Write Console" ermöglichen einer Anwendung das Lesen von Konsolen Eingaben und das Schreiben der Konsolenausgabe als Zeichendaten Strom.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_high\_level\_console\_input\_and\_output\_functions'
- base.high\_level\_console\_input\_and\_output\_functions
- consoles.high\_level\_console\_input\_and\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 086b1bec-85f8-4e31-848d-7cb2d2703a3d
ms.openlocfilehash: 4849426195fa9cc2455d27e4b711e89558b6e93c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037738"
---
# <a name="high-level-console-input-and-output-functions"></a>High-Level Konsolen-Eingabe-und-Ausgabefunktionen

Die Funktionen " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " bzw. die Funktionen "read [**Console**](readconsole.md) " und "Write [**Console**](writeconsole.md) " ermöglichen einer Anwendung das Lesen von Konsolen Eingaben und das Schreiben der Konsolenausgabe als Zeichendaten Strom. "Read **Console** " und " **Write-Console** " Verhalten sich genau wie "read **File** " und " **Write File** ", mit dem Unterschied, dass Sie entweder als breit Zeichenfunktionen (in denen Textargumente Unicode verwenden müssen) oder als ANSI-Funktionen verwendet werden können (in denen Textargumente Zeichen aus dem Windows-Zeichensatz verwenden müssen). Anwendungen, die einen einzelnen Satz von Quellen zur Unterstützung von Unicode oder ANSI-Zeichensatz verwalten müssen, sollten die Dateien "read **Console** " und " **Write-Console** " verwenden.

"Read [**Console**](readconsole.md) " und " [**Write-Console**](writeconsole.md) " können nur mit Konsolen Handles verwendet werden. " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " können mit anderen Handles (z. b. Dateien oder Pipes) verwendet werden. Bei Verwendung mit einem Standard handle, das umgeleitet und kein Konsolen handle mehr ist, tritt bei der Verwendung von "read **Console** " und " **Write-Console** " ein Fehler auf

Um Tastatureingaben zu erhalten, kann ein Prozess " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder " [**infoconsole**](readconsole.md) " mit einem Handle für den Eingabepuffer der Konsole verwenden, oder er kann mithilfe von " **Infofile** " Eingaben aus einer Datei oder einer Pipe lesen, wenn `STDIN` umgeleitet wurde. Diese Funktionen geben nur Tastatur Ereignisse zurück, die in ANSI-oder Unicode-Zeichen übersetzt werden können. Zu den Eingaben, die zurückgegeben werden können, gehören Tastenkombinationen. Die Funktionen geben keine Tastatur Ereignisse zurück, die die Funktionstasten oder Pfeiltasten betreffen. Eingabeereignisse, die von Maus, Fenster, Fokus oder menüeingabe generiert werden, werden verworfen.

Wenn der Zeilen Eingabemodus aktiviert ist (der Standardmodus), werden die [**Dateien**](https://msdn.microsoft.com/library/windows/desktop/aa365467) und die [**infoconsole**](readconsole.md) nicht an die aufrufende Anwendung zurückgegeben, bis die EINGABETASTE gedrückt wird. Wenn der Zeilen Eingabemodus deaktiviert ist, werden die Funktionen erst zurückgegeben, wenn mindestens ein Zeichen verfügbar ist. In beiden Modi werden alle verfügbaren Zeichen gelesen, bis entweder keine weiteren Schlüssel verfügbar sind oder die angegebene Anzahl von Zeichen gelesen wurde. Ungelesene Zeichen werden bis zum nächsten Lesevorgang gepuffert. Die Funktionen melden die Gesamtzahl der tatsächlich gelesenen Zeichen. Wenn der Echo-Eingabemodus aktiviert ist, werden von diesen Funktionen gelesene Zeichen an der aktuellen Cursorposition in den aktiven Bildschirm Puffer geschrieben.

Ein Prozess kann mithilfe von "Write [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder "Write- **Console** " entweder in einen aktiven oder inaktiven Bildschirm Puffer schreiben, oder es kann "Write **File** " verwenden, um in eine Datei oder eine Pipe zu schreiben, wenn "stdout" umgeleitet wurde. Verarbeiteter Ausgabemodus und Umbruch bei EOL-Ausgabemodus Steuern der Art und Weise, wie Zeichen in einen Bildschirm Puffer geschrieben oder wiederholt werden.

Von " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder " [**Write Console**](writeconsole.md)" geschriebene Zeichen, die von "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder " [**infoconsole**](readconsole.md)" zurückgegeben werden, werden an der aktuellen Cursorposition in einen Bildschirm Puffer eingefügt. Beim Schreiben jedes Zeichens wechselt die Cursorposition zur nächsten Zeichen Zelle. das Verhalten am Ende einer Zeile hängt jedoch vom Umbruch des Konsolenbildschirm Puffers im EOL-Ausgabemodus ab.

Weitere Details zur Position des Cursors finden Sie über **[virtuelle terminalsequenzen](console-virtual-terminal-sequences.md)** , insbesondere in der **[Abfrage Zustands](console-virtual-terminal-sequences.md#query-state)** Kategorie zum Suchen der aktuellen Position und der **[Cursor Positionierungs](console-virtual-terminal-sequences.md#cursor-positioning)** Kategorie zum Festlegen der aktuellen Position. Alternativ kann eine Anwendung die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion verwenden, um die aktuelle Cursorposition zu bestimmen, und die [**SetConsoleCursorPosition**](setconsolecursorposition.md) -Funktion, um die Cursorposition festzulegen. Der Mechanismus für **virtuelle Terminal Sequenzen** wird jedoch für alle neuen und laufenden Entwicklungen bevorzugt. Weitere Informationen zu der Strategie, die dieser Entscheidung zugrunde liegt, finden Sie in der Dokumentation zu **[klassischen Funktionen im Vergleich zum virtuellen Terminal](classic-vs-vt.md)** und zur **[Ökosystem-Roadmap](ecosystem-roadmap.md)** .

Ein Beispiel, in dem die e/a-Funktionen auf hoher Ebene verwendet werden, finden [Sie unter Verwenden der High-Level Eingabe-und Ausgabefunktionen](using-the-high-level-input-and-output-functions.md).
