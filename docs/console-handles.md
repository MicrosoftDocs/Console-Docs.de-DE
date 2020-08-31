---
title: Konsolen Handles
description: Ein Konsolen Prozess verwendet Handles, um auf die Eingabe-und Bildschirm Puffer der Konsole zuzugreifen, einschließlich der Funktionen "getstdhandle", "kreatefile" oder "feateconsoleskreenbuffer".
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_handles'
- base.console\_handles
- consoles.console\_handles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: dc723046-b3e9-418a-b386-79be411e5ac8
ms.openlocfilehash: 50b1ca460818080461116df85bf51387c024df89
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059603"
---
# <a name="console-handles"></a>Konsolen Handles


Ein Konsolen Prozess verwendet Handles, um auf die Eingabe-und Bildschirm Puffer der Konsole zuzugreifen. Ein Prozess kann mit der [**getstdhandle**](getstdhandle.md)- [**, der**](https://msdn.microsoft.com/library/windows/desktop/aa363858)-oder der-Funktion oder der-Funktion von " [**kreateconsoleskreenbuffer**](createconsolescreenbuffer.md) " eines der folgenden Handles öffnen.

Die [**getstdhandle**](getstdhandle.md) -Funktion bietet einen Mechanismus zum Abrufen der Standardeingabe (stdin), Standardausgabe (stdout) und Standard fehlerhandles (stderr), die einem Prozess zugeordnet sind. Während der Konsolen Erstellung werden diese Handles vom System erstellt. Anfänglich ist stdin ein Handle für den Eingabepuffer der Konsole, und stdout und stderr sind Handles des aktiven Bildschirm Puffers der Konsole. Die [**setstdhandle**](setstdhandle.md) -Funktion kann jedoch die Standard Handles umleiten, indem das Handle, das stdin, stdout oder stderr zugeordnet ist, geändert wird. Da die Standard Handles des übergeordneten Elements von einem beliebigen untergeordneten Prozess geerbt werden, geben nachfolgende Aufrufe von **getstdhandle** das umgeleitete Handle zurück. Ein Handle, das von **getstdhandle** zurückgegeben wird, kann daher etwas anderes als Konsolen-e/a bezeichnen. Vor dem Erstellen eines untergeordneten Prozesses kann ein übergeordneter Prozess z. b. **setstdhandle** verwenden, um ein Pipehandle als stdin-Handle festzulegen, das vom untergeordneten Prozess geerbt wird. Wenn der untergeordnete Prozess **getstdhandle**aufruft, wird das Pipehandle abgerufen. Dies bedeutet, dass der übergeordnete Prozess die Standard Handles des untergeordneten Prozesses steuern kann. Die von **getstdhandle** zurückgegebenen Handles haben einen generischen \_ Lesevorgang | Generischer \_ Schreibzugriff, es sei denn, " **setstdhandle** " wurde verwendet, um das Standard Handle auf einen geringeren Zugriff festzulegen.

Der Wert der von [**getstdhandle**](getstdhandle.md) zurückgegebenen Handles ist nicht 0, 1 und 2, sodass die standardmäßigen vordefinierten streamkonstanten in stdio. h (stdin, stdout und stderr) nicht in Funktionen verwendet werden können, die ein Konsolen handle erfordern.

Die Funktion " [**deatefile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) " ermöglicht einem Prozess, ein Handle für den Eingabepuffer und den aktiven Bildschirm Puffer der Konsole zu erhalten, auch wenn stdin und stdout umgeleitet wurden. Wenn Sie ein Handle für den Eingabepuffer einer Konsole öffnen möchten, geben Sie den Wert von "$" in einem Aufrufen von " **kreatefile**" an. Geben Sie den Wert von "$" in einem aufzurufenden **Befehl an,** um ein Handle für den aktiven Bildschirm Puffer einer Konsole zu öffnen. Mit " **anatefile** " können Sie den Lese-/Schreibzugriff des Handles angeben, das zurückgegeben wird.

Die Funktion " [**kreateconsoleskreenbuffer**](createconsolescreenbuffer.md) " erstellt einen neuen Bildschirm Puffer und gibt ein Handle zurück. Dieses Handle kann in jeder Funktion verwendet werden, die ein Handle für die Konsolenausgabe akzeptiert. Der neue Bildschirm Puffer ist erst dann aktiv, wenn sein Handle in einem Aufrufen der [**setconsoleactiveskreenbuffer**](setconsoleactivescreenbuffer.md) -Funktion angegeben wird. Beachten Sie, dass sich das Ändern des aktiven Bildschirm Puffers nicht auf das von [**getstdhandle**](getstdhandle.md)zurückgegebene Handle auswirkt. Ebenso wirkt sich die Verwendung von [**setstdhandle**](setstdhandle.md) zum Ändern des stdout-Handles nicht auf den aktiven Bildschirm Puffer aus.

Konsolen Handles, die von " [**kreatefile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) " und " [**feateconsoleskreenbuffer**](createconsolescreenbuffer.md) " zurückgegeben werden, können in beliebigen Konsolenfunktionen verwendet werden, die ein Handle für den Eingabepuffer einer Konsole oder einen Konsolenbildschirm Puffer erfordern. Handles, die von [**getstdhandle**](getstdhandle.md) zurückgegeben werden, können von den Konsolenfunktionen verwendet werden, wenn Sie nicht umgeleitet wurden, um auf etwas anderes als Konsolen-e/a zu verweisen. Wenn ein Standard handle umgeleitet wurde, um auf eine Datei oder eine Pipe zu verweisen, kann das Handle jedoch nur von den Funktionen "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " verwendet werden.

Ein Prozess kann die [**duplikatandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) -Funktion verwenden, um ein doppeltes Konsolen Handle zu erstellen, das über einen anderen Zugriff oder eine andere Vererbbarkeit als das ursprüngliche Handle verfügt. Beachten Sie jedoch, dass ein Prozess ein doppeltes Konsolen Handle nur für die eigene Verwendung erstellen kann. Dies unterscheidet sich von anderen handle-Typen (z. b. Datei-, Pipe-oder Mutex-Objekte), für die **duplikatandle** ein Duplikat erstellen kann, das für einen anderen Prozess gültig ist.

Ein Prozess kann die [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) -Funktion verwenden, um ein Konsolen Handle zu schließen.

 

 




