---
title: "Guide des opérations BizTalk Server 2010 | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dc0d8e9-9ad6-4ce1-8ca7-399b67cb360e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 886dc607f0d133392b522a13ec15026a0f421f40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-2010-operations-guide"></a>Guide des opérations BizTalk Server 2010
Bienvenue dans le Guide des opérations Microsoft® BizTalk® Server 2010. Nous avons créé ce guide pour être une ressource précieuse pour toute personne impliquée dans l’implémentation et l’administration d’une solution BizTalk, en particulier les professionnels de l’informatique.  
  
 Pour télécharger une copie de ce guide sous forme de chm, pdf ou docx, accédez à [Guide des opérations Microsoft BizTalk Server 2010](http://go.microsoft.com/fwlink/?LinkId=212652) (http://go.microsoft.com/fwlink/?LinkId=212652).  
  
## <a name="which-versions-of-biztalk-server-does-the-guide-cover"></a>Les Versions de BizTalk Server couvre le Guide ?  
 Ce guide répond aux besoins [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] et fournit des informations de disponibilité opérationnelle pour vous aider à accélérer avec votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] le programme d’installation.  
  
> [!NOTE]
>  Pour voir le Guide des opérations de [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] ou [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)], consultez [http://go.microsoft.com/fwlink/?LinkID=130458](http://go.microsoft.com/fwlink/?LinkID=130458).  
  
## <a name="where-do-i-start"></a>Où commencer ?  
 Nous organisées le guide selon les aspects fonctionnels de la planification, de déploiement et de gestion une [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation. Vous pouvez donc le lire en fonction de ces aspects fonctionnels. Toutefois, vous devez savoir que les listes de contrôle serait plus recherché après les informations contenues dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Operations Guide, nous avons classé les listes de contrôle dans le document dans le tableau suivant pour faciliter l’accessibilité.  
  
|||  
|-|-|  
|**Configuration de votre environnement BizTalk**|**Configuration d’une haute disponibilité et l’environnement de récupération d’urgence**|  
|-   [Liste de vérification : Mise en route avec BizTalk Server](http://msdn.microsoft.com/library/37d265cd-c393-46ac-ac21-129a1511359b)<br />-   [Liste de vérification : Configuration de Windows Server](~/technical-guides/checklist-configuring-windows-server.md)<br />-   [Liste de vérification : Configuration d’Internet Information Services](~/technical-guides/checklist-configuring-internet-information-services.md)<br />-   [Liste de vérification : Configuration de SQL Server](../technical-guides/checklist-configuring-sql-server.md)<br />-   [Liste de vérification : Configuration de BizTalk Server](~/technical-guides/checklist-configuring-biztalk-server.md)|-   [Liste de vérification : Offrant une haute disponibilité avec une tolérance de panne ou l’équilibrage de charge](~/technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)<br />-   [Liste de vérification : Accroître la disponibilité avec la récupération d’urgence](~/technical-guides/checklist-increasing-availability-with-disaster-recovery.md)|  
|**Surveillance, le test et résolution des problèmes**|**Performances et Maintenance**|  
|-   [Liste de vérification : Analyse opérationnelle](~/technical-guides/checklist-monitoring-operational-readiness.md)<br />-   [Liste de vérification : Gestion et résolution des problèmes de bases de données BizTalk Server](../technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)<br />-   [Liste de vérification : Test opérationnelle](~/technical-guides/checklist-testing-operational-readiness.md)<br />-   [Liste de vérification : Analyse de BizTalk Server avec Operations Manager 2007](~/technical-guides/checklist-monitoring-biztalk-server-with-operations-manager-2007.md)<br />-   [Liste de vérification : Analyse des serveurs SQL Server](~/technical-guides/checklist-monitoring-sql-servers.md)|Listes de contrôle liée à la maintenance :<br /><br /> -   [Liste de vérification : Effectuer des vérifications de Maintenance quotidienne](~/technical-guides/checklist-performing-daily-maintenance-checks.md)<br />-   [Liste de vérification : Effectuer des vérifications de Maintenance hebdomadaire](~/technical-guides/checklist-performing-weekly-maintenance-checks.md)<br />-   [Liste de vérification : Effectuer des vérifications de Maintenance mensuelle](~/technical-guides/checklist-performing-monthly-maintenance-checks.md)<br /><br /> Performances liées aux listes de vérification :<br /><br /> -   [Liste de vérification : Effectuer des vérifications de performances hebdomadaire](~/technical-guides/checklist-performing-weekly-performance-checks.md)<br />-   [Liste de vérification : Effectuer des vérifications de performances mensuel](~/technical-guides/checklist-performing-monthly-performance-checks.md)|  
|**Listes de contrôle pour les autres tâches importantes**||  
|-   [Liste de vérification : Déploiement d’une Application](~/technical-guides/checklist-deploying-an-application.md)<br />-   [Liste de vérification : Exportation des liaisons à partir d’une Application vers un autre](~/technical-guides/checklist-exporting-bindings-from-one-application-to-another.md)<br />-   [Liste de vérification : Mise à jour d’un Assembly](~/technical-guides/checklist-updating-an-assembly.md)<br />-   [Liste de vérification : Mise à jour des artefacts dans une Application BizTalk](~/technical-guides/checklist-updating-artifacts-in-a-biztalk-application.md)|-   [Liste de vérification : Mise à jour d’une Application à l’aide du contrôle de version côte à côte](~/technical-guides/checklist-updating-an-application-using-side-by-side-versioning.md)<br />-   [Liste de vérification : Mise à jour d’une Orchestration à l’aide du contrôle de version côte à côte](~/technical-guides/checklist-updating-an-orchestration-using-side-by-side-versioning.md)<br />-   [Liste de vérification : Installation et configuration des certificats](../technical-guides/checklist-installing-and-configuring-certificates.md)<br />-   [Liste de vérification : Planification des opérations dans un environnement sécurisé](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md)|  
  
 Si vous effectuez les tâches suivantes, vous pouvez démarrer avec les rubriques connexes :  
  
-   **L’évaluation opérationnelle**: Si vous avez le focus sur l’évaluation et l’évaluation de l’état de préparation d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement, puis commencez par lire la [opérations des listes de contrôle](~/technical-guides/operations-checklists.md) et [ Augmentation de la disponibilité de BizTalk Server](~/technical-guides/increasing-availability-for-biztalk-server.md) sections.  
  
-   **Sur le plan opérationnel préparation**: pour vous assurer que votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] infrastructure et les applications soient prêtes sur le plan opérationnel, reportez-vous à la [planification de l’environnement pour BizTalk Server](~/technical-guides/planning-the-environment-for-biztalk-server.md) section.  
  
-   **Gestion d’un environnement d’exploitation**: la plupart des rubriques dans le guide des opérations vous aide à maintenir un fonctionnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement. Vous trouverez meilleures pratiques, les concepts clés et les procédures pour la gestion d’un environnement d’exploitation dans les sections suivantes : [augmenter la disponibilité de BizTalk Server](~/technical-guides/increasing-availability-for-biztalk-server.md), [analyse de BizTalk Server](~/technical-guides/monitoring-biztalk-server2.md), et [maintenance BizTalk Server2](~/technical-guides/maintaining-biztalk-server2.md).  
  
## <a name="whats-in-it"></a>Qu’est qu’elle contient ?  
 Conseils sur l’expérience du monde réel. L’idée du repère émane de représentants Microsoft, les organisations partenaires et les clients qui planifient, déployer et gérer les installations de BizTalk Server. Ce groupe de professionnels de l’informatique ont été accumulées expérience pratique avec des solutions d’une plage divers de BizTalk. Comme leur expérience ils créé des listes de contrôle, meilleures pratiques et des présentations pour guider futures [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] operations. Nous collectées et organiser ces informations pour créer le repère.  
  
 Parties de ce guide sont nouveaux ; Toutefois, une partie importante fait référence à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide, des livres blancs, des articles de la Base de connaissances et d’autres sources. Il a été soigneusement examiné et contrôlé par des experts de la Communauté de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] professionnels de l’informatique et les membres de l’équipe de développement de produit, qui nous accuser réception grandement appréciées à la fin de cette rubrique. Nous pensons que les informations présentées ici aidera [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisateurs résoudre et avant tout, éviter la plupart des problèmes courants qui peuvent se produire pendant le déploiement et la gestion d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.  
  
## <a name="acknowledgments"></a>Accusés de réception  
 Nous dans les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] équipe User Education reconnaissez grandement appréciées la contribution en attente de personnes suivantes pour fournir des commentaires techniques ainsi que beaucoup de contenu pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operations Guide :  
  
-   Paolo Salvatori, Tim Wieman