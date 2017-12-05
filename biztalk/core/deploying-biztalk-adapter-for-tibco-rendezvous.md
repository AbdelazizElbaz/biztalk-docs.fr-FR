---
title: Importer des liaisons pour TIBCO Rendezvous | Documents Microsoft
description: "Déployer votre adaptateur BizTalk pour les applications de TIBCO Rendezvous à l’aide de la fonctionnalité d’importation des liaisons dans BizTalk Server"
ms.custom: 
ms.date: 10/24/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec5751a9-0a08-4cf8-a3ef-e51e488a4180
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dab62d7d7836a59c66329c2c58f7768bc481c036
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="deploy-tibco-rendezvous-ports-and-assemblies"></a><span data-ttu-id="2af13-103">Déployer des assemblys et des ports de TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="2af13-103">Deploy TIBCO Rendezvous ports and assemblies</span></span>
  
## <a name="overview"></a><span data-ttu-id="2af13-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="2af13-104">Overview</span></span>
<span data-ttu-id="2af13-105">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de dupliquer des ports et des assemblys sur un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="2af13-105">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> <span data-ttu-id="2af13-106">L'Assistant exporte la configuration des ports d'envoi/emplacements de réception dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="2af13-106">The wizard exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="2af13-107">Vous pouvez utiliser BizTalk pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2af13-107">You use BizTalk Server to do the following tasks:</span></span>  
  
-   <span data-ttu-id="2af13-108">Déployer ou supprimer des assemblys BizTalk Server dans une base de données de Configuration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="2af13-108">Deploy or remove BizTalk Server assemblies in a BizTalk Configuration database.</span></span>  
  
-   <span data-ttu-id="2af13-109">installation ou désinstallation des assemblys dans le GAC (Global Assembly Cache) ;</span><span class="sxs-lookup"><span data-stu-id="2af13-109">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
-   <span data-ttu-id="2af13-110">Importer ou exporter des informations de liaison d’assembly BizTalk Server vers et à partir de fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="2af13-110">Import or export BizTalk Server assembly binding information to and from binding files.</span></span>  
  
 <span data-ttu-id="2af13-111">Pour plus d’informations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="2af13-111">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2af13-112">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous requiert l'installation de Visual Studio sur un ordinateur (de développement) source.</span><span class="sxs-lookup"><span data-stu-id="2af13-112">Microsoft BizTalk Adapter for TIBCO Rendezvous only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="2af13-113">Visual Studio n'est pas requis sur l'ordinateur de production.</span><span class="sxs-lookup"><span data-stu-id="2af13-113">Visual Studio is not required on the production computer.</span></span>  

## <a name="confirm-your-setup"></a><span data-ttu-id="2af13-114">Vérifiez votre configuration</span><span class="sxs-lookup"><span data-stu-id="2af13-114">Confirm your setup</span></span>

<span data-ttu-id="2af13-115">Avant d’utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour importer un fichier de liaison, vérifiez que les dossiers pour les réponses existent et qu’ils sont identiques sur le nouvel ordinateur, ou vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="2af13-115">Before you use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to import a binding file, confirm that the folders for the responses exist, and that they are identical on the new computer, or you must edit the binding file.</span></span>  
  
## <a name="clean-the-target-computer"></a><span data-ttu-id="2af13-116">Nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="2af13-116">Clean the target computer</span></span>
<span data-ttu-id="2af13-117">Déploiement remplace la configuration d’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="2af13-117">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="2af13-118">Lorsque vous déployez un fichier de liaison (et un assembly) sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.</span><span class="sxs-lookup"><span data-stu-id="2af13-118">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
<span data-ttu-id="2af13-119">Avant d’importer, supprimer les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="2af13-119">Before you import, remove send ports and receive locations bound to the orchestration.</span></span>  
  
<span data-ttu-id="2af13-120">Si vous n’avez pas de Microsoft Visual Studio est installé sur l’ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts :</span><span class="sxs-lookup"><span data-stu-id="2af13-120">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
-   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="2af13-121">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="2af13-121">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
-   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="2af13-122">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="2af13-122">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
<span data-ttu-id="2af13-123">Par exemple, à une invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="2af13-123">For example, at a command prompt, run:</span></span>  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
  
## <a name="next-steps"></a><span data-ttu-id="2af13-124">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2af13-124">Next steps</span></span>
[<span data-ttu-id="2af13-125">Utiliser BizTalk Server des exceptions dans votre orchestration</span><span class="sxs-lookup"><span data-stu-id="2af13-125">Use BizTalk Server Exception Handling in your orchestration</span></span>](../core/using-biztalk-server-exception-handling4.md)  
[<span data-ttu-id="2af13-126">Dépanner</span><span class="sxs-lookup"><span data-stu-id="2af13-126">Troubleshoot</span></span>](../core/troubleshooting-tibco-rendezvous.md)