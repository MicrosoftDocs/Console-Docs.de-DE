---
title: Getconsolealiases-Funktion
description: Ruft alle definierten Konsolen Aliase für die angegebene ausführbare Datei ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: a84579ce7bf27787e986ded2e1f21520f8d442b9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038118"
---
# <a name="getconsolealiases-function"></a><span data-ttu-id="94526-104">Getconsolealiases-Funktion</span><span class="sxs-lookup"><span data-stu-id="94526-104">GetConsoleAliases function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="94526-105">Ruft alle definierten Konsolen Aliase für die angegebene ausführbare Datei ab.</span><span class="sxs-lookup"><span data-stu-id="94526-105">Retrieves all defined console aliases for the specified executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="94526-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="94526-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="94526-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="94526-107">Parameters</span></span>

<span data-ttu-id="94526-108">*lpaliasbuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="94526-108">*lpAliasBuffer* \[out\]</span></span>  
<span data-ttu-id="94526-109">Ein Zeiger auf einen Puffer, der die Aliase empfängt.</span><span class="sxs-lookup"><span data-stu-id="94526-109">A pointer to a buffer that receives the aliases.</span></span>

<span data-ttu-id="94526-110">Das Format der Daten lautet wie folgt: *Quelle1* = *Target1* \\ 0 *source2* = *TARGET2* \\ 0... *Sourcen* = *Targetn* \\ 0, wobei *N* die Anzahl der definierten Konsolen Aliase ist.</span><span class="sxs-lookup"><span data-stu-id="94526-110">The format of the data is as follows: *Source1*=*Target1*\\0 *Source2*=*Target2*\\0... *SourceN*=*TargetN*\\0, where *N* is the number of console aliases defined.</span></span>

<span data-ttu-id="94526-111">*Aliasbufferlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="94526-111">*AliasBufferLength* \[in\]</span></span>  
<span data-ttu-id="94526-112">Die Größe des Puffers, auf den *lpaliasbuffer* zeigt (in Bytes).</span><span class="sxs-lookup"><span data-stu-id="94526-112">The size of the buffer pointed to by *lpAliasBuffer* , in bytes.</span></span>

<span data-ttu-id="94526-113">*lpexename* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="94526-113">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="94526-114">Die ausführbare Datei, deren Aliase abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="94526-114">The executable file whose aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="94526-115">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="94526-115">Return value</span></span>

<span data-ttu-id="94526-116">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="94526-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="94526-117">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="94526-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="94526-118">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="94526-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="94526-119">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="94526-119">Remarks</span></span>

<span data-ttu-id="94526-120">Verwenden Sie die [**getconsolealiaseslength**](getconsolealiaseslength.md) -Funktion, um die erforderliche Größe für den *lpexename* -Puffer zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="94526-120">To determine the required size for the *lpExeName* buffer, use the [**GetConsoleAliasesLength**](getconsolealiaseslength.md) function.</span></span>

<span data-ttu-id="94526-121">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="94526-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="94526-122">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="94526-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="94526-123">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="94526-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="94526-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="94526-124">Minimum supported client</span></span> | <span data-ttu-id="94526-125">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="94526-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="94526-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="94526-126">Minimum supported server</span></span> | <span data-ttu-id="94526-127">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="94526-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="94526-128">Header</span><span class="sxs-lookup"><span data-stu-id="94526-128">Header</span></span> | <span data-ttu-id="94526-129">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="94526-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="94526-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="94526-130">Library</span></span> | <span data-ttu-id="94526-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="94526-131">Kernel32.lib</span></span> |
| <span data-ttu-id="94526-132">DLL</span><span class="sxs-lookup"><span data-stu-id="94526-132">DLL</span></span> | <span data-ttu-id="94526-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="94526-133">Kernel32.dll</span></span> |
| <span data-ttu-id="94526-134">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="94526-134">Unicode and ANSI names</span></span> | <span data-ttu-id="94526-135">**Getconsolealiasesw** (Unicode) und **getconsolealiasesa** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="94526-135">**GetConsoleAliasesW** (Unicode) and **GetConsoleAliasesA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="94526-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="94526-136">See also</span></span>

[<span data-ttu-id="94526-137">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="94526-137">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="94526-138">Konsolenaliase</span><span class="sxs-lookup"><span data-stu-id="94526-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="94526-139">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="94526-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="94526-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="94526-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="94526-141">**Getconsolealiaseslength**</span><span class="sxs-lookup"><span data-stu-id="94526-141">**GetConsoleAliasesLength**</span></span>](getconsolealiaseslength.md)

[<span data-ttu-id="94526-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="94526-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
