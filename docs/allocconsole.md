---
title: AllocConsole-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur AllocConsole-Funktion, die eine neue Konsole für den aufrufenden Prozess zuordnet.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 3b48570424a4c60a56094f5c41934f9946f67203
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357860"
---
# <a name="allocconsole-function"></a><span data-ttu-id="5c2c4-104">AllocConsole-Funktion</span><span class="sxs-lookup"><span data-stu-id="5c2c4-104">AllocConsole function</span></span>

<span data-ttu-id="5c2c4-105">Ordnet eine neue Konsole für den aufrufenden Prozess zu.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-105">Allocates a new console for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="5c2c4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c2c4-106">Syntax</span></span>

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="5c2c4-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="5c2c4-107">Parameters</span></span>

<span data-ttu-id="5c2c4-108">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="5c2c4-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5c2c4-109">Return value</span></span>

<span data-ttu-id="5c2c4-110">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="5c2c4-111">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="5c2c4-112">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-112">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="5c2c4-113">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="5c2c4-113">Remarks</span></span>

<span data-ttu-id="5c2c4-114">Ein Prozess kann nur einer Konsole zugeordnet sein, sodass die **AllocConsole**-Funktion fehlschlägt, wenn der aufrufende Prozess bereits über eine Konsole verfügt.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="5c2c4-115">Ein Prozess kann die [**FreeConsole**](freeconsole.md)-Funktion verwenden, um sich selbst von seiner aktuellen Konsole zu trennen. Anschließend kann er dann **AllocConsole** aufrufen, um eine neue Konsole zu erstellen, oder [**AttachConsole**](attachconsole.md), um eine andere Konsole anzufügen.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="5c2c4-116">Wenn der aufrufenden Prozess einen untergeordneten Prozess erstellt, erbt der untergeordnete Prozess die neue Konsole.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="5c2c4-117">**AllocConsole** initialisiert die Standardhandles für Eingabe, Ausgabe und Fehler für die neue Konsole.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="5c2c4-118">Das Standardeingabehandle ist ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe- und Standardfehlerhandles sind Handles für den Bildschirmpuffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="5c2c4-119">Um diese Handles abzurufen, verwenden Sie die Funktion [**GetStdHandle**](getstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="5c2c4-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="5c2c4-120">Diese Funktion wird hauptsächlich von einer grafischen Benutzeroberflächenanwendung (GUI) zum Erstellen eines Konsolenfensters verwendet.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="5c2c4-121">GUI-Anwendungen werden ohne eine-Konsole initialisiert.</span><span class="sxs-lookup"><span data-stu-id="5c2c4-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="5c2c4-122">Konsolenanwendungen werden mit einer Konsole initialisiert, es sei denn, sie werden als getrennte Prozesse erstellt (durch Aufrufen der [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)-Funktion mit dem **DETACHED\_PROCESS**-Flag).</span><span class="sxs-lookup"><span data-stu-id="5c2c4-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function with the **DETACHED\_PROCESS** flag).</span></span>

## <a name="requirements"></a><span data-ttu-id="5c2c4-123">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5c2c4-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5c2c4-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="5c2c4-124">Minimum supported client</span></span> | <span data-ttu-id="5c2c4-125">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="5c2c4-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5c2c4-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="5c2c4-126">Minimum supported server</span></span> | <span data-ttu-id="5c2c4-127">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="5c2c4-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5c2c4-128">Header</span><span class="sxs-lookup"><span data-stu-id="5c2c4-128">Header</span></span> | <span data-ttu-id="5c2c4-129">ConsoleApi.h (über WinCon.h, Windows.h einschließen)</span><span class="sxs-lookup"><span data-stu-id="5c2c4-129">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="5c2c4-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="5c2c4-130">Library</span></span> | <span data-ttu-id="5c2c4-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="5c2c4-131">Kernel32.lib</span></span> |
| <span data-ttu-id="5c2c4-132">DLL</span><span class="sxs-lookup"><span data-stu-id="5c2c4-132">DLL</span></span> | <span data-ttu-id="5c2c4-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5c2c4-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="5c2c4-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5c2c4-134">See also</span></span>

[<span data-ttu-id="5c2c4-135">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="5c2c4-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5c2c4-136">Konsolen</span><span class="sxs-lookup"><span data-stu-id="5c2c4-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="5c2c4-137">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="5c2c4-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="5c2c4-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="5c2c4-138">**CreateProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[<span data-ttu-id="5c2c4-139">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="5c2c4-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="5c2c4-140">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="5c2c4-140">**GetStdHandle**</span></span>](getstdhandle.md)