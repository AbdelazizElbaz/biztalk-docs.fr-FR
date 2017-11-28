---
title: "Étape 7 : Création et déploiement de l’exemple du Kit de développement DoubleAction | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double action tutorial, building solutions
- deploying, solutions
- building solutions
- double action tutorial, deploying solutions
ms.assetid: f67f8aee-1004-48ee-a6fd-881097382888
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b503f423d736d9c5f08c7d04a84110a85564d11d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-building-and-deploying-the-doubleaction-sdk-sample"></a><span data-ttu-id="b898c-102">Étape 7 : Création et déploiement de l’exemple du Kit de développement DoubleAction</span><span class="sxs-lookup"><span data-stu-id="b898c-102">Step 7: Building and Deploying the DoubleAction SDK Sample</span></span>
<span data-ttu-id="b898c-103">L'exemple DoubleAction.odx montre comment implémenter une orchestration pour générer automatiquement des réponses pour les processus PIP (Partner Interface Processes) double action 0C2, 0C4, 3A2 et 3A4.</span><span class="sxs-lookup"><span data-stu-id="b898c-103">The DoubleAction.odx sample shows how to implement an orchestration to generate responses automatically for the double-action Partner Interface Processes (PIPs) 0C2, 0C4, 3A2, and 3A4.</span></span> <span data-ttu-id="b898c-104">Vous pouvez étendre cet exemple de projet pour prendre en charge des PIP double action supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="b898c-104">You can extend this sample project to support additional double-action PIPs.</span></span>  
  
 <span data-ttu-id="b898c-105">Cet exemple vous permet d'envoyer une réponse automatique à Fabrikam chaque fois que Fabrikam effectue une demande à l'aide de l'un des quatre PIP.</span><span class="sxs-lookup"><span data-stu-id="b898c-105">You use this sample to send a response automatically to Fabrikam whenever Fabrikam makes a request using any one of the four PIPs.</span></span>  
  
### <a name="to-build-and-initialize-the-doubleaction-sample"></a><span data-ttu-id="b898c-106">Pour créer et initialiser l'exemple DoubleAction</span><span class="sxs-lookup"><span data-stu-id="b898c-106">To build and initialize the DoubleAction sample</span></span>  
  
1.  <span data-ttu-id="b898c-107">Sur l'ordinateur Contoso, dans une fenêtre d'invite de commandes, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="b898c-107">On the Contoso computer, in a command prompt window, move to the following folder:</span></span>   
    <span data-ttu-id="b898c-108">*\<lecteur >*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction\\.</span><span class="sxs-lookup"><span data-stu-id="b898c-108">*\<drive>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction\\.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b898c-109">Avant d'exécuter le programme d'installation, ouvrez le fichier DoubleAction.sql (situé dans le dossier ci-dessus) dans le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="b898c-109">Before running the Setup program, open the DoubleAction.sql file (in the above folder) in Notepad.</span></span> <span data-ttu-id="b898c-110">Dans le menu **Fichier** , cliquez sur **Enregistrer sous**.</span><span class="sxs-lookup"><span data-stu-id="b898c-110">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="b898c-111">Dans la zone **Codage** , sélectionnez **ANSI** dans la liste déroulante, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="b898c-111">In the **Encoding** box, select **ANSI** from the drop-down list, and then click **Save**.</span></span> <span data-ttu-id="b898c-112">Sélectionnez **Oui** pour remplacer les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="b898c-112">Click **Yes** to overwrite the existing file.</span></span>  
  
