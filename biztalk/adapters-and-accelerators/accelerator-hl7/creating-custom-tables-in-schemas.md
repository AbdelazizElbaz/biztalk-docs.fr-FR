---
title: "Création de Tables personnalisées dans les schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, Z tables [Z objects]
- Z objects, creating Z tables
- 2.X schemas, creating Z tables
ms.assetid: d6ab8ac9-a835-4ec0-9ddd-76ff267a3cbd
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7c3ce69e60517f90af4031bf76691a551afcbe2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-custom-tables-in-schemas"></a>Création de Tables personnalisées dans les schémas
Vous pouvez créer une table personnalisée dans le tablevalues_\<*version*> schéma .xsd. Vous pouvez baser une table personnalisée sur un type de données existant, un type de base de données ou sur une énumération définie dans une table.  
  
### <a name="to-create-a-z-table"></a>Pour créer une table Z  
  
1.  Dans l’Explorateur de solutions, ouvrez le fichier de schéma de type de données commun  **tablevalues_\<*version*> .xsd **, puis cliquez sur **ouvrir**.  
  
2.  Avec le bouton droit dans l’Éditeur BizTalk, **HL7DefinedTables**, pointez sur **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**.  
  
3.  Nommez la table avec une balise commençant par la lettre « Z ».  
  
4.  Dans le volet Propriétés, tapez les valeurs souhaitées pour les propriétés spécifiques, en fonction des besoins.  
  
5.  Pour associer une énumération avec la table, dans le volet Propriétés, définissez **Derived By** à **Restriction**, cliquez sur **énumération**, cliquez sur le bouton de sélection (...)  **Énumération**, puis tapez les valeurs que vous voulez l’énumération pour contenir dans l’éditeur d’énumération. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Création de Segments de Z déclaré](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [Création de Types de données personnalisés dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [Extension des énumérations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)   
 [La gestion des Segments de Z non déclaré](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)