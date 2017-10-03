---
title: Comment rechercher des Instances de Service suspendues | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service instances, viewing
- service instances, Query tab [Administration Console]
- Query tab [Administration Console], service instances
- service instances, suspended
- Query tab [Administration Console], searching
- instances, suspended
- instances, services
ms.assetid: f91b1151-d879-4aa7-afc8-4cf13d928158
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52c0d3ad192ad2cc8f4429f78cfa38ddc97ac837
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-suspended-service-instances"></a>Recherche des instances de service interrompues
Vous pouvez utiliser la **requête** onglet dans la Console Administration de BizTalk Server pour rechercher des instances de service suspendues. Vous avez la possibilité de rechercher un sous-ensemble spécifique de messages afin de localiser un message particulier associé à un nom de service, un type, un hôte, etc.  
  
> [!NOTE]
>  Les instances achevées alors que certains messages n'étaient pas encore envoyés sont affichées en tant que code d'erreur (« Terminé avec des messages non utilisés ») pour les instances de service interrompues pertinentes. Elles ne peuvent pas être reprises.  
  
> [!NOTE]
>  En cas de regroupement et de filtrage par URI ou par nom d'adaptateur de l'erreur, seuls les ports d'envoi et de réception sont affichés dans les résultats. Ce type de regroupement et de filtrage ne peut pas être appliqué aux orchestrations, qui ne sont pas incluses dans les résultats.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté en tant que membre du groupe des opérateurs de BizTalk Server.  
  
### <a name="to-search-for-suspended-service-instances"></a>Pour rechercher les instances de service interrompues  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, puis cliquez sur le groupe BizTalk.  
  
3.  Dans le volet détails, cliquez sur le **nouvelle requête** onglet.  
  
4.  Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **Instances de Service suspendues** dans la zone de liste déroulante.  
  
5.  Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :  
  
    |Élément| Description|  
    |----------|-----------------|  
    |**Application Name**|Nom de l'application BizTalk Server.|  
    |**Heure de création**|Permet de rechercher les instances de service interrompues qui ont été créées avant ou après la date mentionnée.|  
    |**Adaptateur de l’erreur**|Vous pouvez regrouper ou filtrer les instances de service interrompues par type d'adaptateur. Par exemple : fichier, FTP, HTTP, MQSeries, MSMQ, POP3, SMTP, SOAP ou Windows SharePoint Services. **Remarque :** dans les résultats de la requête, l’adaptateur est uniquement renseigné lorsque l’exécution de BizTalk Server rencontre une erreur lors de l’utilisation de l’adaptateur spécifié. Si l’exécution se produit sans erreur avec l’adaptateur, dans les résultats de la requête, le champ Adaptateur de l'erreur est vide.|  
    |**Code d’erreur**|Vous pouvez regrouper ou filtrer les instances de service interrompues suivant un code d'erreur pour afficher toutes les instances de service interrompues avec génération de ce code d'erreur.|  
    |**Description de l’erreur**|Vous pouvez regrouper ou filtrer les instances de service interrompues en fonction de la description d'erreur fournie.|  
    |**Grouper les résultats selon**|Vous pouvez regrouper ou filtrer les résultats selon l'adaptateur, l'application, le code d'erreur, la description d'erreur, le nom d'hôte, la classe de service, l'état de l'instance de service, le nom de service ou l'URI.|  
    |**Host Name**|Permet de grouper ou de filtrer les instances de service interrompues en fonction du nom de l'hôte.|  
    |**État de l’instance**|Vous pouvez rechercher les instances interrompues ne pouvant pas être reprises ou les instances interrompues pouvant être reprises.|  
    |**Correspondances maximales**|Nombre de résultats à afficher.|  
    |**Classe de service**|Vous pouvez rechercher des adaptateurs isolés (adaptateurs de messagerie), MSMQT, l'orchestration ou le rapport de l'échec du routage.|  
    |**Nom du service**|Vous pouvez grouper ou filtrer les instances de service interrompues en fonction du nom du service.|  
    |**ID du Type de service**|Vous pouvez grouper ou filtrer les instances de service interrompues en fonction de l'ID de type de service.|  
    |**Date d’interruption**|Vous pouvez grouper ou filtrer les instances de service qui ont été interrompues avant ou après la date mentionnée.|  
    |**URI**|Vous pouvez grouper ou filtrer les instances de service interrompues en fonction de l'URI. **Remarque :** dans les résultats de la requête, les URI n’est rempli lors de l’exécution de BizTalk Server rencontre une erreur lors de l’envoi à l’URI spécifié. Si l'exécution se fait sans erreur pendant l’envoi à l’URI, dans les résultats de la requête, le champ URI est vide ou affiche "URI non disponible."|  
  
6.  Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.  
  
7.  Continuez à ajouter des lignes supplémentaires à la requête si nécessaire, en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’onglet requête de la Console Administration](../core/using-the-administration-console-query-tab.md)