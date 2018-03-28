---
title: Comment rechercher des événements de Message suivis | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18df4cf7-c307-4175-926c-9be9f30b29ed
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6a3597d0d68dbd79de6c23e7b6d4b222b9c8376
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-search-for-tracked-message-events"></a>Recherche des événements de message suivis
Vous pouvez utiliser la **nouvelle requête** onglet dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour rechercher des événements des messages suivis.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez activer le suivi du corps et des propriétés de message. Le volet Résultats de la requête indique les informations relatives à l'événement de message, notamment les informations de schéma, le type d'événement, l'ID de l'instance de service et les propriétés promues du message généré.  
  
> [!NOTE]
>  Pour afficher le corps du message réel, vous pouvez appeler la **détails du Message** , menu contextuel et passer à l’onglet « Parties de Message », ou enregistrer le message à partir de la liste des résultats afficher en appelant **enregistrer dans le fichier** à partir de la menu contextuel.  
  
## <a name="prerequisites"></a>Configuration requise  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Opérateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-search-for-tracked-message-items"></a>Pour rechercher les éléments suivis d'un message  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, puis cliquez sur le groupe BizTalk.  
  
3.  Dans le volet détails, cliquez sur le **nouvelle requête** onglet.  
  
4.  Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **événements de Message suivis** dans la zone de liste déroulante.  
  
5.  Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :  
  
    |Élément| Description|  
    |----------|-----------------|  
    |**Heure de création**|Heure à laquelle le message a été créé.|  
    |**Type d’événement**|Type d'événement faisant l'objet du suivi.|  
    |**Correspondances maximales**|Nombre de résultats à afficher.|  
    |**Party**|Organisation qui a envoyé le message.|  
    |**Port**|Port utilisé pour traiter le message.|  
    |**Nom du schéma**|Nom du schéma utilisé par le message.|  
    |**ID d’Instance de service**|ID de l'instance de service utilisée pour le message.|  
    |**URI**|URI utilisé pour le message.|  
    |**\<Sélectionnez un nom de schéma pour les propriétés suivies\>**|Lorsque vous sélectionnez un schéma, les propriétés promues dans ce schéma peuvent être utilisée dans la requête.|  
  
6.  Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.  
  
7.  Continuez à ajouter des lignes supplémentaires à la requête comme il convient en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de l’onglet Requête de la console Administration](../core/using-the-administration-console-query-tab.md)