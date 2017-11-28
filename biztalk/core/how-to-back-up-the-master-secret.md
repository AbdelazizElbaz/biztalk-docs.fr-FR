---
title: Comment sauvegarder le Secret principal | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], backing up
- backing up, Master Secret server
- Master Secret server, backing up
ms.assetid: 22c23f66-b7df-4379-8a9f-065406ba8aa8
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5bd6cdecda9ca2456a770d4cf885fcd420fc18e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-the-master-secret"></a><span data-ttu-id="bc600-102">Comment sauvegarder le Secret principal</span><span class="sxs-lookup"><span data-stu-id="bc600-102">How to Back Up the Master Secret</span></span>
<span data-ttu-id="bc600-103">Vous pouvez sauvegarder le secret principal du serveur de secret principal dans un système de fichiers NTFS ou sur un média amovible, tel qu'une disquette.</span><span class="sxs-lookup"><span data-stu-id="bc600-103">You can back up the master secret from the master secret server onto an NTFS file system or removable media, such as a floppy disk.</span></span>  
  
 <span data-ttu-id="bc600-104">Pour effectuer cette tâche, vous devez être un administrateur SSO (authentification unique) et un administrateur Windows.</span><span class="sxs-lookup"><span data-stu-id="bc600-104">You must be a Single Sign-On Administrator and a Windows administrator to perform this task.</span></span> <span data-ttu-id="bc600-105">Le système SSO vous invitera à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="bc600-105">The SSO system will prompt you for a password.</span></span> <span data-ttu-id="bc600-106">Vous devrez spécifier celui-ci pour restaurer le secret ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="bc600-106">To restore the secret later, you must specify the same password.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="bc600-107">Si le serveur de secret principal échoue et que vous perdez la clé, ou si celle-ci est endommagée, vous ne serez plus en mesure de récupérer les données stockées dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="bc600-107">If the master secret server fails and you lose the key, or if the key becomes corrupted, you will not be able to retrieve data stored in the SSO database.</span></span> <span data-ttu-id="bc600-108">Vous devez sauvegarder le secret principal, sans quoi vous risquez de perdre les données figurant dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="bc600-108">You must back up the master secret, or you risk losing data from the SSO database.</span></span>  
  
### <a name="to-back-up-the-master-secret-using-the-mmc-snap-in"></a><span data-ttu-id="bc600-109">Pour sauvegarder le secret principal à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="bc600-109">To back up the master secret using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="bc600-110">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="bc600-110">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="bc600-111">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="bc600-111">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="bc600-112">Avec le bouton droit **système**, puis cliquez sur **sauvegarde Secret**.</span><span class="sxs-lookup"><span data-stu-id="bc600-112">Right-click **System**, and then click **Backup Secret**.</span></span>  
  
### <a name="to-back-up-the-master-secret-using-the-command-line"></a><span data-ttu-id="bc600-113">Pour sauvegarder le secret principal à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="bc600-113">To back up the master secret using the command line</span></span>  
  
1.  <span data-ttu-id="bc600-114">Sur le **Démarrer** menu, cliquez sur **tous les programmes**, puis cliquez sur **Accessoires**.</span><span class="sxs-lookup"><span data-stu-id="bc600-114">On the **Start** menu, click **All Programs**, and then click **Accessories**.</span></span> <span data-ttu-id="bc600-115">Avec le bouton droit **invite de commandes**, puis cliquez sur **exécuter en tant que...** .</span><span class="sxs-lookup"><span data-stu-id="bc600-115">Right-click **Command Prompt**, and then click **Run As…**.</span></span>  
  
2.  <span data-ttu-id="bc600-116">Sélectionnez l’administrateur approprié, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bc600-116">Select the appropriate Administrator, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="bc600-117">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="bc600-117">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="bc600-118">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="bc600-118">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="bc600-119">Type **ssoconfig – backupSecret  *\<fichier de sauvegarde >***, où  *\<fichier de sauvegarde >* est le chemin d’accès et le nom du fichier où le maître clé secrète est sauvegardé.</span><span class="sxs-lookup"><span data-stu-id="bc600-119">Type **ssoconfig –backupSecret *\<backup file>***, where *\<backup file>* is the path and name of the file where the master secret will be backed up.</span></span> <span data-ttu-id="bc600-120">Par exemple, A:\ssobackup.bak</span><span class="sxs-lookup"><span data-stu-id="bc600-120">For example, A:\ssobackup.bak</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc600-121">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="bc600-121">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="bc600-122">Fournissez un mot de passe pour protéger ce fichier.</span><span class="sxs-lookup"><span data-stu-id="bc600-122">Provide a password to protect this file.</span></span> <span data-ttu-id="bc600-123">Vous serez invité à confirmer le mot de passe, ainsi qu'à fournir une indication de mot de passe pour mémoriser celui-ci.</span><span class="sxs-lookup"><span data-stu-id="bc600-123">You will be prompted to confirm the password and to provide a password hint to help you remember this password.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc600-124">Vous devez enregistrer et stocker le fichier de sauvegarde dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="bc600-124">You must save and store the backup file in a secure location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc600-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc600-125">See Also</span></span>  
 <span data-ttu-id="bc600-126">[Comment générer le Secret principal](../core/how-to-generate-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="bc600-126">[How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md) </span></span>  
 <span data-ttu-id="bc600-127">[Comment restaurer le Secret principal](../core/how-to-restore-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="bc600-127">[How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md) </span></span>  
 <span data-ttu-id="bc600-128">[Serveur de secret principal](../core/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="bc600-128">[Master Secret Server](../core/master-secret-server.md) </span></span>  
 [<span data-ttu-id="bc600-129">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="bc600-129">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)