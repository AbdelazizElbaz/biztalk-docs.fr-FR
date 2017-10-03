---
title: "Comment activer les Services de Notifications sur d’autres ordinateurs dans un groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 571d6b45-b0cc-47f2-bed3-7c6f3e70decc
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b65596e59820258df01a5655ea30adafe439674
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-notifications-services-on-additional-computers-in-a-group"></a>Activation des services de notification sur les autres ordinateurs d'un groupe
Lorsque vous exécutez l'analyse BAM dans un environnement multiserveur, vous devez activer les services Notification Services sur tous les ordinateurs sur lesquels vous envisagez d'exécuter l'utilitaire de gestion de l'analyse BAM afin de déployer une activité.  
  
 Examinez le cas suivant :  
  
-   Le groupe A est composé des ordinateurs suivants :  
  
    -   L'ordinateur 1 sert à administrer l'analyse BAM.  
  
    -   L'ordinateur 2 héberge les bases de données de schémas en étoile et BAM PIT.  
  
    -   L'ordinateur 3 héberge les bases de données d'analyse et d'archives BAM.  
  
    -   L'ordinateur 4 héberge les bases de données d'alertes BAM.  
  
    -   L'ordinateur 5 héberge le reste des bases de données de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Groupe B :  
  
    -   L'ordinateur 6 sert à l'administration de l'analyse BAM. Il contient toutes les bases de données partagées avec le groupe A.  
  
 Pour pouvoir déployer une activité dans les bases de données du groupe A à partir de l'ordinateur du groupe B, vous devez commencer par inscrire les services Notification Services avec le serveur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les hébergeant. Si ces services ne sont pas inscrits, vous recevrez le message d'erreur suivant :  
  
 Déploiement de l'alerte en cours... Erreur : Échec du déploiement de l’analyse BAM.  
  
 Les alertes n'ont pas été déployées.  
  
 Une exception a été levée par la cible d'un appel.  
  
 Les entrées de registre de l'instance spécifiée de Notification Services sont introuvables.  
  
### <a name="to-register-notifications-services-additional-computers"></a>Pour inscrire les services Notification Services sur d'autres ordinateurs  
  
1.  Sur l’ordinateur du groupe supplémentaire, cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2005**, cliquez sur **outils de Configuration**, puis cliquez sur **invite de commandes de Notification Services**.  
  
2.  À l’invite de commandes, tapez : **nscontrol register - nom \<NS du préfixe de nom choisie au config >-server \<serveur ns db sql >**. Cette commande permet à Notification Services de se connecter à la base de données appropriée (ces informations sont conservées par nscontrol dans le registre de l'ordinateur du service).  
  
## <a name="see-also"></a>Voir aussi  
 [Modification des paramètres d’exécution BAM](../core/changing-bam-runtime-settings.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)