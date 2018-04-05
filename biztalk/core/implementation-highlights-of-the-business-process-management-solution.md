---
title: Caractéristiques de l’implémentation de l’activité traitent la Solution de gestion | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, implementing
ms.assetid: 3558db0e-d7f6-4c10-bd58-1601bd44e73f
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: decad6f68398cca2d0b88c4904d3e63c075749b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementation-highlights-of-the-business-process-management-solution"></a><span data-ttu-id="21c76-102">Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="21c76-102">Implementation Highlights of the Business Process Management Solution</span></span>
<span data-ttu-id="21c76-103">Cette section présente de manière plus détaillée les éléments liés à l'implémentation de la solution.</span><span class="sxs-lookup"><span data-stu-id="21c76-103">This section describes the implementation-related elements of the solution in greater detail.</span></span> <span data-ttu-id="21c76-104">Ces éléments incluent l’infrastructure de règles d’entreprise, le nombre d’étapes de traitement, comment les **OrderManager** communique avec les étapes de traitement, l’utilisation de la **OrderHandler** objet et comment la application utilise l’adaptateur Ops.</span><span class="sxs-lookup"><span data-stu-id="21c76-104">These elements include the Business Rules Framework, the number of processing stages, how the **OrderManager** communicates with the processing stages, the use of the **OrderHandler** object, and how the application uses the Ops Adapter.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21c76-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="21c76-105">In This Section</span></span>  
  
-   [<span data-ttu-id="21c76-106">Validation avec des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="21c76-106">Validation with Business Rules</span></span>](../core/validation-with-business-rules.md)  
  
-   [<span data-ttu-id="21c76-107">Nombre d’étapes de traitement</span><span class="sxs-lookup"><span data-stu-id="21c76-107">Number of Processing Stages</span></span>](../core/number-of-processing-stages.md)  
  
-   [<span data-ttu-id="21c76-108">Liaison directe de partenaires inversée</span><span class="sxs-lookup"><span data-stu-id="21c76-108">Inverse Direct Partner Binding</span></span>](../core/inverse-direct-partner-binding.md)  
  
-   [<span data-ttu-id="21c76-109">Communication entre OrderBroker et OrderManager</span><span class="sxs-lookup"><span data-stu-id="21c76-109">Communication between OrderBroker and OrderManager</span></span>](../core/communication-between-orderbroker-and-ordermanager.md)  
  
-   [<span data-ttu-id="21c76-110">À l’aide de l’authentification unique efficacement dans la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="21c76-110">Using SSO Efficiently in the Business Process Management Solution</span></span>](../core/using-sso-efficiently-in-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="21c76-111">À l’aide de l’objet de gestionnaire de commande pour communiquer avec les systèmes principaux</span><span class="sxs-lookup"><span data-stu-id="21c76-111">Using the Order Handler Object to Communicate with Backend Systems</span></span>](../core/using-the-order-handler-object-to-communicate-with-backend-systems.md)  
  
-   [<span data-ttu-id="21c76-112">Fusion de Documents XML</span><span class="sxs-lookup"><span data-stu-id="21c76-112">Merging XML Documents</span></span>](../core/merging-xml-documents.md)  
  
-   [<span data-ttu-id="21c76-113">L’adaptateur Ops</span><span class="sxs-lookup"><span data-stu-id="21c76-113">The Ops Adapter</span></span>](../core/the-ops-adapter.md)  
  
-   [<span data-ttu-id="21c76-114">Objet Recaller</span><span class="sxs-lookup"><span data-stu-id="21c76-114">The Recaller Object</span></span>](../core/the-recaller-object.md)