---
title: "Comment configurer la Navigation entre Distributed activités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f8faf0a-eb06-4383-932d-4106306d6cf3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88c0a1cf8d82ee5cd4e48e176b5b7f633101d8c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-navigation-between-distributed-activities"></a>Configuration de la navigation entre les activités distribuées
La navigation distribuée permet aux utilisateurs d'afficher les activités qui existent dans des déploiements BAM distants. Lorsque vous activez la navigation distribuée, les personnes qui utilisent le portail BAM sur un ordinateur peuvent afficher les activités sur le portail BAM dans un autre déploiement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 La procédure de cette rubrique décrit l'activation de la navigation distribuée dans le scénario suivant :  
  
-   Un service commercial avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déployé sur l'ordinateur 1.  
  
-   Un service d'expédition avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déployé sur l'ordinateur 2 (computer2).  
  
-   Une vue nommée myBusinessView avec une activité nommée Sales Data déployée sur l'ordinateur 1.  
  
-   Une vue nommée myBusinessView avec une activité nommée Shipping Data installée sur l'ordinateur 2 (computer2).  
  
-   Un utilisateur des activités dans le service commercial ayant besoin d'afficher les activités sur les deux ordinateurs.  
  
### <a name="how-to-set-up-distributed-navigation-for-remote-activities"></a>Configuration de la navigation distribuée pour les activités distantes  
  
1.  L’administrateur de l’ordinateur 1 accorde les activités utilisateur l’accès à la vue myBusinessView sur l’ordinateur 1. Vous utilisez la commande bm.exe, comme suit : **ajouter-account - AccountName :\<nom du compte >-affichage :** myBusinessView  
  
2.  L’administrateur de l’ordinateur 1 active la navigation distribuée en exécutant la commande enable-reference, comme suit : **bm.exe enable-reference - TargetServer :** Ordinateur2 **- TargetDatabase :\<cible base de données >**  
  
    > [!NOTE]
    >  En général, le compte utilisé entre les services pour l'accès aux services Web BAM diffère selon l'ordinateur. Par conséquent, dans ce scénario, l’administrateur de l’ordinateur 1 doit ajouter le compte d’emprunt d’identité de services Web de l’ordinateur 1 au rôle BAM_ManagementWS de la base de données d’importation principale BAM pour l’ordinateur 2. Pour plus d’informations, consultez « Affichage et modification des appartenances au rôle » à [http://go.microsoft.com/fwlink/?LinkId=66990](http://go.microsoft.com/fwlink/?LinkId=66990).  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
3.  L'administrateur de l'ordinateur 2 accorde à l'utilisateur des activités l'accès à la vue myBusinessView sur l'ordinateur 2 à l'aide de la commande BM.exe, comme cela est indiqué à l'étape 1.  
  
## <a name="results-of-setting-up-distributed-navigation"></a>Résultats de la configuration de la navigation distribuée  
 Lorsque la navigation distribuée est activée, les utilisateurs ajoutés aux vues sur les deux ordinateurs voient les activités des vues déployées sur les deux ordinateurs dans le volet Mes vues de leur portail de base. Lorsque ces utilisateurs cliquent sur une activité qui est hébergée sur un déploiement à distance, il est redirigé en toute transparence au portail sur lequel qu’activité est hébergée, et ils sont en mesure d’afficher l’activité comme s’il se trouvait sur leur portail par défaut.  
  
> [!NOTE]
>  La navigation distribuée peut être activée dans les deux sens. Suivez la procédure ci-dessus sur les deux ordinateurs qui partagent les activités distantes pour permettre aux utilisateurs des activités des portails de l'un des ordinateurs d'utiliser la navigation distribuée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la Navigation distribuée des activités distantes](../core/managing-distributed-navigation-of-remote-activities.md)   
 [Portail BAM](../core/bam-portal.md)