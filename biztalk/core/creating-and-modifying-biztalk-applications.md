---
title: "Création et modification des Applications BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], modifying
- managing [applications], creating
- applications, modifying
- applications, creating
- modifying, applications
- creating, applications
ms.assetid: d6c9ff3a-3903-40ec-bcaa-e46cbaf8a58d
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5daa9630fb8ad742d34421478a19081ad5c83f50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-modifying-biztalk-applications"></a><span data-ttu-id="75866-102">Création et modification des applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="75866-102">Creating and Modifying BizTalk Applications</span></span>
<span data-ttu-id="75866-103">Cette section décrit comment utiliser la console Administration de BizTalk Server ou l'outil de ligne de commande BTSTask pour créer, configurer et modifier des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="75866-103">This section describes how to use the BizTalk Server Administration console or the BTSTask command-line tool to create, configure, and modify BizTalk applications.</span></span>  
  
 <span data-ttu-id="75866-104">Pour plus d’informations sur la création, la gestion, le déploiement et mise à jour des applications BizTalk, consultez [gestion et déploiement d’applications BizTalk compréhension](../core/understanding-biztalk-application-deployment-and-management.md).</span><span class="sxs-lookup"><span data-stu-id="75866-104">For background information on creating, managing, deploying, and updating BizTalk applications, see [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md).</span></span> <span data-ttu-id="75866-105">Pour plus d’informations sur la gestion des artefacts, notamment la modification de leurs propriétés, consultez [la gestion des artefacts](../core/managing-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="75866-105">For information about managing artifacts, including editing their properties, see [Managing Artifacts](../core/managing-artifacts.md).</span></span> <span data-ttu-id="75866-106">Pour obtenir des instructions sur le déploiement d’applications BizTalk, consultez [déploiement d’Applications BizTalk](../core/deploying-biztalk-applications.md).</span><span class="sxs-lookup"><span data-stu-id="75866-106">For instructions on deploying BizTalk applications, see [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75866-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="75866-107">In This Section</span></span>  
  
-   [<span data-ttu-id="75866-108">Comment créer une Application</span><span class="sxs-lookup"><span data-stu-id="75866-108">How to Create an Application</span></span>](../core/how-to-create-an-application.md)  
  
-   [<span data-ttu-id="75866-109">Comment configurer une Application</span><span class="sxs-lookup"><span data-stu-id="75866-109">How to Configure an Application</span></span>](../core/how-to-configure-an-application.md)  
  
-   [<span data-ttu-id="75866-110">Comment modifier le nom d’une Application</span><span class="sxs-lookup"><span data-stu-id="75866-110">How to Change the Name of an Application</span></span>](../core/how-to-change-the-name-of-an-application.md)  
  
-   [<span data-ttu-id="75866-111">Comment créer ou ajouter un artefact</span><span class="sxs-lookup"><span data-stu-id="75866-111">How to Create or Add an Artifact</span></span>](../core/how-to-create-or-add-an-artifact.md)  
  
-   [<span data-ttu-id="75866-112">Comment créer un lien vers un fichier Lisez-moi</span><span class="sxs-lookup"><span data-stu-id="75866-112">How to Link to a Readme File</span></span>](../core/how-to-link-to-a-readme-file.md)  
  
-   [<span data-ttu-id="75866-113">Comment ajouter un artefact 64 bits à une Application</span><span class="sxs-lookup"><span data-stu-id="75866-113">How to Add a 64-Bit Artifact to an Application</span></span>](../core/how-to-add-a-64-bit-artifact-to-an-application.md)  
  
-   [<span data-ttu-id="75866-114">Comment modifier l’Application par défaut</span><span class="sxs-lookup"><span data-stu-id="75866-114">How to Change the Default Application</span></span>](../core/how-to-change-the-default-application.md)  
  
-   [<span data-ttu-id="75866-115">Comment ajouter une référence à une autre Application</span><span class="sxs-lookup"><span data-stu-id="75866-115">How to Add a Reference to Another Application</span></span>](../core/how-to-add-a-reference-to-another-application.md)  
  
-   [<span data-ttu-id="75866-116">Comment afficher les références d’une Application</span><span class="sxs-lookup"><span data-stu-id="75866-116">How to View the References of an Application</span></span>](../core/how-to-view-the-references-of-an-application.md)  
  
-   [<span data-ttu-id="75866-117">Comment supprimer une référence à une autre Application</span><span class="sxs-lookup"><span data-stu-id="75866-117">How to Remove a Reference to Another Application</span></span>](../core/how-to-remove-a-reference-to-another-application.md)  
  
-   [<span data-ttu-id="75866-118">Comment déplacer un artefact vers une autre Application</span><span class="sxs-lookup"><span data-stu-id="75866-118">How to Move an Artifact to a Different Application</span></span>](../core/how-to-move-an-artifact-to-a-different-application.md)  
  
-   [<span data-ttu-id="75866-119">Comment supprimer un artefact d’une Application</span><span class="sxs-lookup"><span data-stu-id="75866-119">How to Remove an Artifact from an Application</span></span>](../core/how-to-remove-an-artifact-from-an-application.md)