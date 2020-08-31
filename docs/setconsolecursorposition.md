---
title: SetConsoleCursorPosition-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur SetConsoleCursorPosition-Funktion, mit der die Cursorposition im angegebenen Konsolenbildschirm Puffer festgelegt wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: eaa50df16248597f1054f0741113ecc9be1f3264
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060274"
---
# <a name="setconsolecursorposition-function"></a><span data-ttu-id="0fb9c-104">SetConsoleCursorPosition-Funktion</span><span class="sxs-lookup"><span data-stu-id="0fb9c-104">SetConsoleCursorPosition function</span></span>


<span data-ttu-id="0fb9c-105">Legt die Cursorposition im angegebenen Konsolenbildschirm Puffer fest.</span><span class="sxs-lookup"><span data-stu-id="0fb9c-105">Sets the cursor position in the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="0fb9c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0fb9c-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

<a name="parameters"></a><span data-ttu-id="0fb9c-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="0fb9c-107">Parameters</span></span>
----------

<span data-ttu-id="0fb9c-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0fb9c-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="0fb9c-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="0fb9c-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="0fb9c-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="0fb9c-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="0fb9c-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="0fb9c-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="0fb9c-112">*dwcurrsorposition* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0fb9c-112">*dwCursorPosition* \[in\]</span></span>  
<span data-ttu-id="0fb9c-113">Eine [**Koord**](coord-str.md) -Struktur, die die neue Cursorposition in Zeichen angibt.</span><span class="sxs-lookup"><span data-stu-id="0fb9c-113">A [**COORD**](coord-str.md) structure that specifies the new cursor position, in characters.</span></span> <span data-ttu-id="0fb9c-114">Die Koordinaten sind die Spalte und die Zeile einer Bildschirm Puffer-Zeichen Zelle.</span><span class="sxs-lookup"><span data-stu-id="0fb9c-114">The coordinates are the column and row of a screen buffer character cell.</span></span> <span data-ttu-id="0fb9c-115">Die Koordinaten müssen sich innerhalb der Grenzen des Konsolenbildschirm Puffers befinden.</span><span class="sxs-lookup"><span data-stu-id="0fb9c-115">The coordinates must be within the boundaries of the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="0fb9c-116">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="0fb9c-116">Return value</span></span>
------------

<span data-ttu-id="0fb9c-117">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="0fb9c-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0fb9c-118">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="0fb9c-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0fb9c-119">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="0fb9c-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="0fb9c-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0fb9c-120">Remarks</span></span>
-------

<span data-ttu-id="0fb9c-121">Die Cursorposition bestimmt, wo Zeichen, die von der Funktion " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder " [**Write-Console**](writeconsole.md) " geschrieben wurden oder von der Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](readconsole.md) " angezeigt werden, angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0fb9c-121">The cursor position determines where characters written by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function, are displayed.</span></span> <span data-ttu-id="0fb9c-122">Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die aktuelle Position des Cursors zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="0fb9c-122">To determine the current position of the cursor, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="0fb9c-123">Wenn sich die neue Cursorposition nicht innerhalb der Grenzen des Fensters des Konsolenbildschirm Puffers befindet, wird der Fenster Ursprung geändert, um den Cursor sichtbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="0fb9c-123">If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.</span></span>

<a name="examples"></a><span data-ttu-id="0fb9c-124">Beispiele</span><span class="sxs-lookup"><span data-stu-id="0fb9c-124">Examples</span></span>
--------

<span data-ttu-id="0fb9c-125">Ein Beispiel finden Sie unter [Verwenden der übergeordneten Eingabe-und Ausgabefunktionen](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0fb9c-125">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

<a name="requirements"></a><span data-ttu-id="0fb9c-126">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0fb9c-126">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0fb9c-127">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="0fb9c-127">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0fb9c-128">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="0fb9c-128">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0fb9c-129">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="0fb9c-129">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0fb9c-130">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="0fb9c-130">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0fb9c-131">Header</span><span class="sxs-lookup"><span data-stu-id="0fb9c-131">Header</span></span></p></td>
<td><span data-ttu-id="0fb9c-132">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0fb9c-132">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0fb9c-133">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="0fb9c-133">Library</span></span></p></td>
<td><span data-ttu-id="0fb9c-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="0fb9c-134">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0fb9c-135">DLL</span><span class="sxs-lookup"><span data-stu-id="0fb9c-135">DLL</span></span></p></td>
<td><span data-ttu-id="0fb9c-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0fb9c-136">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0fb9c-137"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0fb9c-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0fb9c-138">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="0fb9c-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0fb9c-139">Konsolenbildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="0fb9c-139">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="0fb9c-140">**Getconsolecursorinfo**</span><span class="sxs-lookup"><span data-stu-id="0fb9c-140">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="0fb9c-141">**Getconsoleskreenbufferinfo**</span><span class="sxs-lookup"><span data-stu-id="0fb9c-141">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="0fb9c-142">**"Read Console"**</span><span class="sxs-lookup"><span data-stu-id="0fb9c-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="0fb9c-143">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="0fb9c-143">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="0fb9c-144">**Setconsolecursorinfo**</span><span class="sxs-lookup"><span data-stu-id="0fb9c-144">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

[<span data-ttu-id="0fb9c-145">**Schreib Konsole**</span><span class="sxs-lookup"><span data-stu-id="0fb9c-145">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="0fb9c-146">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="0fb9c-146">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




