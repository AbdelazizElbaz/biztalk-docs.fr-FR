---
title: "Création de Segments de Z déclaré | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Z objects, creating segments
- segments, creating Z segments [Z objects]
- Z segments, creating
- creating, Z segments [Z objects]
ms.assetid: afd1b7b7-089e-4c6a-a063-e708431bb888
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dae9148547f527d29238b6080cd499be8da7b7e6
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="creating-declared-z-segments"></a><span data-ttu-id="4adcc-102">Création de Segments de Z déclaré</span><span class="sxs-lookup"><span data-stu-id="4adcc-102">Creating Declared Z Segments</span></span>
<span data-ttu-id="4adcc-103">Vous pouvez créer des segments Z déclarés à tout niveau d’un schéma (contrairement à non déclaré Z des segments, qui doit être la dernière partie d’un message multipartie, suivant le corps).</span><span class="sxs-lookup"><span data-stu-id="4adcc-103">You can create declared Z segments at any level of a schema (unlike undeclared Z segments, which must be the last part of a multi-party message, following the body part).</span></span>  
  
### <a name="to-create-a-z-segment-in-biztalk-editor"></a><span data-ttu-id="4adcc-104">Pour créer un segment de Z dans l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="4adcc-104">To create a Z segment in BizTalk Editor</span></span>  
  
1.  <span data-ttu-id="4adcc-105">Dans l’Explorateur de solutions de Visual Studio, cliquez sur le schéma auquel vous souhaitez ajouter un segment de Z, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="4adcc-105">In Solution Explorer of Visual Studio, right-click the schema to which you want to add a Z segment, and then click **Open**.</span></span>  
  
2.  <span data-ttu-id="4adcc-106">Dans l’Éditeur BizTalk, cliquez sur le nœud portant le nom du schéma, pointez sur **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**.</span><span class="sxs-lookup"><span data-stu-id="4adcc-106">In BizTalk Editor, right-click the node with the name of the schema, point to **Insert Schema Node**, and then click **Child Record**.</span></span>  
  
