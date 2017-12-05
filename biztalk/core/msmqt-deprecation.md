---
title: Suppression de MSMQT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 007d65ce-d2a2-4602-80c8-55b26617f397
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f869dde7cb4c793e1e36beee6a20bc89d19272e8
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="msmqt-deprecation"></a><span data-ttu-id="cba75-102">Suppression de MSMQT</span><span class="sxs-lookup"><span data-stu-id="cba75-102">MSMQT Deprecation</span></span>
<span data-ttu-id="cba75-103">La fonctionnalité MSMQT a été supprimée de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="cba75-103">The MSMQT feature has been removed from BizTalk Server.</span></span> <span data-ttu-id="cba75-104">Dans le Concepteur d’Orchestration, l’option de transport MSMQT reste disponible dans l’Assistant Configuration du Port au moment du design, comme indiqué dans l’image ci-dessous lorsque vous choisissez la **spécifier maintenant** est définie sur **deliaisondePort**.</span><span class="sxs-lookup"><span data-stu-id="cba75-104">In Orchestration Designer, the MSMQT transport option remains available in the design-time Port Configuration Wizard as shown in the image below when you choose the **Specify now** option for **Port binding**.</span></span>  
  
 <span data-ttu-id="cba75-105">**Assistant Configuration du port montrant le transport MSMQT**</span><span class="sxs-lookup"><span data-stu-id="cba75-105">**Port Configuration Wizard showing MSMQT transport**</span></span>  
  
 <span data-ttu-id="cba75-106">![](../core/media/portconfigurationwizard-msmqt-transport.gif "PortConfigurationWizard_MSMQT_Transport")</span><span class="sxs-lookup"><span data-stu-id="cba75-106">![](../core/media/portconfigurationwizard-msmqt-transport.gif "PortConfigurationWizard_MSMQT_Transport")</span></span>  
  
## <a name="biztalk-server-projects"></a><span data-ttu-id="cba75-107">Projets BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cba75-107">BizTalk Server Projects</span></span>  
 <span data-ttu-id="cba75-108">Les nouveaux projets [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne doivent pas utiliser l'option de transport MSMQT.</span><span class="sxs-lookup"><span data-stu-id="cba75-108">New [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projects should not use the MSMQT transport option.</span></span> <span data-ttu-id="cba75-109">Déploiement d’application à BizTalk Server échoue avec l’erreur **le type de protocole « MSMQT » introuvable**.</span><span class="sxs-lookup"><span data-stu-id="cba75-109">Application deployment to BizTalk Server will fail with the error **Protocol type “MSMQT” not found**.</span></span>  
  
## <a name="migrated-biztalk-server-projects"></a><span data-ttu-id="cba75-110">Projets BizTalk Server migrés</span><span class="sxs-lookup"><span data-stu-id="cba75-110">Migrated BizTalk Server Projects</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="cba75-111">les projets peuvent être migrés vers BizTalk Server à l’aide de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] comme indiqué dans l’Assistant Conversion [migration d’un projet BizTalk Server](../core/migrating-a-biztalk-server-project.md).</span><span class="sxs-lookup"><span data-stu-id="cba75-111"> projects can be migrated to BizTalk Server by using the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Conversion Wizard as documented in [Migrating a BizTalk Server Project](../core/migrating-a-biztalk-server-project.md).</span></span> <span data-ttu-id="cba75-112">Les projets contenant des ports configurés pour utiliser le transport MSMQT doivent être reconfigurés manuellement avant le déploiement de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="cba75-112">Projects containing ports configured to use the MSMQT transport must be manually reconfigured before deployment to BizTalk Server.</span></span> <span data-ttu-id="cba75-113">La reconfiguration recommandée consiste à utiliser l'adaptateur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="cba75-113">The recommended reconfiguration is to use the MSMQ adapter.</span></span>  <span data-ttu-id="cba75-114">Pour plus d’informations sur l’adaptateur MSMQ, consultez [quel est l’adaptateur MSMQ ?](../core/what-is-the-msmq-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="cba75-114">For more information about the MSMQ adapter see [What Is the MSMQ Adapter?](../core/what-is-the-msmq-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba75-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cba75-115">See Also</span></span>  
 [<span data-ttu-id="cba75-116">Migration de l’adaptateur MSMQT vers l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="cba75-116">Migrating from the MSMQT Adapter to the MSMQ Adapter</span></span>](../core/migrating-from-the-msmqt-adapter-to-the-msmq-adapter.md)