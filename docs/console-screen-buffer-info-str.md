---
title: CONSOLE_SCREEN_BUFFER_INFO Struktur
description: Siehe Referenzinformationen zur CONSOLE_SCREEN_BUFFER_INFO Struktur, die Informationen zu einem Konsolenbildschirm Puffer enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4089541ddac93f5be61b7a21d5aa88a88061b261
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060051"
---
# <a name="console_screen_buffer_info-structure"></a><span data-ttu-id="d8d92-104">Konsolen \_ Bildschirm- \_ Puffer \_ Info Struktur</span><span class="sxs-lookup"><span data-stu-id="d8d92-104">CONSOLE\_SCREEN\_BUFFER\_INFO structure</span></span>


<span data-ttu-id="d8d92-105">Enthält Informationen zu einem Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="d8d92-105">Contains information about a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="d8d92-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8d92-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

<a name="members"></a><span data-ttu-id="d8d92-107">Member</span><span class="sxs-lookup"><span data-stu-id="d8d92-107">Members</span></span>
-------

<span data-ttu-id="d8d92-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="d8d92-108">**dwSize**</span></span>  
<span data-ttu-id="d8d92-109">Eine [**Koord**](coord-str.md) -Struktur, die die Größe des Konsolenbildschirm Puffers in Zeichen Spalten und Zeilen enthält.</span><span class="sxs-lookup"><span data-stu-id="d8d92-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="d8d92-110">**dwcurrsorposition**</span><span class="sxs-lookup"><span data-stu-id="d8d92-110">**dwCursorPosition**</span></span>  
<span data-ttu-id="d8d92-111">Eine [**Koord**](coord-str.md) -Struktur, die die Spalten-und Zeilen Koordinaten des Cursors im Konsolenbildschirm Puffer enthält.</span><span class="sxs-lookup"><span data-stu-id="d8d92-111">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="d8d92-112">**wattributes**</span><span class="sxs-lookup"><span data-stu-id="d8d92-112">**wAttributes**</span></span>  
<span data-ttu-id="d8d92-113">Die Attribute der Zeichen, die von den Funktionen " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " und " [**Write-Console**](writeconsole.md) " in einen Bildschirm Puffer geschrieben wurden oder von den Funktionen "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und "read [**Console**](readconsole.md) " auf einen Bildschirm Puffer gespiegelt werden.</span><span class="sxs-lookup"><span data-stu-id="d8d92-113">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="d8d92-114">Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="d8d92-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="d8d92-115">**srwindow**</span><span class="sxs-lookup"><span data-stu-id="d8d92-115">**srWindow**</span></span>  
<span data-ttu-id="d8d92-116">Eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die die Konsolenbildschirm Puffer Koordinaten der oberen linken und unteren rechten Ecke des Anzeige Fensters enthält.</span><span class="sxs-lookup"><span data-stu-id="d8d92-116">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="d8d92-117">**dwmaximumwindowsize**</span><span class="sxs-lookup"><span data-stu-id="d8d92-117">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="d8d92-118">Eine [**Koord**](coord-str.md) -Struktur, die die maximale Größe des Konsolenfensters in Zeichen Spalten und Zeilen enthält, wenn die aktuelle Bildschirm Puffergröße und-Schriftart und die Bildschirmgröße angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="d8d92-118">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<a name="examples"></a><span data-ttu-id="d8d92-119">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d8d92-119">Examples</span></span>
--------

<span data-ttu-id="d8d92-120">Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="d8d92-120">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="d8d92-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="d8d92-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="d8d92-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="d8d92-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="d8d92-123">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="d8d92-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d8d92-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="d8d92-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="d8d92-125">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="d8d92-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d8d92-126">Header</span><span class="sxs-lookup"><span data-stu-id="d8d92-126">Header</span></span></p></td>
<td><span data-ttu-id="d8d92-127">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d8d92-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="d8d92-128"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d8d92-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="d8d92-129">**Koord**</span><span class="sxs-lookup"><span data-stu-id="d8d92-129">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="d8d92-130">**Getconsoleskreenbufferinfo**</span><span class="sxs-lookup"><span data-stu-id="d8d92-130">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="d8d92-131">**"Read Console"**</span><span class="sxs-lookup"><span data-stu-id="d8d92-131">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="d8d92-132">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="d8d92-132">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="d8d92-133">**kleine \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="d8d92-133">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="d8d92-134">**Schreib Konsole**</span><span class="sxs-lookup"><span data-stu-id="d8d92-134">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="d8d92-135">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="d8d92-135">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




