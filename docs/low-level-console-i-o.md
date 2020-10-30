---
title: Low-Level Konsolen-e/a
description: Die e/a-Funktionen der Low-Level-Konsole erweitern die Kontrolle einer Anwendung über die Konsolen-e/a, indem Sie den direkten Zugriff auf die Eingabe-und Bildschirm Puffer einer Konsole aktivieren.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_low\_level\_console\_i\_o'
- base.low\_level\_console\_i\_o
- consoles.low\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c874aff4-6129-4dbc-8949-24d46382d81c
ms.openlocfilehash: b4ec834e44f7ff291466cfe1714442bc17ca7aca
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039548"
---
# <a name="low-level-console-io"></a><span data-ttu-id="8ac94-104">Low-Level Konsolen-e/a</span><span class="sxs-lookup"><span data-stu-id="8ac94-104">Low-Level Console I/O</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="8ac94-105">Die e/a-Funktionen der Low-Level-Konsole erweitern die Kontrolle einer Anwendung über die Konsolen-e/a, indem Sie den direkten Zugriff auf die Eingabe-und Bildschirm Puffer einer Konsole aktivieren.</span><span class="sxs-lookup"><span data-stu-id="8ac94-105">The low-level console I/O functions expand an application's control over console I/O by enabling direct access to a console's input and screen buffers.</span></span> <span data-ttu-id="8ac94-106">Diese Funktionen ermöglichen es einer Anwendung, folgende Aufgaben auszuführen:</span><span class="sxs-lookup"><span data-stu-id="8ac94-106">These functions enable an application to perform the following tasks:</span></span>

- <span data-ttu-id="8ac94-107">Empfangen von Eingaben über Maus-und Puffergröße-Ereignisse</span><span class="sxs-lookup"><span data-stu-id="8ac94-107">Receive input about mouse and buffer-resizing events</span></span>
- <span data-ttu-id="8ac94-108">Erweiterte Informationen zu Tastatureingabe Ereignissen erhalten</span><span class="sxs-lookup"><span data-stu-id="8ac94-108">Receive extended information about keyboard input events</span></span>
- <span data-ttu-id="8ac94-109">Eingabedaten Sätze in den Eingabepuffer schreiben</span><span class="sxs-lookup"><span data-stu-id="8ac94-109">Write input records to the input buffer</span></span>
- <span data-ttu-id="8ac94-110">Eingabedaten Sätze lesen, ohne Sie aus dem Eingabepuffer zu entfernen</span><span class="sxs-lookup"><span data-stu-id="8ac94-110">Read input records without removing them from the input buffer</span></span>
- <span data-ttu-id="8ac94-111">Bestimmen der Anzahl ausstehender Ereignisse im Eingabepuffer</span><span class="sxs-lookup"><span data-stu-id="8ac94-111">Determine the number of pending events in the input buffer</span></span>
- <span data-ttu-id="8ac94-112">Leeren Sie den Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="8ac94-112">Flush the input buffer</span></span>
- <span data-ttu-id="8ac94-113">Lesen und Schreiben von Zeichen folgen von Unicode-oder ANSI-Zeichen an einer bestimmten Position in einem Bildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="8ac94-113">Read and write strings of Unicode or ANSI characters at a specified location in a screen buffer</span></span>
- <span data-ttu-id="8ac94-114">Lese-und Schreibvorgänge für Zeichen folgen mit Text-und Hintergrundfarben Attributen an einem angegebenen Bildschirm Puffer Speicherort</span><span class="sxs-lookup"><span data-stu-id="8ac94-114">Read and write strings of text and background color attributes at a specified screen buffer location</span></span>
- <span data-ttu-id="8ac94-115">Rechteckige Blöcke von Zeichen-und Farbdaten an einem angegebenen Bildschirm Puffer Speicherort lesen und schreiben</span><span class="sxs-lookup"><span data-stu-id="8ac94-115">Read and write rectangular blocks of character and color data at a specified screen buffer location</span></span>
- <span data-ttu-id="8ac94-116">Schreiben eines einzelnen Unicode-oder ANSI-Zeichens oder einer Kombination aus Text-und Hintergrund Farb Attribut in eine angegebene Anzahl von aufeinander folgenden Zellen, beginnend an einem angegebenen Bildschirm Puffer Speicherort</span><span class="sxs-lookup"><span data-stu-id="8ac94-116">Write a single Unicode or ANSI character, or a text and background color attribute combination, to a specified number of consecutive cells beginning at a specified screen buffer location</span></span>

<span data-ttu-id="8ac94-117">Weitere Informationen finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="8ac94-117">For more information, see the following topics:</span></span>

- [<span data-ttu-id="8ac94-118">Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="8ac94-118">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="8ac94-119">Konsolen Modi auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="8ac94-119">Low-Level Console Modes</span></span>](low-level-console-modes.md)
- [<span data-ttu-id="8ac94-120">Konsolen Eingabefunktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="8ac94-120">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)
- [<span data-ttu-id="8ac94-121">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="8ac94-121">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)
