---
title: "La restauration des Applications et d’activer le traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83144965-a51a-481a-afd6-7f573b69badb
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65ae913d45f45b13458294863714823a41ff4e44
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-restore-applications-and-enable-processing"></a><span data-ttu-id="2e215-102">La restauration des Applications et d’activer le traitement</span><span class="sxs-lookup"><span data-stu-id="2e215-102">How to Restore Applications and Enable Processing</span></span>
<span data-ttu-id="2e215-103">Configurer les applications dans le groupe BizTalk et activer le traitement de l’application après avoir suivi les étapes décrites dans la rubrique [comment mettre à jour les ordinateurs Runtime](../technical-guides/how-to-update-the-runtime-computers.md).</span><span class="sxs-lookup"><span data-stu-id="2e215-103">Configure the applications in the BizTalk group and enable application processing after following the steps described in the topic [How to Update the Runtime Computers](../technical-guides/how-to-update-the-runtime-computers.md).</span></span>  
  
### <a name="to-enable-application-configuration-and-restore-application-processing"></a><span data-ttu-id="2e215-104">Pour activer la configuration de l’application et de restauration de traitement de l’application</span><span class="sxs-lookup"><span data-stu-id="2e215-104">To enable application configuration and restore application processing</span></span>  
  
1.  <span data-ttu-id="2e215-105">Exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Installation msi sur chaque serveur BizTalk server dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="2e215-105">Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Installation MSI file on each BizTalk server in the group.</span></span>  
  
2.  <span data-ttu-id="2e215-106">Exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fichier MSI de Configuration d’Application sur un serveur dans le groupe pour configurer l’application pour le site de récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="2e215-106">Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Configuration MSI file on one server in the group to configure the application for the disaster recovery site.</span></span> <span data-ttu-id="2e215-107">Les noms pour les emplacements de réception et envoyer des ports restent les mêmes.</span><span class="sxs-lookup"><span data-stu-id="2e215-107">The names for receive locations and send ports remain the same.</span></span> <span data-ttu-id="2e215-108">Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fichier MSI de Configuration d’Application met à jour les liaisons de sorte que ces artefacts pointent vers les emplacements appropriés dans l’environnement de récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="2e215-108">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Configuration MSI file updates bindings so that these artifacts point to the correct locations in the disaster recovery environment.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e215-109">Si les emplacements de réception et d’envoyer des ports ne sont pas affectés par la perte du site de production, il ne peut pas être nécessaire de reconfigurer l’application à des emplacements spécifiques de la récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="2e215-109">If receive locations and send ports are not affected by the loss of the production site, it may not be necessary to reconfigure the application with disaster recovery-specific locations.</span></span>  
  
3.  <span data-ttu-id="2e215-110">Restauration de traitement de l’application en activant l’application de tous les emplacements de réception, ports d’envoi et les instances d’hôte.</span><span class="sxs-lookup"><span data-stu-id="2e215-110">Restore application processing by enabling all application receive locations, send ports, and host instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e215-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e215-111">See Also</span></span>  
 [<span data-ttu-id="2e215-112">Récupération d’ordinateurs de l’exécution</span><span class="sxs-lookup"><span data-stu-id="2e215-112">Recovering the Runtime Computers</span></span>](../technical-guides/recovering-the-runtime-computers.md)