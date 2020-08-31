---
title: Funktion "Write-consoleoutput"
description: Schreibt Zeichen-und Farb Attributdaten in einen angegebenen rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/WriteConsoleOutput
- wincon/WriteConsoleOutput
- WriteConsoleOutput
- consoleapi2/WriteConsoleOutputA
- wincon/WriteConsoleOutputA
- WriteConsoleOutputA
- consoleapi2/WriteConsoleOutputW
- wincon/WriteConsoleOutputW
- WriteConsoleOutputW
MS-HAID:
- '\_win32\_writeconsoleoutput'
- base.writeconsoleoutput
- consoles.writeconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a98b8118-97ce-4dd4-a337-122d4a76f232
topic_type:
- apiref
api_name:
- WriteConsoleOutput
- WriteConsoleOutputA
- WriteConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e2f84f5c072a8404b129e27bec3464363b9dd3d0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059563"
---
# <a name="writeconsoleoutput-function"></a><span data-ttu-id="df469-104">Funktion "Write-consoleoutput"</span><span class="sxs-lookup"><span data-stu-id="df469-104">WriteConsoleOutput function</span></span>


<span data-ttu-id="df469-105">Schreibt Zeichen-und Farb Attributdaten in einen angegebenen rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="df469-105">Writes character and color attribute data to a specified rectangular block of character cells in a console screen buffer.</span></span> <span data-ttu-id="df469-106">Die zu schreibenden Daten werden aus einem rechteckigen rechteckigen Block an einer bestimmten Position im Quell Puffer entnommen.</span><span class="sxs-lookup"><span data-stu-id="df469-106">The data to be written is taken from a correspondingly sized rectangular block at a specified location in the source buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="df469-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="df469-107">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

<a name="parameters"></a><span data-ttu-id="df469-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="df469-108">Parameters</span></span>
----------

<span data-ttu-id="df469-109">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="df469-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="df469-110">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="df469-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="df469-111">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="df469-111">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="df469-112">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="df469-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="df469-113">*lpBuffer* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="df469-113">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="df469-114">Die Daten, die in den Konsolenbildschirm Puffer geschrieben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="df469-114">The data to be written to the console screen buffer.</span></span> <span data-ttu-id="df469-115">Dieser Zeiger wird als Ursprung eines zweidimensionalen Arrays von [**Char \_ Info**](char-info-str.md) -Strukturen behandelt, deren Größe durch den *dwbuffersize* -Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="df469-115">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="df469-116">*dwbuffersize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="df469-116">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="df469-117">Die Größe des Puffers, auf den durch den *lpBuffer* -Parameter in Zeichen Zellen verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="df469-117">The size of the buffer pointed to by the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="df469-118">Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die Anzahl der Spalten. der **Y** -Member ist die Anzahl der Zeilen.</span><span class="sxs-lookup"><span data-stu-id="df469-118">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="df469-119">*dwbuffercoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="df469-119">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="df469-120">Die Koordinaten der linken oberen Zelle im Puffer, auf die durch den *lpBuffer* -Parameter verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="df469-120">The coordinates of the upper-left cell in the buffer pointed to by the *lpBuffer* parameter.</span></span> <span data-ttu-id="df469-121">Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die-Spalte, und der **Y** -Member ist die Zeile.</span><span class="sxs-lookup"><span data-stu-id="df469-121">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="df469-122">*lpschreiteregion* \[ in, out\]</span><span class="sxs-lookup"><span data-stu-id="df469-122">*lpWriteRegion* \[in, out\]</span></span>  
<span data-ttu-id="df469-123">Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur.</span><span class="sxs-lookup"><span data-stu-id="df469-123">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="df469-124">Bei der Eingabe geben die Strukturmember die oberen linken und unteren rechten Koordinaten des Konsolenbildschirm-Puffer Rechtecks an, in das geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="df469-124">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to write to.</span></span> <span data-ttu-id="df469-125">Bei der Ausgabe geben die Strukturmember das tatsächliche Rechteck an, das verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="df469-125">On output, the structure members specify the actual rectangle that was used.</span></span>

