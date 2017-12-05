---
title: "Résolution des problèmes de Migration BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6eddc0a-2403-4bcd-9327-23f51ce7d57b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ddb6d9780a86183de5a09791de44adda5d57dab
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="troubleshooting-biztalk-server-migration"></a><span data-ttu-id="02fa5-102">Dépannage de la migration BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="02fa5-102">Troubleshooting BizTalk Server Migration</span></span>
<span data-ttu-id="02fa5-103">Cette section fournit un emplacement centralisé pour plus d’informations sur les problèmes connus rencontrés lors de la migration d’applications BizTalk à partir de [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 vers BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="02fa5-103">This section provides a centralized location for information about common problems encountered while migrating BizTalk applications from [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 to BizTalk Server.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="02fa5-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="02fa5-104">Known Issues</span></span>  
  
#### <a name="custom-applications-might-not-work-while-upgrading"></a><span data-ttu-id="02fa5-105">Les applications personnalisées ne fonctionnent pas pendant la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="02fa5-105">Custom applications might not work while upgrading</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="02fa5-106">Problème</span><span class="sxs-lookup"><span data-stu-id="02fa5-106">Problem</span></span>  
 <span data-ttu-id="02fa5-107">Lors de la mise à niveau à partir de [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 vers BizTalk Server, certaines applications personnalisées ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="02fa5-107">While upgrading from [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 to BizTalk Server, some custom applications might not work.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="02fa5-108">Cause</span><span class="sxs-lookup"><span data-stu-id="02fa5-108">Cause</span></span>  
 <span data-ttu-id="02fa5-109">Tous les composants de code géré de BizTalk s'exécutent sous CLR 4.0.</span><span class="sxs-lookup"><span data-stu-id="02fa5-109">All the BizTalk managed code components run on CLR 4.0.</span></span> <span data-ttu-id="02fa5-110">La compilation de ces composants s'effectuant par rapport à [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], ils nécessitent un fichier de configuration pour pouvoir s'exécuter sous CLR 4.0.</span><span class="sxs-lookup"><span data-stu-id="02fa5-110">As these components are compiled against [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], they need a config file to run in CLR 4.0.</span></span>  
  
##### <a name="solution"></a><span data-ttu-id="02fa5-111">Solution</span><span class="sxs-lookup"><span data-stu-id="02fa5-111">Solution</span></span>  
 <span data-ttu-id="02fa5-112">Pour résoudre ce problème, mettez le fichier de configuration à jour.</span><span class="sxs-lookup"><span data-stu-id="02fa5-112">To resolve this issue, update the config file.</span></span>  
  
```  
<configuration>  
<startup useLegacyV2RuntimeActivationPolicy="true">  
<supportedRuntime version="v4.0" />  
</startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02fa5-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02fa5-113">See Also</span></span>  
 [<span data-ttu-id="02fa5-114">Dépannage</span><span class="sxs-lookup"><span data-stu-id="02fa5-114">Troubleshooting</span></span>](../core/troubleshooting.md)