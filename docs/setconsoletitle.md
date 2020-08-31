---
title: Setconsoletitle-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur setconsoletitle-Funktion, mit der der Titel für das aktuelle Konsolenfenster festgelegt wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleTitle
- wincon/SetConsoleTitle
- SetConsoleTitle
- consoleapi2/SetConsoleTitleA
- wincon/SetConsoleTitleA
- SetConsoleTitleA
- consoleapi2/SetConsoleTitleW
- wincon/SetConsoleTitleW
- SetConsoleTitleW
MS-HAID:
- '\_win32\_setconsoletitle'
- base.setconsoletitle
- consoles.setconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1db449b-0dd0-4d61-bb79-b7da9a5168f4
topic_type:
- apiref
api_name:
- SetConsoleTitle
- SetConsoleTitleA
- SetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: e1789243fd5c184221dd53038d8ec87c9b010749
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060484"
---
# <a name="setconsoletitle-function"></a><span data-ttu-id="f9b18-104">Setconsoletitle-Funktion</span><span class="sxs-lookup"><span data-stu-id="f9b18-104">SetConsoleTitle function</span></span>


<span data-ttu-id="f9b18-105">Legt den Titel für das aktuelle Konsolenfenster fest.</span><span class="sxs-lookup"><span data-stu-id="f9b18-105">Sets the title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="f9b18-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9b18-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

<a name="parameters"></a><span data-ttu-id="f9b18-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="f9b18-107">Parameters</span></span>
----------

<span data-ttu-id="f9b18-108">*lpconsoletitle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f9b18-108">*lpConsoleTitle* \[in\]</span></span>  
<span data-ttu-id="f9b18-109">Die Zeichenfolge, die in der Titelleiste des Konsolenfensters angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="f9b18-109">The string to be displayed in the title bar of the console window.</span></span> <span data-ttu-id="f9b18-110">Die Gesamtgröße muss kleiner als 64K sein.</span><span class="sxs-lookup"><span data-stu-id="f9b18-110">The total size must be less than 64K.</span></span>

<a name="return-value"></a><span data-ttu-id="f9b18-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="f9b18-111">Return value</span></span>
------------

<span data-ttu-id="f9b18-112">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="f9b18-112">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f9b18-113">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="f9b18-113">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f9b18-114">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="f9b18-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="f9b18-115">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f9b18-115">Remarks</span></span>
-------

<span data-ttu-id="f9b18-116">Wenn der Prozess beendet wird, stellt das System den ursprünglichen Konsolentitel wieder her.</span><span class="sxs-lookup"><span data-stu-id="f9b18-116">When the process terminates, the system restores the original console title.</span></span>

<span data-ttu-id="f9b18-117">Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole.</span><span class="sxs-lookup"><span data-stu-id="f9b18-117">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="f9b18-118">Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt.</span><span class="sxs-lookup"><span data-stu-id="f9b18-118">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="f9b18-119">Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="f9b18-119">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="f9b18-120">Beispiele</span><span class="sxs-lookup"><span data-stu-id="f9b18-120">Examples</span></span>
--------

<span data-ttu-id="f9b18-121">Im folgenden Beispiel wird gezeigt, wie der Konsolentitel abgerufen und geändert wird.</span><span class="sxs-lookup"><span data-stu-id="f9b18-121">The following example shows how to retrieve and modify the console title.</span></span>

```C
#include <windows.h>
#include <tchar.h>
#include <conio.h>
#include <strsafe.h>

int main( void )
{
   TCHAR szOldTitle[MAX_PATH];
   TCHAR szNewTitle[MAX_PATH];

   // Save current console title.

   if( GetConsoleTitle(szOldTitle, MAX_PATH) )
   {
      // Build new console title string.

      StringCchPrintf(szNewTitle, MAX_PATH, TEXT("TEST: %s"), szOldTitle);

      // Set console title to new title
      if( !SetConsoleTitle(szNewTitle) )
      {
         _tprintf(TEXT("SetConsoleTitle failed (%d)\n"), GetLastError());
         return 1;
      }
      else
      {
         _tprintf(TEXT("SetConsoleTitle succeeded.\n"));
      }
   }
   return 0;
}
```

<a name="requirements"></a><span data-ttu-id="f9b18-122">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f9b18-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f9b18-123">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="f9b18-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f9b18-124">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="f9b18-124">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f9b18-125">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="f9b18-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f9b18-126">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="f9b18-126">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f9b18-127">Header</span><span class="sxs-lookup"><span data-stu-id="f9b18-127">Header</span></span></p></td>
<td><span data-ttu-id="f9b18-128">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f9b18-128">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f9b18-129">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="f9b18-129">Library</span></span></p></td>
<td><span data-ttu-id="f9b18-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="f9b18-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f9b18-131">DLL</span><span class="sxs-lookup"><span data-stu-id="f9b18-131">DLL</span></span></p></td>
<td><span data-ttu-id="f9b18-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f9b18-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f9b18-133">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="f9b18-133">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="f9b18-134"><strong>Setconsoletitlew</strong> (Unicode) und <strong>setconsoletitlea</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="f9b18-134"><strong>SetConsoleTitleW</strong> (Unicode) and <strong>SetConsoleTitleA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f9b18-135"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f9b18-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f9b18-136">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="f9b18-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f9b18-137">**Getconsoleoriginaltitle**</span><span class="sxs-lookup"><span data-stu-id="f9b18-137">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="f9b18-138">**Getconsoletitle**</span><span class="sxs-lookup"><span data-stu-id="f9b18-138">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="f9b18-139">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="f9b18-139">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="f9b18-140">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="f9b18-140">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 




