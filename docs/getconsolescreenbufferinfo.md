---
title: Getconsoleskreenbufferinfo-Funktion
description: Siehe Referenzinformationen zur getconsoleskreenbufferinfo-Funktion, die Informationen zum angegebenen Konsolenbildschirm Puffer abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f80f77b749fc9e9dc0aebf4507b0c41f589e40c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358910"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="d083e-104">Getconsoleskreenbufferinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="d083e-104">GetConsoleScreenBufferInfo function</span></span>

<span data-ttu-id="d083e-105">Ruft Informationen zum angegebenen Konsolenbildschirm Puffer ab.</span><span class="sxs-lookup"><span data-stu-id="d083e-105">Retrieves information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="d083e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d083e-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a><span data-ttu-id="d083e-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="d083e-107">Parameters</span></span>

<span data-ttu-id="d083e-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d083e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d083e-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="d083e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d083e-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="d083e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="d083e-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d083e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d083e-112">*lpconsoleskreenbufferinfo* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="d083e-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="d083e-113">Ein Zeiger auf eine [**Konsolen \_ Bildschirm- \_ Puffer \_ Info**](console-screen-buffer-info-str.md) Struktur, die die Bildschirm Puffer Informationen der Konsole empfängt.</span><span class="sxs-lookup"><span data-stu-id="d083e-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="d083e-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="d083e-114">Return value</span></span>

<span data-ttu-id="d083e-115">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="d083e-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d083e-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="d083e-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d083e-117">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="d083e-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="d083e-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="d083e-118">Remarks</span></span>

<span data-ttu-id="d083e-119">Das Rechteck, das im **srwindow** -Member der [**Konsolen \_ Bildschirm \_ Puffer \_ Info**](console-screen-buffer-info-str.md) -Struktur zurückgegeben wird, kann geändert und dann an die [**setconsolewindowinfo**](setconsolewindowinfo.md) -Funktion weitergegeben werden, um einen Bildlauf des Konsolenbildschirm Puffers im-Fenster durchführen, um die Größe des Fensters zu ändern oder beides.</span><span class="sxs-lookup"><span data-stu-id="d083e-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="d083e-120">Alle Koordinaten, die in der [**Konsolen \_ Bildschirm \_ Puffer \_ Info**](console-screen-buffer-info-str.md) -Struktur zurückgegeben werden, sind in Zeichen Zell Koordinaten, wobei sich der Ursprung (0,0) in der oberen linken Ecke des Konsolenbildschirm Puffers befindet.</span><span class="sxs-lookup"><span data-stu-id="d083e-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="d083e-121">Diese API weist keine Entsprechung für ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** auf.</span><span class="sxs-lookup"><span data-stu-id="d083e-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="d083e-122">Diese Verwendung ist möglicherweise trotzdem für Anwendungen erforderlich, die versuchen, Spalten, Raster oder die Anzeige zu zeichnen, um die Fenstergröße abzurufen.</span><span class="sxs-lookup"><span data-stu-id="d083e-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="d083e-123">Dieser Fenster Zustand wird von der TTY/Pty/pseudoconsole außerhalb des normalen streamflows verwaltet und in der Regel als Benutzer Berechtigung betrachtet, die von der Client Anwendung nicht angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="d083e-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="d083e-124">Updates können für "read [**ConsoleInput**](readconsoleinput.md)" empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="d083e-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="examples"></a><span data-ttu-id="d083e-125">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d083e-125">Examples</span></span>

<span data-ttu-id="d083e-126">Ein Beispiel finden Sie unter [Scrollen des Fensters eines Bildschirm Puffers](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="d083e-126">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="d083e-127">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="d083e-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d083e-128">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="d083e-128">Minimum supported client</span></span> | <span data-ttu-id="d083e-129">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="d083e-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="d083e-130">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="d083e-130">Minimum supported server</span></span> | <span data-ttu-id="d083e-131">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="d083e-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="d083e-132">Header</span><span class="sxs-lookup"><span data-stu-id="d083e-132">Header</span></span> | <span data-ttu-id="d083e-133">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d083e-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d083e-134">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="d083e-134">Library</span></span> | <span data-ttu-id="d083e-135">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="d083e-135">Kernel32.lib</span></span> |
| <span data-ttu-id="d083e-136">DLL</span><span class="sxs-lookup"><span data-stu-id="d083e-136">DLL</span></span> | <span data-ttu-id="d083e-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d083e-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="d083e-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d083e-138">See also</span></span>

[<span data-ttu-id="d083e-139">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="d083e-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d083e-140">**Konsolen \_ Bildschirm- \_ Puffer \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="d083e-140">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="d083e-141">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="d083e-141">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="d083e-142">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="d083e-142">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="d083e-143">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="d083e-143">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="d083e-144">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="d083e-144">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="d083e-145">Fenster-und Bildschirm Puffergröße</span><span class="sxs-lookup"><span data-stu-id="d083e-145">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)