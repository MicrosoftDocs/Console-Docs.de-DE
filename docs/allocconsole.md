---
title: "\"Zuweisung\"-Funktion"
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "Zuweisung", die eine neue Konsole für den aufrufenden Prozess zugeordnet.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: db010f60f1661d67e77de841fc243c24f32e2d1f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037508"
---
# <a name="allocconsole-function"></a><span data-ttu-id="cb83a-104">"Zuweisung"-Funktion</span><span class="sxs-lookup"><span data-stu-id="cb83a-104">AllocConsole function</span></span>

<span data-ttu-id="cb83a-105">Weist eine neue Konsole für den aufrufenden Prozess zu.</span><span class="sxs-lookup"><span data-stu-id="cb83a-105">Allocates a new console for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb83a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cb83a-106">Syntax</span></span>

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="cb83a-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="cb83a-107">Parameters</span></span>

<span data-ttu-id="cb83a-108">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="cb83a-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="cb83a-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="cb83a-109">Return value</span></span>

<span data-ttu-id="cb83a-110">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="cb83a-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="cb83a-111">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="cb83a-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="cb83a-112">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="cb83a-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="cb83a-113">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="cb83a-113">Remarks</span></span>

<span data-ttu-id="cb83a-114">Ein Prozess kann nur mit einer Konsole verknüpft werden, sodass die Funktion " **Zuordnungs Konsole** " fehlschlägt, wenn der aufrufende Prozess bereits über eine Konsole verfügt.</span><span class="sxs-lookup"><span data-stu-id="cb83a-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="cb83a-115">Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich von der aktuellen Konsole zu trennen, und dann kann die Zuweisung von "- **Konsole** " zum Erstellen einer neuen Konsole oder einer [**attachconsole**](attachconsole.md) zum Anfügen an eine andere Konsole durchführen.</span><span class="sxs-lookup"><span data-stu-id="cb83a-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="cb83a-116">Wenn der aufrufenden Prozess einen untergeordneten Prozess erstellt, erbt das untergeordnete Element die neue Konsole.</span><span class="sxs-lookup"><span data-stu-id="cb83a-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="cb83a-117">" **Zugskonsole** " initialisiert Standard Eingaben, Standardausgabe und Standardfehler Handles für die neue Konsole.</span><span class="sxs-lookup"><span data-stu-id="cb83a-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="cb83a-118">Das Standardeingabe Handle ist ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe und Standardfehler Handles sind Handles für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="cb83a-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="cb83a-119">Um diese Handles abzurufen, verwenden Sie die [**getstdhandle**](getstdhandle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="cb83a-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="cb83a-120">Diese Funktion wird hauptsächlich von einer grafischen Benutzeroberflächen Anwendung (GUI) zum Erstellen eines Konsolenfensters verwendet.</span><span class="sxs-lookup"><span data-stu-id="cb83a-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="cb83a-121">GUI-Anwendungen werden ohne eine-Konsole initialisiert.</span><span class="sxs-lookup"><span data-stu-id="cb83a-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="cb83a-122">Konsolen Anwendungen werden mit einer-Konsole initialisiert, es sei denn, Sie werden als getrennte Prozesse erstellt (durch Aufrufen der [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) -Funktion mit dem getrennten **\_ prozessflag** ).</span><span class="sxs-lookup"><span data-stu-id="cb83a-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function with the **DETACHED\_PROCESS** flag).</span></span>

## <a name="requirements"></a><span data-ttu-id="cb83a-123">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="cb83a-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="cb83a-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="cb83a-124">Minimum supported client</span></span> | <span data-ttu-id="cb83a-125">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="cb83a-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="cb83a-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="cb83a-126">Minimum supported server</span></span> | <span data-ttu-id="cb83a-127">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="cb83a-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="cb83a-128">Header</span><span class="sxs-lookup"><span data-stu-id="cb83a-128">Header</span></span> | <span data-ttu-id="cb83a-129">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="cb83a-129">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="cb83a-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="cb83a-130">Library</span></span> | <span data-ttu-id="cb83a-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="cb83a-131">Kernel32.lib</span></span> |
| <span data-ttu-id="cb83a-132">DLL</span><span class="sxs-lookup"><span data-stu-id="cb83a-132">DLL</span></span> | <span data-ttu-id="cb83a-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="cb83a-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="cb83a-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cb83a-134">See also</span></span>

[<span data-ttu-id="cb83a-135">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="cb83a-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="cb83a-136">Trö</span><span class="sxs-lookup"><span data-stu-id="cb83a-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="cb83a-137">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="cb83a-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="cb83a-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="cb83a-138">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="cb83a-139">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="cb83a-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="cb83a-140">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="cb83a-140">**GetStdHandle**</span></span>](getstdhandle.md)
