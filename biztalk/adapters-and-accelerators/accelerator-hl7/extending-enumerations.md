---
title: "Extension des énumérations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enumeration values
- 2.X schemas, enumeration values
ms.assetid: 043def35-b644-4502-a2e2-cc1a5fc0328a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 527894b27c5720a1b006387f861922eb978069b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extending-enumerations"></a><span data-ttu-id="d2dba-102">Extension des énumérations</span><span class="sxs-lookup"><span data-stu-id="d2dba-102">Extending Enumerations</span></span>
<span data-ttu-id="d2dba-103">Vous pouvez ajouter des valeurs pour les énumérations qui définissent les valeurs acceptées pour de nombreux types de champs, des segments et des données dans le corps du message HL7, accusé de réception et les schémas de corps du message.</span><span class="sxs-lookup"><span data-stu-id="d2dba-103">You can add values to the enumerations that establish accepted values for many fields, segments, and data types in HL7 message body, acknowledgment, and message body schemas.</span></span> <span data-ttu-id="d2dba-104">Cela implique la modification de l’ensemble de valeurs dans une table spécifique dans le fichier de schéma valeurs de table commune pour la version HL7 dans lequel vous travaillez (le **Tablevalues_\<***version* **> .xsd** fichier de schéma).</span><span class="sxs-lookup"><span data-stu-id="d2dba-104">This involves changing the set of values in a specific table in the common table values schema file for the HL7 version in which you are working (the **Tablevalues_\<***version***>.xsd** schema file).</span></span>  
  
 <span data-ttu-id="d2dba-105">Vous ajoutez à l’énumération d’une manière différente pour le schéma d’en-tête de message que vous effectuez dans d’autres schémas, tels que le schéma de corps de message.</span><span class="sxs-lookup"><span data-stu-id="d2dba-105">You add to the enumeration in a different way for the message header schema than you do in other schemas, such as the message body schema.</span></span> <span data-ttu-id="d2dba-106">Pour le schéma d’en-tête de message, vous devez modifier la table dans le fichier MSH_25_GLO_DEF.xsd.</span><span class="sxs-lookup"><span data-stu-id="d2dba-106">For the message header schema, you must change the table within the MSH_25_GLO_DEF.xsd file.</span></span> <span data-ttu-id="d2dba-107">Pour les autres schémas, vous modifiez la table dans le fichier de schéma de valeurs de table (tablevalues_\<version > .xsd).</span><span class="sxs-lookup"><span data-stu-id="d2dba-107">For other schemas, you change the table in the table values schema file (tablevalues_\<version>.xsd).</span></span>  
  
### <a name="to-add-an-enumeration-value-to-the-table-values-common-schema-file"></a><span data-ttu-id="d2dba-108">Pour ajouter une valeur d’énumération vers la table de valeurs courantes schéma</span><span class="sxs-lookup"><span data-stu-id="d2dba-108">To add an enumeration value to the table values common schema file</span></span>  
  
1.  <span data-ttu-id="d2dba-109">Vous devez tout d’abord déterminer la table qui contient l’énumération que vous souhaitez ajouter à.</span><span class="sxs-lookup"><span data-stu-id="d2dba-109">You first need to determine the table that contains the enumeration that you want to add to.</span></span> <span data-ttu-id="d2dba-110">Dans l’Explorateur de solutions de [!INCLUDE[vs2012](../../includes/vs2012-md.md)], ouvrez le fichier de schéma qui contient l’élément que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="d2dba-110">In Solution Explorer of [!INCLUDE[vs2012](../../includes/vs2012-md.md)], open the schema file that contains the element that you want to change.</span></span> <span data-ttu-id="d2dba-111">Dans l’Explorateur BizTalk, cliquez sur l’élément de champ que vous souhaitez ajouter une valeur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d2dba-111">In BizTalk Explorer, click the field element that you want to add a value for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2dba-112">Lorsque vous modifiez une énumération dans le fichier de schéma table valeurs courantes, tous les objets qui font référence à cette énumération sont affectées.</span><span class="sxs-lookup"><span data-stu-id="d2dba-112">When you change an enumeration in the table values common schema file, all objects that reference that enumeration are affected.</span></span>  
  
2.  <span data-ttu-id="d2dba-113">Dans le **propriétés** volet, notez le nom de la table dans le **Base Data Type** champ.</span><span class="sxs-lookup"><span data-stu-id="d2dba-113">In the **Properties** pane, note the name of the table in the **Base Data Type** field.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2dba-114">S’il existe aucune table ne répertoriés dans **Base Data Type** champ et le **Derived By** propriété n’est pas définie sur **Restricted**, puis le champ n’est pas une énumération associée .</span><span class="sxs-lookup"><span data-stu-id="d2dba-114">If there is no table listed in **Base Data Type** field, and the **Derived By** property is not set to **Restricted**, then the field does not have an enumeration associated with it.</span></span>  
  
3.  <span data-ttu-id="d2dba-115">Dans l’Explorateur de solutions, ouvrez le **Tablevalues_\<***version***> .xsd**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="d2dba-115">In Solution Explorer, open the **Tablevalues_\<***version***>.xsd**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2dba-116">Vous devez effectuer cette procédure séparément pour chaque version du schéma HL7 que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="d2dba-116">You must perform this procedure separately for each version of the HL7 schema that you want to change.</span></span>  
  
4.  <span data-ttu-id="d2dba-117">Dans l’Éditeur BizTalk, accédez à la table que vous souhaitez modifier, puis cliquez sur ce nœud de la table.</span><span class="sxs-lookup"><span data-stu-id="d2dba-117">In BizTalk Editor, browse to the table you want to change, and then click that table node.</span></span>  
  
