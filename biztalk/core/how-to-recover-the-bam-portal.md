---
title: "Comment récupérer le portail BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2a5df99-6d03-4f1f-8540-1700d3a0b9db
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 781191047e0ee99b0000c7b773d46aa035a7e1d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-recover-the-bam-portal"></a><span data-ttu-id="3b668-102">Récupération du portail BAM</span><span class="sxs-lookup"><span data-stu-id="3b668-102">How to Recover the BAM Portal</span></span>
<span data-ttu-id="3b668-103">Si vous utilisez l'analyse BAM, vous devez récupérer le portail BAM dans le cadre de la récupération de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b668-103">If you are using Business Activity Monitoring (BAM), you must recover the BAM portal as a part of recovering your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3b668-104">Si vous n'utilisez pas l'analyse BAM, cette procédure est facultative.</span><span class="sxs-lookup"><span data-stu-id="3b668-104">If you are not using BAM, this procedure is optional.</span></span>  
  
 <span data-ttu-id="3b668-105">La procédure de récupération de la configuration du portail BAM diffère considérablement selon la version d'IIS que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="3b668-105">The procedure for recovering the BAM portal configuration differs considerably depending on which version of IIS you are using.</span></span> <span data-ttu-id="3b668-106">Lorsque vous restaurez la configuration pour IIS 7, vous utilisez **Appcmd.exe**, et la restauration de la configuration pour le site Web par défaut entier, pas seulement le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="3b668-106">When you restore the configuration for IIS 7, you use **Appcmd.exe**, and you restore the configuration for the entire default Web site, not just the BAM portal.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3b668-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3b668-107">Prerequisites</span></span>  
 <span data-ttu-id="3b668-108">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="3b668-108">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
### <a name="to-recover-the-bam-portal-configuration-iis-70"></a><span data-ttu-id="3b668-109">Pour récupérer la configuration du portail BAM (IIS 7.0)</span><span class="sxs-lookup"><span data-stu-id="3b668-109">To recover the BAM portal configuration (IIS 7.0)</span></span>  
  
