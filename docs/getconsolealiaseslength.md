---
title: Getconsolealiaseslength-Funktion
description: Ruft die erforderliche Größe für den Puffer ab, der von der getconsolealiases-Funktion verwendet wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleAliasesLength
- wincon/GetConsoleAliasesLength
- GetConsoleAliasesLength
- consoleapi3/GetConsoleAliasesLengthA
- wincon/GetConsoleAliasesLengthA
- GetConsoleAliasesLengthA
- consoleapi3/GetConsoleAliasesLengthW
- wincon/GetConsoleAliasesLengthW
- GetConsoleAliasesLengthW
MS-HAID:
- base.getconsolealiaseslength
- consoles.getconsolealiaseslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 29e49eba-0864-4ed7-af82-1ba639261c40
topic_type:
- apiref
api_name:
- GetConsoleAliasesLength
- GetConsoleAliasesLengthA
- GetConsoleAliasesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 23d820574aab837c89f2598e9934536b91715426
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059810"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="69cc6-104">Getconsolealiaseslength-Funktion</span><span class="sxs-lookup"><span data-stu-id="69cc6-104">GetConsoleAliasesLength function</span></span>


<span data-ttu-id="69cc6-105">Ruft die erforderliche Größe für den Puffer ab, der von der [**getconsolealiases**](getconsolealiases.md) -Funktion verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="69cc6-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="69cc6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="69cc6-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="69cc6-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="69cc6-107">Parameters</span></span>
----------

<span data-ttu-id="69cc6-108">*lpexename* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="69cc6-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="69cc6-109">Der Name der ausführbaren Datei, deren Konsolen Aliase abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="69cc6-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

<a name="return-value"></a><span data-ttu-id="69cc6-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="69cc6-110">Return value</span></span>
------------

<span data-ttu-id="69cc6-111">Die Größe des Puffers, der zum Speichern aller für diese ausführbaren Datei definierten Konsolen Aliase in Bytes erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="69cc6-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

<a name="remarks"></a><span data-ttu-id="69cc6-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="69cc6-112">Remarks</span></span>
-------

<span data-ttu-id="69cc6-113">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="69cc6-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="69cc6-114">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="69cc6-114">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="69cc6-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="69cc6-115">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="69cc6-116">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="69cc6-116">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="69cc6-117">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="69cc6-117">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69cc6-118">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="69cc6-118">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="69cc6-119">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="69cc6-119">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69cc6-120">Header</span><span class="sxs-lookup"><span data-stu-id="69cc6-120">Header</span></span></p></td>
<td><span data-ttu-id="69cc6-121">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="69cc6-121">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69cc6-122">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="69cc6-122">Library</span></span></p></td>
<td><span data-ttu-id="69cc6-123">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="69cc6-123">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69cc6-124">DLL</span><span class="sxs-lookup"><span data-stu-id="69cc6-124">DLL</span></span></p></td>
<td><span data-ttu-id="69cc6-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="69cc6-125">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69cc6-126">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="69cc6-126">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="69cc6-127"><strong>Getconsolealiaseslengthw</strong> (Unicode) und <strong>getconsolealiaseslengtha</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="69cc6-127"><strong>GetConsoleAliasesLengthW</strong> (Unicode) and <strong>GetConsoleAliasesLengthA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="69cc6-128"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="69cc6-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="69cc6-129">**Addconsolealias**</span><span class="sxs-lookup"><span data-stu-id="69cc6-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="69cc6-130">Konsolen Aliase</span><span class="sxs-lookup"><span data-stu-id="69cc6-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="69cc6-131">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="69cc6-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="69cc6-132">**Getconsolealias**</span><span class="sxs-lookup"><span data-stu-id="69cc6-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="69cc6-133">**Getconsolealiases**</span><span class="sxs-lookup"><span data-stu-id="69cc6-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="69cc6-134">**Getconsolealiasexes**</span><span class="sxs-lookup"><span data-stu-id="69cc6-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




