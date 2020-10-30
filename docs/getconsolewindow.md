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
ms.openlocfilehash: c74fe1a29b9ba2ea721e874eb624ea2f8517094c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038808"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="ce9de-104">GetConsoleWindow-Funktion</span><span class="sxs-lookup"><span data-stu-id="ce9de-104">GetConsoleWindow function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ce9de-105">Ruft das Fenster Handle ab, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="ce9de-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="ce9de-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ce9de-106">Syntax</span></span>

```C
HWND WINAPI GetConsoleWindow(void);
```

## <a name="parameters"></a><span data-ttu-id="ce9de-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="ce9de-107">Parameters</span></span>

<span data-ttu-id="ce9de-108">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="ce9de-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="ce9de-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ce9de-109">Return value</span></span>

<span data-ttu-id="ce9de-110">Der Rückgabewert ist ein Handle für das Fenster, das von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist, oder **null** , wenn keine solche zugeordnete Konsole vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="ce9de-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

## <a name="remarks"></a><span data-ttu-id="ce9de-111">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="ce9de-111">Remarks</span></span>

<span data-ttu-id="ce9de-112">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="ce9de-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="ce9de-113">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="ce9de-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

<span data-ttu-id="ce9de-114">Für eine Anwendung, die in einer [**pseudoconsole**](pseudoconsoles.md) -Sitzung gehostet wird, gibt diese Funktion ein Fenster Handle nur für Nachrichten Warteschlangen-Zwecke zurück.</span><span class="sxs-lookup"><span data-stu-id="ce9de-114">For an application that is hosted inside a [**pseudoconsole**](pseudoconsoles.md) session, this function returns a window handle for message queue purposes only.</span></span> <span data-ttu-id="ce9de-115">Das zugehörige Fenster wird nicht lokal angezeigt, da die _pseudoconsole_ alle Aktionen in einen Stream für die Darstellung in einem anderen Terminalfenster an anderer Stelle serialisiert.</span><span class="sxs-lookup"><span data-stu-id="ce9de-115">The associated window is not displayed locally as the _pseudoconsole_ is serializing all actions to a stream for presentation on another terminal window elsewhere.</span></span>

## <a name="requirements"></a><span data-ttu-id="ce9de-116">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="ce9de-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ce9de-117">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="ce9de-117">Minimum supported client</span></span> | <span data-ttu-id="ce9de-118">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="ce9de-118">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ce9de-119">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="ce9de-119">Minimum supported server</span></span> | <span data-ttu-id="ce9de-120">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="ce9de-120">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ce9de-121">Header</span><span class="sxs-lookup"><span data-stu-id="ce9de-121">Header</span></span> | <span data-ttu-id="ce9de-122">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ce9de-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ce9de-123">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="ce9de-123">Library</span></span> | <span data-ttu-id="ce9de-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ce9de-124">Kernel32.lib</span></span> |
| <span data-ttu-id="ce9de-125">DLL</span><span class="sxs-lookup"><span data-stu-id="ce9de-125">DLL</span></span> | <span data-ttu-id="ce9de-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ce9de-126">Kernel32.dll</span></span> |

</table>

## <a name="see-also"></a><span data-ttu-id="ce9de-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ce9de-127">See also</span></span>

[<span data-ttu-id="ce9de-128">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="ce9de-128">Console Functions</span></span>](console-functions.md)
