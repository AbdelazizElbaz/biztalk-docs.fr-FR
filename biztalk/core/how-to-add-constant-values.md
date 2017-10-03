---
title: Comment ajouter des valeurs de constante | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f46bf66e-caf2-4352-930f-c3c43a5717c3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 398e2f4d176fdfab866cc8c87ce19aaf523a1b03
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-constant-values"></a>Comment ajouter des valeurs de constante
Lors du test des mappages, il vous arrivera de vouloir définir des valeurs constantes.  
  
## <a name="set-constant-values-for-nodes-in-the-source-or-destination-schema-trees"></a>Définir des valeurs constantes pour les nœuds dans la source ou la destination des arborescences de schéma  
  
1.  Sélectionnez un enregistrement ou un champ dans les arborescences de schémas source ou de destination.  
  
2.  Dans la fenêtre Propriétés, dans le **général** catégorie, utilisez la **valeur** Entrez une valeur pour l’enregistrement sélectionné ou le champ de propriété.  
  
    > [!NOTE]
    >  Vous pouvez associer une valeur uniquement avec un enregistrement avec son **contenu** propriété **texte uniquement** ou **mixte**.  
  
 Pour un nœud dans le schéma source, si vous définissez la **valeur** propriété  **\<vide >**, le message d’instance généré pour le schéma source contient une valeur vide pour le nœud correspondant.  
  
 Il arrive que tous les champs du schéma cible ne soient pas utilisés (certains champs du schéma cible ne possèdent pas de liens entrants). Dans ce cas, l’opération Test Map génère erreur, à condition que la **valider l’entrée TestMap** ou **valider la sortie TestMap** propriétés sont définies sur **True**. Pour éviter les erreurs de mappage de Test dans ce cas, définissez la **valeur** propriété du nœud à une valeur constante ou  **\<vide >**. Utilisez  **\<vide >** si vous ne souhaitez pas définir de données arbitraires pour les champs du schéma cible inutilisées.  
  
## <a name="see-also"></a>Voir aussi  
[Validez et testez vos mappages](../core/how-to-configure-map-validation-and-test-parameters.md)