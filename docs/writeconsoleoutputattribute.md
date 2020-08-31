---
title: Funktion "schreiteconsoleoutputattribute"
description: Kopiert eine Reihe von Zeichen Attributen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: e7c684b2f450713eaa78730676a0148e9b090c79
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060478"
---
# <a name="writeconsoleoutputattribute-function"></a><span data-ttu-id="db38d-104">Funktion "schreiteconsoleoutputattribute"</span><span class="sxs-lookup"><span data-stu-id="db38d-104">WriteConsoleOutputAttribute function</span></span>


<span data-ttu-id="db38d-105">Kopiert eine Reihe von Zeichen Attributen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="db38d-105">Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="db38d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="db38d-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a><span data-ttu-id="db38d-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="db38d-107">Parameters</span></span>
----------

<span data-ttu-id="db38d-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="db38d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="db38d-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="db38d-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="db38d-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="db38d-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="db38d-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="db38d-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="db38d-112">*lpattribute* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="db38d-112">*lpAttribute* \[in\]</span></span>  
<span data-ttu-id="db38d-113">Die Attribute, die beim Schreiben in den Konsolenbildschirm Puffer verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="db38d-113">The attributes to be used when writing to the console screen buffer.</span></span> <span data-ttu-id="db38d-114">Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="db38d-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="db38d-115">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="db38d-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="db38d-116">Die Anzahl der Zellen des Bildschirm Puffers, in die die Attribute kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="db38d-116">The number of screen buffer character cells to which the attributes will be copied.</span></span>

<span data-ttu-id="db38d-117">*dwschreitecoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="db38d-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="db38d-118">Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle im Konsolenbildschirm Puffer angibt, in die die Attribute geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="db38d-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.</span></span>

<span data-ttu-id="db38d-119">*lpnumofattrswritten* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="db38d-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="db38d-120">Ein Zeiger auf eine Variable, die die Anzahl der Attribute empfängt, die tatsächlich in den Konsolenbildschirm Puffer geschrieben wurden.</span><span class="sxs-lookup"><span data-stu-id="db38d-120">A pointer to a variable that receives the number of attributes actually written to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="db38d-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="db38d-121">Return value</span></span>
------------

<span data-ttu-id="db38d-122">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="db38d-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="db38d-123">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="db38d-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="db38d-124">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="db38d-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="db38d-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="db38d-125">Remarks</span></span>
-------

<span data-ttu-id="db38d-126">Wenn die Anzahl der Attribute, in die geschrieben werden soll, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden Attribute in die nächste Zeile geschrieben.</span><span class="sxs-lookup"><span data-stu-id="db38d-126">If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row.</span></span> <span data-ttu-id="db38d-127">Wenn die Anzahl der Attribute, in die geschrieben werden soll, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Attribute bis zum Ende des Bildschirm Puffers der Konsole geschrieben.</span><span class="sxs-lookup"><span data-stu-id="db38d-127">If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="db38d-128">Die Zeichen Werte an den Positionen, die in geschrieben werden, werden nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="db38d-128">The character values at the positions written to are not changed.</span></span>

<a name="requirements"></a><span data-ttu-id="db38d-129">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="db38d-129">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="db38d-130">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="db38d-130">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="db38d-131">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="db38d-131">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="db38d-132">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="db38d-132">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="db38d-133">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="db38d-133">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="db38d-134">Header</span><span class="sxs-lookup"><span data-stu-id="db38d-134">Header</span></span></p></td>
<td><span data-ttu-id="db38d-135">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="db38d-135">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="db38d-136">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="db38d-136">Library</span></span></p></td>
<td><span data-ttu-id="db38d-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="db38d-137">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="db38d-138">DLL</span><span class="sxs-lookup"><span data-stu-id="db38d-138">DLL</span></span></p></td>
<td><span data-ttu-id="db38d-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="db38d-139">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="db38d-140"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="db38d-140"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="db38d-141">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="db38d-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="db38d-142">**Koord**</span><span class="sxs-lookup"><span data-stu-id="db38d-142">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="db38d-143">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="db38d-143">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="db38d-144">**"Read consoleoutput"**</span><span class="sxs-lookup"><span data-stu-id="db38d-144">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="db38d-145">**"Read consoleoutputattribute"**</span><span class="sxs-lookup"><span data-stu-id="db38d-145">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="db38d-146">**"Read consoleoutputcharacter"**</span><span class="sxs-lookup"><span data-stu-id="db38d-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="db38d-147">**Schreibconsoleoutput**</span><span class="sxs-lookup"><span data-stu-id="db38d-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="db38d-148">**Schreibconsoleoutputcharacter**</span><span class="sxs-lookup"><span data-stu-id="db38d-148">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




