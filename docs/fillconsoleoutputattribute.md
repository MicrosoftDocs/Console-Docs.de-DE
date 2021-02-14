---
title: Fillconsoleoutputattribute-Funktion
description: Legt die Zeichen Attribute für eine angegebene Anzahl von Zeichen Zellen fest, beginnend bei den angegebenen Koordinaten in einem Bildschirm Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8b88bfcc264d1370479eef300cea2868142fbb8c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357910"
---
# <a name="fillconsoleoutputattribute-function"></a><span data-ttu-id="1d4b0-104">Fillconsoleoutputattribute-Funktion</span><span class="sxs-lookup"><span data-stu-id="1d4b0-104">FillConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="1d4b0-105">Legt die Zeichen Attribute für eine angegebene Anzahl von Zeichen Zellen fest, beginnend bei den angegebenen Koordinaten in einem Bildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-105">Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="1d4b0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1d4b0-106">Syntax</span></span>

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="1d4b0-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="1d4b0-107">Parameters</span></span>

<span data-ttu-id="1d4b0-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1d4b0-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="1d4b0-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="1d4b0-110">Das Handle muss das Zugriffsrecht **GENERIC\_WRITE** besitzen.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="1d4b0-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="1d4b0-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="1d4b0-112">*wattribute* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1d4b0-112">*wAttribute* \[in\]</span></span>  
<span data-ttu-id="1d4b0-113">Die Attribute, die beim Schreiben in den Konsolenbildschirm Puffer verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-113">The attributes to use when writing to the console screen buffer.</span></span> <span data-ttu-id="1d4b0-114">Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="1d4b0-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="1d4b0-115">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1d4b0-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="1d4b0-116">Die Anzahl der Zeichen Zellen, die auf die angegebenen Farb Attribute festgelegt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-116">The number of character cells to be set to the specified color attributes.</span></span>

<span data-ttu-id="1d4b0-117">*dwschreitecoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1d4b0-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="1d4b0-118">Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle angibt, deren Attribute festgelegt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.</span></span>

<span data-ttu-id="1d4b0-119">*lpnumofattrswritten* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="1d4b0-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="1d4b0-120">Ein Zeiger auf eine Variable, die die Anzahl der Zeichen Zellen empfängt, deren Attribute tatsächlich festgelegt wurden.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-120">A pointer to a variable that receives the number of character cells whose attributes were actually set.</span></span>

## <a name="return-value"></a><span data-ttu-id="1d4b0-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1d4b0-121">Return value</span></span>

<span data-ttu-id="1d4b0-122">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1d4b0-123">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1d4b0-124">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="1d4b0-125">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="1d4b0-125">Remarks</span></span>

<span data-ttu-id="1d4b0-126">Wenn die Anzahl der Zeichen Zellen, deren Attribute festgelegt werden sollen, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden die Zellen der nächsten Zeile festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-126">If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set.</span></span> <span data-ttu-id="1d4b0-127">Wenn die Anzahl der Zellen, die in geschrieben werden sollen, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Zellen bis zum Ende des Konsolenbildschirm Puffers geschrieben.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-127">If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="1d4b0-128">Die Zeichen Werte an den Positionen, die in geschrieben werden, werden nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="1d4b0-129">Diese API wird nicht empfohlen und weist keine bestimmte **[virtuelle Terminal](console-virtual-terminal-sequences.md)** Entsprechung auf.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-129">This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="1d4b0-130">Das Ausfüllen des Bereichs außerhalb des Anzeige Fensters wird nicht unterstützt und ist für den Verlaufs Bereich des Terminal reserviert.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-130">Filling the region outside the viewable window is not supported and is reserved for the terminal's history space.</span></span> <span data-ttu-id="1d4b0-131">Das Ausfüllen eines sichtbaren Bereichs mit neuem Text oder einer Farbe erfolgt durch **[das Verschieben des Cursors](console-virtual-terminal-sequences.md#cursor-positioning)**, **[das Festlegen der neuen Attribute](console-virtual-terminal-sequences.md#text-formatting)**, das anschließende Schreiben des gewünschten Texts für diesen Bereich und das Wiederholen von Zeichen, wenn dies für die Länge der Füllungs Ausführung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-131">Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)**, **[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)**, then writing the desired text for that region, repeating characters if necessary for the length of the fill run.</span></span> <span data-ttu-id="1d4b0-132">Möglicherweise ist eine zusätzliche Cursor Bewegung erforderlich, gefolgt von dem Schreiben des gewünschten Texts zum Ausfüllen eines rechteckigen Bereichs.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-132">Additional cursor movement may be required followed by writing the desired text to fill a rectangular region.</span></span> <span data-ttu-id="1d4b0-133">Es wird erwartet, dass die Client Anwendung ihren eigenen Arbeitsspeicher auf dem Bildschirm hält und den Remote Status nicht Abfragen kann.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-133">The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state.</span></span> <span data-ttu-id="1d4b0-134">Weitere Informationen finden Sie in der **[klassischen Konsole im Vergleich](classic-vs-vt.md)** zu der Dokumentation zu virtuellen Terminals.</span><span class="sxs-lookup"><span data-stu-id="1d4b0-134">More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.</span></span>

## <a name="requirements"></a><span data-ttu-id="1d4b0-135">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1d4b0-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1d4b0-136">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="1d4b0-136">Minimum supported client</span></span> | <span data-ttu-id="1d4b0-137">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1d4b0-137">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1d4b0-138">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="1d4b0-138">Minimum supported server</span></span> | <span data-ttu-id="1d4b0-139">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1d4b0-139">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1d4b0-140">Header</span><span class="sxs-lookup"><span data-stu-id="1d4b0-140">Header</span></span> | <span data-ttu-id="1d4b0-141">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1d4b0-141">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="1d4b0-142">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="1d4b0-142">Library</span></span> | <span data-ttu-id="1d4b0-143">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="1d4b0-143">Kernel32.lib</span></span> |
| <span data-ttu-id="1d4b0-144">DLL</span><span class="sxs-lookup"><span data-stu-id="1d4b0-144">DLL</span></span> | <span data-ttu-id="1d4b0-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1d4b0-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="1d4b0-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1d4b0-146">See also</span></span>

[<span data-ttu-id="1d4b0-147">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="1d4b0-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1d4b0-148">**Koord**</span><span class="sxs-lookup"><span data-stu-id="1d4b0-148">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="1d4b0-149">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="1d4b0-149">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="1d4b0-150">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="1d4b0-150">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="1d4b0-151">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="1d4b0-151">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="1d4b0-152">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="1d4b0-152">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)