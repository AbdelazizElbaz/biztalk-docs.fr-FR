---
title: Comment utiliser des Expressions pour transformer dynamiquement des Messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48387d97-9312-4df5-b614-727ea9035bf8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b9d16c38fefb4e2732bd05f7c3489acaa8ca645
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-expressions-to-dynamic-transform-messages"></a><span data-ttu-id="e734a-102">Utilisation d'expressions pour transformer dynamiquement les messages</span><span class="sxs-lookup"><span data-stu-id="e734a-102">How to Use Expressions to Dynamic Transform Messages</span></span>
<span data-ttu-id="e734a-103">Vous pouvez utiliser des expressions pour transformer dynamiquement des messages dans votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="e734a-103">You can use expressions to dynamic transform messages in your orchestration.</span></span> <span data-ttu-id="e734a-104">XLANG expose une méthode qui peut être appelée à partir d’un **assignation du Message** mettre en forme à l’intérieur d’un **construire un Message** forme.</span><span class="sxs-lookup"><span data-stu-id="e734a-104">XLANG exposes a transform method that can be called from within a **Message Assignment** shape inside of a **Construct Message** shape.</span></span> <span data-ttu-id="e734a-105">C’est la même méthode qui est appelée lorsqu’un **transformer** forme est utilisé, mais vous permet de transformer les messages à l’aide de la carte que vous avez désigné dans l’orchestration par programme.</span><span class="sxs-lookup"><span data-stu-id="e734a-105">This is the same method that is called when a **Transform** shape is used, but allows you to programmatically transform the messages using the map you designated within the orchestration.</span></span> <span data-ttu-id="e734a-106">Cela est utile lorsque vous traitez des messages indépendamment de tout type.</span><span class="sxs-lookup"><span data-stu-id="e734a-106">This is useful when you are doing type-agnostic message processing.</span></span> <span data-ttu-id="e734a-107">Par exemple, si votre processus d'entreprise doit choisir un mappage pour transformer des messages entrants en fonction des paramètres fournis par les messages entrants reçus, vous pouvez faire appel à la méthode de transformation de la forme Expression et garantir l'intégrité de votre processus d'entreprise dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="e734a-107">For example, if you have a business process that needs to choose from a series of maps to transform inbound messages based on the parameters provided by the received inbound messages, you can achieve this by using the transform method in the Expression shape while maintaining your overall business process intact.</span></span>  
  
## <a name="transforming-messages"></a><span data-ttu-id="e734a-108">Transformation des messages</span><span class="sxs-lookup"><span data-stu-id="e734a-108">Transforming messages</span></span>  
 <span data-ttu-id="e734a-109">Vous pouvez utiliser l’exemple de code suivant à transformer par programme les messages dans la **assignation du Message** forme :</span><span class="sxs-lookup"><span data-stu-id="e734a-109">You can use the following sample code to programmatically transform the messages in the **Message Assignment** shape:</span></span>  
  
```  
MyMapType = typeof(MyMapName);  
transform(MyOutputMsg) = MyMapType(MyInputMsg);  
```  
  
 <span data-ttu-id="e734a-110">Dans cet exemple, MyMapType est déclaré en tant que variable de type **System.Type** dans l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="e734a-110">In this example, MyMapType is declared as a variable of type **System.Type** in the orchestration.</span></span> <span data-ttu-id="e734a-111">MyMapName est le nom du mappage créé dans votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e734a-111">MyMapName is the name of a map that was already created in your BizTalk project.</span></span> <span data-ttu-id="e734a-112">Pour référencer un mappage figurant dans un assembly BizTalk distinct, vous devrez référencer l'assembly concerné dans votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e734a-112">If you would like to reference a map that is in a separate BizTalk assembly, you will need to reference that assembly in your BizTalk project.</span></span> <span data-ttu-id="e734a-113">MyInputMsg est le message source et MyOutputMsg le message de destination.</span><span class="sxs-lookup"><span data-stu-id="e734a-113">MyInputMsg is the source message and MyOutputMsg is the destination message.</span></span> <span data-ttu-id="e734a-114">Si votre mappage contient plusieurs messages sources, utilisez l'exemple de code suivant pour transformer les messages :</span><span class="sxs-lookup"><span data-stu-id="e734a-114">If your map takes multiple source messages, then you can use the following sample code to transform the messages:</span></span>  
  
```  
MyMapType = typeof(MyMapName);  
transform(MyOutputMsg) = MyMapType(MyInputMsg1, MyInputMsg2);  
```  
  
> [!NOTE]
>  <span data-ttu-id="e734a-115">En cas de messages sources multiples, ces derniers doivent figurer dans l'expression dans l'ordre correspondant au numéro de partie de message indiqué dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="e734a-115">If you have multiple source messages, they must be placed in order in the expression with respect to the input message part number indicated in the map.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e734a-116">Lors de la transformation dynamique de messages dans la forme Expression, il est recommandé d'écrire un cache dans le code utilisateur pour mettre en mémoire cache les mappages compilés, puis de vous en servir dans la forme Expression pour récupérer les mappages avant la transformation des messages.</span><span class="sxs-lookup"><span data-stu-id="e734a-116">When dynamic transforming messages in the Expression shape, we recommend that you write a cache in user code for caching the compiled maps, and then use the cache in the Expression shape to retrieve the maps before performing the message transformation.</span></span> <span data-ttu-id="e734a-117">Sans cette opération, la mémoire CLR (Common Language Runtime) risque d'être saturée.</span><span class="sxs-lookup"><span data-stu-id="e734a-117">If you are not caching the maps, it is possible to see Common Language Runtime (CLR) memory grow significantly.</span></span> <span data-ttu-id="e734a-118">En effet, lors du mappage dynamique, le composant d'exécution .NET Runtime vérifie l'accès du code et place un objet .NET Evidence dans le tas des objets volumineux lors de chaque transformation. Cet objet est conservé jusqu'à la fin de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="e734a-118">Dynamic mapping requires that the .NET Runtime perform code access check which results in a .NET Evidence object being placed in the Large Object Heap for each transformation and this object is not disposed of until the orchestration completes.</span></span> <span data-ttu-id="e734a-119">Lorsque ces transformations sont effectuées en grand nombre simultanément, la mémoire croît de manière conséquente jusqu'à générer une exception « mémoire insuffisante ».</span><span class="sxs-lookup"><span data-stu-id="e734a-119">Therefore, when there are a lot of these types of transforms occurring simultaneously, you may see the memory usage increase substantially which can also lead to the out of memory exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e734a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e734a-120">See Also</span></span>  
 <span data-ttu-id="e734a-121">[Formes d’orchestration](../core/orchestration-shapes.md) </span><span class="sxs-lookup"><span data-stu-id="e734a-121">[Orchestration Shapes](../core/orchestration-shapes.md) </span></span>  
 [<span data-ttu-id="e734a-122">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="e734a-122">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)