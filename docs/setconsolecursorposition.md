---
title: SetConsoleCursorPosition-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur SetConsoleCursorPosition-Funktion, mit der die Cursorposition im angegebenen Konsolenbildschirm Puffer festgelegt wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: c93fbf4b619b522a95af2b03a49d60ff6f880e7d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039368"
---
# <a name="setconsolecursorposition-function"></a><span data-ttu-id="42002-104">SetConsoleCursorPosition-Funktion</span><span class="sxs-lookup"><span data-stu-id="42002-104">SetConsoleCursorPosition function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="42002-105">Legt die Cursorposition im angegebenen Konsolenbildschirm Puffer fest.</span><span class="sxs-lookup"><span data-stu-id="42002-105">Sets the cursor position in the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="42002-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="42002-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a><span data-ttu-id="42002-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="42002-107">Parameters</span></span>

<span data-ttu-id="42002-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="42002-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="42002-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="42002-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="42002-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="42002-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="42002-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="42002-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="42002-112">*dwcurrsorposition* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="42002-112">*dwCursorPosition* \[in\]</span></span>  
<span data-ttu-id="42002-113">Eine [**Koord**](coord-str.md) -Struktur, die die neue Cursorposition in Zeichen angibt.</span><span class="sxs-lookup"><span data-stu-id="42002-113">A [**COORD**](coord-str.md) structure that specifies the new cursor position, in characters.</span></span> <span data-ttu-id="42002-114">Die Koordinaten sind die Spalte und die Zeile einer Bildschirm Puffer-Zeichen Zelle.</span><span class="sxs-lookup"><span data-stu-id="42002-114">The coordinates are the column and row of a screen buffer character cell.</span></span> <span data-ttu-id="42002-115">Die Koordinaten müssen sich innerhalb der Grenzen des Konsolenbildschirm Puffers befinden.</span><span class="sxs-lookup"><span data-stu-id="42002-115">The coordinates must be within the boundaries of the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="42002-116">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="42002-116">Return value</span></span>

<span data-ttu-id="42002-117">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="42002-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="42002-118">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="42002-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="42002-119">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="42002-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="42002-120">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="42002-120">Remarks</span></span>

<span data-ttu-id="42002-121">Die Cursorposition bestimmt, wo Zeichen, die von der Funktion " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder " [**Write-Console**](writeconsole.md) " geschrieben wurden oder von der Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](readconsole.md) " angezeigt werden, angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="42002-121">The cursor position determines where characters written by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function, are displayed.</span></span> <span data-ttu-id="42002-122">Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die aktuelle Position des Cursors zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="42002-122">To determine the current position of the cursor, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="42002-123">Wenn sich die neue Cursorposition nicht innerhalb der Grenzen des Fensters des Konsolenbildschirm Puffers befindet, wird der Fenster Ursprung geändert, um den Cursor sichtbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="42002-123">If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.</span></span>

> [!TIP]
> <span data-ttu-id="42002-124">Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent in den Abschnitten **[einfache Cursor Positionierung](console-virtual-terminal-sequences.md#simple-cursor-positioning)** und **[Cursor Positionierung](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="42002-124">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[simple cursor positioning](console-virtual-terminal-sequences.md#simple-cursor-positioning)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sections.</span></span> <span data-ttu-id="42002-125">Die Verwendung von Zeilenumbruch-, Wagen Rücklauf-, Rücktaste-und Registerkarten-Steuersequenzen kann bei der Cursor Positionierung ebenfalls hilfreich sein.</span><span class="sxs-lookup"><span data-stu-id="42002-125">Use of the newline, carriage return, backspace, and tab control sequences can also assist with cursor positioning.</span></span>

## <a name="examples"></a><span data-ttu-id="42002-126">Beispiele</span><span class="sxs-lookup"><span data-stu-id="42002-126">Examples</span></span>

<span data-ttu-id="42002-127">Ein Beispiel finden Sie unter [Verwenden der High-Level Eingabe-und Ausgabefunktionen](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="42002-127">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="42002-128">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="42002-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="42002-129">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="42002-129">Minimum supported client</span></span> | <span data-ttu-id="42002-130">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="42002-130">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="42002-131">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="42002-131">Minimum supported server</span></span> | <span data-ttu-id="42002-132">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="42002-132">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="42002-133">Header</span><span class="sxs-lookup"><span data-stu-id="42002-133">Header</span></span> | <span data-ttu-id="42002-134">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="42002-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="42002-135">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="42002-135">Library</span></span> | <span data-ttu-id="42002-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="42002-136">Kernel32.lib</span></span> |
| <span data-ttu-id="42002-137">DLL</span><span class="sxs-lookup"><span data-stu-id="42002-137">DLL</span></span> | <span data-ttu-id="42002-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="42002-138">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="42002-139">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="42002-139">See also</span></span>

[<span data-ttu-id="42002-140">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="42002-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="42002-141">Konsolenbildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="42002-141">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="42002-142">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="42002-142">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="42002-143">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="42002-143">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="42002-144">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="42002-144">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="42002-145">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="42002-145">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="42002-146">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="42002-146">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

[<span data-ttu-id="42002-147">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="42002-147">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="42002-148">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="42002-148">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
