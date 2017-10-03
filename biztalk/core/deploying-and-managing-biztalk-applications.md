---
title: "Déploiement et gestion des Applications BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, managing
- Administration Console [BizTalk Server], applications
- bts06.deployment.application
- managing, applications
ms.assetid: d933ad2b-702b-48df-8ef6-a5702d0521e2
caps.latest.revision: "49"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f355c66f7550f5e4cf2b04cfc8bb1f705cc6ade7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-and-managing-biztalk-applications"></a><span data-ttu-id="6c3be-102">Déploiement et gestion des applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="6c3be-102">Deploying and Managing BizTalk Applications</span></span>
<span data-ttu-id="6c3be-103">Cette section fournit des informations sur la gestion des applications BizTalk, à savoir comment les déployer, les modifier, les mettre à jour et annuler leur déploiement.</span><span class="sxs-lookup"><span data-stu-id="6c3be-103">This section provides information about managing BizTalk applications, including how to deploy, modify, update, and undeploy them.</span></span> <span data-ttu-id="6c3be-104">Les applications BizTalk permettent de visualiser et de gérer les éléments, appelés « artefacts », qui composent une solution d'entreprise BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6c3be-104">BizTalk applications provide a way to view and manage the items, called "artifacts," that make up a BizTalk business solution.</span></span> <span data-ttu-id="6c3be-105">Des exemples d'artefacts sont les assemblys BizTalk, les assemblys .NET, les schémas, les mappages, les liaisons et les certificats.</span><span class="sxs-lookup"><span data-stu-id="6c3be-105">Examples of artifacts are BizTalk assemblies, .NET assemblies, schemas, maps, bindings, and certificates.</span></span>  
  
 <span data-ttu-id="6c3be-106">Vous pouvez créer une application BizTalk et lui ajouter des artefacts.</span><span class="sxs-lookup"><span data-stu-id="6c3be-106">You can create a BizTalk application and add artifacts to it.</span></span> <span data-ttu-id="6c3be-107">Vous pouvez ensuite visualiser, regrouper, déployer et gérer l'application et ses artefacts sous la forme d'une entité unique à partir de la console Administration de BizTalk ou de l'outil de ligne de commande BTSTask.</span><span class="sxs-lookup"><span data-stu-id="6c3be-107">You can then view, package, deploy, and manage the application and its artifacts as a single entity from within the BizTalk Administration console or by using the BTSTask command-line tool.</span></span>  
  
 <span data-ttu-id="6c3be-108">Pour plus d’informations générales sur le déploiement d’applications BizTalk et la maintenance, consultez [gestion et déploiement d’applications BizTalk compréhension](../core/understanding-biztalk-application-deployment-and-management.md).</span><span class="sxs-lookup"><span data-stu-id="6c3be-108">For background information about BizTalk application deployment and maintenance, see [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md).</span></span> <span data-ttu-id="6c3be-109">Pour obtenir des instructions sur le déploiement d’une application simple, qui vous familiarisera avec les fonctionnalités de déploiement d’application de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [procédure pas à pas : déploiement d’une Application BizTalk base](../core/walkthrough-deploying-a-basic-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="6c3be-109">For step-by-step instructions on deploying a simple application, which will familiarize you with the application deployment features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Walkthrough: Deploying a Basic BizTalk Application](../core/walkthrough-deploying-a-basic-biztalk-application.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c3be-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6c3be-110">In This Section</span></span>  
  
-   [<span data-ttu-id="6c3be-111">Meilleures pratiques pour déployer une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="6c3be-111">Best Practices for Deploying a BizTalk Application</span></span>](../core/best-practices-for-deploying-a-biztalk-application.md)  
  
-   [<span data-ttu-id="6c3be-112">Déploiement d’applications BizTalk et la gestion des listes de contrôle</span><span class="sxs-lookup"><span data-stu-id="6c3be-112">BizTalk Application Deployment and Management Checklists</span></span>](../core/biztalk-application-deployment-and-management-checklists.md)  
  
-   [<span data-ttu-id="6c3be-113">Procédure pas à pas : Déploiement d’une Application de base BizTalk</span><span class="sxs-lookup"><span data-stu-id="6c3be-113">Walkthrough: Deploying a Basic BizTalk Application</span></span>](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md) 
  
-   [<span data-ttu-id="6c3be-114">Présentation de gestion et déploiement d’applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="6c3be-114">Understanding BizTalk Application Deployment and Management</span></span>](../core/understanding-biztalk-application-deployment-and-management.md)  
  
-   [<span data-ttu-id="6c3be-115">Comment démarrer et arrêter une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="6c3be-115">How to Start and Stop a BizTalk Application</span></span>](../core/how-to-start-and-stop-a-biztalk-application.md)  
  
-   [<span data-ttu-id="6c3be-116">Création et modification des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="6c3be-116">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)  
  
-   [<span data-ttu-id="6c3be-117">La gestion des artefacts</span><span class="sxs-lookup"><span data-stu-id="6c3be-117">Managing Artifacts</span></span>](../core/managing-artifacts.md)  
  
-   [<span data-ttu-id="6c3be-118">Personnalisation des fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="6c3be-118">Customizing Binding Files</span></span>](../core/customizing-binding-files.md)  
  
-   [<span data-ttu-id="6c3be-119">À l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement d’Application</span><span class="sxs-lookup"><span data-stu-id="6c3be-119">Using Pre- and Post-processing Scripts to Customize Application Deployment</span></span>](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)  
  
-   [<span data-ttu-id="6c3be-120">Déploiement d’Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="6c3be-120">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)  
  
-   [<span data-ttu-id="6c3be-121">Mise à jour des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="6c3be-121">Updating BizTalk Applications</span></span>](../core/updating-biztalk-applications.md)  
  
-   [<span data-ttu-id="6c3be-122">Annulation du déploiement des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="6c3be-122">Undeploying BizTalk Applications</span></span>](../core/undeploying-biztalk-applications.md)