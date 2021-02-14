---
title: Setconsoleoutputcp-Funktion
description: Legt die Ausgabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: abe04e2be5256097e19742bfbc8566c3ab613c4d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357520"
---
# <a name="setconsoleoutputcp-function"></a><span data-ttu-id="a8035-104">Setconsoleoutputcp-Funktion</span><span class="sxs-lookup"><span data-stu-id="a8035-104">SetConsoleOutputCP function</span></span>

<span data-ttu-id="a8035-105">Legt die Ausgabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="a8035-105">Sets the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="a8035-106">Eine-Konsole verwendet Ihre Ausgabe Codepage, um die von den verschiedenen Ausgabefunktionen geschriebenen Zeichen Werte in die im Konsolenfenster angezeigten Bilder zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="a8035-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8035-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a8035-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a><span data-ttu-id="a8035-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="a8035-108">Parameters</span></span>

<span data-ttu-id="a8035-109">*wcodepageid* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="a8035-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="a8035-110">Der Bezeichner der festzulegenden Codepage.</span><span class="sxs-lookup"><span data-stu-id="a8035-110">The identifier of the code page to set.</span></span> <span data-ttu-id="a8035-111">Weitere Informationen finden Sie in den Hinweisen.</span><span class="sxs-lookup"><span data-stu-id="a8035-111">For more information, see Remarks.</span></span>

## <a name="return-value"></a><span data-ttu-id="a8035-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="a8035-112">Return value</span></span>

<span data-ttu-id="a8035-113">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="a8035-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="a8035-114">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="a8035-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="a8035-115">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="a8035-115">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="a8035-116">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="a8035-116">Remarks</span></span>

<span data-ttu-id="a8035-117">Eine Codepage ordnet 256 Zeichen Codes einzelnen Zeichen zu.</span><span class="sxs-lookup"><span data-stu-id="a8035-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="a8035-118">Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="a8035-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="a8035-119">Wenn die aktuelle Schriftart eine Unicode-Schriftart mit fester Größe ist, ändert **setconsoleoutputcp** die Zuordnung der Zeichen Werte in den Glyphe-Satz der Schriftart, anstatt jedes Mal, wenn Sie aufgerufen wird, eine separate Schriftart zu laden.</span><span class="sxs-lookup"><span data-stu-id="a8035-119">If the current font is a fixed-pitch Unicode font, **SetConsoleOutputCP** changes the mapping of the character values into the glyph set of the font, rather than loading a separate font each time it is called.</span></span> <span data-ttu-id="a8035-120">Dies wirkt sich darauf aus, wie erweiterte Zeichen (ASCII-Wert größer als 127) in einem Konsolenfenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a8035-120">This affects how extended characters (ASCII value greater than 127) are displayed in a console window.</span></span> <span data-ttu-id="a8035-121">Wenn es sich bei der aktuellen Schriftart jedoch um eine Raster Schriftart handelt, wirkt sich **setconsoleoutputcp** nicht darauf aus, wie erweiterte Zeichen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a8035-121">However, if the current font is a raster font, **SetConsoleOutputCP** does not affect how extended characters are displayed.</span></span>

<span data-ttu-id="a8035-122">Verwenden Sie die Funktion " [enumsystemcodepages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) ", um die Codepages zu suchen, die vom Betriebssystem installiert oder unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="a8035-122">To find the code pages that are installed or supported by the operating system, use the [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) function.</span></span> <span data-ttu-id="a8035-123">Die Bezeichner der auf dem lokalen Computer verfügbaren Codepages werden auch in der Registrierung unter folgendem Schlüssel gespeichert:</span><span class="sxs-lookup"><span data-stu-id="a8035-123">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

<span data-ttu-id="a8035-124">Es ist jedoch besser, mit [enumsystemcodepages Codepages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) aufzuzählen, da sich die Registrierung in verschiedenen Versionen von Windows unterscheiden kann.</span><span class="sxs-lookup"><span data-stu-id="a8035-124">However, it is better to use [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>
<span data-ttu-id="a8035-125">Verwenden Sie die [IsValidCodePage](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) -Funktion, um zu bestimmen, ob eine bestimmte Codepage gültig ist.</span><span class="sxs-lookup"><span data-stu-id="a8035-125">To determine whether a particular code page is valid, use the [IsValidCodePage](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) function.</span></span> <span data-ttu-id="a8035-126">Verwenden Sie die [**getcpinfoex**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) -Funktion, um weitere Informationen über eine Codepage einschließlich Ihres Namens abzurufen.</span><span class="sxs-lookup"><span data-stu-id="a8035-126">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span> <span data-ttu-id="a8035-127">Eine Liste der verfügbaren Code Page Bezeichner finden Sie unter [Code Page Identifier](/windows/win32/intl/code-page-identifiers).</span><span class="sxs-lookup"><span data-stu-id="a8035-127">For a list of available code page identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="a8035-128">Verwenden Sie die [**getconsoleoutputcp**](getconsoleoutputcp.md) -Funktion, um die aktuelle Ausgabe Codepage einer Konsole zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="a8035-128">To determine a console's current output code page, use the [**GetConsoleOutputCP**](getconsoleoutputcp.md) function.</span></span> <span data-ttu-id="a8035-129">Um die Eingabe Codepage einer Konsole festzulegen und abzurufen, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) und [**getconsolecp**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="a8035-129">To set and retrieve a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8035-130">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="a8035-130">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="a8035-131">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="a8035-131">Minimum supported client</span></span> | <span data-ttu-id="a8035-132">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="a8035-132">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="a8035-133">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="a8035-133">Minimum supported server</span></span> | <span data-ttu-id="a8035-134">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="a8035-134">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="a8035-135">Header</span><span class="sxs-lookup"><span data-stu-id="a8035-135">Header</span></span> | <span data-ttu-id="a8035-136">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a8035-136">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="a8035-137">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="a8035-137">Library</span></span> | <span data-ttu-id="a8035-138">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="a8035-138">Kernel32.lib</span></span> |
| <span data-ttu-id="a8035-139">DLL</span><span class="sxs-lookup"><span data-stu-id="a8035-139">DLL</span></span> | <span data-ttu-id="a8035-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="a8035-140">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="a8035-141">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a8035-141">See also</span></span>

[<span data-ttu-id="a8035-142">Konsolen-Codepages</span><span class="sxs-lookup"><span data-stu-id="a8035-142">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="a8035-143">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="a8035-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="a8035-144">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="a8035-144">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="a8035-145">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="a8035-145">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="a8035-146">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="a8035-146">**SetConsoleCP**</span></span>](setconsolecp.md)