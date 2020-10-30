---
ms.openlocfilehash: eaaaa3487e8f2aa95915f6f10724bf4c26784622
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038873"
---
Eine-Konsole besteht aus einem Eingabepuffer und mindestens einem Bildschirm Puffer. Der Modus eines Konsolen Puffers bestimmt, wie sich die Konsole bei Eingabe-oder Ausgabe Vorgängen verhält. Ein Satz von flagkonstanten wird mit Eingabe Handles verwendet, und ein anderer Satz wird mit Bildschirm Puffer (Ausgabe) Handles verwendet. Das Festlegen der Ausgabe Modi eines Bildschirm Puffers wirkt sich nicht auf die Ausgabe Modi anderer Bildschirm Puffer aus.

Das **aktivieren \_ von Zeilen \_ Eingaben** und **Aktivieren von \_ Echo \_ Eingabe** Modi wirkt sich nur auf Prozesse aus, bei denen die [**Datei**](https://msdn.microsoft.com/library/windows/desktop/aa365467) oder die Schreib [**Konsole**](../readconsole.md) zum Lesen aus dem Eingabepuffer der Konsole verwendet wird. Ebenso wirkt sich der **aktivierten \_ \_ Eingabe** Modus in erster Linie auf die Benutzer " **Infofile** " und " **infoconsole** " aus, mit der Ausnahme, dass Sie auch bestimmt, ob die STRG + C-Eingabe im Eingabepuffer (von der Funktion "read [**ConsoleInput**](../readconsoleinput.md) ") gemeldet wird oder an eine von der Anwendung definierte Funktion weitergeleitet wird.

Die **Modi \_ Fenster \_ Eingabe aktivieren** und **\_ Maus \_ Eingabe aktivieren** legen fest, ob Benutzerinteraktionen mit Fenstergröße und Mausaktionen im Eingabepuffer gemeldet oder verworfen werden. Diese Ereignisse können von " [**infoconsoleinput**](../readconsoleinput.md)" gelesen werden, Sie werden jedoch immer nach " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**infoconsole**](../readconsole.md)" gefiltert.

Die Ausgabe Modi " **\_ verarbeitete \_ Ausgabe aktivieren** " und " **\_ Wrap \_ in \_ EOL \_ aktivieren** " wirken sich nur auf die Prozesse aus, die "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](../readconsole.md) " und [**"Write-**](../writeconsole.md) [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) "
