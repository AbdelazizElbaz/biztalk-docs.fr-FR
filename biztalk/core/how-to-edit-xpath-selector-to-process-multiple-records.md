---
title: "Comment modifier le sélecteur XPath pour traiter plusieurs enregistrements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, editing multiple records
- Business Rules Framework, code samples
- Business Rules Framework, programming
ms.assetid: ef7e1f8d-2e29-4cef-b558-0090648bffc0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34c9b45e3fce9f4ad5730d7f03d2a568b3701742
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-edit-xpath-selector-to-process-multiple-records"></a><span data-ttu-id="fabcb-102">Modification du sélecteur XPath pour traiter plusieurs enregistrements</span><span class="sxs-lookup"><span data-stu-id="fabcb-102">How to Edit XPath Selector to Process Multiple Records</span></span>
<span data-ttu-id="fabcb-103">Enfant distincte TypedXmlDocuments sont créés lorsqu’un TypedXmlDocument est déclaré dans le moteur ; consultez [Assert](../core/assert.md).</span><span class="sxs-lookup"><span data-stu-id="fabcb-103">Separate child TypedXmlDocuments are created when a TypedXmlDocument is asserted into the engine; see [Assert](../core/assert.md).</span></span> <span data-ttu-id="fabcb-104">Le moteur détermine quels TypedXmlDocuments enfants créer en fonction des sélecteurs XPath définis dans les règles.</span><span class="sxs-lookup"><span data-stu-id="fabcb-104">The engine determines which child TypedXmlDocuments to create based on the XPath selectors defined in the rules.</span></span> <span data-ttu-id="fabcb-105">Lorsque vous créez des règles dans l’Éditeur de règles d’entreprise, la valeur du sélecteur XPath est définie par défaut sur le nœud situé au-dessus du nœud sélectionné dans l’onglet Schémas XML de l’Explorateur de faits.</span><span class="sxs-lookup"><span data-stu-id="fabcb-105">When you build rules in the Composer, the XPath Selector value defaults to the node above the node selected in the XML Schemas tab in the Facts Explorer.</span></span> <span data-ttu-id="fabcb-106">La valeur par défaut du champ XPath est définie sur le nœud sélectionné, par rapport à son nœud parent.</span><span class="sxs-lookup"><span data-stu-id="fabcb-106">The XPath Field value defaults to the selected node itself, relative to its parent node.</span></span>  
  
 <span data-ttu-id="fabcb-107">Vous pouvez, dans certains cas, souhaiter personnaliser la valeur XPath par défaut créée par l’Éditeur de règles d’entreprise lors de la création de règles.</span><span class="sxs-lookup"><span data-stu-id="fabcb-107">In some situations you may want to customize the default XPath that the Composer creates when building rules.</span></span> <span data-ttu-id="fabcb-108">Envisageons l’exemple de document XML suivant.</span><span class="sxs-lookup"><span data-stu-id="fabcb-108">Assume the following sample XML document.</span></span>  
  
