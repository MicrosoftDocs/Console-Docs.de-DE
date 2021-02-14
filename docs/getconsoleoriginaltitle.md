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
ms.openlocfilehash: 3c4fc202601cec9257b6cf95efdd460c64122b80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359000"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="f609c-104">Getconsoleoriginaltitle-Funktion</span><span class="sxs-lookup"><span data-stu-id="f609c-104">GetConsoleOriginalTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f609c-105">Ruft den ursprünglichen Titel für das aktuelle Konsolenfenster ab.</span><span class="sxs-lookup"><span data-stu-id="f609c-105">Retrieves the original title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="f609c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f609c-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="f609c-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="f609c-107">Parameters</span></span>

<span data-ttu-id="f609c-108">*lpconsoletitle* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="f609c-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="f609c-109">Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge mit dem ursprünglichen Titel empfängt.</span><span class="sxs-lookup"><span data-stu-id="f609c-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="f609c-110">*nSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f609c-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="f609c-111">Die Größe des *lpconsoletitle* -Puffers in Zeichen.</span><span class="sxs-lookup"><span data-stu-id="f609c-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="f609c-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="f609c-112">Return value</span></span>

<span data-ttu-id="f609c-113">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert die Länge der Zeichenfolge, die in den Puffer kopiert wird (in Zeichen).</span><span class="sxs-lookup"><span data-stu-id="f609c-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="f609c-114">Wenn der Puffer nicht groß genug ist, um den Titel zu speichern, ist der Rückgabewert 0 (null), und [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) gibt eine **\_ erfolgreiche Fehlermeldung** zurück.</span><span class="sxs-lookup"><span data-stu-id="f609c-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) returns **ERROR\_SUCCESS**.</span></span>

<span data-ttu-id="f609c-115">Wenn die Funktion fehlschlägt, ist der Rückgabewert 0 (null), und [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) gibt den Fehlercode zurück.</span><span class="sxs-lookup"><span data-stu-id="f609c-115">If the function fails, the return value is zero and [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f609c-116">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="f609c-116">Remarks</span></span>

<span data-ttu-id="f609c-117">Um den Titel für ein Konsolenfenster festzulegen, verwenden Sie die [**setconsoletitle**](setconsoletitle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="f609c-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="f609c-118">Um die aktuelle Titel Zeichenfolge abzurufen, verwenden Sie die [**getconsoletitle**](getconsoletitle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="f609c-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="f609c-119">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0600 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="f609c-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="f609c-120">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="f609c-120">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

> [!TIP]
> <span data-ttu-id="f609c-121">Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="f609c-121">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="f609c-122">Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus.</span><span class="sxs-lookup"><span data-stu-id="f609c-122">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="f609c-123">Anwendungen, die Remoting über plattformübergreifende Hilfsprogramme und Transporte wie ssh verwenden, funktionieren möglicherweise nicht wie erwartet, wenn Sie diese API verwenden.</span><span class="sxs-lookup"><span data-stu-id="f609c-123">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="f609c-124">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f609c-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f609c-125">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="f609c-125">Minimum supported client</span></span> | <span data-ttu-id="f609c-126">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="f609c-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="f609c-127">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="f609c-127">Minimum supported server</span></span> | <span data-ttu-id="f609c-128">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="f609c-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="f609c-129">Header</span><span class="sxs-lookup"><span data-stu-id="f609c-129">Header</span></span> | <span data-ttu-id="f609c-130">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f609c-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="f609c-131">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="f609c-131">Library</span></span> | <span data-ttu-id="f609c-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="f609c-132">Kernel32.lib</span></span> |
| <span data-ttu-id="f609c-133">DLL</span><span class="sxs-lookup"><span data-stu-id="f609c-133">DLL</span></span> | <span data-ttu-id="f609c-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f609c-134">Kernel32.dll</span></span> |
| <span data-ttu-id="f609c-135">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="f609c-135">Unicode and ANSI names</span></span> | <span data-ttu-id="f609c-136">**Getconsoleoriginaltitlew** (Unicode) und **getconsoleoriginaltitlea** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="f609c-136">**GetConsoleOriginalTitleW** (Unicode) and **GetConsoleOriginalTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="f609c-137">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f609c-137">See also</span></span>

[<span data-ttu-id="f609c-138">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="f609c-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f609c-139">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="f609c-139">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="f609c-140">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="f609c-140">**SetConsoleTitle**</span></span>](setconsoletitle.md)