---
title: "Pour activer le rapport d’état, exécuter &#39; Configuration de BizTalk Server &#39; et configurer la fonctionnalité de rapport d’état EDI-AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf125919-80ab-4cb8-b1f5-0f2616cc6f5c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 334e77ed58d460aea3ca37f73c1165d62da0f10b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="to-enable-status-reporting-run-39biztalk-server-configuration39-and-configure-edi-as2-status-reporting-feature"></a><span data-ttu-id="eb4d7-102">Pour activer le rapport d’état, exécuter &#39; Configuration de BizTalk Server &#39; et configurer la fonctionnalité de rapport d’état EDI-AS2</span><span class="sxs-lookup"><span data-stu-id="eb4d7-102">To enable status reporting, run &#39;BizTalk Server Configuration&#39; and configure EDI-AS2 status reporting feature</span></span>
## <a name="details"></a><span data-ttu-id="eb4d7-103">Détails</span><span class="sxs-lookup"><span data-stu-id="eb4d7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eb4d7-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="eb4d7-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="eb4d7-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="eb4d7-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="eb4d7-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="eb4d7-106">Event ID</span></span>|-|  
|<span data-ttu-id="eb4d7-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="eb4d7-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="eb4d7-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="eb4d7-108"> EDI</span></span>|  
|<span data-ttu-id="eb4d7-109">Composant</span><span class="sxs-lookup"><span data-stu-id="eb4d7-109">Component</span></span>|<span data-ttu-id="eb4d7-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="eb4d7-110">EDI Engine</span></span>|  
|<span data-ttu-id="eb4d7-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="eb4d7-111">Symbolic Name</span></span>|<span data-ttu-id="eb4d7-112">0</span><span class="sxs-lookup"><span data-stu-id="eb4d7-112">0</span></span>|  
|<span data-ttu-id="eb4d7-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="eb4d7-113">Message Text</span></span>|<span data-ttu-id="eb4d7-114">Pour activer la création de rapports d'état, exécutez la configuration de BizTalk Server et configurez la fonctionnalité de création de rapports d'état EDI/AS2.</span><span class="sxs-lookup"><span data-stu-id="eb4d7-114">To enable status reporting, run 'BizTalk Server Configuration' and configure EDI/AS2 status reporting feature.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="eb4d7-115">Explication</span><span class="sxs-lookup"><span data-stu-id="eb4d7-115">Explanation</span></span>  
 <span data-ttu-id="eb4d7-116">Cet événement d'erreur/d'avertissement/d'informations indique que la création de rapports d'état EDI/AS2 ne fonctionne pas car cette fonctionnalité n'a pas été configurée.</span><span class="sxs-lookup"><span data-stu-id="eb4d7-116">This Error/Warning/Information event indicates that EDI/AS2 status reporting is not working because it has not been configured.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="eb4d7-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="eb4d7-117">User Action</span></span>  
 <span data-ttu-id="eb4d7-118">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="eb4d7-118">To resolve this error, do the following:</span></span>  
  
1.  <span data-ttu-id="eb4d7-119">Exécutez l'Assistant Configuration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="eb4d7-119">Run the BizTalk Server Configuration wizard.</span></span> <span data-ttu-id="eb4d7-120">Cliquez sur le nœud Moteur d'exécution EDI/AS2 BizTalk, puis activez la propriété « Activer le rapport d'état EDI/AS2 BizTalk pour ce groupe BizTalk ».</span><span class="sxs-lookup"><span data-stu-id="eb4d7-120">Click the BizTalk EDI/AS2 Runtime node, and check the "Enable BizTalk EDI/AS2 Runtime Status Reporting for this BizTalk Group" property.</span></span> <span data-ttu-id="eb4d7-121">Vous devez configurer l'analyse BAM afin de configurer la création de rapports d'état EDI/AS2.</span><span class="sxs-lookup"><span data-stu-id="eb4d7-121">You must configure BAM in order to configure EDI/AS2 status reporting.</span></span>  
  
2.  <span data-ttu-id="eb4d7-122">Dans la console Administration de BizTalk Server, activez la création de rapports d'état EDI pour le tiers en cliquant sur la propriété « Activer la création de rapports EDI » dans la page Général de la boîte de dialogue Propriétés EDI.</span><span class="sxs-lookup"><span data-stu-id="eb4d7-122">In the BizTalk Server Administration Console, enable EDI status reporting for the party by clicking the "Activate EDI reporting" property in the General page of the EDI Properties dialog box.</span></span> <span data-ttu-id="eb4d7-123">Activez la création de rapports d'état AS2 pour le tiers en cliquant sur la propriété « Activer la création de rapports AS2 » dans la page Général de la boîte de dialogue Propriétés AS2.</span><span class="sxs-lookup"><span data-stu-id="eb4d7-123">Enable AS2 status reporting for the party by clicking the "Activate AS2 reporting" property in the General page of the AS2 Properties dialog box.</span></span> <span data-ttu-id="eb4d7-124">Vous devez redémarrer le service BizTalk après l'activation de la création de rapports d'état EDI ou AS2.</span><span class="sxs-lookup"><span data-stu-id="eb4d7-124">You must restart the BizTalk service after enabling EDI or AS2 status reporting.</span></span>