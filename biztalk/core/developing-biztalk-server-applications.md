---
title: "Développement d’Applications BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99b56f86-d8e4-4f4a-9ce9-9f476ba88ea8
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c71782556d896d0697b73b83e2966f304b77a3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-biztalk-server-applications"></a><span data-ttu-id="5229e-102">Développement des applications BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="5229e-102">Developing BizTalk Server Applications</span></span>
<span data-ttu-id="5229e-103">Cette section contient des informations à l'intention des développeurs chargés de créer des projets BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5229e-103">This section contains information for developers who are tasked with creating BizTalk projects.</span></span> <span data-ttu-id="5229e-104">Les projets sont créés à l'aide de l'environnement de conception du système de projet BizTalk, qui permet de concevoir, organiser et créer les divers éléments des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5229e-104">Projects are created using the BizTalk project System Design Environment, which allows you to design, organize, and build the various elements of BizTalk applications.</span></span> <span data-ttu-id="5229e-105">Les sections suivantes décrivent ce processus en détail.</span><span class="sxs-lookup"><span data-stu-id="5229e-105">The following sections describe this process in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5229e-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5229e-106">In This Section</span></span>  
  
-   [<span data-ttu-id="5229e-107">Outils de développement</span><span class="sxs-lookup"><span data-stu-id="5229e-107">Developer Tools</span></span>](../core/developer-tools.md)  
  
-   [<span data-ttu-id="5229e-108">À l’aide du moteur de messagerie BizTalk</span><span class="sxs-lookup"><span data-stu-id="5229e-108">Using the BizTalk Messaging Engine</span></span>](../core/using-the-biztalk-messaging-engine.md)  
  
-   [<span data-ttu-id="5229e-109">Création de schémas à l’aide de l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="5229e-109">Creating Schemas Using BizTalk Editor</span></span>](../core/creating-schemas-using-biztalk-editor.md)  
  
-   [<span data-ttu-id="5229e-110">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="5229e-110">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)  
  
-   [<span data-ttu-id="5229e-111">Création de Pipelines à l’aide du Concepteur de Pipeline</span><span class="sxs-lookup"><span data-stu-id="5229e-111">Creating Pipelines Using Pipeline Designer</span></span>](../core/creating-pipelines-using-pipeline-designer.md)  
  
-   [<span data-ttu-id="5229e-112">Création d’Orchestrations à l’aide du Concepteur d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="5229e-112">Creating Orchestrations Using Orchestration Designer</span></span>](../core/creating-orchestrations-using-orchestration-designer.md)  
  
-   [<span data-ttu-id="5229e-113">Création et utilisation des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="5229e-113">Creating and Using Business Rules</span></span>](../core/creating-and-using-business-rules.md)  
  
-   [<span data-ttu-id="5229e-114">Utilisation des Services Web</span><span class="sxs-lookup"><span data-stu-id="5229e-114">Using Web Services</span></span>](../core/using-web-services.md)  
  
-   [<span data-ttu-id="5229e-115">Utilisation des Services WCF</span><span class="sxs-lookup"><span data-stu-id="5229e-115">Using WCF Services</span></span>](../core/using-wcf-services.md)  
  
-   [<span data-ttu-id="5229e-116">Observations à caractère international pour la conception d’Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="5229e-116">International Considerations for Designing BizTalk Applications</span></span>](../core/international-considerations-for-designing-biztalk-applications.md)  
  
-   [<span data-ttu-id="5229e-117">Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="5229e-117">Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application</span></span>](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)  
  
-   [<span data-ttu-id="5229e-118">Création d’une Application de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="5229e-118">Creating a Single Sign-On Application</span></span>](../core/creating-a-single-sign-on-application.md)  
  
-   [<span data-ttu-id="5229e-119">Afficher des assemblys avec BizTalk Assembly Viewer</span><span class="sxs-lookup"><span data-stu-id="5229e-119">Viewing Assemblies with the BizTalk Assembly Viewer</span></span>](../core/viewing-assemblies-with-the-biztalk-assembly-viewer.md)  
  
-   [<span data-ttu-id="5229e-120">Implémentation de la sécurité de Message</span><span class="sxs-lookup"><span data-stu-id="5229e-120">Implementing Message Security</span></span>](../core/implementing-message-security.md)  
  
## <a name="see-also"></a><span data-ttu-id="5229e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5229e-121">See Also</span></span>  
 <span data-ttu-id="5229e-122">[Présentation de gestion et déploiement d’applications BizTalk](../core/understanding-biztalk-application-deployment-and-management.md) </span><span class="sxs-lookup"><span data-stu-id="5229e-122">[Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md) </span></span>  
 <span data-ttu-id="5229e-123">[Déploiement d’applications BizTalk et la gestion des listes de contrôle](../core/biztalk-application-deployment-and-management-checklists.md) </span><span class="sxs-lookup"><span data-stu-id="5229e-123">[BizTalk Application Deployment and Management Checklists](../core/biztalk-application-deployment-and-management-checklists.md) </span></span>  
 [<span data-ttu-id="5229e-124">Déploiement d’applications BizTalk et procédures pas à pas de gestion</span><span class="sxs-lookup"><span data-stu-id="5229e-124">BizTalk Application Deployment and Management Walkthroughs</span></span>](http://msdn.microsoft.com/library/5321f8e0-1e2a-4ac4-a4a2-fc244071bc5b)