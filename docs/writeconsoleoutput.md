---
title: Funktion "Write-consoleoutput"
description: Schreibt Zeichen-und Farb Attributdaten in einen angegebenen rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 1f10285cfc5c671ac5d31b8a575e84b1fd0f6a14
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359030"
---
# <a name="writeconsoleoutput-function"></a><span data-ttu-id="86969-104">Funktion "Write-consoleoutput"</span><span class="sxs-lookup"><span data-stu-id="86969-104">WriteConsoleOutput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="86969-105">Schreibt Zeichen-und Farb Attributdaten in einen angegebenen rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="86969-105">Writes character and color attribute data to a specified rectangular block of character cells in a console screen buffer.</span></span> <span data-ttu-id="86969-106">Die zu schreibenden Daten werden aus einem rechteckigen rechteckigen Block an einer bestimmten Position im Quell Puffer entnommen.</span><span class="sxs-lookup"><span data-stu-id="86969-106">The data to be written is taken from a correspondingly sized rectangular block at a specified location in the source buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="86969-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="86969-107">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

## <a name="parameters"></a><span data-ttu-id="86969-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="86969-108">Parameters</span></span>

<span data-ttu-id="86969-109">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="86969-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="86969-110">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="86969-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="86969-111">Das Handle muss das Zugriffsrecht **GENERIC\_WRITE** besitzen.</span><span class="sxs-lookup"><span data-stu-id="86969-111">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="86969-112">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="86969-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="86969-113">*lpBuffer* \[in\]</span><span class="sxs-lookup"><span data-stu-id="86969-113">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="86969-114">Die Daten, die in den Konsolenbildschirm Puffer geschrieben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="86969-114">The data to be written to the console screen buffer.</span></span> <span data-ttu-id="86969-115">Dieser Zeiger wird als Ursprung eines zweidimensionalen Arrays von [**Char \_ Info**](char-info-str.md) -Strukturen behandelt, deren Größe durch den *dwbuffersize* -Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="86969-115">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="86969-116">*dwbuffersize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="86969-116">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="86969-117">Die Größe des Puffers, auf den durch den *lpBuffer* -Parameter in Zeichen Zellen verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="86969-117">The size of the buffer pointed to by the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="86969-118">Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die Anzahl der Spalten. der **Y** -Member ist die Anzahl der Zeilen.</span><span class="sxs-lookup"><span data-stu-id="86969-118">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="86969-119">*dwbuffercoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="86969-119">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="86969-120">Die Koordinaten der linken oberen Zelle im Puffer, auf die durch den *lpBuffer* -Parameter verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="86969-120">The coordinates of the upper-left cell in the buffer pointed to by the *lpBuffer* parameter.</span></span> <span data-ttu-id="86969-121">Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die-Spalte, und der **Y** -Member ist die Zeile.</span><span class="sxs-lookup"><span data-stu-id="86969-121">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="86969-122">*lpschreiteregion* \[ in, out\]</span><span class="sxs-lookup"><span data-stu-id="86969-122">*lpWriteRegion* \[in, out\]</span></span>  
<span data-ttu-id="86969-123">Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur.</span><span class="sxs-lookup"><span data-stu-id="86969-123">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="86969-124">Bei der Eingabe geben die Strukturmember die oberen linken und unteren rechten Koordinaten des Konsolenbildschirm-Puffer Rechtecks an, in das geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="86969-124">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to write to.</span></span> <span data-ttu-id="86969-125">Bei der Ausgabe geben die Strukturmember das tatsächliche Rechteck an, das verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="86969-125">On output, the structure members specify the actual rectangle that was used.</span></span>

## <a name="return-value"></a><span data-ttu-id="86969-126">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="86969-126">Return value</span></span>

<span data-ttu-id="86969-127">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="86969-127">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="86969-128">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="86969-128">If the function fails, the return value is zero.</span></span> <span data-ttu-id="86969-129">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="86969-129">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="86969-130">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="86969-130">Remarks</span></span>

<span data-ttu-id="86969-131">" **Write-consoleoutput** " behandelt den Quell-und den Zielbildschirm Puffer als zweidimensionale Arrays (Spalten und Zeilen von Zeichen Zellen).</span><span class="sxs-lookup"><span data-stu-id="86969-131">**WriteConsoleOutput** treats the source buffer and the destination screen buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="86969-132">Das Rechteck, auf das durch den *lpschreiteregion* -Parameter verwiesen wird, gibt die Größe und Position des Blocks an, in den in den Konsolenbildschirm Puffer geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="86969-132">The rectangle pointed to by the *lpWriteRegion* parameter specifies the size and location of the block to be written to in the console screen buffer.</span></span> <span data-ttu-id="86969-133">Ein Rechteck derselben Größe befindet sich mit seiner oberen linken Zelle an den Koordinaten des Parameters " *dwbuffercoord* " im *lpBuffer* -Array.</span><span class="sxs-lookup"><span data-stu-id="86969-133">A rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="86969-134">Daten aus den Zellen, die sich in der Schnittmenge dieses Rechtecks und des Quell Puffer Rechtecks befinden (dessen Dimensionen durch den *dwbuffersize* -Parameter angegeben werden), werden in das Ziel Rechteck geschrieben.</span><span class="sxs-lookup"><span data-stu-id="86969-134">Data from the cells that are in the intersection of this rectangle and the source buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter) is written to the destination rectangle.</span></span>

