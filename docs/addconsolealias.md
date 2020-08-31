---
title: Addconsolealias-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur addconsolealias-Funktion, die einen Konsolen Alias für die angegebene ausführbare Datei definiert.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 108a77b3178e7695e7477ea198df616fa8bcb199
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060242"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="a2638-104">Addconsolealias-Funktion</span><span class="sxs-lookup"><span data-stu-id="a2638-104">AddConsoleAlias function</span></span>


<span data-ttu-id="a2638-105">Definiert einen konsolenalias für die angegebene ausführbare Datei.</span><span class="sxs-lookup"><span data-stu-id="a2638-105">Defines a console alias for the specified executable.</span></span>

<a name="syntax"></a><span data-ttu-id="a2638-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a2638-106">Syntax</span></span>
------

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

<a name="parameters"></a><span data-ttu-id="a2638-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="a2638-107">Parameters</span></span>
----------

<span data-ttu-id="a2638-108">*Quelle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="a2638-108">*Source* \[in\]</span></span>  
<span data-ttu-id="a2638-109">Der konsolenalias, der dem durch *target*angegebenen Text zugeordnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a2638-109">The console alias to be mapped to the text specified by *Target*.</span></span>

<span data-ttu-id="a2638-110">*Ziel* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="a2638-110">*Target* \[in\]</span></span>  
<span data-ttu-id="a2638-111">Der Text, der als *Quelle*ersetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a2638-111">The text to be substituted for *Source*.</span></span> <span data-ttu-id="a2638-112">Wenn dieser Parameter **null**ist, wird der Konsolen Alias entfernt.</span><span class="sxs-lookup"><span data-stu-id="a2638-112">If this parameter is **NULL**, then the console alias is removed.</span></span>

<span data-ttu-id="a2638-113">*EXEName* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="a2638-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="a2638-114">Der Name der ausführbaren Datei, für die der konsolenalias definiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="a2638-114">The name of the executable file for which the console alias is to be defined.</span></span>

<a name="return-value"></a><span data-ttu-id="a2638-115">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="a2638-115">Return value</span></span>
------------

<span data-ttu-id="a2638-116">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert " **true**".</span><span class="sxs-lookup"><span data-stu-id="a2638-116">If the function succeeds, the return value is **TRUE**.</span></span>

<span data-ttu-id="a2638-117">Wenn die Funktion fehlschlägt, ist der Rückgabewert **false**.</span><span class="sxs-lookup"><span data-stu-id="a2638-117">If the function fails, the return value is **FALSE**.</span></span> <span data-ttu-id="a2638-118">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="a2638-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="a2638-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a2638-119">Remarks</span></span>
-------

<span data-ttu-id="a2638-120">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="a2638-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="a2638-121">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="a2638-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="examples"></a><span data-ttu-id="a2638-122">Beispiele</span><span class="sxs-lookup"><span data-stu-id="a2638-122">Examples</span></span>
--------

<span data-ttu-id="a2638-123">Ein Beispiel finden Sie unter [Konsolen Aliase](console-aliases.md).</span><span class="sxs-lookup"><span data-stu-id="a2638-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

<a name="requirements"></a><span data-ttu-id="a2638-124">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="a2638-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="a2638-125">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="a2638-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="a2638-126">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="a2638-126">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a2638-127">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="a2638-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="a2638-128">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="a2638-128">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a2638-129">Header</span><span class="sxs-lookup"><span data-stu-id="a2638-129">Header</span></span></p></td>
<td><span data-ttu-id="a2638-130">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a2638-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a2638-131">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="a2638-131">Library</span></span></p></td>
<td><span data-ttu-id="a2638-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="a2638-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a2638-133">DLL</span><span class="sxs-lookup"><span data-stu-id="a2638-133">DLL</span></span></p></td>
<td><span data-ttu-id="a2638-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="a2638-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a2638-135">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="a2638-135">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="a2638-136"><strong>Addconsolealiasw</strong> (Unicode) und <strong>addconsolealiasa</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="a2638-136"><strong>AddConsoleAliasW</strong> (Unicode) and <strong>AddConsoleAliasA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="a2638-137"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a2638-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="a2638-138">Konsolen Aliase</span><span class="sxs-lookup"><span data-stu-id="a2638-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="a2638-139">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="a2638-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="a2638-140">**Getconsolealias**</span><span class="sxs-lookup"><span data-stu-id="a2638-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="a2638-141">**Getconsolealiases**</span><span class="sxs-lookup"><span data-stu-id="a2638-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="a2638-142">**Getconsolealiasexes**</span><span class="sxs-lookup"><span data-stu-id="a2638-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




