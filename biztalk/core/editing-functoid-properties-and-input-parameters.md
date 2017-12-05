---
title: "Modification des propriétés des fonctoids et des paramètres d’entrée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 257f92d7-8196-4c7c-98de-819996270e43
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3d87396713b7fa8f7874b921e6ee9097399d1c6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="editing-functoid-properties-and-input-parameters"></a><span data-ttu-id="00ea4-102">Modification des propriétés et paramètres d'entrée d'un fonctoid</span><span class="sxs-lookup"><span data-stu-id="00ea4-102">Editing Functoid Properties and Input Parameters</span></span>
<span data-ttu-id="00ea4-103">Les propriétés de fonctoids peuvent être réparties dans les catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="00ea4-103">Functoid properties can be categorized as follows:</span></span>  
  
-   <span data-ttu-id="00ea4-104">**Étiquette** et **paramètres d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="00ea4-104">**Label** and **Input parameters**.</span></span> <span data-ttu-id="00ea4-105">ces deux propriétés sont accessibles en lecture et en écriture et sont disponibles pour tous les fonctoids.</span><span class="sxs-lookup"><span data-stu-id="00ea4-105">These two properties are read/write and are available for all functoids.</span></span> <span data-ttu-id="00ea4-106">Le **étiquette** propriété fournit un mécanisme qui fournit un nom descriptif pour une instance particulière d’un fonctoid, qui peut aider à la gestion des mappages.</span><span class="sxs-lookup"><span data-stu-id="00ea4-106">The **Label** property provides a mechanism for providing a descriptive name for a particular instance of a functoid, which may help in maintaining maps.</span></span> <span data-ttu-id="00ea4-107">Le **paramètres d’entrée** propriété fournit l’accès à la **configurer \<fonctoid\> fonctoid** boîte de dialogue, qui joue un rôle central dans la configuration du fonctoid.</span><span class="sxs-lookup"><span data-stu-id="00ea4-107">The **Input parameters** property provides access to the **Configure \<Functoid\> Functoid** dialog box, which plays a central role in functoid configuration.</span></span>  
  
-   <span data-ttu-id="00ea4-108">**Script** et **grille Bouclage de Table**.</span><span class="sxs-lookup"><span data-stu-id="00ea4-108">**Script** and **Table Looping Grid**.</span></span> <span data-ttu-id="00ea4-109">Ces deux propriétés donnent accès aux boîtes de dialogue qui ne sont applicables à la **script** et **bouclage de Table** fonctoids, respectivement.</span><span class="sxs-lookup"><span data-stu-id="00ea4-109">These two properties provide access to dialog boxes that are only applicable to the **Scripting** and **Table Looping** functoids, respectively.</span></span> <span data-ttu-id="00ea4-110">Ces boîtes de dialogue sont les **configurer le fonctoid script** boîte de dialogue et les **configurer le fonctoid Bouclage de Table** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="00ea4-110">These dialog boxes are the **Configure Scripting Functoid** dialog box and the **Configure Table Looping Functoid** dialog box.</span></span>  
  
-   <span data-ttu-id="00ea4-111">**Nom**, **aide**, **nombre maximal de paramètres d’entrée**, et **au Minimum les paramètres d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="00ea4-111">**Name**, **Help**, **Maximum Input Parameters**, and **Minimum Input Parameters**.</span></span> <span data-ttu-id="00ea4-112">ces quatre propriétés sont informatives et toujours en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="00ea4-112">These four are informational and always read-only.</span></span>  
  
 <span data-ttu-id="00ea4-113">Pour obtenir des informations conceptuelles sur les propriétés de fonctoid, consultez [propriétés des fonctoids](../core/functoid-properties.md).</span><span class="sxs-lookup"><span data-stu-id="00ea4-113">For conceptual information about these functoid properties, see [Functoid Properties](../core/functoid-properties.md).</span></span>  
  
 <span data-ttu-id="00ea4-114">Cette section fournit des instructions détaillées sur l’utilisation et la modification en particulier, les propriétés des fonctoids, y compris des instructions générales pour la configuration des paramètres d’entrée des fonctoids, la configuration du script pour le **script**  fonctoid et la configuration de grille de table pour le **bouclage de Table** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="00ea4-114">This section provides step-by-step instructions for working with, and specifically modifying, the properties of functoids, including general instructions for configuring input parameters for functoids, configuring script for the **Scripting** functoid, and configuring table grid for the **Table Looping** functoid.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00ea4-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="00ea4-115">In This Section</span></span>  
  
-   [<span data-ttu-id="00ea4-116">Comment configurer les paramètres d’entrée de fonctoid</span><span class="sxs-lookup"><span data-stu-id="00ea4-116">How to Configure Functoid Input Parameters</span></span>](../core/how-to-configure-functoid-input-parameters.md)  
  
-   [<span data-ttu-id="00ea4-117">Comment configurer le fonctoid script</span><span class="sxs-lookup"><span data-stu-id="00ea4-117">How to Configure the Scripting Functoid</span></span>](../core/how-to-configure-the-scripting-functoid.md)  
  
-   [<span data-ttu-id="00ea4-118">Comment configurer le bouclage de Table et de fonctoids Extracteur de Table</span><span class="sxs-lookup"><span data-stu-id="00ea4-118">How to Configure the Table Looping and Table Extractor Functoids</span></span>](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md)  
  
-   [<span data-ttu-id="00ea4-119">Étiquette et commentaires à un fonctoid</span><span class="sxs-lookup"><span data-stu-id="00ea4-119">How to Label and Comment a Functoid</span></span>](../core/how-to-label-and-comment-a-functoid.md)