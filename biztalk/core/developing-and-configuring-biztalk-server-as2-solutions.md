---
title: "Développement et la configuration des Solutions AS2 BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62aa76f2-b692-41d9-862a-3e0089635800
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3cd1bfb6bba469f6096242f3e57fd199a4439e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-and-configuring-biztalk-server-as2-solutions"></a><span data-ttu-id="dca14-102">Développement et configuration de solutions AS2 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="dca14-102">Developing and Configuring BizTalk Server AS2 Solutions</span></span>
## <a name="overview"></a><span data-ttu-id="dca14-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="dca14-103">Overview</span></span>
<span data-ttu-id="dca14-104">Informations destinées aux développeurs créer des solutions BizTalk AS2.</span><span class="sxs-lookup"><span data-stu-id="dca14-104">Information for developers to create BizTalk AS2 solutions.</span></span> <span data-ttu-id="dca14-105">Ces solutions sont créées à l’aide de l’environnement de conception du système de projet BizTalk et le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="dca14-105">These solutions are created using the BizTalk project system design environment and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>
  
 <span data-ttu-id="dca14-106">Avant de développer une solution AS2 BizTalk Server, assurez-vous d'avoir correctement installé et configuré [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec les fonctionnalités AS2.</span><span class="sxs-lookup"><span data-stu-id="dca14-106">Before developing a BizTalk Server AS2 solution, make sure that you have fully installed and configured [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with the AS2 feature.</span></span> <span data-ttu-id="dca14-107">Consultez [BizTalk Server - Nouveautés, Installation, Configuration et mise à niveau](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span><span class="sxs-lookup"><span data-stu-id="dca14-107">See [BizTalk Server - What's New, Installation, Configuration, and Upgrade](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span> <span data-ttu-id="dca14-108">Pour la configuration AS2 spécifiques supplémentaire requis pour développer une solution EDI, consultez [à la configuration des étapes pour optimiser votre environnement](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).</span><span class="sxs-lookup"><span data-stu-id="dca14-108">For additional AS2-specific configuration that is required for developing an EDI solution, see [Post-configuration steps to optimize your environment](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="dca14-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dca14-109">In This Section</span></span>  
  
-   [<span data-ttu-id="dca14-110">Envoyer un Message AS2 via un Port d’envoi de fichier</span><span class="sxs-lookup"><span data-stu-id="dca14-110">Sending an AS2 Message over a FILE Send Port</span></span>](../core/sending-an-as2-message-over-a-file-send-port.md)  
  
-   [<span data-ttu-id="dca14-111">Configuration des propriétés AS2</span><span class="sxs-lookup"><span data-stu-id="dca14-111">Configuring AS2 Properties</span></span>](../core/configuring-as2-properties.md)  
  
-   [<span data-ttu-id="dca14-112">Configuration des propriétés de Pipeline AS2</span><span class="sxs-lookup"><span data-stu-id="dca14-112">Configuring AS2 Pipeline Properties</span></span>](../core/configuring-as2-pipeline-properties.md)  
  
-   [<span data-ttu-id="dca14-113">Configuration des Ports pour une Solution AS2</span><span class="sxs-lookup"><span data-stu-id="dca14-113">Configuring Ports for an AS2 Solution</span></span>](../core/configuring-ports-for-an-as2-solution.md)  
  
-   [<span data-ttu-id="dca14-114">Sécurité AS2</span><span class="sxs-lookup"><span data-stu-id="dca14-114">AS2 Security</span></span>](../core/as2-security.md)  
  
-   [<span data-ttu-id="dca14-115">L’écriture des propriétés de contexte AS2 pour la résolution du tiers sortante</span><span class="sxs-lookup"><span data-stu-id="dca14-115">Writing AS2 Context Properties for Outbound Party Resolution</span></span>](../core/writing-as2-context-properties-for-outbound-party-resolution.md)  
  
-   [<span data-ttu-id="dca14-116">AS2 Propriétés de contexte</span><span class="sxs-lookup"><span data-stu-id="dca14-116">AS2 Context Properties</span></span>](../core/as2-context-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="dca14-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dca14-117">See Also</span></span>  
[<span data-ttu-id="dca14-118">Didacticiels et procédures pas à pas pour EDI, AS2 et EDIFACT</span><span class="sxs-lookup"><span data-stu-id="dca14-118">Tutorials and walkthroughs for EDI, AS2, and EDIFACT</span></span>](../core/tutorials-and-walkthroughs-for-edi-as2-and-edifact.md)  
[<span data-ttu-id="dca14-119">Développement et la configuration des Solutions EDI BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="dca14-119">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)