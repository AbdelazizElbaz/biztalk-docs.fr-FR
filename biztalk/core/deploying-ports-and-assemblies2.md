---
title: "Déploiement de Ports et Assemblies2 | Documents Microsoft"
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
ms.assetid: abbc1391-2b90-42a5-a747-416bc517bb39
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74c3cc840b9dca222d1b55e9277b1ffd6cf326db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="22f11-102">Déploiement des ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="22f11-102">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="22f11-103">Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez dupliquer des ports et des assemblys sur un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="22f11-103">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="22f11-104">configuration de l’emplacement de réception/ports d’envoi exporte dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="22f11-104"> exports send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="22f11-105">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="22f11-105">You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to do the following tasks:</span></span>  
  
-   <span data-ttu-id="22f11-106">déploiement ou suppression des assemblys [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une base de données de configuration BizTalk ;</span><span class="sxs-lookup"><span data-stu-id="22f11-106">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database.</span></span>  
  
-   <span data-ttu-id="22f11-107">installation ou désinstallation des assemblys dans le GAC (Global Assembly Cache) ;</span><span class="sxs-lookup"><span data-stu-id="22f11-107">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
-   <span data-ttu-id="22f11-108">importation/exportation des informations de liaison des assemblys BizTalk vers/à partir de fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="22f11-108">Import or export BizTalk assembly binding information to and from binding files.</span></span>  
  
 <span data-ttu-id="22f11-109">Pour plus d’informations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="22f11-109">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22f11-110">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service requiert l'installation de Visual Studio sur un ordinateur (de développement) source.</span><span class="sxs-lookup"><span data-stu-id="22f11-110">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="22f11-111">Visual Studio n'est pas requis sur l'ordinateur de production.</span><span class="sxs-lookup"><span data-stu-id="22f11-111">Visual Studio is not required on the production computer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22f11-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="22f11-112">In This Section</span></span>  
  
-   [<span data-ttu-id="22f11-113">Vérification de la configuration du déploiement</span><span class="sxs-lookup"><span data-stu-id="22f11-113">Verifying the Deployment Setup</span></span>](../core/verifying-the-deployment-setup2.md)  
  
-   [<span data-ttu-id="22f11-114">Comment nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="22f11-114">How to Clean the Target Computer</span></span>](../core/how-to-clean-the-target-computer2.md)  
  
-   [<span data-ttu-id="22f11-115">Limitations concernant le déploiement</span><span class="sxs-lookup"><span data-stu-id="22f11-115">Deployment Limitations</span></span>](../core/deployment-limitations1.md)