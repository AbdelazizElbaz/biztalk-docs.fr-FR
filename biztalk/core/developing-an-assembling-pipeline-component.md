---
title: "Développement d’assemblage d’un composant de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IComponentUI interface, assembling
- IBaseComponent interface, assembling
- pipeline interfaces, IBaseComponent
- pipeline components [custom], interfaces
- pipeline interfaces, IComponentUI
- IAssemblerComponent interface, assembling
- pipeline interfaces, IAssemblerComponent
- pipeline components [custom], assembling
ms.assetid: 2f85421d-2010-4a36-82b5-ea8016f8aa99
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8de06a815e1c5a6bf71700ad373ae3f278b3a9a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-an-assembling-pipeline-component"></a><span data-ttu-id="3c57a-102">Développement d’un composant de Pipeline d’assemblage</span><span class="sxs-lookup"><span data-stu-id="3c57a-102">Developing an Assembling Pipeline Component</span></span>
<span data-ttu-id="3c57a-103">Un composant de pipeline d’assemblage est un composant .NET ou COM qui reçoit plusieurs messages en entrée et produit un message en sortie.</span><span class="sxs-lookup"><span data-stu-id="3c57a-103">An assembling pipeline component is a .NET or COM component that receives several messages on input and produces one message on output.</span></span> <span data-ttu-id="3c57a-104">Les composants d’assemblage sont utilisés pour collecter des documents individuels dans le lot d'échange de messages.</span><span class="sxs-lookup"><span data-stu-id="3c57a-104">Assembling components are used to collect individual documents into the message interchange batch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c57a-105">La fonctionnalité d'assemblage n'est pas utilisée, par conséquent BizTalk Server transmet toujours un document à la sortie de composant.</span><span class="sxs-lookup"><span data-stu-id="3c57a-105">Assembly functionality is not used, so BizTalk Server always passes one document to the component input.</span></span>  
  
 <span data-ttu-id="3c57a-106">Un composant d’assemblage doit implémenter les interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="3c57a-106">An assembling component must implement the following interfaces:</span></span>  
  
-   `IBaseComponent`  
  
-   `IAssemblerComponent`
  
-   `IComponentUI`
  
-   <span data-ttu-id="3c57a-107">**IPersistPropertyBag.**</span><span class="sxs-lookup"><span data-stu-id="3c57a-107">**IPersistPropertyBag .**</span></span> <span data-ttu-id="3c57a-108">Pour cette interface, consultez la documentation .NET Framework SDK.</span><span class="sxs-lookup"><span data-stu-id="3c57a-108">Refer to the .NET Framework SDK documentation for this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c57a-109">Les composants de pipeline personnalisés doivent copier les parties supplémentaires du message d'entrée vers le ou les messages de sortie.</span><span class="sxs-lookup"><span data-stu-id="3c57a-109">Custom pipeline components should copy any additional parts from the input message to the output message(s).</span></span> <span data-ttu-id="3c57a-110">Ceci les empêche d'effectuer un autre traitement dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="3c57a-110">This preserves them for further processing in the pipeline.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c57a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c57a-111">See Also</span></span>  
 <span data-ttu-id="3c57a-112">[Développement d’un composant de Pipeline général](../core/developing-a-general-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="3c57a-112">[Developing a General Pipeline Component](../core/developing-a-general-pipeline-component.md) </span></span>  
 <span data-ttu-id="3c57a-113">[Développement d’un composant de Pipeline de désassemblage](../core/developing-a-disassembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="3c57a-113">[Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="3c57a-114">[Développement d’un composant de Pipeline de sonde](../core/developing-a-probing-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="3c57a-114">[Developing a Probing Pipeline Component](../core/developing-a-probing-pipeline-component.md) </span></span>  
 <span data-ttu-id="3c57a-115">[Rapports d’erreurs à partir des composants de Pipeline](../core/reporting-errors-from-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="3c57a-115">[Reporting Errors from Pipeline Components](../core/reporting-errors-from-pipeline-components.md) </span></span>  
 <span data-ttu-id="3c57a-116">[Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="3c57a-116">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 <span data-ttu-id="3c57a-117">[Déploiement des composants de Pipeline](../core/deploying-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="3c57a-117">[Deploying Pipeline Components](../core/deploying-pipeline-components.md) </span></span>  
 [<span data-ttu-id="3c57a-118">CustomComponent (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="3c57a-118">CustomComponent (BizTalk Server Sample)</span></span>](../core/customcomponent-biztalk-server-sample.md)