---
title: Konsolen Eingabepuffer
description: Jede Konsole verfügt über einen Eingabepuffer, der eine Warteschlange von Eingabe Ereignisdaten Sätzen enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_input\_buffer'
- base.console\_input\_buffer
- consoles.console\_input\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6e536658-8a27-478e-82ee-d1e11f351301
ms.openlocfilehash: 0a4843279b97da0ca6db50a9ccfa3de644044b68
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060091"
---
# <a name="console-input-buffer"></a>Konsolen Eingabepuffer


Jede Konsole verfügt über einen Eingabepuffer, der eine Warteschlange von Eingabe Ereignisdaten Sätzen enthält. Wenn das Fenster einer Konsole den Tastaturfokus besitzt, formatiert eine Konsole jedes Eingabe Ereignis (z. b. einen einzelnen Tastatur Strich, eine Bewegung der Maus oder einen Mausklick) als Eingabedaten Satz, der im Eingabepuffer der Konsole platziert wird.

Anwendungen können indirekt auf den Eingabepuffer einer Konsole zugreifen, indem Sie die e [/a-Funktionen auf hoher Ebene](high-level-console-input-and-output-functions.md)oder direkt mithilfe der [Konsolen Eingabefunktionen auf niedriger Ebene](low-level-console-input-functions.md)verwenden. Die Eingabefunktionen auf hoher Ebene filtern und verarbeiten die Daten im Eingabepuffer und geben nur einen Stream von Eingabezeichen zurück. Die Eingabefunktionen auf niedriger Ebene ermöglichen es Anwendungen, Eingabedaten Sätze direkt aus dem Eingabepuffer einer Konsole zu lesen oder Eingabedaten Sätze in den Eingabepuffer zu platzieren. Um ein Handle für den Eingabepuffer einer Konsole zu öffnen, geben Sie den Wert von " **$** " in einem aufrufen [**der Funktion "**](https://msdn.microsoft.com/library/windows/desktop/aa363858) Funktion" an.

Ein Eingabedaten Satz ist eine Struktur, die Informationen über den Typ des aufgetretenen Ereignisses (Tastatur, Maus, Fenstergröße, Fokus oder Menü Ereignis) sowie spezifische Details zum Ereignis enthält. Der **eventType** -Member in einer [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur gibt an, welcher Ereignistyp im Datensatz enthalten ist.

Fokus-und Menü Ereignisse werden für die interne Verwendung durch das System in den Eingabepuffer einer Konsole eingefügt und sollten von Anwendungen ignoriert werden.

## <a name="span-idkeyboard_eventsspanspan-idkeyboard_eventsspanspan-idkeyboard_eventsspankeyboard-events"></a><span id="Keyboard_Events"></span><span id="keyboard_events"></span><span id="KEYBOARD_EVENTS"></span>Tastatur Ereignisse


Tastatur Ereignisse werden generiert, wenn eine Taste gedrückt oder freigegeben wird. Dies schließt Steuerelement Schlüssel ein. Allerdings hat die Alt-Taste eine besondere Bedeutung für das System, wenn es gedrückt und freigegeben wird, ohne mit einem anderen Zeichen kombiniert zu werden, und es nicht an die Anwendung übermittelt wird. Außerdem wird die Tastenkombination STRG + C nicht durchlaufen, wenn sich das Eingabe Handle im verarbeiteten Modus befindet.

Wenn das Eingabe Ereignis eine Tastatureingabe ist, ist das **Ereignismember** im [**Eingabe \_ Daten Satz**](input-record-str.md) eine [**Key- \_ Ereignis \_ Daten Satz**](key-event-record-str.md) Struktur, die die folgenden Informationen enthält:

- Ein boolescher Wert, der angibt, ob der Schlüssel gedrückt oder freigegeben wurde.
- Eine Wiederholungs Anzahl, die größer als 1 sein kann, wenn eine Taste angehalten wird.
- Der Code des virtuellen Schlüssels, der den angegebenen Schlüssel Geräte unabhängig identifiziert.
- Der Code für die virtuelle Überprüfung, der den von der Tastatur Hardware generierten geräteabhängigen Wert angibt.
- Der übersetzte Unicode-™ oder ANSI-Zeichen.
- Eine Flagvariable, die den Zustand der Steuerelement Tasten (alt, STRG, Umschalttaste, num-Sperre, Scrollsperre und Feststell Taste) angibt und angibt, ob eine erweiterte Taste gedrückt wurde. Erweiterte Schlüssel für die Tastaturen IBM® 101-Key und 102-Key sind die Tastatur ins, del, Home, Ende, Bild-ab, nach-unten und Pfeiltasten in den Clustern links neben der numerischen Tastatur und die Unterteilung (/) und EINGABETASTE in der numerischen Tastatur.

## <a name="span-idmouse_eventsspanspan-idmouse_eventsspanspan-idmouse_eventsspanmouse-events"></a><span id="Mouse_Events"></span><span id="mouse_events"></span><span id="MOUSE_EVENTS"></span>Mausereignisse


Mausereignisse werden generiert, wenn der Benutzer die Maus bewegt oder eine der Maustasten drückt oder loslässt. Mausereignisse werden nur dann in den Eingabepuffer eingefügt, wenn die folgenden Bedingungen erfüllt sind:

- Der Konsolen Eingabemodus ist so festgelegt, dass ** \_ Maus \_ Eingaben** (Standardmodus) aktiviert werden.
- Das Konsolenfenster hat den Tastaturfokus.
- Der Mauszeiger befindet sich innerhalb der Rahmen des Konsolenfensters.

Wenn es sich bei dem Eingabe Ereignis um ein Maus Ereignis handelt, ist das **Ereignis** Element im [**Eingabe \_ Daten Satz**](input-record-str.md) eine Daten Satzstruktur mit [**Maus \_ Ereignissen \_ **](mouse-event-record-str.md) , die die folgenden Informationen enthält:

- Die Koordinaten des Mauszeigers in Bezug auf die Zeichen Zellen Zeile und-Spalte im Koordinatensystem des Konsolenbildschirm Puffers.
- Eine Flag-Variable, die den Zustand der Maustasten angibt.
- Eine Flag-Variable, die den Zustand der Steuerelement Tasten (alt, STRG, Umschalttaste, num-Sperre, Scrollsperre und Feststell Sperre) angibt und angibt, ob eine erweiterte Taste gedrückt wurde. Erweiterte Schlüssel für die Tastatur "IBM 101-Key" und "102-Key" sind die Tasten "ins", "del", "Start", "nach oben", "Bild-ab" und "Pfeiltasten" in den Clustern links neben der numerischen Tastatur und die "Division (/)" und "Eingabetaste".
- Eine Flagvariable, die angibt, ob es sich bei dem Ereignis um ein normales Schaltflächen-oder Schaltflächen Freigabe Ereignis, ein Maus Verschiebungs Ereignis oder den zweiten Klick eines Doppelklick Ereignisses handelt.

**Hinweis**    Die Maus Positionskoordinaten werden in Bezug auf den Bildschirm Puffer der Konsole, nicht im Konsolenfenster angezeigt. Möglicherweise wurde für den Bildschirm Puffer ein Bildlauf in Bezug auf das Fenster durchgeführt, sodass die linke obere Ecke des Fensters nicht notwendigerweise die Koordinate (0,0) des Konsolenbildschirm Puffers ist. Um die Koordinaten der Maus in Bezug auf das Koordinatensystem des Fensters zu ermitteln, subtrahieren Sie die Fenster Ursprungs Koordinaten von den Maus Positionskoordinaten. Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die Fenster Ursprungs Koordinaten zu bestimmen.

 

Der **dwbuttonstate** -Member der [** \_ \_ Daten Satzstruktur des Maus Ereignisses**](mouse-event-record-str.md) hat ein Bit, das jeder Maustaste entspricht. Das Bit ist 1, wenn die Schaltfläche nicht gedrückt ist, und 0, wenn die Schaltfläche aktiv ist. Ein Schaltflächen Freigabe Ereignis wird durch einen 0-Wert für den **dweventflags** -Member des **Maus \_ Ereignis \_ Datensatzes** und eine Änderung des Bits einer Schaltfläche von 1 bis 0 erkannt. Die [**getnumofconfiguration**](getnumberofconsolemousebuttons.md) Manager-Funktion Ruft die Anzahl der Schaltflächen auf der Maus ab.

## <a name="span-idbuffer-resizing_eventsspanspan-idbuffer-resizing_eventsspanspan-idbuffer-resizing_eventsspanbuffer-resizing-events"></a><span id="Buffer-Resizing_Events"></span><span id="buffer-resizing_events"></span><span id="BUFFER-RESIZING_EVENTS"></span>Puffer-ändern der Größe von Ereignissen


Das Menü eines Konsolenfensters ermöglicht dem Benutzer das Ändern der Größe des aktiven Bildschirm Puffers. Diese Änderung generiert ein Ereignis mit Puffergröße. Ereignisse zur Puffergröße werden im Eingabepuffer platziert, wenn der Eingabemodus der Konsole auf ** \_ Fenster \_ Eingabe aktivieren** festgelegt ist (d. h., der Standardmodus ist deaktiviert).

Handelt es sich bei dem Eingabe Ereignis um ein Puffergrößen Änderung-Ereignis, ist das **Ereignis** Element des [**Eingabe \_ Datensatzes**](input-record-str.md) eine [** \_ \_ \_ Daten Satzstruktur der Fensterpuffer Größe**](window-buffer-size-record-str.md) , die die neue Größe des Konsolenbildschirm Puffers in Zeichen Zellen Spalten und-Zeilen enthält.

Wenn der Benutzer die Größe des Bildschirm Puffers der Konsole reduziert, gehen alle Daten im verworfenen Teil des Puffers verloren.

Änderungen an der Größe des Konsolenbildschirm Puffers als Ergebnis von Anwendungs Aufrufen der Funktion [**setconsoleskreenbuffersize**](setconsolescreenbuffersize.md) werden nicht als Ereignisse für die Puffergrößen Änderung generiert.

 

 




