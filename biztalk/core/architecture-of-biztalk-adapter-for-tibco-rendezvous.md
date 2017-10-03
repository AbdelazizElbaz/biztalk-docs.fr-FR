---
title: "Architecture de l’adaptateur BizTalk pour TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passing messages
- architecture
- message passing
- messages, passing
ms.assetid: 174d6ceb-8e1d-4c93-827d-8155cfe47836
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 801f92453ffc85d83d57c1caa5c89ec618b96ed0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-biztalk-adapter-for-tibco-rendezvous"></a><span data-ttu-id="1d8f5-102">Architecture de l'adaptateur BizTalk pour TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="1d8f5-102">Architecture of BizTalk Adapter for TIBCO Rendezvous</span></span>
<span data-ttu-id="1d8f5-103">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous assure la connectivité bidirectionnelle entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="1d8f5-103">Microsoft BizTalk Adapter for TIBCO Rendezvous provides bi-directional connectivity between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and TIBCO Rendezvous.</span></span> <span data-ttu-id="1d8f5-104">Il utilise l'API TIBCO Rendezvous et l'API d'infrastructure d'adaptateurs BizTalk pour offrir une intégration étroite.</span><span class="sxs-lookup"><span data-stu-id="1d8f5-104">This adapter uses both the TIBCO Rendezvous API and the BizTalk Adapter Framework API to provide tight integration.</span></span>  
  
 <span data-ttu-id="1d8f5-105">TIBCO Rendezvous est un logiciel qui inclut un bus de messages pour l'intégration des applications d'entreprise (IAE).</span><span class="sxs-lookup"><span data-stu-id="1d8f5-105">TIBCO Rendezvous is a software product that provides a message bus for enterprise application integration (EAI).</span></span> <span data-ttu-id="1d8f5-106">Il inclut des API de messagerie en C, C++, Java, Visual Basic et pour Microsoft .NET Framework pour la réception de flux de données dans des feuilles de calcul Microsoft Office Excel et d'autres applications spécifiques.</span><span class="sxs-lookup"><span data-stu-id="1d8f5-106">TIBCO provides messaging APIs in C, C++, Java, Visual Basic and the Microsoft .NET Framework to receive data feeds on Microsoft Office Excel worksheets and other applications of choice.</span></span>  
  
## <a name="message-passing"></a><span data-ttu-id="1d8f5-107">Transmission de messages</span><span class="sxs-lookup"><span data-stu-id="1d8f5-107">Message Passing</span></span>  
 <span data-ttu-id="1d8f5-108">Le concept de base de la transmission de messages est relativement simple :</span><span class="sxs-lookup"><span data-stu-id="1d8f5-108">The basic concept of message passing is fairly simple:</span></span>  
  
-   <span data-ttu-id="1d8f5-109">Un message inclut un sujet unique constitué d'éléments séparés par des points.</span><span class="sxs-lookup"><span data-stu-id="1d8f5-109">A message has a single subject composed of elements separated by periods.</span></span> <span data-ttu-id="1d8f5-110">Il est envoyé à un démon Rendezvous (même s'il peut être transmis à d'autres démons).</span><span class="sxs-lookup"><span data-stu-id="1d8f5-110">It is sent to a single Rendezvous daemon (though it might eventually be broadcast onto other daemons).</span></span>  
  
-   <span data-ttu-id="1d8f5-111">Un port d'écoute annonce ses sujets d'intérêt à un démon (à l'aide d'une fonction de caractère générique de base) et les messages ayant des sujets correspondants lui sont remis si les deux démons sont connectés ou correspondent au même démon.</span><span class="sxs-lookup"><span data-stu-id="1d8f5-111">A listener announces its subjects of interest to a daemon (with a basic wildcard facility), and messages that have matching subjects are delivered to it if the two daemons are 'connected' to each other, or are indeed the same daemon.</span></span> <span data-ttu-id="1d8f5-112">Pour plus d’informations, consultez les Messages dans [Messages dans l’adaptateur BizTalk pour TIBCO Rendezvous](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md).</span><span class="sxs-lookup"><span data-stu-id="1d8f5-112">For more information, see Messages in [Messages in BizTalk Adapter for TIBCO Rendezvous](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md).</span></span>  
  
 <span data-ttu-id="1d8f5-113">La figure suivante présente l'architecture de l'adaptateur BizTalk pour TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="1d8f5-113">The following figure shows the architecture for BizTalk Adapter for TIBCO Rendezvous.</span></span>  
  
 ![](../core/media/tibcorend-arch.gif "TibcoRend_Arch")  
  
## <a name="see-also"></a><span data-ttu-id="1d8f5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d8f5-114">See Also</span></span>  
 <span data-ttu-id="1d8f5-115">[Prise en main](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="1d8f5-115">[Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="1d8f5-116">Planification et Architecture</span><span class="sxs-lookup"><span data-stu-id="1d8f5-116">Planning and Architecture</span></span>](../core/planning-and-architecture15.md)