<span data-ttu-id="86969-135">Zellen im Ziel Rechteck, deren zugehöriger Quell Speicherort außerhalb der Grenzen des Quell Puffer Rechtecks liegt, bleiben beim Schreibvorgang unverändert.</span><span class="sxs-lookup"><span data-stu-id="86969-135">Cells in the destination rectangle whose corresponding source location are outside the boundaries of the source buffer rectangle are left unaffected by the write operation.</span></span> <span data-ttu-id="86969-136">Das heißt, dass es sich hierbei um die Zellen handelt, für die keine Daten geschrieben werden können.</span><span class="sxs-lookup"><span data-stu-id="86969-136">In other words, these are the cells for which no data is available to be written.</span></span>

<span data-ttu-id="86969-137">Vor der Rückgabe von " **Write-consoleoutput** " werden die Member von *lpbeschreib teregion* auf das tatsächliche Bildschirm Puffer Rechteck festgelegt, das von dem Schreibvorgang betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="86969-137">Before **WriteConsoleOutput** returns, it sets the members of *lpWriteRegion* to the actual screen buffer rectangle affected by the write operation.</span></span> <span data-ttu-id="86969-138">Dieses Rechteck reflektiert die Zellen im Ziel Rechteck, für die im Quell Puffer eine entsprechende Zelle vorhanden war, da " **Write-consoleoutput** " die Dimensionen des Ziel Rechtecks auf die Begrenzungen des Konsolenbildschirm Puffers schneidet.</span><span class="sxs-lookup"><span data-stu-id="86969-138">This rectangle reflects the cells in the destination rectangle for which there existed a corresponding cell in the source buffer, because **WriteConsoleOutput** clips the dimensions of the destination rectangle to the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="86969-139">Wenn das von *lpschreiteregion* angegebene Rechteck vollständig außerhalb der Grenzen des Konsolenbildschirm Puffers liegt oder wenn das entsprechende Rechteck vollständig außerhalb der Grenzen des Quell Puffers positioniert ist, werden keine Daten geschrieben.</span><span class="sxs-lookup"><span data-stu-id="86969-139">If the rectangle specified by *lpWriteRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the source buffer, no data is written.</span></span> <span data-ttu-id="86969-140">In diesem Fall gibt die-Funktion mit den Elementen der Struktur zurück, auf die durch den *lpschreiteregion* -Parametersatz verwiesen wird, sodass der **Rechte** Member kleiner als der **linke** Wert ist oder der **untere** Member kleiner als der **obere** Wert ist.</span><span class="sxs-lookup"><span data-stu-id="86969-140">In this case, the function returns with the members of the structure pointed to by the *lpWriteRegion* parameter set such that the **Right** member is less than the **Left**, or the **Bottom** member is less than the **Top**.</span></span> <span data-ttu-id="86969-141">Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die Größe des Konsolenbildschirm Puffers zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="86969-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="86969-142">" **Schreiteconsoleoutput** " hat keine Auswirkung auf die Cursorposition.</span><span class="sxs-lookup"><span data-stu-id="86969-142">**WriteConsoleOutput** has no effect on the cursor position.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="86969-143">Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent in den Positions Sequenzen für **[Textformatierung](console-virtual-terminal-sequences.md#text-formatting)** und **[Cursor](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="86969-143">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="86969-144">Bewegen Sie den Cursor an den einzufügenden Speicherort, wenden Sie die gewünschte Formatierung an, und schreiben Sie den Text.</span><span class="sxs-lookup"><span data-stu-id="86969-144">Move the cursor to the location to insert, apply the formatting desired, and write out the text.</span></span> <span data-ttu-id="86969-145">_Virtuelle Terminal Sequenzen_ werden für alle neuen und laufenden Entwicklungen empfohlen.</span><span class="sxs-lookup"><span data-stu-id="86969-145">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="86969-146">Beispiele</span><span class="sxs-lookup"><span data-stu-id="86969-146">Examples</span></span>

<span data-ttu-id="86969-147">Ein Beispiel finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="86969-147">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="86969-148">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="86969-148">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="86969-149">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="86969-149">Minimum supported client</span></span> | <span data-ttu-id="86969-150">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="86969-150">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="86969-151">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="86969-151">Minimum supported server</span></span> | <span data-ttu-id="86969-152">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="86969-152">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="86969-153">Header</span><span class="sxs-lookup"><span data-stu-id="86969-153">Header</span></span> | <span data-ttu-id="86969-154">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="86969-154">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="86969-155">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="86969-155">Library</span></span> | <span data-ttu-id="86969-156">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="86969-156">Kernel32.lib</span></span> |
| <span data-ttu-id="86969-157">DLL</span><span class="sxs-lookup"><span data-stu-id="86969-157">DLL</span></span> | <span data-ttu-id="86969-158">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="86969-158">Kernel32.dll</span></span> |
| <span data-ttu-id="86969-159">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="86969-159">Unicode and ANSI names</span></span> | <span data-ttu-id="86969-160">**Schreibconsoleoutputw** (Unicode) und **schreiteconsoleoutputa** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="86969-160">**WriteConsoleOutputW** (Unicode) and **WriteConsoleOutputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="86969-161">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="86969-161">See also</span></span>

[<span data-ttu-id="86969-162">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="86969-162">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="86969-163">**Char- \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="86969-163">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="86969-164">**Koord**</span><span class="sxs-lookup"><span data-stu-id="86969-164">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="86969-165">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="86969-165">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="86969-166">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="86969-166">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="86969-167">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="86969-167">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="86969-168">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="86969-168">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="86969-169">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="86969-169">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="86969-170">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="86969-170">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="86969-171">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="86969-171">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="86969-172">**kleine \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="86969-172">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="86969-173">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="86969-173">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="86969-174">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="86969-174">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)