---
title: Getconsoledisplaymode-Funktion
description: Siehe Referenzinformationen zur getconsoledisplaymode-Funktion, die den Anzeigemodus der aktuellen Konsole abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 76b3354ac9b44c36ec4cfe3d12257583d10f2ee2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059811"
---
# <a name="getconsoledisplaymode-function"></a><span data-ttu-id="4766d-104">Getconsoledisplaymode-Funktion</span><span class="sxs-lookup"><span data-stu-id="4766d-104">GetConsoleDisplayMode function</span></span>


<span data-ttu-id="4766d-105">Ruft den Anzeigemodus der aktuellen Konsole ab.</span><span class="sxs-lookup"><span data-stu-id="4766d-105">Retrieves the display mode of the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="4766d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4766d-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

<a name="parameters"></a><span data-ttu-id="4766d-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="4766d-107">Parameters</span></span>
----------

<span data-ttu-id="4766d-108">*lpmodeflags* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="4766d-108">*lpModeFlags* \[out\]</span></span>  
<span data-ttu-id="4766d-109">Der Anzeigemodus der Konsole.</span><span class="sxs-lookup"><span data-stu-id="4766d-109">The display mode of the console.</span></span> <span data-ttu-id="4766d-110">Dieser Parameter kann einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="4766d-110">This parameter can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="4766d-111">Wert</span><span class="sxs-lookup"><span data-stu-id="4766d-111">Value</span></span></th>
<th><span data-ttu-id="4766d-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="4766d-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="4766d-113"><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</span><span class="sxs-lookup"><span data-stu-id="4766d-113"><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</span></span></td>
<td><p><span data-ttu-id="4766d-114">Voll Bild Konsole.</span><span class="sxs-lookup"><span data-stu-id="4766d-114">Full-screen console.</span></span> <span data-ttu-id="4766d-115">Die Konsole befindet sich in diesem Modus, sobald das Fenster maximiert ist.</span><span class="sxs-lookup"><span data-stu-id="4766d-115">The console is in this mode as soon as the window is maximized.</span></span> <span data-ttu-id="4766d-116">An diesem Punkt kann der Übergang zum Vollbildmodus weiterhin fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="4766d-116">At this point, the transition to full-screen mode can still fail.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="4766d-117"><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</span><span class="sxs-lookup"><span data-stu-id="4766d-117"><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</span></span></td>
<td><p><span data-ttu-id="4766d-118">Voll Bild Konsole, die direkt mit der Video Hardware kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="4766d-118">Full-screen console communicating directly with the video hardware.</span></span> <span data-ttu-id="4766d-119">Dieser Modus wird festgelegt, nachdem sich die Konsole im <strong>CONSOLE_FULLSCREEN</strong> Modus befindet, um anzugeben, dass der Übergang zum Vollbildmodus abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="4766d-119">This mode is set after the console is in <strong>CONSOLE_FULLSCREEN</strong> mode to indicate that the transition to full-screen mode has completed.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="4766d-120">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="4766d-120">Return value</span></span>
------------

<span data-ttu-id="4766d-121">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="4766d-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4766d-122">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="4766d-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4766d-123">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4766d-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="4766d-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4766d-124">Remarks</span></span>
-------

<span data-ttu-id="4766d-125">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="4766d-125">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="4766d-126">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="4766d-126">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="4766d-127">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="4766d-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4766d-128">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="4766d-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4766d-129">Windows XP [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="4766d-129">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4766d-130">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="4766d-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4766d-131">Windows Server 2003 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="4766d-131">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4766d-132">Header</span><span class="sxs-lookup"><span data-stu-id="4766d-132">Header</span></span></p></td>
<td><span data-ttu-id="4766d-133">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4766d-133">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4766d-134">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="4766d-134">Library</span></span></p></td>
<td><span data-ttu-id="4766d-135">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4766d-135">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4766d-136">DLL</span><span class="sxs-lookup"><span data-stu-id="4766d-136">DLL</span></span></p></td>
<td><span data-ttu-id="4766d-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4766d-137">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4766d-138"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4766d-138"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4766d-139">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="4766d-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4766d-140">Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="4766d-140">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="4766d-141">**Setconsoledisplaymode**</span><span class="sxs-lookup"><span data-stu-id="4766d-141">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

 

 




