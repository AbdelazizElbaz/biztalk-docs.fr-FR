---
title: "À l’aide de l’adaptateur MQSeries avec une Version antérieure de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MQSeries adapters, compatibility
ms.assetid: 278a13ff-8e46-4af4-a76e-b6d4aad5b768
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba635b9bc4569f17418fc925c54c64d0fdc67461
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-mqseries-adapter-with-an-earlier-version-of-the-adapter"></a><span data-ttu-id="e3210-102">À l’aide de l’adaptateur MQSeries avec une Version antérieure de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="e3210-102">Using MQSeries Adapter with an Earlier Version of the Adapter</span></span>
<span data-ttu-id="e3210-103">Sous Windows, les versions [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)], [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] et [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] de l'adaptateur MQSeries sont toutes compatibles avec le même serveur distant WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="e3210-103">The [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)], [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)], and [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] versions of the MQSeries adapter can all work with the same remote WebSphere MQ Server on Windows.</span></span> <span data-ttu-id="e3210-104">Ceci est dû au fait que les versions suivantes des applications COM+ utilisées par l'adaptateur MQSeries peuvent coexister sur le même ordinateur MQSeries WebSphere :</span><span class="sxs-lookup"><span data-stu-id="e3210-104">This is possible because the following versions of the COM+ applications used with the MQSeries adapter can coexist on the same WebSphere MQSeries computer:</span></span>  
  
