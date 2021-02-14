---
title: Scrollen des Bildschirm Puffers
description: Beschreibt, wie das Konsolenfenster einen Teil des aktiven Bildschirm Puffers anzeigt.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_scrolling\_the\_screen\_buffer'
- base.scrolling\_the\_screen\_buffer
- consoles.scrolling\_the\_screen\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c8404e78-9807-4bed-bc12-25377fa96151
ms.openlocfilehash: 4c55a40f43827deeacfd1302d507732ec9bcc248
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358660"
---
# <a name="scrolling-the-screen-buffer"></a>Scrollen des Bildschirm Puffers

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Im Konsolenfenster wird ein Teil des aktiven Bildschirm Puffers angezeigt. Jeder Bildschirm Puffer verwaltet sein eigenes Aktuelles Fenster Rechteck, das die Koordinaten der oberen linken und der unteren rechten Zeichen Zelle angibt, die im Konsolenfenster angezeigt werden sollen. Verwenden Sie [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md), um das aktuelle Fenster Rechteck eines Bildschirm Puffers zu bestimmen. Wenn ein Bildschirm Puffer erstellt wird, befindet sich die obere linke Ecke des Fensters in der oberen linken Ecke des Konsolenbildschirm Puffers bei (0,0).

Das Fenster Rechteck kann geändert werden, um verschiedene Teile des Konsolenbildschirm Puffers anzuzeigen. Das Fenster Rechteck eines Bildschirm Puffers kann in den folgenden Situationen geändert werden:

- Wenn [**setconsolewindowinfo**](setconsolewindowinfo.md) zum Angeben eines neuen Fenster Rechtecks aufgerufen wird, wird die Position des Fenster Rechtecks durch Ändern der Position des Fenster Rechtecks durch Ändern der Fenstergröße geändert. Beispiele für den Bildlauf des Fenster Inhalts finden Sie unter Scrollen des Fensters [eines Bildschirm Puffers](scrolling-a-screen-buffer-s-window.md).

  ![Bildschirm Puffer Fenster, das um einen großen Pufferinhalt herum schwenken](images/cscon-01.png)

- Wenn Sie die Funktion " [**Write File**](/windows/win32/api/fileapi/nf-fileapi-writefile) " verwenden, um in einen Bildschirm Puffer zu schreiben, bei dem der EOL-Ausgabemodus (End-of-Line) aktiviert ist, wird das Fenster Rechteck automatisch verschoben, sodass der Cursor immer angezeigt wird.
- Wenn die [**SetConsoleCursorPosition**](setconsolecursorposition.md) -Funktion eine neue Cursorposition angibt, die sich außerhalb der Begrenzungen des aktuellen Fenster Rechtecks befindet, verschiebt sich das Fenster Rechteck automatisch, um den Cursor anzuzeigen.
- Wenn der Benutzer die Größe des Konsolenfensters ändert oder die Bild Lauf leisten des Fensters verwendet, kann sich das Fenster Rechteck des aktiven Bildschirm Puffers ändern. Diese Änderung wird im Eingabepuffer nicht als Fenster zum Ändern der Fenstergröße gemeldet.

In jeder dieser Situationen wechselt das Fenster Rechteck dahin, dass ein anderer Teil des Konsolenbildschirm Puffers angezeigt wird, aber der Inhalt des Konsolenbildschirm Puffers bleibt an derselben Position. Die folgenden Situationen können bewirken, dass der Inhalt des Konsolenbildschirm Puffers verschoben wird:

- Wenn die [**scrollconsoleskreenbuffer**](scrollconsolescreenbuffer.md) -Funktion aufgerufen wird, wird ein rechteckiger Block von einem Teil eines Bildschirm Puffers in einen anderen kopiert.
- Wenn Sie mithilfe von "Write [**File**](/windows/win32/api/fileapi/nf-fileapi-writefile) " in einen Bildschirm Puffer schreiben, bei dem der EOL-Ausgabemodus aktiviert ist, wird der Inhalt des Konsolenbildschirm Puffers automatisch durchlaufen, wenn das Ende des Konsolenbildschirm Puffers erreicht wird. Durch diesen Bildlauf wird die oberste Zeile des Konsolenbildschirm Puffers verworfen.

[**Scrollconsoleskreenbuffer**](scrollconsolescreenbuffer.md) gibt das Konsolenbildschirm-Puffer Rechteck an, das verschoben wird, und die neuen linken oberen Koordinaten, auf die das Rechteck kopiert wird. Diese Funktion kann einen Bildlauf für einen Teil oder den gesamten Inhalt des Konsolenbildschirm Puffers durchführen.

Die Abbildung zeigt einen [**scrollconsoleskreenbuffer**](scrollconsolescreenbuffer.md) -Vorgang, der den gesamten Inhalt des Konsolenbildschirm Puffers um mehrere Zeilen nach oben verschiebt. Der Inhalt der obersten Zeilen wird verworfen, und die untersten Zeilen werden mit einem angegebenen Zeichen und einer angegebenen Farbe gefüllt.

![Bildschirm-Puffer Fenster Bildlauf nach oben zum verwerfen](images/cscon-02.png)

Die Auswirkungen von [**scrollconsoleskreenbuffer**](scrollconsolescreenbuffer.md) können durch Angabe eines optionalen clippingrechtecks eingeschränkt werden, sodass der Inhalt des Konsolenbildschirm Puffers außerhalb des clippingrechtecks unverändert bleibt. Der Clipping-Effekt besteht darin, ein Unterfenster (das Clippingrechteck) zu erstellen, dessen Inhalt ohne Auswirkung auf den Rest des Konsolenbildschirm Puffers gescrollt wird. Ein Beispiel für die Verwendung von **scrollconsoleskreenbuffer** finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).