1.  <span data-ttu-id="3b668-110">Dans la boîte de dialogue Exécuter, dans la zone Ouvrir, tapez la commande suivante : `runas /user:` *Nom_Ordinateur*`\`*accountname* `cmd`, puis cliquez sur **OK** ou Appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="3b668-110">On the Run dialog, in the Open box, type the following: `runas /user:`*computername*`\`*accountname* `cmd`, and then click **OK** or press **Enter**.</span></span>  
  
     <span data-ttu-id="3b668-111">*AccountName* doit être un membre du groupe Administrateurs sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3b668-111">*Accountname* must be a member of the administrators group on the local computer.</span></span>  
  
2.  <span data-ttu-id="3b668-112">Lorsque vous y êtes invité, tapez le mot de passe *accountname*, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="3b668-112">When prompted, type the password for *accountname*, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="3b668-113">Type `cd %windir%\system32\inetsrv`, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="3b668-113">Type `cd %windir%\system32\inetsrv`, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="3b668-114">Type `appcmd restore backup “` *nom_sauvegarde*`”`, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="3b668-114">Type `appcmd restore backup “`*backupname*`”`, and then press **Enter**.</span></span>  
  
     <span data-ttu-id="3b668-115">*Nom_sauvegarde* est le nom d’une sauvegarde que vous avez créé précédemment à l’aide de **Appcmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="3b668-115">*Backupname* is the name of a backup you previously created using **Appcmd.exe**.</span></span> <span data-ttu-id="3b668-116">Cette sauvegarde doit exister dans le **%windir%\system32\inetsrv\backup** active.</span><span class="sxs-lookup"><span data-stu-id="3b668-116">This backup must exist in the **%windir%\system32\inetsrv\backup** directory.</span></span> <span data-ttu-id="3b668-117">Elle ne peut pas servir à récupérer les mots de passe créés sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3b668-117">The backup cannot be used to restore passwords created on a different computer.</span></span> <span data-ttu-id="3b668-118">Si BAMAppPool est configuré pour s’exécuter sous une autre identité que la valeur par défaut **NetworkService** compte, vous devez configurer le compte et le mot de passe séparément, comme décrit dans l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="3b668-118">If the BAMAppPool is configured to run under an identity other than the default **NetworkService** account, you must configure the account and password separately, as described in the next step.</span></span>  
  
5.  <span data-ttu-id="3b668-119">À l’aide de la **Gestionnaire des Services Internet (IIS)**, sélectionnez **Pools d’applications** dans les **connexions** volet.</span><span class="sxs-lookup"><span data-stu-id="3b668-119">Using the **Internet Information Services (IIS) Manager**, select **Application Pools** in the **Connections** pane.</span></span>  
  
6.  <span data-ttu-id="3b668-120">Dans le **Pools d’applications** volet, avec le bouton droit le **BAMAppPool**, puis cliquez sur **paramètres avancés**</span><span class="sxs-lookup"><span data-stu-id="3b668-120">In the **Application Pools** pane, right-click the **BAMAppPool**, then click **Advanced Settings**</span></span>  
  
7.  <span data-ttu-id="3b668-121">Dans le **paramètres avancés**boîte de dialogue, faites défiler jusqu'à la **modèle de processus** section.</span><span class="sxs-lookup"><span data-stu-id="3b668-121">In the **Advanced Setting**s dialog, scroll down to the **Process Model** section.</span></span> <span data-ttu-id="3b668-122">Cliquez sur le **identité** boîte.</span><span class="sxs-lookup"><span data-stu-id="3b668-122">Click the **Identity** box.</span></span> <span data-ttu-id="3b668-123">Un bouton représentant des points de suspension s'affiche à droite de la zone.</span><span class="sxs-lookup"><span data-stu-id="3b668-123">This will cause an ellipses button to appear on the right side of the box.</span></span> <span data-ttu-id="3b668-124">Cliquez sur le **ellipses** bouton.</span><span class="sxs-lookup"><span data-stu-id="3b668-124">Click the **ellipses** button.</span></span>  
  
8.  <span data-ttu-id="3b668-125">Dans le **identité du Pool d’applications** boîte de dialogue, cliquez sur le **compte personnalisé** , puis cliquez sur le **définir** bouton.</span><span class="sxs-lookup"><span data-stu-id="3b668-125">In the **Application Pool Identity** dialog, click the **Custom account** button, then click the **Set** button.</span></span>  
  
9. <span data-ttu-id="3b668-126">Dans le **définir les informations d’identification** boîte de dialogue, entrez le nom de compte et un mot de passe pour BAMAppPool.</span><span class="sxs-lookup"><span data-stu-id="3b668-126">In the **Set Credentials** dialog box, enter the account name and password you want to use for the BAMAppPool.</span></span> <span data-ttu-id="3b668-127">Le nom du compte doit être entré en tant que *nom de l’ordinateur*`\`*accountname*, ou *domaine*`\`*accountname*.</span><span class="sxs-lookup"><span data-stu-id="3b668-127">The account name should be entered as *computer name*`\`*accountname*, or *domain*`\`*accountname*.</span></span> <span data-ttu-id="3b668-128">Cliquez sur **OK** pour fermer la **définir les informations d’identification** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3b668-128">Click **OK** to close the **Set Credentials** dialog.</span></span>  
  
10. <span data-ttu-id="3b668-129">Cliquez sur **OK** pour fermer la **identité du Pool d’applications** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3b668-129">Click **OK** to close the **Application Pool Identity** dialog.</span></span>  
  
11. <span data-ttu-id="3b668-130">Cliquez sur **OK** pour fermer la **paramètres avancés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3b668-130">Click **OK** to close the **Advanced Settings** dialog.</span></span>  
  
12. <span data-ttu-id="3b668-131">Vérifiez que le **BAMAppPool** est sélectionné dans la liste des pools d’applications.</span><span class="sxs-lookup"><span data-stu-id="3b668-131">Verify that the **BAMAppPool** is selected in the list of application pools.</span></span> <span data-ttu-id="3b668-132">Dans le **Actions** volet à droite de la **Gestionnaire des Services Internet (IIS)** écran sous **tâches du Pool d’applications**, cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="3b668-132">In the **Actions** pane on the right of the **Internet Information Services (IIS) Manager** screen, under **Application Pool Tasks**, click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b668-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b668-133">See Also</span></span>  
 <span data-ttu-id="3b668-134">[Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="3b668-134">[Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span></span>  
 [<span data-ttu-id="3b668-135">Portail BAM</span><span class="sxs-lookup"><span data-stu-id="3b668-135">BAM Portal</span></span>](../core/bam-portal.md)