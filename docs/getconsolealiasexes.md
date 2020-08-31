---
title: Getconsolealiasexes-Funktion
description: Ruft die Namen aller ausführbaren Dateien mit definierten Konsolen Aliasen ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleAliasExes
- wincon/GetConsoleAliasExes
- GetConsoleAliasExes
- consoleapi3/GetConsoleAliasExesA
- wincon/GetConsoleAliasExesA
- GetConsoleAliasExesA
- consoleapi3/GetConsoleAliasExesW
- wincon/GetConsoleAliasExesW
- GetConsoleAliasExesW
MS-HAID:
- base.getconsolealiasexes
- consoles.getconsolealiasexes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c229de09-cfa6-4829-9c9a-8ff63500eaf4
topic_type:
- apiref
api_name:
- GetConsoleAliasExes
- GetConsoleAliasExesA
- GetConsoleAliasExesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: e112112fc1510ab4c3f0a99ff9b208cc364e361a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059819"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="85ae8-104">Getconsolealiasexes-Funktion</span><span class="sxs-lookup"><span data-stu-id="85ae8-104">GetConsoleAliasExes function</span></span>


<span data-ttu-id="85ae8-105">Ruft die Namen aller ausführbaren Dateien mit definierten Konsolen Aliasen ab.</span><span class="sxs-lookup"><span data-stu-id="85ae8-105">Retrieves the names of all executable files with console aliases defined.</span></span>

<a name="syntax"></a><span data-ttu-id="85ae8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="85ae8-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

<a name="parameters"></a><span data-ttu-id="85ae8-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="85ae8-107">Parameters</span></span>
----------

<span data-ttu-id="85ae8-108">*lpexenamebuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="85ae8-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="85ae8-109">Ein Zeiger auf einen Puffer, der die Namen der ausführbaren Dateien empfängt.</span><span class="sxs-lookup"><span data-stu-id="85ae8-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="85ae8-110">*Exenamebufferlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="85ae8-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="85ae8-111">Die Größe des Puffers, auf den *lpexenamebuffer*zeigt (in Bytes).</span><span class="sxs-lookup"><span data-stu-id="85ae8-111">The size of the buffer pointed to by *lpExeNameBuffer*, in bytes.</span></span>

<a name="return-value"></a><span data-ttu-id="85ae8-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="85ae8-112">Return value</span></span>
------------

<span data-ttu-id="85ae8-113">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="85ae8-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="85ae8-114">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="85ae8-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="85ae8-115">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="85ae8-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="85ae8-116">Hinweise</span><span class="sxs-lookup"><span data-stu-id="85ae8-116">Remarks</span></span>
-------

<span data-ttu-id="85ae8-117">Verwenden Sie die [**getconsolealiasexeslength**](getconsolealiasexeslength.md) -Funktion, um die erforderliche Größe für den *lpexenamebuffer* -Puffer zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="85ae8-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="85ae8-118">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="85ae8-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="85ae8-119">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="85ae8-119">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="85ae8-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="85ae8-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="85ae8-121">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="85ae8-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="85ae8-122">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="85ae8-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="85ae8-123">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="85ae8-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="85ae8-124">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="85ae8-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="85ae8-125">Header</span><span class="sxs-lookup"><span data-stu-id="85ae8-125">Header</span></span></p></td>
<td><span data-ttu-id="85ae8-126">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="85ae8-126">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="85ae8-127">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="85ae8-127">Library</span></span></p></td>
<td><span data-ttu-id="85ae8-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="85ae8-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="85ae8-129">DLL</span><span class="sxs-lookup"><span data-stu-id="85ae8-129">DLL</span></span></p></td>
<td><span data-ttu-id="85ae8-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="85ae8-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="85ae8-131">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="85ae8-131">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="85ae8-132"><strong>Getconsolealiasexesw</strong> (Unicode) und <strong>getconsolealiasexesa</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="85ae8-132"><strong>GetConsoleAliasExesW</strong> (Unicode) and <strong>GetConsoleAliasExesA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="85ae8-133"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="85ae8-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="85ae8-134">**Addconsolealias**</span><span class="sxs-lookup"><span data-stu-id="85ae8-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="85ae8-135">Konsolen Aliase</span><span class="sxs-lookup"><span data-stu-id="85ae8-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="85ae8-136">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="85ae8-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="85ae8-137">**Getconsolealias**</span><span class="sxs-lookup"><span data-stu-id="85ae8-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="85ae8-138">**Getconsolealiasexeslength**</span><span class="sxs-lookup"><span data-stu-id="85ae8-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="85ae8-139">**Getconsolealiases**</span><span class="sxs-lookup"><span data-stu-id="85ae8-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)

 

 




