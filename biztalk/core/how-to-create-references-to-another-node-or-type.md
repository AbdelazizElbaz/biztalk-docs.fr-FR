---
title: "Comment créer des références à un autre nœud ou Type | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c60be9ad-01a9-40e7-b43b-8c3d09bbb32f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 643f39b9a42e2566f77371096d7305f56e11a328
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-references-to-another-node-or-type"></a>Créer des références à un autre nœud ou Type
Vous pouvez utiliser des nœuds globaux pour créer des types de données, ou fragments de structure, réutilisables dont vous pouvez vous servir dans votre schéma dès lors que cette structure est appropriée. Vous pouvez utiliser uniquement les nœuds qui sont des enfants directs de la **schéma** nœud pour créer des types globaux.  
  
 Vous pouvez également créer des références cycliques à l’aide des types de données des nœuds qui ne sont pas des descendants directs du **schéma** nœud. Cela se révèle utile pour représenter des structures récursives dans des schémas.  
  
 Cette rubrique fournit des instructions étape par étape concernant différents types de nœuds globaux ainsi qu'à propos de la manière d'y faire référence pour les utiliser.  
  
 **Création de déclarations globales**  
  
 Vous pouvez créer des types globaux à l'aide d'enregistrements, de champs ou d'attributs. Les types globaux créés à partir d'enregistrements ne peuvent être utilisés que dans les enregistrements. De même, les types créés à partir de champs ne peuvent être utilisés que dans les champs et les types d'attribut ne peuvent être utilisés que dans les attributs. Les procédures suivantes décrivent comment définir et utiliser des déclarations globales.  
  
## <a name="create-a-global-declaration-from-a-node"></a>Créer une déclaration globale à partir d’un nœud  
  
1.  Sélectionnez le **enregistrement** , **attribut de champ**, ou **élément de champ** dont vous souhaitez rendre disponible globalement le type de nœud.  
  
2.  Dans le **propriétés** fenêtre, tapez un nom dans la **Data Structure Type** liste qui sera utilisé comme nom global pour le type complexe et appuyez sur ENTRÉE.  
  
## <a name="create-a-globally-defined-sequence-group-node-choice-group-node-or-all-group-node"></a>Créer un nœud de groupe séquence définie globalement, nœud groupe choix ou nœud groupe tous  
  
1.  Sélectionnez le **enregistrement** nœud dans lequel vous souhaitez insérer le nœud groupe globalement défini.  
  
2.  Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **groupe séquence**, **groupe choix**, ou **toutes les Groupe**, le cas échéant.  
  
3.  Créez une structure dans le groupe nouvellement inséré. Par exemple, insérez **enregistrement** ou **élément de champ** nœuds pour exprimer la structure des données dans le nœud de groupe.  
  
    > [!NOTE]
    >  Groupe de séquences, **groupe choix**, et **groupe tous** nœuds peuvent uniquement contenir des nœuds qui correspondent à des éléments XML et par conséquent pas contenir **attribut de champ** nœuds.  
  
4.  Sélectionnez le nœud de groupe inséré à l'étape 2.  
  
5.  Dans la fenêtre Propriétés, cliquez sur **référence du groupe**, tapez un nom dans le champ valeur, puis appuyez sur ENTRÉE.  
  
     En fournissant un nom dans la **référence du groupe** propriété, vous avez défini globalement le nœud de groupe, après laquelle vous pouvez associer d’autres nœuds de groupe avec ce type globalement défini (structure).  
  
## <a name="create-a-globally-defined-attribute-group-node"></a>Créer un nœud groupe attribut globalement défini  
  
1.  Sélectionnez le **enregistrement** nœud dans lequel vous souhaitez insérer globalement défini **groupe d’attributs** nœud.  
  
2.  Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **groupe d’attributs**.  
  
     Cette opération ajoute une **groupe d’attributs** à la fin des nœuds enfants du nœud de **enregistrement** nœud.  
  
3.  Ajouter les **attribut de champ** ou **groupe d’attributs** nœuds à votre **groupe d’attributs**.  
  
4.  Si vous le souhaitez, si vous souhaitez renommer le **groupe d’attributs** nœud, sélectionnez le **groupe d’attributs** nœud et modifier son **référence du groupe** propriété à un nouveau nom de votre choix.  
  
     Les groupes d'attributs sont toujours globaux et référencés à partir de leur point d'utilisation.  
  
