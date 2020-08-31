---
title: Eingabe-und Ausgabefunktionen auf hoher Ebene
description: Die Funktionen "Infofile" und "Write file" bzw. die Funktionen "Read Console" und "Write Console" ermöglichen einer Anwendung das Lesen von Konsolen Eingaben und das Schreiben der Konsolenausgabe als Zeichendaten Strom.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_high\_level\_console\_input\_and\_output\_functions'
- base.high\_level\_console\_input\_and\_output\_functions
- consoles.high\_level\_console\_input\_and\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 086b1bec-85f8-4e31-848d-7cb2d2703a3d
ms.openlocfilehash: d6e13edf9350fcff812ad02b2d9116c3fe132154
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059642"
---
# <a name="high-level-console-input-and-output-functions"></a>Eingabe-und Ausgabefunktionen auf hoher Ebene


Die Funktionen " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " bzw. die Funktionen "read [**Console**](readconsole.md) " und "Write [**Console**](writeconsole.md) " ermöglichen einer Anwendung das Lesen von Konsolen Eingaben und das Schreiben der Konsolenausgabe als Zeichendaten Strom. "Read **Console** " und " **Write-Console** " Verhalten sich genau wie "read **File** " und " **Write File** ", mit dem Unterschied, dass Sie entweder als breit Zeichenfunktionen (in denen Textargumente Unicode verwenden müssen) oder als ANSI-Funktionen verwendet werden können (in denen Textargumente Zeichen aus dem Windows-Zeichensatz verwenden müssen). Anwendungen, die einen einzelnen Satz von Quellen zur Unterstützung von Unicode oder ANSI-Zeichensatz verwalten müssen, sollten die Dateien "read **Console** " und " **Write-Console**" verwenden.

"Read [**Console**](readconsole.md) " und " [**Write-Console**](writeconsole.md) " können nur mit Konsolen Handles verwendet werden. " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " können mit anderen Handles (z. b. Dateien oder Pipes) verwendet werden. Bei Verwendung mit einem Standard handle, das umgeleitet und kein Konsolen handle mehr ist, tritt bei der Verwendung von "read **Console** " und " **Write-Console** " ein Fehler auf

Zum erhalten von Tastatureingaben kann ein Prozess " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder " [**infoconsole**](readconsole.md) " mit einem Handle für den Eingabepuffer der Konsole verwenden, oder er kann mithilfe von " **Infofile** " Eingaben aus einer Datei oder einer Pipe lesen, wenn stdin umgeleitet wurde. Diese Funktionen geben nur Tastatur Ereignisse zurück, die in ANSI-Zeichen (oder Unicode-Zeichen im Fall von "read **Console**") übersetzt werden können. Zu den Eingaben, die zurückgegeben werden können, gehören Tastenkombinationen. Die Funktionen geben keine Tastatur Ereignisse zurück, die die Funktionstasten oder Pfeiltasten betreffen. Eingabeereignisse, die von Maus, Fenster, Fokus oder menüeingabe generiert werden, werden verworfen.

Wenn der Zeilen Eingabemodus aktiviert ist (der Standardmodus), werden die [**Dateien**](https://msdn.microsoft.com/library/windows/desktop/aa365467) und die [**infoconsole**](readconsole.md) nicht an die aufrufende Anwendung zurückgegeben, bis die EINGABETASTE gedrückt wird. Wenn der Zeilen Eingabemodus deaktiviert ist, werden die Funktionen erst zurückgegeben, wenn mindestens ein Zeichen verfügbar ist. In beiden Modi werden alle verfügbaren Zeichen gelesen, bis entweder keine weiteren Schlüssel verfügbar sind oder die angegebene Anzahl von Zeichen gelesen wurde. Ungelesene Zeichen werden bis zum nächsten Lesevorgang gepuffert. Die Funktionen melden die Gesamtzahl der tatsächlich gelesenen Zeichen. Wenn der Echo-Eingabemodus aktiviert ist, werden von diesen Funktionen gelesene Zeichen an der aktuellen Cursorposition in den aktiven Bildschirm Puffer geschrieben.

Ein Prozess kann mithilfe von "Write [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder "Write- **Console** " entweder in einen aktiven oder inaktiven Bildschirm Puffer schreiben, oder es kann "Write **File** " verwenden, um in eine Datei oder eine Pipe zu schreiben, wenn "stdout" umgeleitet wurde. Verarbeiteter Ausgabemodus und Umbruch bei EOL-Ausgabemodus Steuern der Art und Weise, wie Zeichen in einen Bildschirm Puffer geschrieben oder wiederholt werden.

Von " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder " [**Write Console**](writeconsole.md)" geschriebene Zeichen, die von "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder " [**infoconsole**](readconsole.md)" zurückgegeben werden, werden an der aktuellen Cursorposition in einen Bildschirm Puffer eingefügt. Beim Schreiben jedes Zeichens wechselt die Cursorposition zur nächsten Zeichen Zelle. das Verhalten am Ende einer Zeile hängt jedoch vom Umbruch des Konsolenbildschirm Puffers im EOL-Ausgabemodus ab. Eine Anwendung kann die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion verwenden, um die aktuelle Cursorposition zu bestimmen, und die [**SetConsoleCursorPosition**](setconsolecursorposition.md) -Funktion, um die Cursorposition festzulegen.

Ein Beispiel, in dem die e/a-Funktionen auf hoher Ebene verwendet werden, finden [Sie unter Verwenden der übergeordneten Eingabe-und Ausgabefunktionen](using-the-high-level-input-and-output-functions.md).

 

 




