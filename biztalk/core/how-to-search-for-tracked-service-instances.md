---
title: Comment rechercher des Instances de Service suivies | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6337df9-8c2e-4d4a-a64b-cc040f83bd91
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08e5a7fa563e175d6a1d784e546bd399e20d3c21
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-tracked-service-instances"></a>Recherche d'instances de service suivies
Vous pouvez utiliser la **requête** onglet dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] la console Administration pour rechercher toutes les instances de service suivies. Pour localiser les instances de service, vous pouvez effectuer une recherche sur le nom et la version de l'assembly, les heures de début et de fin de sa durée de vie, le nom ou l'ID d'instance de la classe de service, le nom de l'hôte, le code d'erreur et l'état de l'instance de service.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Opérateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-search-for-tracked-service-instances"></a>Pour rechercher les instances de service suivies  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, puis cliquez sur le groupe BizTalk.  
  
3.  Dans le volet détails, cliquez sur le **nouvelle requête** onglet.  
  
4.  Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **Instances de Service suivies** dans la zone de liste déroulante.  
  
5.  Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :  
  
    |Élément| Description|  
    |----------|-----------------|  
    |**Nom de l’assembly**|Nom de l'assembly pour l'instance de service.|  
    |**Version de l’assembly**|Version de l'instance de service.|  
    |**Heure de fin**|Heure de fin de l'instance de service.|  
    |**Code d’erreur**|Code de l'erreur associée à l'instance de service.|  
    |**Host Name**|Nom de l'hôte de l'instance de service.|  
    |**Correspondances maximales**|Nombre de résultats à afficher.|  
    |**Classe de service**|Classe de l'instance de service.|  
    |**ID d’Instance de service**|ID de l'instance de service.|  
    |**Nom du service**|Le nom de l’instance de service.|  
    |**Start Time**|Heure de début de l'instance de service.|  
    |**État**|État de l'instance de service.|  
  
6.  Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.  
  
7.  Continuez à ajouter des lignes supplémentaires à la requête comme il convient en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’onglet requête de la Console Administration](../core/using-the-administration-console-query-tab.md)