---
title: "Création de liens enregistrement à enregistrement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a3fa4d7-5689-4f55-af1b-369defa37037
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac6abc3d27ad3ee2f135e3ff5c8c1749fcae5f4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="record-to-record-linking"></a>Création de liens enregistrement à enregistrement

## <a name="overview"></a>Vue d'ensemble
Dans Microsoft® [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez utiliser le Mappeur BizTalk pour créer plusieurs liens à la fois entre des portions similaires des schémas source et de destination. Avec les versions précédentes de BizTalk Server, vous deviez créer ces liens un par un. Il existe deux méthodes de création de liens enregistrement à enregistrement, chacune étant adaptée à des scénarios différents basés sur le degré de similarité de la structure des enregistrements des schémas source et de destination pour lesquels des liens sont créés, comme décrit ci-dessous :  
  
-   **Structure de liaison.** utilisez cette méthode quand les enregistrements pour lesquels des liens sont créés dans vos schémas source et de destination possèdent une structure identique ou très similaire.  
  
-   **Mise en correspondance de nom de liaison.** utilisez cette méthode quand les enregistrements pour lesquels des liens sont créés dans vos schémas source et de destination ont une structure très similaire ainsi que des noms d'enregistrement et de champ identiques, mais plus de différences structurelles que la création de liens de type structure n'est capable d'en gérer.  
  
    > [!NOTE]
    >  Création de liens enregistrement à enregistrement s’applique à la copie de la valeur de liaison uniquement, comme configuré à l’aide du **liaisons sources** propriété.  
  
## <a name="record-to-record-linking-structure-links"></a>Enregistrement à l’autre liaison : Les liens de Structure  
 Utilisez cette méthode quand les enregistrements pour lesquels vous souhaitez créer des liens dans vos schémas source et de destination ont une structure identique ou très similaire.  
  
 Si vos schémas ont la même structure exactement, il suffit d'ajouter un lien au nœud racine de chaque schéma. Dans le menu contextuel, sélectionnez le mode de liaison souhaité.  
  
 Si certains enregistrements de vos schémas ont la même structure exactement, il suffit d'ajouter un lien entre ces enregistrements dans chaque schéma. Dans le menu contextuel, sélectionnez le mode de liaison souhaité.  
  
 Pour plus d’informations sur la façon de configurer l’enregistrement à l’autre liaison comme à l’aide de liens de type structure ou correspondance de noms, consultez la rubrique [enregistrements lien automatiquement](../core/how-to-link-records-automatically.md).  
  
> [!NOTE]
>  Les liens de structure constituent le type par défaut de création de liens enregistrement à enregistrement.  
  
## <a name="record-to-record-linking-name-matching-links"></a>Liaison de l’enregistrement à l’autre : Correspondance des noms des liens  
 Utilisez cette méthode quand les enregistrements pour lesquels vous souhaitez créer des liens dans vos schémas source et de destination ont une structure très similaire mais pas rigoureusement identique. Par exemple, les nœuds à relier d'un des schémas source ou de destination pourront comporter plus d'enregistrements ou de champs subordonnés que ceux de l'autre schéma.  
  
 Pour créer un lien de type correspondance de noms entre des parties des schémas source et de destination (voire des schémas entiers, le cas échéant) de structure presque identique, créez un lien partant d'un nœud parent de sous-hiérarchie et se terminant au niveau d'un autre nœud parent de sous-hiérarchie. Dans le menu contextuel, sélectionnez le mode souhaité. Quand vous avez relié les nœuds, des liens sont créés automatiquement pour tous les enregistrements et champs subordonnés dans les schémas source et de destination qui portent le même nom et possèdent la même sous-structure.  
  
 Pour plus d’informations sur la façon de configurer l’enregistrement à l’autre liaison comme à l’aide de liens de type structure ou correspondance de noms, consultez la rubrique [enregistrements lien automatiquement](../core/how-to-link-records-automatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Lier automatiquement des enregistrements](../core/how-to-link-records-automatically.md)   
 [Modifier les propriétés de lien](../core/how-to-edit-link-properties.md)