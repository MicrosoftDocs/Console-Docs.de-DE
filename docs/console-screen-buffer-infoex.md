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
ms.openlocfilehash: 1e4e30601655190bc6f597bbd33dd99f14f8d488
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358081"
---
# <a name="console_screen_buffer_infoex-structure"></a><span data-ttu-id="3e1df-104">Konsolen \_ Bildschirm- \_ Puffer- \_ INFOEX-Struktur</span><span class="sxs-lookup"><span data-stu-id="3e1df-104">CONSOLE\_SCREEN\_BUFFER\_INFOEX structure</span></span>

<span data-ttu-id="3e1df-105">Enthält erweiterte Informationen zu einem Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="3e1df-105">Contains extended information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e1df-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3e1df-106">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="3e1df-107">Member</span><span class="sxs-lookup"><span data-stu-id="3e1df-107">Members</span></span>

<span data-ttu-id="3e1df-108">**CBSIZE**</span><span class="sxs-lookup"><span data-stu-id="3e1df-108">**cbSize**</span></span>  
<span data-ttu-id="3e1df-109">Die Größe der-Struktur in Bytes.</span><span class="sxs-lookup"><span data-stu-id="3e1df-109">The size of this structure, in bytes.</span></span>

<span data-ttu-id="3e1df-110">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="3e1df-110">**dwSize**</span></span>  
<span data-ttu-id="3e1df-111">Eine [**Koord**](coord-str.md) -Struktur, die die Größe des Konsolenbildschirm Puffers in Zeichen Spalten und Zeilen enthält.</span><span class="sxs-lookup"><span data-stu-id="3e1df-111">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="3e1df-112">**dwcurrsorposition**</span><span class="sxs-lookup"><span data-stu-id="3e1df-112">**dwCursorPosition**</span></span>  
<span data-ttu-id="3e1df-113">Eine [**Koord**](coord-str.md) -Struktur, die die Spalten-und Zeilen Koordinaten des Cursors im Konsolenbildschirm Puffer enthält.</span><span class="sxs-lookup"><span data-stu-id="3e1df-113">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="3e1df-114">**wattributes**</span><span class="sxs-lookup"><span data-stu-id="3e1df-114">**wAttributes**</span></span>  
<span data-ttu-id="3e1df-115">Die Attribute der Zeichen, die von den Funktionen " [**Write File**](/windows/win32/api/fileapi/nf-fileapi-writefile) " und " [**Write-Console**](writeconsole.md) " in einen Bildschirm Puffer geschrieben wurden oder von den Funktionen "read [**File**](/windows/win32/api/fileapi/nf-fileapi-readfile) " und "read [**Console**](readconsole.md) " auf einen Bildschirm Puffer gespiegelt werden.</span><span class="sxs-lookup"><span data-stu-id="3e1df-115">The attributes of the characters written to a screen buffer by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="3e1df-116">Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="3e1df-116">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="3e1df-117">**srwindow**</span><span class="sxs-lookup"><span data-stu-id="3e1df-117">**srWindow**</span></span>  
<span data-ttu-id="3e1df-118">Eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die die Konsolenbildschirm Puffer Koordinaten der oberen linken und unteren rechten Ecke des Anzeige Fensters enthält.</span><span class="sxs-lookup"><span data-stu-id="3e1df-118">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="3e1df-119">**dwmaximumwindowsize**</span><span class="sxs-lookup"><span data-stu-id="3e1df-119">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="3e1df-120">Eine [**Koord**](coord-str.md) -Struktur, die die maximale Größe des Konsolenfensters in Zeichen Spalten und Zeilen enthält, wenn die aktuelle Bildschirm Puffergröße und-Schriftart und die Bildschirmgröße angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="3e1df-120">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<span data-ttu-id="3e1df-121">**wpopupattribute**</span><span class="sxs-lookup"><span data-stu-id="3e1df-121">**wPopupAttributes**</span></span>  
<span data-ttu-id="3e1df-122">Das Füll Attribut für Konsolen-Popups.</span><span class="sxs-lookup"><span data-stu-id="3e1df-122">The fill attribute for console pop-ups.</span></span>

<span data-ttu-id="3e1df-123">**bfullscreensupported**</span><span class="sxs-lookup"><span data-stu-id="3e1df-123">**bFullscreenSupported**</span></span>  
<span data-ttu-id="3e1df-124">Wenn dieser Member ist `TRUE` , wird der Vollbildmodus unterstützt, andernfalls ist dies nicht der Fall.</span><span class="sxs-lookup"><span data-stu-id="3e1df-124">If this member is `TRUE`, full-screen mode is supported; otherwise, it is not.</span></span> <span data-ttu-id="3e1df-125">Dabei handelt es sich immer `FALSE` um Systeme nach Windows Vista mit dem [WDDM-Treibermodell](/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) , da der echte direkte VGA-Zugriff auf den Monitor nicht mehr möglich ist.</span><span class="sxs-lookup"><span data-stu-id="3e1df-125">This will always be `FALSE` for systems after Windows Vista with the [WDDM driver model](/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) as true direct VGA access to the monitor is no longer available.</span></span>

<span data-ttu-id="3e1df-126">**ColorTable**</span><span class="sxs-lookup"><span data-stu-id="3e1df-126">**ColorTable**</span></span>  
<span data-ttu-id="3e1df-127">Ein Array von [**COLORREF**](/windows/win32/gdi/colorref) -Werten, die die Farbeinstellungen der Konsole beschreiben.</span><span class="sxs-lookup"><span data-stu-id="3e1df-127">An array of [**COLORREF**](/windows/win32/gdi/colorref) values that describe the console's color settings.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e1df-128">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="3e1df-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3e1df-129">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="3e1df-129">Minimum supported client</span></span> | <span data-ttu-id="3e1df-130">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="3e1df-130">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="3e1df-131">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="3e1df-131">Minimum supported server</span></span> | <span data-ttu-id="3e1df-132">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="3e1df-132">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="3e1df-133">Header</span><span class="sxs-lookup"><span data-stu-id="3e1df-133">Header</span></span> | <span data-ttu-id="3e1df-134">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3e1df-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="3e1df-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3e1df-135">See also</span></span>

[<span data-ttu-id="3e1df-136">**Koord**</span><span class="sxs-lookup"><span data-stu-id="3e1df-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="3e1df-137">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="3e1df-137">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

[<span data-ttu-id="3e1df-138">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="3e1df-138">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

[<span data-ttu-id="3e1df-139">**kleine \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="3e1df-139">**SMALL\_RECT**</span></span>](small-rect-str.md)