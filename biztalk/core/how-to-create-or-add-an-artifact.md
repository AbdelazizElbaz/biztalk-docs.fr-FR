---
title: "Comment créer ou ajouter un artefact | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, artifacts
- artifacts, creating
- applications, artifacts
ms.assetid: fea7487c-b5fa-457f-8c74-a20ea3a6df85
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b231cdf6a25c4ca316c9620ee789e6e3a715fd6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-or-add-an-artifact"></a><span data-ttu-id="0213c-102">Ajout ou création d'un artefact</span><span class="sxs-lookup"><span data-stu-id="0213c-102">How to Create or Add an Artifact</span></span>
<span data-ttu-id="0213c-103">Une fois que vous avez créé une application BizTalk, vous pouvez ajouter des artefacts basés sur un fichier (par exemple des assemblys BizTalk, des assemblys .NET, scripts et certificats) à partir du système de fichiers ou ajouter des stratégies à partir de la base de données du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="0213c-103">After you create a BizTalk application, you can add file-based artifacts (for example BizTalk assemblies, .NET assemblies, scripts, and certificates) from the file system or add policies from the Rule Engine database.</span></span> <span data-ttu-id="0213c-104">Vous pouvez également créer des ports d’envoi, des groupes de ports d’envoi, des emplacements de réception, des ports de réception au sein de l'application.</span><span class="sxs-lookup"><span data-stu-id="0213c-104">You can also create send ports, send port groups, receive locations, and receive ports within the application.</span></span> <span data-ttu-id="0213c-105">La création ou l’ajout d’artefacts permet de les ajouter à la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0213c-105">Creating or adding artifacts adds them to the BizTalk Management database.</span></span> <span data-ttu-id="0213c-106">Vous pouvez ensuite déployer l’application et ses artefacts en tant qu’entité unique, comme décrit dans [déploiement d’Applications BizTalk](../core/deploying-biztalk-applications.md).</span><span class="sxs-lookup"><span data-stu-id="0213c-106">You can then deploy the application and its artifacts as a single entity, as described in [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0213c-107">Certains types d’artefacts doivent être uniques dans un groupe ou une application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0213c-107">Certain types of artifacts must be unique in a BizTalk application or group.</span></span> <span data-ttu-id="0213c-108">Pour plus d’informations, consultez [artefacts que doit être Unique dans une Application ou d’un groupe](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).</span><span class="sxs-lookup"><span data-stu-id="0213c-108">For more information, see [Artifacts That Must Be Unique in an Application or Group](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).</span></span>  
  
 <span data-ttu-id="0213c-109">Pour les procédures d’ajout et de création de chacun des artefacts, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="0213c-109">For procedures on adding or creating each artifact type, see the following topics:</span></span>  
  
-   [<span data-ttu-id="0213c-110">Comment créer un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="0213c-110">How to Create a Send Port</span></span>](../core/how-to-create-a-send-port2.md)  
  
-   [<span data-ttu-id="0213c-111">Comment créer un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="0213c-111">How to Create a Send Port Group</span></span>](../core/how-to-create-a-send-port-group.md)  
  
-   [<span data-ttu-id="0213c-112">Comment créer un Port de réception</span><span class="sxs-lookup"><span data-stu-id="0213c-112">How to Create a Receive Port</span></span>](../core/how-to-create-a-receive-port.md)  
  
-   [<span data-ttu-id="0213c-113">Comment créer un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="0213c-113">How to Create a Receive Location</span></span>](../core/how-to-create-a-receive-location.md)  
  
-   [<span data-ttu-id="0213c-114">Comment ajouter une stratégie à une Application</span><span class="sxs-lookup"><span data-stu-id="0213c-114">How to Add a Policy to an Application</span></span>](../core/how-to-add-a-policy-to-an-application.md)  
  
-   [<span data-ttu-id="0213c-115">Comment ajouter un Assembly BizTalk à une Application</span><span class="sxs-lookup"><span data-stu-id="0213c-115">How to Add a BizTalk Assembly to an Application</span></span>](../core/how-to-add-a-biztalk-assembly-to-an-application.md)  
  
-   [<span data-ttu-id="0213c-116">Comment ajouter un Script de pré-traitement ou de post-traitement à une Application</span><span class="sxs-lookup"><span data-stu-id="0213c-116">How to Add a Pre- or Post-processing Script to an Application</span></span>](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)  
  
-   [<span data-ttu-id="0213c-117">Comment ajouter un fichier à une Application</span><span class="sxs-lookup"><span data-stu-id="0213c-117">How to Add a File to an Application</span></span>](../core/how-to-add-a-file-to-an-application.md)  
  
-   [<span data-ttu-id="0213c-118">Comment ajouter un certificat à une Application</span><span class="sxs-lookup"><span data-stu-id="0213c-118">How to Add a Certificate to an Application</span></span>](../core/how-to-add-a-certificate-to-an-application.md)  
  
-   [<span data-ttu-id="0213c-119">Comment ajouter un composant COM à une Application</span><span class="sxs-lookup"><span data-stu-id="0213c-119">How to Add a COM Component to an Application</span></span>](../core/how-to-add-a-com-component-to-an-application.md)  
  
-   [<span data-ttu-id="0213c-120">Comment ajouter un Assembly .NET à une Application</span><span class="sxs-lookup"><span data-stu-id="0213c-120">How to Add a .NET Assembly to an Application</span></span>](../core/how-to-add-a-net-assembly-to-an-application.md)  
  
-   [<span data-ttu-id="0213c-121">Comment ajouter un artefact BAM à une Application</span><span class="sxs-lookup"><span data-stu-id="0213c-121">How to Add a BAM Artifact to an Application</span></span>](../core/how-to-add-a-bam-artifact-to-an-application.md)  
  
-   [<span data-ttu-id="0213c-122">Comment ajouter un fichier de liaison à une Application</span><span class="sxs-lookup"><span data-stu-id="0213c-122">How to Add a Binding File to an Application</span></span>](../core/how-to-add-a-binding-file-to-an-application2.md)  
  
> [!NOTE]
>  <span data-ttu-id="0213c-123">Si le chemin d'accès (nom du fichier compris) à l'artefact que vous ajoutez est très long, l'opération consistant à ajouter un artefact à une application peut échouer.</span><span class="sxs-lookup"><span data-stu-id="0213c-123">If the artifact you are adding has a very long path (e.g., the path and file name), the operation to add the artifact to an application may fail.</span></span> <span data-ttu-id="0213c-124">Un chemin d'accès est limité à 260 caractères.</span><span class="sxs-lookup"><span data-stu-id="0213c-124">A path can't exceed 260 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0213c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0213c-125">See Also</span></span>  
 <span data-ttu-id="0213c-126">[Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="0213c-126">[Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="0213c-127">Comment ajouter un artefact 64 bits à une Application</span><span class="sxs-lookup"><span data-stu-id="0213c-127">How to Add a 64-Bit Artifact to an Application</span></span>](../core/how-to-add-a-64-bit-artifact-to-an-application.md)