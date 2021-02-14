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
ms.openlocfilehash: 78f9d718c960478e491b76a12f2a670c03529242
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357497"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="ebe3b-104">Getconsolealiaseslength-Funktion</span><span class="sxs-lookup"><span data-stu-id="ebe3b-104">GetConsoleAliasesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ebe3b-105">Ruft die erforderliche Größe für den Puffer ab, der von der [**getconsolealiases**](getconsolealiases.md) -Funktion verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ebe3b-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="ebe3b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ebe3b-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="ebe3b-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="ebe3b-107">Parameters</span></span>

<span data-ttu-id="ebe3b-108">*lpexename* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ebe3b-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="ebe3b-109">Der Name der ausführbaren Datei, deren Konsolen Aliase abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ebe3b-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="ebe3b-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ebe3b-110">Return value</span></span>

<span data-ttu-id="ebe3b-111">Die Größe des Puffers, der zum Speichern aller für diese ausführbaren Datei definierten Konsolen Aliase in Bytes erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="ebe3b-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="ebe3b-112">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="ebe3b-112">Remarks</span></span>

<span data-ttu-id="ebe3b-113">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="ebe3b-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="ebe3b-114">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="ebe3b-114">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="ebe3b-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ebe3b-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ebe3b-116">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="ebe3b-116">Minimum supported client</span></span> | <span data-ttu-id="ebe3b-117">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="ebe3b-117">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ebe3b-118">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="ebe3b-118">Minimum supported server</span></span> | <span data-ttu-id="ebe3b-119">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="ebe3b-119">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ebe3b-120">Header</span><span class="sxs-lookup"><span data-stu-id="ebe3b-120">Header</span></span> | <span data-ttu-id="ebe3b-121">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ebe3b-121">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ebe3b-122">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="ebe3b-122">Library</span></span> | <span data-ttu-id="ebe3b-123">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="ebe3b-123">Kernel32.lib</span></span> |
| <span data-ttu-id="ebe3b-124">DLL</span><span class="sxs-lookup"><span data-stu-id="ebe3b-124">DLL</span></span> | <span data-ttu-id="ebe3b-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ebe3b-125">Kernel32.dll</span></span> |
| <span data-ttu-id="ebe3b-126">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="ebe3b-126">Unicode and ANSI names</span></span> | <span data-ttu-id="ebe3b-127">**Getconsolealiaseslengthw** (Unicode) und **getconsolealiaseslengtha** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="ebe3b-127">**GetConsoleAliasesLengthW** (Unicode) and **GetConsoleAliasesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="ebe3b-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ebe3b-128">See also</span></span>

[<span data-ttu-id="ebe3b-129">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="ebe3b-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="ebe3b-130">Konsolenaliase</span><span class="sxs-lookup"><span data-stu-id="ebe3b-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="ebe3b-131">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="ebe3b-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ebe3b-132">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="ebe3b-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="ebe3b-133">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="ebe3b-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="ebe3b-134">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="ebe3b-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)