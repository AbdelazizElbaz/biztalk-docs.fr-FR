---
title: Gestion de la liste de code | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a924c814-d077-4aea-bacb-bf2e8a3dee01
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13b98fac659c30d1e8e6da50689fc2086d090be4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="code-list-management"></a>Gestion des listes de code

## <a name="overview"></a>Vue d'ensemble
Utilisez XSD pour spécifier un ensemble spécifique de valeurs valides pour un élément ou un attribut. Cette fonctionnalité est disponible en utilisant la **énumération** élément. Lorsque vous dérivez un type de données pour un **élément de champ** ou **attribut de champ** nœud par restriction, une des propriétés qui est disponible dans le **Restriction** la catégorie est la **énumération** propriété. À l’aide de cette propriété, vous pouvez ouvrir le **Éditeur d’énumération** boîte de dialogue dans laquelle vous pouvez entrer les valeurs qui doivent être considérés comme valides pour l’élément ou attribut correspondant dans les messages d’instance.  
  
 Avec les listes de codes, Microsoft BizTalk Server fournit une alternative plus puissante pour gérer les énumérations dans vos schémas. Les listes de codes utilisent une base de données Microsoft Access pour stocker les choix de vos diverses énumérations, vous permettant de les gérer d'une manière plus centralisée. En outre, si vous devez utiliser les valeurs d’énumération sont constituées de codes numériques non intuitive, qui doivent être entrées dans le formulaire à l’aide de la **énumération** propriété, les tables que vous créez une base de données Access à utiliser avec la liste de codes fonctionnalités incluent des descriptions textuelles de ces valeurs numériques. Les descriptions textuelles sont utilisées dans les **CodeList** boîte de dialogue plutôt que leur plus masquer équivalents numériques.  

## <a name="use-the-code-list"></a>Utilisez la liste de code  
 Pour utiliser la fonctionnalité des listes de codes, vous devez effectuer plusieurs étapes dont :  
  
-   Vous devez créer une base de données Access, y placer une table nommée de façon appropriée et comportant les colonnes prévues, et la renseigner avec des valeurs.  
  
    -   Le nom de la table est une combinaison de la **Standard** et **Version Standard** propriétés de la **schéma** nœud, séparé par un caractère de soulignement (_). Par exemple, si vous avez défini le **Standard** propriété de la **schéma** nœud au format XML et le **Version Standard** propriété sur Maversion1, la base de données Access spécifiée par le **Base de données codeList** propriété doit avoir une table nommée xml_maversion1.  
  
        Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

    -   Cette table doit se composer de trois colonnes généralement intitulées Code, Valeur et Description. La première colonne identifie les lignes qui sont liés entre eux, où chaque ligne fournit un choix d’énumération susceptibles d’être autorisés pour les données correspondant au **élément de champ** ou **Attribut de champ** nœud. Toutes les lignes ayant une même valeur dans la première colonne forment un groupe. Généralement, ces valeurs sont des entiers, mais elles peuvent aussi être n'importe quelle chaîne sans espace.  
  
         La deuxième et la troisième colonnes de chaque ligne doivent être configurées pour accueillir respectivement la valeur correspondante et la représentation textuelle de chaque valeur d'énumération possible.  
  
         Par exemple, la représentation suivante d'une table de base de données Access à utiliser avec la fonctionnalité Liste de codes contient deux ensembles de trois valeurs d'énumération associées. Les valeurs spécifiques de la première colonne sont arbitraires et sont utilisées pour associer les lignes liées entre elles.  
  
        |Code|Valeur|DESC|  
        |----------|-----------|----------|  
        |1|13|Rouge|  
        |1|16|Vert|  
        |1|19|Bleu|  
        |2|1|Petit|  
        |2|2|Moyenne|  
        |2|3|Élevé|  
  
-   Vous devez configurer correctement les trois propriétés de la **schéma** nœud :  
  
    -   Le **base de données CodeList** propriété doit être définie sur le nom de la base de données Access que vous avez créé.  
  
    -   Le **Standard** et **Version Standard** propriétés doivent être définies de sorte que lorsqu’elles sont combinées avec un caractère de soulignement (_) séparation, ils forment le nom de la table appropriée dans le texte spécifié Base de données Access.  
  
-   Pour faire utiliser des valeurs dans la base de données Access en un sélectionné **Fieldelement** ou **attribut de champ** nœud, vous devez configurer deux de ses propriétés :  
  
    -   Vous devez définir son **Derived By** propriété **Restriction**. L’autre propriété, vous devez configurer, **CodeList**, n’est pas activé tant que vous n’effectuez cette étape.  
  
    -   Vous devez taper une valeur dans la **CodeList** propriété qui correspond à la valeur de la première colonne (la **Code** colonne) d’une ou plusieurs lignes dans la base de données Access spécifiée. Cette action identifie l’ensemble des valeurs d’énumération que vous souhaitez faire correspondre au **Fieldelement** ou **attribut de champ** nœud.  
  
         Ensuite, vous devez cliquer sur le bouton de sélection (**...** ) situé à droite de la **CodeList** champ de valeur de propriété pour ouvrir la **CodeList** boîte de dialogue. À l’aide de cases à cocher dans cette boîte de dialogue, sélectionnez les valeurs que vous souhaitez autoriser en tant que valeurs autorisées pour les données de message d’instance correspondant au **Fieldelement** ou **attribut de champ** nœud. Il ne vous est permis que de sélectionner un sous-ensemble des valeurs disponibles. Par exemple, à l’aide de l’exemple précédent exemple de tableau, si vous tapez la valeur 1 dans le **CodeList** propriété, le **CodeList** boîte de dialogue contiendra les choix rouge, vert et bleu. Si vous activez les cases à cocher de rouge et vert et que vous ne sélectionnez pas la case à cocher pour le bleu, uniquement les deux premières couleurs apparaîtront dans le schéma XSD en tant que valeurs valides pour le **Fieldelement** ou **attribut de champ** nœud.  
  
> [!NOTE]
>  Le **CodeList** et **base de données CodeList** propriétés sont utilisées au moment du design et sont conservées dans le XSD comme des paramètres correspondants pour le **énumération** propriété. Au moment de l’exécution, toutes les valeurs sont vérifiées par rapport à la **énumération** propriété uniquement.  
  
> [!CAUTION]
>  Pour une donnée **élément de champ** ou **attribut de champ** nœud, n’utilisez pas les deux le **énumération** propriété et la **CodeList** propriété. L'utilisation de la deuxième propriété peut avoir pour effet que les valeurs entrées utilisent la première pour être remplacées.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations relatives à la création de schémas](../core/considerations-when-creating-schemas.md)