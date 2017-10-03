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
ms.openlocfilehash: 27e7095c73cd337a1fb08f2d867e817ad5838206
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="msmqt-deprecation"></a><span data-ttu-id="c0828-102">Suppression de MSMQT</span><span class="sxs-lookup"><span data-stu-id="c0828-102">MSMQT Deprecation</span></span>
<span data-ttu-id="c0828-103">La fonctionnalité MSMQT a été supprimée de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c0828-103">The MSMQT feature has been removed from BizTalk Server.</span></span> <span data-ttu-id="c0828-104">Dans le Concepteur d’Orchestration, l’option de transport MSMQT reste disponible dans l’Assistant Configuration du Port au moment du design, comme indiqué dans l’image ci-dessous lorsque vous choisissez la **spécifier maintenant** est définie sur **deliaisondePort**.</span><span class="sxs-lookup"><span data-stu-id="c0828-104">In Orchestration Designer, the MSMQT transport option remains available in the design-time Port Configuration Wizard as shown in the image below when you choose the **Specify now** option for **Port binding**.</span></span>  
  
 <span data-ttu-id="c0828-105">**Assistant Configuration du port montrant le transport MSMQT**</span><span class="sxs-lookup"><span data-stu-id="c0828-105">**Port Configuration Wizard showing MSMQT transport**</span></span>  
  
 ![](../core/media/portconfigurationwizard-msmqt-transport.gif "PortConfigurationWizard_MSMQT_Transport")  
  
## <a name="biztalk-server-projects"></a><span data-ttu-id="c0828-106">Projets BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c0828-106">BizTalk Server Projects</span></span>  
 <span data-ttu-id="c0828-107">Les nouveaux projets [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne doivent pas utiliser l'option de transport MSMQT.</span><span class="sxs-lookup"><span data-stu-id="c0828-107">New [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projects should not use the MSMQT transport option.</span></span> <span data-ttu-id="c0828-108">Déploiement d’application à [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] échoue avec l’erreur **le type de protocole « MSMQT » introuvable**.</span><span class="sxs-lookup"><span data-stu-id="c0828-108">Application deployment to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] will fail with the error **Protocol type “MSMQT” not found**.</span></span>  
  
## <a name="migrated-biztalk-server-projects"></a><span data-ttu-id="c0828-109">Projets BizTalk Server migrés</span><span class="sxs-lookup"><span data-stu-id="c0828-109">Migrated BizTalk Server Projects</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c0828-110">les projets peuvent être migrés vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] à l’aide de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] comme indiqué dans l’Assistant Conversion [migration d’un projet BizTalk Server](../core/migrating-a-biztalk-server-project.md).</span><span class="sxs-lookup"><span data-stu-id="c0828-110"> projects can be migrated to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] by using the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Conversion Wizard as documented in [Migrating a BizTalk Server Project](../core/migrating-a-biztalk-server-project.md).</span></span> <span data-ttu-id="c0828-111">Les projets contenant des ports configurés pour utiliser le transport MSMQT doivent être reconfigurés manuellement avant leur déploiement vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0828-111">Projects containing ports configured to use the MSMQT transport must be manually reconfigured before deployment to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span> <span data-ttu-id="c0828-112">La reconfiguration recommandée consiste à utiliser l'adaptateur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c0828-112">The recommended reconfiguration is to use the MSMQ adapter.</span></span>  <span data-ttu-id="c0828-113">Pour plus d’informations sur l’adaptateur MSMQ, consultez [quel est l’adaptateur MSMQ ?](../core/what-is-the-msmq-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="c0828-113">For more information about the MSMQ adapter see [What Is the MSMQ Adapter?](../core/what-is-the-msmq-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0828-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0828-114">See Also</span></span>  
 [<span data-ttu-id="c0828-115">Migration à partir de l’adaptateur MSMQT vers l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="c0828-115">Migrating from the MSMQT Adapter to the MSMQ Adapter</span></span>](../core/migrating-from-the-msmqt-adapter-to-the-msmq-adapter.md)