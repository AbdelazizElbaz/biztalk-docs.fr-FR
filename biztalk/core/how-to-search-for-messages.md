---
title: Comment rechercher des Messages | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, viewing
- messages, searching
- Query tab [Administration Console], searching
- Query tab [Administration Console], messages
ms.assetid: c751d23f-913a-4325-81da-a36d61c07e8b
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5443cc021bd5f97621f44d295432c99834bdaed
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-search-for-messages"></a>Recherche de messages
Vous pouvez utiliser la **requête** onglet dans la Console Administration de BizTalk Server pour rechercher une classe spécifique de messages.  
  
## <a name="prerequisites"></a>Configuration requise  
 Pour exécuter cette procédure, vous devez être connecté en tant que membre du groupe des opérateurs de BizTalk Server.  
  
### <a name="to-search-for-messages"></a>Pour rechercher des messages  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur le groupe BizTalk.  
  
3.  Dans le volet détails, cliquez sur le **nouvelle requête** onglet.  
  
4.  Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **Messages** dans la zone de liste déroulante.  
  
5.  Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :  
  
    |Élément| Description|  
    |----------|-----------------|  
    |**Heure de création**|Permet de rechercher les messages créés avant ou après la date spécifiée.|  
    |**Adaptateur de l’erreur**|Vous pouvez regrouper ou filtrer les messages par type d’adaptateur : fichier, FTP, HTTP, MQSeries, MSMQ, POP3, SMTP, SOAP ou Windows SharePoint Services.|  
    |**Code d’erreur**|Vous pouvez regrouper ou filtrer les messages par code d'erreur.|  
    |**Description de l’erreur**|Vous pouvez regrouper ou filtrer les messages en fonction de la description de l'erreur.|  
    |**Host Name**|Vous pouvez regrouper ou filtrer les messages en fonction du nom de l'hôte.|  
    |**État de l’instance**|État de l'instance de service faisant référence au message. Vous pouvez rechercher tous les types d’instances suivantes : toutes les instances en cours d’exécution, toutes les instances suspendues, instances actives, instances mises en attente, les instances de prêt à s’exécuter, instances planifiées, suspendues, mais ne peut pas être repris instances, ou suspendus et peut être repris instances.|  
    |**Correspondances maximales**|Nombre de résultats à afficher.|  
    |**ID de message**|Vous pouvez regrouper ou filtrer les messages en fonction de l'ID du message.|  
    |**État du message**|Vous pouvez rechercher les messages dont l'état est utilisé, en cours, suspendu, suspendu sans reprise possible, suspendu avec reprise possible, mis en file d'attente, mis en file d'attente et en attente de traitement, mis en file d'attente et planifié pour une remise ultérieure, et mis en file d'attente et en attente de nouvel essai.|  
    |**Type de message**|Vous pouvez regrouper ou filtrer les messages en fonction de leur type.|  
    |**Classe de service**|Vous pouvez rechercher des adaptateurs isolés (adaptateurs de messagerie), MSMQT, l'orchestration ou le rapport de l'échec du routage.|  
    |**ID d’Instance de service**|Vous pouvez grouper ou filtrer les messages par ID d'instance de service.|  
    |**Nom du service**|Vous pouvez regrouper ou filtrer les messages par nom du service.|  
    |**ID du Type de service**|Vous pouvez grouper ou filtrer les messages par ID de type de service.|  
    |**URI**|Vous pouvez regrouper ou filtrer les messages par URI.|  
  
6.  Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.  
  
7.  Continuez à ajouter des lignes supplémentaires à la requête si nécessaire, en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de l’onglet Requête de la console Administration](../core/using-the-administration-console-query-tab.md)