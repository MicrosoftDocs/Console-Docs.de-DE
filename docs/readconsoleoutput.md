---
title: Funktion "Read consoleoutput"
description: Liest Zeichen-und Farb Attributdaten aus einem rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer und schreibt Daten in den Ziel Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/ReadConsoleOutput
- wincon/ReadConsoleOutput
- ReadConsoleOutput
- consoleapi2/ReadConsoleOutputA
- wincon/ReadConsoleOutputA
- ReadConsoleOutputA
- consoleapi2/ReadConsoleOutputW
- wincon/ReadConsoleOutputW
- ReadConsoleOutputW
MS-HAID:
- '\_win32\_readconsoleoutput'
- base.readconsoleoutput
- consoles.readconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d1391684-6a8f-4b5e-9706-11970a957710
topic_type:
- apiref
api_name:
- ReadConsoleOutput
- ReadConsoleOutputA
- ReadConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c17f9c3b44ba0d64fcf47659cf24d08d5c76cfdc
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358730"
---
# <a name="readconsoleoutput-function"></a><span data-ttu-id="70bb0-104">Funktion "Read consoleoutput"</span><span class="sxs-lookup"><span data-stu-id="70bb0-104">ReadConsoleOutput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="70bb0-105">Liest Zeichen-und Farb Attributdaten aus einem rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer, und die-Funktion schreibt die Daten in einen rechteckigen Block an einer bestimmten Position im Ziel Puffer.</span><span class="sxs-lookup"><span data-stu-id="70bb0-105">Reads character and color attribute data from a rectangular block of character cells in a console screen buffer, and the function writes the data to a rectangular block at a specified location in the destination buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="70bb0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="70bb0-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

## <a name="parameters"></a><span data-ttu-id="70bb0-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="70bb0-107">Parameters</span></span>

<span data-ttu-id="70bb0-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="70bb0-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="70bb0-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="70bb0-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="70bb0-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="70bb0-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="70bb0-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="70bb0-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="70bb0-112">*lpBuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="70bb0-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="70bb0-113">Ein Zeiger auf einen Ziel Puffer, der die aus dem Konsolenbildschirm Puffer gelesenen Daten empfängt.</span><span class="sxs-lookup"><span data-stu-id="70bb0-113">A pointer to a destination buffer that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="70bb0-114">Dieser Zeiger wird als Ursprung eines zweidimensionalen Arrays von [**Char \_ Info**](char-info-str.md) -Strukturen behandelt, deren Größe durch den *dwbuffersize* -Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="70bb0-114">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="70bb0-115">*dwbuffersize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="70bb0-115">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="70bb0-116">Die Größe des *lpBuffer* -Parameters in Zeichen Zellen.</span><span class="sxs-lookup"><span data-stu-id="70bb0-116">The size of the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="70bb0-117">Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die Anzahl der Spalten. der **Y** -Member ist die Anzahl der Zeilen.</span><span class="sxs-lookup"><span data-stu-id="70bb0-117">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="70bb0-118">*dwbuffercoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="70bb0-118">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="70bb0-119">Die Koordinaten der linken oberen Zelle im *lpBuffer* -Parameter, die die aus dem Konsolenbildschirm Puffer gelesenen Daten empfängt.</span><span class="sxs-lookup"><span data-stu-id="70bb0-119">The coordinates of the upper-left cell in the *lpBuffer* parameter that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="70bb0-120">Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die-Spalte, und der **Y** -Member ist die Zeile.</span><span class="sxs-lookup"><span data-stu-id="70bb0-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="70bb0-121">*lpreadregion* \[ in, out\]</span><span class="sxs-lookup"><span data-stu-id="70bb0-121">*lpReadRegion* \[in, out\]</span></span>  
<span data-ttu-id="70bb0-122">Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur.</span><span class="sxs-lookup"><span data-stu-id="70bb0-122">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="70bb0-123">Bei der Eingabe geben die Strukturmember die oberen linken und unteren rechten Koordinaten des Konsolenbildschirm-Puffer Rechtecks an, von dem die Funktion gelesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="70bb0-123">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle from which the function is to read.</span></span> <span data-ttu-id="70bb0-124">Bei der Ausgabe geben die Strukturmember das tatsächliche Rechteck an, das verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="70bb0-124">On output, the structure members specify the actual rectangle that was used.</span></span>

