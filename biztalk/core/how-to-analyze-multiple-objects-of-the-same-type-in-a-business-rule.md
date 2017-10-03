---
title: "Comment analyser plusieurs objets du même Type dans une règle d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, multiple types
- Business Rules Framework, programming
ms.assetid: ff9790c1-13b0-4eee-8cac-d4f25ef5f0b7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a1e4d2fb01513b1d4d314264ab74b84d3a0223a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-analyze-multiple-objects-of-the-same-type-in-a-business-rule"></a><span data-ttu-id="31ad1-102">Comment analyser plusieurs objets du même Type dans une règle d’entreprise</span><span class="sxs-lookup"><span data-stu-id="31ad1-102">How to Analyze Multiple Objects of the Same Type in a Business Rule</span></span>
<span data-ttu-id="31ad1-103">Dans plusieurs scénarios, vous rédigerez une règle d'entreprise en fonction d'un type et chaque instance de ce type déclarée dans le moteur devra être analysée et traitée séparément par la règle.</span><span class="sxs-lookup"><span data-stu-id="31ad1-103">In many scenarios, you will write a business rule against a type and expect each instance of the type that is asserted into the engine to be separately analyzed and acted upon by the rule.</span></span> <span data-ttu-id="31ad1-104">Dans certains scénarios, cependant, vous souhaiterez analyser simultanément plusieurs instances d'un certain type dans une règle.</span><span class="sxs-lookup"><span data-stu-id="31ad1-104">In some scenarios, however, you will want to analyze multiple instances of a given type simultaneously in a rule.</span></span>  
  
 <span data-ttu-id="31ad1-105">Prenons par exemple une règle qui utilise des instances de la **FamilyMember** classe.</span><span class="sxs-lookup"><span data-stu-id="31ad1-105">Take for example a rule that uses instances of the **FamilyMember** class.</span></span>  
  
```  
IF FamilyMember.Role == Father  
AND FamilyMember.Role == Son  
AND FamilyMember.Surname == FamilyMember.Surname  
THEN FamilyMember.AddChild(FamilyMember)  
```  
  
 <span data-ttu-id="31ad1-106">La règle identifie un **FamilyMember** instance qui est un **père** et une autre instance est un **fils**.</span><span class="sxs-lookup"><span data-stu-id="31ad1-106">The rule identifies a **FamilyMember** instance that is a **Father** and another instance that is a **Son**.</span></span> <span data-ttu-id="31ad1-107">Si les instances sont liées par le nom de famille, le **fils** instance est ajoutée à une collection d’enfants sur l’instance père.</span><span class="sxs-lookup"><span data-stu-id="31ad1-107">If the instances are related by surname, the **Son** instance is added to a collection of children on the Father instance.</span></span> <span data-ttu-id="31ad1-108">Si chaque **FamilyMember** instance est analysée séparément dans la règle, la règle serait déclenchée jamais, car dans ce scénario, le **FamilyMember** a uniquement un seul rôle,**père** ou **fils**.</span><span class="sxs-lookup"><span data-stu-id="31ad1-108">If each **FamilyMember** instance were analyzed separately in the rule, the rule would never fire, because in this scenario, the **FamilyMember** only has one role—**Father** or **Son**.</span></span>  
  
 <span data-ttu-id="31ad1-109">De ce fait, vous devez indiquer au moteur que plusieurs instances doivent être analysées ensemble dans une règle. En outre, vous devez définir un moyen de différencier l'identité de chaque instance dans la règle.</span><span class="sxs-lookup"><span data-stu-id="31ad1-109">Therefore, you must indicate to the engine that multiple instances should be analyzed together in the rule, and you need a way to differentiate the identity of each instance in the rule.</span></span> <span data-ttu-id="31ad1-110">Le **ID d’Instance** propriété est utilisée pour fournir cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="31ad1-110">The **Instance ID** property is used to provide this functionality.</span></span> <span data-ttu-id="31ad1-111">Ce champ est disponible dans la fenêtre Propriétés lors de la sélection d'un fait dans l'Explorateur de faits.</span><span class="sxs-lookup"><span data-stu-id="31ad1-111">This field is available in the Properties window when a fact is selected in Facts Explorer.</span></span> <span data-ttu-id="31ad1-112">Vous devez modifier la valeur du champ avant de déplacer un fait ou un membre dans une règle.</span><span class="sxs-lookup"><span data-stu-id="31ad1-112">You should change the value of the field prior to dragging a fact or member into a rule.</span></span>  
  
 <span data-ttu-id="31ad1-113">À l’aide de la **ID d’Instance** propriété, la règle est reconstruite.</span><span class="sxs-lookup"><span data-stu-id="31ad1-113">Using the **Instance ID** property, the rule would be rebuilt.</span></span> <span data-ttu-id="31ad1-114">Pour les arguments de règle qui utilisent la **fils** instance de **FamilyMember**, le **ID d’Instance** champ est modifié à partir de la valeur par défaut de 0 à 1.</span><span class="sxs-lookup"><span data-stu-id="31ad1-114">For those rule arguments that use the **Son** instance of **FamilyMember**, the **Instance ID** field is changed from the default of 0 to 1.</span></span> <span data-ttu-id="31ad1-115">Lorsque l’ID d’Instance est passée de 0, et le fait ou le membre est déplacé dans l’éditeur de règles, la valeur de l’ID d’Instance s’afficheront dans la règle après la classe.</span><span class="sxs-lookup"><span data-stu-id="31ad1-115">When the Instance ID is changed from 0 and the fact or member is dragged into the rule editor, the value of Instance ID will show up in the rule after the class.</span></span>  
  
