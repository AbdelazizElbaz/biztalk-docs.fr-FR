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
ms.openlocfilehash: 9d7ea539b778cc382991e82841dec45db5316f18
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-add-constant-values"></a><span data-ttu-id="8f1f1-102">Comment ajouter des valeurs de constante</span><span class="sxs-lookup"><span data-stu-id="8f1f1-102">How to Add Constant Values</span></span>
<span data-ttu-id="8f1f1-103">Lors du test des mappages, il vous arrivera de vouloir définir des valeurs constantes.</span><span class="sxs-lookup"><span data-stu-id="8f1f1-103">When testing maps, you will sometimes want to set constant values for use during the test.</span></span>  
  
## <a name="set-constant-values-for-nodes-in-the-source-or-destination-schema-trees"></a><span data-ttu-id="8f1f1-104">Définir des valeurs constantes pour les nœuds dans la source ou la destination des arborescences de schéma</span><span class="sxs-lookup"><span data-stu-id="8f1f1-104">Set constant values for nodes in the source or destination schema trees</span></span>  
  
1.  <span data-ttu-id="8f1f1-105">Sélectionnez un enregistrement ou un champ dans les arborescences de schémas source ou de destination.</span><span class="sxs-lookup"><span data-stu-id="8f1f1-105">Select a record or field in the source or destination schema trees.</span></span>  
  
2.  <span data-ttu-id="8f1f1-106">Dans la fenêtre Propriétés, dans le **général** catégorie, utilisez la **valeur** Entrez une valeur pour l’enregistrement sélectionné ou le champ de propriété.</span><span class="sxs-lookup"><span data-stu-id="8f1f1-106">In the Properties window, in the **General** category, use the **Value** property to enter a value for the selected record or field.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f1f1-107">Vous pouvez associer une valeur uniquement avec un enregistrement avec son **contenu** propriété **texte uniquement** ou **mixte**.</span><span class="sxs-lookup"><span data-stu-id="8f1f1-107">You can only associate a value with a record with its **Content** property set to **Text Only** or **Mixed**.</span></span>  
  
 <span data-ttu-id="8f1f1-108">Pour un nœud dans le schéma source, si vous définissez la **valeur** propriété  **\<vide\>**, le message d’instance généré pour le schéma source contient une valeur vide pour la nœud.</span><span class="sxs-lookup"><span data-stu-id="8f1f1-108">For a node in source schema, if you set the **Value** property to **\<empty\>**, the generated instance message for the source schema contains an empty value for the respective node.</span></span>  
  
 <span data-ttu-id="8f1f1-109">Il arrive que tous les champs du schéma cible ne soient pas utilisés (certains champs du schéma cible ne possèdent pas de liens entrants).</span><span class="sxs-lookup"><span data-stu-id="8f1f1-109">Sometimes, you do not use all the fields in the target schema, i.e. some of the fields in the target schema do not have any incoming links.</span></span> <span data-ttu-id="8f1f1-110">Dans ce cas, l’opération Test Map génère erreur, à condition que la **valider l’entrée TestMap** ou **valider la sortie TestMap** propriétés sont définies sur **True**.</span><span class="sxs-lookup"><span data-stu-id="8f1f1-110">In such cases, the Test Map operation throws error, provided that the **Validate TestMap Input** or **Validate TestMap Output** properties are set to **True**.</span></span> <span data-ttu-id="8f1f1-111">Pour éviter les erreurs de mappage de Test dans ce cas, définissez la **valeur** propriété du nœud à une valeur constante ou  **\<vide\>**.</span><span class="sxs-lookup"><span data-stu-id="8f1f1-111">To avoid Test Map errors in such cases, set the **Value** property of the node to either a constant value or **\<empty\>**.</span></span> <span data-ttu-id="8f1f1-112">Utilisez  **\<vide\>**  si vous ne souhaitez pas définir de données arbitraires pour les champs du schéma cible inutilisées.</span><span class="sxs-lookup"><span data-stu-id="8f1f1-112">Use **\<empty\>** if you do not want to set arbitrary data for unused target schema fields.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f1f1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f1f1-113">See Also</span></span>  
[<span data-ttu-id="8f1f1-114">Valider et tester vos mappages</span><span class="sxs-lookup"><span data-stu-id="8f1f1-114">Validate and test your maps</span></span>](../core/how-to-configure-map-validation-and-test-parameters.md)