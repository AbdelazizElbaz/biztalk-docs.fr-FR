---
title: "Développement et la configuration des Solutions EDI BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65629eb1-8e08-4233-9331-c53ae0abaed4
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6520b062ebc5c106e2f162cc92ff4c793a417b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-and-configuring-biztalk-server-edi-solutions"></a><span data-ttu-id="0a11c-102">Développement et configuration de solutions EDI BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="0a11c-102">Developing and Configuring BizTalk Server EDI Solutions</span></span>
<span data-ttu-id="0a11c-103">Informations pour les développeurs à créer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solutions EDI.</span><span class="sxs-lookup"><span data-stu-id="0a11c-103">Information for developers to create [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI solutions.</span></span> <span data-ttu-id="0a11c-104">Ces solutions sont créées à l’aide de l’environnement de conception du système de projet BizTalk et le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="0a11c-104">These solutions are created using the BizTalk project system design environment and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="0a11c-105">Avant de développer une solution EDI [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], assurez-vous d'avoir correctement installé et configuré [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec les fonctionnalités EDI.</span><span class="sxs-lookup"><span data-stu-id="0a11c-105">Before developing a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI solution, make sure that you have fully installed and configured [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with the EDI feature.</span></span> <span data-ttu-id="0a11c-106">Consultez [BizTalk Server - Nouveautés, Installation, Configuration et mise à niveau](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span><span class="sxs-lookup"><span data-stu-id="0a11c-106">See [BizTalk Server - What's New, Installation, Configuration, and Upgrade](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span> <span data-ttu-id="0a11c-107">Pour une configuration complémentaire spécifique à EDI requise pour développer une solution EDI, consultez [à la configuration des étapes pour optimiser votre environnement](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).</span><span class="sxs-lookup"><span data-stu-id="0a11c-107">For additional EDI-specific configuration required for developing an EDI solution, see [Post-configuration steps to optimize your environment](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a11c-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0a11c-108">In This Section</span></span>  
  
-   [<span data-ttu-id="0a11c-109">Configuration des propriétés EDI</span><span class="sxs-lookup"><span data-stu-id="0a11c-109">Configuring EDI Properties</span></span>](../core/configuring-edi-properties.md)  
  
-   [<span data-ttu-id="0a11c-110">Configuration des propriétés de l’accord Global ou de secours</span><span class="sxs-lookup"><span data-stu-id="0a11c-110">Configuring Global or Fallback Agreement Properties</span></span>](../core/configuring-global-or-fallback-agreement-properties.md)  
  
-   [<span data-ttu-id="0a11c-111">Configuration des propriétés de Pipeline EDI</span><span class="sxs-lookup"><span data-stu-id="0a11c-111">Configuring EDI Pipeline Properties</span></span>](../core/configuring-edi-pipeline-properties.md)  
  
-   [<span data-ttu-id="0a11c-112">Configuration des Ports pour une Solution EDI</span><span class="sxs-lookup"><span data-stu-id="0a11c-112">Configuring Ports for an EDI Solution</span></span>](../core/configuring-ports-for-an-edi-solution.md)  
  
-   [<span data-ttu-id="0a11c-113">Configuration des accusés de réception EDI</span><span class="sxs-lookup"><span data-stu-id="0a11c-113">Configuring EDI Acknowledgments</span></span>](../core/configuring-edi-acknowledgments.md)  
  
-   [<span data-ttu-id="0a11c-114">Configuration des lots EDI</span><span class="sxs-lookup"><span data-stu-id="0a11c-114">Configuring EDI Batches</span></span>](../core/configuring-edi-batches.md)  
  
-   [<span data-ttu-id="0a11c-115">Développement des schémas EDI</span><span class="sxs-lookup"><span data-stu-id="0a11c-115">Developing EDI Schemas</span></span>](../core/developing-edi-schemas.md)  
  
-   [<span data-ttu-id="0a11c-116">À l’aide d’outils au moment du Design XML</span><span class="sxs-lookup"><span data-stu-id="0a11c-116">Using Design-Time XML Tools</span></span>](../core/using-design-time-xml-tools.md)  
  
-   [<span data-ttu-id="0a11c-117">Propriétés de contexte EDI</span><span class="sxs-lookup"><span data-stu-id="0a11c-117">EDI Context Properties</span></span>](../core/edi-context-properties.md)  
  
-   [<span data-ttu-id="0a11c-118">Propriétés de contexte de remplacement EDI</span><span class="sxs-lookup"><span data-stu-id="0a11c-118">EDI Override Context Properties</span></span>](../core/edi-override-context-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="0a11c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a11c-119">See Also</span></span>  

[<span data-ttu-id="0a11c-120">Didacticiels et procédures pas à pas pour EDI, AS2 et EDIFACT</span><span class="sxs-lookup"><span data-stu-id="0a11c-120">Tutorials and walkthroughs for EDI, AS2, and EDIFACT</span></span>](../core/tutorials-and-walkthroughs-for-edi-as2-and-edifact.md)  
[<span data-ttu-id="0a11c-121">Développement et la configuration des Solutions AS2 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="0a11c-121">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)