```  
IF FamilyMember.Role == Father  
AND FamilyMember(1).Role== Son  
AND FamilyMember.Surname == FamilyMember(1).Surname  
THEN FamilyMember.AddChild(FamilyMember(1))  
```  
  
 <span data-ttu-id="31ad1-116">Maintenant, supposons qu’un **père** instance et un **fils** instance sont déclarées dans le moteur.</span><span class="sxs-lookup"><span data-stu-id="31ad1-116">Now, assume that a **Father** instance and a **Son** instance are asserted into the engine.</span></span> <span data-ttu-id="31ad1-117">Le moteur évalue la règle par rapport aux diverses combinaisons d'instances.</span><span class="sxs-lookup"><span data-stu-id="31ad1-117">The engine will evaluate the rule against the various combinations of the instances.</span></span> <span data-ttu-id="31ad1-118">En supposant que le **père** et **fils** instance ont le même nom, le **fils** instance sera ajoutée à la **père** instance en tant que prévu.</span><span class="sxs-lookup"><span data-stu-id="31ad1-118">Assuming that the **Father** and **Son** instance have the same surname, the **Son** instance will be added to the **Father** instance as intended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31ad1-119">Le **ID d’Instance** est utilisée uniquement dans le contexte d’une version d’évaluation de règles donné.</span><span class="sxs-lookup"><span data-stu-id="31ad1-119">The **Instance ID** is only used within the context of a given rule evaluation.</span></span> <span data-ttu-id="31ad1-120">Elle n'est pas ajoutée à une instance d'objet au cours de l'exécution de la stratégie et elle n'a pas de lien avec l'ordre dans lequel les objets sont déclarés.</span><span class="sxs-lookup"><span data-stu-id="31ad1-120">It is not affixed to an object instance across the policy execution and is not related to the order in which objects are asserted.</span></span> <span data-ttu-id="31ad1-121">Chaque instance d'objet est évaluée dans tous les arguments de règle associés à ce type.</span><span class="sxs-lookup"><span data-stu-id="31ad1-121">Each object instance will be evaluated in all rule arguments for that type.</span></span>