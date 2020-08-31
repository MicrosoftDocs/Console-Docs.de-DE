---
title: Getconsolealias-Funktion
description: Ruft den Text für den angegebenen konsolenalias und den Namen der ausführbaren Datei ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleAlias
- wincon/GetConsoleAlias
- GetConsoleAlias
- consoleapi3/GetConsoleAliasA
- wincon/GetConsoleAliasA
- GetConsoleAliasA
- consoleapi3/GetConsoleAliasW
- wincon/GetConsoleAliasW
- GetConsoleAliasW
MS-HAID:
- base.getconsolealias
- consoles.getconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e8514f24-8121-4fad-94bb-c9eedf7a700d
topic_type:
- apiref
api_name:
- GetConsoleAlias
- GetConsoleAliasA
- GetConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 3a7797db4b559e66c1ec30f72e148ff00e79e7aa
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059826"
---
# <a name="getconsolealias-function"></a><span data-ttu-id="1e5d8-104">Getconsolealias-Funktion</span><span class="sxs-lookup"><span data-stu-id="1e5d8-104">GetConsoleAlias function</span></span>


<span data-ttu-id="1e5d8-105">Ruft den Text für den angegebenen konsolenalias und die ausführbare Datei ab.</span><span class="sxs-lookup"><span data-stu-id="1e5d8-105">Retrieves the text for the specified console alias and executable.</span></span>

<a name="syntax"></a><span data-ttu-id="1e5d8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1e5d8-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="1e5d8-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="1e5d8-107">Parameters</span></span>
----------

<span data-ttu-id="1e5d8-108">*lpSource* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1e5d8-108">*lpSource* \[in\]</span></span>  
<span data-ttu-id="1e5d8-109">Der konsolenalias, dessen Text abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="1e5d8-109">The console alias whose text is to be retrieved.</span></span>

<span data-ttu-id="1e5d8-110">*lptargetbuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="1e5d8-110">*lpTargetBuffer* \[out\]</span></span>  
<span data-ttu-id="1e5d8-111">Ein Zeiger auf einen Puffer, der den dem Konsolen Alias zugeordneten Text empfängt.</span><span class="sxs-lookup"><span data-stu-id="1e5d8-111">A pointer to a buffer that receives the text associated with the console alias.</span></span>

<span data-ttu-id="1e5d8-112">*Targetbufferlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1e5d8-112">*TargetBufferLength* \[in\]</span></span>  
<span data-ttu-id="1e5d8-113">Die Größe des Puffers, auf den von *lptargetbuffer*verwiesen wird (in Bytes).</span><span class="sxs-lookup"><span data-stu-id="1e5d8-113">The size of the buffer pointed to by *lpTargetBuffer*, in bytes.</span></span>

<span data-ttu-id="1e5d8-114">*lpexename* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1e5d8-114">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="1e5d8-115">Der Name der ausführbaren Datei.</span><span class="sxs-lookup"><span data-stu-id="1e5d8-115">The name of the executable file.</span></span>

<a name="return-value"></a><span data-ttu-id="1e5d8-116">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1e5d8-116">Return value</span></span>
------------

<span data-ttu-id="1e5d8-117">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="1e5d8-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1e5d8-118">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="1e5d8-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1e5d8-119">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1e5d8-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="1e5d8-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1e5d8-120">Remarks</span></span>
-------

<span data-ttu-id="1e5d8-121">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="1e5d8-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="1e5d8-122">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="1e5d8-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="1e5d8-123">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1e5d8-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="1e5d8-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="1e5d8-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="1e5d8-125">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="1e5d8-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1e5d8-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="1e5d8-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="1e5d8-127">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="1e5d8-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1e5d8-128">Header</span><span class="sxs-lookup"><span data-stu-id="1e5d8-128">Header</span></span></p></td>
<td><span data-ttu-id="1e5d8-129">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1e5d8-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1e5d8-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="1e5d8-130">Library</span></span></p></td>
<td><span data-ttu-id="1e5d8-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1e5d8-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1e5d8-132">DLL</span><span class="sxs-lookup"><span data-stu-id="1e5d8-132">DLL</span></span></p></td>
<td><span data-ttu-id="1e5d8-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1e5d8-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1e5d8-134">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="1e5d8-134">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="1e5d8-135"><strong>Getconsolealiasw</strong> (Unicode) und <strong>getconsolealiasa</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="1e5d8-135"><strong>GetConsoleAliasW</strong> (Unicode) and <strong>GetConsoleAliasA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="1e5d8-136"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1e5d8-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="1e5d8-137">Konsolen Aliase</span><span class="sxs-lookup"><span data-stu-id="1e5d8-137">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="1e5d8-138">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="1e5d8-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1e5d8-139">**Addconsolealias**</span><span class="sxs-lookup"><span data-stu-id="1e5d8-139">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="1e5d8-140">**Getconsolealiases**</span><span class="sxs-lookup"><span data-stu-id="1e5d8-140">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="1e5d8-141">**Getconsolealiasexes**</span><span class="sxs-lookup"><span data-stu-id="1e5d8-141">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