5.  <span data-ttu-id="d2dba-118">Dans la fenêtre Propriétés, dans le **Restriction** , cliquez sur **énumération**, puis cliquez sur le bouton de sélection (...) pour ouvrir l’éditeur d’énumération.</span><span class="sxs-lookup"><span data-stu-id="d2dba-118">In the Properties window, in the **Restriction** section, click **Enumeration**, and then click the ellipsis (…) button to open the Enumeration Editor.</span></span>  
  
6.  <span data-ttu-id="d2dba-119">Dans l’éditeur d’énumération, ajouter la nouvelle valeur à la liste des valeurs existantes, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d2dba-119">In the Enumeration Editor, add the new value to the list of existing values, and then click **OK**.</span></span>  
  
### <a name="to-add-an-enumeration-value-to-a-message-header-schema"></a><span data-ttu-id="d2dba-120">Pour ajouter une valeur d’énumération à un schéma d’en-tête de message</span><span class="sxs-lookup"><span data-stu-id="d2dba-120">To add an enumeration value to a message header schema</span></span>  
  
1.  <span data-ttu-id="d2dba-121">Dans l’Explorateur de solutions, ouvrez le schéma MSH_25_GLO_DEF, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="d2dba-121">In Solution Explorer, open the MSH_25_GLO_DEF schema, and then click **Open**.</span></span>  
  
2.  <span data-ttu-id="d2dba-122">Cliquez sur le **MSH** nœud, pointez sur **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**.</span><span class="sxs-lookup"><span data-stu-id="d2dba-122">Right-click the **MSH** node, point to **Insert Schema Node**, and then click **Child Field Element**.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="d2dba-123">Ajoute un nœud de champ à MSH, appelé **champ**.</span><span class="sxs-lookup"><span data-stu-id="d2dba-123"> adds a field node to MSH, called **Field**.</span></span> <span data-ttu-id="d2dba-124">Cliquez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="d2dba-124">Click **ENTER**.</span></span>  
  
3.  <span data-ttu-id="d2dba-125">Dans le **propriétés** fenêtre, cliquez sur le **Type de données** nœud, puis dans la liste déroulante, sélectionnez la table à laquelle vous souhaitez ajouter la valeur d’énumération.</span><span class="sxs-lookup"><span data-stu-id="d2dba-125">In the **Properties** window, click the **Data Type** node, then from the drop-down list, select the table to which you want to add the enumeration value.</span></span>  
  
4.  <span data-ttu-id="d2dba-126">Dans le **propriétés** fenêtre, dans le **Restriction** , cliquez sur **énumération**, puis cliquez sur le bouton de sélection (...) pour ouvrir l’éditeur d’énumération.</span><span class="sxs-lookup"><span data-stu-id="d2dba-126">In the **Properties** window, in the **Restriction** section, click **Enumeration**, and then click the ellipsis (…) button to open the Enumeration Editor.</span></span>  
  
5.  <span data-ttu-id="d2dba-127">Dans l’éditeur d’énumération, ajouter la nouvelle valeur à la liste des valeurs existantes, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d2dba-127">In the Enumeration Editor, add the new value to the list of existing values, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d2dba-128">Lorsque vous ajoutez une valeur à l’énumération de tous les nœuds, tels que les **champ** nœud, vous ajoutez cette valeur globalement pour tous les objets qui utilisent cette table.</span><span class="sxs-lookup"><span data-stu-id="d2dba-128">When you add a value to the enumeration for any node, such as the **Field** node, you add that value globally for all objects that use that table.</span></span> <span data-ttu-id="d2dba-129">Par conséquent, vous pouvez à présent supprimer la **champ** nœud et la valeur toujours sera présent pour la table.</span><span class="sxs-lookup"><span data-stu-id="d2dba-129">As a result, you can now delete the **Field** node, and the value will still be present for the table.</span></span> <span data-ttu-id="d2dba-130">Vous pouvez le vérifier en le défilement dans le volet droit de l’Éditeur BizTalk pour la table et en vérifiant que la valeur que vous avez ajouté est présente.</span><span class="sxs-lookup"><span data-stu-id="d2dba-130">You can verify this by scrolling in the right pane of BizTalk Editor to the table, and verifying that the value that you added is present.</span></span>  
  
6.  <span data-ttu-id="d2dba-131">Cliquez sur le **champ** dans l’Éditeur BizTalk, cliquez sur **supprimer**, puis cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="d2dba-131">Right-click the **Field** node in BizTalk Editor, click **Delete**, and then click **Yes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2dba-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2dba-132">See Also</span></span>  
 <span data-ttu-id="d2dba-133">[Table les valeurs des schémas courants](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="d2dba-133">[Table Values Common Schemas](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md) </span></span>  
 <span data-ttu-id="d2dba-134">[Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="d2dba-134">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="d2dba-135">[Création de Segments de Z déclaré](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span><span class="sxs-lookup"><span data-stu-id="d2dba-135">[Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span></span>  
 <span data-ttu-id="d2dba-136">[Création de Types de données personnalisés dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="d2dba-136">[Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span></span>  
 <span data-ttu-id="d2dba-137">[Création de Tables personnalisées dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="d2dba-137">[Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span></span>  
 [<span data-ttu-id="d2dba-138">La gestion des Segments de Z non déclaré</span><span class="sxs-lookup"><span data-stu-id="d2dba-138">Handling Undeclared Z Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)