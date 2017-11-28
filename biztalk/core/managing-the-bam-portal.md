---
title: "Gérer le portail BAM dans BizTalk Server | Documents Microsoft"
Description: "Vue d’ensemble de l’installation et la configuration du portail BAM dans BizTalk Server"
ms.custom: 
ms.date: 08/15/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a08aa85-3a45-4a8c-bdb5-5615ca097ce1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d7908c9c7ce8e4b731e0b88569e3dc3fb228a1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-the-bam-portal"></a><span data-ttu-id="71b61-103">Gérer le portail BAM</span><span class="sxs-lookup"><span data-stu-id="71b61-103">Manage the BAM portal</span></span>

## <a name="set-up-bam-portal"></a><span data-ttu-id="71b61-104">Configurer le portail BAM</span><span class="sxs-lookup"><span data-stu-id="71b61-104">Set up BAM portal</span></span>
<span data-ttu-id="71b61-105">En tant qu'administrateur, vous pouvez configurer le portail BAM en exécutant le programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71b61-105">Administrators set up the BAM portal by running the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span></span> <span data-ttu-id="71b61-106">Les outils de configuration de BizTalk Server permettent d'indiquer si le composant BAM est activé, de spécifier les comptes de service Web, les groupes Windows autorisés à afficher le portail ainsi que le site Web destiné à héberger ce portail.</span><span class="sxs-lookup"><span data-stu-id="71b61-106">Use the BizTalk Server configuration tool to specify whether BAM is enabled, and to specify the Web service accounts, the Windows groups that can view portal, and the Web site that will host the portal.</span></span> <span data-ttu-id="71b61-107">Lorsqu'il s'avère nécessaire de mettre à jour la configuration du portail BAM après l'avoir installé, utilisez l'outil de configuration afin de mettre à jour les paramètres tels que le groupe d'utilisateurs du portail, le compte du pool d'applications et l'utilisateur des services Web de gestion.</span><span class="sxs-lookup"><span data-stu-id="71b61-107">If it becomes necessary to update the BAM portal configuration once you have set up the BAM portal, you use the configuration tool to update the configuration settings such as the portal users group, the Application Pool account, and the management Web services user.</span></span>  
  
 <span data-ttu-id="71b61-108">Pour plus d’informations sur l’installation du portail BAM, consultez [Install and Configure le BAM dans plusieurs environnements d’ordinateur](http://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx).</span><span class="sxs-lookup"><span data-stu-id="71b61-108">For more information about installing the BAM portal, see [Install and Configure BAM in Multiple Computer Environments](http://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx).</span></span>  
  
 <span data-ttu-id="71b61-109">Pour plus d’informations sur la configuration du portail BAM, consultez [configurer BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="71b61-109">For more information about configuring the BAM portal, see [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).</span></span>
  
 <span data-ttu-id="71b61-110">Le portail BAM est doté de nombreux paramètres personnalisables par modification du fichier webconfig.xml.</span><span class="sxs-lookup"><span data-stu-id="71b61-110">The BAM portal has many customizable settings that are accessed by modifying the webconfig.xml file.</span></span> <span data-ttu-id="71b61-111">Ces paramètres permettent de contrôler les performances et le fonctionnement du portail.</span><span class="sxs-lookup"><span data-stu-id="71b61-111">These settings control the performance and operation of the BAM portal.</span></span> <span data-ttu-id="71b61-112">Le reste de cette section décrit la procédure de personnalisation de la configuration de votre portail BAM.</span><span class="sxs-lookup"><span data-stu-id="71b61-112">This rest of this section describes how to customize your BAM portal configuration.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="71b61-113">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="71b61-113">Next steps</span></span> 
  
-   [<span data-ttu-id="71b61-114">Personnalisation de la Configuration du portail BAM</span><span class="sxs-lookup"><span data-stu-id="71b61-114">Customizing the BAM Portal Configuration</span></span>](../core/customizing-the-bam-portal-configuration.md)  
  
-   [<span data-ttu-id="71b61-115">Comment configurer le portail BAM pour travailler sur un Cluster d’équilibrage de charge réseau</span><span class="sxs-lookup"><span data-stu-id="71b61-115">How to Configure the BAM Portal to Work on an NLB Cluster</span></span>](../core/how-to-configure-the-bam-portal-to-work-on-an-nlb-cluster.md)  
  
## <a name="see-also"></a><span data-ttu-id="71b61-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71b61-116">See Also</span></span>  
 [<span data-ttu-id="71b61-117">Gestion de l’Infrastructure dynamique BAM</span><span class="sxs-lookup"><span data-stu-id="71b61-117">Managing the BAM Dynamic Infrastructure</span></span>](../core/managing-the-bam-dynamic-infrastructure.md)