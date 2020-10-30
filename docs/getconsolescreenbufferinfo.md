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
ms.openlocfilehash: 251fc71ef58840a962e5c1e09e88474959de27ae
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038768"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="86047-104">Getconsoleskreenbufferinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="86047-104">GetConsoleScreenBufferInfo function</span></span>

<span data-ttu-id="86047-105">Ruft Informationen zum angegebenen Konsolenbildschirm Puffer ab.</span><span class="sxs-lookup"><span data-stu-id="86047-105">Retrieves information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="86047-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="86047-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a><span data-ttu-id="86047-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="86047-107">Parameters</span></span>

<span data-ttu-id="86047-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="86047-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="86047-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="86047-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="86047-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="86047-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="86047-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="86047-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="86047-112">*lpconsoleskreenbufferinfo* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="86047-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="86047-113">Ein Zeiger auf eine [**Konsolen \_ Bildschirm- \_ Puffer \_ Info**](console-screen-buffer-info-str.md) Struktur, die die Bildschirm Puffer Informationen der Konsole empfängt.</span><span class="sxs-lookup"><span data-stu-id="86047-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="86047-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="86047-114">Return value</span></span>

<span data-ttu-id="86047-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="86047-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="86047-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="86047-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="86047-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="86047-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="86047-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="86047-118">Remarks</span></span>

<span data-ttu-id="86047-119">Das Rechteck, das im **srwindow** -Member der [**Konsolen \_ Bildschirm \_ Puffer \_ Info**](console-screen-buffer-info-str.md) -Struktur zurückgegeben wird, kann geändert und dann an die [**setconsolewindowinfo**](setconsolewindowinfo.md) -Funktion weitergegeben werden, um einen Bildlauf des Konsolenbildschirm Puffers im-Fenster durchführen, um die Größe des Fensters zu ändern oder beides.</span><span class="sxs-lookup"><span data-stu-id="86047-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="86047-120">Alle Koordinaten, die in der [**Konsolen \_ Bildschirm \_ Puffer \_ Info**](console-screen-buffer-info-str.md) -Struktur zurückgegeben werden, sind in Zeichen Zell Koordinaten, wobei sich der Ursprung (0,0) in der oberen linken Ecke des Konsolenbildschirm Puffers befindet.</span><span class="sxs-lookup"><span data-stu-id="86047-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="86047-121">Diese API weist keine Entsprechung für ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** auf.</span><span class="sxs-lookup"><span data-stu-id="86047-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="86047-122">Diese Verwendung ist möglicherweise trotzdem für Anwendungen erforderlich, die versuchen, Spalten, Raster oder die Anzeige zu zeichnen, um die Fenstergröße abzurufen.</span><span class="sxs-lookup"><span data-stu-id="86047-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="86047-123">Dieser Fenster Zustand wird von der TTY/Pty/pseudoconsole außerhalb des normalen streamflows verwaltet und in der Regel als Benutzer Berechtigung betrachtet, die von der Client Anwendung nicht angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="86047-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="86047-124">Updates können für "read [**ConsoleInput**](readconsoleinput.md)" empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="86047-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="examples"></a><span data-ttu-id="86047-125">Beispiele</span><span class="sxs-lookup"><span data-stu-id="86047-125">Examples</span></span>

<span data-ttu-id="86047-126">Ein Beispiel finden Sie unter [Scrollen des Fensters eines Bildschirm Puffers](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="86047-126">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="86047-127">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="86047-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="86047-128">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="86047-128">Minimum supported client</span></span> | <span data-ttu-id="86047-129">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="86047-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="86047-130">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="86047-130">Minimum supported server</span></span> | <span data-ttu-id="86047-131">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="86047-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="86047-132">Header</span><span class="sxs-lookup"><span data-stu-id="86047-132">Header</span></span> | <span data-ttu-id="86047-133">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="86047-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="86047-134">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="86047-134">Library</span></span> | <span data-ttu-id="86047-135">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="86047-135">Kernel32.lib</span></span> |
| <span data-ttu-id="86047-136">DLL</span><span class="sxs-lookup"><span data-stu-id="86047-136">DLL</span></span> | <span data-ttu-id="86047-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="86047-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="86047-138">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="86047-138">See also</span></span>

[<span data-ttu-id="86047-139">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="86047-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="86047-140">**Konsolen \_ Bildschirm- \_ Puffer \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="86047-140">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="86047-141">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="86047-141">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="86047-142">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="86047-142">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="86047-143">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="86047-143">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="86047-144">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="86047-144">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="86047-145">Fenster-und Bildschirm Puffergröße</span><span class="sxs-lookup"><span data-stu-id="86047-145">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
