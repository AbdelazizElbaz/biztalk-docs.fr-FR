---
title: "Développement d’un composant de Pipeline général | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63f5d8d1-30fb-4a1e-b4bd-2be07b618b20
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44b85992eb0691b7f27ec1a52812d986429d9e31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-general-pipeline-component"></a><span data-ttu-id="5ead8-102">Développement d’un composant de Pipeline général</span><span class="sxs-lookup"><span data-stu-id="5ead8-102">Developing a General Pipeline Component</span></span>

## <a name="interfaces"></a><span data-ttu-id="5ead8-103">Interfaces</span><span class="sxs-lookup"><span data-stu-id="5ead8-103">Interfaces</span></span>
<span data-ttu-id="5ead8-104">Un composant de pipeline général est un composant .NET ou COM qui implémente les interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ead8-104">A general pipeline component is a .NET or COM component that implements the following interfaces:</span></span>  
  
-   <span data-ttu-id="5ead8-105">Interface IBaseComponent (COM)[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="5ead8-105">IBaseComponent Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   <span data-ttu-id="5ead8-106">Interface IComponent (COM)[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="5ead8-106">IComponent Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   <span data-ttu-id="5ead8-107">Interface IComponentUI (COM)[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="5ead8-107">IComponentUI Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   [<span data-ttu-id="5ead8-108">IPersistPropertyBag</span><span class="sxs-lookup"><span data-stu-id="5ead8-108">IPersistPropertyBag</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.ipersistpropertybag)
  
 <span data-ttu-id="5ead8-109">Un composant de pipeline général reçoit un message du moteur de messagerie BizTalk, le traite, puis le renvoie au moteur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ead8-109">A general pipeline component gets one message from the BizTalk Messaging Engine, processes it, and returns it to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine.</span></span> <span data-ttu-id="5ead8-110">Les composants généraux peuvent également être configurés de sorte à ne pas renvoyer les messages au serveur.</span><span class="sxs-lookup"><span data-stu-id="5ead8-110">General components can also be implemented so that they do not return messages to the server.</span></span> <span data-ttu-id="5ead8-111">Ces composants sont appelés composants de consommation, car ils se contentent de recevoir les messages sans en renvoyer.</span><span class="sxs-lookup"><span data-stu-id="5ead8-111">Such components are called consuming components because the component receives messages but does not produce any result messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ead8-112">Les composants de pipeline personnalisés doivent copier les parties supplémentaires du message d'entrée vers le ou les messages de sortie.</span><span class="sxs-lookup"><span data-stu-id="5ead8-112">Custom pipeline components should copy any additional parts from the input message to the output message(s).</span></span> <span data-ttu-id="5ead8-113">Ceci les empêche d'effectuer un autre traitement dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="5ead8-113">This preserves them for further processing in the pipeline.</span></span>  
  
## <a name="more-pipeline-resources"></a><span data-ttu-id="5ead8-114">Plus de ressources de pipeline</span><span class="sxs-lookup"><span data-stu-id="5ead8-114">More pipeline resources</span></span>
 <span data-ttu-id="5ead8-115">[Développement d’un composant de Pipeline d’assemblage](../core/developing-an-assembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="5ead8-115">[Developing an Assembling Pipeline Component](../core/developing-an-assembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="5ead8-116">[Développement d’un composant de Pipeline de désassemblage](../core/developing-a-disassembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="5ead8-116">[Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="5ead8-117">[Développement d’un composant de Pipeline de sonde](../core/developing-a-probing-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="5ead8-117">[Developing a Probing Pipeline Component](../core/developing-a-probing-pipeline-component.md) </span></span>  
 <span data-ttu-id="5ead8-118">[Rapports d’erreurs à partir des composants de Pipeline](../core/reporting-errors-from-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="5ead8-118">[Reporting Errors from Pipeline Components](../core/reporting-errors-from-pipeline-components.md) </span></span>  
 <span data-ttu-id="5ead8-119">[Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="5ead8-119">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 <span data-ttu-id="5ead8-120">[Déploiement des composants de Pipeline](../core/deploying-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="5ead8-120">[Deploying Pipeline Components](../core/deploying-pipeline-components.md) </span></span>  
 [<span data-ttu-id="5ead8-121">CustomComponent (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="5ead8-121">CustomComponent (BizTalk Server Sample)</span></span>](../core/customcomponent-biztalk-server-sample.md)