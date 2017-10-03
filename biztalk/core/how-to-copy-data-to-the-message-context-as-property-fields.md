---
title: "Comment copier des données dans le contexte du Message en tant que champs de propriété | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fdfe475-d9b4-4cf9-898f-dbd7e719c27c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18242f30f32974cc32ab5d39a4a9c63650f27ffa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-data-to-the-message-context-as-property-fields"></a>Comment copier des données dans le contexte du Message en tant que champs de propriété
Vous pouvez promouvoir une propriété comme un **champ de propriété** dans la même façon que pour promouvoir une propriété comme un **champ distinctif**, et vous pouvez également utiliser le **Promotion rapide** des fonctions aux simplifier le processus.  
  
 Vous pouvez choisir **champ de propriété** plutôt que la promotion **champ distinctif** promotion pour les raisons suivantes :  
  
-   Les valeurs que vous souhaitez promouvoir sont inférieure à la limite de 255 caractères qui s’applique aux **champs de propriété**.  
  
-   Les valeurs dont vous assurez la promotion doivent être accessibles en dehors des orchestrations, par exemple dans des pipelines ou des ports.  
  
 Cette rubrique fournit des instructions pas à pas pour promouvoir une propriété comme un **champ de propriété** dans les deux des manières suivantes.  
  
### <a name="to-promote-a-property-as-a-property-field-using-the-promote-properties-dialog-box"></a>Pour promouvoir une propriété en tant que champ de propriété à l'aide de la boîte de dialogue Promouvoir les propriétés  
  
1.  Si nécessaire, créez un schéma de propriété approprié dans lequel vous effectuerez la promotion d'une propriété. Pour obtenir des instructions pas à pas pour créer des schémas de propriété, consultez [création de schémas de propriété](../core/how-to-create-property-schemas.md).  
  
    > [!NOTE]
    >  Cette étape ne soit pas nécessaire si vous avez déjà créé un schéma de propriété et inséré approprié **élément de champ** nœuds en tant que nœuds enfants de la **schéma** nœud.  
  
2.  Dans l’Éditeur BizTalk, ouvrez le schéma pour lequel vous souhaitez promouvoir une ou plusieurs propriétés, puis sélectionnez le (premier) **Fieldelement**, **attribut de champ**, ou **enregistrement** nœud que vous souhaitez promouvoir en tant qu’un **champ de propriété**.  
  
    > [!NOTE]
    >  Vous pouvez uniquement promouvoir **enregistrement** nœuds s’ils sont configurés pour qu’il contienne uniquement du contenu simple en ayant sa **Content Type** propriété **SimpleContent**.  
  
3.  Cliquez sur le nœud sélectionné, cliquez sur **promouvoir**, puis cliquez sur **afficher les Promotions**.  
  
     Le **promouvoir les propriétés** boîte de dialogue s’ouvre avec apparaît le nœud sélectionné dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue.  
  
4.  Dans le **promouvoir les propriétés** boîte de dialogue, sélectionnez le **champs de propriété** onglet.  
  
5.  Vérifiez que le schéma de propriété dans lequel vous souhaitez promouvoir une propriété se trouve dans le **liste des schémas de propriété** dans l’onglet champs de propriété. Si c'est bien le cas, passez directement à l'étape 8.  
  
6.  Dans le **liste des schémas de propriété** , cliquez sur le **dossier** icône. Le **sélecteur de Type BizTalk** boîte de dialogue s’affiche.  
  
7.  Dans le **sélecteur de Type BizTalk** boîte de dialogue zone, naviguez jusqu’au schéma de propriété approprié (que vous avez créés à l’étape 1), sélectionnez-le, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si vous le souhaitez, vous pouvez modifier le préfixe d’espace de noms associé au schéma de propriété en modifiant la chaîne dans les zones appropriées **préfixe** champ de colonne.  
  
