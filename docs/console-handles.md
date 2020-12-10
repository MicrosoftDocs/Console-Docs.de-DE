---
title: Konsolenhandles
description: Ein Konsolenprozess verwendet Handles, um auf die Eingabe- und Bildschirmpuffer seiner Konsole zuzugreifen, einschließlich der GetStdHandle-, CreateFile- und CreateConsoleScreenBuffer-Funktionen.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_handles'
- base.console\_handles
- consoles.console\_handles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: dc723046-b3e9-418a-b386-79be411e5ac8
ms.localizationpriority: high
ms.openlocfilehash: acc7d65e15451fc2804dc1782644c1ccbaa30e28
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420239"
---
# <a name="console-handles"></a>Konsolenhandles

Ein Konsolenprozess verwendet Handles, um auf die Eingabe- und Bildschirmpuffer seiner Konsole zuzugreifen. Ein Prozess kann die Funktion [**GetStdHandle**](getstdhandle.md), [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) oder [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) verwenden, um eins dieser Handles zu öffnen.

Die [**GetStdHandle**](getstdhandle.md)-Funktion bietet einen Mechanismus zum Abrufen der Standardeingabe- (`STDIN`), Standardausgabe- (`STDOUT`) und Standardfehlerhandles (`STDERR`), die einem Prozess zugeordnet sind. Das System erstellt diese Handles während der Konsolenerstellung. Zu Anfang ist `STDIN` ein Handle zum Eingabepuffer der Konsole, und `STDOUT` und `STDERR` sind Handles des aktiven Bildschirmpuffers der Konsole. Die Funktion [**SetStdHandle**](setstdhandle.md) kann die Standardhandles jedoch umleiten, indem sie das `STDIN`, `STDOUT` oder `STDERR` zugeordnete Handle ändert. Da die Standardhandles des übergeordneten Elements von einem beliebigen untergeordneten Prozess geerbt werden, geben nachfolgende Aufrufe von **GetStdHandle** das umgeleitete Handle zurück. Ein von **GetStdHandle** zurückgegebenes Handle kann daher auf etwas anderes als Konsolen-E/A verweisen. Beispielsweise kann ein übergeordneter Prozess vor dem Erstellen eines untergeordneten Prozesses **SetStdHandle** verwenden, um ein Pipehandle als das `STDIN`-Handle festzulegen, das vom untergeordneten Prozess geerbt wird. Wenn der untergeordnete Prozess **GetStdHandle** aufruft, erhält er das Pipehandle. Dies bedeutet, dass der übergeordnete Prozess die Standardhandles des untergeordneten Prozesses kontrollieren kann. Die von **GetStdHandle** zurückgegebenen Handles verfügen über `GENERIC_READ | GENERIC_WRITE`-Zugriff, es sei denn, **SetStdHandle** wurde verwendet, um für das Standardhandle geringere Zugriffsrechte festzulegen.

Die Werte der von [**GetStdHandle**](getstdhandle.md) zurückgegebenen Handles sind nicht 0, 1 und 2, daher können die vordefinierten Standard-Streamkonstanten in Stdio.h (`STDIN`, `STDOUT` und `STDERR`) nicht in Funktionen verwendet werden, die ein Konsolenhandle erfordern.

Die [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)-Funktion ermöglicht es einem Prozess, ein Handle zum Eingabepuffer und dem aktiven Bildschirmpuffer seiner Konsole abzurufen, selbst wenn `STDIN` und `STDOUT` umgeleitet wurden. Geben Sie den `CONIN$`-Wert in einem Aufruf von **CreateFile** an, um ein Handle zum Eingabepuffer einer Konsole zu öffnen. Geben Sie den `CONOUT$`-Wert in einem Aufruf von **CreateFile** an, um ein Handle zum aktiven Bildschirmpuffer einer Konsole zu öffnen. Mithilfe von **CreateFile** können Sie den Lese-/Schreibzugriff des von der Funktion zurückgegebenen Handles angeben.

Die Funktion [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) erstellt einen neuen Bildschirmpuffer und gibt ein Handle zurück. Dieses Handle kann in jeder Funktion verwendet werden, die ein Handle zur Konsolenausgabe akzeptiert. Der neue Bildschirmpuffer ist nicht aktiv (wird nicht angezeigt), bis sein Handle in einem Aufruf der Funktion [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) angegeben wird. Beachten Sie, dass ein Wechsel des aktiven Bildschirmpuffers sich nicht auf das von [**GetStdHandle**](getstdhandle.md) zurückgegebene Handle auswirkt. Analog dazu wirkt sich die Verwendung von [**SetStdHandle**](setstdhandle.md) zum Ändern des `STDOUT`-Handles nicht auf den aktiven Bildschirmpuffer aus.

Die von [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) und [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) zurückgegebenen Konsolenhandles können in jeder der Konsolenfunktionen verwendet werden, die ein Handle zum Eingabepuffer oder dem Bildschirmpuffer einer Konsole erfordern. Handles, die von [**GetStdHandle**](getstdhandle.md) zurückgegeben werden, können von den Konsolenfunktionen verwendet werden, wenn sie nicht umgeleitet wurden, um auf etwas anderes als die Konsolen-E/A zu verweisen. Wenn ein Standardhandle jedoch umgeleitet wurde, um auf eine Datei oder eine Pipe zu verweisen, kann das Handle nur von den [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)- und [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)-Funktionen verwendet werden. [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype) kann verwendet werden, um den Gerätetyp zu bestimmen, auf den das Handle verweist. Ein Konsolenhandle wird als `FILE_TYPE_CHAR` dargestellt.

Ein Prozess kann die [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251)-Funktion verwenden, um ein Duplikat eines Konsolenhandles zu erstellen, das gegenüber dem ursprünglichen Handle abweichende Zugriffsrechte oder eine andere Vererbung aufweist. Beachten Sie aber, dass ein Prozess ein Duplikat eines Konsolenhandles nur für den eigenen Gebrauch erstellen kann. Dieses Verhalten unterscheidet sich von anderen Handletypen (etwa für Datei-, Pipe- oder Mutexobjekte), für die **DuplicateHandle** ein Duplikat erstellen kann, das für andere Prozesse gültig ist.
Der Zugriff auf eine Konsole muss während der [Erstellung](creation-of-a-console.md) des anderen Prozesse freigegeben werden oder von dem anderen Prozess mithilfe des [**AttachConsole**](attachconsole.md)-Mechanismus angefordert werden.

Zum Schließen eines Konsolenhandles kann ein Prozess die [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211)-Funktion verwenden.
