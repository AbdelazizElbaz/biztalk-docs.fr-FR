---
title: "Configuration de bouclage piloté par les table | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Table Looping functoids
- Table Extractor functoids, configuring
- Table Extractor functoids
- Table Extractor functoids, adding to grid
- Table Looping functoids, about Table Looping functoids
- Table Looping functoids, configuring
- Table Extractor functoids, about Table Extractor functoids
- Table Looping functoids, adding to map
ms.assetid: ecc24d9b-ebc0-4559-9746-58e3b00c02ab
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6030c721207e5b7f2c9958a50758c0ed98097c8d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="table-driven-looping-configuration"></a>Configuration de bouclage piloté par la table
Pour configurer le bouclage piloté par la table dans votre mappage, procédez comme indiqué ci-dessous :  
  
-   **Ajout d’un fonctoid Bouclage de Table à la carte.** Vous avez besoin qu’un seul **bouclage de Table** fonctoid par instance de bouclage piloté par table. Par exemple, si vous utilisez le bouclage piloté par table de dériver les informations BillTo et ShipTo, vous avez besoin qu’un seul **bouclage de Table** fonctoid dans le mappage. Toutefois, si vous utilisez le bouclage piloté par table pour dégager les informations BillTo et ShipTo et StoreName et StoreAddress, vous devrez peut-être deux **bouclage de Table** fonctoids dans votre mappage.  
  
-   **Ajouter un fonctoid Extracteur de Table plus à la page de grille affichée.** Ajoutez autant **extracteur de Table** fonctoids que vous avez besoin pour chaque **bouclage de Table** fonctoid. Le nombre de **extracteur de Table** fonctoids varie selon le nombre de champs dans le schéma de destination. Par exemple, si vous disposez d’un **AddressCode** dans votre schéma source et CompanyName, adresse, ville, état, code postal et AttentionName dans votre schéma de destination, vous devez ajouter six **extracteur de Table** fonctoids à la page de grille affichée.  
  
-   **Configurer le fonctoid Bouclage de Table avec les entrées appropriées.** Commencez par lier le **bouclage de Table** fonctoid à l’élément ou un enregistrement d’instance d’entrée. Établissez également un lien avec la structure du message d’instance de sortie. Ensuite, configurez les entrées à l’aide de la **configurer \<fonctoid\> fonctoid** boîte de dialogue. Pour plus d’informations sur la façon de configurer cette propriété, consultez [modification des propriétés de fonctoid et les paramètres d’entrée](../core/editing-functoid-properties-and-input-parameters.md) . La liste des entrées doit être complète et exhaustive, car ce sont les données que vous utiliserez pour configurer le **grille de fonctoid de Table** propriété. Les entrées doivent être définies comme suit :  
  
    -   **La première entrée.** le premier paramètre d’entrée est le lien établi avec l’enregistrement ou le champ du message d’instance d’entrée. Le **bouclage de Table** effectue un fonctoid Bouclage pour chaque instance de l’enregistrement ou le champ.  
  
        > [!NOTE]
        >  Cette entrée est obligatoire.  
  
    -   **La deuxième entrée.** le second paramètre d’entrée définit le nombre de colonnes de la grille de bouclage. La grille peut contenir jusqu’à 228 colonnes.  
  
        > [!NOTE]
        >  Cette entrée est obligatoire.  
  
    -   **Entrées restantes.** Les autres entrées pour le **bouclage de Table** fonctoid se composent d’une liste de toutes les valeurs possibles susceptibles d’apparaître dans le **grille de fonctoid de Table**.  
  
        > [!NOTE]
        >  L’attribution d’étiquettes aux liens est très utile. Sans les étiquettes, les liens apparaissent dans le **grille de fonctoid de Table** en tant que chemins spécifiés complets.  
  
         Pour obtenir des instructions sur la façon de configurer les entrées pour le **bouclage de Table** fonctoid, consultez [comment ajouter le bouclage de Table et de fonctoids Extracteur de Table à une carte](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md). En particulier, consultez les étapes 3 à 8.  
  
-   **Configurez la propriété de grille de fonctoid de Table du fonctoid Bouclage de Table.** Utilisez le **grille de fonctoid de Table** propriété pour ouvrir la **configurer le fonctoid Bouclage de Table** boîte de dialogue dans laquelle vous configurez les cellules de la grille de bouclage.  
  
     Pour obtenir des instructions sur la configuration de la grille de bouclage, voir [comment ajouter le bouclage de Table et de fonctoids Extracteur de Table à une carte](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md). Voir en particulier les étapes 9 à 10.  
  
-   **Configurez les fonctoids Extracteur de Table.** Utilisez le **paramètres d’entrée** propriété pour configurer le **extracteur de Table** entrées de fonctoid comme suit :  
  
    -   **La première entrée.** Le premier paramètre d’entrée à un **extracteur de Table** fonctoid est la **bouclage de Table** fonctoid.  
  
    -   **La deuxième entrée.** le second paramètre d’entrée spécifie la colonne sur la ligne à partir de laquelle les données doivent être extraites.  
  
     Pour obtenir des instructions sur la façon de configurer le **extracteur de Table** fonctoids associé à un **bouclage de Table** fonctoid, consultez [comment ajouter le bouclage de Table et extracteur de Table Fonctoids à un mappage](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md). Voir en particulier les étapes 11 à 16.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctoid Bouclage de table](../core/table-looping-functoid.md)   
 [Fonctoid Extracteur de table](../core/table-extractor-functoid.md)   
 [Exemple de bouclage piloté par table](../core/table-driven-looping-example.md)   
 [L’ajout de bouclage de Table et fonctoids Extracteur de Table à une carte](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)   
 [Fonctoids avancés](../core/advanced-functoids.md)   
 [Fonctoid Index](../core/index-functoid.md)   
 [Fonctoid Itération](../core/iteration-functoid.md)   
 [Fonctoid Bouclage](../core/looping-functoid.md)   
 [Fonctoid Nombre d’enregistrements](../core/record-count-functoid.md)