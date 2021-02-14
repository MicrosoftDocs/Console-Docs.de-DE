---
title: Setconsolecp-Funktion
description: Legt die Eingabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 040a97360f455fec2ebd043de21e390959f1db0a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357720"
---
# <a name="setconsolecp-function"></a><span data-ttu-id="e0771-104">Setconsolecp-Funktion</span><span class="sxs-lookup"><span data-stu-id="e0771-104">SetConsoleCP function</span></span>

<span data-ttu-id="e0771-105">Legt die Eingabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="e0771-105">Sets the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="e0771-106">Eine-Konsole verwendet die Eingabe Codepage, um Tastatureingaben in den entsprechenden Zeichen Wert zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="e0771-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0771-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0771-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a><span data-ttu-id="e0771-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="e0771-108">Parameters</span></span>

<span data-ttu-id="e0771-109">*wcodepageid* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e0771-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="e0771-110">Der Bezeichner der festzulegenden Codepage.</span><span class="sxs-lookup"><span data-stu-id="e0771-110">The identifier of the code page to be set.</span></span> <span data-ttu-id="e0771-111">Weitere Informationen finden Sie in den Hinweisen.</span><span class="sxs-lookup"><span data-stu-id="e0771-111">For more information, see Remarks.</span></span>

## <a name="return-value"></a><span data-ttu-id="e0771-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e0771-112">Return value</span></span>

<span data-ttu-id="e0771-113">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="e0771-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e0771-114">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="e0771-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e0771-115">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="e0771-115">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="e0771-116">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="e0771-116">Remarks</span></span>

<span data-ttu-id="e0771-117">Eine Codepage ordnet 256 Zeichen Codes einzelnen Zeichen zu.</span><span class="sxs-lookup"><span data-stu-id="e0771-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="e0771-118">Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="e0771-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="e0771-119">Verwenden Sie die Funktion " [**enumsystemcodepages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) ", um die Codepages zu suchen, die vom Betriebssystem installiert oder unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="e0771-119">To find the code pages that are installed or supported by the operating system, use the [**EnumSystemCodePages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) function.</span></span> <span data-ttu-id="e0771-120">Die Bezeichner der auf dem lokalen Computer verfügbaren Codepages werden auch in der Registrierung unter folgendem Schlüssel gespeichert:</span><span class="sxs-lookup"><span data-stu-id="e0771-120">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

<span data-ttu-id="e0771-121">Es ist jedoch besser, mit [**enumsystemcodepages Codepages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) aufzuzählen, da sich die Registrierung in verschiedenen Versionen von Windows unterscheiden kann.</span><span class="sxs-lookup"><span data-stu-id="e0771-121">However, it is better to use [**EnumSystemCodePages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>

<span data-ttu-id="e0771-122">Verwenden Sie die [**IsValidCodePage**](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) -Funktion, um zu bestimmen, ob eine bestimmte Codepage gültig ist.</span><span class="sxs-lookup"><span data-stu-id="e0771-122">To determine whether a particular code page is valid, use the [**IsValidCodePage**](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) function.</span></span> <span data-ttu-id="e0771-123">Verwenden Sie die [**getcpinfoex**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) -Funktion, um weitere Informationen über eine Codepage einschließlich Ihres Namens abzurufen.</span><span class="sxs-lookup"><span data-stu-id="e0771-123">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span> <span data-ttu-id="e0771-124">Eine Liste der verfügbaren Code Page Bezeichner finden Sie unter [Code Page Identifier](/windows/win32/intl/code-page-identifiers).</span><span class="sxs-lookup"><span data-stu-id="e0771-124">For a list of available code page identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="e0771-125">Verwenden Sie die [**getconsolecp**](getconsolecp.md) -Funktion, um die aktuelle Eingabe Codepage einer Konsole zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="e0771-125">To determine a console's current input code page, use the [**GetConsoleCP**](getconsolecp.md) function.</span></span> <span data-ttu-id="e0771-126">Zum Festlegen und Abrufen der Ausgabe Codepage einer Konsole verwenden Sie die Funktionen [**setconsoleoutputcp**](setconsoleoutputcp.md) und [**getconsoleoutputcp**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="e0771-126">To set and retrieve a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0771-127">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e0771-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e0771-128">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="e0771-128">Minimum supported client</span></span> | <span data-ttu-id="e0771-129">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="e0771-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e0771-130">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="e0771-130">Minimum supported server</span></span> | <span data-ttu-id="e0771-131">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="e0771-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e0771-132">Header</span><span class="sxs-lookup"><span data-stu-id="e0771-132">Header</span></span> | <span data-ttu-id="e0771-133">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e0771-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e0771-134">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e0771-134">Library</span></span> | <span data-ttu-id="e0771-135">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="e0771-135">Kernel32.lib</span></span> |
| <span data-ttu-id="e0771-136">DLL</span><span class="sxs-lookup"><span data-stu-id="e0771-136">DLL</span></span> | <span data-ttu-id="e0771-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e0771-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e0771-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e0771-138">See also</span></span>

[<span data-ttu-id="e0771-139">Konsolen-Codepages</span><span class="sxs-lookup"><span data-stu-id="e0771-139">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="e0771-140">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="e0771-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e0771-141">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="e0771-141">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="e0771-142">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="e0771-142">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="e0771-143">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="e0771-143">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)