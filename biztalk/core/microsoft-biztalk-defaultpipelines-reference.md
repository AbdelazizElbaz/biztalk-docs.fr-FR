---
title: "Référence à Microsoft.BizTalk.DefaultPipelines | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, PassThruTransmit
- pipelines, PassThruReceive
- pipelines
- PassThruTransmit pipelines
- XMLReceive pipelines
- pipelines, XMLTransmit
- Pipeline Designer
- pipelines, XMLReceive
- pipelines, about pipelines
- PassThruReceive pipelines
- XMLTransmit pipelines
- namespaces, Microsoft.BizTalk.DefaultPipelines namespace
- Microsoft.BizTalk.DefaultPipelines namespace
ms.assetid: a54f8813-9c6f-4afe-8c76-2db3fa478947
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ad7cad78e3e8606371a5fa49673297cf590ddbe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="microsoftbiztalkdefaultpipelines-reference"></a><span data-ttu-id="fbf0a-102">Référence à Microsoft.BizTalk.DefaultPipelines</span><span class="sxs-lookup"><span data-stu-id="fbf0a-102">Microsoft.BizTalk.DefaultPipelines Reference</span></span>
<span data-ttu-id="fbf0a-103">Le **Microsoft.BizTalk.DefaultPipelines** espace de noms contient les pipelines suivants :</span><span class="sxs-lookup"><span data-stu-id="fbf0a-103">The **Microsoft.BizTalk.DefaultPipelines** namespace contains the following pipelines:</span></span>  
  
-   <span data-ttu-id="fbf0a-104">XMLReceive</span><span class="sxs-lookup"><span data-stu-id="fbf0a-104">XMLReceive</span></span>  
  
-   <span data-ttu-id="fbf0a-105">PassThruReceive</span><span class="sxs-lookup"><span data-stu-id="fbf0a-105">PassThruReceive</span></span>  
  
-   <span data-ttu-id="fbf0a-106">XMLTransmit</span><span class="sxs-lookup"><span data-stu-id="fbf0a-106">XMLTransmit</span></span>  
  
-   <span data-ttu-id="fbf0a-107">PassThruTransmit</span><span class="sxs-lookup"><span data-stu-id="fbf0a-107">PassThruTransmit</span></span>  
  
 <span data-ttu-id="fbf0a-108">Un pipeline est un composant logiciel qui définit et relie une ou plusieurs étapes de traitement des messages reçus ou envoyés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbf0a-108">A pipeline is a software component that defines and links one or more stages for processing messages received or sent by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="fbf0a-109">Ces étapes incluent des fonctions comme le codage ou le décodage, le désassemblage ou l'assemblage et le chiffrement ou le déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-109">The stages include functions such as encoding or decoding, disassembling or assembling, and decrypting or encrypting.</span></span> <span data-ttu-id="fbf0a-110">Ces fonctions sont implémentées dans un ordre précis.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-110">These functions are implemented in a specific order.</span></span> <span data-ttu-id="fbf0a-111">Vous pouvez utiliser le Concepteur de pipeline pour créer des pipelines de réception et d'envoi.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-111">You can use Pipeline Designer to create receive and send pipelines.</span></span>  
  
 <span data-ttu-id="fbf0a-112">Les pipelines par défaut inclus dans un projet BizTalk peuvent traiter tous les types de documents à l’aide de la **PassThruReceive** et **PassThruTransmit** pipelines.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-112">The default pipeline references included in a BizTalk project can process all types of documents using the **PassThruReceive** and **PassThruTransmit** pipelines.</span></span>  
  
 <span data-ttu-id="fbf0a-113">Les listes suivantes présentent les composants des pipelines par défaut.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-113">The following lists show the default components in the default pipelines.</span></span> <span data-ttu-id="fbf0a-114">Elles indiquent aussi l'ordre par défaut des composants de chaque pipeline.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-114">These lists also indicate the default order of the components in each pipeline.</span></span> <span data-ttu-id="fbf0a-115">Vous pouvez ajouter et supprimer des composants selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-115">You can add and delete components if necessary.</span></span>  
  
 <span data-ttu-id="fbf0a-116">Voici les composants par défaut du pipeline XMLReceive par défaut :</span><span class="sxs-lookup"><span data-stu-id="fbf0a-116">The default components in the default XMLReceive pipeline are:</span></span>  
  
-   <span data-ttu-id="fbf0a-117">Décrypteur</span><span class="sxs-lookup"><span data-stu-id="fbf0a-117">Decrypter</span></span>  
  
-   <span data-ttu-id="fbf0a-118">Décodeur</span><span class="sxs-lookup"><span data-stu-id="fbf0a-118">Decoder</span></span>  
  
-   <span data-ttu-id="fbf0a-119">Désassembleur</span><span class="sxs-lookup"><span data-stu-id="fbf0a-119">Disassembler</span></span>  
  
-   <span data-ttu-id="fbf0a-120">Valideur</span><span class="sxs-lookup"><span data-stu-id="fbf0a-120">Validator</span></span>  
  
-   <span data-ttu-id="fbf0a-121">Résolution du tiers</span><span class="sxs-lookup"><span data-stu-id="fbf0a-121">Party Resolution</span></span>  
  
 <span data-ttu-id="fbf0a-122">Voici les composants par défaut du pipeline XMLTransmit par défaut :</span><span class="sxs-lookup"><span data-stu-id="fbf0a-122">The default components in the default XMLTransmit pipeline are:</span></span>  
  
-   <span data-ttu-id="fbf0a-123">Assembleur</span><span class="sxs-lookup"><span data-stu-id="fbf0a-123">Assembler</span></span>  
  
-   <span data-ttu-id="fbf0a-124">Encodeur</span><span class="sxs-lookup"><span data-stu-id="fbf0a-124">Encoder</span></span>  
  
-   <span data-ttu-id="fbf0a-125">Encrypteur</span><span class="sxs-lookup"><span data-stu-id="fbf0a-125">Encrypter</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf0a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbf0a-126">See Also</span></span>  
 <span data-ttu-id="fbf0a-127">[Création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md) </span><span class="sxs-lookup"><span data-stu-id="fbf0a-127">[Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md) </span></span>  
 [<span data-ttu-id="fbf0a-128">À propos des références de Namespace de BizTalk inclus dans les projets BizTalk</span><span class="sxs-lookup"><span data-stu-id="fbf0a-128">About BizTalk Namespace References Included in BizTalk Projects</span></span>](../core/about-biztalk-namespace-references-included-in-biztalk-projects.md)