---
title: Tastenkombination STRG + C und Strg + Pause
description: Die Tastenkombinationen STRG + C und STRG + Break werden von Konsolen Prozessen besonders behandelt.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.localizationpriority: high
ms.openlocfilehash: 38cc3486a9e945635147c2e17a4d2f0d197d1d3c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420189"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a>Tastenkombination STRG + C und Strg + Pause

Die <kbd>CTRL</kbd> + Tastenkombinationen STRG<kbd>C</kbd> und <kbd>STRG</kbd> + <kbd>BREAK</kbd> -Taste werden von Konsolen Prozessen besonders behandelt. Wenn ein Konsolenfenster den Tastaturfokus besitzt, wird <kbd>STRG</kbd> + <kbd>C</kbd> oder <kbd>STRG</kbd>-Taste standardmäßig + <kbd>BREAK</kbd> als Signal (SIGINT oder sigbreak) und nicht als Tastatureingabe behandelt. Standardmäßig werden diese Signale an alle Konsolen Prozesse übermittelt, die an die Konsole angefügt sind. (Getrennte Prozesse sind nicht betroffen. Weitere Informationen finden Sie [**unter Erstellen einer-Konsole**](creation-of-a-console.md).) Das System erstellt in jedem Client Prozess einen neuen Thread, um das Ereignis zu behandeln. Der Thread löst eine Ausnahme aus, wenn der Prozess gedebuggt wird. Der Debugger kann die Ausnahme verarbeiten oder mit der Ausnahme fortfahren, die nicht behandelt wird.

<kbd>STRG</kbd> + <kbd>Break</kbd> wird immer als Signal behandelt, aber eine Anwendung kann das Standardverhalten von <kbd>STRG</kbd> + <kbd>C</kbd> auf zwei Arten ändern, die das Aufrufen der Handlerfunktionen verhindern:

- Die [**setconsolemode**](setconsolemode.md) -Funktion kann den **Aktivierungs Modus für \_ verarbeitete \_ Eingaben** für den Eingabepuffer einer Konsole deaktivieren, sodass STRG + C als Tastatureingabe und nicht als Signal gemeldet wird.
- Wenn [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) mit **null** -und **true** -Werten für die zugehörigen Parameter aufgerufen wird, ignoriert der aufrufende Prozess STRG + C-Signale. Die normale STRG + C-Verarbeitung wird durch Aufrufen von **SetConsoleCtrlHandler** mit **null** -Werten und **false** -Werten wieder hergestellt. Dieses Attribut, bei dem STRG + C-Signale ignoriert oder nicht ignoriert werden, wird von untergeordneten Prozessen geerbt, kann jedoch von einem beliebigen Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse beeinträchtigt werden.

Weitere Informationen zur Verarbeitung dieser Signale, einschließlich Timeouts, finden Sie in der [**Handlerroutine**](handlerroutine.md) -Rückruf Dokumentation.
