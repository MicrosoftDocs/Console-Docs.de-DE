---
title: Funktion "anatepseudoconsole"
description: Weitere Informationen finden Sie in den Referenzinformationen zur createpseudoconsole-Funktion, die eine neue pseudoconsole für den aufrufenden Prozess zugeordnet.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API, Configuration Manager, pseudoconsole
f1_keywords:
- consoleapi/CreatePseudoConsole
- CreatePseudoConsole
topic_type:
- apiref
api_name:
- CreatePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: f10a77781d555a76fdfcea8c8f10ae6bc1f72047
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038298"
---
# <a name="createpseudoconsole-function"></a><span data-ttu-id="744f1-104">Funktion "anatepseudoconsole"</span><span class="sxs-lookup"><span data-stu-id="744f1-104">CreatePseudoConsole function</span></span>

<span data-ttu-id="744f1-105">Erstellt ein neues pseudoconsole-Objekt für den aufrufenden Prozess.</span><span class="sxs-lookup"><span data-stu-id="744f1-105">Creates a new pseudoconsole object for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="744f1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="744f1-106">Syntax</span></span>

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

## <a name="parameters"></a><span data-ttu-id="744f1-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="744f1-107">Parameters</span></span>

<span data-ttu-id="744f1-108">*Größe* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="744f1-108">*size* \[in\]</span></span>  
<span data-ttu-id="744f1-109">Die Abmessungen des Fensters/Puffers in der Anzahl von Zeichen, die bei der anfänglichen Erstellung der pseudoconsole verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="744f1-109">The dimensions of the window/buffer in count of characters that will be used on initial creation of the pseudoconsole.</span></span> <span data-ttu-id="744f1-110">Dies kann später mit [resizepseudoconsole](resizepseudoconsole.md)angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="744f1-110">This can be adjusted later with [ResizePseudoConsole](resizepseudoconsole.md).</span></span>

<span data-ttu-id="744f1-111">*hinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="744f1-111">*hInput* \[in\]</span></span>  
<span data-ttu-id="744f1-112">Ein geöffnetes Handle für einen Datenstrom, der die Benutzereingabe für das Gerät darstellt.</span><span class="sxs-lookup"><span data-stu-id="744f1-112">An open handle to a stream of data that represents user input to the device.</span></span> <span data-ttu-id="744f1-113">Dies ist zurzeit auf [synchrone](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) e/a beschränkt.</span><span class="sxs-lookup"><span data-stu-id="744f1-113">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="744f1-114">*houtput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="744f1-114">*hOutput* \[in\]</span></span>  
<span data-ttu-id="744f1-115">Ein geöffnetes Handle für einen Datenstrom, der die Anwendungs Ausgabe des Geräts darstellt.</span><span class="sxs-lookup"><span data-stu-id="744f1-115">An open handle to a stream of data that represents application output from the device.</span></span> <span data-ttu-id="744f1-116">Dies ist zurzeit auf [synchrone](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) e/a beschränkt.</span><span class="sxs-lookup"><span data-stu-id="744f1-116">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="744f1-117">*dwFlags* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="744f1-117">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="744f1-118">Der Wert kann in folgenden Formen vorliegen:</span><span class="sxs-lookup"><span data-stu-id="744f1-118">The value can be one of the following:</span></span>

| <span data-ttu-id="744f1-119">Wert</span><span class="sxs-lookup"><span data-stu-id="744f1-119">Value</span></span> | <span data-ttu-id="744f1-120">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="744f1-120">Meaning</span></span> |
|-|-|
| <span data-ttu-id="744f1-121">**0**</span><span class="sxs-lookup"><span data-stu-id="744f1-121">**0**</span></span> | <span data-ttu-id="744f1-122">Führt eine standardmäßige Pseudo Konsolen Erstellung aus.</span><span class="sxs-lookup"><span data-stu-id="744f1-122">Perform a standard pseudoconsole creation.</span></span> |
| <span data-ttu-id="744f1-123">**PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD) 1</span><span class="sxs-lookup"><span data-stu-id="744f1-123">**PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD)1</span></span> | <span data-ttu-id="744f1-124">Die erstellte pseudoconsole-Sitzung versucht, die Cursorposition der Pernt-Konsole zu erben.</span><span class="sxs-lookup"><span data-stu-id="744f1-124">The created pseudoconsole session will attempt to inherit the cursor position of the paernt console.</span></span> |

<span data-ttu-id="744f1-125">*PHPC* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="744f1-125">*phPC* \[out\]</span></span>  
<span data-ttu-id="744f1-126">Zeiger auf einen Speicherort, der ein Handle für das neue pseudoconsole-Gerät empfängt.</span><span class="sxs-lookup"><span data-stu-id="744f1-126">Pointer to a location that will receive a handle to the new pseudoconsole device.</span></span>

## <a name="return-value"></a><span data-ttu-id="744f1-127">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="744f1-127">Return value</span></span>

<span data-ttu-id="744f1-128">Typ: **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="744f1-128">Type: **HRESULT**</span></span>

<span data-ttu-id="744f1-129">Wenn diese Methode erfolgreich ausgeführt wird, wird **S_OK** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="744f1-129">If this method succeeds, it returns **S_OK** .</span></span> <span data-ttu-id="744f1-130">Andernfalls wird ein **HRESULT** -Fehlercode zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="744f1-130">Otherwise, it returns an **HRESULT** error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="744f1-131">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="744f1-131">Remarks</span></span>

