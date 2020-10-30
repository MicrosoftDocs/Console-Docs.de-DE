---
title: Funktion "kreateconsoleskreenbuffer"
description: Die Funktion "kreateconsoleskreenbuffer" erstellt einen Bildschirm Puffer für die Windows-Konsole.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- base.createconsolescreenbuffer
- consoles.createconsolescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff
topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0b8f5b33233f49167c67a47f33e5a95b8864f7bd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039132"
---
# <a name="createconsolescreenbuffer-function"></a><span data-ttu-id="84f3c-104">Funktion "kreateconsoleskreenbuffer"</span><span class="sxs-lookup"><span data-stu-id="84f3c-104">CreateConsoleScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="84f3c-105">Erstellt einen Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="84f3c-105">Creates a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="84f3c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="84f3c-106">Syntax</span></span>

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## <a name="parameters"></a><span data-ttu-id="84f3c-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="84f3c-107">Parameters</span></span>

<span data-ttu-id="84f3c-108">*dwDesiredAccess* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="84f3c-108">*dwDesiredAccess* \[in\]</span></span>  
<span data-ttu-id="84f3c-109">Der Zugriff auf den Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="84f3c-109">The access to the console screen buffer.</span></span> <span data-ttu-id="84f3c-110">Eine Liste der Zugriffsrechte finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="84f3c-110">For a list of access rights, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="84f3c-111">*dwsharemode* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="84f3c-111">*dwShareMode* \[in\]</span></span>  
<span data-ttu-id="84f3c-112">Dieser Parameter kann NULL sein, um anzugeben, dass der Puffer nicht freigegeben werden kann, oder es kann sich um einen oder mehrere der folgenden Werte handeln.</span><span class="sxs-lookup"><span data-stu-id="84f3c-112">This parameter can be zero, indicating that the buffer cannot be shared, or it can be one or more of the following values.</span></span>

| <span data-ttu-id="84f3c-113">Wert</span><span class="sxs-lookup"><span data-stu-id="84f3c-113">Value</span></span> | <span data-ttu-id="84f3c-114">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="84f3c-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="84f3c-115">**FILE_SHARE_READ** 0x00000001</span><span class="sxs-lookup"><span data-stu-id="84f3c-115">**FILE_SHARE_READ** 0x00000001</span></span> | <span data-ttu-id="84f3c-116">Andere geöffnete Vorgänge können auf dem Konsolenbildschirm Puffer für den Lesezugriff ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="84f3c-116">Other open operations can be performed on the console screen buffer for read access.</span></span> |
| <span data-ttu-id="84f3c-117">**FILE_SHARE_WRITE** 0x00000002</span><span class="sxs-lookup"><span data-stu-id="84f3c-117">**FILE_SHARE_WRITE** 0x00000002</span></span> | <span data-ttu-id="84f3c-118">Andere geöffnete Vorgänge können auf dem Konsolenbildschirm Puffer für Schreibzugriffe ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="84f3c-118">Other open operations can be performed on the console screen buffer for write access.</span></span> |

