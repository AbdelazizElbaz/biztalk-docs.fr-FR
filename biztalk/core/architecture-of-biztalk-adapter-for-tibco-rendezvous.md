---
title: "Architecture de l’adaptateur TIBCO Rendezvous | Documents Microsoft"
description: "En savoir plus sur l’adaptateur BizTalk pour TIBCO Rendezvous fonctionne, y compris la transmission de messages, dans BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 174d6ceb-8e1d-4c93-827d-8155cfe47836
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3bfee2b51df8781091ea30e512810bae21a5f2a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="architecture-of-the-tibco-rendezvous-adapter"></a><span data-ttu-id="401f1-103">Architecture de l’adaptateur TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="401f1-103">Architecture of the TIBCO Rendezvous adapter</span></span>

## <a name="overview"></a><span data-ttu-id="401f1-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="401f1-104">Overview</span></span>
<span data-ttu-id="401f1-105">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous assure la connectivité bidirectionnelle entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="401f1-105">Microsoft BizTalk Adapter for TIBCO Rendezvous provides bi-directional connectivity between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and TIBCO Rendezvous.</span></span> <span data-ttu-id="401f1-106">Il utilise l'API TIBCO Rendezvous et l'API d'infrastructure d'adaptateurs BizTalk pour offrir une intégration étroite.</span><span class="sxs-lookup"><span data-stu-id="401f1-106">This adapter uses both the TIBCO Rendezvous API and the BizTalk Adapter Framework API to provide tight integration.</span></span>  
  
 <span data-ttu-id="401f1-107">TIBCO Rendezvous est un logiciel qui inclut un bus de messages pour l'intégration des applications d'entreprise (IAE).</span><span class="sxs-lookup"><span data-stu-id="401f1-107">TIBCO Rendezvous is a software product that provides a message bus for enterprise application integration (EAI).</span></span> <span data-ttu-id="401f1-108">Il inclut des API de messagerie en C, C++, Java, Visual Basic et pour Microsoft .NET Framework pour la réception de flux de données dans des feuilles de calcul Microsoft Office Excel et d'autres applications spécifiques.</span><span class="sxs-lookup"><span data-stu-id="401f1-108">TIBCO provides messaging APIs in C, C++, Java, Visual Basic and the Microsoft .NET Framework to receive data feeds on Microsoft Office Excel worksheets and other applications of choice.</span></span>  
  
## <a name="message-passing"></a><span data-ttu-id="401f1-109">Transmission de messages</span><span class="sxs-lookup"><span data-stu-id="401f1-109">Message Passing</span></span>  
 <span data-ttu-id="401f1-110">Le concept de base de la transmission de messages est relativement simple :</span><span class="sxs-lookup"><span data-stu-id="401f1-110">The basic concept of message passing is fairly simple:</span></span>  
  
-   <span data-ttu-id="401f1-111">Un message inclut un sujet unique constitué d'éléments séparés par des points.</span><span class="sxs-lookup"><span data-stu-id="401f1-111">A message has a single subject composed of elements separated by periods.</span></span> <span data-ttu-id="401f1-112">Il est envoyé à un démon Rendezvous (même s'il peut être transmis à d'autres démons).</span><span class="sxs-lookup"><span data-stu-id="401f1-112">It is sent to a single Rendezvous daemon (though it might eventually be broadcast onto other daemons).</span></span>  
  
-   <span data-ttu-id="401f1-113">Un port d'écoute annonce ses sujets d'intérêt à un démon (à l'aide d'une fonction de caractère générique de base) et les messages ayant des sujets correspondants lui sont remis si les deux démons sont connectés ou correspondent au même démon.</span><span class="sxs-lookup"><span data-stu-id="401f1-113">A listener announces its subjects of interest to a daemon (with a basic wildcard facility), and messages that have matching subjects are delivered to it if the two daemons are 'connected' to each other, or are indeed the same daemon.</span></span> <span data-ttu-id="401f1-114">Pour plus d’informations, consultez les Messages dans [Messages dans l’adaptateur BizTalk pour TIBCO Rendezvous](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md).</span><span class="sxs-lookup"><span data-stu-id="401f1-114">For more information, see Messages in [Messages in BizTalk Adapter for TIBCO Rendezvous](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md).</span></span>  
  
 <span data-ttu-id="401f1-115">La figure suivante présente l'architecture de l'adaptateur BizTalk pour TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="401f1-115">The following figure shows the architecture for BizTalk Adapter for TIBCO Rendezvous.</span></span>  
  
 ![](../core/media/tibcorend-arch.gif "TibcoRend_Arch")  
  
## <a name="see-also"></a><span data-ttu-id="401f1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="401f1-116">See Also</span></span>  
 [<span data-ttu-id="401f1-117">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="401f1-117">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)  