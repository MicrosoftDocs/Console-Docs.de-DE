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
ms.openlocfilehash: be237eac7649ad76615aea341a555a8a7af6445c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357890"
---
# <a name="ctrlclose-signal"></a><span data-ttu-id="5769e-104">STRG + schließen-Signal</span><span class="sxs-lookup"><span data-stu-id="5769e-104">CTRL+CLOSE Signal</span></span>

<span data-ttu-id="5769e-105">Das System generiert ein STRG + schließen-Signal, wenn der Benutzer eine Konsole schließt.</span><span class="sxs-lookup"><span data-stu-id="5769e-105">The system generates a CTRL+CLOSE signal when the user closes a console.</span></span> <span data-ttu-id="5769e-106">Alle Prozesse, die an die Konsole angefügt sind, erhalten das Signal, sodass jeder Prozess vor dem beenden eine Bereinigungs Möglichkeit erhält.</span><span class="sxs-lookup"><span data-stu-id="5769e-106">All processes attached to the console receive the signal, giving each process an opportunity to clean up before termination.</span></span> <span data-ttu-id="5769e-107">Wenn ein Prozess dieses Signal empfängt, kann die Handlerfunktion nach dem Ausführen von Bereinigungs Vorgängen eine der folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="5769e-107">When a process receives this signal, the handler function can take one of the following actions after performing any cleanup operations:</span></span>

- <span data-ttu-id="5769e-108">Wenden Sie [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) an, um den Prozess zu beenden.</span><span class="sxs-lookup"><span data-stu-id="5769e-108">Call [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) to terminate the process.</span></span>
- <span data-ttu-id="5769e-109">Gibt **false** zurück.</span><span class="sxs-lookup"><span data-stu-id="5769e-109">Return **FALSE**.</span></span> <span data-ttu-id="5769e-110">Wenn keine der registrierten Handlerfunktionen **true** zurückgibt, beendet der Standard Handler den Prozess.</span><span class="sxs-lookup"><span data-stu-id="5769e-110">If none of the registered handler functions returns **TRUE**, the default handler terminates the process.</span></span>
- <span data-ttu-id="5769e-111">Gibt **true** zurück.</span><span class="sxs-lookup"><span data-stu-id="5769e-111">Return **TRUE**.</span></span> <span data-ttu-id="5769e-112">In diesem Fall werden keine anderen Handlerfunktionen aufgerufen, und der Prozess wird beendet.</span><span class="sxs-lookup"><span data-stu-id="5769e-112">In this case, no other handler functions are called and the process terminates.</span></span>