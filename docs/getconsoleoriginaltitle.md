---
title: Getconsoleoriginaltitle-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur getconsoleoriginaltitle-Funktion, die den ursprünglichen Titel für das aktuelle Konsolenfenster abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: ad12ff7b931b6bbc36a7fb0e9e0ee2ac3512a1f5
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037998"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="badd8-104">Getconsoleoriginaltitle-Funktion</span><span class="sxs-lookup"><span data-stu-id="badd8-104">GetConsoleOriginalTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="badd8-105">Ruft den ursprünglichen Titel für das aktuelle Konsolenfenster ab.</span><span class="sxs-lookup"><span data-stu-id="badd8-105">Retrieves the original title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="badd8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="badd8-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="badd8-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="badd8-107">Parameters</span></span>

<span data-ttu-id="badd8-108">*lpconsoletitle* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="badd8-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="badd8-109">Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge mit dem ursprünglichen Titel empfängt.</span><span class="sxs-lookup"><span data-stu-id="badd8-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="badd8-110">*nSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="badd8-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="badd8-111">Die Größe des *lpconsoletitle* -Puffers in Zeichen.</span><span class="sxs-lookup"><span data-stu-id="badd8-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="badd8-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="badd8-112">Return value</span></span>

<span data-ttu-id="badd8-113">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert die Länge der Zeichenfolge, die in den Puffer kopiert wird (in Zeichen).</span><span class="sxs-lookup"><span data-stu-id="badd8-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="badd8-114">Wenn der Puffer nicht groß genug ist, um den Titel zu speichern, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt eine **\_ erfolgreiche Fehlermeldung** zurück.</span><span class="sxs-lookup"><span data-stu-id="badd8-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns **ERROR\_SUCCESS** .</span></span>

<span data-ttu-id="badd8-115">Wenn die Funktion fehlschlägt, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt den Fehlercode zurück.</span><span class="sxs-lookup"><span data-stu-id="badd8-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="badd8-116">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="badd8-116">Remarks</span></span>

<span data-ttu-id="badd8-117">Um den Titel für ein Konsolenfenster festzulegen, verwenden Sie die [**setconsoletitle**](setconsoletitle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="badd8-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="badd8-118">Um die aktuelle Titel Zeichenfolge abzurufen, verwenden Sie die [**getconsoletitle**](getconsoletitle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="badd8-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="badd8-119">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0600 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="badd8-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="badd8-120">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="badd8-120">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

> [!TIP]
> <span data-ttu-id="badd8-121">Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="badd8-121">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="badd8-122">Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus.</span><span class="sxs-lookup"><span data-stu-id="badd8-122">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="badd8-123">Anwendungen, die Remoting über plattformübergreifende Hilfsprogramme und Transporte wie ssh verwenden, funktionieren möglicherweise nicht wie erwartet, wenn Sie diese API verwenden.</span><span class="sxs-lookup"><span data-stu-id="badd8-123">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="badd8-124">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="badd8-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="badd8-125">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="badd8-125">Minimum supported client</span></span> | <span data-ttu-id="badd8-126">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="badd8-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="badd8-127">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="badd8-127">Minimum supported server</span></span> | <span data-ttu-id="badd8-128">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="badd8-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="badd8-129">Header</span><span class="sxs-lookup"><span data-stu-id="badd8-129">Header</span></span> | <span data-ttu-id="badd8-130">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="badd8-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="badd8-131">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="badd8-131">Library</span></span> | <span data-ttu-id="badd8-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="badd8-132">Kernel32.lib</span></span> |
| <span data-ttu-id="badd8-133">DLL</span><span class="sxs-lookup"><span data-stu-id="badd8-133">DLL</span></span> | <span data-ttu-id="badd8-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="badd8-134">Kernel32.dll</span></span> |
| <span data-ttu-id="badd8-135">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="badd8-135">Unicode and ANSI names</span></span> | <span data-ttu-id="badd8-136">**Getconsoleoriginaltitlew** (Unicode) und **getconsoleoriginaltitlea** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="badd8-136">**GetConsoleOriginalTitleW** (Unicode) and **GetConsoleOriginalTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="badd8-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="badd8-137">See also</span></span>

[<span data-ttu-id="badd8-138">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="badd8-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="badd8-139">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="badd8-139">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="badd8-140">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="badd8-140">**SetConsoleTitle**</span></span>](setconsoletitle.md)
