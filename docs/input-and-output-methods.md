---
title: Eingabe-und Ausgabemethoden
description: Es gibt zwei unterschiedliche Ansätze für Konsolen-e/a. die Wahl hängt von der Flexibilität und Steuerung der Anwendungsanforderungen ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_input\_and\_output\_methods'
- base.input\_and\_output\_methods
- consoles.input\_and\_output\_methods
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55a86d5d-d0b1-4d0c-b42f-7342809289ad
ms.openlocfilehash: 29f4ca8f4851c73f79d810f56b57f490995cad04
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060435"
---
# <a name="input-and-output-methods"></a><span data-ttu-id="2adad-104">Eingabe-und Ausgabemethoden</span><span class="sxs-lookup"><span data-stu-id="2adad-104">Input and Output Methods</span></span>


<span data-ttu-id="2adad-105">Es gibt zwei unterschiedliche Ansätze für Konsolen-e/a. die Wahl hängt von der Flexibilität und Steuerung der Anwendungsanforderungen ab.</span><span class="sxs-lookup"><span data-stu-id="2adad-105">There are two different approaches to console I/O, the choice of which depends on how much flexibility and control an application needs.</span></span> <span data-ttu-id="2adad-106">Der allgemeine Ansatz ermöglicht eine einfache Zeichen Strom-e/a, schränkt aber den Zugriff auf die Eingabe-und Bildschirm Puffer einer Konsole ein.</span><span class="sxs-lookup"><span data-stu-id="2adad-106">The high-level approach enables simple character stream I/O, but it limits access to a console's input and screen buffers.</span></span> <span data-ttu-id="2adad-107">Die Low-Level-Vorgehensweise erfordert, dass Entwickler mehr Code schreiben und eine größere Anzahl von Funktionen auswählen, aber auch eine höhere Flexibilität der Anwendung bietet.</span><span class="sxs-lookup"><span data-stu-id="2adad-107">The low-level approach requires that developers write more code and choose among a greater range of functions, but it also gives an application more flexibility.</span></span>

<span data-ttu-id="2adad-108">Eine Anwendung kann die Datei-e/a-Funktionen, "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747)" und die Konsolenfunktionen " [**infoconsole**](readconsole.md) " und " [**Write-Console**](writeconsole.md)" für e/a-Vorgänge auf hoher Ebene verwenden, die indirekten Zugriff auf die Eingabe-und Bildschirm Puffer einer Konsole bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2adad-108">An application can use the file I/O functions, [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), and the console functions, [**ReadConsole**](readconsole.md) and [**WriteConsole**](writeconsole.md), for high-level I/O that provides indirect access to a console's input and screen buffers.</span></span> <span data-ttu-id="2adad-109">Die Eingabefunktionen auf hoher Ebene filtern und verarbeiten die Daten im Eingabepuffer einer Konsole, um die Eingabe als Zeichendaten Strom zurückzugeben, wobei die Eingabe von Maus-und Puffergröße verworfen wird.</span><span class="sxs-lookup"><span data-stu-id="2adad-109">The high-level input functions filter and process the data in a console's input buffer to return input as a stream of characters, discarding mouse and buffer-resizing input.</span></span> <span data-ttu-id="2adad-110">Entsprechend schreiben die Ausgabefunktionen auf hoher Ebene einen Datenstrom von Zeichen, die an der aktuellen Cursorposition in einem Bildschirm Puffer angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2adad-110">Similarly, the high-level output functions write a stream of characters that are displayed at the current cursor location in a screen buffer.</span></span> <span data-ttu-id="2adad-111">Eine Anwendung steuert die Funktionsweise dieser Funktionen, indem die e/a-Modi einer Konsole festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="2adad-111">An application controls the way these functions work by setting a console's I/O modes.</span></span>

