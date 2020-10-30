---
title: Getconsoletitle-Funktion
description: Ruft den Titel und die Größe des Titels für das aktuelle Konsolenfenster ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 23b52ba1d5dde40ef842297249fdd2f87cebcb12
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037878"
---
# <a name="getconsoletitle-function"></a><span data-ttu-id="9b704-104">Getconsoletitle-Funktion</span><span class="sxs-lookup"><span data-stu-id="9b704-104">GetConsoleTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9b704-105">Ruft den Titel für das aktuelle Konsolenfenster ab.</span><span class="sxs-lookup"><span data-stu-id="9b704-105">Retrieves the title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="9b704-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b704-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="9b704-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="9b704-107">Parameters</span></span>

<span data-ttu-id="9b704-108">*lpconsoletitle* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="9b704-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="9b704-109">Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge mit dem Titel empfängt.</span><span class="sxs-lookup"><span data-stu-id="9b704-109">A pointer to a buffer that receives a null-terminated string containing the title.</span></span> <span data-ttu-id="9b704-110">Wenn der Puffer zu klein ist, um den Titel zu speichern, speichert die Funktion so viele Zeichen des Titels, wie Sie in den Puffer passt, und endet mit einem NULL-Terminator.</span><span class="sxs-lookup"><span data-stu-id="9b704-110">If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.</span></span>

<span data-ttu-id="9b704-111">*nSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9b704-111">*nSize* \[in\]</span></span>  
<span data-ttu-id="9b704-112">Die Größe des Puffers, auf den der *lpconsoletitle* -Parameter zeigt (in Zeichen).</span><span class="sxs-lookup"><span data-stu-id="9b704-112">The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="9b704-113">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="9b704-113">Return value</span></span>

<span data-ttu-id="9b704-114">Wenn die Funktion erfolgreich ausgeführt wird, entspricht der Rückgabewert der Länge des Konsolenfenster Titels in Zeichen.</span><span class="sxs-lookup"><span data-stu-id="9b704-114">If the function succeeds, the return value is the length of the console window's title, in characters.</span></span>

<span data-ttu-id="9b704-115">Wenn die Funktion fehlschlägt, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt den Fehlercode zurück.</span><span class="sxs-lookup"><span data-stu-id="9b704-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b704-116">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="9b704-116">Remarks</span></span>

<span data-ttu-id="9b704-117">Um den Titel für ein Konsolenfenster festzulegen, verwenden Sie die [**setconsoletitle**](setconsoletitle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="9b704-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="9b704-118">Um die ursprüngliche Titel Zeichenfolge abzurufen, verwenden Sie die [**getconsoleoriginaltitle**](getconsoleoriginaltitle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="9b704-118">To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="9b704-119">Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="9b704-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="9b704-120">Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus.</span><span class="sxs-lookup"><span data-stu-id="9b704-120">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="9b704-121">Anwendungen, die Remoting über plattformübergreifende Hilfsprogramme und Transporte wie ssh verwenden, funktionieren möglicherweise nicht wie erwartet, wenn Sie diese API verwenden.</span><span class="sxs-lookup"><span data-stu-id="9b704-121">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="examples"></a><span data-ttu-id="9b704-122">Beispiele</span><span class="sxs-lookup"><span data-stu-id="9b704-122">Examples</span></span>

<span data-ttu-id="9b704-123">Ein Beispiel finden Sie unter [**setconsoletitle**](setconsoletitle.md).</span><span class="sxs-lookup"><span data-stu-id="9b704-123">For an example, see [**SetConsoleTitle**](setconsoletitle.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="9b704-124">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="9b704-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9b704-125">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="9b704-125">Minimum supported client</span></span> | <span data-ttu-id="9b704-126">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="9b704-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="9b704-127">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="9b704-127">Minimum supported server</span></span> | <span data-ttu-id="9b704-128">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="9b704-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="9b704-129">Header</span><span class="sxs-lookup"><span data-stu-id="9b704-129">Header</span></span> | <span data-ttu-id="9b704-130">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9b704-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9b704-131">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="9b704-131">Library</span></span> | <span data-ttu-id="9b704-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="9b704-132">Kernel32.lib</span></span> |
| <span data-ttu-id="9b704-133">DLL</span><span class="sxs-lookup"><span data-stu-id="9b704-133">DLL</span></span> | <span data-ttu-id="9b704-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9b704-134">Kernel32.dll</span></span> |
| <span data-ttu-id="9b704-135">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="9b704-135">Unicode and ANSI names</span></span> | <span data-ttu-id="9b704-136">**Getconsoletitlew** (Unicode) und **getconsoletitlea** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="9b704-136">**GetConsoleTitleW** (Unicode) and **GetConsoleTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="9b704-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9b704-137">See also</span></span>

[<span data-ttu-id="9b704-138">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="9b704-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9b704-139">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="9b704-139">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="9b704-140">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="9b704-140">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="9b704-141">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="9b704-141">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="9b704-142">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="9b704-142">**SetConsoleTitle**</span></span>](setconsoletitle.md)
