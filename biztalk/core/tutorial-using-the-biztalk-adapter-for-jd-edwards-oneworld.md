---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour JD Edwards OneWorld | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e13a648-7eaf-40c4-a71b-b66999087a69
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab54a0fe0f4a036e0045938951cf44337087853b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-jd-edwards-oneworld"></a><span data-ttu-id="a2cfc-102">Didacticiel : Utilisation de l’adaptateur BizTalk pour JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="a2cfc-102">Tutorial: Using the BizTalk Adapter for JD Edwards OneWorld</span></span>
<span data-ttu-id="a2cfc-103">L’exemple suivant présente à l’aide des propriétés de contexte BizTalk pour contrôler le J.D.</span><span class="sxs-lookup"><span data-stu-id="a2cfc-103">The following demonstrates using BizTalk Context Properties to control the J.D.</span></span> <span data-ttu-id="a2cfc-104">Session Edwards OneWorld dans votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="a2cfc-104">Edwards OneWorld session in your orchestration.</span></span> <span data-ttu-id="a2cfc-105">Le didacticiel suppose que vous disposez d’une orchestration qui envoie des appels BeginDoc, EditLine et EndDoc vers un port d’envoi lié à l’adaptateur Microsoft BizTalk pour J.D.</span><span class="sxs-lookup"><span data-stu-id="a2cfc-105">The tutorial assumes you have an orchestration that sends BeginDoc, EditLine and EndDoc calls to a send port bound to the Microsoft BizTalk Adapter for J.D.</span></span> <span data-ttu-id="a2cfc-106">Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="a2cfc-106">Edwards OneWorld.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2cfc-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a2cfc-107">In This Section</span></span>  
  
-   [<span data-ttu-id="a2cfc-108">Étape 1 : Faire référence à la DLL du schéma</span><span class="sxs-lookup"><span data-stu-id="a2cfc-108">Step 1: Reference the Schema DLL</span></span>](../core/step-1-reference-the-schema-dll2.md)  
  
-   [<span data-ttu-id="a2cfc-109">Étape 2 : Créer l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="a2cfc-109">Step 2: Create the Orchestration</span></span>](../core/step-2-create-the-orchestration1.md)  
  
-   [<span data-ttu-id="a2cfc-110">Étape 3 : Créer et exécuter le projet</span><span class="sxs-lookup"><span data-stu-id="a2cfc-110">Step 3: Complete and Run the Project</span></span>](../core/step-3-complete-and-run-the-project2.md)  
  
-   [<span data-ttu-id="a2cfc-111">Étape 4 : Créer un exemple XML BeginDoc</span><span class="sxs-lookup"><span data-stu-id="a2cfc-111">Step 4: Create a Sample XML BeginDoc</span></span>](../core/step-4-create-a-sample-xml-begindoc1.md)