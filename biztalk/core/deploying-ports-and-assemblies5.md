---
title: "Déploiement de Ports et Assemblies5 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, deploying
- assemblies, deploying
- deployment, ports and assemblies
ms.assetid: 11d980c4-2502-4da2-b505-d7326aae619a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31df94e2a659fa29e6f21d2bd705de31da3c6b9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="183fc-102">Déploiement des ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="183fc-102">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="183fc-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de dupliquer des ports et des assemblys sur un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="183fc-103">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="183fc-104">Exporte la configuration des emplacements de réception/ports envoi dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="183fc-104"> exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="183fc-105">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="183fc-105">You use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to perform these tasks:</span></span>  
  
-   <span data-ttu-id="183fc-106">déploiement ou suppression des assemblys [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une base de données de configuration BizTalk ;</span><span class="sxs-lookup"><span data-stu-id="183fc-106">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database.</span></span>  
  
-   <span data-ttu-id="183fc-107">installation ou désinstallation des assemblys dans le GAC (Global Assembly Cache) ;</span><span class="sxs-lookup"><span data-stu-id="183fc-107">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
-   <span data-ttu-id="183fc-108">importation/exportation des informations de liaison des assemblys [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vers/à partir de fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="183fc-108">Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files.</span></span>  
  
 <span data-ttu-id="183fc-109">Pour plus d’informations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="183fc-109">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="183fc-110">L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise requiert l'installation de Visual Studio sur un ordinateur (de développement) source.</span><span class="sxs-lookup"><span data-stu-id="183fc-110">The Microsoft BizTalk Adapter for PeopleSoft Enterprise only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="183fc-111">Visual Studio n'est pas requis sur l'ordinateur de production.</span><span class="sxs-lookup"><span data-stu-id="183fc-111">Visual Studio is not required on the production computer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="183fc-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="183fc-112">In This Section</span></span>  
  
-   [<span data-ttu-id="183fc-113">L’importation de fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="183fc-113">Importing Binding Files</span></span>](../core/importing-binding-files1.md)  
  
-   [<span data-ttu-id="183fc-114">Limitations concernant le déploiement</span><span class="sxs-lookup"><span data-stu-id="183fc-114">Deployment Limitations</span></span>](../core/deployment-limitations3.md)