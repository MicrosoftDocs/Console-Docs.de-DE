---
title: GetConsoleWindow-Funktion
description: Ruft das Fenster Handle ab, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: dd356bab4674da0cc090e42911829dee994fa8b1
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059675"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="c6bab-104">GetConsoleWindow-Funktion</span><span class="sxs-lookup"><span data-stu-id="c6bab-104">GetConsoleWindow function</span></span>


<span data-ttu-id="c6bab-105">Ruft das Fenster Handle ab, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="c6bab-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="c6bab-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c6bab-106">Syntax</span></span>
------

```C
HWND WINAPI GetConsoleWindow(void);
```

<a name="parameters"></a><span data-ttu-id="c6bab-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="c6bab-107">Parameters</span></span>
----------

<span data-ttu-id="c6bab-108">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="c6bab-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="c6bab-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c6bab-109">Return value</span></span>
------------

<span data-ttu-id="c6bab-110">Der Rückgabewert ist ein Handle für das Fenster, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist, oder **null** , wenn keine solche zugeordnete Konsole vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="c6bab-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

<a name="remarks"></a><span data-ttu-id="c6bab-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c6bab-111">Remarks</span></span>
-------

<span data-ttu-id="c6bab-112">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="c6bab-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="c6bab-113">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="c6bab-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="c6bab-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c6bab-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c6bab-115">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="c6bab-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c6bab-116">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="c6bab-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c6bab-117">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="c6bab-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c6bab-118">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="c6bab-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c6bab-119">Header</span><span class="sxs-lookup"><span data-stu-id="c6bab-119">Header</span></span></p></td>
<td><span data-ttu-id="c6bab-120">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c6bab-120">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c6bab-121">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="c6bab-121">Library</span></span></p></td>
<td><span data-ttu-id="c6bab-122">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c6bab-122">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c6bab-123">DLL</span><span class="sxs-lookup"><span data-stu-id="c6bab-123">DLL</span></span></p></td>
<td><span data-ttu-id="c6bab-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c6bab-124">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c6bab-125"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c6bab-125"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c6bab-126">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="c6bab-126">Console Functions</span></span>](console-functions.md)

 

 




