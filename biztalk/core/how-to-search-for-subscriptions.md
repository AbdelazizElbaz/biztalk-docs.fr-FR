---
title: Comment rechercher des abonnements | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Query tab [Administration Console], subscriptions
- Query tab [Administration Console], searching
- subscriptions, viewing
- subscriptions, searching
ms.assetid: 95f8fd20-2750-412b-a67b-18976e7706e2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f1830a4c1dddfa3dcfc2a1177b69410dd8ee0ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-subscriptions"></a>Recherche d'abonnements
Vous pouvez utiliser la **requête** onglet dans la Console Administration de BizTalk Server pour rechercher des abonnements. Cela peut s'avérer utile pour vérifier tous les abonnements définis dans le système. Lors du dépannage des échecs de routage, vous pouvez vérifier les abonnements pour identifier ceux qui seraient mal configurés et causeraient l'échec du routage.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté en tant que membre du groupe des opérateurs de BizTalk Server.  
  
### <a name="to-search-for-subscriptions"></a>Pour rechercher des abonnements  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
2.  Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur le groupe BizTalk.  
  
3.  Dans le volet détails, cliquez sur le **nouvelle requête** onglet.  
  
4.  Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **abonnements** dans la zone de liste déroulante.  
  
5.  Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :  
  
    |Élément| Description|  
    |----------|-----------------|  
    |**Correspondances maximales**|Nombre de résultats à afficher.|  
    |**ID d’Instance de service**|Vous pouvez filtrer les abonnements par ID d'instance de service.|  
    |**Nom du service**|Vous pouvez filtrer les abonnements par nom de service.|  
    |**Type d’abonnement**|Vous pouvez filtrer les abonnements par abonnement d'activation ou par abonnement d'instance.|  
  
6.  Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.  
  
7.  Continuez à ajouter des lignes supplémentaires à la requête si nécessaire, en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’onglet requête de la Console Administration](../core/using-the-administration-console-query-tab.md)