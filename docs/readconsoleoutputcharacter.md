---
title: "\"Read consoleoutputcharacter\"-Funktion"
description: Kopiert eine Anzahl von Zeichen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/ReadConsoleOutputCharacter
- wincon/ReadConsoleOutputCharacter
- ReadConsoleOutputCharacter
- consoleapi2/ReadConsoleOutputCharacterA
- wincon/ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterA
- consoleapi2/ReadConsoleOutputCharacterW
- wincon/ReadConsoleOutputCharacterW
- ReadConsoleOutputCharacterW
MS-HAID:
- '\_win32\_readconsoleoutputcharacter'
- base.readconsoleoutputcharacter
- consoles.readconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f47464a9-6c59-4f15-abd0-be29ab515698
topic_type:
- apiref
api_name:
- ReadConsoleOutputCharacter
- ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8f761d10951e6df77a54fd075c29379657204a99
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060363"
---
# <a name="readconsoleoutputcharacter-function"></a><span data-ttu-id="abbf5-104">"Read consoleoutputcharacter"-Funktion</span><span class="sxs-lookup"><span data-stu-id="abbf5-104">ReadConsoleOutputCharacter function</span></span>


<span data-ttu-id="abbf5-105">Kopiert eine Anzahl von Zeichen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="abbf5-105">Copies a number of characters from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="abbf5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="abbf5-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

<a name="parameters"></a><span data-ttu-id="abbf5-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="abbf5-107">Parameters</span></span>
----------

<span data-ttu-id="abbf5-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="abbf5-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="abbf5-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="abbf5-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="abbf5-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="abbf5-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="abbf5-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="abbf5-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="abbf5-112">*lpcharacter* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="abbf5-112">*lpCharacter* \[out\]</span></span>  
<span data-ttu-id="abbf5-113">Ein Zeiger auf einen Puffer, der die aus dem Konsolenbildschirm Puffer gelesenen Zeichen empfängt.</span><span class="sxs-lookup"><span data-stu-id="abbf5-113">A pointer to a buffer that receives the characters read from the console screen buffer.</span></span>

<span data-ttu-id="abbf5-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="abbf5-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="abbf5-115">Die Anzahl der zu lesenden Zeichen Zellen des Bildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="abbf5-115">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="abbf5-116">Die Größe des Puffers, auf den der *lpcharacter* -Parameter verweist, sollte lauten `nLength * sizeof(TCHAR)` .</span><span class="sxs-lookup"><span data-stu-id="abbf5-116">The size of the buffer pointed to by the *lpCharacter* parameter should be `nLength * sizeof(TCHAR)`.</span></span>

<span data-ttu-id="abbf5-117">*dwumkoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="abbf5-117">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="abbf5-118">Die Koordinaten der ersten Zelle im Konsolenbildschirm Puffer, von der in Zeichen gelesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="abbf5-118">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="abbf5-119">Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die-Spalte, und der **Y** -Member ist die Zeile.</span><span class="sxs-lookup"><span data-stu-id="abbf5-119">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="abbf5-120">*lpnumofcharsread* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="abbf5-120">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="abbf5-121">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich gelesenen Zeichen empfängt.</span><span class="sxs-lookup"><span data-stu-id="abbf5-121">A pointer to a variable that receives the number of characters actually read.</span></span>

<a name="return-value"></a><span data-ttu-id="abbf5-122">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="abbf5-122">Return value</span></span>
------------

<span data-ttu-id="abbf5-123">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="abbf5-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="abbf5-124">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="abbf5-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="abbf5-125">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="abbf5-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="abbf5-126">Hinweise</span><span class="sxs-lookup"><span data-stu-id="abbf5-126">Remarks</span></span>
-------

<span data-ttu-id="abbf5-127">Wenn sich die Anzahl der zu lesenden Zeichen über das Ende der angegebenen Bildschirm Puffer Zeile hinaus erstreckt, werden Zeichen aus der nächsten Zeile gelesen.</span><span class="sxs-lookup"><span data-stu-id="abbf5-127">If the number of characters to be read from extends beyond the end of the specified screen buffer row, characters are read from the next row.</span></span> <span data-ttu-id="abbf5-128">Wenn die Anzahl der zu lesenden Zeichen über das Ende des Konsolenbildschirm Puffers hinausgeht, werden Zeichen bis zum Ende des Konsolenbildschirm Puffers gelesen.</span><span class="sxs-lookup"><span data-stu-id="abbf5-128">If the number of characters to be read from extends beyond the end of the console screen buffer, characters up to the end of the console screen buffer are read.</span></span>

<span data-ttu-id="abbf5-129">Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole.</span><span class="sxs-lookup"><span data-stu-id="abbf5-129">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="abbf5-130">Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt.</span><span class="sxs-lookup"><span data-stu-id="abbf5-130">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="abbf5-131">Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="abbf5-131">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="abbf5-132">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="abbf5-132">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="abbf5-133">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="abbf5-133">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="abbf5-134">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="abbf5-134">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="abbf5-135">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="abbf5-135">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="abbf5-136">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="abbf5-136">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="abbf5-137">Header</span><span class="sxs-lookup"><span data-stu-id="abbf5-137">Header</span></span></p></td>
<td><span data-ttu-id="abbf5-138">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="abbf5-138">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="abbf5-139">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="abbf5-139">Library</span></span></p></td>
<td><span data-ttu-id="abbf5-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="abbf5-140">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="abbf5-141">DLL</span><span class="sxs-lookup"><span data-stu-id="abbf5-141">DLL</span></span></p></td>
<td><span data-ttu-id="abbf5-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="abbf5-142">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="abbf5-143">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="abbf5-143">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="abbf5-144">"Read <strong>consoleoutputcharakteriw</strong> (Unicode)" und "read <strong>consoleoutputcharaka</strong> (ANSI)"</span><span class="sxs-lookup"><span data-stu-id="abbf5-144"><strong>ReadConsoleOutputCharacterW</strong> (Unicode) and <strong>ReadConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="abbf5-145"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="abbf5-145"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="abbf5-146">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="abbf5-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="abbf5-147">**Koord**</span><span class="sxs-lookup"><span data-stu-id="abbf5-147">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="abbf5-148">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="abbf5-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="abbf5-149">**"Read consoleoutput"**</span><span class="sxs-lookup"><span data-stu-id="abbf5-149">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="abbf5-150">**"Read consoleoutputattribute"**</span><span class="sxs-lookup"><span data-stu-id="abbf5-150">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="abbf5-151">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="abbf5-151">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="abbf5-152">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="abbf5-152">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="abbf5-153">**Schreibconsoleoutput**</span><span class="sxs-lookup"><span data-stu-id="abbf5-153">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="abbf5-154">**"Schreibconsoleoutputattribute"**</span><span class="sxs-lookup"><span data-stu-id="abbf5-154">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="abbf5-155">**Schreibconsoleoutputcharacter**</span><span class="sxs-lookup"><span data-stu-id="abbf5-155">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




