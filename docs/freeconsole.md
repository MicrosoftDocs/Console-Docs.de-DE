---
title: Freeconsole-Funktion
description: Siehe Referenzinformationen zur freeconsole-Funktion, die den aufrufenden Prozess von seiner Konsole trennt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 3c8ba7b236b379bb57729538e065afebb68cc0cf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059867"
---
# <a name="freeconsole-function"></a><span data-ttu-id="e03e8-104">Freeconsole-Funktion</span><span class="sxs-lookup"><span data-stu-id="e03e8-104">FreeConsole function</span></span>


<span data-ttu-id="e03e8-105">Trennt den aufrufenden Prozess von seiner Konsole aus.</span><span class="sxs-lookup"><span data-stu-id="e03e8-105">Detaches the calling process from its console.</span></span>

<a name="syntax"></a><span data-ttu-id="e03e8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e03e8-106">Syntax</span></span>
------

```C
BOOL WINAPI FreeConsole(void);
```

<a name="parameters"></a><span data-ttu-id="e03e8-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="e03e8-107">Parameters</span></span>
----------

<span data-ttu-id="e03e8-108">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="e03e8-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="e03e8-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e03e8-109">Return value</span></span>
------------

<span data-ttu-id="e03e8-110">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="e03e8-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e03e8-111">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="e03e8-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e03e8-112">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e03e8-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="e03e8-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e03e8-113">Remarks</span></span>
-------

<span data-ttu-id="e03e8-114">Ein Prozess kann höchstens an eine Konsole angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="e03e8-114">A process can be attached to at most one console.</span></span> <span data-ttu-id="e03e8-115">Wenn der Aufrufprozess nicht bereits an eine Konsole angefügt ist, lautet der Fehlercode **" \_ ungültiger \_ Parameter** " (87).</span><span class="sxs-lookup"><span data-stu-id="e03e8-115">If the calling process is not already attached to a console, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="e03e8-116">Ein Prozess kann die **freeconsole** -Funktion verwenden, um sich von seiner Konsole zu trennen.</span><span class="sxs-lookup"><span data-stu-id="e03e8-116">A process can use the **FreeConsole** function to detach itself from its console.</span></span> <span data-ttu-id="e03e8-117">Wenn andere Prozesse die-Konsole gemeinsam nutzen, wird die Konsole nicht zerstört, aber der Prozess, der **freeconsole** aufgerufen hat, kann nicht darauf verweisen.</span><span class="sxs-lookup"><span data-stu-id="e03e8-117">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="e03e8-118">Eine Konsole wird geschlossen, wenn der letzte daran angefügte Prozess beendet wird oder **freeconsole**aufruft.</span><span class="sxs-lookup"><span data-stu-id="e03e8-118">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="e03e8-119">Nachdem ein Prozess **freeconsole**aufgerufen hat, kann er die Funktion " [**Zuweisung**](allocconsole.md) " aufrufen, um eine neue Konsole [**oder eine**](attachconsole.md) anfügekonsole zum Anfügen an eine andere Konsole zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e03e8-119">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<a name="requirements"></a><span data-ttu-id="e03e8-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e03e8-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e03e8-121">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="e03e8-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e03e8-122">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="e03e8-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e03e8-123">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="e03e8-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e03e8-124">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="e03e8-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e03e8-125">Header</span><span class="sxs-lookup"><span data-stu-id="e03e8-125">Header</span></span></p></td>
<td><span data-ttu-id="e03e8-126">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e03e8-126">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e03e8-127">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e03e8-127">Library</span></span></p></td>
<td><span data-ttu-id="e03e8-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e03e8-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e03e8-129">DLL</span><span class="sxs-lookup"><span data-stu-id="e03e8-129">DLL</span></span></p></td>
<td><span data-ttu-id="e03e8-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e03e8-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e03e8-131"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e03e8-131"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e03e8-132">**"Zuweisung"-Konsole**</span><span class="sxs-lookup"><span data-stu-id="e03e8-132">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="e03e8-133">**Attachconsole**</span><span class="sxs-lookup"><span data-stu-id="e03e8-133">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="e03e8-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="e03e8-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e03e8-135">Trö</span><span class="sxs-lookup"><span data-stu-id="e03e8-135">Consoles</span></span>](consoles.md)

 

 




