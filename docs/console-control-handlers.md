---
title: Konsolen-Bearbeitungssteuerelemente
description: Jeder Konsolen Prozess verfügt über eine eigene Liste von Steuerelement-Handlerfunktionen, die vom System aufgerufen werden, wenn der Prozess das Signal STRG + C, Strg + Pause oder STRG + schließen empfängt.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_control\_handlers'
- base.console\_control\_handlers
- consoles.console\_control\_handlers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6480e8ee-d228-4c07-99df-de1e0c3ca250
ms.openlocfilehash: 06528cfc93d074bd0cc2579d5ba50445025a04fb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358140"
---
# <a name="console-control-handlers"></a>Konsolen-Bearbeitungssteuerelemente

Jeder Konsolen Prozess verfügt über eine eigene Liste von Steuerelement-Handlerfunktionen, die vom System aufgerufen werden, wenn der Prozess das Signal [STRG + C](ctrl-c-and-ctrl-break-signals.md), [Strg + Pause](ctrl-c-and-ctrl-break-signals.md)oder [STRG + schließen](ctrl-close-signal.md) empfängt. Anfänglich enthält die Liste der Steuerelement Handler für jeden Prozess nur eine Standardhandlerfunktion, die die [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) -Funktion aufruft. Ein Konsolen Prozess kann zusätzliche [**Handlerroutine**](handlerroutine.md) -Funktionen hinzufügen oder entfernen, indem er die [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion aufruft. Diese Funktion hat keine Auswirkung auf die Listen von Steuerelement Handlern für andere Prozesse. Wenn ein Konsolen Prozess eines der Steuersignale empfängt, ruft er die Handlerfunktionen für eine zuletzt registrierte, erste Methode auf, bis einer der Handler " **true**" zurückgibt. Wenn keiner der Handler **true** zurückgibt, wird der Standard Handler aufgerufen.

Der *dwctrltype* -Parameter der Funktion identifiziert, welches Steuerungs Signal empfangen wurde, und der Rückgabewert gibt an, ob das Signal behandelt wurde.

Im Befehlszeilen Client-Prozess wird ein neuer Thread gestartet, um die Handlerroutinen auszuführen. Weitere Informationen zu den Timeout Werten und Aktionen dieses Threads finden Sie in der [**Handlerroutine**](handlerroutine.md#remarks) -Funktions Dokumentation.

Ein Beispiel für eine steuerungshandlerfunktion finden Sie unter [Registrieren einer Steuerelement Handler-Funktion](registering-a-control-handler-function.md).