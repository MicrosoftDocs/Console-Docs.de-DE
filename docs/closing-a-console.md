---
title: Schließen einer Konsole
description: Ein Prozess kann die freeconsole-Funktion verwenden, um sich von seiner Konsole zu trennen.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_closing\_a\_console'
- base.closing\_a\_console
- consoles.closing\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 254b7cfc-4dee-452f-a409-4fc90d20d4c1
ms.openlocfilehash: bdd6b98f96f4ecb64aa6750396c30ef2dd6d0f74
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060178"
---
# <a name="closing-a-console"></a><span data-ttu-id="ee0fd-104">Schließen einer Konsole</span><span class="sxs-lookup"><span data-stu-id="ee0fd-104">Closing a Console</span></span>


<span data-ttu-id="ee0fd-105">Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich von seiner Konsole zu trennen.</span><span class="sxs-lookup"><span data-stu-id="ee0fd-105">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="ee0fd-106">Wenn andere Prozesse die-Konsole gemeinsam nutzen, wird die Konsole nicht zerstört, aber der Prozess, der **freeconsole** aufgerufen hat, kann nicht darauf verweisen.</span><span class="sxs-lookup"><span data-stu-id="ee0fd-106">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="ee0fd-107">Nachdem **freeconsole**aufgerufen wurde, kann der Prozess mithilfe von " [**Zuweisung**](allocconsole.md) " eine neue Konsole oder eine anfügekonsole zum Anfügen an eine andere Konsole erstellen. [**AttachConsole**](attachconsole.md)</span><span class="sxs-lookup"><span data-stu-id="ee0fd-107">After calling **FreeConsole**, the process can use [**AllocConsole**](allocconsole.md) to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="ee0fd-108">Eine Konsole wird geschlossen, wenn der letzte daran angefügte Prozess beendet wird oder [**freeconsole**](freeconsole.md)aufruft.</span><span class="sxs-lookup"><span data-stu-id="ee0fd-108">A console is closed when the last process attached to it terminates or calls [**FreeConsole**](freeconsole.md).</span></span>

 

 




