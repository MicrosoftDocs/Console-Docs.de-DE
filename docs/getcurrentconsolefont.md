---
title: Getcurrentconsolefont-Funktion
description: Ruft Informationen über die aktuelle Konsolen Schriftart für einen angegebenen Konsolenbildschirm Puffer ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetCurrentConsoleFont
- wincon/GetCurrentConsoleFont
- GetCurrentConsoleFont
MS-HAID:
- '\_win32\_getcurrentconsolefont'
- base.getcurrentconsolefont
- consoles.getcurrentconsolefont
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 347508ea-5c15-4568-b99f-1e7f5cdac8c1
topic_type:
- apiref
api_name:
- GetCurrentConsoleFont
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 4116dcf034c619544ed1689e3161f4eca4250a81
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059682"
---
# <a name="getcurrentconsolefont-function"></a><span data-ttu-id="01959-104">Getcurrentconsolefont-Funktion</span><span class="sxs-lookup"><span data-stu-id="01959-104">GetCurrentConsoleFont function</span></span>


<span data-ttu-id="01959-105">Ruft Informationen über die aktuelle Konsolen Schriftart ab.</span><span class="sxs-lookup"><span data-stu-id="01959-105">Retrieves information about the current console font.</span></span>

<a name="syntax"></a><span data-ttu-id="01959-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="01959-106">Syntax</span></span>
------

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

<a name="parameters"></a><span data-ttu-id="01959-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="01959-107">Parameters</span></span>
----------

<span data-ttu-id="01959-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="01959-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="01959-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="01959-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="01959-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="01959-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="01959-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="01959-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="01959-112">*bmaximumwindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="01959-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="01959-113">Wenn dieser Parameter **true**ist, werden für die maximale Fenstergröße Schriftart Informationen abgerufen.</span><span class="sxs-lookup"><span data-stu-id="01959-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="01959-114">Wenn dieser Parameter **false**ist, werden für die aktuelle Fenstergröße Schriftart Informationen abgerufen.</span><span class="sxs-lookup"><span data-stu-id="01959-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="01959-115">*lpconsolecurrentfont* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="01959-115">*lpConsoleCurrentFont* \[out\]</span></span>  
<span data-ttu-id="01959-116">Ein Zeiger auf eine [**Konsolen \_ Schriftart \_ Info**](console-font-info-str.md) -Struktur, die die angeforderten Schriftart Informationen empfängt.</span><span class="sxs-lookup"><span data-stu-id="01959-116">A pointer to a [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) structure that receives the requested font information.</span></span>

<a name="return-value"></a><span data-ttu-id="01959-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="01959-117">Return value</span></span>
------------

<span data-ttu-id="01959-118">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="01959-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="01959-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="01959-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="01959-120">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="01959-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="01959-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="01959-121">Remarks</span></span>
-------

<span data-ttu-id="01959-122">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="01959-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="01959-123">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="01959-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="01959-124">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="01959-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="01959-125">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="01959-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="01959-126">Windows XP [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="01959-126">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="01959-127">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="01959-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="01959-128">Windows Server 2003 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="01959-128">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="01959-129">Header</span><span class="sxs-lookup"><span data-stu-id="01959-129">Header</span></span></p></td>
<td><span data-ttu-id="01959-130">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="01959-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="01959-131">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="01959-131">Library</span></span></p></td>
<td><span data-ttu-id="01959-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="01959-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="01959-133">DLL</span><span class="sxs-lookup"><span data-stu-id="01959-133">DLL</span></span></p></td>
<td><span data-ttu-id="01959-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="01959-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="01959-135"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="01959-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="01959-136">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="01959-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="01959-137">Konsolenbildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="01959-137">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="01959-138">**Informationen zur Konsolen \_ Schriftart \_**</span><span class="sxs-lookup"><span data-stu-id="01959-138">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="01959-139">**Getconsolefontsize**</span><span class="sxs-lookup"><span data-stu-id="01959-139">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

 

 




