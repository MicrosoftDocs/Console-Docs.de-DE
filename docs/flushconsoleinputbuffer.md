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
ms.openlocfilehash: c36191738e09911dc9cc7c441371616001d250db
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357560"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="88734-105">Flushconsoleingeputbuffer-Funktion</span><span class="sxs-lookup"><span data-stu-id="88734-105">FlushConsoleInputBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="88734-106">Leert den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="88734-106">Flushes the console input buffer.</span></span> <span data-ttu-id="88734-107">Alle Eingabedaten Sätze, die sich derzeit im Eingabepuffer befinden, werden verworfen.</span><span class="sxs-lookup"><span data-stu-id="88734-107">All input records currently in the input buffer are discarded.</span></span>

## <a name="syntax"></a><span data-ttu-id="88734-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="88734-108">Syntax</span></span>

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

## <a name="parameters"></a><span data-ttu-id="88734-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="88734-109">Parameters</span></span>

<span data-ttu-id="88734-110">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="88734-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="88734-111">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="88734-111">A handle to the console input buffer.</span></span> <span data-ttu-id="88734-112">Das Handle muss das Zugriffsrecht **GENERIC\_WRITE** besitzen.</span><span class="sxs-lookup"><span data-stu-id="88734-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="88734-113">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="88734-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="88734-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="88734-114">Return value</span></span>

<span data-ttu-id="88734-115">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="88734-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="88734-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="88734-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="88734-117">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="88734-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="88734-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="88734-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="88734-119">Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="88734-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="88734-120">Wenn Sie versuchen, die Eingabe Warteschlange gleichzeitig zu leeren, kann der Status in der Warteschlange auf unerwartete Weise zerstört werden.</span><span class="sxs-lookup"><span data-stu-id="88734-120">Attempting to empty the input queue all at once can destroy state in the queue in an unexpected manner.</span></span>

## <a name="requirements"></a><span data-ttu-id="88734-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="88734-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="88734-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="88734-122">Minimum supported client</span></span> | <span data-ttu-id="88734-123">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="88734-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="88734-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="88734-124">Minimum supported server</span></span> | <span data-ttu-id="88734-125">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="88734-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="88734-126">Header</span><span class="sxs-lookup"><span data-stu-id="88734-126">Header</span></span> | <span data-ttu-id="88734-127">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="88734-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="88734-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="88734-128">Library</span></span> | <span data-ttu-id="88734-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="88734-129">Kernel32.lib</span></span> |
| <span data-ttu-id="88734-130">DLL</span><span class="sxs-lookup"><span data-stu-id="88734-130">DLL</span></span> | <span data-ttu-id="88734-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="88734-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="88734-132">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="88734-132">See also</span></span>

[<span data-ttu-id="88734-133">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="88734-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="88734-134">Konsolen Eingabefunktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="88734-134">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="88734-135">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="88734-135">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="88734-136">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="88734-136">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="88734-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="88734-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="88734-138">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="88734-138">**WriteConsoleInput**</span></span>](writeconsoleinput.md)