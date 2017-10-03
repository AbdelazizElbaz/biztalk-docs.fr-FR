---
title: "Définition des Expressions de filtre sur les Ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, context properties
- filtering, send ports
- send ports, filtering
- context properties, send ports
- context properties, filtering
- filtering, context properties
ms.assetid: 48c7c83b-9464-4ed9-bd8d-cf5b75e16702
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b94497f4e1412f81c36df3195994aafa32ecc451
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-filter-expressions-on-send-ports"></a><span data-ttu-id="41124-102">Définition d’Expressions de filtre sur les Ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="41124-102">Setting Filter Expressions on Send Ports</span></span>
<span data-ttu-id="41124-103">Vous définissez des propriétés de contexte dans les expressions de filtre sur le port d’envoi pour contrôler ce que le port envoie.</span><span class="sxs-lookup"><span data-stu-id="41124-103">You set context properties in filter expressions on the send port to control what the port sends.</span></span> <span data-ttu-id="41124-104">Vous pouvez définir les expressions de filtre avec un nombre d’opérateurs qui vous offrent une grande souplesse dans la façon dont vous filtrez de la propriété (égalité ou inégalité, existe, supérieur à, supérieur ou égal à, inférieur à et inférieur ou égal à).</span><span class="sxs-lookup"><span data-stu-id="41124-104">You can set the filter expressions with a number of operators that offer you flexibility in how you filter the property (equality or inequality, exists, greater than, great than or equal to, less than, and less than or equal to).</span></span>  
  
### <a name="to-set-the-filter-expression-on-a-send-port"></a><span data-ttu-id="41124-105">Pour définir l’expression de filtre sur un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="41124-105">To set the filter expression on a send port</span></span>  
  
1.  <span data-ttu-id="41124-106">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, et **Application BizTalk 1** (ou une autre application).</span><span class="sxs-lookup"><span data-stu-id="41124-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1** (or another application).</span></span> <span data-ttu-id="41124-107">Cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="41124-107">Click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="41124-108">Cliquez sur le port d’envoi que vous souhaitez définir pour l’expression de filtre, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="41124-108">Right-click the send port that you want to set the filter expression for, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="41124-109">Dans l’arborescence de la boîte de dialogue Propriétés de Port d’envoi, cliquez sur **filtres**.</span><span class="sxs-lookup"><span data-stu-id="41124-109">In the console tree of the Send Port Properties dialog box, click **Filters**.</span></span>  
  
4.  <span data-ttu-id="41124-110">Cliquez sur la zone de texte dans le **propriété** colonne, puis sélectionnez la propriété de contexte à partir de la **propriété** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="41124-110">Click the text box in the **Property** column, and then select the context property from the **Property** drop-down list.</span></span>  
  
5.  <span data-ttu-id="41124-111">Cliquez sur le **opérateur** dans la ligne de la propriété et sélectionnez l’opérateur pour la propriété dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="41124-111">Click the **Operator** box in the row for the property, and select the operator for the property from the drop-down list.</span></span>  
  
6.  <span data-ttu-id="41124-112">Cliquez sur le **valeur** dans la ligne de la propriété, puis tapez une expression de valeur.</span><span class="sxs-lookup"><span data-stu-id="41124-112">Click the **Value** box in the row for the property, and type a value expression.</span></span>  
  
7.  <span data-ttu-id="41124-113">Si vous devez ajouter une autre clause de l’expression de filtre, cliquez sur le **Group By** dans la ligne de la propriété et sélectionnez **et** ou **ou** pour déterminer la relation entre le clauses.</span><span class="sxs-lookup"><span data-stu-id="41124-113">If you need to add another  clause for the filter expression, click the **Group By** box in the row for the property, and select **And** or **Or** to determine the relationship of the clauses.</span></span>  
  
8.  <span data-ttu-id="41124-114">Répétez les étapes 4 à 6 pour ajouter une autre clause de filtre.</span><span class="sxs-lookup"><span data-stu-id="41124-114">Repeat steps 4 through 6 to add another filter clause.</span></span>  
  
9. <span data-ttu-id="41124-115">Vérifiez que l’expression de filtre est correcte dans le volet du bas de la **filtres** volet.</span><span class="sxs-lookup"><span data-stu-id="41124-115">Verify that the filter expression is correct in the pane at the bottom of the **Filters** pane.</span></span>  
  
10. <span data-ttu-id="41124-116">Lorsque vous avez ajouté toutes les clauses de filtre, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="41124-116">When you have added all filter clauses, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41124-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41124-117">See Also</span></span>  
 <span data-ttu-id="41124-118">[Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="41124-118">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 [<span data-ttu-id="41124-119">À l’aide des propriétés de contexte</span><span class="sxs-lookup"><span data-stu-id="41124-119">Using Context Properties</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-context-properties.md)