---
title: "Résolution des problèmes de connexion après la restauration du système de Destination | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9232ca3-dadb-4b3c-8ec4-4e307c32d2e5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e691e690552f6decb3eed5f55dd17295c21a4efd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="resolving-login-issues-after-restoring-the-destination-system"></a>Résolution des problèmes de connexion après la restauration du système de Destination
Selon la façon dont le système source a été configuré au cours du déploiement, les utilisateurs « orphelins » peuvent doivent être résolus. Un utilisateur orphelins de la base de données est un utilisateur qui ne dispose pas d’une sécurité correspondante login dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Créer des connexions correspondantes pour ces utilisateurs avant de mettre le système en ligne à l’aide de la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] SQL Management Studio (dans **sécurité**, **connexions**). Vous pouvez créer ces connexions à tout moment, mais nous vous recommandons de créer les lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d’envoi de journaux est configuré.  
  
 Les connexions qui sont créées doivent correspondre aux comptes Windows et les groupes qui ont été utilisées lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a été configuré sur le système source et à toutes les connexions qui ont été manuellement créées et utilisées dans tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-a créé le rôle. Si ces connexions correspondent à des comptes Windows locaux ou de groupes, les comptes et les groupes doivent d’abord être créés avant que la connexion peut être ajoutée. Si le nom d’ordinateur du serveur BizTalk n’est pas modifié, puis résolvez les utilisateurs associés aux connexions pour les comptes et groupes locaux.  
  
 Lors de la configuration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoi de journaux, suivez les étapes de 918992 de l’Article de Base de connaissances Microsoft [comment transférer les connexions et les mots de passe entre instances de SQL Server 2005 et SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=157143) (http:// go.Microsoft.com/fwlink/ ? LinkId = 157143) pour créer un script qui ajoute les connexions nécessaires pour le serveur de destination.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes d’envoi de journaux](../technical-guides/troubleshooting-log-shipping.md)