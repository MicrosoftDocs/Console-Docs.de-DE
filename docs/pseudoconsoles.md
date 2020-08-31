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
# <a name="pseudoconsoles"></a><span data-ttu-id="ab96f-104">Pseudo Konsolen</span><span class="sxs-lookup"><span data-stu-id="ab96f-104">Pseudoconsoles</span></span>

<span data-ttu-id="ab96f-105">Eine *pseudoconsole* ist ein Gerätetyp, mit dem Anwendungen zum Host für Zeichenmodus-Anwendungen werden können.</span><span class="sxs-lookup"><span data-stu-id="ab96f-105">A *pseudoconsole* is a device type that allows applications to become the host for character-mode applications.</span></span> 

<span data-ttu-id="ab96f-106">Dies steht im Gegensatz zu einer typischen Konsolen Sitzung, bei der das Betriebssystem ein Hostingfenster im Namen der zeichenmodusanwendung erstellt, um die grafische Ausgabe und die Benutzereingabe zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="ab96f-106">This is in contrast to a typical console session where the operating system will create a hosting window on behalf of the character-mode application to handle graphical output and user input.</span></span>

<span data-ttu-id="ab96f-107">Mit einer pseudoconsole wird das Hostingfenster nicht erstellt.</span><span class="sxs-lookup"><span data-stu-id="ab96f-107">With a pseudoconsole, the hosting window is not created.</span></span> <span data-ttu-id="ab96f-108">Die Anwendung, die die pseudoconsole erstellt, muss für die Anzeige der grafischen Ausgabe und das Erfassen von Benutzereingaben zuständig sein.</span><span class="sxs-lookup"><span data-stu-id="ab96f-108">The application that makes the pseudoconsole must become responsible for displaying the graphical output and collecting user input.</span></span> <span data-ttu-id="ab96f-109">Alternativ können die Informationen auch weiter an eine andere Anwendung weitergeleitet werden, die für diese Aktivitäten zu einem späteren Zeitpunkt in der Kette verantwortlich ist.</span><span class="sxs-lookup"><span data-stu-id="ab96f-109">Alternatively, the information can be relayed further to another application responsible for these activities at a later point in the chain.</span></span>

<span data-ttu-id="ab96f-110">Diese Funktion ist für Terminalfenster Anwendungen von Drittanbietern auf der Plattform oder für die Umleitung von Zeichenmodus-Aktivitäten in eine Remote-Terminalfenster Sitzung auf einem anderen Computer oder sogar auf einer anderen Plattform konzipiert.</span><span class="sxs-lookup"><span data-stu-id="ab96f-110">This functionality is designed for third-party "terminal window" applications to exist on the platform or for redirection of character-mode activities to a remote "terminal window" session on another machine or even on another platform.</span></span>

<span data-ttu-id="ab96f-111">Beachten Sie, dass die zugrunde liegende Konsolen Sitzung weiterhin im Auftrag der Anwendung erstellt wird, die die pseudoconsole anfordert.</span><span class="sxs-lookup"><span data-stu-id="ab96f-111">Note that the underlying console session will still be created on behalf of the application requesting the pseudoconsole.</span></span> <span data-ttu-id="ab96f-112">Es gelten weiterhin alle Regeln der [Konsolen Sitzungen](consoles.md) , einschließlich der Möglichkeit, dass mehrere Anwendungen im Zeichenmodus für Anwendungen eine Verbindung mit der Sitzung herstellen.</span><span class="sxs-lookup"><span data-stu-id="ab96f-112">All the rules of [console sessions](consoles.md) still apply including the ability for multiple client character-mode applications to connect to the session.</span></span>

<span data-ttu-id="ab96f-113">Die Informationen, die über den Pseudo Konsolen Kanal bereitgestellt werden, werden immer in UTF-8 codiert, um maximale Kompatibilität mit der vorhandenen Welt der Pseudo Terminal-Funktionalität zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="ab96f-113">To provide maximum compatibility with the existing world of  pseudoterminal functionality, the information provided over the pseudoconsole channel will always be encoded in UTF-8.</span></span> <span data-ttu-id="ab96f-114">Dies hat keine Auswirkung auf die Codepage oder die Codierung der angefügten Client Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="ab96f-114">This does not affect the codepage or encoding of the client applications that are attached.</span></span> <span data-ttu-id="ab96f-115">Die Übersetzung erfolgt bei Bedarf innerhalb des pseudoconsole-Systems.</span><span class="sxs-lookup"><span data-stu-id="ab96f-115">Translation will happen inside the pseudoconsole system as necessary.</span></span>

<span data-ttu-id="ab96f-116">Ein Beispiel für den Einstieg finden Sie unter [Erstellen einer pseudoconsole-Sitzung](creating-a-pseudoconsole-session.md).</span><span class="sxs-lookup"><span data-stu-id="ab96f-116">An example for getting started can be found at [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

<span data-ttu-id="ab96f-117">Weitere Hintergrundinformationen zu Pseudo Konsolen finden Sie im Ankündigungs Blogbeitrag: [Windows-Befehlszeile: Einführung in die Windows-Pseudo Konsole (](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/)Configuration Manager).</span><span class="sxs-lookup"><span data-stu-id="ab96f-117">Some additional background information on pseudoconsoles can be found at the announcement blog post: [Windows Command-Line: Introducing the Windows Pseudo Console (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>
