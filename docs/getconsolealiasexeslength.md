---
title: Getconsolealiasexeslength-Funktion
description: Ruft die erforderliche Größe für den Puffer ab, der von der getconsolealiasexes-Funktion verwendet wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapie/GetConsoleAliasExesLength
- wincon/GetConsoleAliasExesLength
- GetConsoleAliasExesLength
- consoleapie/GetConsoleAliasExesLengthA
- wincon/GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthA
- consoleapie/GetConsoleAliasExesLengthW
- wincon/GetConsoleAliasExesLengthW
- GetConsoleAliasExesLengthW
MS-HAID:
- base.getconsolealiasexeslength
- consoles.getconsolealiasexeslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4f23bbb1-3e43-47a9-b91a-e91529b07fb5
topic_type:
- apiref
api_name:
- GetConsoleAliasExesLength
- GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0f4459254e9382a0c784ceb2c214af056087ab1b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059802"
---
# <a name="getconsolealiasexeslength-function"></a><span data-ttu-id="27fb6-104">Getconsolealiasexeslength-Funktion</span><span class="sxs-lookup"><span data-stu-id="27fb6-104">GetConsoleAliasExesLength function</span></span>


<span data-ttu-id="27fb6-105">Ruft die erforderliche Größe für den Puffer ab, der von der [**getconsolealiasexes**](getconsolealiasexes.md) -Funktion verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="27fb6-105">Retrieves the required size for the buffer used by the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="27fb6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="27fb6-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

<a name="parameters"></a><span data-ttu-id="27fb6-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="27fb6-107">Parameters</span></span>
----------

<span data-ttu-id="27fb6-108">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="27fb6-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="27fb6-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="27fb6-109">Return value</span></span>
------------

<span data-ttu-id="27fb6-110">Die Größe des Puffers, der zum Speichern der Namen aller ausführbaren Dateien erforderlich ist, für die Konsolen Aliase definiert sind (in Bytes).</span><span class="sxs-lookup"><span data-stu-id="27fb6-110">The size of the buffer required to store the names of all executable files that have console aliases defined, in bytes.</span></span>

<a name="remarks"></a><span data-ttu-id="27fb6-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="27fb6-111">Remarks</span></span>
-------

<span data-ttu-id="27fb6-112">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="27fb6-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="27fb6-113">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="27fb6-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="27fb6-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="27fb6-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="27fb6-115">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="27fb6-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="27fb6-116">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="27fb6-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="27fb6-117">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="27fb6-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="27fb6-118">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="27fb6-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="27fb6-119">Header</span><span class="sxs-lookup"><span data-stu-id="27fb6-119">Header</span></span></p></td>
<td><span data-ttu-id="27fb6-120">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="27fb6-120">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="27fb6-121">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="27fb6-121">Library</span></span></p></td>
<td><span data-ttu-id="27fb6-122">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="27fb6-122">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="27fb6-123">DLL</span><span class="sxs-lookup"><span data-stu-id="27fb6-123">DLL</span></span></p></td>
<td><span data-ttu-id="27fb6-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="27fb6-124">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="27fb6-125">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="27fb6-125">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="27fb6-126"><strong>Getconsolealiasexeslengthw</strong> (Unicode) und <strong>getconsolealiasexeslengtha</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="27fb6-126"><strong>GetConsoleAliasExesLengthW</strong> (Unicode) and <strong>GetConsoleAliasExesLengthA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="27fb6-127"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="27fb6-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="27fb6-128">**Addconsolealias**</span><span class="sxs-lookup"><span data-stu-id="27fb6-128">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="27fb6-129">Konsolen Aliase</span><span class="sxs-lookup"><span data-stu-id="27fb6-129">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="27fb6-130">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="27fb6-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="27fb6-131">**Getconsolealias**</span><span class="sxs-lookup"><span data-stu-id="27fb6-131">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="27fb6-132">**Getconsolealiases**</span><span class="sxs-lookup"><span data-stu-id="27fb6-132">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="27fb6-133">**Getconsolealiasexes**</span><span class="sxs-lookup"><span data-stu-id="27fb6-133">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




