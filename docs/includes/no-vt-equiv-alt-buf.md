---
ms.openlocfilehash: ef8a068fe6edd2a7d2013c930c238235326b8c1d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039133"
---
> [!TIP]
> <span data-ttu-id="0afb1-101">Diese API wird nicht empfohlen, verfügt aber über eine ungefähre **[virtuelle Terminal](../console-virtual-terminal-sequences.md)** Entsprechung in der **[Alternativen Bildschirm Puffer](../console-virtual-terminal-sequences.md#alternate-screen-buffer)** Sequenz.</span><span class="sxs-lookup"><span data-stu-id="0afb1-101">This API is not recommended but it does have an approximate **[virtual terminal](../console-virtual-terminal-sequences.md)** equivalent in the **[alternate screen buffer](../console-virtual-terminal-sequences.md#alternate-screen-buffer)** sequence.</span></span> <span data-ttu-id="0afb1-102">Durch Festlegen des _Alternativen Bildschirm Puffers_ kann eine Anwendung einen separaten, isolierten Speicherplatz zum Zeichnen über den Verlauf der Sitzungs Laufzeit bereitstellen und gleichzeitig den Inhalt beibehalten, der vom Invoker der Anwendung angezeigt wurde.</span><span class="sxs-lookup"><span data-stu-id="0afb1-102">Setting the _alternate screen buffer_ can provide an application with a separate, isolated space for drawing over the course of its session runtime while preserving the content that was displayed by the application's invoker.</span></span> <span data-ttu-id="0afb1-103">Dadurch wird die Erstellung von Zeichnungs Informationen für die einfache Wiederherstellung beim Prozess beendet.</span><span class="sxs-lookup"><span data-stu-id="0afb1-103">This maintains that drawing information for simple restoration on process exit.</span></span>
