---
title: "La création d’une Occurrence d’un enregistrement d’existant, un élément de champ ou un nœud d’attribut de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02380f68-056c-47c4-a0d6-61d599a4685d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64f8974de22b7ee99a02d551553cb5e36f31a0d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-new-occurrence-of-an-existing-record-field-element-or-field-attribute-node"></a><span data-ttu-id="2efa9-102">La création d’une Occurrence d’un enregistrement d’existant, un élément de champ ou un nœud d’attribut de champ</span><span class="sxs-lookup"><span data-stu-id="2efa9-102">How to Create a New Occurrence of an Existing Record, Field Element, or Field Attribute Node</span></span>
<span data-ttu-id="2efa9-103">Vous pouvez créer de nouvelles instances d’un objet **enregistrement**, **Fieldelement**, ou **attribut de champ** nœud telles que les modifications ultérieures apportées à n’importe quelle instance soient répercutées dans toutes les instances.</span><span class="sxs-lookup"><span data-stu-id="2efa9-103">You can create new instances of an existing **Record**, **Field Element**, or **Field Attribute** node such that subsequent modifications to any instance are reflected in all instances.</span></span>  
  
### <a name="to-create-a-new-instance-of-an-existing-record-field-element-or-field-attribute-node"></a><span data-ttu-id="2efa9-104">Pour créer une instance d’un nœud Enregistrement, Élément de champ ou Attribut de champ existant</span><span class="sxs-lookup"><span data-stu-id="2efa9-104">To create a new instance of an existing Record, Field Element, or Field Attribute node</span></span>  
  
1.  <span data-ttu-id="2efa9-105">Sélectionnez la version d’origine **enregistrement**, **élément de champ**, ou **attribut de champ** nœud, vérifiez que son **Base Data Type** propriété est définie correctement, puis, dans son **Data Structure Type** (**enregistrement** nœuds) ou son **Type de données** (**élément de champ** et  **Attribut de champ** nœuds) propriété, tapez un nom de type de données personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2efa9-105">Select the original **Record**, **Field Element**, or **Field Attribute** node, make sure its **Base Data Type** property is set correctly, and then in its **Data Structure Type** (**Record** nodes) or its **Data Type** (**Field Element** and **Field Attribute** nodes) property, type a custom data type name.</span></span>  
  
2.  <span data-ttu-id="2efa9-106">Insérer le nouvel **enregistrement**, **Fieldelement**, ou **attribut de champ** nom que vous avez tapé à l’étape 1 de type de nœud et définissez une des propriétés suivantes pour les données personnalisées.</span><span class="sxs-lookup"><span data-stu-id="2efa9-106">Insert the new **Record**, **Field Element**, or **Field Attribute** node and set one of the following properties to the custom data type name you typed in step 1.</span></span>  
  
    -   <span data-ttu-id="2efa9-107">Type de Structure de données (**enregistrement** nœuds)</span><span class="sxs-lookup"><span data-stu-id="2efa9-107">Data Structure Type (**Record** nodes)</span></span>  
  
    -   <span data-ttu-id="2efa9-108">Type de données (**Fieldelement** et **attribut de champ** nœuds)</span><span class="sxs-lookup"><span data-stu-id="2efa9-108">Data Type (**Field Element** and **Field Attribute** nodes)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2efa9-109">Si un nouveau **enregistrement** ou **élément de champ** le nœud est un frère du nœud d’origine et vous donnez au nouveau nœud le même nom que le nœud d’origine, vous verrez un message demandant dupliquer les nœuds dans la même étendue avec le même nom.</span><span class="sxs-lookup"><span data-stu-id="2efa9-109">If a new **Record** or **Field Element** node is a sibling of the original node, and you give the new node the same name as the original node, you will see a message box asking about duplicate nodes in the same scope with the same name.</span></span> <span data-ttu-id="2efa9-110">En cliquant sur **Oui** exécute la même action que le choix le nom de type de données personnalisé à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="2efa9-110">Clicking **Yes** performs the same action as choosing the custom data type name in step 2.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2efa9-111">Vous avez créé une nouvelle instance d’existants **enregistrement**, **Fieldelement**, ou **attribut de champ** nœud.</span><span class="sxs-lookup"><span data-stu-id="2efa9-111">You have created a new instance of the existing **Record**, **Field Element**, or **Field Attribute** node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2efa9-112">Certaines propriétés de **enregistrement**, **Fieldelement**, ou **attribut de champ** instances de nœud restent identiques (une modification apportée à une seule instance est une modification à toutes les instances) et d’autres propriétés peuvent être définies indépendamment pour chaque instance.</span><span class="sxs-lookup"><span data-stu-id="2efa9-112">Some properties of **Record**, **Field Element**, or **Field Attribute** node instances remain identical (a change to one instance is a change to all instances), and other properties can be set independently for each instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2efa9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2efa9-113">See Also</span></span>  
 [<span data-ttu-id="2efa9-114">Insertion de nœuds dans un schéma</span><span class="sxs-lookup"><span data-stu-id="2efa9-114">Inserting Nodes into a Schema</span></span>](../core/inserting-nodes-into-a-schema.md)