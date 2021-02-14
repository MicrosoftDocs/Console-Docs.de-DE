---
title: Setconsolewindowinfo-Funktion
description: Legt die aktuelle Größe und Position des Fensters eines Konsolenbildschirm Puffers fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: af3f9d63b01697a2ab0735014a4836d9ab11d8cf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358530"
---
# <a name="setconsolewindowinfo-function"></a><span data-ttu-id="1ef9c-104">Setconsolewindowinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="1ef9c-104">SetConsoleWindowInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="1ef9c-105">Legt die aktuelle Größe und Position des Fensters eines Konsolenbildschirm Puffers fest.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-105">Sets the current size and position of a console screen buffer's window.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ef9c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ef9c-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

## <a name="parameters"></a><span data-ttu-id="1ef9c-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="1ef9c-107">Parameters</span></span>

<span data-ttu-id="1ef9c-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1ef9c-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="1ef9c-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="1ef9c-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="1ef9c-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="1ef9c-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="1ef9c-112">*babsolute* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1ef9c-112">*bAbsolute* \[in\]</span></span>  
<span data-ttu-id="1ef9c-113">Wenn dieser Parameter auf **true** festgelegt ist, geben die Koordinaten die neuen oberen linken und unteren rechten Ecke des Fensters an.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-113">If this parameter is **TRUE**, the coordinates specify the new upper-left and lower-right corners of the window.</span></span> <span data-ttu-id="1ef9c-114">Wenn der Wert **false** ist, sind die Koordinaten relativ zu den aktuellen Fenstern der Fenster Ecke.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-114">If it is **FALSE**, the coordinates are relative to the current window-corner coordinates.</span></span>

<span data-ttu-id="1ef9c-115">*lpconsolewindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1ef9c-115">*lpConsoleWindow* \[in\]</span></span>  
<span data-ttu-id="1ef9c-116">Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die die neuen oberen linken und unteren rechten Ecke des Fensters angibt.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure that specifies the new upper-left and lower-right corners of the window.</span></span>

## <a name="return-value"></a><span data-ttu-id="1ef9c-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1ef9c-117">Return value</span></span>

<span data-ttu-id="1ef9c-118">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1ef9c-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1ef9c-120">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="1ef9c-121">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="1ef9c-121">Remarks</span></span>

<span data-ttu-id="1ef9c-122">Die Funktion schlägt fehl, wenn das angegebene Fenster Rechteck die Grenzen des Konsolenbildschirm Puffers überschreitet.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-122">The function fails if the specified window rectangle extends beyond the boundaries of the console screen buffer.</span></span> <span data-ttu-id="1ef9c-123">Dies bedeutet, dass die **oberen** und **linken** Member des *lpconsolewindow* -Rechtecks (oder die berechneten oberen und linken Koordinaten, wenn *babsolute* false ist) nicht kleiner als 0 (null) sein dürfen.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-123">This means that the **Top** and **Left** members of the *lpConsoleWindow* rectangle (or the calculated top and left coordinates, if *bAbsolute* is FALSE) cannot be less than zero.</span></span> <span data-ttu-id="1ef9c-124">Entsprechend dürfen die **unteren** und **rechten** Elemente (oder die berechneten unteren und rechten Koordinaten) nicht größer sein als (Bildschirm Puffer Höhe – 1) und (Bildschirm Puffer Breite – 1).</span><span class="sxs-lookup"><span data-stu-id="1ef9c-124">Similarly, the **Bottom** and **Right** members (or the calculated bottom and right coordinates) cannot be greater than (screen buffer height – 1) and (screen buffer width – 1), respectively.</span></span> <span data-ttu-id="1ef9c-125">Die-Funktion schlägt auch fehl, wenn das **Rechte** Element (oder die berechnete rechte Koordinate) kleiner als oder gleich dem **linken** Member (oder der berechneten linken Koordinate) ist oder wenn der **untere** Member (oder die berechnete untere Koordinate) kleiner oder gleich dem **oberen** Element (oder der berechneten oberen Koordinate) ist.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-125">The function also fails if the **Right** member (or calculated right coordinate) is less than or equal to the **Left** member (or calculated left coordinate) or if the **Bottom** member (or calculated bottom coordinate) is less than or equal to the **Top** member (or calculated top coordinate).</span></span>

