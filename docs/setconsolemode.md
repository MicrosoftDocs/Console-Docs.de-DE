---
title: SetConsoleMode-Funktion
description: Legt den Eingabemodus des Eingabepuffers einer Konsole oder den Ausgabemodus des Bildschirmpuffers einer Konsole fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 2af598f465be6e1a33f5a8f9a2c9abe98d6ed0d2
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420299"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="c6449-104">SetConsoleMode-Funktion</span><span class="sxs-lookup"><span data-stu-id="c6449-104">SetConsoleMode function</span></span>

<span data-ttu-id="c6449-105">Legt den Eingabemodus des Eingabepuffers einer Konsole oder den Ausgabemodus des Bildschirmpuffers einer Konsole fest.</span><span class="sxs-lookup"><span data-stu-id="c6449-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6449-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c6449-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a><span data-ttu-id="c6449-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="c6449-107">Parameters</span></span>

<span data-ttu-id="c6449-108">*hConsoleHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c6449-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="c6449-109">Ein Handle zum Konsoleneingabepuffer oder zu einem Konsolenbildschirmpuffer.</span><span class="sxs-lookup"><span data-stu-id="c6449-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="c6449-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="c6449-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="c6449-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="c6449-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="c6449-112">*dwMode* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c6449-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="c6449-113">Der Eingabe- oder Ausgabemodus, der festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c6449-113">The input or output mode to be set.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="c6449-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c6449-114">Return value</span></span>

<span data-ttu-id="c6449-115">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="c6449-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c6449-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="c6449-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c6449-117">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) auf.</span><span class="sxs-lookup"><span data-stu-id="c6449-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="c6449-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="c6449-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="c6449-119">Um den aktuellen Modus eines Konsoleneingabepuffers oder Bildschirmpuffers zu bestimmen, verwenden Sie die Funktion [**GetConsoleMode**](getconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="c6449-119">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="c6449-120">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c6449-120">Examples</span></span>

<span data-ttu-id="c6449-121">Ein Beispiel finden Sie unter [Lesen von Eingabepufferereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="c6449-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c6449-122">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c6449-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c6449-123">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="c6449-123">Minimum supported client</span></span> | <span data-ttu-id="c6449-124">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="c6449-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c6449-125">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="c6449-125">Minimum supported server</span></span> | <span data-ttu-id="c6449-126">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="c6449-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c6449-127">Header</span><span class="sxs-lookup"><span data-stu-id="c6449-127">Header</span></span> | <span data-ttu-id="c6449-128">ConsoleApi.h (über WinCon.h, Windows.h einschließen)</span><span class="sxs-lookup"><span data-stu-id="c6449-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c6449-129">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="c6449-129">Library</span></span> | <span data-ttu-id="c6449-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c6449-130">Kernel32.lib</span></span> |
| <span data-ttu-id="c6449-131">DLL</span><span class="sxs-lookup"><span data-stu-id="c6449-131">DLL</span></span> | <span data-ttu-id="c6449-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c6449-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c6449-133">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c6449-133">See also</span></span>

[<span data-ttu-id="c6449-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="c6449-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c6449-135">Konsolenmodi</span><span class="sxs-lookup"><span data-stu-id="c6449-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="c6449-136">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="c6449-136">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="c6449-137">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="c6449-137">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="c6449-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="c6449-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="c6449-139">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="c6449-139">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="c6449-140">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="c6449-140">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="c6449-141">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="c6449-141">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="c6449-142">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="c6449-142">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
