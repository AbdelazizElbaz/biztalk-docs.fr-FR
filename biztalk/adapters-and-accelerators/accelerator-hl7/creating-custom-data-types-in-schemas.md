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
# <a name="creating-custom-data-types-in-schemas"></a><span data-ttu-id="be0cb-102">Création de Types de données personnalisés dans les schémas</span><span class="sxs-lookup"><span data-stu-id="be0cb-102">Creating Custom Data Types in Schemas</span></span>
<span data-ttu-id="be0cb-103">Vous pouvez créer un type de données personnalisé dans le datatypes_\<*version*> schéma .xsd.</span><span class="sxs-lookup"><span data-stu-id="be0cb-103">You can create a custom data type in the datatypes_\<*version*>.xsd common schema.</span></span> <span data-ttu-id="be0cb-104">Vous pouvez baser un type de données personnalisé sur un type de données existant, un type de base de données ou sur une énumération définie dans une table.</span><span class="sxs-lookup"><span data-stu-id="be0cb-104">You can base a custom data type on an existing data type, a base data type, or on an enumeration defined in a table.</span></span>  
  
### <a name="to-create-a-z-data-type"></a><span data-ttu-id="be0cb-105">Pour créer un type de données Z</span><span class="sxs-lookup"><span data-stu-id="be0cb-105">To create a Z data type</span></span>  
  
1.  <span data-ttu-id="be0cb-106">Dans l’Explorateur de solutions de Visual Studio, ouvrez le fichier de schéma de type de données commun (**datatypes_\<*version*> .xsd **), puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="be0cb-106">In Solution Explorer of Visual Studio, open the common data-type schema file (**datatypes_\<*version*>.xsd**), and then click **Open**.</span></span>  
  
2.  <span data-ttu-id="be0cb-107">Avec le bouton droit dans l’Éditeur BizTalk, **HL7DefinedDataTypes**, pointez sur **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant** pour créer un type de données du composant, ou cliquez sur  **Élément enfant** pour créer un type de données simple.</span><span class="sxs-lookup"><span data-stu-id="be0cb-107">In BizTalk Editor, right-click **HL7DefinedDataTypes**, point to **Insert Schema Node**, and then click **Child Record** to create a component data type, or click **Child Element** to create a simple data type.</span></span>  
  
3.  <span data-ttu-id="be0cb-108">Nommez le type de données avec une balise de trois caractères commençant par « Z ».</span><span class="sxs-lookup"><span data-stu-id="be0cb-108">Name the data type with a three-character tag starting with "Z".</span></span>  
  
4.  <span data-ttu-id="be0cb-109">Dans le volet Propriétés, tapez les valeurs souhaitées pour **Base Data Type**, **Type de données**et d’autres propriétés, en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="be0cb-109">In the Properties pane, type the values you want for **Base Data Type**, **Data Type**, and other properties, as needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be0cb-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be0cb-110">See Also</span></span>  
 <span data-ttu-id="be0cb-111">[Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="be0cb-111">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="be0cb-112">[Création de Segments de Z déclaré](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span><span class="sxs-lookup"><span data-stu-id="be0cb-112">[Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span></span>  
 <span data-ttu-id="be0cb-113">[Création de Tables personnalisées dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="be0cb-113">[Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span></span>  
 <span data-ttu-id="be0cb-114">[Extension des énumérations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="be0cb-114">[Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span></span>  
 [<span data-ttu-id="be0cb-115">La gestion des Segments de Z non déclaré</span><span class="sxs-lookup"><span data-stu-id="be0cb-115">Handling Undeclared Z Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)