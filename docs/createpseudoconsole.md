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
# <a name="createpseudoconsole-function"></a>Funktion "anatepseudoconsole"

Erstellt ein neues pseudoconsole-Objekt für den aufrufenden Prozess.

## <a name="syntax"></a>Syntax

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

## <a name="parameters"></a>Parameter

*Größe* \[ in\]  
Die Abmessungen des Fensters/Puffers in der Anzahl von Zeichen, die bei der anfänglichen Erstellung der pseudoconsole verwendet werden. Dies kann später mit [resizepseudoconsole](resizepseudoconsole.md)angepasst werden.

*hinput* \[ in\]  
Ein geöffnetes Handle für einen Datenstrom, der die Benutzereingabe für das Gerät darstellt. Dies ist zurzeit auf [synchrone](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) e/a beschränkt.

*houtput* \[ in\]  
Ein geöffnetes Handle für einen Datenstrom, der die Anwendungs Ausgabe des Geräts darstellt. Dies ist zurzeit auf [synchrone](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) e/a beschränkt.

*dwFlags* \[ in\]  
Der Wert kann in folgenden Formen vorliegen:

| Wert | Bedeutung |
|-|-|
| **0** | Führt eine standardmäßige Pseudo Konsolen Erstellung aus. |
| **PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD) 1 | Die erstellte pseudoconsole-Sitzung versucht, die Cursorposition der Pernt-Konsole zu erben. |

*PHPC* \[ vorgenommen\]  
Zeiger auf einen Speicherort, der ein Handle für das neue pseudoconsole-Gerät empfängt.

## <a name="return-value"></a>Rückgabewert

Typ: **HRESULT**

Wenn diese Methode erfolgreich ausgeführt wird, wird **S_OK** zurückgegeben. Andernfalls wird ein **HRESULT** -Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen

Diese Funktion wird hauptsächlich von Anwendungen verwendet, die versuchen, ein Terminalfenster für eine Befehlszeilen-Benutzerschnittstellen Anwendung (CUI) zu sein. Die Aufrufer werden für die Darstellung der Informationen im Ausgabestream und für die Erfassung von Benutzereingaben und die Serialisierung in den Eingabestream verantwortlich.

Die als UTF-8 codierten Eingabe-und Ausgabedaten Ströme enthalten nur-Text, der mit [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md)interleavt ist.

Im Ausgabestream können die [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md) von der aufrufenden Anwendung decodiert werden, um das Layout zu gestalten und den reinen Text in einem Anzeige Fenster darzustellen.

Im Eingabestream stellt Klartext eine Standardtastatur Eingabe dar. Kompliziertere Vorgänge werden durch Codierungs Steuerelement-und Mausbewegungen als in diesen Stream eingebettete [virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md) dargestellt.

Das von dieser Funktion erstellte Handle muss mit [closepseudoconsole](closepseudoconsole.md) geschlossen werden, wenn die Vorgänge abgeschlossen sind.

Wenn verwendet wird `PSEUDOCONSOLE_INHERIT_CURSOR` , sollte die aufrufende Anwendung darauf vorbereitet sein, auf die Anforderung für den Cursor Zustand in einer asynchronen Weise in einem Hintergrund Thread zu reagieren, indem die Anforderung für Cursor Informationen weitergeleitet oder interpretiert wird, die empfangen und beantwortet werden `hOutput` `hInput` . Wenn dies nicht der Fall ist, kann die aufrufenden Anwendung bei einer weiteren Anforderung des Pseudo Konsolen Systems hängen bleiben.

## <a name="examples"></a>Beispiele

Eine vollständige Exemplarische Vorgehensweise zur Verwendung dieser Funktion zum Einrichten einer Pseudo Konsolen Sitzung finden Sie unter [Erstellen einer pseudoconsole-Sitzung](creating-a-pseudoconsole-session.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 10-Update vom Oktober 2018 (Version 1809) \[ nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2019 \[ -Desktop-Apps\] |
| Header | Consoleapi. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Pseudo Konsolen](pseudoconsoles.md)

[Erstellen einer Pseudokonsolensitzung](creating-a-pseudoconsole-session.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)