<a name="return-value"></a><span data-ttu-id="df469-126">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="df469-126">Return value</span></span>
------------

<span data-ttu-id="df469-127">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="df469-127">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="df469-128">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="df469-128">If the function fails, the return value is zero.</span></span> <span data-ttu-id="df469-129">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="df469-129">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="df469-130">Hinweise</span><span class="sxs-lookup"><span data-stu-id="df469-130">Remarks</span></span>
-------

<span data-ttu-id="df469-131">" **Write-consoleoutput** " behandelt den Quell-und den Zielbildschirm Puffer als zweidimensionale Arrays (Spalten und Zeilen von Zeichen Zellen).</span><span class="sxs-lookup"><span data-stu-id="df469-131">**WriteConsoleOutput** treats the source buffer and the destination screen buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="df469-132">Das Rechteck, auf das durch den *lpschreiteregion* -Parameter verwiesen wird, gibt die Größe und Position des Blocks an, in den in den Konsolenbildschirm Puffer geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="df469-132">The rectangle pointed to by the *lpWriteRegion* parameter specifies the size and location of the block to be written to in the console screen buffer.</span></span> <span data-ttu-id="df469-133">Ein Rechteck derselben Größe befindet sich mit seiner oberen linken Zelle an den Koordinaten des Parameters " *dwbuffercoord* " im *lpBuffer* -Array.</span><span class="sxs-lookup"><span data-stu-id="df469-133">A rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="df469-134">Daten aus den Zellen, die sich in der Schnittmenge dieses Rechtecks und des Quell Puffer Rechtecks befinden (dessen Dimensionen durch den *dwbuffersize* -Parameter angegeben werden), werden in das Ziel Rechteck geschrieben.</span><span class="sxs-lookup"><span data-stu-id="df469-134">Data from the cells that are in the intersection of this rectangle and the source buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter) is written to the destination rectangle.</span></span>

<span data-ttu-id="df469-135">Zellen im Ziel Rechteck, deren zugehöriger Quell Speicherort außerhalb der Grenzen des Quell Puffer Rechtecks liegt, bleiben beim Schreibvorgang unverändert.</span><span class="sxs-lookup"><span data-stu-id="df469-135">Cells in the destination rectangle whose corresponding source location are outside the boundaries of the source buffer rectangle are left unaffected by the write operation.</span></span> <span data-ttu-id="df469-136">Das heißt, dass es sich hierbei um die Zellen handelt, für die keine Daten geschrieben werden können.</span><span class="sxs-lookup"><span data-stu-id="df469-136">In other words, these are the cells for which no data is available to be written.</span></span>

