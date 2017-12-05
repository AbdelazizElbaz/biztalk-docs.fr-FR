---
title: "Comment récupérer Enterprise Single Sign-On | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 845e6ff7-88a8-4ab4-b307-f9275d44600e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a87404e608789fa3dba003f3aba6155c5f049e8d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-recover-enterprise-single-sign-on"></a><span data-ttu-id="66e00-102">Récupération de l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="66e00-102">How to Recover Enterprise Single Sign-On</span></span>
<span data-ttu-id="66e00-103">Avant de restaurer BizTalk Server, vous devez restaurer l'authentification unique de l'entreprise (SSO).</span><span class="sxs-lookup"><span data-stu-id="66e00-103">Before you can recover BizTalk Server, you must first recover Enterprise Single Sign-On (SSO).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="66e00-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="66e00-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="66e00-105">Pour effectuer cette tâche, vous devez ouvrir une session en tant que membre du groupe Administrateurs de l'authentification unique et du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="66e00-105">You must be logged on as a member of the Single Sign-On Administrators group and a member of the Administrators group to perform this task.</span></span>  
  
-   <span data-ttu-id="66e00-106">Vous devez disposer du mot de passe utilisé lors de la configuration de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="66e00-106">You must have the password used during SSO configuration.</span></span>  
  
-   <span data-ttu-id="66e00-107">Toutes les bases de données sont intactes sur le serveur distant.</span><span class="sxs-lookup"><span data-stu-id="66e00-107">All databases are intact on the remote server.</span></span>  
  
-   <span data-ttu-id="66e00-108">Le fichier de sauvegarde du secret principal est intact et stocké dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="66e00-108">The backup master secret file is intact and stored in a safe place.</span></span>  
  
### <a name="to-recover-enterprise-single-sign-on"></a><span data-ttu-id="66e00-109">Pour restaurer l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="66e00-109">To recover Enterprise Single Sign-On</span></span>  
  
1.  <span data-ttu-id="66e00-110">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Configuration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="66e00-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="66e00-111">Dans la Configuration de Microsoft BizTalk Server, dans l’arborescence de la console, cliquez sur **Enterprise SSO**.</span><span class="sxs-lookup"><span data-stu-id="66e00-111">In Microsoft BizTalk Server Configuration, in the console tree, click **Enterprise SSO**.</span></span>  
  
3.  <span data-ttu-id="66e00-112">Dans le volet détails, sélectionnez **activer Enterprise Single Sign-On sur cet ordinateur**, puis cliquez sur **joindre un système SSO existant**.</span><span class="sxs-lookup"><span data-stu-id="66e00-112">In the details pane, select **Enable Enterprise Single Sign-On on this computer**, and then click **Join an existing SSO system**.</span></span>  
  
4.  <span data-ttu-id="66e00-113">Dans **banques de données**, entrez le nom du serveur SQL qui héberge la base de données SSO et le nom de la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="66e00-113">In **Data stores**, enter the name of the SQL server hosting the SSO database and the name of the SSO database.</span></span>  
  
5.  <span data-ttu-id="66e00-114">Dans **service Windows**, entrez le nom d’utilisateur et un mot de passe pour le compte de service d’authentification unique que vous avez utilisé lors de l’installation et configuration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="66e00-114">In **Windows service**, enter the user name and password for the SSO service account that you used when you originally installed and configured BizTalk Server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="66e00-115">Vous pouvez utiliser un autre compte, mais celui-ci doit être membre du groupe Administrateurs de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="66e00-115">You can use a different account, but it must be a member of the Single Sign-On Administrators group.</span></span>  
  
6.  <span data-ttu-id="66e00-116">Cliquez sur **Appliquer la configuration**.</span><span class="sxs-lookup"><span data-stu-id="66e00-116">Click **Apply Configuration**.</span></span>  
  
     <span data-ttu-id="66e00-117">L'avertissement qui s'affiche indique qu'aucun secret principal n'a été récupéré.</span><span class="sxs-lookup"><span data-stu-id="66e00-117">A warning that no master secrets were retrieved is displayed.</span></span> <span data-ttu-id="66e00-118">Vous pouvez utiliser l'Observateur d'événements pour vérifier que le service d'authentification unique de l'entreprise est démarré et exécuté sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="66e00-118">You can use Event Viewer to verify that the Enterprise Single Sign-On service is now started and running on the computer.</span></span>  
  
7.  <span data-ttu-id="66e00-119">Cliquez sur **fichier**, puis cliquez sur **Exit**.</span><span class="sxs-lookup"><span data-stu-id="66e00-119">Click **File**, and then click **Exit**.</span></span>  
  
8.  <span data-ttu-id="66e00-120">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="66e00-120">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="66e00-121">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="66e00-121">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="66e00-122">**CD programme Files\Common Files\Enterprise Single Sign-On**</span><span class="sxs-lookup"><span data-stu-id="66e00-122">**cd Program Files\Common Files\Enterprise Single Sign-On**</span></span>  
  
10. <span data-ttu-id="66e00-123">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="66e00-123">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="66e00-124">**ssoconfig - restoreSecret***\<backupfile  \>*</span><span class="sxs-lookup"><span data-stu-id="66e00-124">**ssoconfig -restoreSecret**  *\<backupfile\>*</span></span>  
  
     <span data-ttu-id="66e00-125">où  *\<backupfile\>*  est le nom du fichier de secret principal que vous avez sauvegardé.</span><span class="sxs-lookup"><span data-stu-id="66e00-125">where *\<backupfile\>* is the name of the master secret file that you backed up.</span></span>  
  
     <span data-ttu-id="66e00-126">Lorsque **ssoconfig** vous demande le mot de passe du fichier de sauvegarde, entrez le mot de passe qui a été spécifié lors de la configuration de l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="66e00-126">When **ssoconfig** prompts you for the backup file password, enter the password that was specified during SSO configuration.</span></span> <span data-ttu-id="66e00-127">Si le mot de passe est correct, **ssoconfig** affiche le message suivant :</span><span class="sxs-lookup"><span data-stu-id="66e00-127">If the password is correct, **ssoconfig** displays the following message:</span></span>  
  
     <span data-ttu-id="66e00-128">**L’opération s’est terminée avec succès**</span><span class="sxs-lookup"><span data-stu-id="66e00-128">**The operation completed successfully**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e00-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66e00-129">See Also</span></span>  
 <span data-ttu-id="66e00-130">[Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="66e00-130">[Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span></span>  
 [<span data-ttu-id="66e00-131">Configuration d’Enterprise SSO à l’aide de la Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="66e00-131">Configuring Enterprise SSO Using the BizTalk Server Configuration</span></span>](http://msdn.microsoft.com/library/f63d1aec-a8c7-4e76-a67f-19af69e252f0)