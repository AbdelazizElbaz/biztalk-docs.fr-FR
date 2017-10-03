---
title: Recherche de toutes les Instances de Service | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service instances, Query tab [Administration Console]
- Query tab [Administration Console], service instances
- Query tab [Administration Console], searching
- service instances, searching
- instances, services
ms.assetid: 48cb885c-aaf1-44e8-9810-2e70cf63db81
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e96622fad23c28c0d4147f64a11cc540e88e7f97
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-all-service-instances"></a>Recherche de toutes les instances de service
Vous pouvez utiliser la **requête** onglet dans la Console Administration de BizTalk Server pour rechercher toutes les instances de service. Vous ne pouvez pas désinscrire un type de service spécifique si certaines instances sont en cours d'exécution ou suspendues. Ainsi, avant de désinscrire un type de service, vous pouvez rechercher toutes les instances de service pour vous assurer qu'aucune de ces instances n'est en cours d'exécution ou suspendue.  
  
> [!NOTE]
>  En cas de regroupement et de filtrage par URI, seuls les ports d'envoi et de réception sont affichés dans les résultats. Ce type de regroupement et de filtrage ne peut pas être appliqué aux orchestrations, qui ne sont pas incluses dans les résultats.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté en tant que membre du groupe des opérateurs de BizTalk Server.  
  
### <a name="to-search-for-all-service-instances"></a>Pour rechercher toutes les instances de service  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur le groupe BizTalk.  
  
3.  Dans le volet détails, cliquez sur le **nouvelle requête** onglet.  
  
4.  Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **toutes les Instances de Service en cours d’exécution** dans la zone de liste déroulante.  
  
5.  Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Application Name**|Application BizTalk Server|  
    |**Heure de création**|Permet de rechercher toutes les instances de service qui ont été créées avant ou après la date mentionnée.|  
    |**Grouper les résultats selon**|Vous pouvez regrouper les résultats par application, nom d'hôte, classe de service, état de l'instance de service ou nom de service.|  
    |**Host Name**|Nom de l'hôte BizTalk|  
    |**État de l’instance**|Vous pouvez rechercher toutes les instances en cours d'exécution, suspendues, actives, mises en attente, exécutables, planifiées, suspendues sans reprise possible ou suspendues avec reprise possible.|  
    |**Correspondances maximales**|Nombre de résultats à afficher (obligatoire). Cela est généralement défini sur 50, la valeur par défaut.<br /><br /> Lorsque vous incluez l'option Grouper les résultats selon, le nombre de groupes s'affiche et non le nombre total d'enregistrements.|  
    |**Classe de service**|Vous pouvez rechercher des adaptateurs isolés (adaptateurs de messagerie), MSMQT, l'orchestration ou le rapport de l'échec du routage.|  
    |**ID d’Instance de service**|Vous pouvez grouper ou filtrer les instances de service en fonction de leur ID.|  
    |**Nom du service**|Vous pouvez grouper ou filtrer les instances de service par nom de service.|  
    |**ID du Type de service**|Vous pouvez grouper ou filtrer les instances de service par ID de type de service.|  
  
6.  Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.  
  
7.  Continuez à ajouter des lignes supplémentaires à la requête si nécessaire, en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’onglet requête de la Console Administration](../core/using-the-administration-console-query-tab.md)