---
title: Setstdhandle-Funktion
description: Legt das Handle für das angegebene Standardgerät (Standardeingabe, Standardausgabe oder Standardfehler) fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 6ab17a2162d31c956ec64dbb33696c20ae085298
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060531"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="c6ddb-104">Setstdhandle-Funktion</span><span class="sxs-lookup"><span data-stu-id="c6ddb-104">SetStdHandle function</span></span>


<span data-ttu-id="c6ddb-105">Legt das Handle für das angegebene Standardgerät (Standardeingabe, Standardausgabe oder Standardfehler) fest.</span><span class="sxs-lookup"><span data-stu-id="c6ddb-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

<a name="syntax"></a><span data-ttu-id="c6ddb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c6ddb-106">Syntax</span></span>
------

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

<a name="parameters"></a><span data-ttu-id="c6ddb-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="c6ddb-107">Parameters</span></span>
----------

<span data-ttu-id="c6ddb-108">*nstdhandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c6ddb-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="c6ddb-109">Das Standardgerät, für das das Handle festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c6ddb-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="c6ddb-110">Dieser Parameter kann einen der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="c6ddb-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="c6ddb-111">Wert</span><span class="sxs-lookup"><span data-stu-id="c6ddb-111">Value</span></span></th>
<th><span data-ttu-id="c6ddb-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="c6ddb-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="c6ddb-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="c6ddb-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span></span></td>
<td><p><span data-ttu-id="c6ddb-114">Das Standardeingabe Gerät.</span><span class="sxs-lookup"><span data-stu-id="c6ddb-114">The standard input device.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="c6ddb-115"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="c6ddb-115"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span></span></td>
<td><p><span data-ttu-id="c6ddb-116">Das Standardausgabe Gerät.</span><span class="sxs-lookup"><span data-stu-id="c6ddb-116">The standard output device.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="c6ddb-117"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="c6ddb-117"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span></span></td>
<td><p><span data-ttu-id="c6ddb-118">Das Standardfehler Gerät.</span><span class="sxs-lookup"><span data-stu-id="c6ddb-118">The standard error device.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="c6ddb-119">*hHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c6ddb-119">*hHandle* \[in\]</span></span>  
<span data-ttu-id="c6ddb-120">Das Handle für das Standardgerät.</span><span class="sxs-lookup"><span data-stu-id="c6ddb-120">The handle for the standard device.</span></span>

<a name="return-value"></a><span data-ttu-id="c6ddb-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c6ddb-121">Return value</span></span>
------------

<span data-ttu-id="c6ddb-122">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="c6ddb-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c6ddb-123">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="c6ddb-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c6ddb-124">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="c6ddb-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="c6ddb-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c6ddb-125">Remarks</span></span>
-------

<span data-ttu-id="c6ddb-126">Die Standard Handles eines Prozesses wurden möglicherweise durch einen Aufrufen von **setstdhandle**umgeleitet. in diesem Fall gibt [**getstdhandle**](getstdhandle.md) das umgeleitete Handle zurück.</span><span class="sxs-lookup"><span data-stu-id="c6ddb-126">The standard handles of a process may have been redirected by a call to **SetStdHandle**, in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="c6ddb-127">Wenn die Standard Handles umgeleitet wurden, können Sie den Wert von "$" in einem Aufrufen der Funktion "angleichen [**Datei**](https://msdn.microsoft.com/library/windows/desktop/aa363858) " angeben, um ein Handle für den Eingabepuffer einer Konsole abzurufen.</span><span class="sxs-lookup"><span data-stu-id="c6ddb-127">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="c6ddb-128">Entsprechend können Sie den Wert für "$ $" angeben, um ein Handle für den aktiven Bildschirm Puffer der Konsole zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c6ddb-128">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

<a name="examples"></a><span data-ttu-id="c6ddb-129">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c6ddb-129">Examples</span></span>
--------

<span data-ttu-id="c6ddb-130">Ein Beispiel finden Sie unter [Erstellen eines untergeordneten Prozesses mit umgeleiteter Eingabe und Ausgabe](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span><span class="sxs-lookup"><span data-stu-id="c6ddb-130">For an example, see [Creating a Child Process with Redirected Input and Output](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span></span>

<a name="requirements"></a><span data-ttu-id="c6ddb-131">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c6ddb-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c6ddb-132">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="c6ddb-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c6ddb-133">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="c6ddb-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c6ddb-134">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="c6ddb-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c6ddb-135">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="c6ddb-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c6ddb-136">Header</span><span class="sxs-lookup"><span data-stu-id="c6ddb-136">Header</span></span></p></td>
<td><span data-ttu-id="c6ddb-137">Processenv. h (über Winbase. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c6ddb-137">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c6ddb-138">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="c6ddb-138">Library</span></span></p></td>
<td><span data-ttu-id="c6ddb-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c6ddb-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c6ddb-140">DLL</span><span class="sxs-lookup"><span data-stu-id="c6ddb-140">DLL</span></span></p></td>
<td><span data-ttu-id="c6ddb-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c6ddb-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c6ddb-142"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c6ddb-142"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c6ddb-143">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="c6ddb-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c6ddb-144">Konsolen Handles</span><span class="sxs-lookup"><span data-stu-id="c6ddb-144">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="c6ddb-145">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="c6ddb-145">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="c6ddb-146">**Getstdhandle**</span><span class="sxs-lookup"><span data-stu-id="c6ddb-146">**GetStdHandle**</span></span>](getstdhandle.md)

 

 




