---
title: "Le développement d’Orchestrations interdépendantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5464096e-66d8-48de-bc02-c754c5cfbada
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93f8d086a60487e144b02c01a393eb6f10a63b40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-develop-interdependent-orchestrations"></a><span data-ttu-id="55bd0-102">Développement d'orchestrations interdépendantes</span><span class="sxs-lookup"><span data-stu-id="55bd0-102">How to Develop Interdependent Orchestrations</span></span>
<span data-ttu-id="55bd0-103">Vous pouvez vous servir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour développer un ensemble d'orchestrations dotées de services Web interdépendants.</span><span class="sxs-lookup"><span data-stu-id="55bd0-103">You can use [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to develop a set of orchestrations that have interdependent Web services.</span></span> <span data-ttu-id="55bd0-104">Cette situation peut survenir lorsque vos orchestrations font référence à des types de données et/ou des ports dans l'orchestration depuis laquelle ils ont été appelés.</span><span class="sxs-lookup"><span data-stu-id="55bd0-104">This scenario arises when you have orchestrations that reference data types and/or ports in the orchestration from which they were called.</span></span> <span data-ttu-id="55bd0-105">Ce type de scénario se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="55bd0-105">An example of this type of scenario is characterized by the following:</span></span>  
  
-   <span data-ttu-id="55bd0-106">Vous possédez au moins deux orchestrations.</span><span class="sxs-lookup"><span data-stu-id="55bd0-106">You have two or more orchestrations.</span></span>  
  
-   <span data-ttu-id="55bd0-107">La première orchestration (Orch1) appelle la seconde orchestration (Orch2) via un appel de service Web unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="55bd0-107">The first orchestration (Orch1) calls the second orchestration (Orch2) with a one-way Web service call.</span></span>  
  
-   <span data-ttu-id="55bd0-108">Orch2 répond à Orch1 via un appel de service Web.</span><span class="sxs-lookup"><span data-stu-id="55bd0-108">Orch2 responds back to Orch1 with a Web service call.</span></span>  
  
 <span data-ttu-id="55bd0-109">Pour un exemple de ce type de projet, consultez [didacticiel 2 : processus de bon de commande](http://msdn.microsoft.com/library/a324ef1b-39b3-49ab-9719-a13f526cb467).</span><span class="sxs-lookup"><span data-stu-id="55bd0-109">For one example of this type of project, see [Tutorial 2: Purchase Order Process](http://msdn.microsoft.com/library/a324ef1b-39b3-49ab-9719-a13f526cb467).</span></span>  
  
### <a name="to-develop-two-interdependent-orchestrations-orch1-and-orch2"></a><span data-ttu-id="55bd0-110">Pour développer deux orchestrations interdépendantes Orch1 et Orch2</span><span class="sxs-lookup"><span data-stu-id="55bd0-110">To develop two interdependent orchestrations Orch1 and Orch2</span></span>  
  
1.  <span data-ttu-id="55bd0-111">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez une version partielle de l'orchestration Orch1 avec un port de réception qui sera affiché en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="55bd0-111">Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a partial version of the Orch1 that has a receive port which will be exposed as a Web service.</span></span>  
  
2.  <span data-ttu-id="55bd0-112">Compilez Orch1.</span><span class="sxs-lookup"><span data-stu-id="55bd0-112">Compile Orch1.</span></span>  
  
3.  <span data-ttu-id="55bd0-113">Exécutez l'Assistant Publication de services Web et publiez le port.</span><span class="sxs-lookup"><span data-stu-id="55bd0-113">Run the Web Services Publishing Wizard and publish the port.</span></span>  
  
4.  <span data-ttu-id="55bd0-114">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez et terminez intégralement Orch2, en utilisant le service Web d'Orch1.</span><span class="sxs-lookup"><span data-stu-id="55bd0-114">Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create and complete all of Orch2, consuming Orch1's web service.</span></span>  
  
5.  <span data-ttu-id="55bd0-115">Compilez Orch2.</span><span class="sxs-lookup"><span data-stu-id="55bd0-115">Compile Orch2.</span></span>  
  
6.  <span data-ttu-id="55bd0-116">Exécutez l'Assistant Publication de services Web et publiez le ou les ports.</span><span class="sxs-lookup"><span data-stu-id="55bd0-116">Run the Web Services Publishing Wizard and publish the port(s).</span></span>  
  
7.  <span data-ttu-id="55bd0-117">Terminez Orch1, en utilisant le(s) service(s) Web d'Orch2, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="55bd0-117">Complete Orch1, consuming Orch2's web service(s) as needed.</span></span>  
  
8.  <span data-ttu-id="55bd0-118">Recompilez Orch1.</span><span class="sxs-lookup"><span data-stu-id="55bd0-118">Recompile Orch1.</span></span>  
  
9. <span data-ttu-id="55bd0-119">Déployez Orch1 et Orch2.</span><span class="sxs-lookup"><span data-stu-id="55bd0-119">Deploy Orch1 and Orch2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55bd0-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55bd0-120">See Also</span></span>  
 [<span data-ttu-id="55bd0-121">Comment utiliser l’Assistant Publication de Services Web BizTalk pour publier une Orchestration en tant que Service Web</span><span class="sxs-lookup"><span data-stu-id="55bd0-121">How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service</span></span>](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)