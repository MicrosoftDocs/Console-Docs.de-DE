---
title: Flushconsoleingeputbuffer-Funktion
description: Leert den Konsolen Eingabepuffer. Alle Eingabedaten Sätze, die sich derzeit im Eingabepuffer befinden, werden verworfen.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/FlushConsoleInputBuffer
- wincon/FlushConsoleInputBuffer
- FlushConsoleInputBuffer
MS-HAID:
- '\_win32\_flushconsoleinputbuffer'
- base.flushconsoleinputbuffer
- consoles.flushconsoleinputbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6f7832d6-1fb2-4ca8-bd07-43123c990851
topic_type:
- apiref
api_name:
- FlushConsoleInputBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dd184e1fc1f788912be00e9270ccb239c20b8ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059875"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="3e36d-105">Flushconsoleingeputbuffer-Funktion</span><span class="sxs-lookup"><span data-stu-id="3e36d-105">FlushConsoleInputBuffer function</span></span>


<span data-ttu-id="3e36d-106">Leert den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="3e36d-106">Flushes the console input buffer.</span></span> <span data-ttu-id="3e36d-107">Alle Eingabedaten Sätze, die sich derzeit im Eingabepuffer befinden, werden verworfen.</span><span class="sxs-lookup"><span data-stu-id="3e36d-107">All input records currently in the input buffer are discarded.</span></span>

<a name="syntax"></a><span data-ttu-id="3e36d-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="3e36d-108">Syntax</span></span>
------

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

<a name="parameters"></a><span data-ttu-id="3e36d-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="3e36d-109">Parameters</span></span>
----------

<span data-ttu-id="3e36d-110">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="3e36d-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="3e36d-111">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="3e36d-111">A handle to the console input buffer.</span></span> <span data-ttu-id="3e36d-112">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="3e36d-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="3e36d-113">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="3e36d-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<a name="return-value"></a><span data-ttu-id="3e36d-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="3e36d-114">Return value</span></span>
------------

<span data-ttu-id="3e36d-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="3e36d-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3e36d-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="3e36d-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3e36d-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="3e36d-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="3e36d-118">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="3e36d-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="3e36d-119">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="3e36d-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="3e36d-120">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="3e36d-120">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3e36d-121">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="3e36d-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="3e36d-122">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="3e36d-122">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3e36d-123">Header</span><span class="sxs-lookup"><span data-stu-id="3e36d-123">Header</span></span></p></td>
<td><span data-ttu-id="3e36d-124">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3e36d-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3e36d-125">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="3e36d-125">Library</span></span></p></td>
<td><span data-ttu-id="3e36d-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="3e36d-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3e36d-127">DLL</span><span class="sxs-lookup"><span data-stu-id="3e36d-127">DLL</span></span></p></td>
<td><span data-ttu-id="3e36d-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3e36d-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="3e36d-129"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3e36d-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="3e36d-130">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="3e36d-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3e36d-131">Konsolen Eingabefunktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="3e36d-131">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="3e36d-132">**Getnumofconsoleinputevents**</span><span class="sxs-lookup"><span data-stu-id="3e36d-132">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="3e36d-133">**"Etekconsoleinput"**</span><span class="sxs-lookup"><span data-stu-id="3e36d-133">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="3e36d-134">**Read ConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="3e36d-134">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="3e36d-135">**Schreibconsoleinput**</span><span class="sxs-lookup"><span data-stu-id="3e36d-135">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