<span data-ttu-id="df469-137">Vor der Rückgabe von " **Write-consoleoutput** " werden die Member von *lpbeschreib teregion* auf das tatsächliche Bildschirm Puffer Rechteck festgelegt, das von dem Schreibvorgang betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="df469-137">Before **WriteConsoleOutput** returns, it sets the members of *lpWriteRegion* to the actual screen buffer rectangle affected by the write operation.</span></span> <span data-ttu-id="df469-138">Dieses Rechteck reflektiert die Zellen im Ziel Rechteck, für die im Quell Puffer eine entsprechende Zelle vorhanden war, da " **Write-consoleoutput** " die Dimensionen des Ziel Rechtecks auf die Begrenzungen des Konsolenbildschirm Puffers schneidet.</span><span class="sxs-lookup"><span data-stu-id="df469-138">This rectangle reflects the cells in the destination rectangle for which there existed a corresponding cell in the source buffer, because **WriteConsoleOutput** clips the dimensions of the destination rectangle to the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="df469-139">Wenn das von *lpschreiteregion* angegebene Rechteck vollständig außerhalb der Grenzen des Konsolenbildschirm Puffers liegt oder wenn das entsprechende Rechteck vollständig außerhalb der Grenzen des Quell Puffers positioniert ist, werden keine Daten geschrieben.</span><span class="sxs-lookup"><span data-stu-id="df469-139">If the rectangle specified by *lpWriteRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the source buffer, no data is written.</span></span> <span data-ttu-id="df469-140">In diesem Fall gibt die-Funktion mit den Elementen der Struktur zurück, auf die durch den *lpschreiteregion* -Parametersatz verwiesen wird, sodass der **Rechte** Member kleiner als der **linke**Wert ist oder der **untere** Member kleiner als der **obere**Wert ist.</span><span class="sxs-lookup"><span data-stu-id="df469-140">In this case, the function returns with the members of the structure pointed to by the *lpWriteRegion* parameter set such that the **Right** member is less than the **Left**, or the **Bottom** member is less than the **Top**.</span></span> <span data-ttu-id="df469-141">Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die Größe des Konsolenbildschirm Puffers zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="df469-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="df469-142">" **Schreiteconsoleoutput** " hat keine Auswirkung auf die Cursorposition.</span><span class="sxs-lookup"><span data-stu-id="df469-142">**WriteConsoleOutput** has no effect on the cursor position.</span></span>

<span data-ttu-id="df469-143">Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole.</span><span class="sxs-lookup"><span data-stu-id="df469-143">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="df469-144">Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt.</span><span class="sxs-lookup"><span data-stu-id="df469-144">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="df469-145">Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="df469-145">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="df469-146">Beispiele</span><span class="sxs-lookup"><span data-stu-id="df469-146">Examples</span></span>
--------

<span data-ttu-id="df469-147">Ein Beispiel finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="df469-147">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="df469-148">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="df469-148">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="df469-149">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="df469-149">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="df469-150">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="df469-150">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="df469-151">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="df469-151">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="df469-152">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="df469-152">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="df469-153">Header</span><span class="sxs-lookup"><span data-stu-id="df469-153">Header</span></span></p></td>
<td><span data-ttu-id="df469-154">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="df469-154">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="df469-155">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="df469-155">Library</span></span></p></td>
<td><span data-ttu-id="df469-156">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="df469-156">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="df469-157">DLL</span><span class="sxs-lookup"><span data-stu-id="df469-157">DLL</span></span></p></td>
<td><span data-ttu-id="df469-158">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="df469-158">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="df469-159">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="df469-159">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="df469-160"><strong>Schreibconsoleoutputw</strong> (Unicode) und <strong>schreiteconsoleoutputa</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="df469-160"><strong>WriteConsoleOutputW</strong> (Unicode) and <strong>WriteConsoleOutputA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="df469-161"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="df469-161"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="df469-162">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="df469-162">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="df469-163">**Char- \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="df469-163">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="df469-164">**Koord**</span><span class="sxs-lookup"><span data-stu-id="df469-164">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="df469-165">**Getconsoleskreenbufferinfo**</span><span class="sxs-lookup"><span data-stu-id="df469-165">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="df469-166">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="df469-166">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="df469-167">**"Read consoleoutput"**</span><span class="sxs-lookup"><span data-stu-id="df469-167">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="df469-168">**"Read consoleoutputattribute"**</span><span class="sxs-lookup"><span data-stu-id="df469-168">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="df469-169">**"Read consoleoutputcharacter"**</span><span class="sxs-lookup"><span data-stu-id="df469-169">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="df469-170">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="df469-170">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="df469-171">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="df469-171">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="df469-172">**kleine \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="df469-172">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="df469-173">**"Schreibconsoleoutputattribute"**</span><span class="sxs-lookup"><span data-stu-id="df469-173">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="df469-174">**Schreibconsoleoutputcharacter**</span><span class="sxs-lookup"><span data-stu-id="df469-174">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