## <a name="return-value"></a><span data-ttu-id="70bb0-125">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="70bb0-125">Return value</span></span>

<span data-ttu-id="70bb0-126">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="70bb0-126">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="70bb0-127">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="70bb0-127">If the function fails, the return value is zero.</span></span> <span data-ttu-id="70bb0-128">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="70bb0-128">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="70bb0-129">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="70bb0-129">Remarks</span></span>

<span data-ttu-id="70bb0-130">Der Bildschirm Puffer der Konsole und der Ziel Puffer werden von "read **consoleoutput** " als zweidimensionale Arrays (Spalten und Zeilen von Zeichen Zellen) behandelt.</span><span class="sxs-lookup"><span data-stu-id="70bb0-130">**ReadConsoleOutput** treats the console screen buffer and the destination buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="70bb0-131">Das Rechteck, auf das durch den *lpreadregion* -Parameter verwiesen wird, gibt die Größe und Position des Blocks an, der aus dem Konsolenbildschirm Puffer gelesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="70bb0-131">The rectangle pointed to by the *lpReadRegion* parameter specifies the size and location of the block to be read from the console screen buffer.</span></span> <span data-ttu-id="70bb0-132">Ein Ziel Rechteck derselben Größe befindet sich mit seiner oberen linken Zelle an den Koordinaten des Parameters " *dwbuffercoord* " im *lpBuffer* -Array.</span><span class="sxs-lookup"><span data-stu-id="70bb0-132">A destination rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="70bb0-133">Aus den Zellen des Konsolenbildschirm-Puffer Quell Rechtecks gelesene Daten werden in die entsprechenden Zellen im Ziel Puffer kopiert.</span><span class="sxs-lookup"><span data-stu-id="70bb0-133">Data read from the cells in the console screen buffer source rectangle is copied to the corresponding cells in the destination buffer.</span></span> <span data-ttu-id="70bb0-134">Wenn sich die entsprechende Zelle außerhalb der Grenzen des Ziel Puffer Rechtecks befindet (dessen Abmessungen durch den *dwbuffersize* -Parameter angegeben werden), werden die Daten nicht kopiert.</span><span class="sxs-lookup"><span data-stu-id="70bb0-134">If the corresponding cell is outside the boundaries of the destination buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter), the data is not copied.</span></span>

<span data-ttu-id="70bb0-135">Zellen im Ziel Puffer, die den Koordinaten entsprechen, die sich nicht innerhalb der Grenzen des Konsolenbildschirm Puffers befinden, bleiben unverändert.</span><span class="sxs-lookup"><span data-stu-id="70bb0-135">Cells in the destination buffer corresponding to coordinates that are not within the boundaries of the console screen buffer are left unchanged.</span></span> <span data-ttu-id="70bb0-136">Anders ausgedrückt: Dies sind die Zellen, für die keine Bildschirm Puffer Daten zum Lesen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="70bb0-136">In other words, these are the cells for which no screen buffer data is available to be read.</span></span>

