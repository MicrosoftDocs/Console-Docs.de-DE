---
title: Setconsoleskreenbuffersize-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "setconsoleskreenbuffersize", die die Größe des angegebenen Konsolenbildschirm Puffers ändert.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0e2f3a3ea11f291e88837885c6fc3e555fd39e09
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060509"
---
# <a name="setconsolescreenbuffersize-function"></a><span data-ttu-id="e0a57-104">Setconsoleskreenbuffersize-Funktion</span><span class="sxs-lookup"><span data-stu-id="e0a57-104">SetConsoleScreenBufferSize function</span></span>


<span data-ttu-id="e0a57-105">Ändert die Größe des angegebenen Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="e0a57-105">Changes the size of the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="e0a57-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0a57-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

<a name="parameters"></a><span data-ttu-id="e0a57-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="e0a57-107">Parameters</span></span>
----------

<span data-ttu-id="e0a57-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e0a57-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="e0a57-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="e0a57-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="e0a57-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="e0a57-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="e0a57-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="e0a57-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="e0a57-112">*dwSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e0a57-112">*dwSize* \[in\]</span></span>  
<span data-ttu-id="e0a57-113">Eine [**Koord**](coord-str.md) -Struktur, die die neue Größe des Konsolenbildschirm Puffers in Zeichen Zeilen und-Spalten angibt.</span><span class="sxs-lookup"><span data-stu-id="e0a57-113">A [**COORD**](coord-str.md) structure that specifies the new size of the console screen buffer, in character rows and columns.</span></span> <span data-ttu-id="e0a57-114">Die angegebene Breite und Höhe darf nicht kleiner sein als die Breite und Höhe des Fensters des Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="e0a57-114">The specified width and height cannot be less than the width and height of the console screen buffer's window.</span></span> <span data-ttu-id="e0a57-115">Die angegebenen Dimensionen dürfen auch nicht kleiner als die vom System zulässige Mindestgröße sein.</span><span class="sxs-lookup"><span data-stu-id="e0a57-115">The specified dimensions also cannot be less than the minimum size allowed by the system.</span></span> <span data-ttu-id="e0a57-116">Dieses Minimum hängt von der aktuellen Schriftgröße für die Konsole (vom Benutzer ausgewählt) und den von der [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) -Funktion zurückgegebenen **SM- \_ cxMin** -und **SM- \_ Cymin** -Werten ab.</span><span class="sxs-lookup"><span data-stu-id="e0a57-116">This minimum depends on the current font size for the console (selected by the user) and the **SM\_CXMIN** and **SM\_CYMIN** values returned by the [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) function.</span></span>

<a name="return-value"></a><span data-ttu-id="e0a57-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e0a57-117">Return value</span></span>
------------

<span data-ttu-id="e0a57-118">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="e0a57-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e0a57-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="e0a57-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e0a57-120">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e0a57-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="e0a57-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e0a57-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e0a57-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="e0a57-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e0a57-123">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="e0a57-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e0a57-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="e0a57-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e0a57-125">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="e0a57-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e0a57-126">Header</span><span class="sxs-lookup"><span data-stu-id="e0a57-126">Header</span></span></p></td>
<td><span data-ttu-id="e0a57-127">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e0a57-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e0a57-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e0a57-128">Library</span></span></p></td>
<td><span data-ttu-id="e0a57-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e0a57-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e0a57-130">DLL</span><span class="sxs-lookup"><span data-stu-id="e0a57-130">DLL</span></span></p></td>
<td><span data-ttu-id="e0a57-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e0a57-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e0a57-132"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e0a57-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e0a57-133">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="e0a57-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e0a57-134">Konsolen Eingabepuffer</span><span class="sxs-lookup"><span data-stu-id="e0a57-134">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="e0a57-135">**Koord**</span><span class="sxs-lookup"><span data-stu-id="e0a57-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="e0a57-136">**Getconsoleskreenbufferinfo**</span><span class="sxs-lookup"><span data-stu-id="e0a57-136">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="e0a57-137">**Setconsolewindowinfo**</span><span class="sxs-lookup"><span data-stu-id="e0a57-137">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

 

 




