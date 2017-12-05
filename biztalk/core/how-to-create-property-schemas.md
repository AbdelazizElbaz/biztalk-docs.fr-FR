---
title: "Comment créer des schémas de propriété | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24086dea-62b8-4ef6-8af8-eb4ab7c3c018
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee97f4cb3065fdb201ec19f88a79e7899f03ac49
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-property-schemas"></a>Comment créer des schémas de propriété
Si vous choisissez de promouvoir des champs en tant que champs de propriété, vous devez d'abord définir un schéma de propriété. Ce schéma de propriété spécifie un ensemble de champs non structuré dans lequel vous pouvez promouvoir des champs depuis un message d'instance défini par un schéma associé à votre schéma.  
  
> [!IMPORTANT]
>  Vous ne devez ni copier ni modifier un schéma de propriété existant pour créer un schéma. Le schéma de propriété contient des données internes propres au schéma.  
  
> [!NOTE]
>  Il n'est pas nécessaire de créer un schéma de propriété pour promouvoir des champs distinctifs.  
  
### <a name="to-create-a-property-schema"></a>Pour créer un schéma de propriété  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit à un projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue le **modèles** , cliquez sur **schéma de propriété**.  
  
3.  Dans le **nom** zone, tapez un nom pour le schéma, puis cliquez sur **ajouter**.  
  
     Le nouveau schéma de propriété s’ouvre, et il contient déjà un **élément de champ** nœud nommé Property1.  
  
4.  Dans l’arborescence du schéma, avec le bouton droit qui **Fieldelement** nœud, cliquez sur **renommer**, tapez un nom descriptif pour la première propriété dans le schéma, puis appuyez sur ENTRÉE.  
  
5.  Définir le **Type de données** et d’autres propriétés pertinentes, comme il convient pour le **élément de champ** nœud dans la fenêtre Propriétés.  
  
6.  Si vous souhaitez insérer **Fieldelement** nœuds pour les propriétés supplémentaires, cliquez sur le \<schéma\> nœud, cliquez sur **insérer un nœud de schéma**, puis cliquez sur  **Élément de champ enfant**, puis répétez les étapes 4 et 5. Répétez l’opération pour créer l’ensemble de **élément de champ** nœuds dans lequel vous avez l’intention de promouvoir les valeurs à partir des messages d’instance.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des schémas dans des projets](../core/managing-schemas-within-projects.md)