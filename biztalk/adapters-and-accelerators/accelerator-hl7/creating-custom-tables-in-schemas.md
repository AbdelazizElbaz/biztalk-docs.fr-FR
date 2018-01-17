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
ms.openlocfilehash: a663dd593123e647f2f466b6d472d60bb32be1be
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="creating-custom-tables-in-schemas"></a><span data-ttu-id="3896b-102">Création de Tables personnalisées dans les schémas</span><span class="sxs-lookup"><span data-stu-id="3896b-102">Creating Custom Tables in Schemas</span></span>
<span data-ttu-id="3896b-103">Vous pouvez créer une table personnalisée dans le tablevalues_\<*version*\>schéma .xsd.</span><span class="sxs-lookup"><span data-stu-id="3896b-103">You can create a custom table in the tablevalues_\<*version*\>.xsd common schema.</span></span> <span data-ttu-id="3896b-104">Vous pouvez baser une table personnalisée sur un type de données existant, un type de base de données ou sur une énumération définie dans une table.</span><span class="sxs-lookup"><span data-stu-id="3896b-104">You can base a custom table on an existing data type, a base data type, or on an enumeration defined in a table.</span></span>  
  
### <a name="to-create-a-z-table"></a><span data-ttu-id="3896b-105">Pour créer une table Z</span><span class="sxs-lookup"><span data-stu-id="3896b-105">To create a Z table</span></span>  
  
1.  <span data-ttu-id="3896b-106">Dans l’Explorateur de solutions, ouvrez le fichier de schéma de type de données commun **tablevalues_\<*version*\>.xsd**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="3896b-106">In Solution Explorer, open the common data-type schema file **tablevalues_\<*version*\>.xsd**, and then click **Open**.</span></span>  
  
2.  <span data-ttu-id="3896b-107">Avec le bouton droit dans l’Éditeur BizTalk, **HL7DefinedTables**, pointez sur **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**.</span><span class="sxs-lookup"><span data-stu-id="3896b-107">In BizTalk Editor, right-click **HL7DefinedTables**, point to **Insert Schema Node**, and then click **Child Field Element**.</span></span>  
  
3.  <span data-ttu-id="3896b-108">Nommez la table avec une balise commençant par la lettre « Z ».</span><span class="sxs-lookup"><span data-stu-id="3896b-108">Name the table with a tag starting with the letter "Z".</span></span>  
  
4.  <span data-ttu-id="3896b-109">Dans le volet Propriétés, tapez les valeurs souhaitées pour les propriétés spécifiques, en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="3896b-109">In the Properties pane, type the values you want for specific properties, as needed.</span></span>  
  
5.  <span data-ttu-id="3896b-110">Pour associer une énumération avec la table, dans le volet Propriétés, définissez **Derived By** à **Restriction**, cliquez sur **énumération**, cliquez sur le bouton de sélection (...)  **Énumération**, puis tapez les valeurs que vous voulez l’énumération pour contenir dans l’éditeur d’énumération.</span><span class="sxs-lookup"><span data-stu-id="3896b-110">To associate an enumeration with the table, in the Properties pane, set **Derived By** to **Restriction**, click **Enumeration**, click the ellipsis (…) button for **Enumeration**, and then type the values that you want the enumeration to contain in the Enumeration Editor.</span></span> <span data-ttu-id="3896b-111">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3896b-111">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3896b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3896b-112">See Also</span></span>  
 <span data-ttu-id="3896b-113">[Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="3896b-113">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="3896b-114">[Création de Segments de Z déclaré](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span><span class="sxs-lookup"><span data-stu-id="3896b-114">[Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span></span>  
 <span data-ttu-id="3896b-115">[Création de Types de données personnalisés dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="3896b-115">[Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span></span>  
 <span data-ttu-id="3896b-116">[Extension des énumérations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="3896b-116">[Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span></span>  
 [<span data-ttu-id="3896b-117">Gestion des segments Z non déclarés</span><span class="sxs-lookup"><span data-stu-id="3896b-117">Handling Undeclared Z Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)