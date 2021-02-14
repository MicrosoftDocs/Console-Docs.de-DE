---
title: Scrollconsoleskreenbuffer-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur scrollconsoleskreenbuffer-Funktion, die einen Datenblock in einem Bildschirm Puffer verschiebt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 1bf009a91063c12ad14604349d68ca0de1d8eaa1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358670"
---
# <a name="scrollconsolescreenbuffer-function"></a><span data-ttu-id="eef5f-104">Scrollconsoleskreenbuffer-Funktion</span><span class="sxs-lookup"><span data-stu-id="eef5f-104">ScrollConsoleScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="eef5f-105">Verschiebt einen Datenblock in einem Bildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="eef5f-105">Moves a block of data in a screen buffer.</span></span> <span data-ttu-id="eef5f-106">Die Auswirkungen des Verschiebens können durch Angabe eines clippingrechtecks eingeschränkt werden, sodass der Inhalt des Konsolenbildschirm Puffers außerhalb des clippingrechtecks unverändert bleibt.</span><span class="sxs-lookup"><span data-stu-id="eef5f-106">The effects of the move can be limited by specifying a clipping rectangle, so the contents of the console screen buffer outside the clipping rectangle are unchanged.</span></span>

## <a name="syntax"></a><span data-ttu-id="eef5f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="eef5f-107">Syntax</span></span>

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

## <a name="parameters"></a><span data-ttu-id="eef5f-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="eef5f-108">Parameters</span></span>

<span data-ttu-id="eef5f-109">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="eef5f-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="eef5f-110">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="eef5f-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="eef5f-111">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="eef5f-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="eef5f-112">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="eef5f-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="eef5f-113">*lpscrollrechteck* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="eef5f-113">*lpScrollRectangle* \[in\]</span></span>  
<span data-ttu-id="eef5f-114">Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, deren Member die Links oben und rechts unten des Konsolenbildschirm-Puffer Rechtecks angibt, das verschoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="eef5f-114">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to be moved.</span></span>

<span data-ttu-id="eef5f-115">*lpcliprectangle* \[ in, optional\]</span><span class="sxs-lookup"><span data-stu-id="eef5f-115">*lpClipRectangle* \[in, optional\]</span></span>  
<span data-ttu-id="eef5f-116">Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, deren Member die oberen linken und unteren rechten Koordinaten des Konsolenbildschirm-Puffer Rechtecks angibt, das durch Scrollen beeinflusst wird.</span><span class="sxs-lookup"><span data-stu-id="eef5f-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle that is affected by the scrolling.</span></span> <span data-ttu-id="eef5f-117">Dieser Zeiger kann **null** sein.</span><span class="sxs-lookup"><span data-stu-id="eef5f-117">This pointer can be **NULL**.</span></span>

<span data-ttu-id="eef5f-118">*dwdestinationorigin* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="eef5f-118">*dwDestinationOrigin* \[in\]</span></span>  
<span data-ttu-id="eef5f-119">Eine [**Koord**](coord-str.md) -Struktur, die die linke obere Ecke der neuen Position des *lpscrollrechteck* -Inhalts in Zeichen angibt.</span><span class="sxs-lookup"><span data-stu-id="eef5f-119">A [**COORD**](coord-str.md) structure that specifies the upper-left corner of the new location of the *lpScrollRectangle* contents, in characters.</span></span>

<span data-ttu-id="eef5f-120">*lpfill* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="eef5f-120">*lpFill* \[in\]</span></span>  
<span data-ttu-id="eef5f-121">Ein Zeiger auf eine [**Char \_ Info**](char-info-str.md) -Struktur, die die Zeichen-und Farb Attribute angibt, die zum Auffüllen der Zellen innerhalb der Schnittmenge von *lpscrollrechteck* und *lpcliprectangle* verwendet werden sollen, die als Ergebnis der Verschiebung leer gelassen wurden.</span><span class="sxs-lookup"><span data-stu-id="eef5f-121">A pointer to a [**CHAR\_INFO**](char-info-str.md) structure that specifies the character and color attributes to be used in filling the cells within the intersection of *lpScrollRectangle* and *lpClipRectangle* that were left empty as a result of the move.</span></span>

