---
title: "Création de Types de données personnalisés dans les schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas, creating Z data types [Z objects]
- data types, creating [Z objects]
- Z objects, creating Z data types
ms.assetid: e545c849-d414-4d5d-bb56-d3f9d5238c70
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09b07843a6e010021b00a1ffa7c3010977d1d3c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-custom-data-types-in-schemas"></a>Création de Types de données personnalisés dans les schémas
Vous pouvez créer un type de données personnalisé dans le datatypes_\<*version*> schéma .xsd. Vous pouvez baser un type de données personnalisé sur un type de données existant, un type de base de données ou sur une énumération définie dans une table.  
  
### <a name="to-create-a-z-data-type"></a>Pour créer un type de données Z  
  
1.  Dans l’Explorateur de solutions de Visual Studio, ouvrez le fichier de schéma de type de données commun (**datatypes_\<*version*> .xsd **), puis cliquez sur **ouvrir**.  
  
2.  Avec le bouton droit dans l’Éditeur BizTalk, **HL7DefinedDataTypes**, pointez sur **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant** pour créer un type de données du composant, ou cliquez sur  **Élément enfant** pour créer un type de données simple.  
  
3.  Nommez le type de données avec une balise de trois caractères commençant par « Z ».  
  
4.  Dans le volet Propriétés, tapez les valeurs souhaitées pour **Base Data Type**, **Type de données**et d’autres propriétés, en fonction des besoins.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Création de Segments de Z déclaré](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [Création de Tables personnalisées dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)   
 [Extension des énumérations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)   
 [La gestion des Segments de Z non déclaré](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)