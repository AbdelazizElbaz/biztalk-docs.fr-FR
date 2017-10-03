---
title: "Comment modifier les propriétés du groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying, groups
- configuring, groups
- groups, configuring
- managing [groups], properties
- groups, modifying
- managing [groups], modifying
- groups, properties
ms.assetid: 59e0853d-81b0-43f9-85bf-099868e25fad
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a191011b6824086e26c72ce5e5a182a167ca0e37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-group-properties"></a>Modification des propriétés du groupe
Cette procédure vous permet de configurer les propriétés globales pour le groupe BizTalk Server de manière à pouvoir sélectionner un certificat de signature, modifier l'intervalle d'actualisation du cache et déterminer la façon dont BizTalk Server gérera les messages volumineux. Pour plus d’informations sur les propriétés du groupe BizTalk Server, consultez [groupes BizTalk](../core/biztalk-groups.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server.  
  
### <a name="to-configure-biztalk-group-properties"></a>Pour configurer les propriétés du groupe BizTalk  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **groupe BizTalk**, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés d’un groupe** boîte de dialogue le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Entrer le nom du groupe. Le nom d'un tel groupe ne doit pas comporter plus de 128 caractères. Le nom dans cette zone s’affiche en regard du **groupe** nœud dans l’arborescence de la console, ainsi que le nom du serveur et le nom de base de données de gestion BizTalk.|  
    |**Server**|Afficher le serveur sur lequel la base de données de gestion BizTalk est stockée.|  
    |**Base de données**|Afficher la base de données de gestion BizTalk dans laquelle les paramètres de configuration de ce groupe sont stockés.|  
    |**Nom du serveur de l’authentification unique**|Entrer le nom du serveur de l'authentification unique de l'entreprise que cet ordinateur doit utiliser pour stocker les informations spécifiques aux adaptateurs et y accéder. Il s'agit du nom du serveur d'authentification unique utilisé pour établir la connexion à la base de données d'authentification unique.|  
    |**Groupe d’administrateurs BizTalk**|Afficher le nom du groupe d'administrateurs disposant des droits nécessaires à la gestion de l'environnement BizTalk Server après installation.|  
    |**Groupe des opérateurs BizTalk**|Afficher le nom du groupe d'opérateurs disposant des droits nécessaires à l'affichage de la configuration, l'exécution de requêtes, la maintenance des ordinateurs et l'analyse de base des applications.|  
    |**Opérateurs B2B de BizTalk Server**|Afficher le nom du groupe des opérateurs interentreprises.|  
  
4.  Sur le **bases de données** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Bases de données**|Afficher le nom de toutes les bases de données dans l'application et sur les serveurs où elles résident, tel que spécifié lors de la configuration.|  
  
5.  Sur le **certificat** onglet, procédez comme suit, puis cliquez sur **OK**:  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom commun**|Afficher une description du certificat sélectionné.|  
    |**Empreinte numérique**|Afficher l'empreinte du certificat de clé privée utilisé pour appliquer une signature numérique aux messages sortants de ce groupe. Le format de l'empreinte de certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est une valeur hexadécimale (nombre de 0 à 9 ou lettre de A à F).|  
    |**Supprimer le certificat**|Cliquer pour supprimer le certificat affiché.|  
    |**Parcourir**|Cliquez pour afficher les **sélectionner un certificat** boîte de dialogue, dans laquelle vous sélectionnez le certificat de signature pour l’utilisateur actuel ou le magasin personnel à utiliser avec le groupe.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des groupes](../core/managing-groups.md)   
 [Groupes BizTalk](../core/biztalk-groups.md)   
 [Comment ajouter un serveur à un groupe](../core/how-to-add-a-server-to-a-group.md)   
 [Comment déplacer un serveur à partir d’un groupe à un autre](../core/how-to-move-a-server-from-one-group-to-another.md)   
 [Comment supprimer un serveur d’un groupe](../core/how-to-remove-a-server-from-a-group.md)