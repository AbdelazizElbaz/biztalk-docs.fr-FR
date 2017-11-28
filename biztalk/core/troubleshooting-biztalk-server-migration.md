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
ms.openlocfilehash: 1dcdb53c7123b4ffaa2294db080e1efc4fb4eb65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-server-migration"></a><span data-ttu-id="5cf69-102">Dépannage de la migration BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="5cf69-102">Troubleshooting BizTalk Server Migration</span></span>
<span data-ttu-id="5cf69-103">Cette section centralise les informations sur les problèmes connus rencontrés lors de la migration d'applications BizTalk depuis [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 vers [!INCLUDE[prague](../includes/prague-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cf69-103">This section provides a centralized location for information about common problems encountered while migrating BizTalk applications from [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 to [!INCLUDE[prague](../includes/prague-md.md)].</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="5cf69-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="5cf69-104">Known Issues</span></span>  
  
#### <a name="custom-applications-might-not-work-while-upgrading"></a><span data-ttu-id="5cf69-105">Les applications personnalisées ne fonctionnent pas pendant la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="5cf69-105">Custom applications might not work while upgrading</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="5cf69-106">Problème</span><span class="sxs-lookup"><span data-stu-id="5cf69-106">Problem</span></span>  
 <span data-ttu-id="5cf69-107">Certaines applications personnalisées ne fonctionnent pas pendant la mise à niveau depuis [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 vers [!INCLUDE[prague](../includes/prague-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cf69-107">While upgrading from [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 to [!INCLUDE[prague](../includes/prague-md.md)], some custom applications might not work.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="5cf69-108">Cause</span><span class="sxs-lookup"><span data-stu-id="5cf69-108">Cause</span></span>  
 <span data-ttu-id="5cf69-109">Tous les composants de code géré de BizTalk s'exécutent sous CLR 4.0.</span><span class="sxs-lookup"><span data-stu-id="5cf69-109">All the BizTalk managed code components run on CLR 4.0.</span></span> <span data-ttu-id="5cf69-110">La compilation de ces composants s'effectuant par rapport à [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], ils nécessitent un fichier de configuration pour pouvoir s'exécuter sous CLR 4.0.</span><span class="sxs-lookup"><span data-stu-id="5cf69-110">As these components are compiled against [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], they need a config file to run in CLR 4.0.</span></span>  
  
##### <a name="solution"></a><span data-ttu-id="5cf69-111">Solution</span><span class="sxs-lookup"><span data-stu-id="5cf69-111">Solution</span></span>  
 <span data-ttu-id="5cf69-112">Pour résoudre ce problème, mettez le fichier de configuration à jour.</span><span class="sxs-lookup"><span data-stu-id="5cf69-112">To resolve this issue, update the config file.</span></span>  
  
```  
<configuration>  
<startup useLegacyV2RuntimeActivationPolicy="true">  
<supportedRuntime version="v4.0" />  
</startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cf69-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cf69-113">See Also</span></span>  
 [<span data-ttu-id="5cf69-114">Dépannage</span><span class="sxs-lookup"><span data-stu-id="5cf69-114">Troubleshooting</span></span>](../core/troubleshooting.md)