<span data-ttu-id="70bb0-137">Vor der Rückgabe von "read **consoleoutput** " werden die Member der Struktur, auf die durch den *lpreadregion* -Parameter verwiesen wird, auf das tatsächliche Bildschirm Puffer Rechteck festgelegt, dessen Zellen in den Ziel Puffer kopiert wurden.</span><span class="sxs-lookup"><span data-stu-id="70bb0-137">Before **ReadConsoleOutput** returns, it sets the members of the structure pointed to by the *lpReadRegion* parameter to the actual screen buffer rectangle whose cells were copied into the destination buffer.</span></span> <span data-ttu-id="70bb0-138">Dieses Rechteck reflektiert die Zellen im Quell Rechteck, für die im Ziel Puffer eine entsprechende Zelle vorhanden war, da die Dimensionen des Quell Rechtecks von "read **consoleoutput** " an die Grenzen des Konsolenbildschirm Puffers angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="70bb0-138">This rectangle reflects the cells in the source rectangle for which there existed a corresponding cell in the destination buffer, because **ReadConsoleOutput** clips the dimensions of the source rectangle to fit the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="70bb0-139">Wenn das von *lpreadregion* angegebene Rechteck vollständig außerhalb der Grenzen des Konsolenbildschirm Puffers liegt oder das entsprechende Rechteck vollständig außerhalb der Grenzen des Ziel Puffers positioniert ist, werden keine Daten kopiert.</span><span class="sxs-lookup"><span data-stu-id="70bb0-139">If the rectangle specified by *lpReadRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the destination buffer, no data is copied.</span></span> <span data-ttu-id="70bb0-140">In diesem Fall gibt die-Funktion mit den Elementen der Struktur zurück, auf die durch den *lpreadregion* -Parametersatz verwiesen wird, sodass der **Rechte** Member kleiner als der **linke** Wert ist oder der **untere** Member kleiner als der **obere** Wert ist.</span><span class="sxs-lookup"><span data-stu-id="70bb0-140">In this case, the function returns with the members of the structure pointed to by the *lpReadRegion* parameter set such that the **Right** member is less than the **Left**, or the **Bottom** member is less than the **Top**.</span></span> <span data-ttu-id="70bb0-141">Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die Größe des Konsolenbildschirm Puffers zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="70bb0-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="70bb0-142">Die Funktion "read **consoleoutput** " hat keine Auswirkung auf die Cursorposition des Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="70bb0-142">The **ReadConsoleOutput** function has no effect on the console screen buffer's cursor position.</span></span> <span data-ttu-id="70bb0-143">Der Inhalt des Konsolenbildschirm Puffers wird von der-Funktion nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="70bb0-143">The contents of the console screen buffer are not changed by the function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="examples"></a><span data-ttu-id="70bb0-144">Beispiele</span><span class="sxs-lookup"><span data-stu-id="70bb0-144">Examples</span></span>

<span data-ttu-id="70bb0-145">Ein Beispiel finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="70bb0-145">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="70bb0-146">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="70bb0-146">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="70bb0-147">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="70bb0-147">Minimum supported client</span></span> | <span data-ttu-id="70bb0-148">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="70bb0-148">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="70bb0-149">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="70bb0-149">Minimum supported server</span></span> | <span data-ttu-id="70bb0-150">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="70bb0-150">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="70bb0-151">Header</span><span class="sxs-lookup"><span data-stu-id="70bb0-151">Header</span></span> | <span data-ttu-id="70bb0-152">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="70bb0-152">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="70bb0-153">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="70bb0-153">Library</span></span> | <span data-ttu-id="70bb0-154">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="70bb0-154">Kernel32.lib</span></span> |
| <span data-ttu-id="70bb0-155">DLL</span><span class="sxs-lookup"><span data-stu-id="70bb0-155">DLL</span></span> | <span data-ttu-id="70bb0-156">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="70bb0-156">Kernel32.dll</span></span> |
| <span data-ttu-id="70bb0-157">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="70bb0-157">Unicode and ANSI names</span></span> | <span data-ttu-id="70bb0-158">"Read **consoleoutputw** (Unicode)" und "read **consoleoutputa** " (ANSI)</span><span class="sxs-lookup"><span data-stu-id="70bb0-158">**ReadConsoleOutputW** (Unicode) and **ReadConsoleOutputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="70bb0-159">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="70bb0-159">See also</span></span>

[<span data-ttu-id="70bb0-160">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="70bb0-160">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="70bb0-161">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="70bb0-161">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="70bb0-162">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="70bb0-162">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="70bb0-163">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="70bb0-163">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="70bb0-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="70bb0-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="70bb0-165">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="70bb0-165">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="70bb0-166">**kleine \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="70bb0-166">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="70bb0-167">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="70bb0-167">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="70bb0-168">**Char- \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="70bb0-168">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="70bb0-169">**Koord**</span><span class="sxs-lookup"><span data-stu-id="70bb0-169">**COORD**</span></span>](coord-str.md)