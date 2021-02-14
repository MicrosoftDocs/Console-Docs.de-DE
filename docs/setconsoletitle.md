---
title: Setconsoletitle-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur setconsoletitle-Funktion, mit der der Titel für das aktuelle Konsolenfenster festgelegt wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 5955bba0c7b317dbcdbc9593b60bfb3092376dc1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358540"
---
# <a name="setconsoletitle-function"></a><span data-ttu-id="617d0-104">Setconsoletitle-Funktion</span><span class="sxs-lookup"><span data-stu-id="617d0-104">SetConsoleTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="617d0-105">Legt den Titel für das aktuelle Konsolenfenster fest.</span><span class="sxs-lookup"><span data-stu-id="617d0-105">Sets the title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="617d0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="617d0-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

## <a name="parameters"></a><span data-ttu-id="617d0-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="617d0-107">Parameters</span></span>

<span data-ttu-id="617d0-108">*lpconsoletitle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="617d0-108">*lpConsoleTitle* \[in\]</span></span>  
<span data-ttu-id="617d0-109">Die Zeichenfolge, die in der Titelleiste des Konsolenfensters angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="617d0-109">The string to be displayed in the title bar of the console window.</span></span> <span data-ttu-id="617d0-110">Die Gesamtgröße muss kleiner als 64K sein.</span><span class="sxs-lookup"><span data-stu-id="617d0-110">The total size must be less than 64K.</span></span>

## <a name="return-value"></a><span data-ttu-id="617d0-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="617d0-111">Return value</span></span>

<span data-ttu-id="617d0-112">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="617d0-112">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="617d0-113">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="617d0-113">If the function fails, the return value is zero.</span></span> <span data-ttu-id="617d0-114">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="617d0-114">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="617d0-115">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="617d0-115">Remarks</span></span>

<span data-ttu-id="617d0-116">Wenn der Prozess beendet wird, stellt das System den ursprünglichen Konsolentitel wieder her.</span><span class="sxs-lookup"><span data-stu-id="617d0-116">When the process terminates, the system restores the original console title.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="617d0-117">Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent in den **[Fenstertitel](console-virtual-terminal-sequences.md#window-title)** Sequenzen.</span><span class="sxs-lookup"><span data-stu-id="617d0-117">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[window title](console-virtual-terminal-sequences.md#window-title)** sequences.</span></span> <span data-ttu-id="617d0-118">_Virtuelle Terminal Sequenzen_ werden für alle neuen und laufenden Entwicklungen empfohlen.</span><span class="sxs-lookup"><span data-stu-id="617d0-118">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="617d0-119">Beispiele</span><span class="sxs-lookup"><span data-stu-id="617d0-119">Examples</span></span>

<span data-ttu-id="617d0-120">Im folgenden Beispiel wird gezeigt, wie der Konsolentitel abgerufen und geändert wird.</span><span class="sxs-lookup"><span data-stu-id="617d0-120">The following example shows how to retrieve and modify the console title.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="617d0-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="617d0-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="617d0-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="617d0-122">Minimum supported client</span></span> | <span data-ttu-id="617d0-123">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="617d0-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="617d0-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="617d0-124">Minimum supported server</span></span> | <span data-ttu-id="617d0-125">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="617d0-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="617d0-126">Header</span><span class="sxs-lookup"><span data-stu-id="617d0-126">Header</span></span> | <span data-ttu-id="617d0-127">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="617d0-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="617d0-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="617d0-128">Library</span></span> | <span data-ttu-id="617d0-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="617d0-129">Kernel32.lib</span></span> |
| <span data-ttu-id="617d0-130">DLL</span><span class="sxs-lookup"><span data-stu-id="617d0-130">DLL</span></span> | <span data-ttu-id="617d0-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="617d0-131">Kernel32.dll</span></span> |
| <span data-ttu-id="617d0-132">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="617d0-132">Unicode and ANSI names</span></span> | <span data-ttu-id="617d0-133">**Setconsoletitlew** (Unicode) und **setconsoletitlea** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="617d0-133">**SetConsoleTitleW** (Unicode) and **SetConsoleTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="617d0-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="617d0-134">See also</span></span>

[<span data-ttu-id="617d0-135">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="617d0-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="617d0-136">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="617d0-136">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="617d0-137">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="617d0-137">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="617d0-138">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="617d0-138">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="617d0-139">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="617d0-139">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)