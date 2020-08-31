---
title: Schreibconsoleoutputcharacter-Funktion
description: Kopiert eine Anzahl von Zeichen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/WriteConsoleOutputCharacter
- wincon/WriteConsoleOutputCharacter
- WriteConsoleOutputCharacter
- consoleapi2/WriteConsoleOutputCharacterA
- wincon/WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterA
- consoleapi2/WriteConsoleOutputCharacterW
- wincon/WriteConsoleOutputCharacterW
- WriteConsoleOutputCharacterW
MS-HAID:
- '\_win32\_writeconsoleoutputcharacter'
- base.writeconsoleoutputcharacter
- consoles.writeconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7cc935ea-6b19-4494-b746-259aa7aaa9cc
topic_type:
- apiref
api_name:
- WriteConsoleOutputCharacter
- WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: bc313abbcb28016968355cc405e0cc2de3d36cb0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060472"
---
# <a name="writeconsoleoutputcharacter-function"></a><span data-ttu-id="0b93d-104">Schreibconsoleoutputcharacter-Funktion</span><span class="sxs-lookup"><span data-stu-id="0b93d-104">WriteConsoleOutputCharacter function</span></span>


<span data-ttu-id="0b93d-105">Kopiert eine Anzahl von Zeichen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="0b93d-105">Copies a number of characters to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="0b93d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b93d-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a><span data-ttu-id="0b93d-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="0b93d-107">Parameters</span></span>
----------

<span data-ttu-id="0b93d-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0b93d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="0b93d-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="0b93d-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="0b93d-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="0b93d-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="0b93d-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="0b93d-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="0b93d-112">*lpcharacter* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0b93d-112">*lpCharacter* \[in\]</span></span>  
<span data-ttu-id="0b93d-113">Die Zeichen, die in den Konsolenbildschirm Puffer geschrieben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="0b93d-113">The characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="0b93d-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0b93d-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="0b93d-115">Die Anzahl der zu schreibenden Zeichen.</span><span class="sxs-lookup"><span data-stu-id="0b93d-115">The number of characters to be written.</span></span>

<span data-ttu-id="0b93d-116">*dwschreitecoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0b93d-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="0b93d-117">Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle im Konsolenbildschirm Puffer angibt, in die Zeichen geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="0b93d-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which characters will be written.</span></span>

<span data-ttu-id="0b93d-118">*lpnumofcharswritten* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="0b93d-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="0b93d-119">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Zeichen empfängt.</span><span class="sxs-lookup"><span data-stu-id="0b93d-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<a name="return-value"></a><span data-ttu-id="0b93d-120">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="0b93d-120">Return value</span></span>
------------

<span data-ttu-id="0b93d-121">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="0b93d-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0b93d-122">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="0b93d-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0b93d-123">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="0b93d-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="0b93d-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0b93d-124">Remarks</span></span>
-------

<span data-ttu-id="0b93d-125">Wenn die Anzahl der Zeichen, in die geschrieben werden soll, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden Zeichen in die nächste Zeile geschrieben.</span><span class="sxs-lookup"><span data-stu-id="0b93d-125">If the number of characters to be written to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="0b93d-126">Wenn die Anzahl der Zeichen, in die geschrieben werden soll, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden Zeichen bis zum Ende des Bildschirm Puffers der Konsole geschrieben.</span><span class="sxs-lookup"><span data-stu-id="0b93d-126">If the number of characters to be written to extends beyond the end of the console screen buffer, characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="0b93d-127">Die Attributwerte an den Positionen, die in geschrieben werden, werden nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="0b93d-127">The attribute values at the positions written to are not changed.</span></span>

<span data-ttu-id="0b93d-128">Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole.</span><span class="sxs-lookup"><span data-stu-id="0b93d-128">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="0b93d-129">Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt.</span><span class="sxs-lookup"><span data-stu-id="0b93d-129">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="0b93d-130">Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="0b93d-130">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="0b93d-131">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0b93d-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0b93d-132">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="0b93d-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0b93d-133">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="0b93d-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0b93d-134">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="0b93d-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0b93d-135">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="0b93d-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0b93d-136">Header</span><span class="sxs-lookup"><span data-stu-id="0b93d-136">Header</span></span></p></td>
<td><span data-ttu-id="0b93d-137">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0b93d-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0b93d-138">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="0b93d-138">Library</span></span></p></td>
<td><span data-ttu-id="0b93d-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="0b93d-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0b93d-140">DLL</span><span class="sxs-lookup"><span data-stu-id="0b93d-140">DLL</span></span></p></td>
<td><span data-ttu-id="0b93d-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0b93d-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0b93d-142">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="0b93d-142">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="0b93d-143">" <strong>Schreibconsoleoutputcharakteriw</strong> (Unicode)" und " <strong>Write Message consoleoutputcharakteria</strong> (ANSI)"</span><span class="sxs-lookup"><span data-stu-id="0b93d-143"><strong>WriteConsoleOutputCharacterW</strong> (Unicode) and <strong>WriteConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0b93d-144"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0b93d-144"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0b93d-145">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="0b93d-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0b93d-146">**Koord**</span><span class="sxs-lookup"><span data-stu-id="0b93d-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="0b93d-147">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="0b93d-147">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="0b93d-148">**"Read consoleoutput"**</span><span class="sxs-lookup"><span data-stu-id="0b93d-148">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="0b93d-149">**"Read consoleoutputattribute"**</span><span class="sxs-lookup"><span data-stu-id="0b93d-149">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="0b93d-150">**"Read consoleoutputcharacter"**</span><span class="sxs-lookup"><span data-stu-id="0b93d-150">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="0b93d-151">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="0b93d-151">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="0b93d-152">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="0b93d-152">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="0b93d-153">**Schreibconsoleoutput**</span><span class="sxs-lookup"><span data-stu-id="0b93d-153">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="0b93d-154">**"Schreibconsoleoutputattribute"**</span><span class="sxs-lookup"><span data-stu-id="0b93d-154">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

 

 




