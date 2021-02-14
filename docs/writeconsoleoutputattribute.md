---
title: Funktion "schreiteconsoleoutputattribute"
description: Kopiert eine Reihe von Zeichen Attributen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d4c940243b8367e2f66923c14ffa90de7c9a384b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357760"
---
# <a name="writeconsoleoutputattribute-function"></a><span data-ttu-id="c3d2f-104">Funktion "schreiteconsoleoutputattribute"</span><span class="sxs-lookup"><span data-stu-id="c3d2f-104">WriteConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c3d2f-105">Kopiert eine Reihe von Zeichen Attributen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-105">Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3d2f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c3d2f-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="c3d2f-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="c3d2f-107">Parameters</span></span>

<span data-ttu-id="c3d2f-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c3d2f-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="c3d2f-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="c3d2f-110">Das Handle muss das Zugriffsrecht **GENERIC\_WRITE** besitzen.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="c3d2f-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="c3d2f-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="c3d2f-112">*lpattribute* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c3d2f-112">*lpAttribute* \[in\]</span></span>  
<span data-ttu-id="c3d2f-113">Die Attribute, die beim Schreiben in den Konsolenbildschirm Puffer verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-113">The attributes to be used when writing to the console screen buffer.</span></span> <span data-ttu-id="c3d2f-114">Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="c3d2f-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="c3d2f-115">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c3d2f-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="c3d2f-116">Die Anzahl der Zellen des Bildschirm Puffers, in die die Attribute kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-116">The number of screen buffer character cells to which the attributes will be copied.</span></span>

<span data-ttu-id="c3d2f-117">*dwschreitecoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c3d2f-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="c3d2f-118">Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle im Konsolenbildschirm Puffer angibt, in die die Attribute geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.</span></span>

<span data-ttu-id="c3d2f-119">*lpnumofattrswritten* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="c3d2f-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="c3d2f-120">Ein Zeiger auf eine Variable, die die Anzahl der Attribute empfängt, die tatsächlich in den Konsolenbildschirm Puffer geschrieben wurden.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-120">A pointer to a variable that receives the number of attributes actually written to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="c3d2f-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c3d2f-121">Return value</span></span>

<span data-ttu-id="c3d2f-122">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c3d2f-123">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c3d2f-124">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="c3d2f-125">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="c3d2f-125">Remarks</span></span>

<span data-ttu-id="c3d2f-126">Wenn die Anzahl der Attribute, in die geschrieben werden soll, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden Attribute in die nächste Zeile geschrieben.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-126">If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row.</span></span> <span data-ttu-id="c3d2f-127">Wenn die Anzahl der Attribute, in die geschrieben werden soll, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Attribute bis zum Ende des Bildschirm Puffers der Konsole geschrieben.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-127">If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="c3d2f-128">Die Zeichen Werte an den Positionen, die in geschrieben werden, werden nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="c3d2f-129">Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent in den Positions Sequenzen für **[Textformatierung](console-virtual-terminal-sequences.md#text-formatting)** und **[Cursor](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="c3d2f-129">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="c3d2f-130">Bewegen Sie den Cursor an den einzufügenden Speicherort, wenden Sie die gewünschte Formatierung an, und schreiben Sie Text, um ihn auszufüllen.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-130">Move the cursor to the location to insert, apply the formatting desired, and write out text to fill.</span></span> <span data-ttu-id="c3d2f-131">Es gibt keine Entsprechung für das Anwenden von Farben auf einen Bereich, ohne dass auch Text ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-131">There is no equivalent to apply color to an area without also emitting text.</span></span> <span data-ttu-id="c3d2f-132">Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus, bei denen die jeweilige Client Anwendung ihren eigenen gezeichneten Zustand zur weiteren Bearbeitung merken soll.</span><span class="sxs-lookup"><span data-stu-id="c3d2f-132">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3d2f-133">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c3d2f-133">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c3d2f-134">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="c3d2f-134">Minimum supported client</span></span> | <span data-ttu-id="c3d2f-135">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="c3d2f-135">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c3d2f-136">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="c3d2f-136">Minimum supported server</span></span> | <span data-ttu-id="c3d2f-137">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="c3d2f-137">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c3d2f-138">Header</span><span class="sxs-lookup"><span data-stu-id="c3d2f-138">Header</span></span> | <span data-ttu-id="c3d2f-139">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c3d2f-139">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c3d2f-140">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="c3d2f-140">Library</span></span> | <span data-ttu-id="c3d2f-141">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c3d2f-141">Kernel32.lib</span></span> |
| <span data-ttu-id="c3d2f-142">DLL</span><span class="sxs-lookup"><span data-stu-id="c3d2f-142">DLL</span></span> | <span data-ttu-id="c3d2f-143">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c3d2f-143">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c3d2f-144">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c3d2f-144">See also</span></span>

[<span data-ttu-id="c3d2f-145">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="c3d2f-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c3d2f-146">**Koord**</span><span class="sxs-lookup"><span data-stu-id="c3d2f-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="c3d2f-147">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="c3d2f-147">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="c3d2f-148">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="c3d2f-148">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="c3d2f-149">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="c3d2f-149">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="c3d2f-150">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="c3d2f-150">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="c3d2f-151">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="c3d2f-151">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="c3d2f-152">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="c3d2f-152">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)