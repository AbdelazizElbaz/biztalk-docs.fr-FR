---
title: "Scénario : Déploiement d’une nouvelle Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, applications
- applications, deploying
- deploying [applications], examples
- applications, examples
- examples, deploying
ms.assetid: 6d34a626-9fd4-4c33-a067-b66333eec01f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 938767237d21b74829c786bdd5d57c7d9df15c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-deploying-a-new-application"></a><span data-ttu-id="df424-102">Scénario : Déploiement d’une nouvelle Application</span><span class="sxs-lookup"><span data-stu-id="df424-102">Scenario: Deploying a New Application</span></span>
<span data-ttu-id="df424-103">Cette rubrique décrit un scénario de déploiement d'une application dans un nouvel environnement où elle n'a encore jamais été déployée; par exemple le déploiement d'une application configurée dans un environnement intermédiaire vers un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="df424-103">This topic describes the scenario of deploying an application into a new environment where it has not been deployed before; for example, deploying an application that has been configured in a staging environment into a production environment.</span></span>  
  
 <span data-ttu-id="df424-104">Comme décrit dans [le processus de déploiement d’Application](../core/the-application-deployment-process.md), lorsque vous souhaitez déplacer une application d’un environnement à un autre, vous exportez l’application dans un fichier .msi.</span><span class="sxs-lookup"><span data-stu-id="df424-104">As described in [The Application Deployment Process](../core/the-application-deployment-process.md), when you want to move an application from one environment to another, you export the application into an .msi file.</span></span> <span data-ttu-id="df424-105">Vous importez ensuite le fichier .msi dans le groupe BizTalk au sein du nouvel environnement.</span><span class="sxs-lookup"><span data-stu-id="df424-105">You then import the .msi file into the BizTalk group in the new environment.</span></span> <span data-ttu-id="df424-106">Vous installez également l'application sur les ordinateurs du groupe qui doivent l'exécuter.</span><span class="sxs-lookup"><span data-stu-id="df424-106">You also install the application on the computers in that group that will run the application.</span></span> <span data-ttu-id="df424-107">Pour qu'elle puisse fonctionner, vous devez installer l'application sur chaque ordinateur qui devra l'exécuter et démarrer l'application.</span><span class="sxs-lookup"><span data-stu-id="df424-107">Before it can begin functioning, you must install the application on each computer that will run it and also start the application.</span></span>  
  
 <span data-ttu-id="df424-108">Dans le schéma suivant, Application1 est importée à partir d'un fichier .msi dans le groupe BizTalk B.</span><span class="sxs-lookup"><span data-stu-id="df424-108">In the following diagram, Application1 is imported from an .msi file into BizTalk Group B.</span></span>  
  
 <span data-ttu-id="df424-109">![Déploiement d’une application BizTalk](../core/media/deployapplication.gif "DeployApplication")</span><span class="sxs-lookup"><span data-stu-id="df424-109">![Deploying a BizTalk application](../core/media/deployapplication.gif "DeployApplication")</span></span>  
  
 <span data-ttu-id="df424-110">Ceci importe les artefacts dans les différentes bases de données de BizTalk Server, comme suit :</span><span class="sxs-lookup"><span data-stu-id="df424-110">This imports artifacts into the various BizTalk Server databases as follows:</span></span>  
  
-   <span data-ttu-id="df424-111">L'assembly BizTalk, l'assembly .NET, les liaisons, le fichier de liaisons, le modèle BAM, le composant COM, le certificat et le fichier texte sont tous ajoutés à la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="df424-111">The BizTalk assembly, .NET assembly, bindings, binding file, BAM template, COM component, certificate, and text file are all added to the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="df424-112">La stratégie et le vocabulaire sont ajoutés à la base de données du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="df424-112">The policy and vocabulary are added to the Rule Engine database.</span></span>  
  
-   <span data-ttu-id="df424-113">Le modèle BAM et le fichier de définition d'analyse BAM sont tous deux ajoutés à la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="df424-113">The BAM template and BAM definition file are both added to the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="df424-114">Chacun de ces artéfacts est également associé à Application1 dans la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="df424-114">Each of these artifacts is also associated with Application1 in the BizTalk Management database.</span></span>  
  
 <span data-ttu-id="df424-115">L'application est aussi installée sur un ordinateur local à partir du fichier .msi.</span><span class="sxs-lookup"><span data-stu-id="df424-115">The application is also installed on a local computer from the .msi file.</span></span> <span data-ttu-id="df424-116">Ceci installe différents artefacts inclus dans le fichier .msi, comme suit :</span><span class="sxs-lookup"><span data-stu-id="df424-116">This installs various artifacts that are included in the .msi file, as follows:</span></span>  
  
-   <span data-ttu-id="df424-117">Le répertoire virtuel, appelé VirtualDirectory, est créé dans la métabase Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="df424-117">The virtual directory, named VirtualDirectory, is created in the Internet Information Services (IIS) metabase.</span></span>  
  
-   <span data-ttu-id="df424-118">Le certificat est ajouté au magasin de certificats local.</span><span class="sxs-lookup"><span data-stu-id="df424-118">The certificate is added to the local certificate store.</span></span>  
  
-   <span data-ttu-id="df424-119">Le fichier texte et le composant COM sont copiés dans le système de fichiers local.</span><span class="sxs-lookup"><span data-stu-id="df424-119">The text file and COM component are copied to the local file system.</span></span>  
  
-   <span data-ttu-id="df424-120">L'assembly BizTalk et l'assembly .NET sont ajoutés au GAC (Global Assembly Cache), si cette option de déploiement a été sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="df424-120">The BizTalk assembly and .NET assembly are added to the global assembly cache (GAC), if this deployment option was selected for them.</span></span>  
  
-   <span data-ttu-id="df424-121">L'assembly .NET et le composant COM sont ajoutés au registre Windows, si cette option de déploiement a été sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="df424-121">The .NET assembly and COM component are added to the Windows registry, if that deployment option was selected for them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df424-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df424-122">See Also</span></span>  
 <span data-ttu-id="df424-123">[Déploiement d’applications et scénarios de gestion](../core/application-deployment-and-management-scenarios.md) </span><span class="sxs-lookup"><span data-stu-id="df424-123">[Application Deployment and Management Scenarios](../core/application-deployment-and-management-scenarios.md) </span></span>  
 [<span data-ttu-id="df424-124">Déploiement d’Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="df424-124">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)