<span data-ttu-id="84f3c-119">*lpsecurityattribute* \[ in, optional\]</span><span class="sxs-lookup"><span data-stu-id="84f3c-119">*lpSecurityAttributes* \[in, optional\]</span></span>  
<span data-ttu-id="84f3c-120">Ein Zeiger auf eine Struktur von [**Sicherheits \_ Attributen**](https://msdn.microsoft.com/library/windows/desktop/aa379560) , die bestimmt, ob das zurückgegebene Handle von untergeordneten Prozessen geerbt werden kann.</span><span class="sxs-lookup"><span data-stu-id="84f3c-120">A pointer to a [**SECURITY\_ATTRIBUTES**](https://msdn.microsoft.com/library/windows/desktop/aa379560) structure that determines whether the returned handle can be inherited by child processes.</span></span> <span data-ttu-id="84f3c-121">Wenn *lpsecurityattribute* **null** ist, kann das Handle nicht geerbt werden.</span><span class="sxs-lookup"><span data-stu-id="84f3c-121">If *lpSecurityAttributes* is **NULL** , the handle cannot be inherited.</span></span> <span data-ttu-id="84f3c-122">Der **lpsecuritydescriptor** -Member der-Struktur gibt eine Sicherheits Beschreibung für den neuen Konsolenbildschirm Puffer an.</span><span class="sxs-lookup"><span data-stu-id="84f3c-122">The **lpSecurityDescriptor** member of the structure specifies a security descriptor for the new console screen buffer.</span></span> <span data-ttu-id="84f3c-123">Wenn *lpsecurityattribute* **null** ist, erhält der Konsolenbildschirm Puffer eine Standard Sicherheits Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="84f3c-123">If *lpSecurityAttributes* is **NULL** , the console screen buffer gets a default security descriptor.</span></span> <span data-ttu-id="84f3c-124">Die ACLs in der Standard Sicherheits Beschreibung eines Konsolenbildschirm Puffers stammen aus dem primären Token oder dem Identitätswechsel Token des Erstellers.</span><span class="sxs-lookup"><span data-stu-id="84f3c-124">The ACLs in the default security descriptor for a console screen buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="84f3c-125">*dwFlags* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="84f3c-125">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="84f3c-126">Der Typ des zu erstellenden Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="84f3c-126">The type of console screen buffer to create.</span></span> <span data-ttu-id="84f3c-127">Der einzige unterstützte Bildschirm Puffertyp ist der **Konsolen \_ TextMode- \_ Puffer** .</span><span class="sxs-lookup"><span data-stu-id="84f3c-127">The only supported screen buffer type is **CONSOLE\_TEXTMODE\_BUFFER** .</span></span>

<span data-ttu-id="84f3c-128">*lpscreenbufferdata*</span><span class="sxs-lookup"><span data-stu-id="84f3c-128">*lpScreenBufferData*</span></span>  
<span data-ttu-id="84f3c-129">Bleiben muss **null** sein.</span><span class="sxs-lookup"><span data-stu-id="84f3c-129">Reserved; should be **NULL** .</span></span>

## <a name="return-value"></a><span data-ttu-id="84f3c-130">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="84f3c-130">Return value</span></span>

<span data-ttu-id="84f3c-131">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ein Handle für den neuen Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="84f3c-131">If the function succeeds, the return value is a handle to the new console screen buffer.</span></span>

<span data-ttu-id="84f3c-132">Wenn die Funktion fehlschlägt, ist der Rückgabewert ein **ungültiger \_ handle- \_ Wert** .</span><span class="sxs-lookup"><span data-stu-id="84f3c-132">If the function fails, the return value is **INVALID\_HANDLE\_VALUE** .</span></span> <span data-ttu-id="84f3c-133">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="84f3c-133">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="84f3c-134">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="84f3c-134">Remarks</span></span>

<span data-ttu-id="84f3c-135">Eine Konsole kann über mehrere Bildschirm Puffer verfügen, aber nur einen aktiven Bildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="84f3c-135">A console can have multiple screen buffers but only one active screen buffer.</span></span> <span data-ttu-id="84f3c-136">Der Zugriff auf inaktive Bildschirm Puffer ist für Lese-und Schreibvorgänge möglich, es wird jedoch nur der aktive Bildschirm Puffer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="84f3c-136">Inactive screen buffers can be accessed for reading and writing, but only the active screen buffer is displayed.</span></span> <span data-ttu-id="84f3c-137">Verwenden Sie die Funktion [**setconsoleactiveskreenbuffer**](setconsoleactivescreenbuffer.md) , damit der neue Bildschirm den Puffer für den aktiven Bildschirm puffert.</span><span class="sxs-lookup"><span data-stu-id="84f3c-137">To make the new screen buffer the active screen buffer, use the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function.</span></span>

<span data-ttu-id="84f3c-138">Der neu erstellte Bildschirm Puffer kopiert einige Eigenschaften aus dem Puffer des aktiven Bildschirms, wenn diese Funktion aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="84f3c-138">The newly created screen buffer will copy some properties from the active screen buffer at the time that this function is called.</span></span> <span data-ttu-id="84f3c-139">Das Verhalten sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="84f3c-139">The behavior is as follows:</span></span>

- <span data-ttu-id="84f3c-140">`Font` -kopiert aus dem aktiven Bildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="84f3c-140">`Font` - copied from active screen buffer</span></span>
- <span data-ttu-id="84f3c-141">`Display Window Size` -kopiert aus dem aktiven Bildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="84f3c-141">`Display Window Size` - copied from active screen buffer</span></span>
- <span data-ttu-id="84f3c-142">`Buffer Size` -Übereinstimmung mit `Display Window Size` ( **nicht** kopiert)</span><span class="sxs-lookup"><span data-stu-id="84f3c-142">`Buffer Size` - matched to `Display Window Size` ( **NOT** copied)</span></span>
- <span data-ttu-id="84f3c-143">`Default Attributes` (Farben)-aus aktivem Bildschirm Puffer kopiert</span><span class="sxs-lookup"><span data-stu-id="84f3c-143">`Default Attributes` (colors) - copied from active screen buffer</span></span>
- <span data-ttu-id="84f3c-144">`Default Popup Attributes` (Farben)-aus aktivem Bildschirm Puffer kopiert</span><span class="sxs-lookup"><span data-stu-id="84f3c-144">`Default Popup Attributes` (colors) - copied from active screen buffer</span></span>

<span data-ttu-id="84f3c-145">Der aufrufenden Prozess kann das zurückgegebene Handle in jeder Funktion verwenden, die ein Handle für einen Konsolenbildschirm Puffer erfordert, je nach den Einschränkungen des Zugriffs, der durch den *dwDesiredAccess* -Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="84f3c-145">The calling process can use the returned handle in any function that requires a handle to a console screen buffer, subject to the limitations of access specified by the *dwDesiredAccess* parameter.</span></span>

<span data-ttu-id="84f3c-146">Der aufrufenden Prozess kann die [**duplikatandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) -Funktion verwenden, um ein doppeltes Bildschirm Puffer Handle zu erstellen, das über einen anderen Zugriff oder eine andere Vererbbarkeit als das ursprüngliche Handle verfügt.</span><span class="sxs-lookup"><span data-stu-id="84f3c-146">The calling process can use the [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) function to create a duplicate screen buffer handle that has different access or inheritability from the original handle.</span></span> <span data-ttu-id="84f3c-147">**Duplikatandle** kann jedoch nicht zum Erstellen eines Duplikats verwendet werden, das für einen anderen Prozess gültig ist (außer durch Vererbung).</span><span class="sxs-lookup"><span data-stu-id="84f3c-147">However, **DuplicateHandle** cannot be used to create a duplicate that is valid for a different process (except through inheritance).</span></span>

<span data-ttu-id="84f3c-148">Verwenden Sie die [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) -Funktion, um das Bildschirm Puffer Handle der Konsole zu schließen.</span><span class="sxs-lookup"><span data-stu-id="84f3c-148">To close the console screen buffer handle, use the [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) function.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="84f3c-149">Beispiele</span><span class="sxs-lookup"><span data-stu-id="84f3c-149">Examples</span></span>

<span data-ttu-id="84f3c-150">Ein Beispiel finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="84f3c-150">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="84f3c-151">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="84f3c-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="84f3c-152">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="84f3c-152">Minimum supported client</span></span> | <span data-ttu-id="84f3c-153">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="84f3c-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="84f3c-154">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="84f3c-154">Minimum supported server</span></span> | <span data-ttu-id="84f3c-155">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="84f3c-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="84f3c-156">Header</span><span class="sxs-lookup"><span data-stu-id="84f3c-156">Header</span></span> | <span data-ttu-id="84f3c-157">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="84f3c-157">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="84f3c-158">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="84f3c-158">Library</span></span> | <span data-ttu-id="84f3c-159">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="84f3c-159">Kernel32.lib</span></span> |
| <span data-ttu-id="84f3c-160">DLL</span><span class="sxs-lookup"><span data-stu-id="84f3c-160">DLL</span></span> | <span data-ttu-id="84f3c-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="84f3c-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="84f3c-162">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="84f3c-162">See also</span></span>

[<span data-ttu-id="84f3c-163">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="84f3c-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="84f3c-164">Konsolenbildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="84f3c-164">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="84f3c-165">**CloseHandle**</span><span class="sxs-lookup"><span data-stu-id="84f3c-165">**CloseHandle**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724211)

[<span data-ttu-id="84f3c-166">**Duplialisiehandle**</span><span class="sxs-lookup"><span data-stu-id="84f3c-166">**DuplicateHandle**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724251)

[<span data-ttu-id="84f3c-167">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="84f3c-167">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="84f3c-168">**Sicherheits \_ Attribute**</span><span class="sxs-lookup"><span data-stu-id="84f3c-168">**SECURITY\_ATTRIBUTES**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa379560)

[<span data-ttu-id="84f3c-169">**SetConsoleActiveScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="84f3c-169">**SetConsoleActiveScreenBuffer**</span></span>](setconsoleactivescreenbuffer.md)

[<span data-ttu-id="84f3c-170">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="84f3c-170">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)
