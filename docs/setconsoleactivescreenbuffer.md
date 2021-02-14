---
title: Setconsoleactiveskreenbuffer-Funktion
description: Legt den angegebenen Bildschirm Puffer auf den aktuell angezeigten Konsolenbildschirm Puffer fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 72545409bfff6485a4e454d9a004f7f9fa0161e3
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357750"
---
# <a name="setconsoleactivescreenbuffer-function"></a><span data-ttu-id="88382-104">Setconsoleactiveskreenbuffer-Funktion</span><span class="sxs-lookup"><span data-stu-id="88382-104">SetConsoleActiveScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="88382-105">Legt den angegebenen Bildschirm Puffer auf den aktuell angezeigten Konsolenbildschirm Puffer fest.</span><span class="sxs-lookup"><span data-stu-id="88382-105">Sets the specified screen buffer to be the currently displayed console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="88382-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="88382-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a><span data-ttu-id="88382-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="88382-107">Parameters</span></span>

<span data-ttu-id="88382-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="88382-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="88382-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="88382-109">A handle to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="88382-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="88382-110">Return value</span></span>

<span data-ttu-id="88382-111">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="88382-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="88382-112">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="88382-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="88382-113">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="88382-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="88382-114">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="88382-114">Remarks</span></span>

<span data-ttu-id="88382-115">Eine Konsole kann über mehrere Bildschirmpuffer verfügen.</span><span class="sxs-lookup"><span data-stu-id="88382-115">A console can have multiple screen buffers.</span></span> <span data-ttu-id="88382-116">**Setconsoleactiveskreenbuffer** bestimmt, welche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="88382-116">**SetConsoleActiveScreenBuffer** determines which one is displayed.</span></span> <span data-ttu-id="88382-117">Sie können in einen inaktiven Bildschirm Puffer schreiben und dann **setconsoleactiveskreenbuffer** verwenden, um den Inhalt des Puffers anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="88382-117">You can write to an inactive screen buffer and then use **SetConsoleActiveScreenBuffer** to display the buffer's contents.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="88382-118">Beispiele</span><span class="sxs-lookup"><span data-stu-id="88382-118">Examples</span></span>

<span data-ttu-id="88382-119">Ein Beispiel finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="88382-119">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="88382-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="88382-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="88382-121">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="88382-121">Minimum supported client</span></span> | <span data-ttu-id="88382-122">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="88382-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="88382-123">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="88382-123">Minimum supported server</span></span> | <span data-ttu-id="88382-124">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="88382-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="88382-125">Header</span><span class="sxs-lookup"><span data-stu-id="88382-125">Header</span></span> | <span data-ttu-id="88382-126">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="88382-126">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="88382-127">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="88382-127">Library</span></span> | <span data-ttu-id="88382-128">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="88382-128">Kernel32.lib</span></span> |
| <span data-ttu-id="88382-129">DLL</span><span class="sxs-lookup"><span data-stu-id="88382-129">DLL</span></span> | <span data-ttu-id="88382-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="88382-130">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="88382-131">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="88382-131">See also</span></span>

[<span data-ttu-id="88382-132">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="88382-132">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="88382-133">Konsolenbildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="88382-133">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="88382-134">**CreateConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="88382-134">**CreateConsoleScreenBuffer**</span></span>](createconsolescreenbuffer.md)