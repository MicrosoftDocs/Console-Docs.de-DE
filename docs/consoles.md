---
title: Konsolen – Windows-Desktop
description: Eine-Konsole ist eine Anwendung, die e/a-Vorgänge für Befehlszeilen Anwendungen bereitstellt.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: b50ccd3d38b70ce67498451c8272b832c59fcef9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039118"
---
# <a name="consoles"></a><span data-ttu-id="713fd-104">Trö</span><span class="sxs-lookup"><span data-stu-id="713fd-104">Consoles</span></span>

<span data-ttu-id="713fd-105">Eine- *Konsole* ist eine Anwendung, die e/a-Dienste für Anwendungen im Zeichenmodus bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="713fd-105">A *console* is an application that provides I/O services to character-mode applications.</span></span>

<span data-ttu-id="713fd-106">Eine-Konsole besteht aus einem Eingabepuffer und mindestens einem Bildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="713fd-106">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="713fd-107">Der *Eingabepuffer* enthält eine Warteschlange von Eingabedaten Sätzen, die jeweils Informationen über ein Eingabe Ereignis enthalten.</span><span class="sxs-lookup"><span data-stu-id="713fd-107">The *input buffer* contains a queue of input records, each of which contains information about an input event.</span></span> <span data-ttu-id="713fd-108">Die Eingabe Warteschlange enthält immer Key-Press-und Key-Release-Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="713fd-108">The input queue always includes key-press and key-release events.</span></span> <span data-ttu-id="713fd-109">Es kann auch Mausereignisse (Zeiger Bewegungen und Schaltflächen-Pressen und Releases) und Ereignisse enthalten, in denen sich Benutzeraktionen auf die Größe des aktiven Bildschirm Puffers auswirken.</span><span class="sxs-lookup"><span data-stu-id="713fd-109">It may also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer.</span></span> <span data-ttu-id="713fd-110">Ein *Bildschirm Puffer* ist ein zweidimensionales Array von Zeichen-und Farbdaten für die Ausgabe in einem Konsolenfenster.</span><span class="sxs-lookup"><span data-stu-id="713fd-110">A *screen buffer* is a two-dimensional array of character and color data for output in a console window.</span></span> <span data-ttu-id="713fd-111">Eine beliebige Anzahl von Prozessen kann eine-Konsole gemeinsam verwenden.</span><span class="sxs-lookup"><span data-stu-id="713fd-111">Any number of processes can share a console.</span></span>

> [!TIP]
><span data-ttu-id="713fd-112">Eine breitere Idee von Konsolen und deren Beziehung zu Terminals und Befehlszeilen-Client Anwendungen finden Sie in der Roadmap für das **[Ökosystem](ecosystem-roadmap.md)** .</span><span class="sxs-lookup"><span data-stu-id="713fd-112">A broader idea of consoles and how they relate to terminals and command-line client applications can be found in the **[ecosystem roadmap](ecosystem-roadmap.md)** .</span></span>

- [<span data-ttu-id="713fd-113">Erstellung einer Konsole</span><span class="sxs-lookup"><span data-stu-id="713fd-113">Creation of a Console</span></span>](creation-of-a-console.md)
- [<span data-ttu-id="713fd-114">Anfügen an eine Konsole</span><span class="sxs-lookup"><span data-stu-id="713fd-114">Attaching to a Console</span></span>](attaching-to-a-console.md)
- [<span data-ttu-id="713fd-115">Schließen einer Konsole</span><span class="sxs-lookup"><span data-stu-id="713fd-115">Closing a Console</span></span>](closing-a-console.md)
- [<span data-ttu-id="713fd-116">Konsolenhandles</span><span class="sxs-lookup"><span data-stu-id="713fd-116">Console Handles</span></span>](console-handles.md)
- [<span data-ttu-id="713fd-117">Konsoleneingabepuffer</span><span class="sxs-lookup"><span data-stu-id="713fd-117">Console Input Buffer</span></span>](console-input-buffer.md)
- [<span data-ttu-id="713fd-118">Konsolenbildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="713fd-118">Console Screen Buffers</span></span>](console-screen-buffers.md)
- [<span data-ttu-id="713fd-119">Fenster-und Bildschirm Puffergröße</span><span class="sxs-lookup"><span data-stu-id="713fd-119">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
- [<span data-ttu-id="713fd-120">Konsolenauswahl</span><span class="sxs-lookup"><span data-stu-id="713fd-120">Console Selection</span></span>](console-selection.md)
- [<span data-ttu-id="713fd-121">Scrollen des Bildschirm Puffers</span><span class="sxs-lookup"><span data-stu-id="713fd-121">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)