2.  <span data-ttu-id="b898c-113">Si votre [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] installation est en cours d’exécution sur SQL Server 2008 R2/2008 SP1, exécutez setupx64.bat dans le même dossier.</span><span class="sxs-lookup"><span data-stu-id="b898c-113">If your [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] installation is running on SQL Server 2008 R2/2008 SP1, run setupx64.bat in the same folder.</span></span> <span data-ttu-id="b898c-114">Le fichier de commandes effectuera les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b898c-114">The batch file will perform the following actions:</span></span>  
  
    -   <span data-ttu-id="b898c-115">Crée une procédure stockée SQL (`PipAutomationGetAction`) dans la base de données BTARNDATA pour récupérer le message d'action à partir de la table MessagesToLOB.</span><span class="sxs-lookup"><span data-stu-id="b898c-115">Creates a SQL stored procedure (`PipAutomationGetAction`) in the BTARNDATA database to retrieve the action message from the MessagesToLOB table.</span></span>  
  
    -   <span data-ttu-id="b898c-116">Compile le projet .NET HeaderHelper et inscrit l'assembly dans le GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="b898c-116">Compiles the HeaderHelper .NET project and registers the assembly in the global assembly cache.</span></span>  
  
    -   <span data-ttu-id="b898c-117">Crée et lie le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SQL receive port (MessagesToLOB_Receive_Port).</span><span class="sxs-lookup"><span data-stu-id="b898c-117">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SQL receive port (MessagesToLOB_Receive_Port).</span></span>  
  
    -   <span data-ttu-id="b898c-118">Active l'emplacement de réception (MessagesToLOB_Receive_Location).</span><span class="sxs-lookup"><span data-stu-id="b898c-118">Enables the receive location (MessagesToLOB_Receive_Location).</span></span>  
  
    -   <span data-ttu-id="b898c-119">Compile et déploiement l'orchestration double action PIPAutomation (DoubleAction.odx).</span><span class="sxs-lookup"><span data-stu-id="b898c-119">Compiles and deploys the double-action PIPAutomation orchestration (DoubleAction.odx).</span></span>  
  
    -   <span data-ttu-id="b898c-120">Lie et démarre l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b898c-120">Binds and starts the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b898c-121">L'exemple affiche des avertissements pendant la compilation.</span><span class="sxs-lookup"><span data-stu-id="b898c-121">The sample displays some warnings while compiling.</span></span> <span data-ttu-id="b898c-122">Vous pouvez ignorer ces avertissements.</span><span class="sxs-lookup"><span data-stu-id="b898c-122">You can ignore these warnings.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b898c-123">Vérifiez que DoubleAction.odx a été lié à **MessagesToLOB_Receive_Port**et que l'orchestration a été démarrée.</span><span class="sxs-lookup"><span data-stu-id="b898c-123">Verify that DoubleAction.odx has been bound to **MessagesToLOB_Receive_Port**, and that the orchestration has been started.</span></span>  
  
3.  <span data-ttu-id="b898c-124">Dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Console d’Administration, développez le **groupe BizTalk**, **Applications**, et **BizTalk Application 1** nœuds.</span><span class="sxs-lookup"><span data-stu-id="b898c-124">In [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Administration Console, expand the **BizTalk Group**, **Applications**, and **BizTalk Application 1** nodes.</span></span> <span data-ttu-id="b898c-125">Cliquez sur le nœud **Orchestrations** .</span><span class="sxs-lookup"><span data-stu-id="b898c-125">Click the **Orchestrations** node.</span></span> <span data-ttu-id="b898c-126">Cliquez avec le bouton droit sur l'orchestration **DoubleAction** , puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b898c-126">Right-click the **DoubleAction** orchestration, and then click **Properties**.</span></span> <span data-ttu-id="b898c-127">Dans la boîte de dialogue Propriétés, cliquez sur le nœud **Liaisons** , puis affectez à **Hôte** la valeur **BizTalkServerApplication** et affectez à **Port de réception** la valeur **MessageToLOB_ReceivePort**.</span><span class="sxs-lookup"><span data-stu-id="b898c-127">In the Properties dialog box, click the **Bindings** node, and then set the **Host** to **BizTalkServerApplication** and set the **Receive Port** to **MessageToLOB_ReceivePort**.</span></span> <span data-ttu-id="b898c-128">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b898c-128">Click **OK**.</span></span> <span data-ttu-id="b898c-129">Cliquez avec le bouton droit sur l'orchestration **DoubleAction** , puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="b898c-129">Right-click the **DoubleAction** orchestration, and then click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b898c-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b898c-130">See Also</span></span>  
 [<span data-ttu-id="b898c-131">Création et configuration de la Solution Fabrikam</span><span class="sxs-lookup"><span data-stu-id="b898c-131">Creating and Configuring the Fabrikam Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-fabrikam-solution.md)