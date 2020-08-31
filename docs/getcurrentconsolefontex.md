---
title: Getcurrentconsolefontex-Funktion
description: Siehe Referenzinformationen zur getcurrentconsolefontex-Funktion, die erweiterte Informationen zur aktuell verwendeten Konsolen Schriftart abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetCurrentConsoleFontEx
- wincon/GetCurrentConsoleFontEx
- GetCurrentConsoleFontEx
MS-HAID:
- base.getcurrentconsolefontex
- consoles.getcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 97d8e730-4110-4be5-b099-0acc1b6f8eb5
topic_type:
- apiref
api_name:
- GetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0ea8d5ad928003d4039a6c8611073ab3c38ce34f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059691"
---
# <a name="getcurrentconsolefontex-function"></a><span data-ttu-id="2c85e-104">Getcurrentconsolefontex-Funktion</span><span class="sxs-lookup"><span data-stu-id="2c85e-104">GetCurrentConsoleFontEx function</span></span>


<span data-ttu-id="2c85e-105">Ruft erweiterte Informationen über die aktuelle Konsolen Schriftart ab.</span><span class="sxs-lookup"><span data-stu-id="2c85e-105">Retrieves extended information about the current console font.</span></span>

<a name="syntax"></a><span data-ttu-id="2c85e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2c85e-106">Syntax</span></span>
------

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

<a name="parameters"></a><span data-ttu-id="2c85e-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="2c85e-107">Parameters</span></span>
----------

<span data-ttu-id="2c85e-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2c85e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="2c85e-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="2c85e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="2c85e-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="2c85e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="2c85e-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="2c85e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="2c85e-112">*bmaximumwindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2c85e-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="2c85e-113">Wenn dieser Parameter **true**ist, werden für die maximale Fenstergröße Schriftart Informationen abgerufen.</span><span class="sxs-lookup"><span data-stu-id="2c85e-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="2c85e-114">Wenn dieser Parameter **false**ist, werden für die aktuelle Fenstergröße Schriftart Informationen abgerufen.</span><span class="sxs-lookup"><span data-stu-id="2c85e-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="2c85e-115">*lpconsolecurrentfontex* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="2c85e-115">*lpConsoleCurrentFontEx* \[out\]</span></span>  
<span data-ttu-id="2c85e-116">Ein Zeiger auf eine [**Konsolen \_ Schriftart \_ INFOEX**](console-font-infoex.md) -Struktur, die die angeforderten Schriftart Informationen empfängt.</span><span class="sxs-lookup"><span data-stu-id="2c85e-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that receives the requested font information.</span></span>

<a name="return-value"></a><span data-ttu-id="2c85e-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="2c85e-117">Return value</span></span>
------------

<span data-ttu-id="2c85e-118">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="2c85e-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2c85e-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="2c85e-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2c85e-120">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2c85e-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="2c85e-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="2c85e-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2c85e-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="2c85e-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2c85e-123">Windows Vista [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="2c85e-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2c85e-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="2c85e-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2c85e-125">Windows Server 2008 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="2c85e-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2c85e-126">Header</span><span class="sxs-lookup"><span data-stu-id="2c85e-126">Header</span></span></p></td>
<td><span data-ttu-id="2c85e-127">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2c85e-127">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2c85e-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="2c85e-128">Library</span></span></p></td>
<td><span data-ttu-id="2c85e-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2c85e-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2c85e-130">DLL</span><span class="sxs-lookup"><span data-stu-id="2c85e-130">DLL</span></span></p></td>
<td><span data-ttu-id="2c85e-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2c85e-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2c85e-132"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2c85e-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2c85e-133">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="2c85e-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2c85e-134">**Konsolen \_ Schriftart \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="2c85e-134">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)

 

 




