---
title: "Déploiement de Ports et Assemblies1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, deploying
- deployment, ports
- deployment, assemblies
- assemblies, deploying
ms.assetid: e259f7fe-c443-4015-a630-f08220e5437a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf2515cd5ee80f62a55e0b26b33bb93c3685ce6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="349dd-102">Déploiement des ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="349dd-102">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="349dd-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de dupliquer des ports et des assemblys sur un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="349dd-103">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> <span data-ttu-id="349dd-104">L'Assistant exporte la configuration des ports d'envoi/emplacements de réception dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="349dd-104">The wizard exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="349dd-105">Vous pouvez utiliser BizTalk pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="349dd-105">You use BizTalk Server to do the following tasks:</span></span>  
  
-   <span data-ttu-id="349dd-106">Déployer ou supprimer des assemblys BizTalk Server dans une base de données de Configuration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="349dd-106">Deploy or remove BizTalk Server assemblies in a BizTalk Configuration database.</span></span>  
  
-   <span data-ttu-id="349dd-107">installation ou désinstallation des assemblys dans le GAC (Global Assembly Cache) ;</span><span class="sxs-lookup"><span data-stu-id="349dd-107">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
-   <span data-ttu-id="349dd-108">Importer ou exporter des informations de liaison d’assembly BizTalk Server vers et à partir de fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="349dd-108">Import or export BizTalk Server assembly binding information to and from binding files.</span></span>  
  
 <span data-ttu-id="349dd-109">Pour plus d’informations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="349dd-109">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="349dd-110">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous requiert l'installation de Visual Studio sur un ordinateur (de développement) source.</span><span class="sxs-lookup"><span data-stu-id="349dd-110">Microsoft BizTalk Adapter for TIBCO Rendezvous only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="349dd-111">Visual Studio n'est pas requis sur l'ordinateur de production.</span><span class="sxs-lookup"><span data-stu-id="349dd-111">Visual Studio is not required on the production computer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="349dd-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="349dd-112">In This Section</span></span>  
  
-   [<span data-ttu-id="349dd-113">Vérification de la configuration du déploiement</span><span class="sxs-lookup"><span data-stu-id="349dd-113">Verifying the Deployment Setup</span></span>](../core/verifying-the-deployment-setup3.md)  
  
-   [<span data-ttu-id="349dd-114">Comment nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="349dd-114">How to Clean the Target Computer</span></span>](../core/how-to-clean-the-target-computer1.md)