---
title: Konsolen Prozessgruppen
description: Wenn ein Prozess zum Erstellen eines neuen Konsolen Prozesses die Funktion "Debugprozess" verwendet, kann er das \_ Flag "neue Prozessgruppe erstellen" angeben, \_ \_ damit der neue Prozess der Stamm Prozess einer Konsolen Prozessgruppe wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_process\_groups'
- base.console\_process\_groups
- consoles.console\_process\_groups
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
ms.openlocfilehash: 467959e651f7e0806742ca3920ca0d441d5543cc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060090"
---
# <a name="console-process-groups"></a><span data-ttu-id="47292-104">Konsolen Prozessgruppen</span><span class="sxs-lookup"><span data-stu-id="47292-104">Console Process Groups</span></span>


<span data-ttu-id="47292-105">Wenn ein Prozess zum Erstellen eines neuen Konsolen Prozesses die Funktion " [**Debugprozess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) " verwendet, kann er das Flag " \*\* \_ neue \_ Prozess \_ Gruppe erstellen\*\* " angeben, damit der neue Prozess der Stamm Prozess einer Konsolen Prozessgruppe wird.</span><span class="sxs-lookup"><span data-stu-id="47292-105">When a process uses the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function to create a new console process, it can specify the **CREATE\_NEW\_PROCESS\_GROUP** flag to make the new process the root process of a console process group.</span></span> <span data-ttu-id="47292-106">Die Prozessgruppe umfasst alle Prozesse, bei denen es sich um nachfolgende Elemente des Stamm Prozesses handelt.</span><span class="sxs-lookup"><span data-stu-id="47292-106">The process group includes all processes that are descendants of the root process.</span></span>

<span data-ttu-id="47292-107">Ein Prozess kann die [**generateconsolectrlevent**](generateconsolectrlevent.md) -Funktion verwenden, um das Signal STRG + C oder STRG + UNTBR an alle Prozesse in einer Konsolen Prozessgruppe zu senden.</span><span class="sxs-lookup"><span data-stu-id="47292-107">A process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to all processes in a console process group.</span></span> <span data-ttu-id="47292-108">Das Signal wird nur von den Prozessen in der Gruppe empfangen, die an dieselbe Konsole wie der Prozess mit dem Namen **generateconsolectrlevent**angefügt sind.</span><span class="sxs-lookup"><span data-stu-id="47292-108">The signal is only received by those processes in the group that are attached to the same console as the process that called **GenerateConsoleCtrlEvent**.</span></span>

 

 




