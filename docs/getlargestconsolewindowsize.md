---
title: Getlargestconsolewindowsize-Funktion
description: Ruft die Größe des größtmöglichen Konsolenfensters basierend auf der aktuellen Schriftart und der Größe der Anzeige ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 3fe4ddf83f25f1951defed52eaf8fea18e1ff2dc
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358870"
---
# <a name="getlargestconsolewindowsize-function"></a><span data-ttu-id="e0c6d-104">Getlargestconsolewindowsize-Funktion</span><span class="sxs-lookup"><span data-stu-id="e0c6d-104">GetLargestConsoleWindowSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e0c6d-105">Ruft die Größe des größtmöglichen Konsolenfensters basierend auf der aktuellen Schriftart und der Größe der Anzeige ab.</span><span class="sxs-lookup"><span data-stu-id="e0c6d-105">Retrieves the size of the largest possible console window, based on the current font and the size of the display.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0c6d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0c6d-106">Syntax</span></span>

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a><span data-ttu-id="e0c6d-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="e0c6d-107">Parameters</span></span>

<span data-ttu-id="e0c6d-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e0c6d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="e0c6d-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="e0c6d-109">A handle to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="e0c6d-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e0c6d-110">Return value</span></span>

<span data-ttu-id="e0c6d-111">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert eine [**coord**](coord-str.md) -Struktur, die die Anzahl der Zeichen Zellen Spalten (**X** -Member) und der Zeilen (**Y** -Member) im größtmöglichen Konsolenfenster angibt.</span><span class="sxs-lookup"><span data-stu-id="e0c6d-111">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that specifies the number of character cell columns (**X** member) and rows (**Y** member) in the largest possible console window.</span></span> <span data-ttu-id="e0c6d-112">Andernfalls sind die Elemente der-Struktur 0 (null).</span><span class="sxs-lookup"><span data-stu-id="e0c6d-112">Otherwise, the members of the structure are zero.</span></span>

<span data-ttu-id="e0c6d-113">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="e0c6d-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="e0c6d-114">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="e0c6d-114">Remarks</span></span>

<span data-ttu-id="e0c6d-115">Die-Funktion berücksichtigt nicht die Größe des Bildschirm Puffers der Konsole. Dies bedeutet, dass die zurückgegebene Fenstergröße möglicherweise größer als die Größe des Konsolenbildschirm Puffers ist.</span><span class="sxs-lookup"><span data-stu-id="e0c6d-115">The function does not take into consideration the size of the console screen buffer, which means that the window size returned may be larger than the size of the console screen buffer.</span></span> <span data-ttu-id="e0c6d-116">Mithilfe der [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion kann die maximale Größe des Konsolenfensters anhand der aktuellen Bildschirm Puffergröße, der aktuellen Schriftart und der Anzeige Größe bestimmt werden.</span><span class="sxs-lookup"><span data-stu-id="e0c6d-116">The [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function can be used to determine the maximum size of the console window, given the current screen buffer size, the current font, and the display size.</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="e0c6d-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e0c6d-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e0c6d-118">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="e0c6d-118">Minimum supported client</span></span> | <span data-ttu-id="e0c6d-119">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="e0c6d-119">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e0c6d-120">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="e0c6d-120">Minimum supported server</span></span> | <span data-ttu-id="e0c6d-121">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="e0c6d-121">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e0c6d-122">Header</span><span class="sxs-lookup"><span data-stu-id="e0c6d-122">Header</span></span> | <span data-ttu-id="e0c6d-123">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e0c6d-123">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e0c6d-124">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e0c6d-124">Library</span></span> | <span data-ttu-id="e0c6d-125">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="e0c6d-125">Kernel32.lib</span></span> |
| <span data-ttu-id="e0c6d-126">DLL</span><span class="sxs-lookup"><span data-stu-id="e0c6d-126">DLL</span></span> | <span data-ttu-id="e0c6d-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e0c6d-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e0c6d-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e0c6d-128">See also</span></span>

[<span data-ttu-id="e0c6d-129">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="e0c6d-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e0c6d-130">**Koord**</span><span class="sxs-lookup"><span data-stu-id="e0c6d-130">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="e0c6d-131">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="e0c6d-131">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="e0c6d-132">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="e0c6d-132">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="e0c6d-133">Fenster-und Bildschirm Puffergröße</span><span class="sxs-lookup"><span data-stu-id="e0c6d-133">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)