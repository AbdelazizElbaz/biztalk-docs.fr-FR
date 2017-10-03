---
title: "Comment afficher les informations d’Instance pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, viewing
- managing [send ports], viewing
- viewing, send ports
ms.assetid: 37cf6561-5341-4a05-b531-33ab0334966e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78632bdb9b5da6d4fd4de7fc35b91f410e2e5f42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-instance-information-for-a-send-port"></a>Affichage des informations sur l'instance d'un port d'envoi
Cette rubrique décrit comment afficher la liste des instances de service en cours d'exécution pour un port d'envoi à l'aide de la console Administration de BizTalk Server. Une instance de service est une instance du service de port d'envoi créée lorsqu'un message est envoyé au port d'envoi. Si vous suivez la procédure de cette rubrique, les informations sur l'instance s'affichent dans la page Présentation du groupe du port d'envoi.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server ou Opérateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-view-instance-information-for-a-send-port"></a>Pour afficher les informations d'instance pour un port d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi pour lequel vous voulez afficher les informations d'instance de service.  
  
3.  Cliquez sur **Ports d’envoi**, cliquez sur le port d’envoi, pointez sur **vue**, puis cliquez sur **informations sur l’Instance**.  
  
     Le volet des résultats de la requête situé dans la section inférieure de la page affiche toutes les instances en cours d'exécution du port d'envoi.  
  
4.  Pour affiner la requête et afficher les informations d’instance de service différent pour le port d’envoi, cliquez sur la zone sous **valeur** pour le champ Rechercher, sélectionnez le type d’instance à afficher, puis cliquez sur **exécuter la requête**. Pour plus d'informations sur la création des requêtes, consultez les rubriques relatives à la recherche dans la section Voir aussi.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)   
 [Comment rechercher des Instances de Service en cours d’exécution](../core/how-to-search-for-running-service-instances.md)   
 [Comment rechercher des Instances de Service suspendues](../core/how-to-search-for-suspended-service-instances.md)   
 [Comment rechercher des Messages](../core/how-to-search-for-messages.md)   
 [Comment rechercher des abonnements](../core/how-to-search-for-subscriptions.md)