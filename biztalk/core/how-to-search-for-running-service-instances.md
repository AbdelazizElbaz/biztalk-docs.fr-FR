---
title: Comment rechercher des Instances de Service en cours d’exécution | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service instances, viewing
- service instances, Query tab [Administration Console]
- Query tab [Administration Console], service instances
- Query tab [Administration Console], searching
- service instances, searching
- service instances, running
ms.assetid: fc65bf33-c013-4e6a-b9fd-b4536811e7b4
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8873747b39d6fa178b813d361b72ccf24f44b54a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-search-for-running-service-instances"></a>Recherche des instances de service en cours d'exécution
Vous pouvez utiliser la **requête** onglet dans la Console Administration de BizTalk Server pour rechercher une mise en attente, active, dans le point d’arrêt, planifié et une nouvelle tentative de l’instance de service.  
  
## <a name="prerequisites"></a>Configuration requise  
 Pour exécuter cette procédure, vous devez être connecté en tant que membre du groupe des opérateurs de BizTalk Server.  
  
### <a name="to-search-for-running-service-instances"></a>Pour rechercher les instances de service en cours d'exécution  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur le groupe BizTalk.  
  
3.  Dans le volet détails, cliquez sur le **nouvelle requête** onglet.  
  
4.  Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **en cours d’exécution des Instances de Service** dans la zone de liste déroulante.  
  
5.  Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :  
  
    |Élément| Description|  
    |----------|-----------------|  
    |**Application Name**|Application BizTalk Server|  
    |**Heure de création**|Permet de rechercher les instances de service en cours d'exécution qui ont été créées avant ou après la date mentionnée.|  
    |**Grouper les résultats selon**|Vous pouvez regrouper les résultats par application, nom d'hôte, type d'opération en attente, classe de service, état de l'instance de service ou nom de service.|  
    |**Host Name**|Nom de l'hôte BizTalk|  
    |**État de l’instance**|Vous pouvez rechercher les instances actives, mises en attente, prêtes à être exécutées et planifiées.|  
    |**Correspondances maximales**|Nombre de résultats à afficher.|  
    |**Opérations en attente**|Vous pouvez rechercher les instances de service en cours d'exécution pour lesquelles la suspension ou l'arrêt est en attente.|  
    |**Classe de service**|Vous pouvez rechercher des adaptateurs isolés (adaptateurs de messagerie), MSMQT, l'orchestration ou le rapport de l'échec du routage.|  
    |**Nom du service**|Vous pouvez grouper ou filtrer les instances de service en cours d'exécution en fonction du nom du service.|  
    |**ID du Type de service**|Vous pouvez grouper ou filtrer les messages par ID de type de service.|  
  
6.  Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.  
  
7.  Continuez à ajouter des lignes supplémentaires à la requête si nécessaire, en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de l’onglet Requête de la console Administration](../core/using-the-administration-console-query-tab.md)