## <a name="return-value"></a><span data-ttu-id="eef5f-122">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="eef5f-122">Return value</span></span>

<span data-ttu-id="eef5f-123">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="eef5f-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="eef5f-124">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="eef5f-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="eef5f-125">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="eef5f-125">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="eef5f-126">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="eef5f-126">Remarks</span></span>

<span data-ttu-id="eef5f-127">**Scrollconsoleskreenbuffer** kopiert den Inhalt eines rechteckigen Bereichs eines Bildschirm Puffers, der durch den *lpscrollrechteck* -Parameter angegeben ist, in einen anderen Bereich des Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="eef5f-127">**ScrollConsoleScreenBuffer** copies the contents of a rectangular region of a screen buffer, specified by the *lpScrollRectangle* parameter, to another area of the console screen buffer.</span></span> <span data-ttu-id="eef5f-128">Das Ziel Rechteck hat die gleichen Dimensionen wie das *lpscrollrechteck* -Rechteck mit seiner oberen linken Ecke an den Koordinaten, die durch den *dwdestinationorigin* -Parameter angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="eef5f-128">The target rectangle has the same dimensions as the *lpScrollRectangle* rectangle with its upper-left corner at the coordinates specified by the *dwDestinationOrigin* parameter.</span></span> <span data-ttu-id="eef5f-129">Die Teile von *lpscrollrechteck* , die sich nicht mit dem Ziel Rechteck überlappen, werden mit den Zeichen-und Farb Attributen aufgefüllt, die durch den *lpfill* -Parameter angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="eef5f-129">Those parts of *lpScrollRectangle* that do not overlap with the target rectangle are filled in with the character and color attributes specified by the *lpFill* parameter.</span></span>

<span data-ttu-id="eef5f-130">Das Clippingrechteck gilt für Änderungen, die sowohl im *lpscrollrechteck* -Rechteck als auch im Ziel Rechteck vorgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="eef5f-130">The clipping rectangle applies to changes made in both the *lpScrollRectangle* rectangle and the target rectangle.</span></span> <span data-ttu-id="eef5f-131">Wenn das Clippingrechteck z. b. keinen Bereich enthält, der durch den Inhalt von *lpfill* aufgefüllt wäre, bleibt der ursprüngliche Inhalt des Bereichs unverändert.</span><span class="sxs-lookup"><span data-stu-id="eef5f-131">For example, if the clipping rectangle does not include a region that would have been filled by the contents of *lpFill*, the original contents of the region are left unchanged.</span></span>

