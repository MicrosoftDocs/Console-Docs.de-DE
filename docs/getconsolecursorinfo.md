---
title: Getconsolecursorinfo-Funktion
description: Ruft Informationen über die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleCursorInfo
- wincon/GetConsoleCursorInfo
- GetConsoleCursorInfo
MS-HAID:
- '\_win32\_getconsolecursorinfo'
- base.getconsolecursorinfo
- consoles.getconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6200577d-8d84-46bd-9330-d0b6cbbb3e52
topic_type:
- apiref
api_name:
- GetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d87fe0828451615e837c1c6c809a0160f15cf018
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059794"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="87c8e-104">Getconsolecursorinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="87c8e-104">GetConsoleCursorInfo function</span></span>


<span data-ttu-id="87c8e-105">Ruft Informationen über die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer ab.</span><span class="sxs-lookup"><span data-stu-id="87c8e-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="87c8e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="87c8e-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

<a name="parameters"></a><span data-ttu-id="87c8e-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="87c8e-107">Parameters</span></span>
----------

<span data-ttu-id="87c8e-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="87c8e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="87c8e-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="87c8e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="87c8e-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="87c8e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="87c8e-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="87c8e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="87c8e-112">*lpconsolecursorinfo* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="87c8e-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="87c8e-113">Ein Zeiger auf eine [**Konsolen \_ Cursor \_ Info**](console-cursor-info-str.md) -Struktur, die Informationen über den Cursor der Konsole empfängt.</span><span class="sxs-lookup"><span data-stu-id="87c8e-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

<a name="return-value"></a><span data-ttu-id="87c8e-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="87c8e-114">Return value</span></span>
------------

<span data-ttu-id="87c8e-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="87c8e-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="87c8e-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="87c8e-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="87c8e-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="87c8e-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="87c8e-118">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="87c8e-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="87c8e-119">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="87c8e-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="87c8e-120">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="87c8e-120">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="87c8e-121">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="87c8e-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="87c8e-122">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="87c8e-122">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="87c8e-123">Header</span><span class="sxs-lookup"><span data-stu-id="87c8e-123">Header</span></span></p></td>
<td><span data-ttu-id="87c8e-124">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="87c8e-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="87c8e-125">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="87c8e-125">Library</span></span></p></td>
<td><span data-ttu-id="87c8e-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="87c8e-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="87c8e-127">DLL</span><span class="sxs-lookup"><span data-stu-id="87c8e-127">DLL</span></span></p></td>
<td><span data-ttu-id="87c8e-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="87c8e-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="87c8e-129"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="87c8e-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="87c8e-130">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="87c8e-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="87c8e-131">Konsolenbildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="87c8e-131">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="87c8e-132">**Konsolen \_ Cursor \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="87c8e-132">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="87c8e-133">**Setconsolecursorinfo**</span><span class="sxs-lookup"><span data-stu-id="87c8e-133">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

 

 




