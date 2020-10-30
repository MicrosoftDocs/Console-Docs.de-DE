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
ms.openlocfilehash: 7eb27a383a0bdbfc985188eb477ab9a878f33274
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039438"
---
# <a name="setconsoleactivescreenbuffer-function"></a><span data-ttu-id="83151-104">Setconsoleactiveskreenbuffer-Funktion</span><span class="sxs-lookup"><span data-stu-id="83151-104">SetConsoleActiveScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="83151-105">Legt den angegebenen Bildschirm Puffer auf den aktuell angezeigten Konsolenbildschirm Puffer fest.</span><span class="sxs-lookup"><span data-stu-id="83151-105">Sets the specified screen buffer to be the currently displayed console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="83151-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="83151-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a><span data-ttu-id="83151-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="83151-107">Parameters</span></span>

<span data-ttu-id="83151-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="83151-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="83151-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="83151-109">A handle to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="83151-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="83151-110">Return value</span></span>

<span data-ttu-id="83151-111">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="83151-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="83151-112">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="83151-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="83151-113">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="83151-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="83151-114">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="83151-114">Remarks</span></span>

<span data-ttu-id="83151-115">Eine Konsole kann über mehrere Bildschirm Puffer verfügen.</span><span class="sxs-lookup"><span data-stu-id="83151-115">A console can have multiple screen buffers.</span></span> <span data-ttu-id="83151-116">**Setconsoleactiveskreenbuffer** bestimmt, welche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="83151-116">**SetConsoleActiveScreenBuffer** determines which one is displayed.</span></span> <span data-ttu-id="83151-117">Sie können in einen inaktiven Bildschirm Puffer schreiben und dann **setconsoleactiveskreenbuffer** verwenden, um den Inhalt des Puffers anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="83151-117">You can write to an inactive screen buffer and then use **SetConsoleActiveScreenBuffer** to display the buffer's contents.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="83151-118">Beispiele</span><span class="sxs-lookup"><span data-stu-id="83151-118">Examples</span></span>

<span data-ttu-id="83151-119">Ein Beispiel finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="83151-119">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="83151-120">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="83151-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="83151-121">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="83151-121">Minimum supported client</span></span> | <span data-ttu-id="83151-122">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="83151-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="83151-123">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="83151-123">Minimum supported server</span></span> | <span data-ttu-id="83151-124">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="83151-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="83151-125">Header</span><span class="sxs-lookup"><span data-stu-id="83151-125">Header</span></span> | <span data-ttu-id="83151-126">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="83151-126">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="83151-127">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="83151-127">Library</span></span> | <span data-ttu-id="83151-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="83151-128">Kernel32.lib</span></span> |
| <span data-ttu-id="83151-129">DLL</span><span class="sxs-lookup"><span data-stu-id="83151-129">DLL</span></span> | <span data-ttu-id="83151-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="83151-130">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="83151-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="83151-131">See also</span></span>

[<span data-ttu-id="83151-132">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="83151-132">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="83151-133">Konsolenbildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="83151-133">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="83151-134">**CreateConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="83151-134">**CreateConsoleScreenBuffer**</span></span>](createconsolescreenbuffer.md)
