---
title: Getconsolealiaseslength-Funktion
description: Ruft die erforderliche Größe für den Puffer ab, der von der getconsolealiases-Funktion verwendet wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 395acba39600fe1a98a80ed06ea23646b0b9f174
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038958"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="6d3e1-104">Getconsolealiaseslength-Funktion</span><span class="sxs-lookup"><span data-stu-id="6d3e1-104">GetConsoleAliasesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="6d3e1-105">Ruft die erforderliche Größe für den Puffer ab, der von der [**getconsolealiases**](getconsolealiases.md) -Funktion verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6d3e1-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="6d3e1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d3e1-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="6d3e1-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="6d3e1-107">Parameters</span></span>

<span data-ttu-id="6d3e1-108">*lpexename* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6d3e1-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="6d3e1-109">Der Name der ausführbaren Datei, deren Konsolen Aliase abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="6d3e1-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="6d3e1-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="6d3e1-110">Return value</span></span>

<span data-ttu-id="6d3e1-111">Die Größe des Puffers, der zum Speichern aller für diese ausführbaren Datei definierten Konsolen Aliase in Bytes erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="6d3e1-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="6d3e1-112">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="6d3e1-112">Remarks</span></span>

<span data-ttu-id="6d3e1-113">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="6d3e1-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="6d3e1-114">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="6d3e1-114">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="6d3e1-115">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="6d3e1-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6d3e1-116">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="6d3e1-116">Minimum supported client</span></span> | <span data-ttu-id="6d3e1-117">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6d3e1-117">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6d3e1-118">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="6d3e1-118">Minimum supported server</span></span> | <span data-ttu-id="6d3e1-119">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6d3e1-119">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6d3e1-120">Header</span><span class="sxs-lookup"><span data-stu-id="6d3e1-120">Header</span></span> | <span data-ttu-id="6d3e1-121">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6d3e1-121">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="6d3e1-122">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="6d3e1-122">Library</span></span> | <span data-ttu-id="6d3e1-123">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="6d3e1-123">Kernel32.lib</span></span> |
| <span data-ttu-id="6d3e1-124">DLL</span><span class="sxs-lookup"><span data-stu-id="6d3e1-124">DLL</span></span> | <span data-ttu-id="6d3e1-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6d3e1-125">Kernel32.dll</span></span> |
| <span data-ttu-id="6d3e1-126">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="6d3e1-126">Unicode and ANSI names</span></span> | <span data-ttu-id="6d3e1-127">**Getconsolealiaseslengthw** (Unicode) und **getconsolealiaseslengtha** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="6d3e1-127">**GetConsoleAliasesLengthW** (Unicode) and **GetConsoleAliasesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="6d3e1-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6d3e1-128">See also</span></span>

[<span data-ttu-id="6d3e1-129">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="6d3e1-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="6d3e1-130">Konsolenaliase</span><span class="sxs-lookup"><span data-stu-id="6d3e1-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="6d3e1-131">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="6d3e1-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6d3e1-132">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="6d3e1-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="6d3e1-133">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="6d3e1-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="6d3e1-134">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="6d3e1-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
