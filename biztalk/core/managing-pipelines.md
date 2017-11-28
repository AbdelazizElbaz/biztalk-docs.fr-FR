---
title: "Gérer les pipelines | Documents Microsoft"
description: "Liens rapides pour activer le suivi et les propriétés du pipeline sur un port d’envoi ou emplacement de réception dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d60b54e0-0a5a-4264-b0e5-96bb187d782b
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0edfbdd97e134abc6f153acf136ff62a979f8b0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-pipelines"></a><span data-ttu-id="348de-103">Gestion des pipelines</span><span class="sxs-lookup"><span data-stu-id="348de-103">Managing Pipelines</span></span>

## <a name="overview"></a><span data-ttu-id="348de-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="348de-104">Overview</span></span>
<span data-ttu-id="348de-105">Cette section fournit des instructions sur la gestion des pipelines dans un groupe BizTalk à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="348de-105">This section provides instructions on using the BizTalk Server Administration console to manage the pipelines in a BizTalk group.</span></span> <span data-ttu-id="348de-106">Vous pouvez configurer le suivi des événements et des messages, ainsi que les propriétés de pipeline d'un emplacement de réception ou port d'envoi spécifique.</span><span class="sxs-lookup"><span data-stu-id="348de-106">You can configure tracking for events and messages as well as configure pipeline properties for a specific send port or receive location.</span></span>  
  
 <span data-ttu-id="348de-107">Les pipelines effectuent des actions sur les messages entrants et sortants, telles que la conversion de ces messages d'un format natif en XML, le chiffrement ou le déchiffrement de données, la promotion de propriétés, etc.</span><span class="sxs-lookup"><span data-stu-id="348de-107">Pipelines perform actions on incoming and outgoing messages, such as transforming them from a native format into XML, encrypting or unencrypting data, performing property promotion, and so on.</span></span>  
  
 <span data-ttu-id="348de-108">Vous ne pouvez pas ajouter un pipeline de manière individuelle à une application. Son ajout s'effectue dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="348de-108">You cannot add a pipeline to an application individually; a pipeline is added to an application as follows:</span></span>  
  
-   <span data-ttu-id="348de-109">Lorsque vous ajoutez un assembly BizTalk contenant un pipeline à l’application, comme décrit dans [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="348de-109">When you add a BizTalk assembly containing a pipeline to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
-   <span data-ttu-id="348de-110">Lorsque vous importez un fichier .msi dans une application qui comprend un assembly BizTalk contenant un pipeline, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="348de-110">When you import an .msi file into an application that includes a BizTalk assembly containing a pipeline, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="348de-111">Lorsqu’un développeur déploie dans une application un assembly contenant un pipeline à partir de Visual Studio, comme décrit dans [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="348de-111">When a developer deploys into an application an assembly containing a pipeline from Visual Studio, as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  
  
 <span data-ttu-id="348de-112">Pour des informations générales sur les pipelines, consultez [Pipelines](../core/pipelines.md).</span><span class="sxs-lookup"><span data-stu-id="348de-112">For background information about pipelines, see [Pipelines](../core/pipelines.md).</span></span> <span data-ttu-id="348de-113">Pour plus d’informations sur le développement de pipelines, consultez [création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md).</span><span class="sxs-lookup"><span data-stu-id="348de-113">For information about developing pipelines, see [Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="348de-114">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="348de-114">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="348de-115">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="348de-115">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="348de-116">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="348de-116">Next steps</span></span>
  
-   [<span data-ttu-id="348de-117">Configurer le suivi d’un Pipeline</span><span class="sxs-lookup"><span data-stu-id="348de-117">Configure Tracking for a Pipeline</span></span>](../core/how-to-configure-tracking-for-a-pipeline.md)  
  
-   [<span data-ttu-id="348de-118">Configurer les propriétés de Pipeline par Instance pour un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="348de-118">Configure Per-Instance Pipeline Properties for a Send Port</span></span>](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md)  
  
-   [<span data-ttu-id="348de-119">Configurer les propriétés de Pipeline par instance d’un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="348de-119">Configure Per-instance Pipeline Properties for a Receive Location</span></span>](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md)