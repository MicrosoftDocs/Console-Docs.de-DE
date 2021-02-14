---
title: GetConsoleWindow-Funktion
description: Ruft das Fenster Handle ab, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: ead8c4216fd0d1beb2a5fa6a6acfe3f4ce20df6f
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358890"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="64381-104">GetConsoleWindow-Funktion</span><span class="sxs-lookup"><span data-stu-id="64381-104">GetConsoleWindow function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="64381-105">Ruft das Fenster Handle ab, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="64381-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="64381-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="64381-106">Syntax</span></span>

```C
HWND WINAPI GetConsoleWindow(void);
```

## <a name="parameters"></a><span data-ttu-id="64381-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="64381-107">Parameters</span></span>

<span data-ttu-id="64381-108">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="64381-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="64381-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="64381-109">Return value</span></span>

<span data-ttu-id="64381-110">Der Rückgabewert ist ein Handle für das Fenster, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist, oder **null** , wenn keine solche zugeordnete Konsole vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="64381-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

## <a name="remarks"></a><span data-ttu-id="64381-111">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="64381-111">Remarks</span></span>

<span data-ttu-id="64381-112">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="64381-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="64381-113">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="64381-113">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

<span data-ttu-id="64381-114">Für eine Anwendung, die in einer [**pseudoconsole**](pseudoconsoles.md) -Sitzung gehostet wird, gibt diese Funktion ein Fenster Handle nur für Nachrichten Warteschlangen-Zwecke zurück.</span><span class="sxs-lookup"><span data-stu-id="64381-114">For an application that is hosted inside a [**pseudoconsole**](pseudoconsoles.md) session, this function returns a window handle for message queue purposes only.</span></span> <span data-ttu-id="64381-115">Das zugehörige Fenster wird nicht lokal angezeigt, da die _pseudoconsole_ alle Aktionen in einen Stream für die Darstellung in einem anderen Terminalfenster an anderer Stelle serialisiert.</span><span class="sxs-lookup"><span data-stu-id="64381-115">The associated window is not displayed locally as the _pseudoconsole_ is serializing all actions to a stream for presentation on another terminal window elsewhere.</span></span>

## <a name="requirements"></a><span data-ttu-id="64381-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="64381-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="64381-117">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="64381-117">Minimum supported client</span></span> | <span data-ttu-id="64381-118">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="64381-118">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="64381-119">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="64381-119">Minimum supported server</span></span> | <span data-ttu-id="64381-120">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="64381-120">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="64381-121">Header</span><span class="sxs-lookup"><span data-stu-id="64381-121">Header</span></span> | <span data-ttu-id="64381-122">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="64381-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="64381-123">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="64381-123">Library</span></span> | <span data-ttu-id="64381-124">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="64381-124">Kernel32.lib</span></span> |
| <span data-ttu-id="64381-125">DLL</span><span class="sxs-lookup"><span data-stu-id="64381-125">DLL</span></span> | <span data-ttu-id="64381-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="64381-126">Kernel32.dll</span></span> |

</table>

## <a name="see-also"></a><span data-ttu-id="64381-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="64381-127">See also</span></span>

[<span data-ttu-id="64381-128">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="64381-128">Console Functions</span></span>](console-functions.md)