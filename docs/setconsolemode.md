---
title: Setconsolemode-Funktion
description: Legt den Eingabemodus für den Eingabepuffer einer Konsole oder den Ausgabemodus eines Konsolenbildschirm Puffers fest.
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
ms.openlocfilehash: b382e6567d2099e2d6eacf33c8e19233f20c6400
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039358"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="5e3fd-104">Setconsolemode-Funktion</span><span class="sxs-lookup"><span data-stu-id="5e3fd-104">SetConsoleMode function</span></span>

<span data-ttu-id="5e3fd-105">Legt den Eingabemodus für den Eingabepuffer einer Konsole oder den Ausgabemodus eines Konsolenbildschirm Puffers fest.</span><span class="sxs-lookup"><span data-stu-id="5e3fd-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="5e3fd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5e3fd-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a><span data-ttu-id="5e3fd-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="5e3fd-107">Parameters</span></span>

<span data-ttu-id="5e3fd-108">*hconsolehandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5e3fd-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="5e3fd-109">Ein Handle des Konsolen Eingabe Puffers oder eines Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="5e3fd-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="5e3fd-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="5e3fd-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="5e3fd-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="5e3fd-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="5e3fd-112">*dwmode* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5e3fd-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="5e3fd-113">Der Eingabe-oder Ausgabemodus, der festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="5e3fd-113">The input or output mode to be set.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="5e3fd-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5e3fd-114">Return value</span></span>

<span data-ttu-id="5e3fd-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="5e3fd-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="5e3fd-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="5e3fd-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="5e3fd-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="5e3fd-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="5e3fd-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="5e3fd-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="5e3fd-119">Verwenden Sie die [**getconsolemode**](getconsolemode.md) -Funktion, um den aktuellen Modus eines Konsolen Eingabe Puffers oder Bildschirm Puffers zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="5e3fd-119">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="5e3fd-120">Beispiele</span><span class="sxs-lookup"><span data-stu-id="5e3fd-120">Examples</span></span>

<span data-ttu-id="5e3fd-121">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="5e3fd-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="5e3fd-122">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="5e3fd-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5e3fd-123">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="5e3fd-123">Minimum supported client</span></span> | <span data-ttu-id="5e3fd-124">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="5e3fd-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5e3fd-125">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="5e3fd-125">Minimum supported server</span></span> | <span data-ttu-id="5e3fd-126">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="5e3fd-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5e3fd-127">Header</span><span class="sxs-lookup"><span data-stu-id="5e3fd-127">Header</span></span> | <span data-ttu-id="5e3fd-128">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5e3fd-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="5e3fd-129">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="5e3fd-129">Library</span></span> | <span data-ttu-id="5e3fd-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="5e3fd-130">Kernel32.lib</span></span> |
| <span data-ttu-id="5e3fd-131">DLL</span><span class="sxs-lookup"><span data-stu-id="5e3fd-131">DLL</span></span> | <span data-ttu-id="5e3fd-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5e3fd-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="5e3fd-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5e3fd-133">See also</span></span>

[<span data-ttu-id="5e3fd-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="5e3fd-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5e3fd-135">Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="5e3fd-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="5e3fd-136">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="5e3fd-136">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="5e3fd-137">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="5e3fd-137">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="5e3fd-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="5e3fd-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="5e3fd-139">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="5e3fd-139">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="5e3fd-140">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="5e3fd-140">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="5e3fd-141">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="5e3fd-141">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="5e3fd-142">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="5e3fd-142">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
