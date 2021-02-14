---
title: CONSOLE_SCREEN_BUFFER_INFO-Struktur
description: Siehe Referenzinformationen zur CONSOLE_SCREEN_BUFFER_INFO Struktur, die Informationen zu einem Konsolenbildschirm Puffer enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFO
- wincon/CONSOLE_SCREEN_BUFFER_INFO
- CONSOLE_SCREEN_BUFFER_INFO
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFO
- wincon/PCONSOLE_SCREEN_BUFFER_INFO
- PCONSOLE_SCREEN_BUFFER_INFO
MS-HAID:
- '\_win32\_console\_screen\_buffer\_info\_str'
- base.console\_screen\_buffer\_info\_str
- consoles.console\_screen\_buffer\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 586b3e0f-2f6b-4a03-b8e4-602a892be56d
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 31ef1cf8e78029be48d5217cbc82f84663d627b5
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358120"
---
# <a name="console_screen_buffer_info-structure"></a><span data-ttu-id="6daec-104">Konsolen \_ Bildschirm- \_ Puffer \_ Info Struktur</span><span class="sxs-lookup"><span data-stu-id="6daec-104">CONSOLE\_SCREEN\_BUFFER\_INFO structure</span></span>

<span data-ttu-id="6daec-105">Enthält Informationen zu einem Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="6daec-105">Contains information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="6daec-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6daec-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

## <a name="members"></a><span data-ttu-id="6daec-107">Member</span><span class="sxs-lookup"><span data-stu-id="6daec-107">Members</span></span>

<span data-ttu-id="6daec-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="6daec-108">**dwSize**</span></span>  
<span data-ttu-id="6daec-109">Eine [**Koord**](coord-str.md) -Struktur, die die Größe des Konsolenbildschirm Puffers in Zeichen Spalten und Zeilen enthält.</span><span class="sxs-lookup"><span data-stu-id="6daec-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="6daec-110">**dwcurrsorposition**</span><span class="sxs-lookup"><span data-stu-id="6daec-110">**dwCursorPosition**</span></span>  
<span data-ttu-id="6daec-111">Eine [**Koord**](coord-str.md) -Struktur, die die Spalten-und Zeilen Koordinaten des Cursors im Konsolenbildschirm Puffer enthält.</span><span class="sxs-lookup"><span data-stu-id="6daec-111">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="6daec-112">**wattributes**</span><span class="sxs-lookup"><span data-stu-id="6daec-112">**wAttributes**</span></span>  
<span data-ttu-id="6daec-113">Die Attribute der Zeichen, die von den Funktionen " [**Write File**](/windows/win32/api/fileapi/nf-fileapi-writefile) " und " [**Write-Console**](writeconsole.md) " in einen Bildschirm Puffer geschrieben wurden oder von den Funktionen "read [**File**](/windows/win32/api/fileapi/nf-fileapi-readfile) " und "read [**Console**](readconsole.md) " auf einen Bildschirm Puffer gespiegelt werden.</span><span class="sxs-lookup"><span data-stu-id="6daec-113">The attributes of the characters written to a screen buffer by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="6daec-114">Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="6daec-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="6daec-115">**srwindow**</span><span class="sxs-lookup"><span data-stu-id="6daec-115">**srWindow**</span></span>  
<span data-ttu-id="6daec-116">Eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die die Konsolenbildschirm Puffer Koordinaten der oberen linken und unteren rechten Ecke des Anzeige Fensters enthält.</span><span class="sxs-lookup"><span data-stu-id="6daec-116">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="6daec-117">**dwmaximumwindowsize**</span><span class="sxs-lookup"><span data-stu-id="6daec-117">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="6daec-118">Eine [**Koord**](coord-str.md) -Struktur, die die maximale Größe des Konsolenfensters in Zeichen Spalten und Zeilen enthält, wenn die aktuelle Bildschirm Puffergröße und-Schriftart und die Bildschirmgröße angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="6daec-118">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

## <a name="examples"></a><span data-ttu-id="6daec-119">Beispiele</span><span class="sxs-lookup"><span data-stu-id="6daec-119">Examples</span></span>

<span data-ttu-id="6daec-120">Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="6daec-120">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="6daec-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="6daec-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6daec-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="6daec-122">Minimum supported client</span></span> | <span data-ttu-id="6daec-123">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6daec-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6daec-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="6daec-124">Minimum supported server</span></span> | <span data-ttu-id="6daec-125">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6daec-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6daec-126">Header</span><span class="sxs-lookup"><span data-stu-id="6daec-126">Header</span></span> | <span data-ttu-id="6daec-127">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6daec-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="6daec-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6daec-128">See also</span></span>

[<span data-ttu-id="6daec-129">**Koord**</span><span class="sxs-lookup"><span data-stu-id="6daec-129">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="6daec-130">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="6daec-130">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="6daec-131">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="6daec-131">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="6daec-132">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="6daec-132">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="6daec-133">**kleine \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="6daec-133">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="6daec-134">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="6daec-134">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="6daec-135">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="6daec-135">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)