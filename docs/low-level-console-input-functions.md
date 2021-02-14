---
title: Low-Level Konsolen Eingabefunktionen
description: Ein Puffer der Konsolen Eingabefunktionen auf niedriger Ebene enthält Eingabedaten Sätze, die Informationen zu Tastatur, Maus, Puffergröße, Fokus und Menü Ereignissen enthalten können.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_low\_level\_console\_input\_functions'
- base.low\_level\_console\_input\_functions
- consoles.low\_level\_console\_input\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41488614-ca7c-4207-b706-f7776423c7ba
ms.openlocfilehash: fc2969cb266479a0acdde890f4ad3710ca8d7e42
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357820"
---
# <a name="low-level-console-input-functions"></a>Low-Level Konsolen Eingabefunktionen

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ein Puffer der Konsolen Eingabefunktionen auf niedriger Ebene enthält Eingabedaten Sätze, die Informationen zu Tastatur, Maus, Puffergröße, Fokus und Menü Ereignissen enthalten können. Die Low-Level-Funktionen bieten direkten Zugriff auf den Eingabepuffer, im Gegensatz zu den Funktionen auf hoher Ebene, mit denen die Daten des Eingabe Puffers gefiltert und verarbeitet werden, wobei alle außer Tastatureingaben verworfen werden.

Es gibt fünf Funktionen auf niedriger Ebene für den Zugriff auf den Eingabepuffer einer Konsole:

- [**ReadConsoleInput**](readconsoleinput.md)
- [**PeekConsoleInput**](peekconsoleinput.md)
- [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)
- [**WriteConsoleInput**](writeconsoleinput.md)
- [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

Die Funktionen "read [**ConsoleInput**](readconsoleinput.md)", " [**Peer**](peekconsoleinput.md)Adapter" und "Write- [**ConsoleInput**](writeconsoleinput.md) " verwenden die [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur, um aus einem Eingabepuffer zu lesen oder in diesen zu schreiben.

Im folgenden finden Sie Beschreibungen der Konsolen Eingabefunktionen auf niedriger Ebene.

| Funktion | BESCHREIBUNG |
|-|-|
| [**ReadConsoleInput**](readconsoleinput.md) | Liest Eingabedaten Sätze aus einem Eingabepuffer und entfernt Sie. Die Funktion gibt erst zurück, wenn mindestens ein Datensatz verfügbar ist, der gelesen werden kann. Anschließend werden alle verfügbaren Datensätze in den Puffer des aufrufenden Prozesses übertragen, bis entweder keine weiteren Datensätze verfügbar sind oder die angegebene Anzahl von Datensätzen gelesen wurde. Ungelesene Datensätze verbleiben im Eingabepuffer für den nächsten Lesevorgang. Die-Funktion meldet die Gesamtzahl der gelesenen Datensätze. Ein Beispiel für die Verwendung von [**readconsoleinput**](readconsoleinput.md)finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md). |
| [**PeekConsoleInput**](peekconsoleinput.md) | Liest, ohne die ausstehenden Eingabedaten Sätze in einem Eingabepuffer zu entfernen. Alle verfügbaren Datensätze bis zur angegebenen Zahl werden in den Puffer des aufrufenden Prozesses kopiert. Wenn keine Datensätze verfügbar sind, gibt die Funktion sofort zurück. Die-Funktion meldet die Gesamtzahl der gelesenen Datensätze. |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) | Bestimmt die Anzahl der ungelesenen Eingabedaten Sätze in einem Eingabepuffer. |
| [**WriteConsoleInput**](writeconsoleinput.md) | Fügt Eingabedaten Sätze in den Eingabepuffer hinter allen ausstehenden Datensätzen im Puffer ein. Der Eingabepuffer wächst bei Bedarf dynamisch, um so viele Datensätze wie geschrieben zu halten. Um diese Funktion verwenden zu können, muss das angegebene Eingabepuffer Handle über das allgemeine \_ Schreibzugriffs Recht verfügen. |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) | Verwirft alle ungelesenen Ereignisse im Eingabepuffer. Um diese Funktion verwenden zu können, muss das angegebene Eingabepuffer Handle über das allgemeine \_ Schreibzugriffs Recht verfügen. |

Ein Thread des Anwendungsprozesses kann einen Warte Vorgang ausführen, um zu warten, bis die Eingabe in einem Eingabepuffer verfügbar ist. Um einen Warte Vorgang zu initiieren, geben Sie ein Handle für den Eingabepuffer an, wenn Sie eine der [Wait-Funktionen](/windows/win32/sync/wait-functions)aufzurufen. Diese Funktionen können zurückgeben, wenn der Status von einem oder mehreren-Objekten signalisiert wird. Der Status eines Konsolen Eingabe Handles wird signalisiert, wenn sich ungelesene Datensätze im Eingabepuffer befinden. Der Status wird auf "nicht signalisiert" zurückgesetzt, wenn der Eingabepuffer leer ist. Wenn keine Eingabe verfügbar ist, wechselt der aufrufende Thread in einen effizienten Wartezustand und beansprucht sehr wenig Prozessorzeit, während darauf gewartet wird, dass die Bedingungen des warte Vorgangs erfüllt werden.