## <a name="use-a-type-or-group-that-has-been-globally-defined"></a>Utiliser un type ou un groupe qui a été globalement défini  
  
1.  Sélectionnez le nœud pour lequel vous souhaitez utiliser un type globalement défini.  
  
2.  Dans la fenêtre Propriétés, sélectionnez le type globalement défini dans la liste déroulante pour le **Data Structure Type** propriété (**enregistrement** nœuds), **Type de données** (depropriété **Élément de champ** et **attribut de champ** nœuds), ou **référence du groupe** (**groupe séquence**, **le groupe choix**, **Groupe tous**, et **groupe d’attributs** nœuds). Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
    > [!NOTE]
    >  Les changements apportés ultérieurement au type ou groupe globalement défini peuvent être effectués dans tous les emplacements de schéma où il apparaît. Ces modifications seront appliquées à tous ces emplacements au fur et à mesure que vous les apporterez dans l'emplacement unique arbitraire.  
  
 Une fois que vous avez créé une déclaration globale, vous êtes dans l'impossibilité de la supprimer en une seule étape. Toutefois, vous pouvez la supprimer à l’aide de la **les types de données globaux nettoyage** boîte de dialogue lorsque le schéma est enregistré, à l’aide de la procédure suivante.  
  
## <a name="delete-a-global-declaration"></a>Supprimer une déclaration globale  
  
1.  Supprimez tous les nœuds dans lesquels ce type ou ce groupe global est utilisé, ou spécifiez un autre type ou groupe à utiliser dans tous ces nœuds, ou combinez ces deux opérations. Pour obtenir des instructions pour la suppression d’un nœud, consultez [suppression de nœuds](../core/how-to-delete-nodes.md).  
  
2.  Lors de l’enregistrement de la spécification, la **les types de données globaux nettoyage** boîte de dialogue s’affiche. Sélectionnez la déclaration globale que vous souhaitez supprimer complètement de votre spécification, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Le **les types de données globaux nettoyage** boîte de dialogue s’affiche chaque fois que vous enregistrez un schéma avec les types de données inutilisé. Si cette boîte de dialogue n'apparaît pas, c'est soit que tous les types de données sont utilisés quelque part dans le schéma, soit que le schéma n'a pas été modifié depuis son ouverture, auquel cas il contient peut-être encore des types de données non utilisés précédemment conservés.  
  
## <a name="create-cyclical-references-to-another-node"></a>Créer des références cycliques à un autre nœud  
 Vous pouvez créer des références cycliques à un nœud pour représenter des éléments récursifs de schéma. Pour ce faire, vous devez créer un nœud dont le type est défini par un enregistrement associé. Imaginez par exemple un message d'instance intégré dans un nombre arbitraire d'enveloppes partageant la même structure. À l'aide de références cycliques, vous pouvez créer un schéma définissant de tels messages d'instance.  
  
### <a name="create-a-cyclical-reference"></a>Créer une référence cyclique  
  
1.  Sélectionnez un **enregistrement** nœud pour lequel vous voulez créer une référence récursive. Il s'agit du nœud représentant la partie supérieure de la structure récursive.  
  
2.  Dans la fenêtre Propriétés, vérifiez que le **Data Structure Type** a une valeur.  
  
     Vérifier que le **enregistrement** nœud dispose d’un jeu nommé type associé est nécessaire, car les structures récursives sont définies lorsqu’un type contient lui-même. Les types ne peuvent se contenir eux-mêmes que via une utilisation imbriquée de types globaux nommés.  
  
3.  Sélectionnez un enfant **enregistrement** nœud enfant ou insérez un **enregistrement** nœud.  
  
4.  Pour l’enfant **enregistrement** nœud, dans la fenêtre Propriétés, dans le **Data Structure Type** , sélectionnez la structure de données identifiée à l’étape 2.  
  
> [!IMPORTANT]
>  - Le **Min Occurs** propriété du nœud répété doit être définie sur zéro (**0**). Sa définition sur un (**1**) provoque une boucle infinie.  
>
>  - Si vous importez un schéma qui contient un élément récursif, l'Éditeur BizTalk ne vérifie pas automatiquement que ce dernier est valide.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des nœuds dans un schéma](../core/managing-the-nodes-within-a-schema.md)