<span data-ttu-id="1ef9c-126">Bei-Konsolen mit mehr als einem Bildschirm Puffer wirkt sich das Ändern der Fensterposition für einen Bildschirm Puffer nicht auf die Fensterpositionen der anderen Bildschirm Puffer aus.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-126">For consoles with more than one screen buffer, changing the window location for one screen buffer does not affect the window locations of the other screen buffers.</span></span>

<span data-ttu-id="1ef9c-127">Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die aktuelle Größe und Position des Fensters eines Bildschirm Puffers zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-127">To determine the current size and position of a screen buffer's window, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span> <span data-ttu-id="1ef9c-128">Diese Funktion gibt auch die maximale Größe des Fensters zurück, wenn die aktuelle Bildschirm Puffergröße, die aktuelle Schriftgröße und die Bildschirmgröße angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-128">This function also returns the maximum size of the window, given the current screen buffer size, the current font size, and the screen size.</span></span> <span data-ttu-id="1ef9c-129">Die [**getlargestconsolewindowsize**](getlargestconsolewindowsize.md) -Funktion gibt die maximale Fenstergröße in Anbetracht der aktuellen Schriftart und Bildschirmgröße zurück, berücksichtigt jedoch nicht die Größe des Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-129">The [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) function returns the maximum window size given the current font and screen sizes, but it does not consider the size of the console screen buffer.</span></span>

<span data-ttu-id="1ef9c-130">**Setconsolewindowinfo** kann verwendet werden, um den Inhalt des Konsolenbildschirm Puffers durch Verschieben der Position des Fenster Rechtecks zu scrollen, ohne seine Größe zu ändern.</span><span class="sxs-lookup"><span data-stu-id="1ef9c-130">**SetConsoleWindowInfo** can be used to scroll the contents of the console screen buffer by shifting the position of the window rectangle without changing its size.</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="examples"></a><span data-ttu-id="1ef9c-131">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1ef9c-131">Examples</span></span>

<span data-ttu-id="1ef9c-132">Ein Beispiel finden Sie unter [Scrollen des Fensters eines Bildschirm Puffers](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="1ef9c-132">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="1ef9c-133">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1ef9c-133">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1ef9c-134">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="1ef9c-134">Minimum supported client</span></span> | <span data-ttu-id="1ef9c-135">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1ef9c-135">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1ef9c-136">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="1ef9c-136">Minimum supported server</span></span> | <span data-ttu-id="1ef9c-137">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1ef9c-137">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1ef9c-138">Header</span><span class="sxs-lookup"><span data-stu-id="1ef9c-138">Header</span></span> | <span data-ttu-id="1ef9c-139">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1ef9c-139">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="1ef9c-140">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="1ef9c-140">Library</span></span> | <span data-ttu-id="1ef9c-141">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="1ef9c-141">Kernel32.lib</span></span> |
| <span data-ttu-id="1ef9c-142">DLL</span><span class="sxs-lookup"><span data-stu-id="1ef9c-142">DLL</span></span> | <span data-ttu-id="1ef9c-143">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1ef9c-143">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="1ef9c-144">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1ef9c-144">See also</span></span>

[<span data-ttu-id="1ef9c-145">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="1ef9c-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1ef9c-146">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="1ef9c-146">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="1ef9c-147">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="1ef9c-147">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="1ef9c-148">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="1ef9c-148">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="1ef9c-149">Scrollen des Bildschirm Puffers</span><span class="sxs-lookup"><span data-stu-id="1ef9c-149">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="1ef9c-150">**kleine \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="1ef9c-150">**SMALL\_RECT**</span></span>](small-rect-str.md)