```  
<Order>  
   <Orderline>  
      <Hat style="Baseball">                        
         <Cost>10</Cost>  
      </Hat>  
      <Shirt color="Black">  
         <Cost>20</Cost>  
      </Shirt>  
      <Total></Total>  
   </Orderline>  
   <Orderline>  
      <Hat style="Bowler">                        
         <Cost>20</Cost>  
      </Hat>  
      <Shirt color="Red">  
         <Cost>20</Cost>  
      </Shirt>  
      <Total></Total>  
   </Orderline>  
</Order>  
```  
  
 <span data-ttu-id="fabcb-109">Supposons que vous vouliez créer une règle qui calcule la valeur Total de chaque Orderline.</span><span class="sxs-lookup"><span data-stu-id="fabcb-109">Assume that you want to build a rule that calculates the Total value for each Orderline.</span></span> <span data-ttu-id="fabcb-110">Votre règle se présenterait alors comme suit :</span><span class="sxs-lookup"><span data-stu-id="fabcb-110">Your rule would look like the following.</span></span>  
  
 <span data-ttu-id="fabcb-111">IF 1==1</span><span class="sxs-lookup"><span data-stu-id="fabcb-111">IF 1==1</span></span>  
  
 <span data-ttu-id="fabcb-112">PUIS **/Order/Orderline/**Total = (**/Order/Orderline/Hat/**coût + **/Order/Orderline/Shirt/**coût)</span><span class="sxs-lookup"><span data-stu-id="fabcb-112">THEN **/Order/Orderline/**Total = (**/Order/Orderline/Hat/**Cost + **/Order/Orderline/Shirt/**Cost)</span></span>  
  
 <span data-ttu-id="fabcb-113">La partie en gras des XPath indique la partie Sélecteur et le reste représente le XPath du champ.</span><span class="sxs-lookup"><span data-stu-id="fabcb-113">The bold portion of the XPaths indicate the Selector portion and the remainder represents the Field XPath.</span></span> <span data-ttu-id="fabcb-114">Il s’agit des valeurs par défaut créées par l'Éditeur.</span><span class="sxs-lookup"><span data-stu-id="fabcb-114">These are the defaults built by the Composer.</span></span> <span data-ttu-id="fabcb-115">L’exécution de cette stratégie aboutirait toutefois à la création de 6 objets : 2 objets Orderline, 2 objets Hat et 2 objets Shirt.</span><span class="sxs-lookup"><span data-stu-id="fabcb-115">Running this policy, however, would result in the creation of 6 objects—2 Orderline objects, 2 Hat objects, and 2 Shirt objects.</span></span> <span data-ttu-id="fabcb-116">Les totaux de Orderline seraient calculés pour chaque combinaison d'objets Hat et Shirt et ils auraient toujours la même valeur, qui serait le résultat de la dernière exécution de la règle.</span><span class="sxs-lookup"><span data-stu-id="fabcb-116">The Orderline totals would be calculated for each combination of Hat and Shirt objects and the totals would always be set to the same value, which resulted from the last execution of the rule.</span></span> <span data-ttu-id="fabcb-117">La règle serait déclenchée 8 fois.</span><span class="sxs-lookup"><span data-stu-id="fabcb-117">The rule would fire 8 times.</span></span> <span data-ttu-id="fabcb-118">Ce n’est pas ce qui est prévu dans ce scénario.</span><span class="sxs-lookup"><span data-stu-id="fabcb-118">This is not what is intended in this scenario.</span></span>  
  
 <span data-ttu-id="fabcb-119">Une solution consisterait à modifier les valeurs XPath de la manière suivante.</span><span class="sxs-lookup"><span data-stu-id="fabcb-119">One solution would be to edit the XPath values to be as follows.</span></span>  
  
 <span data-ttu-id="fabcb-120">IF 1==1</span><span class="sxs-lookup"><span data-stu-id="fabcb-120">IF 1==1</span></span>  
  
 <span data-ttu-id="fabcb-121">PUIS **/Order/Orderline/**Total = (**/Order/Orderline/**Hat/coût + **/Order/Orderline/**Shirt/coût)</span><span class="sxs-lookup"><span data-stu-id="fabcb-121">THEN **/Order/Orderline/**Total = (**/Order/Orderline/**Hat/Cost + **/Order/Orderline/**Shirt/Cost)</span></span>  
  
 <span data-ttu-id="fabcb-122">Les valeurs du Sélecteur XPath des trois champs ont été définies sur la même valeur /Order/Orderline et les valeurs XPath du champ ont été modifiées en conséquence.</span><span class="sxs-lookup"><span data-stu-id="fabcb-122">The Selector XPath values for all three fields have been set to the same /Order/Orderline value and the Field XPath values have been edited accordingly.</span></span> <span data-ttu-id="fabcb-123">Cela est possible en modifiant les valeurs Sélecteur XPath et Champ XPath dans la fenêtre Propriétés lorsqu'un nœud est sélectionné sous l'onglet Schémas XML. Il convient de procéder à cette modification avant de déplacer le champ dans un argument de règle.</span><span class="sxs-lookup"><span data-stu-id="fabcb-123">This is done by changing the XPath Selector and XPath Field values in the Properties window when a node is selected in the XML Schemas tab. This should be done prior to dragging the field into a rule argument.</span></span>  
  
 <span data-ttu-id="fabcb-124">L’exécution de la stratégie avec cette modification aboutirait au calcul correct de la valeur Total pour chaque Orderline en fonction des valeurs Cost des nœuds Hat et Shirt appartenant à cet Orderline.</span><span class="sxs-lookup"><span data-stu-id="fabcb-124">Executing the policy with this change would result in the Total value being correctly calculated for each Orderline based on the Cost values of the Shirt and Hat nodes within that Orderline.</span></span>