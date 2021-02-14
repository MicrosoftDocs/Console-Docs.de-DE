---
title: Setconsolecursorinfo-Funktion
description: Legt die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 565ed3bda8bd864fb52aac0106f01cee96eb78ba
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357690"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="31636-104">Setconsolecursorinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="31636-104">SetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="31636-105">Legt die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer fest.</span><span class="sxs-lookup"><span data-stu-id="31636-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="31636-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="31636-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="31636-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="31636-107">Parameters</span></span>

<span data-ttu-id="31636-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="31636-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="31636-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="31636-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="31636-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="31636-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="31636-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="31636-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="31636-112">*lpconsolecursorinfo* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="31636-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="31636-113">Ein Zeiger auf eine [**Konsolen \_ Cursor \_ Info**](console-cursor-info-str.md) -Struktur, die die neuen Spezifikationen für den Cursor des Konsolenbildschirm Puffers bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="31636-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="31636-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="31636-114">Return value</span></span>

<span data-ttu-id="31636-115">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="31636-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="31636-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="31636-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="31636-117">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="31636-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="31636-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="31636-118">Remarks</span></span>

<span data-ttu-id="31636-119">Wenn der Cursor eines Bildschirm Puffers sichtbar ist, kann seine Darstellung variieren und reicht von der vollständigen Füllung einer Zeichen Zelle bis zum Anzeigen als horizontale Linie am unteren Rand der Zelle.</span><span class="sxs-lookup"><span data-stu-id="31636-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="31636-120">Der **dwSize** -Member der [**Konsolen \_ Cursor \_ Info**](console-cursor-info-str.md) -Struktur gibt den Prozentsatz einer Zeichen Zelle an, die vom Cursor ausgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="31636-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="31636-121">Wenn dieser Member kleiner als 1 oder größer als 100 ist, schlägt **setconsolecursorinfo** fehl.</span><span class="sxs-lookup"><span data-stu-id="31636-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

> [!TIP]
> <span data-ttu-id="31636-122">Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent im **[Cursor Sichtbarkeits](console-virtual-terminal-sequences.md#cursor-visibility)** Abschnitt mit `^[[?25h` den `^[[?25l` Sequenzen und.</span><span class="sxs-lookup"><span data-stu-id="31636-122">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[cursor visibility](console-virtual-terminal-sequences.md#cursor-visibility)** section with the `^[[?25h` and `^[[?25l` sequences.</span></span> 

## <a name="requirements"></a><span data-ttu-id="31636-123">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="31636-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="31636-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="31636-124">Minimum supported client</span></span> | <span data-ttu-id="31636-125">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="31636-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="31636-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="31636-126">Minimum supported server</span></span> | <span data-ttu-id="31636-127">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="31636-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="31636-128">Header</span><span class="sxs-lookup"><span data-stu-id="31636-128">Header</span></span> | <span data-ttu-id="31636-129">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="31636-129">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="31636-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="31636-130">Library</span></span> | <span data-ttu-id="31636-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="31636-131">Kernel32.lib</span></span> |
| <span data-ttu-id="31636-132">DLL</span><span class="sxs-lookup"><span data-stu-id="31636-132">DLL</span></span> | <span data-ttu-id="31636-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="31636-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="31636-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="31636-134">See also</span></span>

[<span data-ttu-id="31636-135">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="31636-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="31636-136">Konsolenbildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="31636-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="31636-137">**Konsolen \_ Cursor \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="31636-137">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="31636-138">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="31636-138">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="31636-139">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="31636-139">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)