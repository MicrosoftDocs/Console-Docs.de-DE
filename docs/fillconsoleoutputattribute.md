---
title: Fillconsoleoutputattribute-Funktion
description: Legt die Zeichen Attribute für eine angegebene Anzahl von Zeichen Zellen fest, beginnend bei den angegebenen Koordinaten in einem Bildschirm Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 4b3df3a9922655835979136a33628e2be0663f4e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059882"
---
# <a name="fillconsoleoutputattribute-function"></a><span data-ttu-id="b64e3-104">Fillconsoleoutputattribute-Funktion</span><span class="sxs-lookup"><span data-stu-id="b64e3-104">FillConsoleOutputAttribute function</span></span>


<span data-ttu-id="b64e3-105">Legt die Zeichen Attribute für eine angegebene Anzahl von Zeichen Zellen fest, beginnend bei den angegebenen Koordinaten in einem Bildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="b64e3-105">Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="b64e3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b64e3-106">Syntax</span></span>
------

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a><span data-ttu-id="b64e3-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="b64e3-107">Parameters</span></span>
----------

<span data-ttu-id="b64e3-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b64e3-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="b64e3-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="b64e3-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="b64e3-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="b64e3-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="b64e3-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="b64e3-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="b64e3-112">*wattribute* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b64e3-112">*wAttribute* \[in\]</span></span>  
<span data-ttu-id="b64e3-113">Die Attribute, die beim Schreiben in den Konsolenbildschirm Puffer verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b64e3-113">The attributes to use when writing to the console screen buffer.</span></span> <span data-ttu-id="b64e3-114">Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="b64e3-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="b64e3-115">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b64e3-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="b64e3-116">Die Anzahl der Zeichen Zellen, die auf die angegebenen Farb Attribute festgelegt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b64e3-116">The number of character cells to be set to the specified color attributes.</span></span>

<span data-ttu-id="b64e3-117">*dwschreitecoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b64e3-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="b64e3-118">Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle angibt, deren Attribute festgelegt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b64e3-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.</span></span>

<span data-ttu-id="b64e3-119">*lpnumofattrswritten* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="b64e3-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="b64e3-120">Ein Zeiger auf eine Variable, die die Anzahl der Zeichen Zellen empfängt, deren Attribute tatsächlich festgelegt wurden.</span><span class="sxs-lookup"><span data-stu-id="b64e3-120">A pointer to a variable that receives the number of character cells whose attributes were actually set.</span></span>

<a name="return-value"></a><span data-ttu-id="b64e3-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b64e3-121">Return value</span></span>
------------

<span data-ttu-id="b64e3-122">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="b64e3-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b64e3-123">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="b64e3-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b64e3-124">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b64e3-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="b64e3-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b64e3-125">Remarks</span></span>
-------

<span data-ttu-id="b64e3-126">Wenn die Anzahl der Zeichen Zellen, deren Attribute festgelegt werden sollen, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden die Zellen der nächsten Zeile festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b64e3-126">If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set.</span></span> <span data-ttu-id="b64e3-127">Wenn die Anzahl der Zellen, die in geschrieben werden sollen, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Zellen bis zum Ende des Konsolenbildschirm Puffers geschrieben.</span><span class="sxs-lookup"><span data-stu-id="b64e3-127">If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="b64e3-128">Die Zeichen Werte an den Positionen, die in geschrieben werden, werden nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="b64e3-128">The character values at the positions written to are not changed.</span></span>

<a name="requirements"></a><span data-ttu-id="b64e3-129">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b64e3-129">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b64e3-130">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="b64e3-130">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b64e3-131">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="b64e3-131">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b64e3-132">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="b64e3-132">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b64e3-133">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="b64e3-133">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b64e3-134">Header</span><span class="sxs-lookup"><span data-stu-id="b64e3-134">Header</span></span></p></td>
<td><span data-ttu-id="b64e3-135">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b64e3-135">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b64e3-136">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="b64e3-136">Library</span></span></p></td>
<td><span data-ttu-id="b64e3-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b64e3-137">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b64e3-138">DLL</span><span class="sxs-lookup"><span data-stu-id="b64e3-138">DLL</span></span></p></td>
<td><span data-ttu-id="b64e3-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b64e3-139">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b64e3-140"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b64e3-140"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b64e3-141">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="b64e3-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b64e3-142">**Koord**</span><span class="sxs-lookup"><span data-stu-id="b64e3-142">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="b64e3-143">**Fillconsoleoutputcharacter**</span><span class="sxs-lookup"><span data-stu-id="b64e3-143">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="b64e3-144">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="b64e3-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="b64e3-145">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="b64e3-145">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="b64e3-146">**"Schreibconsoleoutputattribute"**</span><span class="sxs-lookup"><span data-stu-id="b64e3-146">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

 

 