<span data-ttu-id="2adad-112">Die e/a-Funktionen auf niedriger Ebene bieten direkten Zugriff auf die Eingabe-und Bildschirm Puffer einer Konsole, sodass eine Anwendung auf die Maus-und Puffergröße für Eingabeereignisse und erweiterte Informationen für Tastatur Ereignisse zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="2adad-112">The low-level I/O functions provide direct access to a console's input and screen buffers, enabling an application to access mouse and buffer-resizing input events and extended information for keyboard events.</span></span> <span data-ttu-id="2adad-113">Mithilfe von Ausgabefunktionen auf niedriger Ebene kann eine Anwendung eine angegebene Anzahl von aufeinander folgenden Zeichen Zellen in einem Bildschirm Puffer lesen oder in rechteckige Blöcke von Zeichen Zellen an einer bestimmten Position in einem Bildschirm Puffer schreiben.</span><span class="sxs-lookup"><span data-stu-id="2adad-113">Low-level output functions enable an application to read from or write to a specified number of consecutive character cells in a screen buffer, or to read or write to rectangular blocks of character cells at a specified location in a screen buffer.</span></span> <span data-ttu-id="2adad-114">Die Eingabemodi einer Konsole beeinflussen Eingaben auf niedriger Ebene, indem der Anwendung ermöglicht wird, zu bestimmen, ob Maus-und Puffer-resialisierungsereignisse im Eingabepuffer platziert werden.</span><span class="sxs-lookup"><span data-stu-id="2adad-114">A console's input modes affect low-level input by enabling the application to determine whether mouse and buffer-resizing events are placed in the input buffer.</span></span> <span data-ttu-id="2adad-115">Die Ausgabe Modi einer Konsole haben keine Auswirkungen auf die Ausgabe auf niedriger Ebene.</span><span class="sxs-lookup"><span data-stu-id="2adad-115">A console's output modes have no effect on low-level output.</span></span>

<span data-ttu-id="2adad-116">Die e/a-Methoden auf hoher und niedriger Ebene schließen sich nicht gegenseitig aus, und eine Anwendung kann eine beliebige Kombination dieser Funktionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="2adad-116">The high-level and low-level I/O methods are not mutually exclusive, and an application can use any combination of these functions.</span></span> <span data-ttu-id="2adad-117">In der Regel verwendet eine Anwendung jedoch nur einen Ansatz oder den anderen.</span><span class="sxs-lookup"><span data-stu-id="2adad-117">Typically, however, an application uses one approach or the other exclusively.</span></span>

<span data-ttu-id="2adad-118">In den folgenden Themen werden die Konsolen Modi und die e/a-Funktionen auf hoher und niedriger Ebene beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2adad-118">The following topics describe the console modes and the high-level and low-level I/O functions.</span></span>

- [<span data-ttu-id="2adad-119">Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="2adad-119">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="2adad-120">E/a-Konsole auf hoher Ebene</span><span class="sxs-lookup"><span data-stu-id="2adad-120">High-Level Console I/O</span></span>](high-level-console-i-o.md)
- [<span data-ttu-id="2adad-121">Allgemeine Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="2adad-121">High-Level Console Modes</span></span>](high-level-console-modes.md)
- [<span data-ttu-id="2adad-122">Eingabe-und Ausgabefunktionen auf hoher Ebene</span><span class="sxs-lookup"><span data-stu-id="2adad-122">High-Level Console Input and Output Functions</span></span>](high-level-console-input-and-output-functions.md)
- [<span data-ttu-id="2adad-123">E/a-Konsole auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="2adad-123">Low-Level Console I/O</span></span>](low-level-console-i-o.md)
- [<span data-ttu-id="2adad-124">Konsolen Modi auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="2adad-124">Low-Level Console Modes</span></span>](low-level-console-modes.md)
- [<span data-ttu-id="2adad-125">Konsolen Eingabefunktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="2adad-125">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)
- [<span data-ttu-id="2adad-126">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="2adad-126">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

 

 




