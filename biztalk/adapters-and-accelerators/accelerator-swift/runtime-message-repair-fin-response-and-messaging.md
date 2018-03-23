---
title: Runtime, la réparation, la réponse FIN et la messagerie de message | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, about architecture
- architecture
- BizTalk Accelerator for SWIFT, architecture
ms.assetid: c7f34517-6663-44a6-b6ea-6d55fdb08caf
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 539d6f6d7a2b84262750f8b3c6da3c16a67f0de9
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="runtime-message-repair-fin-response-and-messaging"></a><span data-ttu-id="b5d7d-102">Runtime, la réparation de messages, la réponse FIN et la messagerie</span><span class="sxs-lookup"><span data-stu-id="b5d7d-102">Runtime, message repair, FIN response, and messaging</span></span>

## <a name="overview"></a><span data-ttu-id="b5d7d-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="b5d7d-103">Overview</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="b5d7d-104"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit aux clients et partenaires avec la fonctionnalité de messagerie et la connectivité financiers-sectorielles, qui contribue à accélérer l’implémentation de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] comme intergiciel (middleware) pour les organisations financières.</span><span class="sxs-lookup"><span data-stu-id="b5d7d-104"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides customers and partners with financial-industry-specific messaging and connectivity functionality, which helps accelerate implementation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] as middleware for financial organizations.</span></span>  
  
 <span data-ttu-id="b5d7d-105">En utilisant les normes de l’ouvrir en fonction outils et des fonctionnalités de runtime de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour implémenter la prise en charge des formats de message comme SWIFT, A4SWIFT permet de réduire la barrière à l’adoption de normes SWIFT mises à jour en utilisant [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] comme un à usage général plateforme d’intégration intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="b5d7d-105">By leveraging the open-standards based tools and runtime facilities of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to implement support for message formats like SWIFT, A4SWIFT reduces the barrier to adoption of updated SWIFT standards by employing [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] as a general-purpose middleware integration platform.</span></span>  
  
 <span data-ttu-id="b5d7d-106">A4SWIFT et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] réduire la temps de commercialisation lors également réduire le coût total de possession (TCO) en réduisant les coûts de maintenance et de prise en charge globale de la livraison des serveurs de classe pour l’hébergement d’applications et intégration ainsi que du flux de travail d’entreprise mise en œuvre dans le secteur des services financiers.</span><span class="sxs-lookup"><span data-stu-id="b5d7d-106">A4SWIFT and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] reduce the time-to-market while also decreasing the total cost of ownership (TCO) by reducing the overall maintenance and support cost of delivering enterprise class servers for application hosting and integration as well as workflow implementation in the financial services industry.</span></span>  
  
 <span data-ttu-id="b5d7d-107">Vous pouvez classer les fonctionnalités A4SWIFT SWIFT de messagerie et de connectivité SWIFT.</span><span class="sxs-lookup"><span data-stu-id="b5d7d-107">You can broadly categorize A4SWIFT functionality as SWIFT messaging and SWIFT connectivity.</span></span> <span data-ttu-id="b5d7d-108">Messagerie d’A4SWIFT complet comprend des messages SWIFT l’analyse et de validation (y compris le traitement par lot entrant/sortant), d’entrée de message et de réparation (y compris l’intégration [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] que l’outil frontal utilisateur) et d’autres applications Line of business (LOB).</span><span class="sxs-lookup"><span data-stu-id="b5d7d-108">Full A4SWIFT messaging encompasses SWIFT message parsing and validation (including inbound/outbound batching), message entry and repair (including integration with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] as the front-end user tool), and other line-of-business (LOB) applications.</span></span>  
  
 [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]<span data-ttu-id="b5d7d-109"> Fournit des schémas XSD et la validation complète, y compris les règles de réseau, pour tous les 358 des messages financières (FIN).</span><span class="sxs-lookup"><span data-stu-id="b5d7d-109"> provides XSD schemas and full validation, including network rules, for all 358 of the financial (FIN) messages.</span></span> <span data-ttu-id="b5d7d-110">Il fournit également debatching entrant.</span><span class="sxs-lookup"><span data-stu-id="b5d7d-110">It also provides inbound debatching.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="b5d7d-111">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b5d7d-111">Next steps</span></span>  
 <span data-ttu-id="b5d7d-112">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="b5d7d-112">This section contains:</span></span>  
  
-   [<span data-ttu-id="b5d7d-113">Components</span><span class="sxs-lookup"><span data-stu-id="b5d7d-113">Components</span></span>](components.md)  
  
-   [<span data-ttu-id="b5d7d-114">Exécution de BizTalk Accelerator pour SWIFT</span><span class="sxs-lookup"><span data-stu-id="b5d7d-114">BizTalk Accelerator for SWIFT Runtime</span></span>](biztalk-accelerator-for-swift-runtime.md)  
  
-   [<span data-ttu-id="b5d7d-115">Réparation et renvoi des messages</span><span class="sxs-lookup"><span data-stu-id="b5d7d-115">Message Repair and New Submission</span></span>](message-repair-and-new-submission.md)  
  
-   [<span data-ttu-id="b5d7d-116">Rapprochement des réponses FIN</span><span class="sxs-lookup"><span data-stu-id="b5d7d-116">FIN Response Reconciliation</span></span>](fin-response-reconciliation.md)  
  
-   [<span data-ttu-id="b5d7d-117">Messages SWIFT</span><span class="sxs-lookup"><span data-stu-id="b5d7d-117">SWIFT Messages</span></span>](swift-messages.md)

- [<span data-ttu-id="b5d7d-118">Propriétés promues A4SWIFT_\*</span><span class="sxs-lookup"><span data-stu-id="b5d7d-118">A4SWIFT_\* Promoted Properties</span></span>](a4swift-promoted-properties.md)