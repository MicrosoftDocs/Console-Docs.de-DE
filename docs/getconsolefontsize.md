---
title: Getconsolefontsize-Funktion
description: Ruft die Größe der Schriftart ab, die vom angegebenen Konsolenbildschirm Puffer verwendet wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- base.getconsolefontsize
- consoles.getconsolefontsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01
topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: b992ddaab35cb5af25479426dca83ef6381e73dd
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059795"
---
# <a name="getconsolefontsize-function"></a><span data-ttu-id="23f0a-104">Getconsolefontsize-Funktion</span><span class="sxs-lookup"><span data-stu-id="23f0a-104">GetConsoleFontSize function</span></span>


<span data-ttu-id="23f0a-105">Ruft die Größe der Schriftart ab, die vom angegebenen Konsolenbildschirm Puffer verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="23f0a-105">Retrieves the size of the font used by the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="23f0a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="23f0a-106">Syntax</span></span>
------

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

<a name="parameters"></a><span data-ttu-id="23f0a-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="23f0a-107">Parameters</span></span>
----------

<span data-ttu-id="23f0a-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="23f0a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="23f0a-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="23f0a-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="23f0a-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="23f0a-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="23f0a-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="23f0a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="23f0a-112">*nschriftart* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="23f0a-112">*nFont* \[in\]</span></span>  
<span data-ttu-id="23f0a-113">Der Index der Schriftart, deren Größe abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="23f0a-113">The index of the font whose size is to be retrieved.</span></span> <span data-ttu-id="23f0a-114">Dieser Index wird durch Aufrufen der [**getcurrentconsolefont**](getcurrentconsolefont.md) -Funktion abgerufen.</span><span class="sxs-lookup"><span data-stu-id="23f0a-114">This index is obtained by calling the [**GetCurrentConsoleFont**](getcurrentconsolefont.md) function.</span></span>

<a name="return-value"></a><span data-ttu-id="23f0a-115">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="23f0a-115">Return value</span></span>
------------

<span data-ttu-id="23f0a-116">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert eine [**coord**](coord-str.md) -Struktur, die die Breite und Höhe jedes Zeichens in der Schriftart in logischen Einheiten enthält.</span><span class="sxs-lookup"><span data-stu-id="23f0a-116">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="23f0a-117">Der **X** -Member enthält die Breite, während das **Y** -Element die Höhe enthält.</span><span class="sxs-lookup"><span data-stu-id="23f0a-117">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="23f0a-118">Wenn die Funktion fehlschlägt, sind die Breite und die Höhe 0 (null).</span><span class="sxs-lookup"><span data-stu-id="23f0a-118">If the function fails, the width and the height are zero.</span></span> <span data-ttu-id="23f0a-119">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="23f0a-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="23f0a-120">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="23f0a-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="23f0a-121">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="23f0a-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="23f0a-122">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="23f0a-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="23f0a-123">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="23f0a-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="23f0a-124">Windows XP [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="23f0a-124">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="23f0a-125">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="23f0a-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="23f0a-126">Windows Server 2003 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="23f0a-126">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="23f0a-127">Header</span><span class="sxs-lookup"><span data-stu-id="23f0a-127">Header</span></span></p></td>
<td><span data-ttu-id="23f0a-128">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="23f0a-128">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="23f0a-129">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="23f0a-129">Library</span></span></p></td>
<td><span data-ttu-id="23f0a-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="23f0a-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="23f0a-131">DLL</span><span class="sxs-lookup"><span data-stu-id="23f0a-131">DLL</span></span></p></td>
<td><span data-ttu-id="23f0a-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="23f0a-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="23f0a-133"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="23f0a-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="23f0a-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="23f0a-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="23f0a-135">Konsolenbildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="23f0a-135">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="23f0a-136">**Koord**</span><span class="sxs-lookup"><span data-stu-id="23f0a-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="23f0a-137">**Getcurrentconsolefont**</span><span class="sxs-lookup"><span data-stu-id="23f0a-137">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)

 

 




