---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour JD Edwards EnterpriseOne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1cafbe72-2b90-4d8e-9a1d-5735cefeb3d4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6e35ddc82235c29384da049d131bbb8e96d9967
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-jd-edwards-enterpriseone"></a><span data-ttu-id="ff449-102">Didacticiel : Utilisation de l’adaptateur BizTalk pour JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="ff449-102">Tutorial: Using the BizTalk Adapter for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="ff449-103">L’exemple suivant présente à l’aide des propriétés de contexte BizTalk pour contrôler le J.D.</span><span class="sxs-lookup"><span data-stu-id="ff449-103">The following demonstrates using BizTalk Context Properties to control the J.D.</span></span>  <span data-ttu-id="ff449-104">Session Edwards OneWorld dans votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="ff449-104">Edwards OneWorld session in your orchestration.</span></span> <span data-ttu-id="ff449-105">Le didacticiel suppose que vous disposez d’une orchestration qui envoie des appels BeginDoc, EditLine et EndDoc vers un port d’envoi lié à l’adaptateur Microsoft BizTalk pour J.D.</span><span class="sxs-lookup"><span data-stu-id="ff449-105">The tutorial assumes you have an orchestration that sends BeginDoc, EditLine and EndDoc calls to a send port bound to the Microsoft BizTalk Adapter for J.D.</span></span> <span data-ttu-id="ff449-106">Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="ff449-106">Edwards OneWorld.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff449-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ff449-107">In This Section</span></span>  
  
-   [<span data-ttu-id="ff449-108">Étape 1 : Faire référence à la DLL du schéma</span><span class="sxs-lookup"><span data-stu-id="ff449-108">Step 1: Reference the Schema DLL</span></span>](../core/step-1-reference-the-schema-dll1.md)  
  
-   [<span data-ttu-id="ff449-109">Étape 2 : Créer l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="ff449-109">Step 2: Create the Orchestration</span></span>](../core/step-2-create-the-orchestration2.md)  
  
-   [<span data-ttu-id="ff449-110">Étape 3 : Créer et exécuter le projet</span><span class="sxs-lookup"><span data-stu-id="ff449-110">Step 3: Complete and Run the Project</span></span>](../core/step-3-complete-and-run-the-project1.md)  
  
-   [<span data-ttu-id="ff449-111">Étape 4 : Créer un exemple XML BeginDoc</span><span class="sxs-lookup"><span data-stu-id="ff449-111">Step 4: Create a Sample XML BeginDoc</span></span>](../core/step-4-create-a-sample-xml-begindoc2.md)