---
title: "La création d’une Occurrence d’un enregistrement d’existant, un élément de champ ou un nœud d’attribut de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02380f68-056c-47c4-a0d6-61d599a4685d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64f8974de22b7ee99a02d551553cb5e36f31a0d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-new-occurrence-of-an-existing-record-field-element-or-field-attribute-node"></a>La création d’une Occurrence d’un enregistrement d’existant, un élément de champ ou un nœud d’attribut de champ
Vous pouvez créer de nouvelles instances d’un objet **enregistrement**, **Fieldelement**, ou **attribut de champ** nœud telles que les modifications ultérieures apportées à n’importe quelle instance soient répercutées dans toutes les instances.  
  
### <a name="to-create-a-new-instance-of-an-existing-record-field-element-or-field-attribute-node"></a>Pour créer une instance d’un nœud Enregistrement, Élément de champ ou Attribut de champ existant  
  
1.  Sélectionnez la version d’origine **enregistrement**, **élément de champ**, ou **attribut de champ** nœud, vérifiez que son **Base Data Type** propriété est définie correctement, puis, dans son **Data Structure Type** (**enregistrement** nœuds) ou son **Type de données** (**élément de champ** et  **Attribut de champ** nœuds) propriété, tapez un nom de type de données personnalisé.  
  
2.  Insérer le nouvel **enregistrement**, **Fieldelement**, ou **attribut de champ** nom que vous avez tapé à l’étape 1 de type de nœud et définissez une des propriétés suivantes pour les données personnalisées.  
  
    -   Type de Structure de données (**enregistrement** nœuds)  
  
    -   Type de données (**Fieldelement** et **attribut de champ** nœuds)  
  
    > [!NOTE]
    >  Si un nouveau **enregistrement** ou **élément de champ** le nœud est un frère du nœud d’origine et vous donnez au nouveau nœud le même nom que le nœud d’origine, vous verrez un message demandant dupliquer les nœuds dans la même étendue avec le même nom. En cliquant sur **Oui** exécute la même action que le choix le nom de type de données personnalisé à l’étape 2.  
  
> [!NOTE]
>  Vous avez créé une nouvelle instance d’existants **enregistrement**, **Fieldelement**, ou **attribut de champ** nœud.  
  
> [!NOTE]
>  Certaines propriétés de **enregistrement**, **Fieldelement**, ou **attribut de champ** instances de nœud restent identiques (une modification apportée à une seule instance est une modification à toutes les instances) et d’autres propriétés peuvent être définies indépendamment pour chaque instance.  
  
## <a name="see-also"></a>Voir aussi  
 [Insertion de nœuds dans un schéma](../core/inserting-nodes-into-a-schema.md)