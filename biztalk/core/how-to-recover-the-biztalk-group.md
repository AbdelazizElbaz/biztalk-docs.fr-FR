---
title: "Comment récupérer le groupe BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1010e55-7e3d-4565-8604-ea652ea4da8c
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: deaf3ddae7d7351d53c5cd46b7d48633e0271a3d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-recover-the-biztalk-group"></a><span data-ttu-id="d9971-102">Récupération du groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="d9971-102">How to Recover the BizTalk Group</span></span>
<span data-ttu-id="d9971-103">Dans le cadre du processus de récupération du système, vous devez rejoindre un groupe BizTalk existant sur le serveur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d9971-103">You must rejoin the BizTalk Server to an existing BizTalk group as part of the system recovery process.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d9971-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d9971-104">Prerequisites</span></span>  
 <span data-ttu-id="d9971-105">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="d9971-105">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
 <span data-ttu-id="d9971-106">Si vous récupérez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Édition Standard, vous devez télécharger un script facilitant la récupération du serveur.</span><span class="sxs-lookup"><span data-stu-id="d9971-106">If you are recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition, you must download a script that facilitates recovery of the server.</span></span> <span data-ttu-id="d9971-107">Télécharger [RestoreConfig.vbe](http://go.microsoft.com/fwlink/?LinkID=195799).</span><span class="sxs-lookup"><span data-stu-id="d9971-107">Download [RestoreConfig.vbe](http://go.microsoft.com/fwlink/?LinkID=195799).</span></span>  
  
### <a name="to-recover-the-biztalk-group-standard-edition"></a><span data-ttu-id="d9971-108">Pour récupérer le groupe BizTalk (Édition Standard)</span><span class="sxs-lookup"><span data-stu-id="d9971-108">To recover the BizTalk group (Standard Edition)</span></span>  
  
1.  <span data-ttu-id="d9971-109">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d9971-109">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="d9971-110">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="d9971-110">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="d9971-111">**RestoreConfig.vbe***\<SavedConfigXML  \>*</span><span class="sxs-lookup"><span data-stu-id="d9971-111">**RestoreConfig.vbe**  *\<SavedConfigXML\>*</span></span>  
  
     <span data-ttu-id="d9971-112">Où  *\<SavedConfigXML\>*  est le chemin d’accès complet et le nom du fichier de configuration enregistrée.</span><span class="sxs-lookup"><span data-stu-id="d9971-112">Where *\<SavedConfigXML\>* is the full path and filename of the saved configuration file.</span></span>  
  
     <span data-ttu-id="d9971-113">L'invite de commandes doit se fermer sans afficher d'erreur.</span><span class="sxs-lookup"><span data-stu-id="d9971-113">The above should exit without displaying any errors.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9971-114">Pour récupérer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition sur un ordinateur 64 bits, vous devez exécuter **RestoreConfig.vbe** à partir de l’invite de commandes 32 bits afin qu’elle peut mettre à jour le Registre 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d9971-114">To recover [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition on a 64-bit computer, you must run **RestoreConfig.vbe** from the 32-bit command prompt so that it can update the 32-bit registry.</span></span> <span data-ttu-id="d9971-115">Pour ouvrir l’invite de commandes 32 bits, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **c:\windows\syswow64\cmd.exe**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d9971-115">To open the 32-bit command prompt, click **Start**, click **Run**, type **c:\windows\syswow64\cmd.exe**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9971-116">Le nom de l'ordinateur ayant échoué se trouve dans le fichier de la configuration enregistrée.</span><span class="sxs-lookup"><span data-stu-id="d9971-116">The name of the computer that failed is contained in the saved configuration file.</span></span> <span data-ttu-id="d9971-117">Le nom de l'ordinateur sur lequel vous effectuez la restauration doit être identique à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="d9971-117">The name of the computer that you are restoring onto must have that same name.</span></span> <span data-ttu-id="d9971-118">Vous devez exécuter le script décrit ci-dessus sur un ordinateur possédant ce nom.</span><span class="sxs-lookup"><span data-stu-id="d9971-118">You must run the script above on a computer with that name.</span></span> <span data-ttu-id="d9971-119">Toutefois, vous pouvez modifier le nom de l'ordinateur ayant échoué dans le fichier de la configuration enregistrée.</span><span class="sxs-lookup"><span data-stu-id="d9971-119">You can, however, change the name of the computer that failed in the saved configuration file.</span></span> <span data-ttu-id="d9971-120">Si vous procédez ainsi, vous pourrez exécuter le script précédent sur un ordinateur de nom différent.</span><span class="sxs-lookup"><span data-stu-id="d9971-120">If you do so, you can run the script above onto a computer with a different name.</span></span>  
  
### <a name="to-recover-the-biztalk-group-developer-edition-or-enterprise-edition"></a><span data-ttu-id="d9971-121">Pour récupérer le groupe BizTalk (Édition Développeur ou Édition Entreprise)</span><span class="sxs-lookup"><span data-stu-id="d9971-121">To recover the BizTalk group (Developer Edition or Enterprise Edition)</span></span>  
  
1.  <span data-ttu-id="d9971-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Configuration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="d9971-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="d9971-123">Dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], dans l’arborescence de la console, cliquez sur **groupe**.</span><span class="sxs-lookup"><span data-stu-id="d9971-123">In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], in the console tree, click **Group**.</span></span>  
  
3.  <span data-ttu-id="d9971-124">Dans le volet détails, sélectionnez **joindre un groupe BizTalk existant**, puis spécifiez la base de gestion BizTalk (BizTalkMgmtDb) distante appropriée.</span><span class="sxs-lookup"><span data-stu-id="d9971-124">In the details pane, select **Join an existing BizTalk Group**, and then specify the appropriate remote BizTalk Management (BizTalkMgmtDb) database.</span></span>  
  
4.  <span data-ttu-id="d9971-125">Cliquez sur **Appliquer la configuration**.</span><span class="sxs-lookup"><span data-stu-id="d9971-125">Click **Apply Configuration**.</span></span>  
  
5.  <span data-ttu-id="d9971-126">Cliquez sur **fichier**, puis cliquez sur **Exit**.</span><span class="sxs-lookup"><span data-stu-id="d9971-126">Click **File**, and then click **Exit**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9971-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9971-127">See Also</span></span>  
 [<span data-ttu-id="d9971-128">Récupération d’un ordinateur exécutant BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d9971-128">Recovering a Computer Running BizTalk Server</span></span>](../core/recovering-a-computer-running-biztalk-server.md)