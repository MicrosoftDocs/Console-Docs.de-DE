---
title: Setcurrentconsolefontex-Funktion
description: Siehe Referenzinformationen zur setcurrentconsolefontex-Funktion, mit der erweiterte Informationen über die aktuelle Konsolen Schriftart festgelegt werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/SetCurrentConsoleFontEx
- wincon/SetCurrentConsoleFontEx
- SetCurrentConsoleFontEx
MS-HAID:
- base.setcurrentconsolefontex
- consoles.setcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: fbc31e2a-31df-4e9e-9f61-35a4ff812f8f
topic_type:
- apiref
api_name:
- SetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9d97383f40c38489ac3ea5e7c75386163b9d5d2d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060018"
---
# <a name="setcurrentconsolefontex-function"></a><span data-ttu-id="ac4da-104">Setcurrentconsolefontex-Funktion</span><span class="sxs-lookup"><span data-stu-id="ac4da-104">SetCurrentConsoleFontEx function</span></span>


<span data-ttu-id="ac4da-105">Legt erweiterte Informationen über die aktuelle Konsolen Schriftart fest.</span><span class="sxs-lookup"><span data-stu-id="ac4da-105">Sets extended information about the current console font.</span></span>

<a name="syntax"></a><span data-ttu-id="ac4da-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac4da-106">Syntax</span></span>
------

```C
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

<a name="parameters"></a><span data-ttu-id="ac4da-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="ac4da-107">Parameters</span></span>
----------

<span data-ttu-id="ac4da-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ac4da-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ac4da-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="ac4da-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="ac4da-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="ac4da-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="ac4da-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="ac4da-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ac4da-112">*bmaximumwindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ac4da-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="ac4da-113">Wenn dieser Parameter auf **true**festgelegt ist, werden für die maximale Fenstergröße Schriftart Informationen festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ac4da-113">If this parameter is **TRUE**, font information is set for the maximum window size.</span></span> <span data-ttu-id="ac4da-114">Wenn dieser Parameter auf **false**festgelegt ist, werden für die aktuelle Fenstergröße Schriftart Informationen festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ac4da-114">If this parameter is **FALSE**, font information is set for the current window size.</span></span>

<span data-ttu-id="ac4da-115">*lpconsolecurrentfontex* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ac4da-115">*lpConsoleCurrentFontEx* \[in\]</span></span>  
<span data-ttu-id="ac4da-116">Ein Zeiger auf eine [**Konsolen \_ Schriftart \_ INFOEX**](console-font-infoex.md) -Struktur, die die Schriftart Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="ac4da-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that contains the font information.</span></span>

<a name="return-value"></a><span data-ttu-id="ac4da-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ac4da-117">Return value</span></span>
------------

<span data-ttu-id="ac4da-118">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="ac4da-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ac4da-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="ac4da-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ac4da-120">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ac4da-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="ac4da-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ac4da-121">Remarks</span></span>
-------

<span data-ttu-id="ac4da-122">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="ac4da-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="ac4da-123">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="ac4da-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="ac4da-124">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ac4da-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ac4da-125">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="ac4da-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ac4da-126">Windows Vista [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="ac4da-126">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ac4da-127">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="ac4da-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ac4da-128">Windows Server 2008 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="ac4da-128">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ac4da-129">Header</span><span class="sxs-lookup"><span data-stu-id="ac4da-129">Header</span></span></p></td>
<td><span data-ttu-id="ac4da-130">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ac4da-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ac4da-131">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="ac4da-131">Library</span></span></p></td>
<td><span data-ttu-id="ac4da-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ac4da-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ac4da-133">DLL</span><span class="sxs-lookup"><span data-stu-id="ac4da-133">DLL</span></span></p></td>
<td><span data-ttu-id="ac4da-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ac4da-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ac4da-135"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ac4da-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ac4da-136">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="ac4da-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ac4da-137">**Konsolen \_ Schriftart \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="ac4da-137">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)

 

 




