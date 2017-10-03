---
title: "Déploiement des Applications BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.deployment.application
helpviewer_keywords:
- deploying [applications]
- managing [applications], deploying
- applications, deploying
ms.assetid: eef12d8a-6f5c-4eb2-b85b-df9281c0b88e
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56417fa7e9c4aef40a6c76144a8e2d9e5bae548f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-biztalk-applications"></a><span data-ttu-id="570fb-102">Déploiement des applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="570fb-102">Deploying BizTalk Applications</span></span>
<span data-ttu-id="570fb-103">Cette rubrique présente les informations suivantes sur le déploiement des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="570fb-103">This section provides the following information about deploying BizTalk applications:</span></span>  
  
-   <span data-ttu-id="570fb-104">exportation d'une application et de ses artefacts vers un fichier Windows Installer (.msi) ;</span><span class="sxs-lookup"><span data-stu-id="570fb-104">Exporting an application and its artifacts to a Windows Installer (.msi) file</span></span>  
  
-   <span data-ttu-id="570fb-105">importation du fichier .msi dans un autre groupe BizTalk pour y créer l'application et ses artefacts ;</span><span class="sxs-lookup"><span data-stu-id="570fb-105">Importing the .msi file into another BizTalk group to create the application and its artifacts in the new group</span></span>  
  
-   <span data-ttu-id="570fb-106">installation de l'application sur les ordinateurs qui vont l'exécuter ;</span><span class="sxs-lookup"><span data-stu-id="570fb-106">Installing the application on the computers that will run it</span></span>  
  
-   <span data-ttu-id="570fb-107">installation des assemblys BizTalk dans le Global Assembly Cache (GAC) ;</span><span class="sxs-lookup"><span data-stu-id="570fb-107">Installing BizTalk assemblies to the global assembly cache (GAC)</span></span>  
  
-   <span data-ttu-id="570fb-108">surveillance de la progression du déploiement et test de l'application ;</span><span class="sxs-lookup"><span data-stu-id="570fb-108">Monitoring the progress of the deployment and testing the application</span></span>  
  
-   <span data-ttu-id="570fb-109">déploiement d'une application pour un partenaire commercial ;</span><span class="sxs-lookup"><span data-stu-id="570fb-109">Deploying an application to a business partner</span></span>  
  
-   <span data-ttu-id="570fb-110">modification d'un fichier de liaison afin de personnaliser les liaisons pour différents environnements de déploiement.</span><span class="sxs-lookup"><span data-stu-id="570fb-110">Editing a binding file to customize the bindings for different deployment environments</span></span>  
  
 <span data-ttu-id="570fb-111">Pour obtenir la liste des tâches que vous devez effectuer dans les scénarios de déploiement d’application, consultez [déploiement d’applications BizTalk et la gestion des listes de contrôle](../core/biztalk-application-deployment-and-management-checklists.md).</span><span class="sxs-lookup"><span data-stu-id="570fb-111">For checklists of tasks that you need to perform in different application deployment scenarios, see [BizTalk Application Deployment and Management Checklists](../core/biztalk-application-deployment-and-management-checklists.md).</span></span> <span data-ttu-id="570fb-112">Pour plus d’informations sur les applications BizTalk et leur déploiement, consultez [gestion et déploiement d’applications BizTalk compréhension](../core/understanding-biztalk-application-deployment-and-management.md).</span><span class="sxs-lookup"><span data-stu-id="570fb-112">For background information on BizTalk applications and their deployment, see [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md).</span></span> <span data-ttu-id="570fb-113">Pour plus d’informations sur la création d’une application et de modifier en ajoutant ou supprimant des artefacts ou en ajoutant une référence à une autre application, consultez [création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md).</span><span class="sxs-lookup"><span data-stu-id="570fb-113">For information about creating an application and modifying it by adding or removing artifacts or adding a reference to another application, see [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md).</span></span> <span data-ttu-id="570fb-114">Pour plus d’informations sur le déploiement des assemblys BizTalk, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="570fb-114">For information about deploying BizTalk assemblies, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="570fb-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="570fb-115">In This Section</span></span>  
  
-   [<span data-ttu-id="570fb-116">Exportation de stratégies, les liaisons et les Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="570fb-116">Exporting BizTalk Applications, Bindings, and Policies</span></span>](../core/exporting-biztalk-applications-bindings-and-policies.md)  
  
-   [<span data-ttu-id="570fb-117">L’importation de stratégies, les liaisons et les Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="570fb-117">Importing BizTalk Applications, Bindings, and Policies</span></span>](../core/importing-biztalk-applications-bindings-and-policies.md)  
  
-   [<span data-ttu-id="570fb-118">Comment installer une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="570fb-118">How to Install a BizTalk Application</span></span>](../core/how-to-install-a-biztalk-application.md)  
  
-   [<span data-ttu-id="570fb-119">Surveillance de la progression de votre déploiement d’Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="570fb-119">Monitoring the Progress of Your BizTalk Application Deployment</span></span>](../core/monitoring-the-progress-of-your-biztalk-application-deployment.md)