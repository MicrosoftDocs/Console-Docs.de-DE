---
ms.openlocfilehash: eaaaa3487e8f2aa95915f6f10724bf4c26784622
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "93038873"
---
Eine Konsole besteht aus einem Eingabepuffer und einem oder mehreren Bildschirmpuffern. Der Modus eines Konsolenpuffers bestimmt, wie sich die Konsole bei Eingabe- oder Ausgabevorgängen (E/A) verhält. Ein Satz von Flag-Konstanten wird mit Eingabehandles und ein weiterer Satz mit Bildschirmpufferhandles (Ausgabehandles) verwendet. Das Festlegen der Ausgabemodi eines Bildschirmpuffers wirkt sich nicht auf die Ausgabemodi anderer Bildschirmpuffer aus.

Die Modi **ENABLE\_LINE\_INPUT** und **ENABLE\_ECHO\_INPUT** betreffen nur Prozesse, die zum Lesen aus dem Eingabepuffer der Konsole [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) oder [**ReadConsole**](../readconsole.md) verwenden. In ähnlicher Weise wirkt sich der Modus **ENABLE\_PROCESSED\_INPUT** primär auf Benutzer von **ReadFile** und **ReadConsole** aus, mit der Ausnahme, dass er auch bestimmt, ob CTRL+C-Eingaben im Eingabepuffer gemeldet (um von der Funktion [**ReadConsoleInput**](../readconsoleinput.md) gelesen zu werden) oder an eine von der Anwendung definierte Funktion übergeben werden.

Die Modi **ENABLE\_WINDOW\_INPUT** und **ENABLE\_MOUSE\_INPUT** bestimmen, ob Benutzerinteraktionen mit Fenstergrößenänderung und Mausaktionen im Eingabepuffer gemeldet oder verworfen werden. Diese Ereignisse können von [**ReadConsoleInput**](../readconsoleinput.md) gelesen werden, aber sie werden von [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) und [**ReadConsole**](../readconsole.md) immer gefiltert.

Die Modi **ENABLE\_PROCESSED\_OUTPUT** und **ENABLE\_WRAP\_AT\_EOL\_OUTPUT** betreffen nur Prozesse, die [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) oder [**ReadConsole**](../readconsole.md) und [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) oder [**WriteConsole**](../writeconsole.md) verwenden.