-   <span data-ttu-id="e3210-105">**L’application MQSAgent (MQSAgent2) COM +** utilisé avec l’adaptateur MQSeries pour [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3210-105">**MQSAgent (MQSAgent2) COM+ application** used with the MQSeries Adapter for [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)].</span></span>  
  
-   <span data-ttu-id="e3210-106">**Application MQSAgent COM +** utilisé avec l’adaptateur MQSeries pour [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3210-106">**MQSAgent COM+ application** used with the MQSeries Adapter for [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)].</span></span>  
  
-   <span data-ttu-id="e3210-107">**Application MQHelper COM +** utilisé avec l’adaptateur MQSeries pour [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3210-107">**MQHelper COM+ application** used with the MQSeries Adapter for [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3210-108">Lors de la configuration d'une installation côte à côte de ces applications COM+, assurez-vous qu'aucune d'entre elles ne soit configurée de manière à utiliser les mêmes files d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="e3210-108">When configuring a side-by-side installation of these COM+ applications, ensure that none of these COM+ applications are configured to use the same MQSeries queues.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e3210-109">Une installation côte à côte de la version [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] de l'application COM+ de l'adaptateur MQSeries avec une version antérieure est uniquement prise en charge si une version antérieure de BizTalk Server n'est pas installée sur l'ordinateur MQSeries WebSphere.</span><span class="sxs-lookup"><span data-stu-id="e3210-109">Side-by-side installation of the [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] version of the MQSeries Adapter COM+ application with an earlier version of the MQSeries Adapter COM+ application is only supported if an earlier version of BizTalk Server is not installed on the WebSphere MQSeries computer.</span></span>  
  
### <a name="to-install-the-biztalk-server-2006-version-of-the-mqseries-adapter-com-application-on-a-websphere-mqseries-computer-that-is-running-an-earlier-version-of-the-mqseries-adapter-com-application"></a><span data-ttu-id="e3210-110">Pour installer la version BizTalk Server 2006 de l'application COM+ de l'adaptateur MQSeries sur un ordinateur MQSeries WebSphere exécutant une version antérieure de cette application</span><span class="sxs-lookup"><span data-stu-id="e3210-110">To install the BizTalk Server 2006 version of the MQSeries Adapter COM+ application on a WebSphere MQSeries computer that is running an earlier version of the MQSeries Adapter COM+ application</span></span>  
  
1.  <span data-ttu-id="e3210-111">Exécutez le fichier Bootstrap.msi se trouvant dans le répertoire \Platform\BootStrap\ du CD [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] afin de copier les fichiers de dépendances MSVCR80.dll et MSVCP80.dll sur l'ordinateur MQSeries WebSphere.</span><span class="sxs-lookup"><span data-stu-id="e3210-111">Run the Bootstrap.msi from the \Platform\BootStrap\ directory of the [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] CD to copy the dependency files MSVCR80.dll and MSVCP80.dll to the WebSphere MQSeries computer.</span></span>  
  
2.  <span data-ttu-id="e3210-112">Copiez le fichier MQSAgent.dll situé dans le répertoire \Msi\Program Files\ du CD [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] sur l'ordinateur MQSeries WebSphere.</span><span class="sxs-lookup"><span data-stu-id="e3210-112">Copy the file MQSAgent.dll from the \Msi\Program Files\ directory on the [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] CD to the WebSphere MQSeries computer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3210-113">Si vous envisagez d'utiliser l'utilitaire de suivi MQSAgent, copiez également le fichier MQSTrace.cmd situé dans le même répertoire vers l'ordinateur MQSeries WebSphere.</span><span class="sxs-lookup"><span data-stu-id="e3210-113">Also copy the file MQSTrace.cmd from this directory to the WebSphere MQSeries computer if you plan on using the MQSAgent tracing utility.</span></span> <span data-ttu-id="e3210-114">Pour plus d’informations sur l’application MQSAgent utilitaire de suivi consultez [analyse des erreurs de l’adaptateur MQSeries avec les outils de suivi](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md).</span><span class="sxs-lookup"><span data-stu-id="e3210-114">For more information about the MQSAgent tracing utility see [Analyzing MQSeries Adapter Errors with the Trace Tools](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md).</span></span>  
  
3.  <span data-ttu-id="e3210-115">Enregistrez manuellement les composants dans le fichier MQSAgent.dll en exécutant la commande regsvr32 mqsagent.dll sur l'ordinateur MQSeries WebSphere :</span><span class="sxs-lookup"><span data-stu-id="e3210-115">Manually register the components in MQSAgent.dll by running regsvr32 mqsagent.dll on the WebSphere MQSeries computer:</span></span>  
  
    ```  
    regsvr32 MQSAgent.dll  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e3210-116">Exécutez cette commande à partir du répertoire dans lequel vous avez copié le fichier MQSAgent.dll.</span><span class="sxs-lookup"><span data-stu-id="e3210-116">Run this command from the same directory that you copied MQSAgent.dll to.</span></span>  
  
4.  <span data-ttu-id="e3210-117">Créez une application COM+ pour les composants MQSAgent :</span><span class="sxs-lookup"><span data-stu-id="e3210-117">Create a new COM+ application for the MQSAgent components:</span></span>  
  
    -   <span data-ttu-id="e3210-118">Cliquez sur Applications COM +, cliquez sur **nouveau**, **Application** pour afficher la **Assistant Installation d’applications COM +** et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="e3210-118">Right-click COM+ Applications, click **New**, **Application** to display the **COM+ Application Install Wizard** and click **Next**.</span></span>  
  
    -   <span data-ttu-id="e3210-119">Cliquez sur **créer une application vide**.</span><span class="sxs-lookup"><span data-stu-id="e3210-119">Click **Create an empty application**.</span></span>  
  
    -   <span data-ttu-id="e3210-120">Entrez le nom **MQSAgent2**, laissez l’option par défaut **application serveur** activé, puis cliquez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="e3210-120">Enter the name **MQSAgent2**, leave the default option for **Server application** enabled and click **Next**.</span></span>  
  
    -   <span data-ttu-id="e3210-121">Sélectionnez l’option de **cet utilisateur**, entrez les informations de compte approprié, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="e3210-121">Select the option for **This user**, enter the appropriate account information and click **Next**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="e3210-122">Ce compte doit avoir reçu les autorisations de connexion, de placement et/ou d'obtention pour les files d'attente IBM WebSphere MQ appropriées.</span><span class="sxs-lookup"><span data-stu-id="e3210-122">This account should have connect and put and/or get permissions on the appropriate IBM WebSphere MQ queues.</span></span>  
  
    -   <span data-ttu-id="e3210-123">Cliquez sur **suivant** sur l’ajout de **les rôles d’Application** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e3210-123">Click **Next** on the Add **Application Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="e3210-124">Cliquez sur **suivant** sur la **ajouter des utilisateurs aux rôles** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e3210-124">Click **Next** on the **Add Users to Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="e3210-125">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="e3210-125">Click **Finish**.</span></span>  
  
5.  <span data-ttu-id="e3210-126">Ajoutez les composants MQSAgent.dll à l'application MQSAgent2 COM+ :</span><span class="sxs-lookup"><span data-stu-id="e3210-126">Add the MQSAgent.dll components to the MQSAgent2 COM+ application:</span></span>  
  
    -   <span data-ttu-id="e3210-127">Cliquez pour développer le **MQSAgent2** l’Application COM +.</span><span class="sxs-lookup"><span data-stu-id="e3210-127">Click to expand the **MQSAgent2** COM+ Application.</span></span>  
  
    -   <span data-ttu-id="e3210-128">Avec le bouton droit **composants** et cliquez sur **nouveau**, **composant** pour lancer l’Assistant Installation du composant COM +, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="e3210-128">Right-click **Components** and click **New**, **Component** to launch the COM+ Component Install Wizard and then click **Next**.</span></span>  
  
    -   <span data-ttu-id="e3210-129">Cliquez sur **installer de nouveaux composants**, recherchez le fichier MQSAgent.dll, puis sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="e3210-129">Click **Install New Components**, browse to the file MQSAgent.dll and then click **Open**.</span></span>  
  
    -   <span data-ttu-id="e3210-130">Cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="e3210-130">Click **Next**, and then click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3210-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3210-131">See Also</span></span>  
 [<span data-ttu-id="e3210-132">À l’aide de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="e3210-132">Using the MQSeries Adapter</span></span>](../core/using-the-mqseries-adapter.md)