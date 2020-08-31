---
title: Setconsoledisplaymode-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur setconsoledisplaymode-Funktion, mit der der Anzeigemodus des angegebenen Konsolenbildschirm Puffers festgelegt wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0d4564b9a7562fb495c9834df98708d5faff5334
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060106"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="e2276-104">Setconsoledisplaymode-Funktion</span><span class="sxs-lookup"><span data-stu-id="e2276-104">SetConsoleDisplayMode function</span></span>


<span data-ttu-id="e2276-105">Legt den Anzeigemodus des angegebenen Konsolenbildschirm Puffers fest.</span><span class="sxs-lookup"><span data-stu-id="e2276-105">Sets the display mode of the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="e2276-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e2276-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

<a name="parameters"></a><span data-ttu-id="e2276-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="e2276-107">Parameters</span></span>
----------

<span data-ttu-id="e2276-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e2276-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="e2276-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="e2276-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="e2276-110">*dwFlags* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e2276-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="e2276-111">Der Anzeigemodus der Konsole.</span><span class="sxs-lookup"><span data-stu-id="e2276-111">The display mode of the console.</span></span> <span data-ttu-id="e2276-112">Dieser Parameter kann einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="e2276-112">This parameter can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e2276-113">Wert</span><span class="sxs-lookup"><span data-stu-id="e2276-113">Value</span></span></th>
<th><span data-ttu-id="e2276-114">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="e2276-114">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="e2276-115"><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong> 1</span><span class="sxs-lookup"><span data-stu-id="e2276-115"><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong> 1</span></span></td>
<td><p><span data-ttu-id="e2276-116">Der Text wird im Vollbildmodus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e2276-116">Text is displayed in full-screen mode.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e2276-117"><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong> 2</span><span class="sxs-lookup"><span data-stu-id="e2276-117"><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong> 2</span></span></td>
<td><p><span data-ttu-id="e2276-118">Der Text wird in einem Konsolenfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e2276-118">Text is displayed in a console window.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="e2276-119">*lpnewscreenbufferdimensions* \[ Out, optional\]</span><span class="sxs-lookup"><span data-stu-id="e2276-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="e2276-120">Ein Zeiger auf eine [**Koord**](coord-str.md) -Struktur, die die neuen Abmessungen des Bildschirm Puffers empfängt, in Zeichen.</span><span class="sxs-lookup"><span data-stu-id="e2276-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="e2276-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e2276-121">Return value</span></span>
------------

<span data-ttu-id="e2276-122">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="e2276-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e2276-123">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="e2276-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e2276-124">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e2276-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="e2276-125">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e2276-125">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e2276-126">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="e2276-126">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e2276-127">Windows XP [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="e2276-127">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e2276-128">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="e2276-128">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e2276-129">Windows Server 2003 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="e2276-129">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e2276-130">Header</span><span class="sxs-lookup"><span data-stu-id="e2276-130">Header</span></span></p></td>
<td><span data-ttu-id="e2276-131">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e2276-131">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e2276-132">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e2276-132">Library</span></span></p></td>
<td><span data-ttu-id="e2276-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e2276-133">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e2276-134">DLL</span><span class="sxs-lookup"><span data-stu-id="e2276-134">DLL</span></span></p></td>
<td><span data-ttu-id="e2276-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e2276-135">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e2276-136"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e2276-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e2276-137">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="e2276-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e2276-138">Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="e2276-138">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="e2276-139">**Getconsoledisplaymode**</span><span class="sxs-lookup"><span data-stu-id="e2276-139">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)

 

 




