---
title: Architecture de la Solution EDI | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55709a89-7706-4c64-ada3-16951951c943
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42afbb604a8cef1387418e175a39150f0182c607
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-solution-architecture"></a><span data-ttu-id="04804-102">Architecture de la solution EDI</span><span class="sxs-lookup"><span data-stu-id="04804-102">EDI Solution Architecture</span></span>
<span data-ttu-id="04804-103">L’échange de données électroniques (EDI) est un des moyens plus répandus par lequel les entités échangent électronique des données.</span><span class="sxs-lookup"><span data-stu-id="04804-103">Electronic Data Interchange (EDI) is one of the most prevalent means by which business entities exchange data electronically.</span></span> <span data-ttu-id="04804-104">L'utilisation d'EDI inclut une syntaxe et des normes de message (notamment ANSI X12 et UN/EDIFACT), un protocole de messagerie et des transports.</span><span class="sxs-lookup"><span data-stu-id="04804-104">EDI usage entails message syntax and standards (including ANSI X12 and UN/EDIFACT), messaging protocol, and transports.</span></span> <span data-ttu-id="04804-105">La messagerie EDI présente les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="04804-105">The following are characteristics of EDI messaging:</span></span>  
  
-   <span data-ttu-id="04804-106">Les protocoles de messagerie EDI vérifient que les données arrivent toujours comme prévu. Les données corrompues ou incorrectes sont automatiquement détectées et signalées.</span><span class="sxs-lookup"><span data-stu-id="04804-106">EDI messaging protocols ensure that data always arrives as expected, and corrupted or incorrect data is automatically detected and reported.</span></span>  
  
-   <span data-ttu-id="04804-107">Les mécanismes EDI indiquent généralement les schémas d'agrégation de données (lots).</span><span class="sxs-lookup"><span data-stu-id="04804-107">EDI mechanisms usually specify data aggregation schemes (batching).</span></span>  
  
-   <span data-ttu-id="04804-108">Les utilisateurs personnalisent souvent les définitions de document EDI via l'application d'un sous-ensemble ou d'une implémentation spécifique d'une instruction EDI.</span><span class="sxs-lookup"><span data-stu-id="04804-108">Users often customize EDI document definitions by implementing subset or specific implementation of an EDI guideline.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="04804-109"> traite les messages EDI à l'aide de pipelines de réception et d'envoi spécifiques à EDI, qui peuvent analyser et sérialiser les messages EDI.</span><span class="sxs-lookup"><span data-stu-id="04804-109"> processes EDI messages using receive and send pipelines specific to EDI that can parse and serialize EDI messages.</span></span> <span data-ttu-id="04804-110">Cette section décrit l'architecture des solutions EDI sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], notamment les spécificités du traitement côté réception et côté envoi, de la validation des messages et de la création de rapports d'état.</span><span class="sxs-lookup"><span data-stu-id="04804-110">This section describes the architecture of EDI solutions on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], including specifics of receive-side and send-side processing, message validation, and status reporting.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04804-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="04804-111">In This Section</span></span>  
  
-   [<span data-ttu-id="04804-112">Messagerie EDI</span><span class="sxs-lookup"><span data-stu-id="04804-112">EDI Messaging</span></span>](../core/edi-messaging.md)  
  
-   [<span data-ttu-id="04804-113">Le rôle des accords dans le traitement EDI</span><span class="sxs-lookup"><span data-stu-id="04804-113">The Role of Agreements in EDI Processing</span></span>](../core/the-role-of-agreements-in-edi-processing.md)  
  
-   [<span data-ttu-id="04804-114">Réception des Messages EDI dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="04804-114">How BizTalk Server Receives EDI Messages</span></span>](../core/how-biztalk-server-receives-edi-messages.md)  
  
-   [<span data-ttu-id="04804-115">Envoi des Messages EDI dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="04804-115">How BizTalk Server Sends EDI Messages</span></span>](../core/how-biztalk-server-sends-edi-messages.md)  
  
-   [<span data-ttu-id="04804-116">Validation des messages EDI</span><span class="sxs-lookup"><span data-stu-id="04804-116">EDI Message Validation</span></span>](../core/edi-message-validation.md)  
  
-   [<span data-ttu-id="04804-117">Les Extensions de l’outil XML à l’aide de</span><span class="sxs-lookup"><span data-stu-id="04804-117">Using the XML Tool Extensions</span></span>](../core/using-the-xml-tool-extensions.md)