<span data-ttu-id="eef5f-132">Wenn die Bild Lauf-oder Zielbereiche die Abmessungen des Konsolenbildschirm Puffers überschreiten, werden Sie abgeschnitten.</span><span class="sxs-lookup"><span data-stu-id="eef5f-132">If the scroll or target regions extend beyond the dimensions of the console screen buffer, they are clipped.</span></span> <span data-ttu-id="eef5f-133">Wenn z. b. *lpscrollrechteck* der in (0,0) und (19, 19) enthaltene Bereich und *dwdestinationorigin* (10, 15) ist, ist das Ziel Rechteck der Bereich, der in (10, 15) und (29, 34) enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="eef5f-133">For example, if *lpScrollRectangle* is the region contained by (0,0) and (19,19) and *dwDestinationOrigin* is (10,15), the target rectangle is the region contained by (10,15) and (29,34).</span></span> <span data-ttu-id="eef5f-134">Wenn der Bildschirm Puffer der Konsole jedoch 50 Zeichen breit und 30 Zeichen hoch ist, wird das Ziel Rechteck auf (10, 15) und (29, 29) zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="eef5f-134">However, if the console screen buffer is 50 characters wide and 30 characters high, the target rectangle is clipped to (10,15) and (29,29).</span></span> <span data-ttu-id="eef5f-135">Änderungen am Konsolenbildschirm Puffer werden auch gemäß *lpcliprectangle* abgeschnitten, wenn der Parameter eine [**kleine \_ Rect**](small-rect-str.md) -Struktur angibt.</span><span class="sxs-lookup"><span data-stu-id="eef5f-135">Changes to the console screen buffer are also clipped according to *lpClipRectangle*, if the parameter specifies a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="eef5f-136">Wenn das Clippingrechteck als (0,0) und (49, 19) angegeben wird, werden nur die Änderungen vorgenommen, die in diesem Bereich des Konsolenbildschirm Puffers auftreten.</span><span class="sxs-lookup"><span data-stu-id="eef5f-136">If the clipping rectangle is specified as (0,0) and (49,19), only the changes that occur in that region of the console screen buffer are made.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="eef5f-137">Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="eef5f-137">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="eef5f-138">Die Verwendung von kann mit Bild Lauf **[Rändern](console-virtual-terminal-sequences.md#scrolling-margins)** , die **[Cursor Positionierung](console-virtual-terminal-sequences.md#cursor-positioning)** zum Festlegen der aktiven Position außerhalb des Bereichs und Zeilen Vorgängen zum Erzwingen von Text verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="eef5f-138">Use can be approximated with **[scroll margins](console-virtual-terminal-sequences.md#scrolling-margins)** to fix an area of the screen, **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** to set the active position outside the region, and newlines to force text to move.</span></span> <span data-ttu-id="eef5f-139">Der verbleibende Speicherplatz kann durch Verschieben des Cursors, **[festlegen grafischer Attribute](console-virtual-terminal-sequences.md#text-formatting)** und Schreiben von normalem Text aufgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="eef5f-139">The remaining space can be filled by moving the cursor, **[setting graphical attributes](console-virtual-terminal-sequences.md#text-formatting)**, and writing normal text.</span></span>

## <a name="examples"></a><span data-ttu-id="eef5f-140">Beispiele</span><span class="sxs-lookup"><span data-stu-id="eef5f-140">Examples</span></span>

<span data-ttu-id="eef5f-141">Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="eef5f-141">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="eef5f-142">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="eef5f-142">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="eef5f-143">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="eef5f-143">Minimum supported client</span></span> | <span data-ttu-id="eef5f-144">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="eef5f-144">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="eef5f-145">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="eef5f-145">Minimum supported server</span></span> | <span data-ttu-id="eef5f-146">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="eef5f-146">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="eef5f-147">Header</span><span class="sxs-lookup"><span data-stu-id="eef5f-147">Header</span></span> | <span data-ttu-id="eef5f-148">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="eef5f-148">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="eef5f-149">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="eef5f-149">Library</span></span> | <span data-ttu-id="eef5f-150">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="eef5f-150">Kernel32.lib</span></span> |
| <span data-ttu-id="eef5f-151">DLL</span><span class="sxs-lookup"><span data-stu-id="eef5f-151">DLL</span></span> | <span data-ttu-id="eef5f-152">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="eef5f-152">Kernel32.dll</span></span> |
| <span data-ttu-id="eef5f-153">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="eef5f-153">Unicode and ANSI names</span></span> | <span data-ttu-id="eef5f-154">**Scrollconsoleskreenbufferw** (Unicode) und **scrollconsoleskreenbuffera** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="eef5f-154">**ScrollConsoleScreenBufferW** (Unicode) and **ScrollConsoleScreenBufferA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="eef5f-155">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="eef5f-155">See also</span></span>

[<span data-ttu-id="eef5f-156">**Char- \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="eef5f-156">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="eef5f-157">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="eef5f-157">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="eef5f-158">**Koord**</span><span class="sxs-lookup"><span data-stu-id="eef5f-158">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="eef5f-159">Scrollen des Bildschirm Puffers</span><span class="sxs-lookup"><span data-stu-id="eef5f-159">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="eef5f-160">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="eef5f-160">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="eef5f-161">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="eef5f-161">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="eef5f-162">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="eef5f-162">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="eef5f-163">**kleine \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="eef5f-163">**SMALL\_RECT**</span></span>](small-rect-str.md)