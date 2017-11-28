---
title: "Didacticiel 2 : Utiliser l’adaptateur d’écho à partir de .NET | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e489c79-51b4-4067-9584-67c67f86aedd
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5291fc9e465476ea804cd8c46b1b53ea6c02d842
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-2-consume-the-echo-adapter-from-net"></a><span data-ttu-id="a48bd-102">Didacticiel 2 : Utiliser l’adaptateur d’écho à partir de .NET</span><span class="sxs-lookup"><span data-stu-id="a48bd-102">Tutorial 2: Consume the Echo Adapter from .NET</span></span>
<span data-ttu-id="a48bd-103">Cette section fournit les étapes pour consommer les opérations entrantes et sortantes exposées par l’adaptateur d’écho à partir de .NET.</span><span class="sxs-lookup"><span data-stu-id="a48bd-103">This section gives the steps for consuming the inbound and outbound operations exposed by the Echo adapter from .NET.</span></span> <span data-ttu-id="a48bd-104">L’adaptateur Echo a été développé dans [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="a48bd-104">The Echo adapter was developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a48bd-105">Le code d’adaptateur d’écho et de test est inclus dans les fichiers d’installation de BizTalk à `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` ou `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.</span><span class="sxs-lookup"><span data-stu-id="a48bd-105">The Echo Adapter and test code is included with your BizTalk installation files at `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` or `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="a48bd-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a48bd-106">In This Section</span></span>  
  
-   [<span data-ttu-id="a48bd-107">Étape 1 : Tester le gestionnaire sortant de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="a48bd-107">Step 1: Test Outbound Handler of the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-test-outbound-handler-of-the-echo-adapter.md)  
  
-   [<span data-ttu-id="a48bd-108">Étape 2 : Tester le Gestionnaire d’entrée de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="a48bd-108">Step 2: Test Inbound Handler of the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="a48bd-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a48bd-109">See Also</span></span>  
 <span data-ttu-id="a48bd-110">[Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="a48bd-110">[Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="a48bd-111">Didacticiels de kit de développement logiciel l’adaptateur WCF LOB</span><span class="sxs-lookup"><span data-stu-id="a48bd-111">WCF LOB Adapter SDK Tutorials</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)