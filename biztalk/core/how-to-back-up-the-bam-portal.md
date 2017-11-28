---
title: Comment sauvegarder le portail BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cea02e6-e387-4048-a1f3-d7c3c562f470
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27e7308e54505c795e35ffa2fbb2d287c1a49ec4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-the-bam-portal"></a><span data-ttu-id="e1dd1-102">Sauvegarde du portail BAM</span><span class="sxs-lookup"><span data-stu-id="e1dd1-102">How to Back Up the BAM Portal</span></span>
<span data-ttu-id="e1dd1-103">Si vous utilisez l'analyse BAM (Business Activity Monitoring), vous devez sauvegarder le portail BAM dans le cadre de la sauvegarde de votre serveur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-103">If you are using Business Activity Monitoring (BAM), you must back up the BAM portal as part of backing up your BizTalk server.</span></span> <span data-ttu-id="e1dd1-104">Si vous n'utilisez pas l'analyse BAM, cette procédure est facultative.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-104">If you are not using BAM, this procedure is optional.</span></span>  
  
 <span data-ttu-id="e1dd1-105">Certaines phases du processus de sauvegarde diffèrent nettement selon la version d'Internet Information Services (IIS) que vous sauvegardez.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-105">Certain portions of the backup process differ markedly depending on which version of Internet Information Services (IIS) you are backing up.</span></span> <span data-ttu-id="e1dd1-106">IIS 6.0 permet de sauvegarder la configuration du pool d'applications et la configuration du site Web séparément. Vous pouvez également chiffrer les fichiers de sauvegarde de la configuration à l'aide d'un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-106">IIS 6.0 permits you to back up the application pool configuration and web site configuration separately, and you can encrypt the configuration backup files using a password.</span></span>  
  
 <span data-ttu-id="e1dd1-107">IIS 7.0 enregistre les paramètres de configuration pour le pool d’applications et le site web dans un fichier applicationHost.config. Le fichier applicationHost.config n’est pas chiffré, mais les mots de passe de compte, le cas échéant, sont chiffrées dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-107">IIS 7.0 saves configuration settings for both the application pool and web site to a single file, applicationHost.config. The applicationHost.config file is not encrypted, but account passwords, if any, are encrypted in the file.</span></span> <span data-ttu-id="e1dd1-108">Le chiffrement est effectué à l'aide du certificat de l'ordinateur en cours de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-108">Encryption is performed using the certificate from the computer you are backing up.</span></span> <span data-ttu-id="e1dd1-109">Cette configuration ne peut pas être restaurée sur un autre ordinateur que celui dont elle provient.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-109">This configuration cannot be restored to a computer other than the one from which it originated.</span></span>  
  
 <span data-ttu-id="e1dd1-110">Vous ne pouvez pas sauvegarder la configuration du portail BAM à l’aide du Gestionnaire IIS 7.0 ; Vous devez utiliser le **Appcmd.exe** outil de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-110">You cannot back up the BAM portal configuration using the IIS 7.0 Manager; you must use the **Appcmd.exe** command-line tool.</span></span> <span data-ttu-id="e1dd1-111">Pour plus d’informations sur Appcmd, consultez [http://go.microsoft.com/fwlink/?LinkId=147497](http://go.microsoft.com/fwlink/?LinkId=147497).</span><span class="sxs-lookup"><span data-stu-id="e1dd1-111">For more information about Appcmd, see [http://go.microsoft.com/fwlink/?LinkId=147497](http://go.microsoft.com/fwlink/?LinkId=147497).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e1dd1-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e1dd1-112">Prerequisites</span></span>  
 <span data-ttu-id="e1dd1-113">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-113">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
### <a name="to-back-up-the-bam-portal-iis-70"></a><span data-ttu-id="e1dd1-114">Pour sauvegarder le portail BAM (IIS 7.0)</span><span class="sxs-lookup"><span data-stu-id="e1dd1-114">To back up the BAM portal (IIS 7.0)</span></span>  
  
1.  <span data-ttu-id="e1dd1-115">Cliquez sur **Démarrer**, puis sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-115">Click **Start**, and then click **Run**.</span></span>  
  
2.  <span data-ttu-id="e1dd1-116">Dans la boîte de dialogue Exécuter, dans la zone Ouvrir, tapez la commande suivante : `runas /user:` *Nom_Ordinateur*`\`*accountname* `cmd`, puis cliquez sur **OK** ou Appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-116">On the Run dialog, in the Open box, type the following: `runas /user:`*computername*`\`*accountname* `cmd`, and then click **OK** or press **Enter**.</span></span>  
  
     <span data-ttu-id="e1dd1-117">*AccountName* doit être un membre du groupe Administrateurs sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-117">*Accountname* must be a member of the administrators group on the local computer.</span></span>  
  
3.  <span data-ttu-id="e1dd1-118">Lorsque vous y êtes invité, tapez le mot de passe *accountname*, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-118">When prompted, type the password for *accountname*, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="e1dd1-119">Type `cd %windir%\system32\inetsrv`, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-119">Type `cd %windir%\system32\inetsrv`, and then press **Enter**.</span></span>  
  
5.  <span data-ttu-id="e1dd1-120">Type `appcmd add backup “` *nom_sauvegarde*`”`, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-120">Type `appcmd add backup “`*backupname*`”`, and then press **Enter**.</span></span>  
  
     <span data-ttu-id="e1dd1-121">Il n'est pas utile d'entrer un nom de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-121">You do not have to enter a backup name.</span></span> <span data-ttu-id="e1dd1-122">Si aucun nom n'est défini, il est généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-122">If not set, it will be autogenerated.</span></span> <span data-ttu-id="e1dd1-123">« 20090224T123302 » est un exemple de nom de sauvegarde généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-123">An example of an autogenerated backup name is “20090224T123302.”</span></span>  
  
     <span data-ttu-id="e1dd1-124">Pour afficher une liste des sauvegardes de configuration existant, tapez `appcmd list backup`, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-124">To see a list of existing configuration backups, type `appcmd list backup`, and then press **Enter**.</span></span> <span data-ttu-id="e1dd1-125">Les sauvegardes créées par l’utilisateur sont enregistrés dans le **%windir%\system32\inetsrv\backup** active.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-125">Backups created by the user are saved in the **%windir%\system32\inetsrv\backup** directory.</span></span> <span data-ttu-id="e1dd1-126">Pour afficher la liste des options de sauvegarde fourni par **appcmd.exe**, type `appcmd backup /?`, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e1dd1-126">To see a list of the backup options provided by **appcmd.exe**, type `appcmd backup /?`, and then press **Enter**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1dd1-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1dd1-127">See Also</span></span>  
 <span data-ttu-id="e1dd1-128">[Sauvegarde d’un ordinateur exécutant BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="e1dd1-128">[Backing Up a Computer Running BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md) </span></span>  
 <span data-ttu-id="e1dd1-129">[Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="e1dd1-129">[Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span></span>  
 [<span data-ttu-id="e1dd1-130">Portail BAM</span><span class="sxs-lookup"><span data-stu-id="e1dd1-130">BAM Portal</span></span>](../core/bam-portal.md)