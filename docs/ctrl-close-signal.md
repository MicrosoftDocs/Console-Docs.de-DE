---
title: STRG + schließen-Signal
description: Das System generiert ein STRG + schließen-Signal, wenn der Benutzer eine Konsole schließt.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: d3775bf0b8536fc531905ee6665a1e2c294d0a68
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038228"
---
# <a name="ctrlclose-signal"></a><span data-ttu-id="2997f-104">STRG + schließen-Signal</span><span class="sxs-lookup"><span data-stu-id="2997f-104">CTRL+CLOSE Signal</span></span>

<span data-ttu-id="2997f-105">Das System generiert ein STRG + schließen-Signal, wenn der Benutzer eine Konsole schließt.</span><span class="sxs-lookup"><span data-stu-id="2997f-105">The system generates a CTRL+CLOSE signal when the user closes a console.</span></span> <span data-ttu-id="2997f-106">Alle Prozesse, die an die Konsole angefügt sind, erhalten das Signal, sodass jeder Prozess vor dem beenden eine Bereinigungs Möglichkeit erhält.</span><span class="sxs-lookup"><span data-stu-id="2997f-106">All processes attached to the console receive the signal, giving each process an opportunity to clean up before termination.</span></span> <span data-ttu-id="2997f-107">Wenn ein Prozess dieses Signal empfängt, kann die Handlerfunktion nach dem Ausführen von Bereinigungs Vorgängen eine der folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="2997f-107">When a process receives this signal, the handler function can take one of the following actions after performing any cleanup operations:</span></span>

- <span data-ttu-id="2997f-108">Wenden Sie [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) an, um den Prozess zu beenden.</span><span class="sxs-lookup"><span data-stu-id="2997f-108">Call [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) to terminate the process.</span></span>
- <span data-ttu-id="2997f-109">Gibt **false** zurück.</span><span class="sxs-lookup"><span data-stu-id="2997f-109">Return **FALSE** .</span></span> <span data-ttu-id="2997f-110">Wenn keine der registrierten Handlerfunktionen **true** zurückgibt, beendet der Standard Handler den Prozess.</span><span class="sxs-lookup"><span data-stu-id="2997f-110">If none of the registered handler functions returns **TRUE** , the default handler terminates the process.</span></span>
- <span data-ttu-id="2997f-111">Gibt **true** zurück.</span><span class="sxs-lookup"><span data-stu-id="2997f-111">Return **TRUE** .</span></span> <span data-ttu-id="2997f-112">In diesem Fall werden keine anderen Handlerfunktionen aufgerufen, und der Prozess wird beendet.</span><span class="sxs-lookup"><span data-stu-id="2997f-112">In this case, no other handler functions are called and the process terminates.</span></span>
