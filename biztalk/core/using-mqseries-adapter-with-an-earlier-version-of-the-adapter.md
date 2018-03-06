---
redirect_url: /biztalk/core/mqseries-adapter-deployment-options
redirect_document_id: 
ROBOTS: NOINDEX
ms.openlocfilehash: 2aa74be2d86bcb8f32661fdcf06727eb6391861d
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="using-mqseries-adapter-with-an-earlier-version-of-the-adapter"></a><span data-ttu-id="6c3f8-101">À l’aide de l’adaptateur MQSeries avec une Version antérieure de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="6c3f8-101">Using MQSeries Adapter with an Earlier Version of the Adapter</span></span>
<span data-ttu-id="6c3f8-102">Les différentes versions de BizTalk Server de l’adaptateur MQSeries peuvent fonctionner avec le même serveur distant WebSphere MQ sur Windows.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-102">The different BizTalk Server versions of the MQSeries adapter can all work with the same remote WebSphere MQ Server on Windows.</span></span> <span data-ttu-id="6c3f8-103">Ceci est dû au fait que les versions suivantes des applications COM+ utilisées par l'adaptateur MQSeries peuvent coexister sur le même ordinateur MQSeries WebSphere :</span><span class="sxs-lookup"><span data-stu-id="6c3f8-103">This is possible because the following versions of the COM+ applications used with the MQSeries adapter can coexist on the same WebSphere MQSeries computer:</span></span>  
  
-   <span data-ttu-id="6c3f8-104">**L’application MQSAgent (MQSAgent2) COM +** utilisé avec l’adaptateur MQSeries (BizTalk Server 2006)</span><span class="sxs-lookup"><span data-stu-id="6c3f8-104">**MQSAgent (MQSAgent2) COM+ application** used with the MQSeries Adapter (BizTalk Server 2006)</span></span> 
  
-   <span data-ttu-id="6c3f8-105">**Application MQSAgent COM +** utilisé avec l’adaptateur MQSeries (BizTalk Server 2004)</span><span class="sxs-lookup"><span data-stu-id="6c3f8-105">**MQSAgent COM+ application** used with the MQSeries Adapter (BizTalk Server 2004)</span></span>  
  
-   <span data-ttu-id="6c3f8-106">**Application MQHelper COM +** utilisé avec l’adaptateur MQSeries (BizTalk Server 2002)</span><span class="sxs-lookup"><span data-stu-id="6c3f8-106">**MQHelper COM+ application** used with the MQSeries Adapter (BizTalk Server 2002)</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="6c3f8-107">Lors de la configuration d'une installation côte à côte de ces applications COM+, assurez-vous qu'aucune d'entre elles ne soit configurée de manière à utiliser les mêmes files d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-107">When configuring a side-by-side installation of these COM+ applications, ensure that none of these COM+ applications are configured to use the same MQSeries queues.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6c3f8-108">Installation côte à côte de la version de BizTalk Server 2006 de l’application COM + adaptateur MQSeries avec une version antérieure de l’application COM + MQSeries Adapter n’est possible que si une version antérieure de BizTalk Server n’est pas installée sur le WebSphere Ordinateur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-108">Side-by-side installation of the BizTalk Server 2006 version of the MQSeries Adapter COM+ application with an earlier version of the MQSeries Adapter COM+ application is only supported if an earlier version of BizTalk Server is not installed on the WebSphere MQSeries computer.</span></span>  
  
### <a name="to-install-the-biztalk-server-2006-version-of-the-mqseries-adapter-com-application-on-a-websphere-mqseries-computer-that-is-running-an-earlier-version-of-the-mqseries-adapter-com-application"></a><span data-ttu-id="6c3f8-109">Pour installer la version BizTalk Server 2006 de l'application COM+ de l'adaptateur MQSeries sur un ordinateur MQSeries WebSphere exécutant une version antérieure de cette application</span><span class="sxs-lookup"><span data-stu-id="6c3f8-109">To install the BizTalk Server 2006 version of the MQSeries Adapter COM+ application on a WebSphere MQSeries computer that is running an earlier version of the MQSeries Adapter COM+ application</span></span>  
  
1.  <span data-ttu-id="6c3f8-110">Exécutez le bootstrap.msi dans le répertoire \Platform\BootStrap\ du CD BizTalk Server 2006 pour copier les fichiers de dépendances MSVCR80.dll et MSVCP80.dll sur l’ordinateur WebSphere MQSeries.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-110">Run the Bootstrap.msi from the \Platform\BootStrap\ directory of the BizTalk Server 2006 CD to copy the dependency files MSVCR80.dll and MSVCP80.dll to the WebSphere MQSeries computer.</span></span>  
  