<span data-ttu-id="744f1-132">Diese Funktion wird hauptsächlich von Anwendungen verwendet, die versuchen, ein Terminalfenster für eine Befehlszeilen-Benutzerschnittstellen Anwendung (CUI) zu sein.</span><span class="sxs-lookup"><span data-stu-id="744f1-132">This function is primarily used by applications attempting to be a terminal window for a command-line user interface (CUI) application.</span></span> <span data-ttu-id="744f1-133">Die Aufrufer werden für die Darstellung der Informationen im Ausgabestream und für die Erfassung von Benutzereingaben und die Serialisierung in den Eingabestream verantwortlich.</span><span class="sxs-lookup"><span data-stu-id="744f1-133">The callers become responsible for presentation of the information on the output stream and for collecting user input and serializing it into the input stream.</span></span>

<span data-ttu-id="744f1-134">Die als UTF-8 codierten Eingabe-und Ausgabedaten Ströme enthalten nur-Text, der mit [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md)interleavt ist.</span><span class="sxs-lookup"><span data-stu-id="744f1-134">The input and output streams encoded as UTF-8 contain plain text interleaved with [Virtual Terminal Sequences](console-virtual-terminal-sequences.md).</span></span>

<span data-ttu-id="744f1-135">Im Ausgabestream können die [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md) von der aufrufenden Anwendung decodiert werden, um das Layout zu gestalten und den reinen Text in einem Anzeige Fenster darzustellen.</span><span class="sxs-lookup"><span data-stu-id="744f1-135">On the output stream, the [virtual terminal sequences](console-virtual-terminal-sequences.md) can be decoded by the calling application to layout and present the plain text in a display window.</span></span>

<span data-ttu-id="744f1-136">Im Eingabestream stellt Klartext eine Standardtastatur Eingabe dar.</span><span class="sxs-lookup"><span data-stu-id="744f1-136">On the input stream, plain text represents standard keyboard keys input by a user.</span></span> <span data-ttu-id="744f1-137">Kompliziertere Vorgänge werden durch Codierungs Steuerelement-und Mausbewegungen als in diesen Stream eingebettete [virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md) dargestellt.</span><span class="sxs-lookup"><span data-stu-id="744f1-137">More complicated operations are represented by encoding control keys and mouse movements as [virtual terminal sequences](console-virtual-terminal-sequences.md) embedded in this stream.</span></span>

<span data-ttu-id="744f1-138">Das von dieser Funktion erstellte Handle muss mit [closepseudoconsole](closepseudoconsole.md) geschlossen werden, wenn die Vorgänge abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="744f1-138">The handle created by this function must be closed with [ClosePseudoConsole](closepseudoconsole.md) when operations are complete.</span></span>

<span data-ttu-id="744f1-139">Wenn verwendet wird `PSEUDOCONSOLE_INHERIT_CURSOR` , sollte die aufrufende Anwendung darauf vorbereitet sein, auf die Anforderung für den Cursor Zustand in einer asynchronen Weise in einem Hintergrund Thread zu reagieren, indem die Anforderung für Cursor Informationen weitergeleitet oder interpretiert wird, die empfangen und beantwortet werden `hOutput` `hInput` .</span><span class="sxs-lookup"><span data-stu-id="744f1-139">If using `PSEUDOCONSOLE_INHERIT_CURSOR`, the calling application should be prepared to respond to the request for the cursor state in an asynchronous fashion on a background thread by forwarding or interpreting the request for cursor information that will be received on `hOutput` and replying on `hInput`.</span></span> <span data-ttu-id="744f1-140">Wenn dies nicht der Fall ist, kann die aufrufenden Anwendung bei einer weiteren Anforderung des Pseudo Konsolen Systems hängen bleiben.</span><span class="sxs-lookup"><span data-stu-id="744f1-140">Failure to do so may cause the calling application to hang while making another request of the pseudoconsole system.</span></span>

## <a name="examples"></a><span data-ttu-id="744f1-141">Beispiele</span><span class="sxs-lookup"><span data-stu-id="744f1-141">Examples</span></span>

<span data-ttu-id="744f1-142">Eine vollständige Exemplarische Vorgehensweise zur Verwendung dieser Funktion zum Einrichten einer Pseudo Konsolen Sitzung finden Sie unter [Erstellen einer pseudoconsole-Sitzung](creating-a-pseudoconsole-session.md).</span><span class="sxs-lookup"><span data-stu-id="744f1-142">For a full walkthrough on using this function to establish a pseudoconsole session, please see [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="744f1-143">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="744f1-143">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="744f1-144">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="744f1-144">Minimum supported client</span></span> | <span data-ttu-id="744f1-145">Windows 10-Update vom Oktober 2018 (Version 1809) \[ nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="744f1-145">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="744f1-146">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="744f1-146">Minimum supported server</span></span> | <span data-ttu-id="744f1-147">Nur Windows Server 2019 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="744f1-147">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="744f1-148">Header</span><span class="sxs-lookup"><span data-stu-id="744f1-148">Header</span></span> | <span data-ttu-id="744f1-149">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="744f1-149">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="744f1-150">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="744f1-150">Library</span></span> | <span data-ttu-id="744f1-151">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="744f1-151">Kernel32.lib</span></span> |
| <span data-ttu-id="744f1-152">DLL</span><span class="sxs-lookup"><span data-stu-id="744f1-152">DLL</span></span> | <span data-ttu-id="744f1-153">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="744f1-153">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="744f1-154">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="744f1-154">See also</span></span>

[<span data-ttu-id="744f1-155">Pseudo Konsolen</span><span class="sxs-lookup"><span data-stu-id="744f1-155">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="744f1-156">Erstellen einer Pseudokonsolensitzung</span><span class="sxs-lookup"><span data-stu-id="744f1-156">Creating a Pseudoconsole Session</span></span>](creating-a-pseudoconsole-session.md)

[<span data-ttu-id="744f1-157">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="744f1-157">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)

[<span data-ttu-id="744f1-158">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="744f1-158">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
