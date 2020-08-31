---
title: Getconsoleskreenbufferinfoex-Funktion
description: Ruft erweiterte Informationen zum angegebenen Bildschirm Puffer der Konsole ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 69cb3c59af1a93cf6af664bbecaf05ef00b64ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059747"
---
# <a name="getconsolescreenbufferinfoex-function"></a><span data-ttu-id="09e8f-104">Getconsoleskreenbufferinfoex-Funktion</span><span class="sxs-lookup"><span data-stu-id="09e8f-104">GetConsoleScreenBufferInfoEx function</span></span>


<span data-ttu-id="09e8f-105">Ruft erweiterte Informationen zum angegebenen Bildschirm Puffer der Konsole ab.</span><span class="sxs-lookup"><span data-stu-id="09e8f-105">Retrieves extended information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="09e8f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="09e8f-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

<a name="parameters"></a><span data-ttu-id="09e8f-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="09e8f-107">Parameters</span></span>
----------

<span data-ttu-id="09e8f-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="09e8f-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="09e8f-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="09e8f-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="09e8f-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="09e8f-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="09e8f-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="09e8f-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="09e8f-112">*lpconsoleskreenbufferinfoex* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="09e8f-112">*lpConsoleScreenBufferInfoEx* \[out\]</span></span>  
<span data-ttu-id="09e8f-113">Eine [\*\* \_ \_ \_ INFOEX-Struktur des Konsolenbildschirm Puffers\*\*](console-screen-buffer-infoex.md) , die die angeforderten Konsolenbildschirm Puffer Informationen empfängt.</span><span class="sxs-lookup"><span data-stu-id="09e8f-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that receives the requested console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="09e8f-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="09e8f-114">Return value</span></span>
------------

<span data-ttu-id="09e8f-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="09e8f-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="09e8f-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="09e8f-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="09e8f-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="09e8f-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="09e8f-118">Hinweise</span><span class="sxs-lookup"><span data-stu-id="09e8f-118">Remarks</span></span>
-------

<span data-ttu-id="09e8f-119">Das Rechteck, das im **srwindow** -Member der [\*\* \_ \_ \_ INFOEX-Struktur der Konsolenbildschirm Puffer\*\*](console-screen-buffer-infoex.md) zurückgegeben wurde, kann geändert und dann an die [**setconsolewindowinfo**](setconsolewindowinfo.md) -Funktion weitergegeben werden, um einen Bildlauf im Fenster des Konsolenbildschirm Puffers durchführen, um die Größe des Fensters oder beides zu ändern.</span><span class="sxs-lookup"><span data-stu-id="09e8f-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="09e8f-120">Alle in der INFOEX-Struktur des [\*\*Konsolen \_ Bildschirm \_ Puffers \_ \*\*](console-screen-buffer-infoex.md) zurückgegebenen Koordinaten befinden sich in Zeichen Zellen Koordinaten, wobei sich der Ursprung (0, 0) in der oberen linken Ecke des Konsolenbildschirm Puffers befindet.</span><span class="sxs-lookup"><span data-stu-id="09e8f-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

<a name="requirements"></a><span data-ttu-id="09e8f-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="09e8f-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="09e8f-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="09e8f-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="09e8f-123">Windows Vista [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="09e8f-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="09e8f-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="09e8f-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="09e8f-125">Windows Server 2008 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="09e8f-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="09e8f-126">Header</span><span class="sxs-lookup"><span data-stu-id="09e8f-126">Header</span></span></p></td>
<td><span data-ttu-id="09e8f-127">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="09e8f-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="09e8f-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="09e8f-128">Library</span></span></p></td>
<td><span data-ttu-id="09e8f-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="09e8f-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="09e8f-130">DLL</span><span class="sxs-lookup"><span data-stu-id="09e8f-130">DLL</span></span></p></td>
<td><span data-ttu-id="09e8f-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="09e8f-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="09e8f-132"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="09e8f-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="09e8f-133">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="09e8f-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="09e8f-134">**Konsolen \_ Bildschirm- \_ Puffer \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="09e8f-134">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="09e8f-135">**Setconsoleskreenbufferinfoex**</span><span class="sxs-lookup"><span data-stu-id="09e8f-135">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

 

 




