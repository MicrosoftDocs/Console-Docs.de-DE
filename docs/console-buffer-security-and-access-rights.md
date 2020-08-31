---
title: Sicherheit und Zugriffsrechte für die Konsolen Puffer
description: Das Windows-Sicherheitsmodell ermöglicht es Ihnen, den Zugriff auf Konsolen Eingabepuffer und Konsolenbildschirm Puffer zu steuern. Weitere Informationen zur Sicherheit finden Sie unter Zugriffs Steuerungsmodell.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: 63cfdb91f4ab9696ade81c7a15bc62e1c93ab6e3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060162"
---
# <a name="console-buffer-security-and-access-rights"></a><span data-ttu-id="19f29-105">Sicherheit und Zugriffsrechte für die Konsolen Puffer</span><span class="sxs-lookup"><span data-stu-id="19f29-105">Console Buffer Security and Access Rights</span></span>


<span data-ttu-id="19f29-106">Das Windows-Sicherheitsmodell ermöglicht es Ihnen, den Zugriff auf Konsolen Eingabepuffer und Konsolenbildschirm Puffer zu steuern.</span><span class="sxs-lookup"><span data-stu-id="19f29-106">The Windows security model enables you to control access to console input buffers and console screen buffers.</span></span> <span data-ttu-id="19f29-107">Weitere Informationen zur Sicherheit finden Sie unter [Zugriffs Steuerungsmodell](https://msdn.microsoft.com/library/windows/desktop/aa374876).</span><span class="sxs-lookup"><span data-stu-id="19f29-107">For more information about security, see [Access-Control Model](https://msdn.microsoft.com/library/windows/desktop/aa374876).</span></span>

<span data-ttu-id="19f29-108">Sie können eine [Sicherheits Beschreibung](https://msdn.microsoft.com/library/windows/desktop/aa379563) für die Konsolen Eingabe und die Bildschirm Puffer der Konsole angeben, wenn Sie [**die Funktion**](https://msdn.microsoft.com/library/windows/desktop/aa363858) "up" oder " [**kreateconsoleskreenbuffer**](createconsolescreenbuffer.md) " aufrufen.</span><span class="sxs-lookup"><span data-stu-id="19f29-108">You can specify a [security descriptor](https://msdn.microsoft.com/library/windows/desktop/aa379563) for the console input and console screen buffers when you call the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) or [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function.</span></span> <span data-ttu-id="19f29-109">Wenn Sie **null**angeben, erhält das Objekt eine Standard Sicherheits Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="19f29-109">If you specify **NULL**, the object gets a default security descriptor.</span></span> <span data-ttu-id="19f29-110">Die ACLs in der Standard Sicherheits Beschreibung für einen Konsolen Puffer stammen aus dem primären Token oder dem Identitätswechsel Token des Erstellers.</span><span class="sxs-lookup"><span data-stu-id="19f29-110">The ACLs in the default security descriptor for a console buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="19f29-111">Die von "", "", " [**", "**](https://msdn.microsoft.com/library/windows/desktop/aa363858)", " [**", "**](createconsolescreenbuffer.md)", "", " \*\*" und " \_ \*\* [**getstdhandle**](getstdhandle.md) " zurückgegebenen Handles verfügen über die **allgemeinen \_ Lese** Zugriffsrechte und</span><span class="sxs-lookup"><span data-stu-id="19f29-111">The handles returned by [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md), and [**GetStdHandle**](getstdhandle.md) have the **GENERIC\_READ** and **GENERIC\_WRITE** access rights.</span></span>

<span data-ttu-id="19f29-112">Zu den gültigen Zugriffsrechten gehören die allgemeinen \*\* \_ Lese\*\* -und **generischen \_ Schreib** [Zugriffsrechte](https://msdn.microsoft.com/library/windows/desktop/aa446632).</span><span class="sxs-lookup"><span data-stu-id="19f29-112">The valid access rights include the **GENERIC\_READ** and **GENERIC\_WRITE** [generic access rights](https://msdn.microsoft.com/library/windows/desktop/aa446632).</span></span>


| <span data-ttu-id="19f29-113">Wert</span><span class="sxs-lookup"><span data-stu-id="19f29-113">Value</span></span>                            | <span data-ttu-id="19f29-114">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="19f29-114">Meaning</span></span>                                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="19f29-115">**Generisch \_ Read** (0x80000000l)</span><span class="sxs-lookup"><span data-stu-id="19f29-115">**GENERIC\_READ** (0x80000000L)</span></span>  | <span data-ttu-id="19f29-116">Fordert Lesezugriff auf den Konsolenbildschirm Puffer an und ermöglicht dem Prozess das Lesen von Daten aus dem Puffer.</span><span class="sxs-lookup"><span data-stu-id="19f29-116">Requests read access to the console screen buffer, enabling the process to read data from the buffer.</span></span> |
| <span data-ttu-id="19f29-117">**Generisch \_ Write** (0x40000000l)</span><span class="sxs-lookup"><span data-stu-id="19f29-117">**GENERIC\_WRITE** (0x40000000L)</span></span> | <span data-ttu-id="19f29-118">Fordert Schreibzugriff auf den Konsolenbildschirm Puffer an und ermöglicht dem Prozess das Schreiben von Daten in den Puffer.</span><span class="sxs-lookup"><span data-stu-id="19f29-118">Requests write access to the console screen buffer, enabling the process to write data to the buffer.</span></span> |










