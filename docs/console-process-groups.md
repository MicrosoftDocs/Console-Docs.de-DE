---
title: Konsolen Prozessgruppen
description: Wenn ein Prozess zum Erstellen eines neuen Konsolen Prozesses die Funktion "Debugprozess" verwendet, kann er das \_ Flag "neue Prozessgruppe erstellen" angeben, \_ \_ damit der neue Prozess der Stamm Prozess einer Konsolen Prozessgruppe wird.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_process\_groups'
- base.console\_process\_groups
- consoles.console\_process\_groups
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
ms.openlocfilehash: 8df877eca9a52ef9072685c673461723dda78a0b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358100"
---
# <a name="console-process-groups"></a><span data-ttu-id="7d662-104">Konsolen Prozessgruppen</span><span class="sxs-lookup"><span data-stu-id="7d662-104">Console Process Groups</span></span>

<span data-ttu-id="7d662-105">Wenn ein Prozess zum Erstellen eines neuen Konsolen Prozesses die Funktion " [**Debugprozess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) " verwendet, kann er das Flag " **\_ neue \_ Prozess \_ Gruppe erstellen** " angeben, damit der neue Prozess der Stamm Prozess einer Konsolen Prozessgruppe wird.</span><span class="sxs-lookup"><span data-stu-id="7d662-105">When a process uses the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function to create a new console process, it can specify the **CREATE\_NEW\_PROCESS\_GROUP** flag to make the new process the root process of a console process group.</span></span> <span data-ttu-id="7d662-106">Die Prozessgruppe umfasst alle Prozesse, bei denen es sich um nachfolgende Elemente des Stamm Prozesses handelt.</span><span class="sxs-lookup"><span data-stu-id="7d662-106">The process group includes all processes that are descendants of the root process.</span></span>

<span data-ttu-id="7d662-107">Ein Prozess kann die [**generateconsolectrlevent**](generateconsolectrlevent.md) -Funktion verwenden, um das Signal STRG + C oder STRG + UNTBR an alle Prozesse in einer Konsolen Prozessgruppe zu senden.</span><span class="sxs-lookup"><span data-stu-id="7d662-107">A process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to all processes in a console process group.</span></span> <span data-ttu-id="7d662-108">Das Signal wird nur von den Prozessen in der Gruppe empfangen, die an dieselbe Konsole wie der Prozess mit dem Namen **generateconsolectrlevent** angefügt sind.</span><span class="sxs-lookup"><span data-stu-id="7d662-108">The signal is only received by those processes in the group that are attached to the same console as the process that called **GenerateConsoleCtrlEvent**.</span></span>