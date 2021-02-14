---
title: Getconsolecp-Funktion
description: Ruft die Eingabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/GetConsoleCP
- wincon/GetConsoleCP
- GetConsoleCP
MS-HAID:
- '\_win32\_getconsolecp'
- base.getconsolecp
- consoles.getconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9e0af6d9-0f5c-45b3-a686-22449d26de47
topic_type:
- apiref
api_name:
- GetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: fd581c1f11f457054257e1e36e55b726f48b34fb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358460"
---
# <a name="getconsolecp-function"></a><span data-ttu-id="ab529-104">Getconsolecp-Funktion</span><span class="sxs-lookup"><span data-stu-id="ab529-104">GetConsoleCP function</span></span>

<span data-ttu-id="ab529-105">Ruft die Eingabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="ab529-105">Retrieves the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="ab529-106">Eine-Konsole verwendet die Eingabe Codepage, um Tastatureingaben in den entsprechenden Zeichen Wert zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="ab529-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

## <a name="syntax"></a><span data-ttu-id="ab529-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ab529-107">Syntax</span></span>

```C
UINT WINAPI GetConsoleCP(void);
```

## <a name="parameters"></a><span data-ttu-id="ab529-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab529-108">Parameters</span></span>

<span data-ttu-id="ab529-109">Diese Funktion besitzt keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="ab529-109">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="ab529-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ab529-110">Return value</span></span>

<span data-ttu-id="ab529-111">Der Rückgabewert ist ein Code, der die Codepage bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="ab529-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="ab529-112">Eine Liste der Bezeichner finden Sie unter [Code Page Identifier](/windows/win32/intl/code-page-identifiers).</span><span class="sxs-lookup"><span data-stu-id="ab529-112">For a list of identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="ab529-113">Wenn der Rückgabewert 0 (null) ist, ist die Funktion fehlgeschlagen.</span><span class="sxs-lookup"><span data-stu-id="ab529-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="ab529-114">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="ab529-114">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="ab529-115">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="ab529-115">Remarks</span></span>

<span data-ttu-id="ab529-116">Eine Codepage ordnet 256 Zeichen Codes einzelnen Zeichen zu.</span><span class="sxs-lookup"><span data-stu-id="ab529-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="ab529-117">Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="ab529-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="ab529-118">Weitere Informationen zu einer Codepage, einschließlich des Namens, finden Sie in der [**getcpinfoex**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="ab529-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span>

<span data-ttu-id="ab529-119">Um die Eingabe Codepage einer Konsole festzulegen, verwenden Sie die [**setconsolecp**](setconsolecp.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="ab529-119">To set a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) function.</span></span> <span data-ttu-id="ab529-120">Um die Ausgabe Codepage einer Konsole festzulegen und abzufragen, verwenden Sie die Funktionen [**setconsoleoutputcp**](setconsoleoutputcp.md) und [**getconsoleoutputcp**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="ab529-120">To set and query a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="ab529-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ab529-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ab529-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="ab529-122">Minimum supported client</span></span> | <span data-ttu-id="ab529-123">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="ab529-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ab529-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="ab529-124">Minimum supported server</span></span> | <span data-ttu-id="ab529-125">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="ab529-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ab529-126">Header</span><span class="sxs-lookup"><span data-stu-id="ab529-126">Header</span></span> | <span data-ttu-id="ab529-127">ConsoleApi.h (über WinCon.h, Windows.h einschließen)</span><span class="sxs-lookup"><span data-stu-id="ab529-127">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ab529-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="ab529-128">Library</span></span> | <span data-ttu-id="ab529-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="ab529-129">Kernel32.lib</span></span> |
| <span data-ttu-id="ab529-130">DLL</span><span class="sxs-lookup"><span data-stu-id="ab529-130">DLL</span></span> | <span data-ttu-id="ab529-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ab529-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ab529-132">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ab529-132">See also</span></span>

[<span data-ttu-id="ab529-133">Konsolen-Codepages</span><span class="sxs-lookup"><span data-stu-id="ab529-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="ab529-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="ab529-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ab529-135">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="ab529-135">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="ab529-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="ab529-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="ab529-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="ab529-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)