---
title: Getconsoleoutputcp-Funktion
description: Ruft die Ausgabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: e80618ebd5c6b29f00e79594c55bfa15fab315ba
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059755"
---
# <a name="getconsoleoutputcp-function"></a><span data-ttu-id="bf879-104">Getconsoleoutputcp-Funktion</span><span class="sxs-lookup"><span data-stu-id="bf879-104">GetConsoleOutputCP function</span></span>


<span data-ttu-id="bf879-105">Ruft die Ausgabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="bf879-105">Retrieves the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="bf879-106">Eine-Konsole verwendet Ihre Ausgabe Codepage, um die von den verschiedenen Ausgabefunktionen geschriebenen Zeichen Werte in die im Konsolenfenster angezeigten Bilder zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="bf879-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

<a name="syntax"></a><span data-ttu-id="bf879-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="bf879-107">Syntax</span></span>
------

```C
UINT WINAPI GetConsoleOutputCP(void);
```

<a name="parameters"></a><span data-ttu-id="bf879-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="bf879-108">Parameters</span></span>
----------

<span data-ttu-id="bf879-109">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="bf879-109">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="bf879-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="bf879-110">Return value</span></span>
------------

<span data-ttu-id="bf879-111">Der Rückgabewert ist ein Code, der die Codepage bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="bf879-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="bf879-112">Eine Liste der Bezeichner finden Sie unter [Code Page Identifier](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="bf879-112">For a list of identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="bf879-113">Wenn der Rückgabewert 0 (null) ist, ist die Funktion fehlgeschlagen.</span><span class="sxs-lookup"><span data-stu-id="bf879-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="bf879-114">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="bf879-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="bf879-115">Hinweise</span><span class="sxs-lookup"><span data-stu-id="bf879-115">Remarks</span></span>
-------

<span data-ttu-id="bf879-116">Eine Codepage ordnet 256 Zeichen Codes einzelnen Zeichen zu.</span><span class="sxs-lookup"><span data-stu-id="bf879-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="bf879-117">Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="bf879-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="bf879-118">Weitere Informationen zu einer Codepage, einschließlich des Namens, finden Sie in der [**getcpinfoex**](https://msdn.microsoft.com/library/windows/desktop/dd318081) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="bf879-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span>

<span data-ttu-id="bf879-119">Verwenden Sie die [**setconsoleoutputcp**](setconsoleoutputcp.md) -Funktion, um die Ausgabe Codepage einer Konsole festzulegen.</span><span class="sxs-lookup"><span data-stu-id="bf879-119">To set a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) function.</span></span> <span data-ttu-id="bf879-120">Verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) und [**getconsolecp**](getconsolecp.md) , um die Eingabe Codepage einer Konsole festzulegen und abzufragen.</span><span class="sxs-lookup"><span data-stu-id="bf879-120">To set and query a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="bf879-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="bf879-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="bf879-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="bf879-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="bf879-123">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="bf879-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bf879-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="bf879-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="bf879-125">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="bf879-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bf879-126">Header</span><span class="sxs-lookup"><span data-stu-id="bf879-126">Header</span></span></p></td>
<td><span data-ttu-id="bf879-127">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bf879-127">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bf879-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="bf879-128">Library</span></span></p></td>
<td><span data-ttu-id="bf879-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="bf879-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bf879-130">DLL</span><span class="sxs-lookup"><span data-stu-id="bf879-130">DLL</span></span></p></td>
<td><span data-ttu-id="bf879-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bf879-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="bf879-132"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bf879-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="bf879-133">Konsolen Codepages</span><span class="sxs-lookup"><span data-stu-id="bf879-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="bf879-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="bf879-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bf879-135">**Getconsolecp**</span><span class="sxs-lookup"><span data-stu-id="bf879-135">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="bf879-136">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="bf879-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="bf879-137">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="bf879-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 




