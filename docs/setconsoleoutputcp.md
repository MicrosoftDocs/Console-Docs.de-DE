---
title: Setconsoleoutputcp-Funktion
description: Legt die Ausgabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: ae1f3970af6c8db1ebedc29e0644ed001258ecc5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060502"
---
# <a name="setconsoleoutputcp-function"></a><span data-ttu-id="d1d4c-104">Setconsoleoutputcp-Funktion</span><span class="sxs-lookup"><span data-stu-id="d1d4c-104">SetConsoleOutputCP function</span></span>


<span data-ttu-id="d1d4c-105">Legt die Ausgabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-105">Sets the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="d1d4c-106">Eine-Konsole verwendet Ihre Ausgabe Codepage, um die von den verschiedenen Ausgabefunktionen geschriebenen Zeichen Werte in die im Konsolenfenster angezeigten Bilder zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

<a name="syntax"></a><span data-ttu-id="d1d4c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1d4c-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a><span data-ttu-id="d1d4c-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="d1d4c-108">Parameters</span></span>
----------

<span data-ttu-id="d1d4c-109">*wcodepageid* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d1d4c-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="d1d4c-110">Der Bezeichner der festzulegenden Codepage.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-110">The identifier of the code page to set.</span></span> <span data-ttu-id="d1d4c-111">Weitere Informationen finden Sie in den Hinweisen.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-111">For more information, see Remarks.</span></span>

<a name="return-value"></a><span data-ttu-id="d1d4c-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="d1d4c-112">Return value</span></span>
------------

<span data-ttu-id="d1d4c-113">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="d1d4c-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d1d4c-114">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d1d4c-115">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="d1d4c-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="d1d4c-116">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d1d4c-116">Remarks</span></span>
-------

<span data-ttu-id="d1d4c-117">Eine Codepage ordnet 256 Zeichen Codes einzelnen Zeichen zu.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="d1d4c-118">Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="d1d4c-119">Wenn die aktuelle Schriftart eine Unicode-Schriftart mit fester Größe ist, ändert **setconsoleoutputcp** die Zuordnung der Zeichen Werte in den Glyphe-Satz der Schriftart, anstatt jedes Mal, wenn Sie aufgerufen wird, eine separate Schriftart zu laden.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-119">If the current font is a fixed-pitch Unicode font, **SetConsoleOutputCP** changes the mapping of the character values into the glyph set of the font, rather than loading a separate font each time it is called.</span></span> <span data-ttu-id="d1d4c-120">Dies wirkt sich darauf aus, wie erweiterte Zeichen (ASCII-Wert größer als 127) in einem Konsolenfenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-120">This affects how extended characters (ASCII value greater than 127) are displayed in a console window.</span></span> <span data-ttu-id="d1d4c-121">Wenn es sich bei der aktuellen Schriftart jedoch um eine Raster Schriftart handelt, wirkt sich **setconsoleoutputcp** nicht darauf aus, wie erweiterte Zeichen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-121">However, if the current font is a raster font, **SetConsoleOutputCP** does not affect how extended characters are displayed.</span></span>

<span data-ttu-id="d1d4c-122">Verwenden Sie die Funktion " [enumsystemcodepages](https://go.microsoft.com/fwlink/p/?linkid=178051) ", um die Codepages zu suchen, die vom Betriebssystem installiert oder unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-122">To find the code pages that are installed or supported by the operating system, use the [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) function.</span></span> <span data-ttu-id="d1d4c-123">Die Bezeichner der auf dem lokalen Computer verfügbaren Codepages werden auch in der Registrierung unter folgendem Schlüssel gespeichert:</span><span class="sxs-lookup"><span data-stu-id="d1d4c-123">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

<span data-ttu-id="d1d4c-124">**HKEY \_ local \_ Machine \\ System \\ CurrentControlSet \\ Control \\ nls \\ Codepage**</span><span class="sxs-lookup"><span data-stu-id="d1d4c-124">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="d1d4c-125">Es ist jedoch besser, mit [enumsystemcodepages Codepages](https://go.microsoft.com/fwlink/p/?linkid=178051) aufzuzählen, da sich die Registrierung in verschiedenen Versionen von Windows unterscheiden kann.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-125">However, it is better to use [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>
<span data-ttu-id="d1d4c-126">Verwenden Sie die [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) -Funktion, um zu bestimmen, ob eine bestimmte Codepage gültig ist.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-126">To determine whether a particular code page is valid, use the [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) function.</span></span> <span data-ttu-id="d1d4c-127">Verwenden Sie die [**getcpinfoex**](https://msdn.microsoft.com/library/windows/desktop/dd318081) -Funktion, um weitere Informationen über eine Codepage einschließlich Ihres Namens abzurufen.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-127">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="d1d4c-128">Eine Liste der verfügbaren Code Page Bezeichner finden Sie unter [Code Page Identifier](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="d1d4c-128">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="d1d4c-129">Verwenden Sie die [**getconsoleoutputcp**](getconsoleoutputcp.md) -Funktion, um die aktuelle Ausgabe Codepage einer Konsole zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="d1d4c-129">To determine a console's current output code page, use the [**GetConsoleOutputCP**](getconsoleoutputcp.md) function.</span></span> <span data-ttu-id="d1d4c-130">Um die Eingabe Codepage einer Konsole festzulegen und abzurufen, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) und [**getconsolecp**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="d1d4c-130">To set and retrieve a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="d1d4c-131">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="d1d4c-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="d1d4c-132">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="d1d4c-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="d1d4c-133">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="d1d4c-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d1d4c-134">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="d1d4c-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="d1d4c-135">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="d1d4c-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d1d4c-136">Header</span><span class="sxs-lookup"><span data-stu-id="d1d4c-136">Header</span></span></p></td>
<td><span data-ttu-id="d1d4c-137">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d1d4c-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d1d4c-138">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="d1d4c-138">Library</span></span></p></td>
<td><span data-ttu-id="d1d4c-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d1d4c-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d1d4c-140">DLL</span><span class="sxs-lookup"><span data-stu-id="d1d4c-140">DLL</span></span></p></td>
<td><span data-ttu-id="d1d4c-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d1d4c-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="d1d4c-142"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d1d4c-142"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="d1d4c-143">Konsolen Codepages</span><span class="sxs-lookup"><span data-stu-id="d1d4c-143">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="d1d4c-144">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="d1d4c-144">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d1d4c-145">**Getconsolecp**</span><span class="sxs-lookup"><span data-stu-id="d1d4c-145">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="d1d4c-146">**Getconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="d1d4c-146">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="d1d4c-147">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="d1d4c-147">**SetConsoleCP**</span></span>](setconsolecp.md)

 

 




