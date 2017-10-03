---
title: "Composant de Pipeline du développement d’une détection | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], probing
- IProbeMessage interface
- pipeline interfaces, IProbeMessage
ms.assetid: c3da467d-5270-4c7f-9c38-ce9989bf1b63
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8081c31fc781cd2d1cbc291587f358376a033d66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-probing-pipeline-component"></a><span data-ttu-id="2375e-102">Développement d’un composant de Pipeline de sonde</span><span class="sxs-lookup"><span data-stu-id="2375e-102">Developing a Probing Pipeline Component</span></span>
<span data-ttu-id="2375e-103">Tout composant de pipeline (général, assemblage ou désassemblage) peut implémenter la `IProbeMessage` interface si elle doit prendre en charge les fonctionnalités de sondage des messages.</span><span class="sxs-lookup"><span data-stu-id="2375e-103">Any pipeline component (general, assembling, or disassembling) can implement the `IProbeMessage` interface if it must support message probing functionality.</span></span> <span data-ttu-id="2375e-104">Un composant de sonde est utilisé dans les étapes du pipeline qui ont **PremièreCorrespondance** mode d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2375e-104">A probing component is used in the pipeline stages that have **FirstMatch** execution mode.</span></span> <span data-ttu-id="2375e-105">Dans ces étapes, le moteur de messagerie BizTalk transmet le début du message au composant afin de déterminer si ce dernier reconnaît le format du message.</span><span class="sxs-lookup"><span data-stu-id="2375e-105">In such stages, the BizTalk Messaging Engine gives the beginning part of the message to the component to determine if the component recognizes the format of the message.</span></span> <span data-ttu-id="2375e-106">Si c'est le cas, la totalité du message est remise au composant pour traitement.</span><span class="sxs-lookup"><span data-stu-id="2375e-106">If the component recognizes the format, the entire message is given to the component for processing.</span></span>  
  
 <span data-ttu-id="2375e-107">Le **IProbeMessage** interface expose une méthode unique, **sonde**, ce qui permet au composant vérifier le début du message.</span><span class="sxs-lookup"><span data-stu-id="2375e-107">The **IProbeMessage** interface exposes a single method, **Probe**, which enables the component to check the beginning part of the message.</span></span> <span data-ttu-id="2375e-108">La valeur de retour détermine si ce composant est exécuté.</span><span class="sxs-lookup"><span data-stu-id="2375e-108">The return value determines whether this component is run.</span></span> <span data-ttu-id="2375e-109">Les étapes suivantes donnent un aperçu de la manière dont le moteur de messagerie BizTalk exécute une étape dans laquelle la reconnaissance est requise :</span><span class="sxs-lookup"><span data-stu-id="2375e-109">The following steps outline how the BizTalk Messaging Engine runs a stage that requires recognition:</span></span>  
  
1.  <span data-ttu-id="2375e-110">Si l'étape ne contient pas de composants, elle n'est pas exécutée et le message est remis aux étapes suivantes pour traitement.</span><span class="sxs-lookup"><span data-stu-id="2375e-110">If the stage does not contain any components, the stage is not run and the message is given to the subsequent stages for processing.</span></span>  
  
2.  <span data-ttu-id="2375e-111">Vérifiez si le composant implémente le **IProbeMessage** interface.</span><span class="sxs-lookup"><span data-stu-id="2375e-111">Check if the component implements the **IProbeMessage** interface.</span></span> <span data-ttu-id="2375e-112">Si ce n'est pas le cas, le moteur de messagerie appelle le composant.</span><span class="sxs-lookup"><span data-stu-id="2375e-112">If not, the Messaging Engine invokes the component.</span></span> <span data-ttu-id="2375e-113">Le traitement de l'étape est effectué et le message est transmis à la prochaine étape.</span><span class="sxs-lookup"><span data-stu-id="2375e-113">The stage processing is done and the message is given to the next stage.</span></span>  
  
3.  <span data-ttu-id="2375e-114">Le **sonde** méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="2375e-114">The **Probe** method is invoked.</span></span> <span data-ttu-id="2375e-115">Si la valeur de retour est **True**, le composant est exécuté.</span><span class="sxs-lookup"><span data-stu-id="2375e-115">If the return value is **True**, the component is run.</span></span> <span data-ttu-id="2375e-116">Ensuite, le traitement de l'étape est effectué et le message est transmis à une prochaine étape.</span><span class="sxs-lookup"><span data-stu-id="2375e-116">Then the stage processing is done and the message is given to a next stage.</span></span>  
  
4.  <span data-ttu-id="2375e-117">Le moteur de messagerie obtient le prochain composant dans l'étape.</span><span class="sxs-lookup"><span data-stu-id="2375e-117">The Messaging Engine gets the next component in the stage.</span></span> <span data-ttu-id="2375e-118">S'il n'y a plus de composants et qu'aucun des composants n'a été exécuté, il génère une erreur indiquant que le traitement du pipeline a échoué.</span><span class="sxs-lookup"><span data-stu-id="2375e-118">If there are no more components and none of the components have been run, it generates an error that pipeline processing has failed.</span></span> <span data-ttu-id="2375e-119">S'il n'y a plus de composants et qu'au moins un des composants a été exécuté, le traitement est effectué.</span><span class="sxs-lookup"><span data-stu-id="2375e-119">If there are no more components and at least one component has been run, the processing is done.</span></span>  
  
 <span data-ttu-id="2375e-120">Si une étape ne requiert pas de reconnaissance (par exemple, le mode d’exécution est **tous les**), le moteur de messagerie appelle le composant sans interroger d’abord pour la **IProbeMessage** interface et en appelant le **Sonde** (méthode).</span><span class="sxs-lookup"><span data-stu-id="2375e-120">If a stage does not require recognition (for example, the execution mode is **All**), the Messaging Engine invokes the component without first querying for the **IProbeMessage** interface and calling the **Probe** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2375e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2375e-121">See Also</span></span>  
 <span data-ttu-id="2375e-122">[Développement d’un composant de Pipeline général](../core/developing-a-general-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="2375e-122">[Developing a General Pipeline Component](../core/developing-a-general-pipeline-component.md) </span></span>  
 <span data-ttu-id="2375e-123">[Développement d’un composant de Pipeline d’assemblage](../core/developing-an-assembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="2375e-123">[Developing an Assembling Pipeline Component](../core/developing-an-assembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="2375e-124">[Développement d’un composant de Pipeline de désassemblage](../core/developing-a-disassembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="2375e-124">[Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="2375e-125">[Rapports d’erreurs à partir des composants de Pipeline](../core/reporting-errors-from-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="2375e-125">[Reporting Errors from Pipeline Components](../core/reporting-errors-from-pipeline-components.md) </span></span>  
 <span data-ttu-id="2375e-126">[Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="2375e-126">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 [<span data-ttu-id="2375e-127">Déploiement des composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="2375e-127">Deploying Pipeline Components</span></span>](../core/deploying-pipeline-components.md)