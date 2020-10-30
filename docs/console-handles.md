---
title: Konsolenhandles
description: Ein Konsolen Prozess verwendet Handles, um auf die Eingabe-und Bildschirm Puffer der Konsole zuzugreifen, einschließlich der Funktionen "getstdhandle", "kreatefile" oder "feateconsoleskreenbuffer".
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
ms.openlocfilehash: 29d25e83281c7c98c74ae4a0da03eea06dbf0077
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039228"
---
# <a name="console-handles"></a>Konsolenhandles

Ein Konsolen Prozess verwendet Handles, um auf die Eingabe-und Bildschirm Puffer der Konsole zuzugreifen. Ein Prozess kann mit der [**getstdhandle**](getstdhandle.md)- [**, der**](https://msdn.microsoft.com/library/windows/desktop/aa363858)-oder der-Funktion oder der-Funktion von " [**kreateconsoleskreenbuffer**](createconsolescreenbuffer.md) " eines der folgenden Handles öffnen.

Die [**getstdhandle**](getstdhandle.md) -Funktion bietet einen Mechanismus zum Abrufen der Standardeingabe ( `STDIN` ), der Standardausgabe ( `STDOUT` ) und der Standard-Fehler ( `STDERR` ) Handles, die einem Prozess zugeordnet sind. Während der Konsolen Erstellung werden diese Handles vom System erstellt. Anfänglich `STDIN` ist ein Handle für den Eingabepuffer der Konsole, und `STDOUT` und `STDERR` sind Handles des aktiven Bildschirm Puffers der Konsole. Die [**setstdhandle**](setstdhandle.md) -Funktion kann jedoch die Standard Handles umleiten, indem das Handle, das mit, oder verknüpft ist, geändert wird `STDIN` `STDOUT` `STDERR` . Da die Standard Handles des übergeordneten Elements von einem beliebigen untergeordneten Prozess geerbt werden, geben nachfolgende Aufrufe von **getstdhandle** das umgeleitete Handle zurück. Ein Handle, das von **getstdhandle** zurückgegeben wird, kann daher etwas anderes als Konsolen-e/a bezeichnen. Vor dem Erstellen eines untergeordneten Prozesses kann ein übergeordneter Prozess z. b. **setstdhandle** verwenden, um ein Pipehandle als Handle festzulegen, `STDIN` das vom untergeordneten Prozess geerbt wird. Wenn der untergeordnete Prozess **getstdhandle** aufruft, wird das Pipehandle abgerufen. Dies bedeutet, dass der übergeordnete Prozess die Standard Handles des untergeordneten Prozesses steuern kann. Die von **getstdhandle** zurückgegebenen Handles haben `GENERIC_READ | GENERIC_WRITE` Zugriff, wenn **setstdhandle** nicht zum Festlegen des Standard Handles für einen geringeren Zugriff verwendet wurde.

Der Wert der von [**getstdhandle**](getstdhandle.md) zurückgegebenen Handles ist nicht 0, 1 und 2, sodass die standardmäßigen vordefinierten streamkonstanten in stdio. h ( `STDIN` , `STDOUT` und `STDERR` ) nicht in Funktionen verwendet werden können, die ein Konsolen handle erfordern.

Die [**Funktion**](https://msdn.microsoft.com/library/windows/desktop/aa363858) "-Funktion" ermöglicht einem Prozess, ein Handle für den Eingabepuffer und den aktiven Bildschirm Puffer der Konsole zu erhalten, auch wenn `STDIN` und `STDOUT` umgeleitet wurden. Wenn Sie ein Handle für den Eingabepuffer einer Konsole öffnen möchten, geben Sie den `CONIN$` Wert in einem Aufrufen von " **anatefile** " an. Geben Sie `CONOUT$` **den** Wert in einem aufzurufenden Befehl an, um ein Handle für den aktiven Bildschirm Puffer einer Konsole zu öffnen. Mit " **anatefile** " können Sie den Lese-/Schreibzugriff des Handles angeben, das zurückgegeben wird.

Die Funktion " [**kreateconsoleskreenbuffer**](createconsolescreenbuffer.md) " erstellt einen neuen Bildschirm Puffer und gibt ein Handle zurück. Dieses Handle kann in jeder Funktion verwendet werden, die ein Handle für die Konsolenausgabe akzeptiert. Der neue Bildschirm Puffer ist nicht aktiv (angezeigt), bis sein Handle in einem Aufrufen der [**setconsoleactiveskreenbuffer**](setconsoleactivescreenbuffer.md) -Funktion angegeben wird. Beachten Sie, dass sich das Ändern des aktiven Bildschirm Puffers nicht auf das von [**getstdhandle**](getstdhandle.md)zurückgegebene Handle auswirkt. Ebenso wirkt sich die Verwendung von [**setstdhandle**](setstdhandle.md) zum Ändern des `STDOUT` Handles nicht auf den aktiven Bildschirm Puffer aus.

Konsolen Handles, die von " [**kreatefile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) " und " [**feateconsoleskreenbuffer**](createconsolescreenbuffer.md) " zurückgegeben werden, können in beliebigen Konsolenfunktionen verwendet werden, die ein Handle für den Eingabepuffer einer Konsole oder einen Konsolenbildschirm Puffer erfordern. Handles, die von [**getstdhandle**](getstdhandle.md) zurückgegeben werden, können von den Konsolenfunktionen verwendet werden, wenn Sie nicht umgeleitet wurden, um auf etwas anderes als Konsolen-e/a zu verweisen. Wenn ein Standard handle umgeleitet wurde, um auf eine Datei oder eine Pipe zu verweisen, kann das Handle jedoch nur von den Funktionen "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " verwendet werden. [**Getfiletype**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype) kann bei der Bestimmung des Gerätetyps helfen, auf den sich das Handle bezieht. Ein Konsolen Handle wird als dargestellt `FILE_TYPE_CHAR` .

Ein Prozess kann die [**duplikatandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) -Funktion verwenden, um ein doppeltes Konsolen Handle zu erstellen, das über einen anderen Zugriff oder eine andere Vererbbarkeit als das ursprüngliche Handle verfügt. Beachten Sie jedoch, dass ein Prozess ein doppeltes Konsolen Handle nur für die eigene Verwendung erstellen kann. Dies unterscheidet sich von anderen handle-Typen (z. b. Datei-, Pipe-oder Mutex-Objekte), für die **duplikatandle** ein Duplikat erstellen kann, das für einen anderen Prozess gültig ist.
Der Zugriff auf eine-Konsole muss während der [Erstellung](creation-of-a-console.md) des anderen Prozesses freigegeben werden, oder Sie kann vom anderen Prozess über den [**attachconsole**](attachconsole.md) -Mechanismus angefordert werden.

Ein Prozess kann die [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) -Funktion verwenden, um ein Konsolen Handle zu schließen.