8.  Avec le nœud à promouvoir est toujours sélectionné dans l’arborescence de schéma sur le côté gauche de la **promouvoir les propriétés** boîte de dialogue, cliquez sur **ajouter**.  
  
     Si autorisé, le nœud sélectionné est ajouté à la fin de la **liste de champs de propriété** sur la **champs de propriété** onglet. Sinon, une zone de message fournit une explication Si non autorisée, la **ajouter** bouton n’est pas activé.  
  
9. Double-cliquez sur **propriété** cellule de colonne pour la ligne que vous venez d’ajouter à la **liste de champs de propriété**, puis, dans la liste déroulante, sélectionnez le **schéma de propriété** et correspondant **élément de champ** nœud dans lequel vous souhaitez promouvoir le nœud sélectionné. Les valeurs de liste déroulante ont le format x : y, où X est le préfixe d’espace de noms d’un schéma de propriété dans le **liste des schémas de propriété**, et Y est le nom du nœud d’un **élément de champ** nœud ce schéma de propriété.  
  
     La valeur par défaut dans la liste déroulante est le premier schéma de propriété **(élément de champ)** nœud qui n’a pas encore été promu, triées par ordre alphabétique sur tous les schémas de propriété pertinents. Il s'agira rarement du nœud de schéma de propriété dans lequel vous avez l'intention de promouvoir un nœud de schéma donné.  
  
10. Vous pouvez sélectionner pour la promotion des nœuds supplémentaires dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue en cliquant sur **ajouter** et puis effectuez l’étape 9 après chaque sélection.  
  
11. Lorsque vous avez terminé, cliquez sur **OK**.  
  
     Les nœuds que vous avez sélectionné pour promouvoir sont désormais **champs de propriété** et sont associés à un particulier **élément de champ** nœud dans un schéma de propriété.  
  
### <a name="to-promote-a-property-as-a-property-field-using-the-quick-promotion-command"></a>Pour promouvoir une propriété en tant que champ de propriété à l'aide de l'option Promotion rapide  
  
1.  Dans l’Éditeur BizTalk, ouvrez le schéma pour lequel vous souhaitez promouvoir une ou plusieurs propriétés, puis sélectionnez le (premier) **Fieldelement**, **attribut de champ**, ou **enregistrement** nœud que vous souhaitez promouvoir en tant qu’un **champ de propriété**.  
  
    > [!NOTE]
    >  Vous pouvez uniquement promouvoir **enregistrement** nœuds s’ils sont configurés pour qu’il contienne uniquement du contenu simple en ayant sa **Content Type** propriété **SimpleContent**.  
  
2.  Cliquez sur le nœud sélectionné, cliquez sur **promouvoir**, puis cliquez sur **Promotion rapide**.  
  
     Si le schéma de propriété par défaut, comme défini par le **nom de schéma de propriété par défaut** propriété sur le **Pages de propriétés** pour le schéma pertinent, n’existe pas, vous devez cliquer sur **OK**dans la boîte de dialogue de confirmation pour créer le schéma de propriété par défaut et le configurer avec une **élément de champ** nœud pour prendre en compte votre promotion de propriétés.  
  
> [!NOTE]
>  Vous pouvez afficher et gérer les propriétés promues à l’aide de la **Promotions rapides** fonctionnalité en ouvrant le **promouvoir les propriétés** boîte de dialogue, puis cliquez sur le **champs de propriété** onglet. Pour obtenir des instructions pour l’ouverture du **promouvoir les propriétés** boîte de dialogue, consultez [ouverture de la boîte de dialogue promouvoir les propriétés](../core/how-to-open-the-promote-properties-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Promotion des propriétés](../core/promoting-properties.md)   
 [Comment créer des schémas de propriété](../core/how-to-create-property-schemas.md)   
 [Façons d’utiliser le contenu de Message pour le traitement des messages de contrôle](../core/ways-to-use-message-content-to-control-message-processing.md)