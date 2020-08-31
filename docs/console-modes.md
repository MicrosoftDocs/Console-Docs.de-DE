---
title: Konsolen Modi
description: Jedem Konsolen Eingabepuffer ist ein Satz von Eingabemodi zugeordnet, der sich auf Eingabe Vorgänge auswirkt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: b00f53a282833b560a29c6bed4c7ef0b9e056ba5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060098"
---
# <a name="console-modes"></a><span data-ttu-id="ca6ac-104">Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="ca6ac-104">Console Modes</span></span>


<span data-ttu-id="ca6ac-105">Jedem Konsolen Eingabepuffer ist ein Satz von Eingabemodi zugeordnet, der sich auf Eingabe Vorgänge auswirkt.</span><span class="sxs-lookup"><span data-stu-id="ca6ac-105">Associated with each console input buffer is a set of input modes that affects input operations.</span></span> <span data-ttu-id="ca6ac-106">Ebenso hat jeder Konsolenbildschirm Puffer eine Reihe von Ausgabe Modi, die sich auf Ausgabe Vorgänge auswirken.</span><span class="sxs-lookup"><span data-stu-id="ca6ac-106">Similarly, each console screen buffer has a set of output modes that affects output operations.</span></span> <span data-ttu-id="ca6ac-107">Die Eingabemodi können in zwei Gruppen unterteilt werden: solche, die sich auf die Eingabefunktionen auf hoher Ebene auswirken, und diejenigen, die sich auf die Eingabefunktionen auf niedriger Ebene auswirken.</span><span class="sxs-lookup"><span data-stu-id="ca6ac-107">The input modes can be divided into two groups: those that affect the high-level input functions and those that affect the low-level input functions.</span></span> <span data-ttu-id="ca6ac-108">Die Ausgabe Modi wirken sich nur auf Anwendungen aus, die die Ausgabefunktionen auf hoher Ebene verwenden.</span><span class="sxs-lookup"><span data-stu-id="ca6ac-108">The output modes only affect applications that use the high-level output functions.</span></span>

<span data-ttu-id="ca6ac-109">Die [**getconsolemode**](getconsolemode.md) -Funktion meldet den aktuellen Eingabemodus für den Eingabepuffer einer Konsole oder den aktuellen Ausgabemodus eines Bildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="ca6ac-109">The [**GetConsoleMode**](getconsolemode.md) function reports the current input mode of a console's input buffer or the current output mode of a screen buffer.</span></span> <span data-ttu-id="ca6ac-110">Die [**setconsolemode**](setconsolemode.md) -Funktion legt den aktuellen Modus eines Konsolen Eingabe Puffers oder eines Bildschirm Puffers fest.</span><span class="sxs-lookup"><span data-stu-id="ca6ac-110">The [**SetConsoleMode**](setconsolemode.md) function sets the current mode of either a console input buffer or a screen buffer.</span></span> <span data-ttu-id="ca6ac-111">Wenn in einer Konsole mehrere Bildschirm Puffer angezeigt werden, können die Ausgabe Modi der einzelnen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca6ac-111">If a console has multiple screen buffers, the output modes of each can be different.</span></span> <span data-ttu-id="ca6ac-112">Eine Anwendung kann e/a-Modi jederzeit ändern.</span><span class="sxs-lookup"><span data-stu-id="ca6ac-112">An application can change I/O modes at any time.</span></span> <span data-ttu-id="ca6ac-113">Weitere Informationen zu den Konsolen Modi, die e/a-Vorgänge auf hoher Ebene und niedriger Ebene betreffen, finden Sie unter allgemeine [Konsolen](high-level-console-modes.md) Modi und [Low-Level-Konsolen Modi](low-level-console-modes.md).</span><span class="sxs-lookup"><span data-stu-id="ca6ac-113">For more information about the console modes that affect high-level and low-level I/O operations, see [High-Level Console Modes](high-level-console-modes.md) and [Low-Level Console Modes](low-level-console-modes.md).</span></span>

<span data-ttu-id="ca6ac-114">Die [**getconsoledisplaymode**](getconsoledisplaymode.md) -Funktion meldet, ob sich die aktuelle Konsole im Vollbildmodus befindet und ob Sie direkt mit der Hardware kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="ca6ac-114">The [**GetConsoleDisplayMode**](getconsoledisplaymode.md) function reports whether the current console is in full-screen mode and whether it communicates directly with the hardware.</span></span>

 

 




