---
title: Konsolen – Windows-Desktop
description: Eine-Konsole ist eine Anwendung, die e/a-Vorgänge für Befehlszeilen Anwendungen bereitstellt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: 7b447e3c1d6d72c58890797177f6668f5d835d35
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059946"
---
# <a name="consoles"></a><span data-ttu-id="ef7fa-104">Trö</span><span class="sxs-lookup"><span data-stu-id="ef7fa-104">Consoles</span></span>

<span data-ttu-id="ef7fa-105">Eine- *Konsole* (oder ein *Terminal*) ist eine Anwendung, die e/a-Vorgänge für Anwendungen im Zeichenmodus bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="ef7fa-105">A *console* (or *terminal*) is an application that provides I/O to character-mode applications.</span></span> <span data-ttu-id="ef7fa-106">Dieser prozessorunabhängige Mechanismus vereinfacht das Portieren vorhandener Zeichenmodusanwendungen oder das Erstellen neuer Zeichenmodus-Tools und-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="ef7fa-106">This processor-independent mechanism makes it easy to port existing character-mode applications or to create new character-mode tools and applications.</span></span>

<span data-ttu-id="ef7fa-107">Eine-Konsole besteht aus einem Eingabepuffer und mindestens einem Bildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="ef7fa-107">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="ef7fa-108">Der *Eingabepuffer* enthält eine Warteschlange von Eingabedaten Sätzen, die jeweils Informationen über ein Eingabe Ereignis enthalten.</span><span class="sxs-lookup"><span data-stu-id="ef7fa-108">The *input buffer* contains a queue of input records, each of which contains information about an input event.</span></span> <span data-ttu-id="ef7fa-109">Die Eingabe Warteschlange enthält immer Key-Press-und Key-Release-Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="ef7fa-109">The input queue always includes key-press and key-release events.</span></span> <span data-ttu-id="ef7fa-110">Es kann auch Mausereignisse (Zeiger Bewegungen und Schaltflächen-Pressen und Releases) und Ereignisse enthalten, in denen sich Benutzeraktionen auf die Größe des aktiven Bildschirm Puffers auswirken.</span><span class="sxs-lookup"><span data-stu-id="ef7fa-110">It may also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer.</span></span> <span data-ttu-id="ef7fa-111">Ein *Bildschirm Puffer* ist ein zweidimensionales Array von Zeichen-und Farbdaten für die Ausgabe in einem Konsolenfenster.</span><span class="sxs-lookup"><span data-stu-id="ef7fa-111">A *screen buffer* is a two-dimensional array of character and color data for output in a console window.</span></span> <span data-ttu-id="ef7fa-112">Eine beliebige Anzahl von Prozessen kann eine-Konsole gemeinsam verwenden.</span><span class="sxs-lookup"><span data-stu-id="ef7fa-112">Any number of processes can share a console.</span></span>

- [<span data-ttu-id="ef7fa-113">Erstellung einer Konsole</span><span class="sxs-lookup"><span data-stu-id="ef7fa-113">Creation of a Console</span></span>](creation-of-a-console.md)
- [<span data-ttu-id="ef7fa-114">Anfügen an eine Konsole</span><span class="sxs-lookup"><span data-stu-id="ef7fa-114">Attaching to a Console</span></span>](attaching-to-a-console.md)
- [<span data-ttu-id="ef7fa-115">Schließen einer Konsole</span><span class="sxs-lookup"><span data-stu-id="ef7fa-115">Closing a Console</span></span>](closing-a-console.md)
- [<span data-ttu-id="ef7fa-116">Konsolen Handles</span><span class="sxs-lookup"><span data-stu-id="ef7fa-116">Console Handles</span></span>](console-handles.md)
- [<span data-ttu-id="ef7fa-117">Konsolen Eingabepuffer</span><span class="sxs-lookup"><span data-stu-id="ef7fa-117">Console Input Buffer</span></span>](console-input-buffer.md)
- [<span data-ttu-id="ef7fa-118">Konsolenbildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="ef7fa-118">Console Screen Buffers</span></span>](console-screen-buffers.md)
- [<span data-ttu-id="ef7fa-119">Fenster-und Bildschirm Puffergröße</span><span class="sxs-lookup"><span data-stu-id="ef7fa-119">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
- [<span data-ttu-id="ef7fa-120">Konsolen Auswahl</span><span class="sxs-lookup"><span data-stu-id="ef7fa-120">Console Selection</span></span>](console-selection.md)
- [<span data-ttu-id="ef7fa-121">Scrollen des Bildschirm Puffers</span><span class="sxs-lookup"><span data-stu-id="ef7fa-121">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)
