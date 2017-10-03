---
title: "Journaux de BizTalk Server à l’aide de l’adresse IP et un nom de Cluster Windows | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82ef6908-6009-4d06-8315-0bc85a0aad18
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8619ea6c4eea3eefee5b86282a29e0165d0fb074
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-log-shipping-using-a-windows-cluster-name-and-ip-address"></a>BizTalk Server journaux de transaction à l’aide de l’adresse IP et un nom de Cluster Windows
Il est possible de simplifier [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoi de journaux à l’aide de deux instances d’un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster que les serveurs source et de destination dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] scénario de livraison de journal. Puis, dans le cas d’un événement de récupération d’urgence, la récupération de base de données est simplifiée par les de commutation simplement le nom et les ressources d’adresse IP associés avec le cluster [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances comme décrit ci-dessous. Lorsque vous utilisez cette approche il est inutile d’exécuter le script UpdateDatabase.vbs comme décrit dans la rubrique [la restauration de bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md) , car le nom de la base de données reste inchangé.  
  
> [!NOTE]  
>  Pour augmenter la tolérance de panne pour le cluster [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances, le cluster [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances doivent être séparés géographiquement.  
  
### <a name="to-implement-biztalk-server-log-shipping-using-a-windows-server-cluster-name-and-ip-address-resource"></a>Pour implémenter des journaux de BizTalk Server envoi à l’aide d’un nom de Cluster Windows Server et les IP adresse ressource  
  
1.  Arrêter les serveurs BizTalk de production.  
  
2.  Effectuer un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journal de restauration de l’envoi de journaux vers le serveur secondaire [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster.  
  
3.  Suivez les étapes décrites dans la rubrique [configuration de BizTalk Server l’envoi de journaux](../technical-guides/configuring-biztalk-server-log-shipping.md) reconfigurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction afin que la base de données secondaire [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] l’instance de cluster est désormais le groupe source et le serveur principal [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]l’instance de cluster est désormais le groupe de destination.  
  
4.  Arrêter l’adresse IP et réseau de la ressource de nom PublicSQLClustername sur le serveur principal [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] l’instance de cluster.  
  
5.  Configurer et démarrer les ressources de cluster de nom réseau et PublicSQLClustername IP sur le serveur secondaire [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] l’instance de cluster.  
  
6.  Démarrez les serveurs BizTalk de production.  
  
7.  Vérification de la restauration de journaux.  
  
8.  Démarrer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] relatives des services sur le site de production.  
  
 Après avoir effectué ces étapes, le groupe BizTalk pointe vers le serveur secondaire [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] l’instance de cluster comme l’illustre la figure suivante.  
  
 L’exemple suivant illustre comment configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoi de journaux à l’aide de deux instances de cluster de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et déplacer le nom de cluster et IP adresse ressource.  
  
 ![Envoi de journaux BizTalk à l’aide d’un nom de Cluster et l’IP](../technical-guides/media/5055689e-c26b-4077-a531-74a50fec1393.gif "5055689e-c26b-4077-a531-74a50fec1393")  
  
 **Implémentation d’un envoi de journaux de BizTalk Server à l’aide du nom de cluster Windows Server et les ressources d’adresse IP**  
  
## <a name="see-also"></a>Voir aussi  
 [Haute disponibilité pour les bases de données](../technical-guides/high-availability-for-databases.md)   
 [Journaux de configuration de BizTalk Server](../technical-guides/configuring-biztalk-server-log-shipping.md)   
 [Comment restaurer des bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)