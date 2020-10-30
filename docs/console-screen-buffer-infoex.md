---
title: CONSOLE_SCREEN_BUFFER_INFOEX-Struktur
description: Siehe Referenzinformationen zur CONSOLE_SCREEN_BUFFER_INFOEX Struktur, die erweiterte Informationen zu einem Konsolenbildschirm Puffer enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFOEX
- wincon/CONSOLE_SCREEN_BUFFER_INFOEX
- CONSOLE_SCREEN_BUFFER_INFOEX
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFOEX
- wincon/PCONSOLE_SCREEN_BUFFER_INFOEX
- PCONSOLE_SCREEN_BUFFER_INFOEX
MS-HAID:
- base.console\_screen\_buffer\_infoex
- consoles.console\_screen\_buffer\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6ed40df3-063d-41c9-8637-510c95104603
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: baf6eeb51cbae5ce410c190852c22ae237e6a367
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038348"
---
# <a name="console_screen_buffer_infoex-structure"></a><span data-ttu-id="70cb1-104">Konsolen \_ Bildschirm- \_ Puffer- \_ INFOEX-Struktur</span><span class="sxs-lookup"><span data-stu-id="70cb1-104">CONSOLE\_SCREEN\_BUFFER\_INFOEX structure</span></span>

<span data-ttu-id="70cb1-105">Enthält erweiterte Informationen zu einem Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="70cb1-105">Contains extended information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="70cb1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="70cb1-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

## <a name="members"></a><span data-ttu-id="70cb1-107">Member</span><span class="sxs-lookup"><span data-stu-id="70cb1-107">Members</span></span>

<span data-ttu-id="70cb1-108">**CBSIZE**</span><span class="sxs-lookup"><span data-stu-id="70cb1-108">**cbSize**</span></span>  
<span data-ttu-id="70cb1-109">Die Größe der-Struktur in Bytes.</span><span class="sxs-lookup"><span data-stu-id="70cb1-109">The size of this structure, in bytes.</span></span>

<span data-ttu-id="70cb1-110">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="70cb1-110">**dwSize**</span></span>  
<span data-ttu-id="70cb1-111">Eine [**Koord**](coord-str.md) -Struktur, die die Größe des Konsolenbildschirm Puffers in Zeichen Spalten und Zeilen enthält.</span><span class="sxs-lookup"><span data-stu-id="70cb1-111">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="70cb1-112">**dwcurrsorposition**</span><span class="sxs-lookup"><span data-stu-id="70cb1-112">**dwCursorPosition**</span></span>  
<span data-ttu-id="70cb1-113">Eine [**Koord**](coord-str.md) -Struktur, die die Spalten-und Zeilen Koordinaten des Cursors im Konsolenbildschirm Puffer enthält.</span><span class="sxs-lookup"><span data-stu-id="70cb1-113">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="70cb1-114">**wattributes**</span><span class="sxs-lookup"><span data-stu-id="70cb1-114">**wAttributes**</span></span>  
<span data-ttu-id="70cb1-115">Die Attribute der Zeichen, die von den Funktionen " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " und " [**Write-Console**](writeconsole.md) " in einen Bildschirm Puffer geschrieben wurden oder von den Funktionen "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und "read [**Console**](readconsole.md) " auf einen Bildschirm Puffer gespiegelt werden.</span><span class="sxs-lookup"><span data-stu-id="70cb1-115">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="70cb1-116">Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="70cb1-116">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="70cb1-117">**srwindow**</span><span class="sxs-lookup"><span data-stu-id="70cb1-117">**srWindow**</span></span>  
<span data-ttu-id="70cb1-118">Eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die die Konsolenbildschirm Puffer Koordinaten der oberen linken und unteren rechten Ecke des Anzeige Fensters enthält.</span><span class="sxs-lookup"><span data-stu-id="70cb1-118">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="70cb1-119">**dwmaximumwindowsize**</span><span class="sxs-lookup"><span data-stu-id="70cb1-119">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="70cb1-120">Eine [**Koord**](coord-str.md) -Struktur, die die maximale Größe des Konsolenfensters in Zeichen Spalten und Zeilen enthält, wenn die aktuelle Bildschirm Puffergröße und-Schriftart und die Bildschirmgröße angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="70cb1-120">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<span data-ttu-id="70cb1-121">**wpopupattribute**</span><span class="sxs-lookup"><span data-stu-id="70cb1-121">**wPopupAttributes**</span></span>  
<span data-ttu-id="70cb1-122">Das Füll Attribut für Konsolen-Popups.</span><span class="sxs-lookup"><span data-stu-id="70cb1-122">The fill attribute for console pop-ups.</span></span>

<span data-ttu-id="70cb1-123">**bfullscreensupported**</span><span class="sxs-lookup"><span data-stu-id="70cb1-123">**bFullscreenSupported**</span></span>  
<span data-ttu-id="70cb1-124">Wenn dieser Member ist `TRUE` , wird der Vollbildmodus unterstützt, andernfalls ist dies nicht der Fall.</span><span class="sxs-lookup"><span data-stu-id="70cb1-124">If this member is `TRUE`, full-screen mode is supported; otherwise, it is not.</span></span> <span data-ttu-id="70cb1-125">Dabei handelt es sich immer `FALSE` um Systeme nach Windows Vista mit dem [WDDM-Treibermodell](https://docs.microsoft.com/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) , da der echte direkte VGA-Zugriff auf den Monitor nicht mehr möglich ist.</span><span class="sxs-lookup"><span data-stu-id="70cb1-125">This will always be `FALSE` for systems after Windows Vista with the [WDDM driver model](https://docs.microsoft.com/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) as true direct VGA access to the monitor is no longer available.</span></span>

<span data-ttu-id="70cb1-126">**ColorTable**</span><span class="sxs-lookup"><span data-stu-id="70cb1-126">**ColorTable**</span></span>  
<span data-ttu-id="70cb1-127">Ein Array von [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) -Werten, die die Farbeinstellungen der Konsole beschreiben.</span><span class="sxs-lookup"><span data-stu-id="70cb1-127">An array of [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) values that describe the console's color settings.</span></span>

## <a name="requirements"></a><span data-ttu-id="70cb1-128">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="70cb1-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="70cb1-129">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="70cb1-129">Minimum supported client</span></span> | <span data-ttu-id="70cb1-130">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="70cb1-130">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="70cb1-131">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="70cb1-131">Minimum supported server</span></span> | <span data-ttu-id="70cb1-132">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="70cb1-132">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="70cb1-133">Header</span><span class="sxs-lookup"><span data-stu-id="70cb1-133">Header</span></span> | <span data-ttu-id="70cb1-134">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="70cb1-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="70cb1-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="70cb1-135">See also</span></span>

[<span data-ttu-id="70cb1-136">**Koord**</span><span class="sxs-lookup"><span data-stu-id="70cb1-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="70cb1-137">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="70cb1-137">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

[<span data-ttu-id="70cb1-138">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="70cb1-138">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

[<span data-ttu-id="70cb1-139">**kleine \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="70cb1-139">**SMALL\_RECT**</span></span>](small-rect-str.md)
