---
title: "\"Zuweisung\"-Funktion"
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "Zuweisung", die eine neue Konsole für den aufrufenden Prozess zugeordnet.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 2e06cdc82c4e58dd09b99fa08bf4917ad37b552f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060243"
---
# <a name="allocconsole-function"></a><span data-ttu-id="22ef5-104">"Zuweisung"-Funktion</span><span class="sxs-lookup"><span data-stu-id="22ef5-104">AllocConsole function</span></span>


<span data-ttu-id="22ef5-105">Weist eine neue Konsole für den aufrufenden Prozess zu.</span><span class="sxs-lookup"><span data-stu-id="22ef5-105">Allocates a new console for the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="22ef5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="22ef5-106">Syntax</span></span>
------

```C
BOOL WINAPI AllocConsole(void);
```

<a name="parameters"></a><span data-ttu-id="22ef5-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="22ef5-107">Parameters</span></span>
----------

<span data-ttu-id="22ef5-108">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="22ef5-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="22ef5-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="22ef5-109">Return value</span></span>
------------

<span data-ttu-id="22ef5-110">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="22ef5-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="22ef5-111">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="22ef5-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="22ef5-112">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="22ef5-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="22ef5-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="22ef5-113">Remarks</span></span>
-------

<span data-ttu-id="22ef5-114">Ein Prozess kann nur mit einer Konsole verknüpft werden, sodass die Funktion " **Zuordnungs Konsole** " fehlschlägt, wenn der aufrufende Prozess bereits über eine Konsole verfügt.</span><span class="sxs-lookup"><span data-stu-id="22ef5-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="22ef5-115">Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich von der aktuellen Konsole zu trennen, und dann kann die Zuweisung von "- **Konsole** " zum Erstellen einer neuen Konsole oder einer [**attachconsole**](attachconsole.md) zum Anfügen an eine andere Konsole durchführen.</span><span class="sxs-lookup"><span data-stu-id="22ef5-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="22ef5-116">Wenn der aufrufenden Prozess einen untergeordneten Prozess erstellt, erbt das untergeordnete Element die neue Konsole.</span><span class="sxs-lookup"><span data-stu-id="22ef5-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="22ef5-117">" **Zugskonsole** " initialisiert Standard Eingaben, Standardausgabe und Standardfehler Handles für die neue Konsole.</span><span class="sxs-lookup"><span data-stu-id="22ef5-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="22ef5-118">Das Standardeingabe Handle ist ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe und Standardfehler Handles sind Handles für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="22ef5-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="22ef5-119">Um diese Handles abzurufen, verwenden Sie die [**getstdhandle**](getstdhandle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="22ef5-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="22ef5-120">Diese Funktion wird hauptsächlich von einer grafischen Benutzeroberflächen Anwendung (GUI) zum Erstellen eines Konsolenfensters verwendet.</span><span class="sxs-lookup"><span data-stu-id="22ef5-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="22ef5-121">GUI-Anwendungen werden ohne eine-Konsole initialisiert.</span><span class="sxs-lookup"><span data-stu-id="22ef5-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="22ef5-122">Konsolen Anwendungen werden mit einer-Konsole initialisiert, es sei denn, Sie werden als getrennte Prozesse erstellt (durch Aufrufen der [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) -Funktion mit dem getrennten \*\* \_ prozessflag\*\* ).</span><span class="sxs-lookup"><span data-stu-id="22ef5-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function with the **DETACHED\_PROCESS** flag).</span></span>

<a name="requirements"></a><span data-ttu-id="22ef5-123">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="22ef5-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="22ef5-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="22ef5-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="22ef5-125">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="22ef5-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="22ef5-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="22ef5-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="22ef5-127">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="22ef5-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="22ef5-128">Header</span><span class="sxs-lookup"><span data-stu-id="22ef5-128">Header</span></span></p></td>
<td><span data-ttu-id="22ef5-129">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="22ef5-129">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="22ef5-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="22ef5-130">Library</span></span></p></td>
<td><span data-ttu-id="22ef5-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="22ef5-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="22ef5-132">DLL</span><span class="sxs-lookup"><span data-stu-id="22ef5-132">DLL</span></span></p></td>
<td><span data-ttu-id="22ef5-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="22ef5-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="22ef5-134"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="22ef5-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="22ef5-135">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="22ef5-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="22ef5-136">Trö</span><span class="sxs-lookup"><span data-stu-id="22ef5-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="22ef5-137">**Attachconsole**</span><span class="sxs-lookup"><span data-stu-id="22ef5-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="22ef5-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="22ef5-138">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="22ef5-139">**Freeconsole**</span><span class="sxs-lookup"><span data-stu-id="22ef5-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="22ef5-140">**Getstdhandle**</span><span class="sxs-lookup"><span data-stu-id="22ef5-140">**GetStdHandle**</span></span>](getstdhandle.md)

 

 




