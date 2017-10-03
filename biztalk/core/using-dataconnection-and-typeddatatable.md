---
title: "À l’aide de TypedDataTable et DataConnection | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Retract function [Business Rules Engine], TypedData table
- RetractByType function [Business Rules Engine], TypedData table
- Retract function [Business Rules Engine], DataConnection
- RetractByType function [Business Rules Engine], DataConnection
- Assert function [Business Rules Engine], TypedData table
- Business Rules Engine, DataConnection tips
- TypedData table
- Business Rules Engine, TypedData table tips
- Assert function [Business Rules Engine], DataConnection
- Update function [Business Rules Engine], TypedData table
- Update function [Business Rules Engine], DataConnection
ms.assetid: e825803e-6626-4ddd-a77e-75a3ba2b74a4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b5a0a490023d77676cc5d156ad5126ad5d7d6c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-dataconnection-and-typeddatatable"></a>Utilisation de TypedDataTable et DataConnection
Dans de nombreux scénarios, à l’aide de **DataConnection** offre de meilleures performances et consomme moins de mémoire que l’utilisation de **TypedDataTable**. Toutefois, **TypedDataTable** peut être nécessaire dans certains cas en raison de certaines restrictions sur l’utilisation de **DataConnection**. Dans d’autres cas, à l’aide de **TypedDataTable** peut générer de meilleures performances que l’utilisation de **DataConnection**. Cette rubrique décrit les critères et facteurs à examiner pour choisir l'approche appropriée.  
  
## <a name="when-to-use-typeddatatable-instead-of-dataconnection"></a>Quand utiliser TypedDataTable à la place de DataConnection  
 Utilisez TypedDataTable à la place de DataConnection dans les cas suivants :  
  
-   Les données doivent être modifiées, mais la table ne possède pas de clé primaire. Pour apporter des modifications de données à l’aide de **DataConnection**, une clé primaire est nécessaire. Par conséquent, s’il n’existe aucune clé primaire, **TypedDataTable** est la seule approche viable.  
  
    > [!NOTE]
    >  Le moteur de règles met uniquement à jour les valeurs dans la mémoire pour un **TypedDataTable**. Il incombe à l'appelant de rendre ces modifications permanentes.  
  
-   La sélectivité est élevée. Ceci signifie qu'un grand pourcentage de lignes de la table réussira les tests spécifiés comme conditions de règle. Dans ce cas, **DataConnection** ne fournit pas beaucoup d’avantages et il peut effectuer plus mauvais que **TypedDataTable**.  
  
-   La table est généralement petite, avec moins de 500 lignes. Notez que ce nombre peut être plus grand ou plus petit selon la forme de règle et la mémoire disponible pour le moteur de règles.  
  
-   Le comportement de type chaînage de règle est attendu dans un ensemble de règles. Appel de la **mise à jour** fonctionnent sur un **DataConnection** n’est pas pris en charge, mais vous pouvez appeler **DataConnection.Update** dans une règle à l’aide d’une méthode d’assistance. Lorsque le chaînage des propriétés de la règle est obligatoire, **TypedDataTable** est un meilleur choix.  
  
-   Une ou plusieurs colonnes de la table contiennent une très grande quantité de données inutiles aux règles. Il s'agit par exemple d'une base de données d'image où les colonnes contiennent l'image (grande quantité de données), le nom, la date, etc. Si l'image n'est pas requise, il peut être préférable de sélectionner uniquement les colonnes requises par les règles. Par exemple, peut être plus efficace que l’utilisation d’émettant une requête telle que « SELECT Name, Date à partir de la TABLE » **DataConnection**.  
  
-   Si de nombreuses règles besoin ou mettre à jour la même ligne de base de données, à l’aide un **TypedDataTable**, la ligne est partagée entre toutes les règles, et si la condition est identique (par exemple, Table.Column == 5), l’évaluation de condition peut être optimisée. Avec un **DataConnection**, en règle générale, une requête est générée pour chaque règle utilise le **DataConnection**. Bien que les lignes soient réutilisées (si la table possède une clé primaire), les requêtes multiples peuvent être générées pour obtenir les mêmes données chaque fois.  
  
## <a name="when-to-use-dataconnection-instead-of-typeddatatable"></a>Quand utiliser DataConnection à la place de TypedDataTable  
 Utilisez DataConnection à la place de TypedDataTable dans les cas suivants :  
  
-   La table contient un grand nombre de lignes, mais la sélectivité est faible — seul un faible pourcentage de lignes satisferont les conditions de règle.  
  
-   Seule une table de base de données est volumineuse ; tous les autres objets utilisés dans la règle ont un petit nombre d'instances. Dans le pire des cas, le nombre de requêtes exécutées sur la base de données est égal au produit de toutes les autres instances utilisées dans la règle.  
  
-   Les règles se composent exclusivement de conditions conjonctives et des objets autres que la table de base de données sont utilisés dans ces règles.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données dans le moteur de règles d’entreprise](../core/data-access-in-the-business-rule-engine.md)