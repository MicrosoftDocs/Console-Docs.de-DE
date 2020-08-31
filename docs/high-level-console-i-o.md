---
title: E/a-Konsole auf hoher Ebene
description: Die e/a-Funktionen auf hoher Ebene stellen eine einfache Möglichkeit dar, einen Datenstrom aus Konsolen Eingaben zu lesen oder einen Zeichendaten Strom in die Konsolenausgabe zu schreiben.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_high\_level\_console\_i\_o'
- base.high\_level\_console\_i\_o
- consoles.high\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6d191fee-87bb-4659-8056-910149e591f7
ms.openlocfilehash: 2209259f604bb8653bca6ab38ca763b63f65713f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059611"
---
# <a name="high-level-console-io"></a><span data-ttu-id="a1d56-104">E/a-Konsole auf hoher Ebene</span><span class="sxs-lookup"><span data-stu-id="a1d56-104">High-Level Console I/O</span></span>


<span data-ttu-id="a1d56-105">Die e/a-Funktionen auf hoher Ebene stellen eine einfache Möglichkeit dar, einen Datenstrom aus Konsolen Eingaben zu lesen oder einen Zeichendaten Strom in die Konsolenausgabe zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="a1d56-105">The high-level I/O functions provide a simple way to read a stream of characters from console input or to write a stream of characters to console output.</span></span> <span data-ttu-id="a1d56-106">Ein allgemeiner Lesevorgang ruft Eingabezeichen aus dem Eingabepuffer einer Konsole ab und speichert Sie in einem angegebenen Puffer.</span><span class="sxs-lookup"><span data-stu-id="a1d56-106">A high-level read operation gets input characters from a console's input buffer and stores them in a specified buffer.</span></span> <span data-ttu-id="a1d56-107">Ein hoher Schreibvorgang erfordert Zeichen aus einem angegebenen Puffer und schreibt Sie in einen Bildschirm Puffer an der aktuellen Cursorposition, wobei der Cursor beim Schreiben jedes Zeichens vorwärts bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="a1d56-107">A high-level write operation takes characters from a specified buffer and writes them to a screen buffer at the current cursor location, advancing the cursor as each character is written.</span></span>

<span data-ttu-id="a1d56-108">Die e/a-Vorgänge auf hoher Ebene bieten Ihnen die Wahl zwischen den Funktionen "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " sowie den Funktionen "read [**Console**](readconsole.md) " und " [**Write Console**](writeconsole.md) ".</span><span class="sxs-lookup"><span data-stu-id="a1d56-108">High-level I/O gives you a choice between the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions and the [**ReadConsole**](readconsole.md) and [**WriteConsole**](writeconsole.md) functions.</span></span> <span data-ttu-id="a1d56-109">Sie sind mit Ausnahme zweier wichtiger Unterschiede identisch.</span><span class="sxs-lookup"><span data-stu-id="a1d56-109">They are identical, except for two important differences.</span></span> <span data-ttu-id="a1d56-110">Die Konsolenfunktionen unterstützen die Verwendung von Unicode-Zeichen oder den ANSI-Zeichensatz. Unicode wird von den Datei-e/a-Funktionen nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a1d56-110">The console functions support the use of either Unicode characters or the ANSI character set; the file I/O functions do not support Unicode.</span></span> <span data-ttu-id="a1d56-111">Außerdem können die Datei-e/a-Funktionen für den Zugriff auf Dateien, Pipes und serielle Kommunikationsgeräte verwendet werden. die Konsolenfunktionen können nur mit Konsolen Handles verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a1d56-111">Also, the file I/O functions can be used to access files, pipes, and serial communications devices; the console functions can only be used with console handles.</span></span> <span data-ttu-id="a1d56-112">Dieser Unterschied ist wichtig, wenn eine Anwendung auf Standard Handles basiert, die möglicherweise umgeleitet wurden.</span><span class="sxs-lookup"><span data-stu-id="a1d56-112">This distinction is important if an application relies on standard handles that may have been redirected.</span></span>

<span data-ttu-id="a1d56-113">Wenn Sie einen der Funktionen auf hoher Ebene verwenden, kann eine Anwendung die Text-und Hintergrundfarben steuern, die zum Anzeigen von Zeichen verwendet werden, die anschließend in einen Bildschirm Puffer geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="a1d56-113">When using either set of high-level functions, an application can control the text and background colors used to display characters subsequently written to a screen buffer.</span></span> <span data-ttu-id="a1d56-114">Eine Anwendung kann auch die Konsolen Modi verwenden, die sich auf die e/a-Konsole auf hoher Ebene auswirken, um die folgenden Eigenschaften zu aktivieren oder zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="a1d56-114">An application can also use the console modes that affect high-level console I/O to enable or disable the following properties:</span></span>

- <span data-ttu-id="a1d56-115">Wiedergabe von Tastatureingaben in den aktiven Bildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="a1d56-115">Echoing of keyboard input to the active screen buffer</span></span>
- <span data-ttu-id="a1d56-116">Zeilen Eingabe, in der ein Lesevorgang erst zurückgegeben wird, wenn die EINGABETASTE gedrückt wird</span><span class="sxs-lookup"><span data-stu-id="a1d56-116">Line input, in which a read operation does not return until the ENTER key is pressed</span></span>
- <span data-ttu-id="a1d56-117">Automatische Verarbeitung von Tastatureingaben zur Handhabung von Wagen Rücklauf-, STRG + C-und anderen Eingabe Details</span><span class="sxs-lookup"><span data-stu-id="a1d56-117">Automatic processing of keyboard input to handle carriage returns, CTRL+C, and other input details</span></span>
- <span data-ttu-id="a1d56-118">Automatische Verarbeitung der Ausgabe zur Behandlung von Zeilenumbruch, Wagen Rücklauf, backspaces und anderen Ausgabe Details</span><span class="sxs-lookup"><span data-stu-id="a1d56-118">Automatic processing of output to handle line wrapping, carriage returns, backspaces, and other output details</span></span>

<span data-ttu-id="a1d56-119">Weitere Informationen finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="a1d56-119">For more information, see the following topics:</span></span>

- [<span data-ttu-id="a1d56-120">Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="a1d56-120">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="a1d56-121">Allgemeine Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="a1d56-121">High-Level Console Modes</span></span>](high-level-console-modes.md)
- [<span data-ttu-id="a1d56-122">Eingabe-und Ausgabefunktionen auf hoher Ebene</span><span class="sxs-lookup"><span data-stu-id="a1d56-122">High-Level Console Input and Output Functions</span></span>](high-level-console-input-and-output-functions.md)

 

 




