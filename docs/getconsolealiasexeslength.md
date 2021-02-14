---
title: Getconsolealiasexeslength-Funktion
description: Ruft die erforderliche Größe für den Puffer ab, der von der getconsolealiasexes-Funktion verwendet wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 4285bb64e919851a38494383a440afa6b94c8032
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358470"
---
# <a name="getconsolealiasexeslength-function"></a><span data-ttu-id="c9f4c-104">Getconsolealiasexeslength-Funktion</span><span class="sxs-lookup"><span data-stu-id="c9f4c-104">GetConsoleAliasExesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c9f4c-105">Ruft die erforderliche Größe für den Puffer ab, der von der [**getconsolealiasexes**](getconsolealiasexes.md) -Funktion verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c9f4c-105">Retrieves the required size for the buffer used by the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9f4c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9f4c-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

## <a name="parameters"></a><span data-ttu-id="c9f4c-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="c9f4c-107">Parameters</span></span>

<span data-ttu-id="c9f4c-108">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="c9f4c-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="c9f4c-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c9f4c-109">Return value</span></span>

<span data-ttu-id="c9f4c-110">Die Größe des Puffers, der zum Speichern der Namen aller ausführbaren Dateien erforderlich ist, für die Konsolen Aliase definiert sind (in Bytes).</span><span class="sxs-lookup"><span data-stu-id="c9f4c-110">The size of the buffer required to store the names of all executable files that have console aliases defined, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9f4c-111">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="c9f4c-111">Remarks</span></span>

<span data-ttu-id="c9f4c-112">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="c9f4c-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="c9f4c-113">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="c9f4c-113">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="c9f4c-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c9f4c-114">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c9f4c-115">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="c9f4c-115">Minimum supported client</span></span> | <span data-ttu-id="c9f4c-116">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="c9f4c-116">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c9f4c-117">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="c9f4c-117">Minimum supported server</span></span> | <span data-ttu-id="c9f4c-118">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="c9f4c-118">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c9f4c-119">Header</span><span class="sxs-lookup"><span data-stu-id="c9f4c-119">Header</span></span> | <span data-ttu-id="c9f4c-120">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c9f4c-120">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c9f4c-121">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="c9f4c-121">Library</span></span> | <span data-ttu-id="c9f4c-122">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c9f4c-122">Kernel32.lib</span></span> |
| <span data-ttu-id="c9f4c-123">DLL</span><span class="sxs-lookup"><span data-stu-id="c9f4c-123">DLL</span></span> | <span data-ttu-id="c9f4c-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c9f4c-124">Kernel32.dll</span></span> |
| <span data-ttu-id="c9f4c-125">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="c9f4c-125">Unicode and ANSI names</span></span> | <span data-ttu-id="c9f4c-126">**Getconsolealiasexeslengthw** (Unicode) und **getconsolealiasexeslengtha** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="c9f4c-126">**GetConsoleAliasExesLengthW** (Unicode) and **GetConsoleAliasExesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="c9f4c-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c9f4c-127">See also</span></span>

[<span data-ttu-id="c9f4c-128">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="c9f4c-128">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="c9f4c-129">Konsolenaliase</span><span class="sxs-lookup"><span data-stu-id="c9f4c-129">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="c9f4c-130">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="c9f4c-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c9f4c-131">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="c9f4c-131">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="c9f4c-132">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="c9f4c-132">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="c9f4c-133">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="c9f4c-133">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)