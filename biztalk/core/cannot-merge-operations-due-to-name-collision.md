---
title: "Impossible de fusionner les opérations en raison d’une collision de nom | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81ddb8b7-6f7e-420c-b7c3-921c0e305326
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8f884b4eea6be64f1d1575b157805703d12cee3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-merge-operations-due-to-name-collision"></a><span data-ttu-id="5b7d9-102">Impossible de fusionner l'opération en raison d'une collision de noms</span><span class="sxs-lookup"><span data-stu-id="5b7d9-102">Cannot merge operations due to name collision</span></span>
## <a name="details"></a><span data-ttu-id="5b7d9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5b7d9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b7d9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5b7d9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5b7d9-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5b7d9-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="5b7d9-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5b7d9-106">Event ID</span></span>|<span data-ttu-id="5b7d9-107">0</span><span class="sxs-lookup"><span data-stu-id="5b7d9-107">0</span></span>|  
|<span data-ttu-id="5b7d9-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5b7d9-108">Event Source</span></span>|<span data-ttu-id="5b7d9-109">0</span><span class="sxs-lookup"><span data-stu-id="5b7d9-109">0</span></span>|  
|<span data-ttu-id="5b7d9-110">Composant</span><span class="sxs-lookup"><span data-stu-id="5b7d9-110">Component</span></span>|<span data-ttu-id="5b7d9-111">0</span><span class="sxs-lookup"><span data-stu-id="5b7d9-111">0</span></span>|  
|<span data-ttu-id="5b7d9-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5b7d9-112">Symbolic Name</span></span>|<span data-ttu-id="5b7d9-113">0</span><span class="sxs-lookup"><span data-stu-id="5b7d9-113">0</span></span>|  
|<span data-ttu-id="5b7d9-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5b7d9-114">Message Text</span></span>|<span data-ttu-id="5b7d9-115">Impossible de fusionner l'opération « {0} » en raison d'une collision de noms.</span><span class="sxs-lookup"><span data-stu-id="5b7d9-115">Cannot merge operation "{0}" due to name collision.</span></span> <span data-ttu-id="5b7d9-116">Toutes les opérations d'un service Web doivent avoir des noms uniques.</span><span class="sxs-lookup"><span data-stu-id="5b7d9-116">All operations in a web service must have unique names.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5b7d9-117">Explication</span><span class="sxs-lookup"><span data-stu-id="5b7d9-117">Explanation</span></span>  
 <span data-ttu-id="5b7d9-118">Cette erreur indique que le nom ou le nom d'opération de deux ports en cours de fusion sont identiques.</span><span class="sxs-lookup"><span data-stu-id="5b7d9-118">This error indicates the port name or the operation name of two different ports that are being merged have the same name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5b7d9-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5b7d9-119">User Action</span></span>  
 <span data-ttu-id="5b7d9-120">À l'aide de l'Assistant Configuration du port, vérifiez que tous les ports en cours de fusion portent différents noms ou sont associés à des opérations différentes.</span><span class="sxs-lookup"><span data-stu-id="5b7d9-120">Using the Port Configuration Wizard, ensure that all the ports that are being merged have different port names and operation.</span></span>  
  
 <span data-ttu-id="5b7d9-121">Pour plus d'informations sur la configuration des ports, consultez la ressource suivante dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="5b7d9-121">For additional information on port configuration, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="5b7d9-122">Comment exécuter l’Assistant Configuration du Port</span><span class="sxs-lookup"><span data-stu-id="5b7d9-122">How to Run the Port Configuration Wizard</span></span>](../core/how-to-run-the-port-configuration-wizard.md)