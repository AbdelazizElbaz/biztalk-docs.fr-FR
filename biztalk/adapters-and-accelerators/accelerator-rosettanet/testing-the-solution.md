---
title: Test de la Solution | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing solutions
- private process tutorial, testing solutions
ms.assetid: 90faf959-bac6-4695-8cb7-ecabe52baf1a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7af2cab529344f499ff006a6cd99401ae63c4668
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="testing-the-solution"></a><span data-ttu-id="42ef3-102">Test de la Solution</span><span class="sxs-lookup"><span data-stu-id="42ef3-102">Testing the Solution</span></span>
<span data-ttu-id="42ef3-103">Dans cette section, vous tester votre solution complète.</span><span class="sxs-lookup"><span data-stu-id="42ef3-103">In this section, you test your complete solution.</span></span> <span data-ttu-id="42ef3-104">Vous utilisez l’outil de LOBWebApplication créé dans la solution Fabrikam pour soumettre des demandes PIP 3A2 à l’application Contoso LOB.</span><span class="sxs-lookup"><span data-stu-id="42ef3-104">You use the LOBWebApplication tool created in the Fabrikam solution to submit 3A2 PIP requests to the Contoso LOB application.</span></span> <span data-ttu-id="42ef3-105">L’orchestration privée Contoso que vous avez créé puis soumet une Contoso 3A2 en fonction des demande de prix et la disponibilité au système ERP à l’aide de l’adaptateur SQL pour BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="42ef3-105">The Contoso private orchestration that you created then submits a Contoso based 3A2 Price and Availability request to the ERP system using the SQL adapter for BizTalk Server.</span></span> <span data-ttu-id="42ef3-106">Lorsque la réponse est reçue à partir du système ERP, l’orchestration appelle le moteur de règles d’entreprise pour appliquer la situation d’urgence doit stratégie commerciale que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="42ef3-106">When the response is received from the ERP system, the orchestration calls the Business Rule Engine to enforce the emergency needs business policy that you created.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42ef3-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="42ef3-107">In This Section</span></span>  
  
-   [<span data-ttu-id="42ef3-108">Création d’une demande de prix et de disponibilité avec l’exemple Fabrikam</span><span class="sxs-lookup"><span data-stu-id="42ef3-108">Creating a Price and Availability Request with the Fabrikam Sample</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-a-price-and-availability-request-with-the-fabrikam-sample.md)