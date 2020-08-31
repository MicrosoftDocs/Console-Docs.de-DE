---
title: Pseudo Konsolen – Windows-Desktop
description: Eine Pseudo Konsole ist ein Konzept, das verwendet wird, um den hostingaspekt oder den Wartungs Aspekt einer zeichenmodusanwendung bereitzustellen.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API, Configuration Manager, pseudoconsole
ms.openlocfilehash: ce2dfb14371e35a738e9c42ba2be8d2bb2758946
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059570"
---
# <a name="pseudoconsoles"></a>Pseudo Konsolen

Eine *pseudoconsole* ist ein Gerätetyp, mit dem Anwendungen zum Host für Zeichenmodus-Anwendungen werden können. 

Dies steht im Gegensatz zu einer typischen Konsolen Sitzung, bei der das Betriebssystem ein Hostingfenster im Namen der zeichenmodusanwendung erstellt, um die grafische Ausgabe und die Benutzereingabe zu verarbeiten.

Mit einer pseudoconsole wird das Hostingfenster nicht erstellt. Die Anwendung, die die pseudoconsole erstellt, muss für die Anzeige der grafischen Ausgabe und das Erfassen von Benutzereingaben zuständig sein. Alternativ können die Informationen auch weiter an eine andere Anwendung weitergeleitet werden, die für diese Aktivitäten zu einem späteren Zeitpunkt in der Kette verantwortlich ist.

Diese Funktion ist für Terminalfenster Anwendungen von Drittanbietern auf der Plattform oder für die Umleitung von Zeichenmodus-Aktivitäten in eine Remote-Terminalfenster Sitzung auf einem anderen Computer oder sogar auf einer anderen Plattform konzipiert.

Beachten Sie, dass die zugrunde liegende Konsolen Sitzung weiterhin im Auftrag der Anwendung erstellt wird, die die pseudoconsole anfordert. Es gelten weiterhin alle Regeln der [Konsolen Sitzungen](consoles.md) , einschließlich der Möglichkeit, dass mehrere Anwendungen im Zeichenmodus für Anwendungen eine Verbindung mit der Sitzung herstellen.

Die Informationen, die über den Pseudo Konsolen Kanal bereitgestellt werden, werden immer in UTF-8 codiert, um maximale Kompatibilität mit der vorhandenen Welt der Pseudo Terminal-Funktionalität zu gewährleisten. Dies hat keine Auswirkung auf die Codepage oder die Codierung der angefügten Client Anwendungen. Die Übersetzung erfolgt bei Bedarf innerhalb des pseudoconsole-Systems.

Ein Beispiel für den Einstieg finden Sie unter [Erstellen einer pseudoconsole-Sitzung](creating-a-pseudoconsole-session.md).

Weitere Hintergrundinformationen zu Pseudo Konsolen finden Sie im Ankündigungs Blogbeitrag: [Windows-Befehlszeile: Einführung in die Windows-Pseudo Konsole (](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/)Configuration Manager).
