---
title: Getconsoleskreenbufferinfo-Funktion
description: Siehe Referenzinformationen zur getconsoleskreenbufferinfo-Funktion, die Informationen zum angegebenen Konsolenbildschirm Puffer abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 8ced380982705647b7944cee0f72c723c38776c3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059715"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="15db4-104">Getconsoleskreenbufferinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="15db4-104">GetConsoleScreenBufferInfo function</span></span>


<span data-ttu-id="15db4-105">Ruft Informationen zum angegebenen Konsolenbildschirm Puffer ab.</span><span class="sxs-lookup"><span data-stu-id="15db4-105">Retrieves information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="15db4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="15db4-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

<a name="parameters"></a><span data-ttu-id="15db4-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="15db4-107">Parameters</span></span>
----------

<span data-ttu-id="15db4-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="15db4-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="15db4-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="15db4-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="15db4-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="15db4-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="15db4-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="15db4-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="15db4-112">*lpconsoleskreenbufferinfo* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="15db4-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="15db4-113">Ein Zeiger auf eine [**Konsolen \_ Bildschirm- \_ Puffer \_ Info**](console-screen-buffer-info-str.md) Struktur, die die Bildschirm Puffer Informationen der Konsole empfängt.</span><span class="sxs-lookup"><span data-stu-id="15db4-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="15db4-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="15db4-114">Return value</span></span>
------------

<span data-ttu-id="15db4-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="15db4-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="15db4-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="15db4-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="15db4-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="15db4-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="15db4-118">Hinweise</span><span class="sxs-lookup"><span data-stu-id="15db4-118">Remarks</span></span>
-------

<span data-ttu-id="15db4-119">Das Rechteck, das im **srwindow** -Member der [**Konsolen \_ Bildschirm \_ Puffer \_ Info**](console-screen-buffer-info-str.md) -Struktur zurückgegeben wird, kann geändert und dann an die [**setconsolewindowinfo**](setconsolewindowinfo.md) -Funktion weitergegeben werden, um einen Bildlauf des Konsolenbildschirm Puffers im-Fenster durchführen, um die Größe des Fensters zu ändern oder beides.</span><span class="sxs-lookup"><span data-stu-id="15db4-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="15db4-120">Alle Koordinaten, die in der [**Konsolen \_ Bildschirm \_ Puffer \_ Info**](console-screen-buffer-info-str.md) -Struktur zurückgegeben werden, sind in Zeichen Zell Koordinaten, wobei sich der Ursprung (0,0) in der oberen linken Ecke des Konsolenbildschirm Puffers befindet.</span><span class="sxs-lookup"><span data-stu-id="15db4-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

<a name="examples"></a><span data-ttu-id="15db4-121">Beispiele</span><span class="sxs-lookup"><span data-stu-id="15db4-121">Examples</span></span>
--------

<span data-ttu-id="15db4-122">Ein Beispiel finden Sie unter [Scrollen des Fensters eines Bildschirm Puffers](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="15db4-122">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

<a name="requirements"></a><span data-ttu-id="15db4-123">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="15db4-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="15db4-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="15db4-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="15db4-125">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="15db4-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="15db4-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="15db4-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="15db4-127">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="15db4-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="15db4-128">Header</span><span class="sxs-lookup"><span data-stu-id="15db4-128">Header</span></span></p></td>
<td><span data-ttu-id="15db4-129">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="15db4-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="15db4-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="15db4-130">Library</span></span></p></td>
<td><span data-ttu-id="15db4-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="15db4-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="15db4-132">DLL</span><span class="sxs-lookup"><span data-stu-id="15db4-132">DLL</span></span></p></td>
<td><span data-ttu-id="15db4-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="15db4-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="15db4-134"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="15db4-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="15db4-135">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="15db4-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="15db4-136">**Konsolen \_ Bildschirm- \_ Puffer \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="15db4-136">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="15db4-137">**Getlargestconsolewindowsize**</span><span class="sxs-lookup"><span data-stu-id="15db4-137">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="15db4-138">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="15db4-138">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="15db4-139">**Setconsoleskreenbuffersize**</span><span class="sxs-lookup"><span data-stu-id="15db4-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="15db4-140">**Setconsolewindowinfo**</span><span class="sxs-lookup"><span data-stu-id="15db4-140">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="15db4-141">Fenster-und Bildschirm Puffergröße</span><span class="sxs-lookup"><span data-stu-id="15db4-141">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)

 

 




