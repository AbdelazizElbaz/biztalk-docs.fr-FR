---
title: "Comment contrôler la taille de la liste des résultats | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- results list [Orchestration Debugger], deleting columns
- results list [Orchestration Debugger], limiting list size
- Orchestration Debugger, results list
- results list [Orchestration Designer]
- results list [Orchestration Debugger], adding columns
ms.assetid: 4d41003f-5ea9-4599-8ec0-737c342ffdbd
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80787e4c7dbac57aca9c787943846e924a1a7870
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-control-the-size-of-the-results-list"></a>Contrôle de la taille de la liste des résultats
Sur le **Hub du groupe** page de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, le volet contient des colonnes autant d’informations dont vous avez besoin de faire défiler pour afficher les résultats de la requête. Vous pouvez ajouter ou supprimer des colonnes dans le volet pour afficher uniquement les informations nécessaires. Pour ajouter ou supprimer des colonnes, une partie du volet de résultats de requête et cliquez avec le bouton droit **Ajout/Suppression de colonnes** dans le menu contextuel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs pour effectuer cette procédure.  
  
### <a name="to-add-or-remove-columns-in-the-results-list"></a>Pour ajouter ou supprimer des colonnes dans la liste de résultats  
  
1.  Avec le bouton droit n’importe quelle cellule dans la **résultats de la requête** liste, puis cliquez sur **Ajout/Suppression de colonnes** dans le menu contextuel.  
  
    > [!NOTE]
    >  Les éléments qui sont déjà présents dans la liste des résultats s’affichent sur le côté droit sous **colonnes affichées**. Les éléments qui ne sont pas présentes dans la liste des résultats s’affichent sur le côté gauche sous **colonnes disponibles**.  
  
2.  Pour ajouter une colonne, sélectionnez un des éléments à partir de **colonnes disponibles** et cliquez sur **ajouter** pour déplacer cette colonne à la liste des **colonnes affichées**.  
  
3.  Pour supprimer une colonne, sélectionnez un des éléments à partir de **colonnes affichées** et cliquez sur **supprimer** pour déplacer cette colonne à la liste des **colonnes disponibles**.  
  
 Vous pouvez contrôler le nombre de résultats renvoyés par la requête à l'aide des filtres fournis lors de la création ou de l'exécution d'une requête.  
  
## <a name="columns-in-the-query-results-list"></a>Colonnes dans la liste de résultats de la requête  
 Les résultats de la requête sont affichés dans le volet Résultats de la requête en bas de la vue à l'origine de la requête. Vous ne pouvez pas accéder directement à la liste de résultats. Ce menu contextuel présente toutes les actions que vous pouvez entreprendre sur l'entrée sélectionnée dans la vue actuellement active. Par exemple, si l'enregistrement contient un ID instance de service, les actions liées à ce service s'affichent. Si un ID de message est indiqué, ce sont les actions associées au message qui apparaissent.  
  
 Lorsqu'il n'est pas nécessaire de consulter toutes les informations contenues dans cette liste complète, vous pouvez sélectionner uniquement les colonnes que vous souhaitez afficher ou rétablir celles que vous avez supprimées. Lorsque vous triez la liste de résultats suivant l'heure, les instances sont triées en tenant compte des millisecondes, même si les millisecondes n'apparaissent pas dans la liste. Lorsque vous réutilisez une requête enregistrée, les résultats affichent uniquement les colonnes sélectionnées à chaque exécution de la requête.  
  
 Le tableau suivant répertorie la liste complète des éléments qui apparaissent dans la liste de résultats.  
  
|||  
|-|-|  
|**Champ de Message ou de service**|**Description**|  
|Nom du service|Nom de l'instance de service.|  
|Type d’événement|Type de service (par exemple, messagerie (pipeline), orchestration, adaptateur de transport).|  
|Description de l’erreur|Description de l'erreur, le cas échéant.|  
|État|État de l'opération lors de l'exécution de la requête.|  
|Code d'erreur|Code de l'erreur, le cas échéant.|  
|Certificat de déchiffrement|Affiche les informations de certificat relatives au message ou au service.|  
|Duration|Délai d'exécution de l'opération.|  
|Nom du port|Port impliqué dans le flux de l'instance.|  
|Signature|Informations de signature numérique du message.|  
|Taille|Taille du message en octets.|  
|Start Time|Heure à laquelle l'opération a commencé.|  
|Heure de fin|Heure de l’opération s’est terminée.|  
|Nombre de parties|Nombre de parties dans le message.|  
|Soirée|Identificateur du tiers démarrant l'opération.|  
|URI|URI du tiers initiateur.|  
|TimeStamp|Heure à laquelle l'opération a commencé.|  
|Hôte|Nom de l'hôte BizTalk exécutant l'instance de service.|  
|Nom de l'assembly|Nom de l'assembly .NET qui implémente l'instance de service.|  
|Version de l’assembly|Numéro de version de l'assembly associé.|  
|Heure du déploiement|Heure à laquelle l'assembly de l'instance de service a été déployé dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|ID de l'activité|Identifie l’activité (par exemple, les messages envoyés et reçus par le pipeline / l’orchestration ont le même ID) de l’instance de service unique.|  
|ID instance de service|Identificateur unique universel (GUID, Globally Unique Identifier) qui identifie une exécution d'une instance de service.|  
|ID d'instance de message|Identificateur unique universel (GUID, Globally Unique Identifier) qui identifie une instance de message.|  
|ID de service|Identificateur unique universel (GUID, Globally Unique Identifier) qui identifie un service.|  
|Classe du service|Type de classe (pipeline ou orchestration).|  
|ID de classe de service|GUID indépendant d'un service permettant d'identifier un service (par exemple, orchestration).|  
|Icône|Icône de la ligne de résultat.|  
|Adaptateur|Adaptateur utilisé dans l'opération.|