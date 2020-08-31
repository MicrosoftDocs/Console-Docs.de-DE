---
title: Tastenkombination STRG + C und Strg + Pause
description: Die Tastenkombinationen STRG + C und STRG + Break werden von Konsolen Prozessen besonders behandelt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.openlocfilehash: 95e28c9d390e9edb0be7dcac5aa4600224ab118c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059891"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a>Tastenkombination STRG + C und Strg + Pause


Die Tastenkombinationen STRG + C und STRG + Break werden von Konsolen Prozessen besonders behandelt. Wenn ein Konsolenfenster den Tastaturfokus besitzt, wird standardmäßig STRG + C oder STRG + UNTBR als Signal (SIGINT oder sigbreak) und nicht als Tastatureingabe behandelt. Standardmäßig werden diese Signale an alle Konsolen Prozesse übermittelt, die an die Konsole angefügt sind. (Getrennte Prozesse sind nicht betroffen.) Das System erstellt in jedem Client Prozess einen neuen Thread, um das Ereignis zu behandeln. Der Thread löst eine Ausnahme aus, wenn der Prozess gedebuggt wird. Der Debugger kann die Ausnahme verarbeiten oder mit der Ausnahme fortfahren, die nicht behandelt wird.

STRG + UNTBR wird immer als Signal behandelt, aber eine Anwendung kann das Standardverhalten von STRG + C auf zwei Arten ändern, mit denen verhindert wird, dass die Handlerfunktionen aufgerufen werden:

- Die [**setconsolemode**](setconsolemode.md) -Funktion kann den **Aktivierungs Modus für \_ verarbeitete \_ Eingaben** für den Eingabepuffer einer Konsole deaktivieren, sodass STRG + C als Tastatureingabe und nicht als Signal gemeldet wird.
- Wenn [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) mit **null** -und **true** -Werten für die zugehörigen Parameter aufgerufen wird, ignoriert der aufrufende Prozess STRG + C-Signale. Die normale STRG + C-Verarbeitung wird durch Aufrufen von **SetConsoleCtrlHandler** mit **null** -Werten und **false** -Werten wieder hergestellt. Dieses Attribut, bei dem STRG + C-Signale ignoriert oder nicht ignoriert werden, wird von untergeordneten Prozessen geerbt, kann jedoch von einem beliebigen Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse beeinträchtigt werden.

 

 




