---
ms.openlocfilehash: ca6de914ff9199090e96e2c813a176fcc90df27d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357278"
---
Eine Konsole besteht aus einem Eingabepuffer und einem oder mehreren Bildschirmpuffern. Der Modus eines Konsolenpuffers bestimmt, wie sich die Konsole bei Eingabe- oder Ausgabevorgängen (E/A) verhält. Ein Satz von Flag-Konstanten wird mit Eingabehandles und ein weiterer Satz mit Bildschirmpufferhandles (Ausgabehandles) verwendet. Das Festlegen der Ausgabemodi eines Bildschirmpuffers wirkt sich nicht auf die Ausgabemodi anderer Bildschirmpuffer aus.

Die Modi **ENABLE\_LINE\_INPUT** und **ENABLE\_ECHO\_INPUT** betreffen nur Prozesse, die zum Lesen aus dem Eingabepuffer der Konsole [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) oder [**ReadConsole**](../readconsole.md) verwenden. In ähnlicher Weise wirkt sich der Modus **ENABLE\_PROCESSED\_INPUT** primär auf Benutzer von **ReadFile** und **ReadConsole** aus, mit der Ausnahme, dass er auch bestimmt, ob CTRL+C-Eingaben im Eingabepuffer gemeldet (um von der Funktion [**ReadConsoleInput**](../readconsoleinput.md) gelesen zu werden) oder an eine von der Anwendung definierte Funktion übergeben werden.

Die Modi **ENABLE\_WINDOW\_INPUT** und **ENABLE\_MOUSE\_INPUT** bestimmen, ob Benutzerinteraktionen mit Fenstergrößenänderung und Mausaktionen im Eingabepuffer gemeldet oder verworfen werden. Diese Ereignisse können von [**ReadConsoleInput**](../readconsoleinput.md) gelesen werden, aber sie werden von [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) und [**ReadConsole**](../readconsole.md) immer gefiltert.

Die Modi **ENABLE\_PROCESSED\_OUTPUT** und **ENABLE\_WRAP\_AT\_EOL\_OUTPUT** betreffen nur Prozesse, die [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) oder [**ReadConsole**](../readconsole.md) und [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) oder [**WriteConsole**](../writeconsole.md) verwenden.