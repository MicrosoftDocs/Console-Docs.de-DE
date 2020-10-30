---
title: Flushconsoleingeputbuffer-Funktion
description: Leert den Konsolen Eingabepuffer. Alle Eingabedaten Sätze, die sich derzeit im Eingabepuffer befinden, werden verworfen.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 543552e9252c1f28701a0b316b43597cdd9cd2c9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039048"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="9cfa3-105">Flushconsoleingeputbuffer-Funktion</span><span class="sxs-lookup"><span data-stu-id="9cfa3-105">FlushConsoleInputBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9cfa3-106">Leert den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="9cfa3-106">Flushes the console input buffer.</span></span> <span data-ttu-id="9cfa3-107">Alle Eingabedaten Sätze, die sich derzeit im Eingabepuffer befinden, werden verworfen.</span><span class="sxs-lookup"><span data-stu-id="9cfa3-107">All input records currently in the input buffer are discarded.</span></span>

## <a name="syntax"></a><span data-ttu-id="9cfa3-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="9cfa3-108">Syntax</span></span>

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

## <a name="parameters"></a><span data-ttu-id="9cfa3-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="9cfa3-109">Parameters</span></span>

<span data-ttu-id="9cfa3-110">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9cfa3-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="9cfa3-111">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="9cfa3-111">A handle to the console input buffer.</span></span> <span data-ttu-id="9cfa3-112">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="9cfa3-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="9cfa3-113">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="9cfa3-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="9cfa3-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="9cfa3-114">Return value</span></span>

<span data-ttu-id="9cfa3-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="9cfa3-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9cfa3-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="9cfa3-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9cfa3-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="9cfa3-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="9cfa3-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="9cfa3-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="9cfa3-119">Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="9cfa3-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="9cfa3-120">Wenn Sie versuchen, die Eingabe Warteschlange gleichzeitig zu leeren, kann der Status in der Warteschlange auf unerwartete Weise zerstört werden.</span><span class="sxs-lookup"><span data-stu-id="9cfa3-120">Attempting to empty the input queue all at once can destroy state in the queue in an unexpected manner.</span></span>

## <a name="requirements"></a><span data-ttu-id="9cfa3-121">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="9cfa3-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9cfa3-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="9cfa3-122">Minimum supported client</span></span> | <span data-ttu-id="9cfa3-123">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="9cfa3-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="9cfa3-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="9cfa3-124">Minimum supported server</span></span> | <span data-ttu-id="9cfa3-125">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="9cfa3-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="9cfa3-126">Header</span><span class="sxs-lookup"><span data-stu-id="9cfa3-126">Header</span></span> | <span data-ttu-id="9cfa3-127">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9cfa3-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9cfa3-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="9cfa3-128">Library</span></span> | <span data-ttu-id="9cfa3-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="9cfa3-129">Kernel32.lib</span></span> |
| <span data-ttu-id="9cfa3-130">DLL</span><span class="sxs-lookup"><span data-stu-id="9cfa3-130">DLL</span></span> | <span data-ttu-id="9cfa3-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9cfa3-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="9cfa3-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9cfa3-132">See also</span></span>

[<span data-ttu-id="9cfa3-133">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="9cfa3-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9cfa3-134">Konsolen Eingabefunktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="9cfa3-134">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="9cfa3-135">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="9cfa3-135">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="9cfa3-136">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="9cfa3-136">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="9cfa3-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="9cfa3-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="9cfa3-138">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="9cfa3-138">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
