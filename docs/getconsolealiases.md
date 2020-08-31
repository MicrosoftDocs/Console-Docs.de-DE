---
title: Getconsolealiases-Funktion
description: Ruft alle definierten Konsolen Aliase für die angegebene ausführbare Datei ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleAliases
- wincon/GetConsoleAliases
- GetConsoleAliases
- consoleapi3/GetConsoleAliasesA
- wincon/GetConsoleAliasesA
- GetConsoleAliasesA
- consoleapi3/GetConsoleAliasesW
- wincon/GetConsoleAliasesW
- GetConsoleAliasesW
MS-HAID:
- base.getconsolealiases
- consoles.getconsolealiases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425
topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9e8e28323d5b696390d574a86561d7414f419bcc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059818"
---
# <a name="getconsolealiases-function"></a><span data-ttu-id="ed40c-104">Getconsolealiases-Funktion</span><span class="sxs-lookup"><span data-stu-id="ed40c-104">GetConsoleAliases function</span></span>


<span data-ttu-id="ed40c-105">Ruft alle definierten Konsolen Aliase für die angegebene ausführbare Datei ab.</span><span class="sxs-lookup"><span data-stu-id="ed40c-105">Retrieves all defined console aliases for the specified executable.</span></span>

<a name="syntax"></a><span data-ttu-id="ed40c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ed40c-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="ed40c-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="ed40c-107">Parameters</span></span>
----------

<span data-ttu-id="ed40c-108">*lpaliasbuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="ed40c-108">*lpAliasBuffer* \[out\]</span></span>  
<span data-ttu-id="ed40c-109">Ein Zeiger auf einen Puffer, der die Aliase empfängt.</span><span class="sxs-lookup"><span data-stu-id="ed40c-109">A pointer to a buffer that receives the aliases.</span></span>

<span data-ttu-id="ed40c-110">Das Format der Daten lautet wie folgt: *Quelle1* = *Target1* \\ 0*source2* = *TARGET2* \\ 0... *Sourcen* = *Targetn* \\ 0, wobei *N* die Anzahl der definierten Konsolen Aliase ist.</span><span class="sxs-lookup"><span data-stu-id="ed40c-110">The format of the data is as follows: *Source1*=*Target1*\\0*Source2*=*Target2*\\0... *SourceN*=*TargetN*\\0, where *N* is the number of console aliases defined.</span></span>

<span data-ttu-id="ed40c-111">*Aliasbufferlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ed40c-111">*AliasBufferLength* \[in\]</span></span>  
<span data-ttu-id="ed40c-112">Die Größe des Puffers, auf den *lpaliasbuffer*zeigt (in Bytes).</span><span class="sxs-lookup"><span data-stu-id="ed40c-112">The size of the buffer pointed to by *lpAliasBuffer*, in bytes.</span></span>

<span data-ttu-id="ed40c-113">*lpexename* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ed40c-113">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="ed40c-114">Die ausführbare Datei, deren Aliase abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ed40c-114">The executable file whose aliases are to be retrieved.</span></span>

<a name="return-value"></a><span data-ttu-id="ed40c-115">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ed40c-115">Return value</span></span>
------------

<span data-ttu-id="ed40c-116">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="ed40c-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ed40c-117">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="ed40c-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ed40c-118">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ed40c-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="ed40c-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ed40c-119">Remarks</span></span>
-------

<span data-ttu-id="ed40c-120">Verwenden Sie die [**getconsolealiaseslength**](getconsolealiaseslength.md) -Funktion, um die erforderliche Größe für den *lpexename* -Puffer zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="ed40c-120">To determine the required size for the *lpExeName* buffer, use the [**GetConsoleAliasesLength**](getconsolealiaseslength.md) function.</span></span>

<span data-ttu-id="ed40c-121">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="ed40c-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="ed40c-122">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="ed40c-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="ed40c-123">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ed40c-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ed40c-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="ed40c-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ed40c-125">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="ed40c-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ed40c-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="ed40c-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ed40c-127">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="ed40c-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ed40c-128">Header</span><span class="sxs-lookup"><span data-stu-id="ed40c-128">Header</span></span></p></td>
<td><span data-ttu-id="ed40c-129">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ed40c-129">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ed40c-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="ed40c-130">Library</span></span></p></td>
<td><span data-ttu-id="ed40c-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ed40c-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ed40c-132">DLL</span><span class="sxs-lookup"><span data-stu-id="ed40c-132">DLL</span></span></p></td>
<td><span data-ttu-id="ed40c-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ed40c-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ed40c-134">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="ed40c-134">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="ed40c-135"><strong>Getconsolealiasesw</strong> (Unicode) und <strong>getconsolealiasesa</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="ed40c-135"><strong>GetConsoleAliasesW</strong> (Unicode) and <strong>GetConsoleAliasesA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ed40c-136"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ed40c-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ed40c-137">**Addconsolealias**</span><span class="sxs-lookup"><span data-stu-id="ed40c-137">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="ed40c-138">Konsolen Aliase</span><span class="sxs-lookup"><span data-stu-id="ed40c-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="ed40c-139">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="ed40c-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ed40c-140">**Getconsolealias**</span><span class="sxs-lookup"><span data-stu-id="ed40c-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="ed40c-141">**Getconsolealiaseslength**</span><span class="sxs-lookup"><span data-stu-id="ed40c-141">**GetConsoleAliasesLength**</span></span>](getconsolealiaseslength.md)

[<span data-ttu-id="ed40c-142">**Getconsolealiasexes**</span><span class="sxs-lookup"><span data-stu-id="ed40c-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




