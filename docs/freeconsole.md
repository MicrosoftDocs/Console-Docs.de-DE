---
title: Freeconsole-Funktion
description: Siehe Referenzinformationen zur freeconsole-Funktion, die den aufrufenden Prozess von seiner Konsole trennt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: af4382026b8e6455319e16ee21255fbc9352e3cd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039018"
---
# <a name="freeconsole-function"></a><span data-ttu-id="0a214-104">Freeconsole-Funktion</span><span class="sxs-lookup"><span data-stu-id="0a214-104">FreeConsole function</span></span>

<span data-ttu-id="0a214-105">Trennt den aufrufenden Prozess von seiner Konsole aus.</span><span class="sxs-lookup"><span data-stu-id="0a214-105">Detaches the calling process from its console.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a214-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0a214-106">Syntax</span></span>

```C
BOOL WINAPI FreeConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="0a214-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="0a214-107">Parameters</span></span>

<span data-ttu-id="0a214-108">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="0a214-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="0a214-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="0a214-109">Return value</span></span>

<span data-ttu-id="0a214-110">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="0a214-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0a214-111">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="0a214-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0a214-112">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="0a214-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="0a214-113">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="0a214-113">Remarks</span></span>

<span data-ttu-id="0a214-114">Ein Prozess kann höchstens an eine Konsole angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="0a214-114">A process can be attached to at most one console.</span></span> <span data-ttu-id="0a214-115">Wenn der Aufrufprozess nicht bereits an eine Konsole angefügt ist, lautet der Fehlercode **" \_ ungültiger \_ Parameter** " (87).</span><span class="sxs-lookup"><span data-stu-id="0a214-115">If the calling process is not already attached to a console, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="0a214-116">Ein Prozess kann die **freeconsole** -Funktion verwenden, um sich von seiner Konsole zu trennen.</span><span class="sxs-lookup"><span data-stu-id="0a214-116">A process can use the **FreeConsole** function to detach itself from its console.</span></span> <span data-ttu-id="0a214-117">Wenn andere Prozesse die-Konsole gemeinsam nutzen, wird die Konsole nicht zerstört, aber der Prozess, der **freeconsole** aufgerufen hat, kann nicht darauf verweisen.</span><span class="sxs-lookup"><span data-stu-id="0a214-117">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="0a214-118">Eine Konsole wird geschlossen, wenn der letzte daran angefügte Prozess beendet wird oder **freeconsole** aufruft.</span><span class="sxs-lookup"><span data-stu-id="0a214-118">A console is closed when the last process attached to it terminates or calls **FreeConsole** .</span></span> <span data-ttu-id="0a214-119">Nachdem ein Prozess **freeconsole** aufgerufen hat, kann er die Funktion " [**Zuweisung**](allocconsole.md) " aufrufen, um eine neue Konsole [**oder eine**](attachconsole.md) anfügekonsole zum Anfügen an eine andere Konsole zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0a214-119">After a process calls **FreeConsole** , it can call the [**AllocConsole**](allocconsole.md) function to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a214-120">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="0a214-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0a214-121">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="0a214-121">Minimum supported client</span></span> | <span data-ttu-id="0a214-122">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="0a214-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="0a214-123">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="0a214-123">Minimum supported server</span></span> | <span data-ttu-id="0a214-124">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="0a214-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="0a214-125">Header</span><span class="sxs-lookup"><span data-stu-id="0a214-125">Header</span></span> | <span data-ttu-id="0a214-126">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0a214-126">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0a214-127">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="0a214-127">Library</span></span> | <span data-ttu-id="0a214-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="0a214-128">Kernel32.lib</span></span> |
| <span data-ttu-id="0a214-129">DLL</span><span class="sxs-lookup"><span data-stu-id="0a214-129">DLL</span></span> | <span data-ttu-id="0a214-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0a214-130">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="0a214-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0a214-131">See also</span></span>

[<span data-ttu-id="0a214-132">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="0a214-132">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="0a214-133">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="0a214-133">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="0a214-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="0a214-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0a214-135">Trö</span><span class="sxs-lookup"><span data-stu-id="0a214-135">Consoles</span></span>](consoles.md)
