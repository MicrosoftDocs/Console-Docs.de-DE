---
title: Getconsoletitle-Funktion
description: Ruft den Titel und die Größe des Titels für das aktuelle Konsolenfenster ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 5b8e78e65e52c3f10be14afa6a122fa12609a2eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059699"
---
# <a name="getconsoletitle-function"></a><span data-ttu-id="33e12-104">Getconsoletitle-Funktion</span><span class="sxs-lookup"><span data-stu-id="33e12-104">GetConsoleTitle function</span></span>


<span data-ttu-id="33e12-105">Ruft den Titel für das aktuelle Konsolenfenster ab.</span><span class="sxs-lookup"><span data-stu-id="33e12-105">Retrieves the title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="33e12-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="33e12-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a><span data-ttu-id="33e12-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="33e12-107">Parameters</span></span>
----------

<span data-ttu-id="33e12-108">*lpconsoletitle* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="33e12-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="33e12-109">Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge mit dem Titel empfängt.</span><span class="sxs-lookup"><span data-stu-id="33e12-109">A pointer to a buffer that receives a null-terminated string containing the title.</span></span> <span data-ttu-id="33e12-110">Wenn der Puffer zu klein ist, um den Titel zu speichern, speichert die Funktion so viele Zeichen des Titels, wie Sie in den Puffer passt, und endet mit einem NULL-Terminator.</span><span class="sxs-lookup"><span data-stu-id="33e12-110">If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.</span></span>

<span data-ttu-id="33e12-111">*nSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="33e12-111">*nSize* \[in\]</span></span>  
<span data-ttu-id="33e12-112">Die Größe des Puffers, auf den der *lpconsoletitle* -Parameter zeigt (in Zeichen).</span><span class="sxs-lookup"><span data-stu-id="33e12-112">The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="33e12-113">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="33e12-113">Return value</span></span>
------------

<span data-ttu-id="33e12-114">Wenn die Funktion erfolgreich ausgeführt wird, entspricht der Rückgabewert der Länge des Konsolenfenster Titels in Zeichen.</span><span class="sxs-lookup"><span data-stu-id="33e12-114">If the function succeeds, the return value is the length of the console window's title, in characters.</span></span>

<span data-ttu-id="33e12-115">Wenn die Funktion fehlschlägt, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt den Fehlercode zurück.</span><span class="sxs-lookup"><span data-stu-id="33e12-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

<a name="remarks"></a><span data-ttu-id="33e12-116">Hinweise</span><span class="sxs-lookup"><span data-stu-id="33e12-116">Remarks</span></span>
-------

<span data-ttu-id="33e12-117">Um den Titel für ein Konsolenfenster festzulegen, verwenden Sie die [**setconsoletitle**](setconsoletitle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="33e12-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="33e12-118">Um die ursprüngliche Titel Zeichenfolge abzurufen, verwenden Sie die [**getconsoleoriginaltitle**](getconsoleoriginaltitle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="33e12-118">To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.</span></span>

<span data-ttu-id="33e12-119">Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole.</span><span class="sxs-lookup"><span data-stu-id="33e12-119">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="33e12-120">Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt.</span><span class="sxs-lookup"><span data-stu-id="33e12-120">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="33e12-121">Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="33e12-121">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="33e12-122">Beispiele</span><span class="sxs-lookup"><span data-stu-id="33e12-122">Examples</span></span>
--------

<span data-ttu-id="33e12-123">Ein Beispiel finden Sie unter [**setconsoletitle**](setconsoletitle.md).</span><span class="sxs-lookup"><span data-stu-id="33e12-123">For an example, see [**SetConsoleTitle**](setconsoletitle.md).</span></span>

<a name="requirements"></a><span data-ttu-id="33e12-124">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="33e12-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="33e12-125">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="33e12-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="33e12-126">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="33e12-126">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="33e12-127">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="33e12-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="33e12-128">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="33e12-128">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="33e12-129">Header</span><span class="sxs-lookup"><span data-stu-id="33e12-129">Header</span></span></p></td>
<td><span data-ttu-id="33e12-130">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="33e12-130">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="33e12-131">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="33e12-131">Library</span></span></p></td>
<td><span data-ttu-id="33e12-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="33e12-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="33e12-133">DLL</span><span class="sxs-lookup"><span data-stu-id="33e12-133">DLL</span></span></p></td>
<td><span data-ttu-id="33e12-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="33e12-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="33e12-135">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="33e12-135">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="33e12-136"><strong>Getconsoletitlew</strong> (Unicode) und <strong>getconsoletitlea</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="33e12-136"><strong>GetConsoleTitleW</strong> (Unicode) and <strong>GetConsoleTitleA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="33e12-137"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="33e12-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="33e12-138">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="33e12-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="33e12-139">**Getconsoleoriginaltitle**</span><span class="sxs-lookup"><span data-stu-id="33e12-139">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="33e12-140">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="33e12-140">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="33e12-141">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="33e12-141">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="33e12-142">**Setconsoletitle**</span><span class="sxs-lookup"><span data-stu-id="33e12-142">**SetConsoleTitle**</span></span>](setconsoletitle.md)

 

 




