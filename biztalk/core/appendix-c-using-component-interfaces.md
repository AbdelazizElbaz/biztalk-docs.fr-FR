---
title: "Annexe c : à l’aide des Interfaces de composant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Enterprise Integration Points
- EIP
- component interfaces
ms.assetid: 2e3bc5ef-24ea-4e09-8e95-31feefaf5536
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c482a01de8f6040f31e6563c97b041dedbe9e88
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-c-using-component-interfaces"></a><span data-ttu-id="bd0d9-102">Annexe c : à l’aide des Interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="bd0d9-102">Appendix C: Using Component Interfaces</span></span>
<span data-ttu-id="bd0d9-103">Les rubriques de cette section décrivent la création des interfaces de composant (et la modification des interfaces de composant existantes) pour les utiliser avec l'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="bd0d9-103">The topics in this section describe how to create new component interfaces—and how to modify existing component interfaces—for use with Microsoft BizTalk Adapter for PeopleSoft Enterprise.</span></span> <span data-ttu-id="bd0d9-104">Elles décrivent également l'application de la sécurité à ces interfaces de composant et leur test.</span><span class="sxs-lookup"><span data-stu-id="bd0d9-104">They also describe how to apply security to those component interfaces and how to test them.</span></span>  
  
 <span data-ttu-id="bd0d9-105">Vous pouvez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="bd0d9-105">You can do the following:</span></span>  
  
-   <span data-ttu-id="bd0d9-106">utiliser les interfaces de composant fournies par PeopleSoft avec votre application ;</span><span class="sxs-lookup"><span data-stu-id="bd0d9-106">Use component interfaces supplied by PeopleSoft with your application.</span></span>  
  
     <span data-ttu-id="bd0d9-107">Les interfaces de composant sont également appelées points d'intégration d'entreprise (EIP, Enterprise Integration Points).</span><span class="sxs-lookup"><span data-stu-id="bd0d9-107">Component interfaces also are known as Enterprise Integration Points (EIP).</span></span>  
  
-   <span data-ttu-id="bd0d9-108">modifier une interface de composant existante ;</span><span class="sxs-lookup"><span data-stu-id="bd0d9-108">Modify an existing component interface.</span></span>  
  
-   <span data-ttu-id="bd0d9-109">créer une interface de composant.</span><span class="sxs-lookup"><span data-stu-id="bd0d9-109">Create a new component interface.</span></span>  
  
 <span data-ttu-id="bd0d9-110">Avant d'utiliser votre interface de composant, vous devez appliquer et tester la sécurité.</span><span class="sxs-lookup"><span data-stu-id="bd0d9-110">Before using your component interface, you must apply and test security.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd0d9-111">Cette section est conçue comme un complément utile. Elle n'est pas destinée à remplacer la documentation PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="bd0d9-111">This section is intended as a helpful supplement; it is not a substitute for PeopleSoft documentation.</span></span> <span data-ttu-id="bd0d9-112">Pour obtenir des informations complètes et actualisées sur les interfaces de composant PeopleSoft, consultez la bibliothèque en ligne PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="bd0d9-112">For complete and up-to-date information about PeopleSoft component interfaces, see the PeopleSoft Online Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd0d9-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bd0d9-113">In This Section</span></span>  
  
-   [<span data-ttu-id="bd0d9-114">Comment créer des Interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="bd0d9-114">How to Create Component Interfaces</span></span>](../core/how-to-create-component-interfaces.md)  
  
-   [<span data-ttu-id="bd0d9-115">Méthodes standard dans les Interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="bd0d9-115">Standard Methods in Component Interfaces</span></span>](../core/standard-methods-in-component-interfaces.md)  
  
-   [<span data-ttu-id="bd0d9-116">Comment sécuriser les Interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="bd0d9-116">How to Help Secure Component Interfaces</span></span>](../core/how-to-help-secure-component-interfaces.md)  
  
-   [<span data-ttu-id="bd0d9-117">Comment tester des Interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="bd0d9-117">How to Test Component Interfaces</span></span>](../core/how-to-test-component-interfaces.md)