3.  <span data-ttu-id="4adcc-107">Nom de l’enregistrement en commençant le nom avec trois caractères alphanumériques, en majuscules, avec le premier chiffre en cours à « Z ».</span><span class="sxs-lookup"><span data-stu-id="4adcc-107">Name the record starting the name with three alphanumeric digits, in capitals, with the first digit being "Z".</span></span> <span data-ttu-id="4adcc-108">(La balise de segment Z doit contenir trois caractères.) Pour ce faire, insérez un trait de soulignement (_) et puis ajoutez une brève description du segment.</span><span class="sxs-lookup"><span data-stu-id="4adcc-108">(The Z segment tag must include three characters.) Insert an underscore (_), and then add a short description of the segment.</span></span> <span data-ttu-id="4adcc-109">La description doit être une série de mots, sans espaces, avec la première lettre de chaque mot en majuscules.</span><span class="sxs-lookup"><span data-stu-id="4adcc-109">The description should be one or a series of words, without spaces, with the first letter of each word capitalized.</span></span> <span data-ttu-id="4adcc-110">Le dernier mot doit être « Segment ».</span><span class="sxs-lookup"><span data-stu-id="4adcc-110">The last word should be "Segment".</span></span> <span data-ttu-id="4adcc-111">(Un exemple est « ZPP_PatientPreferencesSegment.) Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="4adcc-111">(An example is "ZPP_PatientPreferencesSegment.) Press **Enter**.</span></span>  
  
4.  <span data-ttu-id="4adcc-112">Dans le volet Propriétés, tapez les propriétés souhaitées pour le segment Z, y compris **Data Structure Type** (nom de schéma ou XSD : anyType), **Max Occurs**, et **Min Occurs**.</span><span class="sxs-lookup"><span data-stu-id="4adcc-112">In the Properties pane, type the properties you want for the Z segment, including **Data Structure Type** (schema name or xsd:anyType), **Max Occurs**, and **Min Occurs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4adcc-113">Si vous entrez un type de structure de données pour l’enregistrement, vous ne serez pas en mesure d’ajouter un élément de champ enfant.</span><span class="sxs-lookup"><span data-stu-id="4adcc-113">If you enter a data structure type for the record, you will not be able to add a child field element.</span></span>  
  
5.  <span data-ttu-id="4adcc-114">Dans l’Éditeur BizTalk, cliquez sur le nom du segment Z, pointez sur **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**.</span><span class="sxs-lookup"><span data-stu-id="4adcc-114">In BizTalk Editor, right-click the name of the Z segment, point to **Insert Schema Node**, then click **Child Field Element**.</span></span>  
  
6.  <span data-ttu-id="4adcc-115">Tapez le nom du champ, en commençant le nom avec les trois premiers chiffres du nom du segment, suivi d’un point et le numéro du champ, suivi d’un trait de soulignement et une brève description du champ.</span><span class="sxs-lookup"><span data-stu-id="4adcc-115">Type the name of the field, starting the name with the first three digits of the segment name, followed by a period and the number of the field, followed by an underscore and then a short description of the field.</span></span> <span data-ttu-id="4adcc-116">La description doit être une série de mots, sans espaces, avec la première lettre de chaque mot en majuscules.</span><span class="sxs-lookup"><span data-stu-id="4adcc-116">The description should be one or a series of words, without spaces, with the first letter of each word capitalized.</span></span> <span data-ttu-id="4adcc-117">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="4adcc-117">Press **Enter**.</span></span>  
  
7.  <span data-ttu-id="4adcc-118">Dans le volet Propriétés, tapez les propriétés souhaitées pour le segment Z, y compris **Type de données**, **Nillable**, **fixe**, **Max Occurs**, et **Min Occurs**.</span><span class="sxs-lookup"><span data-stu-id="4adcc-118">In the Properties pane, type the properties you want for the Z segment, including **Data Type**, **Nillable**, **Fixed**, **Max Occurs**, and **Min Occurs**.</span></span>  
  
8.  <span data-ttu-id="4adcc-119">Pour créer un champ avec les composants, créez le champ en tant qu’enregistrement et puis créer un élément enfant de cet enregistrement pour chaque composant.</span><span class="sxs-lookup"><span data-stu-id="4adcc-119">To create a field with components, create the field as a record, and then create a child element of that record for each component.</span></span> <span data-ttu-id="4adcc-120">Pour créer un champ avec les sous-composants, créez le champ et les composants sous forme d’enregistrements et les sous-composants en tant qu’enfant éléments.</span><span class="sxs-lookup"><span data-stu-id="4adcc-120">To create a field with subcomponents, create the field and components as records, and the subcomponents as child elements.</span></span> <span data-ttu-id="4adcc-121">Notez que les sous-composants ne peut pas être des types de données composites.</span><span class="sxs-lookup"><span data-stu-id="4adcc-121">Note that subcomponents cannot be composite data types.</span></span> <span data-ttu-id="4adcc-122">Par exemple, pour le segment nommé ZPP_PatientPreferencesSegment, vous pouvez créer un champ ZPP.1_Dietary et un composant PD.1 Allergies avec un sous-composant PD.1.1_FoodGroupAllergy.</span><span class="sxs-lookup"><span data-stu-id="4adcc-122">For example, for the segment named ZPP_PatientPreferencesSegment, you might create a ZPP.1_Dietary field and a PD.1 Allergies component with a PD.1.1_FoodGroupAllergy subcomponent.</span></span> <span data-ttu-id="4adcc-123">Le sous-composant PD.1.1_FoodGroupAllergy devrait être un type de données simple.</span><span class="sxs-lookup"><span data-stu-id="4adcc-123">The PD.1.1_FoodGroupAllergy subcomponent would have to be a simple data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adcc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4adcc-124">See Also</span></span>  
 <span data-ttu-id="4adcc-125">[Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="4adcc-125">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="4adcc-126">[Création de Types de données personnalisés dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="4adcc-126">[Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span></span>  
 <span data-ttu-id="4adcc-127">[Création de Tables personnalisées dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="4adcc-127">[Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span></span>  
 <span data-ttu-id="4adcc-128">[Extension des énumérations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="4adcc-128">[Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span></span>  
 [<span data-ttu-id="4adcc-129">Gestion des segments Z non déclarés</span><span class="sxs-lookup"><span data-stu-id="4adcc-129">Handling Undeclared Z Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)