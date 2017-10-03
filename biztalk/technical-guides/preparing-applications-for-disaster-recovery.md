---
title: "Préparation d’Applications pour la récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0ef93099-aa6b-424a-a4ce-87d855c6afe3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7028b1386f71f653dfc41b9de2522cdbd8d02126
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="preparing-applications-for-disaster-recovery"></a><span data-ttu-id="3e113-102">Préparation d’Applications pour la récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="3e113-102">Preparing Applications for Disaster Recovery</span></span>
<span data-ttu-id="3e113-103">Les applications BizTalk (fichiers binaires et les artefacts d’une configuration comme emplacements de réception et ports d’envoi) sont déployées sur le groupe BizTalk de production lorsque le groupe est restauré sur le site de récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="3e113-103">BizTalk applications (binaries and configuration artifacts such as receive locations and send ports) are deployed to the production BizTalk group when the group is restored at the disaster recovery site.</span></span> <span data-ttu-id="3e113-104">Cette configuration devra peut-être être modifiée selon que des emplacements de configuration telles que les emplacements de réception et les ports d’envoi qui sont spécifiques à la production.</span><span class="sxs-lookup"><span data-stu-id="3e113-104">This configuration may have to be altered depending on whether there are configuration locations such as receive locations and send ports that are production-specific.</span></span>  
  
 <span data-ttu-id="3e113-105">Pour accélérer la restauration des applications sur le site de récupération d’urgence, un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fichier .msi qui installe les fichiers binaires sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serveurs d’exécution doivent être mis à jour sur la récupération d’urgence [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serveurs de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3e113-105">To speed the restoration of applications at the disaster recovery site, a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] .msi file that installs the binaries on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers must be kept up-to-date on the disaster recovery [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers.</span></span> <span data-ttu-id="3e113-106">Lorsque le groupe BizTalk de production est restauré sur le site de récupération d’urgence, un fichier de .msi de configuration application spécifique à la récupération d’urgence peut doivent être installées pour configurer l’application pour les artefacts de spécifiques de la récupération d’urgence, tels que emplacements de réception et ports d’envoi, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3e113-106">When the production BizTalk group is restored at the disaster recovery site, a disaster recovery-specific application configuration .msi file may need to be installed in order to configure the application for disaster recovery-specific artifacts, such as receive locations and send ports, as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e113-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e113-107">See Also</span></span>  
 [<span data-ttu-id="3e113-108">Déploiement d’une Application</span><span class="sxs-lookup"><span data-stu-id="3e113-108">Deploying an Application</span></span>](../technical-guides/deploying-an-application.md)