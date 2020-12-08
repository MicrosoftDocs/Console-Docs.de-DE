---
title: STRG+C- und STRG+UNTBR-Signale
description: Die Tastenkombinationen STRG+C und STRG+UNTBR werden von Konsolenprozessen besonders behandelt.
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420189"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a>STRG+C- und STRG+UNTBR-Signale

Die Tastenkombinationen <kbd>STRG</kbd>+<kbd>C</kbd> und <kbd>STRG</kbd>+<kbd>UNTBR</kbd> werden von Konsolenprozessen besonders behandelt. Wenn ein Konsolenfenster den Tastaturfokus besitzt, wird <kbd>STRG</kbd>+<kbd>C</kbd> oder <kbd>STRG</kbd>+<kbd>UNTBR</kbd> standardmäßig als Signal (SIGINT oder SIGBREAK) und nicht als Tastatureingabe behandelt. Standardmäßig werden diese Signale an alle Konsolenprozesse übermittelt, die an die Konsole angefügt sind. (Getrennte Prozesse sind nicht betroffen. Siehe [**Erstellung einer Konsole**](creation-of-a-console.md).) Das System erstellt in jedem Clientprozess einen neuen Thread, um das Ereignis zu behandeln. Der Thread löst eine Ausnahme aus, wenn der Prozess debuggt wird. Der Debugger kann die Ausnahme verarbeiten oder fortfahren, ohne die Ausnahme zu behandeln.

<kbd>STRG</kbd>+<kbd>UNTBR</kbd> wird immer als Signal behandelt, aber eine Anwendung kann das Standardverhalten für <kbd>STRG</kbd>+<kbd>C</kbd> auf zwei Arten ändern, mit denen verhindert wird, dass die Handlerfunktionen aufgerufen werden:

- Die [**SetConsoleMode**](setconsolemode.md)-Funktion kann den Eingabemodus **ENABLE\_PROCESSED\_INPUT** für den Eingabepuffer einer Konsole aktivieren, sodass STRG+C als Tastatureingabe anstatt als Signal gemeldet wird.
- Wenn [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) mit **NULL**- und **TRUE**-Werten für seine Parameter aufgerufen wird, ignoriert der aufrufende Prozess STRG+C-Signale. Die normale STRG+C-Verarbeitung wird durch Aufrufen von **SetConsoleCtrlHandler** mit **NULL**- und **FALSE**-Werten wiederhergestellt. Dieses Attribut, mit dem STRG+C-Signale ignoriert oder nicht ignoriert werden, wird von untergeordneten Prozessen geerbt, kann jedoch von jedem Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse davon betroffen sind.

Weitere Informationen zur Verarbeitung dieser Signale, einschließlich Timeouts, finden Sie in der [**Handlerroutine**](handlerroutine.md)-Rückrufdokumentation.