2.  <span data-ttu-id="6c3f8-111">Copiez le fichier MQSAgent.dll à partir du répertoire \Msi\Program Files\ sur le CD-ROM de BizTalk Server 2006 à l’ordinateur WebSphere MQSeries.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-111">Copy the file MQSAgent.dll from the \Msi\Program Files\ directory on the BizTalk Server 2006 CD to the WebSphere MQSeries computer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c3f8-112">Si vous envisagez d'utiliser l'utilitaire de suivi MQSAgent, copiez également le fichier MQSTrace.cmd situé dans le même répertoire vers l'ordinateur MQSeries WebSphere.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-112">Also copy the file MQSTrace.cmd from this directory to the WebSphere MQSeries computer if you plan on using the MQSAgent tracing utility.</span></span> <span data-ttu-id="6c3f8-113">Pour plus d’informations sur l’application MQSAgent utilitaire de suivi consultez [analyse des erreurs de l’adaptateur MQSeries avec les outils de suivi](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6c3f8-113">For more information about the MQSAgent tracing utility see [Analyzing MQSeries Adapter Errors with the Trace Tools](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md).</span></span>  
  
3.  <span data-ttu-id="6c3f8-114">Enregistrez manuellement les composants dans le fichier MQSAgent.dll en exécutant la commande regsvr32 mqsagent.dll sur l'ordinateur MQSeries WebSphere :</span><span class="sxs-lookup"><span data-stu-id="6c3f8-114">Manually register the components in MQSAgent.dll by running regsvr32 mqsagent.dll on the WebSphere MQSeries computer:</span></span>  
  
    ```  
    regsvr32 MQSAgent.dll  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="6c3f8-115">Exécutez cette commande à partir du répertoire dans lequel vous avez copié le fichier MQSAgent.dll.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-115">Run this command from the same directory that you copied MQSAgent.dll to.</span></span>  
  
4.  <span data-ttu-id="6c3f8-116">Créez une application COM+ pour les composants MQSAgent :</span><span class="sxs-lookup"><span data-stu-id="6c3f8-116">Create a new COM+ application for the MQSAgent components:</span></span>  
  
    -   <span data-ttu-id="6c3f8-117">Cliquez sur Applications COM +, cliquez sur **nouveau**, **Application** pour afficher la **Assistant Installation d’applications COM +** et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-117">Right-click COM+ Applications, click **New**, **Application** to display the **COM+ Application Install Wizard** and click **Next**.</span></span>  
  
    -   <span data-ttu-id="6c3f8-118">Cliquez sur **créer une application vide**.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-118">Click **Create an empty application**.</span></span>  
  
    -   <span data-ttu-id="6c3f8-119">Entrez le nom **MQSAgent2**, laissez l’option par défaut **application serveur** activé, puis cliquez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-119">Enter the name **MQSAgent2**, leave the default option for **Server application** enabled and click **Next**.</span></span>  
  
    -   <span data-ttu-id="6c3f8-120">Sélectionnez l’option de **cet utilisateur**, entrez les informations de compte approprié, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-120">Select the option for **This user**, enter the appropriate account information and click **Next**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6c3f8-121">Ce compte doit avoir reçu les autorisations de connexion, de placement et/ou d'obtention pour les files d'attente IBM WebSphere MQ appropriées.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-121">This account should have connect and put and/or get permissions on the appropriate IBM WebSphere MQ queues.</span></span>  
  
    -   <span data-ttu-id="6c3f8-122">Cliquez sur **suivant** sur l’ajout de **les rôles d’Application** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-122">Click **Next** on the Add **Application Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="6c3f8-123">Cliquez sur **suivant** sur la **ajouter des utilisateurs aux rôles** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-123">Click **Next** on the **Add Users to Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="6c3f8-124">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-124">Click **Finish**.</span></span>  
  
5.  <span data-ttu-id="6c3f8-125">Ajoutez les composants MQSAgent.dll à l'application MQSAgent2 COM+ :</span><span class="sxs-lookup"><span data-stu-id="6c3f8-125">Add the MQSAgent.dll components to the MQSAgent2 COM+ application:</span></span>  
  
    -   <span data-ttu-id="6c3f8-126">Cliquez pour développer le **MQSAgent2** l’Application COM +.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-126">Click to expand the **MQSAgent2** COM+ Application.</span></span>  
  
    -   <span data-ttu-id="6c3f8-127">Avec le bouton droit **composants** et cliquez sur **nouveau**, **composant** pour lancer l’Assistant Installation du composant COM +, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-127">Right-click **Components** and click **New**, **Component** to launch the COM+ Component Install Wizard and then click **Next**.</span></span>  
  
    -   <span data-ttu-id="6c3f8-128">Cliquez sur **installer de nouveaux composants**, recherchez le fichier MQSAgent.dll, puis sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-128">Click **Install New Components**, browse to the file MQSAgent.dll and then click **Open**.</span></span>  
  
    -   <span data-ttu-id="6c3f8-129">Cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="6c3f8-129">Click **Next**, and then click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c3f8-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c3f8-130">See Also</span></span>  
 [<span data-ttu-id="6c3f8-131">Utilisation de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="6c3f8-131">Using the MQSeries Adapter</span></span>](../core/using-the-mqseries-adapter.md)