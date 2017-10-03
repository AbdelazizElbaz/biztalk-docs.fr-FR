---
title: "Comment afficher les informations d’Instance pour un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], viewing
- receive ports, viewing
- viewing, receive ports
ms.assetid: dad038bc-1202-489b-b144-a93bf1f53c0c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e46da8bfb99246b67f93c02fa19689099f8acb24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-instance-information-for-a-receive-port"></a>Affichage des informations d'instance pour un port de réception
La présente rubrique explique comment afficher les instances de service pour un port de réception à l'aide de la console Administration de BizTalk Server. Chaque fois que le port de réception reçoit un message, une instance de service est créée pour traiter le message. Si vous suivez la procédure de cette rubrique, les informations sur l'instance s'affichent dans la page Présentation du groupe du port de réception.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-view-instance-information-for-a-receive-port"></a>Pour afficher les informations d'instance pour un port de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel vous voulez afficher les informations d'instance.  
  
3.  Cliquez sur **Ports de réception**, sélectionnez le port de réception, cliquez sur **vue**, puis cliquez sur **informations sur l’Instance**.  
  
     Le volet des résultats de la requête situé dans la section inférieure de la page affiche toutes les instances du port de réception.  
  
4.  Pour affiner la requête et afficher les informations d’instance différent pour le port de réception, cliquez sur la zone sous **valeur** pour le **recherche de** , sélectionnez le type d’instance à afficher, puis cliquez sur **exécuter Requête**. Pour plus d'informations sur la création des requêtes, consultez les rubriques relatives à la recherche dans la section Voir aussi.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Ports de réception](../core/managing-receive-ports.md)   
 [Comment rechercher des Instances de Service en cours d’exécution](../core/how-to-search-for-running-service-instances.md)   
 [Comment rechercher des Instances de Service suspendues](../core/how-to-search-for-suspended-service-instances.md)   
 [Comment rechercher des Messages](../core/how-to-search-for-messages.md)   
 [Comment rechercher des abonnements](../core/how-to-search-for-subscriptions.md)