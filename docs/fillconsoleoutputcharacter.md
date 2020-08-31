---
title: Fillconsoleoutputcharacter-Funktion
description: Schreibt ein Zeichen so oft wie angegeben in den Konsolenbildschirm Puffer, beginnend bei den angegebenen Koordinaten.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d11e0ef196f9923f1478e17faacd41b43a0511eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059883"
---
# <a name="fillconsoleoutputcharacter-function"></a><span data-ttu-id="5a686-104">Fillconsoleoutputcharacter-Funktion</span><span class="sxs-lookup"><span data-stu-id="5a686-104">FillConsoleOutputCharacter function</span></span>


<span data-ttu-id="5a686-105">Schreibt ein Zeichen so oft wie angegeben in den Konsolenbildschirm Puffer, beginnend bei den angegebenen Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="5a686-105">Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.</span></span>

<a name="syntax"></a><span data-ttu-id="5a686-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5a686-106">Syntax</span></span>
------

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a><span data-ttu-id="5a686-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="5a686-107">Parameters</span></span>
----------

<span data-ttu-id="5a686-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5a686-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="5a686-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="5a686-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="5a686-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="5a686-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="5a686-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="5a686-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="5a686-112">*ccharacter* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5a686-112">*cCharacter* \[in\]</span></span>  
<span data-ttu-id="5a686-113">Das Zeichen, das in den Konsolenbildschirm Puffer geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="5a686-113">The character to be written to the console screen buffer.</span></span>

<span data-ttu-id="5a686-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5a686-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="5a686-115">Die Anzahl der Zeichen Zellen, in die das Zeichen geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="5a686-115">The number of character cells to which the character should be written.</span></span>

<span data-ttu-id="5a686-116">*dwschreitecoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5a686-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="5a686-117">Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle angibt, in die das Zeichen geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="5a686-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.</span></span>

<span data-ttu-id="5a686-118">*lpnumofcharswritten* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="5a686-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="5a686-119">Ein Zeiger auf eine Variable, die die Anzahl der Zeichen empfängt, die tatsächlich in den Konsolenbildschirm Puffer geschrieben wurden.</span><span class="sxs-lookup"><span data-stu-id="5a686-119">A pointer to a variable that receives the number of characters actually written to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="5a686-120">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5a686-120">Return value</span></span>
------------

<span data-ttu-id="5a686-121">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="5a686-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="5a686-122">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="5a686-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="5a686-123">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="5a686-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="5a686-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5a686-124">Remarks</span></span>
-------

<span data-ttu-id="5a686-125">Wenn die Anzahl der Zeichen, die in geschrieben werden sollen, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden Zeichen in die nächste Zeile geschrieben.</span><span class="sxs-lookup"><span data-stu-id="5a686-125">If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="5a686-126">Wenn die Anzahl der Zeichen, in die geschrieben wird, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Zeichen bis zum Ende des Bildschirm Puffers der Konsole geschrieben.</span><span class="sxs-lookup"><span data-stu-id="5a686-126">If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="5a686-127">Die Attributwerte an den geschriebenen Positionen werden nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="5a686-127">The attribute values at the positions written are not changed.</span></span>

<span data-ttu-id="5a686-128">Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole.</span><span class="sxs-lookup"><span data-stu-id="5a686-128">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="5a686-129">Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt.</span><span class="sxs-lookup"><span data-stu-id="5a686-129">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="5a686-130">Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="5a686-130">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="5a686-131">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5a686-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="5a686-132">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="5a686-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="5a686-133">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="5a686-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5a686-134">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="5a686-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="5a686-135">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="5a686-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5a686-136">Header</span><span class="sxs-lookup"><span data-stu-id="5a686-136">Header</span></span></p></td>
<td><span data-ttu-id="5a686-137">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5a686-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5a686-138">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="5a686-138">Library</span></span></p></td>
<td><span data-ttu-id="5a686-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="5a686-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5a686-140">DLL</span><span class="sxs-lookup"><span data-stu-id="5a686-140">DLL</span></span></p></td>
<td><span data-ttu-id="5a686-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5a686-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5a686-142">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="5a686-142">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="5a686-143"><strong>Fillconsoleoutputcharakteriw</strong> (Unicode) und <strong>fillconsoleoutputcharakteria</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="5a686-143"><strong>FillConsoleOutputCharacterW</strong> (Unicode) and <strong>FillConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="5a686-144"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5a686-144"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="5a686-145">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="5a686-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5a686-146">**Koord**</span><span class="sxs-lookup"><span data-stu-id="5a686-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="5a686-147">**Fillconsoleoutputattribute**</span><span class="sxs-lookup"><span data-stu-id="5a686-147">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="5a686-148">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="5a686-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="5a686-149">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="5a686-149">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="5a686-150">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="5a686-150">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="5a686-151">**Schreibconsoleoutputcharacter**</span><span class="sxs-lookup"><span data-stu-id="5a686-151">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




