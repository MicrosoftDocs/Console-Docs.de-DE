---
title: Setconsoleskreenbufferinfoex-Funktion
description: Legt erweiterte Informationen zum angegebenen Konsolenbildschirm Puffer auf den angegebenen Puffer fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 403ce6c3625aacdcc8b2eb498e7df1715d1e6b94
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060496"
---
# <a name="setconsolescreenbufferinfoex-function"></a><span data-ttu-id="d5d21-104">Setconsoleskreenbufferinfoex-Funktion</span><span class="sxs-lookup"><span data-stu-id="d5d21-104">SetConsoleScreenBufferInfoEx function</span></span>


<span data-ttu-id="d5d21-105">Legt erweiterte Informationen zum angegebenen Konsolenbildschirm Puffer fest.</span><span class="sxs-lookup"><span data-stu-id="d5d21-105">Sets extended information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="d5d21-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d5d21-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

<a name="parameters"></a><span data-ttu-id="d5d21-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="d5d21-107">Parameters</span></span>
----------

<span data-ttu-id="d5d21-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d5d21-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d5d21-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="d5d21-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d5d21-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="d5d21-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="d5d21-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d5d21-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d5d21-112">*lpconsoleskreenbufferinfoex* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d5d21-112">*lpConsoleScreenBufferInfoEx* \[in\]</span></span>  
<span data-ttu-id="d5d21-113">Eine [\*\* \_ \_ \_ INFOEX-Struktur des Konsolenbildschirm Puffers\*\*](console-screen-buffer-infoex.md) , die die Bildschirm Puffer Informationen der Konsole enthält.</span><span class="sxs-lookup"><span data-stu-id="d5d21-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that contains the console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="d5d21-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="d5d21-114">Return value</span></span>
------------

<span data-ttu-id="d5d21-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="d5d21-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d5d21-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="d5d21-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d5d21-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="d5d21-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="d5d21-118">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="d5d21-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="d5d21-119">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="d5d21-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="d5d21-120">Windows Vista [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="d5d21-120">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d5d21-121">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="d5d21-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="d5d21-122">Windows Server 2008 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="d5d21-122">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d5d21-123">Header</span><span class="sxs-lookup"><span data-stu-id="d5d21-123">Header</span></span></p></td>
<td><span data-ttu-id="d5d21-124">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d5d21-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d5d21-125">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="d5d21-125">Library</span></span></p></td>
<td><span data-ttu-id="d5d21-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d5d21-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d5d21-127">DLL</span><span class="sxs-lookup"><span data-stu-id="d5d21-127">DLL</span></span></p></td>
<td><span data-ttu-id="d5d21-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d5d21-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="d5d21-129"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d5d21-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="d5d21-130">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="d5d21-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d5d21-131">**Konsolen \_ Bildschirm- \_ Puffer \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="d5d21-131">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="d5d21-132">**Getconsoleskreenbufferinfoex**</span><span class="sxs-lookup"><span data-stu-id="d5d21-132">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

 

 




