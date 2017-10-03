---
title: "L’installation du logiciel BAM-événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3638d34-f5a8-4ffd-99eb-d38aed4c0732
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5c41606f6056dcc4edb90b4db5ef6a41901835b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-bam-eventing-software"></a><span data-ttu-id="14ef7-102">Installation du logiciel BAM-Événements</span><span class="sxs-lookup"><span data-stu-id="14ef7-102">Installing the BAM-Eventing Software</span></span>
<span data-ttu-id="14ef7-103">Pour mettre en œuvre des solutions BAM à l'aide des API d'événements BAM ou configurer votre application Windows Workflow Foundation ou Windows Communication Foundation afin d'utiliser l'intercepteur BAM pour Windows Workflow Foundation, vous devez installer le logiciel BAM-Événements à l'aide du programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14ef7-103">To implement BAM solutions using the BAM eventing APIs or configure your Windows Workflow Foundation or Windows Communication Foundation application to use the BAM interceptor for Windows Workflow Foundation, you must install the BAM-Eventing software by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Setup program.</span></span> <span data-ttu-id="14ef7-104">Ce logiciel peut être installé dans le cadre de l'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ou séparément en sélectionnant Prise en charge de BAM-Événements sous Logiciels complémentaires dans l'application d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14ef7-104">This software can be installed as part of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime or separately by selecting BAM Eventing Support under Additional Software in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup application.</span></span>  
  
### <a name="to-install-the-bam-eventing-software"></a><span data-ttu-id="14ef7-105">Pour installer le logiciel BAM-Événements</span><span class="sxs-lookup"><span data-stu-id="14ef7-105">To install the BAM-Eventing software</span></span>  
  
1.  <span data-ttu-id="14ef7-106">Connectez-vous à l'ordinateur qui hébergera l'application WF en utilisant un compte disposant des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="14ef7-106">Log on to the computer that will host the WF application using an account that has Administrator privileges.</span></span>  
  
2.  <span data-ttu-id="14ef7-107">Exécutez le programme d'installation disponible sur le CD-ROM d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14ef7-107">Run the Setup program on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Installation CD.</span></span>  
  
3.  <span data-ttu-id="14ef7-108">Désactivez toutes les options sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="14ef7-108">Clear all selected options.</span></span> <span data-ttu-id="14ef7-109">Si vous ne le faites pas, vous risquez d'installer des logiciels dont vous n'avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="14ef7-109">If you do not perform this step, you may install software you do not need.</span></span>  
  
4.  <span data-ttu-id="14ef7-110">Développez **des logiciels supplémentaires**, puis sélectionnez le **BAM-événements** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="14ef7-110">Expand **Additional Software**, and then select the **BAM-Eventing** check box.</span></span>  
  
5.  <span data-ttu-id="14ef7-111">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="14ef7-111">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="14ef7-112">Cliquez sur **Installer**.</span><span class="sxs-lookup"><span data-stu-id="14ef7-112">Click **Install**.</span></span>  
  
7.  <span data-ttu-id="14ef7-113">Lorsque la procédure d’installation est terminée, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="14ef7-113">When the installation procedure is complete, click **OK**.</span></span>  
  
     <span data-ttu-id="14ef7-114">Le logiciel BAM-Événements est maintenant installé.</span><span class="sxs-lookup"><span data-stu-id="14ef7-114">The BAM-Eventing software is now installed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14ef7-115">L'installation de la bibliothèque d'intercepteurs BAM à l'aide de cette méthode ne requiert pas l'achat de licences supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="14ef7-115">Installing the BAM interceptor library using this method does not require the purchase of additional licenses.</span></span>  
  
 <span data-ttu-id="14ef7-116">Si vous souhaitez surveiller les données des compteurs de performance des intercepteurs BAM, vous devez d'abord les enregistrer à l'aide du fichier InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="14ef7-116">If you are interested in monitoring performance counter data for the BAM interceptors, you must first register them by using InstallUtil.exe.</span></span>  
  
### <a name="to-register-bam-interceptor-performance-counters-by-using-installutilexe"></a><span data-ttu-id="14ef7-117">Pour enregistrer des compteurs de performance d'intercepteur BAM à l'aide du fichier InstallUtil.exe</span><span class="sxs-lookup"><span data-stu-id="14ef7-117">To register BAM interceptor performance counters by using InstallUtil.exe</span></span>  
  
1.  <span data-ttu-id="14ef7-118">Démarrer  **[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes** en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="14ef7-118">Start **[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt** as an administrator.</span></span>  
  
2.  <span data-ttu-id="14ef7-119">À l'invite de commande, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="14ef7-119">At the command prompt, enter the following command:</span></span>  
  
     <span data-ttu-id="14ef7-120">InstallUtil [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\Microsoft.BizTalk.Bam.Interceptors.dll</span><span class="sxs-lookup"><span data-stu-id="14ef7-120">InstallUtil [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\Microsoft.BizTalk.Bam.Interceptors.dll</span></span>  
  
3.  <span data-ttu-id="14ef7-121">Type **Exit**, puis appuyez sur ENTRÉE pour fermer l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="14ef7-121">Type **Exit**, and then press ENTER to close the command prompt.</span></span>  
  
     <span data-ttu-id="14ef7-122">Les compteurs de performance d'intercepteur BAM ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="14ef7-122">The BAM interceptor performance counters are now available.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14ef7-123">Par défaut, seuls les administrateurs et certains comptes système sont autorisés à enregistrer les données de performance.</span><span class="sxs-lookup"><span data-stu-id="14ef7-123">By default, only Administrators and some system accounts have permission to log performance data.</span></span> <span data-ttu-id="14ef7-124">Pour activer l'accès sur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], ajoutez le compte utilisé pour l'exécution des applications de workflow au groupe Utilisateurs du journal de performance.</span><span class="sxs-lookup"><span data-stu-id="14ef7-124">To enable access on [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], add the account used for running workflow applications to the Performance Log Users group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ef7-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14ef7-125">See Also</span></span>  
 <span data-ttu-id="14ef7-126">[Implémentation de Solutions BAM](../core/implementing-bam-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="14ef7-126">[Implementing BAM Solutions](../core/implementing-bam-solutions.md) </span></span>  
 [<span data-ttu-id="14ef7-127">Vue d’ensemble de l’installation de BizTalk Server 2013 et 2013 R2</span><span class="sxs-lookup"><span data-stu-id="14ef7-127">Installation Overview for BizTalk Server 2013 and 2013 R2</span></span>](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)