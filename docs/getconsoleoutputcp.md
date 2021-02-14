---
title: Getconsoleoutputcp-Funktion
description: Ruft die Ausgabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 858b0de83c7b1c4678e992b5f9d0ca3d4876ba49
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358950"
---
# <a name="getconsoleoutputcp-function"></a><span data-ttu-id="3217e-104">Getconsoleoutputcp-Funktion</span><span class="sxs-lookup"><span data-stu-id="3217e-104">GetConsoleOutputCP function</span></span>

<span data-ttu-id="3217e-105">Ruft die Ausgabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="3217e-105">Retrieves the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="3217e-106">Eine-Konsole verwendet Ihre Ausgabe Codepage, um die von den verschiedenen Ausgabefunktionen geschriebenen Zeichen Werte in die im Konsolenfenster angezeigten Bilder zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="3217e-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="3217e-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="3217e-107">Syntax</span></span>

```C
UINT WINAPI GetConsoleOutputCP(void);
```

## <a name="parameters"></a><span data-ttu-id="3217e-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="3217e-108">Parameters</span></span>

<span data-ttu-id="3217e-109">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="3217e-109">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="3217e-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="3217e-110">Return value</span></span>

<span data-ttu-id="3217e-111">Der Rückgabewert ist ein Code, der die Codepage bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="3217e-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="3217e-112">Eine Liste der Bezeichner finden Sie unter [Code Page Identifier](/windows/win32/intl/code-page-identifiers).</span><span class="sxs-lookup"><span data-stu-id="3217e-112">For a list of identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="3217e-113">Wenn der Rückgabewert 0 (null) ist, ist die Funktion fehlgeschlagen.</span><span class="sxs-lookup"><span data-stu-id="3217e-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="3217e-114">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="3217e-114">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="3217e-115">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="3217e-115">Remarks</span></span>

<span data-ttu-id="3217e-116">Eine Codepage ordnet 256 Zeichen Codes einzelnen Zeichen zu.</span><span class="sxs-lookup"><span data-stu-id="3217e-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="3217e-117">Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="3217e-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="3217e-118">Weitere Informationen zu einer Codepage, einschließlich des Namens, finden Sie in der [**getcpinfoex**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="3217e-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span>

<span data-ttu-id="3217e-119">Verwenden Sie die [**setconsoleoutputcp**](setconsoleoutputcp.md) -Funktion, um die Ausgabe Codepage einer Konsole festzulegen.</span><span class="sxs-lookup"><span data-stu-id="3217e-119">To set a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) function.</span></span> <span data-ttu-id="3217e-120">Verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) und [**getconsolecp**](getconsolecp.md) , um die Eingabe Codepage einer Konsole festzulegen und abzufragen.</span><span class="sxs-lookup"><span data-stu-id="3217e-120">To set and query a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="3217e-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="3217e-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3217e-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="3217e-122">Minimum supported client</span></span> | <span data-ttu-id="3217e-123">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="3217e-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="3217e-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="3217e-124">Minimum supported server</span></span> | <span data-ttu-id="3217e-125">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="3217e-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="3217e-126">Header</span><span class="sxs-lookup"><span data-stu-id="3217e-126">Header</span></span> | <span data-ttu-id="3217e-127">ConsoleApi.h (über WinCon.h, Windows.h einschließen)</span><span class="sxs-lookup"><span data-stu-id="3217e-127">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="3217e-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="3217e-128">Library</span></span> | <span data-ttu-id="3217e-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="3217e-129">Kernel32.lib</span></span> |
| <span data-ttu-id="3217e-130">DLL</span><span class="sxs-lookup"><span data-stu-id="3217e-130">DLL</span></span> | <span data-ttu-id="3217e-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3217e-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="3217e-132">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3217e-132">See also</span></span>

[<span data-ttu-id="3217e-133">Konsolen-Codepages</span><span class="sxs-lookup"><span data-stu-id="3217e-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="3217e-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="3217e-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3217e-135">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="3217e-135">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="3217e-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="3217e-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="3217e-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="3217e-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)