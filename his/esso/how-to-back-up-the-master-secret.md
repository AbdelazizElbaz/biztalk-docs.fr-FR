---
title: Comment sauvegarder le Secret principal | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0841c52a-7b15-45f8-9900-f5c9e3abd90b
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 124c077d7a15a4938f94239518ad02c8268074a4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-back-up-the-master-secret"></a><span data-ttu-id="2972b-102">Comment sauvegarder le Secret principal</span><span class="sxs-lookup"><span data-stu-id="2972b-102">How to Back Up the Master Secret</span></span>
<span data-ttu-id="2972b-103">Vous pouvez sauvegarder le secret principal du serveur de secret principal dans un système de fichiers NTFS ou sur un média amovible, tel qu'une disquette.</span><span class="sxs-lookup"><span data-stu-id="2972b-103">You can back up the master secret from the master secret server onto an NTFS file system or removable media, such as a floppy disk.</span></span>  
  
 <span data-ttu-id="2972b-104">Vous devez être un administrateur de l’authentification unique et un administrateur Windows pour effectuer cette tâche.</span><span class="sxs-lookup"><span data-stu-id="2972b-104">You must be a Single Sign-On administrator and a Windows administrator to perform this task.</span></span> <span data-ttu-id="2972b-105">Le système Single Sign-On (SSO) vous demandera un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="2972b-105">The Single Sign-On (SSO) system will prompt you for a password.</span></span> <span data-ttu-id="2972b-106">Vous devrez spécifier celui-ci pour restaurer le secret ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="2972b-106">To restore the secret later, you must specify the same password.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2972b-107">Si le serveur de secret principal tombe en panne et vous perdez la clé, ou si la clé est endommagée, vous ne serez pas en mesure de récupérer les données stockées dans la base de données d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="2972b-107">If the master secret server crashes and you lose the key, or if the key becomes corrupted, you will not be able to retrieve data stored in the Credential database.</span></span> <span data-ttu-id="2972b-108">Vous devez sauvegarder le secret principal, ou vous risquez de perdre des données à partir de la base de données d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="2972b-108">You must back up the master secret, or you risk losing data from the Credential database.</span></span>  
  
### <a name="to-back-up-the-master-secret-using-the-mmc-snap-in"></a><span data-ttu-id="2972b-109">Pour sauvegarder le secret principal à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="2972b-109">To back up the master secret using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="2972b-110">Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="2972b-110">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="2972b-111">Dans le volet d’étendue du composant logiciel enfichable ENTSSO Microsoft Management Console (MMC), développez le **Enterprise Single Sign-On** nœud.</span><span class="sxs-lookup"><span data-stu-id="2972b-111">In the scope pane of the ENTSSO Microsoft Management Console (MMC) Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="2972b-112">Avec le bouton droit **système**, puis cliquez sur **sauvegarder le Secret principal**.</span><span class="sxs-lookup"><span data-stu-id="2972b-112">Right-click **System**, and then click **Back up Master Secret**.</span></span>  
  
### <a name="to-back-up-the-master-secret-using-the-command-line"></a><span data-ttu-id="2972b-113">Pour sauvegarder le secret principal à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="2972b-113">To back up the master secret using the command line</span></span>  
  
1.  <span data-ttu-id="2972b-114">Sur le **Démarrer** menu, cliquez sur **programmes**, puis cliquez sur **Accessoires**.</span><span class="sxs-lookup"><span data-stu-id="2972b-114">On the **Start** menu, click **Programs**, and then click **Accessories**.</span></span> <span data-ttu-id="2972b-115">Avec le bouton droit **invite de commandes**, puis cliquez sur **exécuter en tant que...** .</span><span class="sxs-lookup"><span data-stu-id="2972b-115">Right-click **Command Prompt**, and then click **Run As…**.</span></span>  
  
2.  <span data-ttu-id="2972b-116">Sélectionnez l’administrateur approprié, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2972b-116">Select the appropriate Administrator, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2972b-117">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="2972b-117">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="2972b-118">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="2972b-118">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="2972b-119">Type `ssoconfig –backupsecret <backup file>`, où  *\<fichier de sauvegarde >* est le chemin d’accès et le nom du fichier où le secret principal sera sauvegardé, par exemple, `A:\ssobackup.bak`.</span><span class="sxs-lookup"><span data-stu-id="2972b-119">Type `ssoconfig –backupsecret <backup file>`, where *\<backup file>* is the path and name of the file where the master secret will be backed up, for example, `A:\ssobackup.bak`.</span></span>  
  
5.  <span data-ttu-id="2972b-120">Fournir un mot de passe pour protéger ce fichier.</span><span class="sxs-lookup"><span data-stu-id="2972b-120">Provide a password to help protect this file.</span></span>  
  
     <span data-ttu-id="2972b-121">Vous serez invité à confirmer le mot de passe, ainsi qu'à fournir une indication de mot de passe pour mémoriser celui-ci.</span><span class="sxs-lookup"><span data-stu-id="2972b-121">You will be prompted to confirm the password and to provide a password hint to help you remember this password.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2972b-122">Vous devez enregistrer et stocker le fichier de sauvegarde dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="2972b-122">You must save and store the backup file in a secure location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2972b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2972b-123">See Also</span></span>  
 <span data-ttu-id="2972b-124">[Comment générer le Secret principal](../esso/how-to-generate-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="2972b-124">[How to Generate the Master Secret](../esso/how-to-generate-the-master-secret.md) </span></span>  
 <span data-ttu-id="2972b-125">[Comment restaurer le Secret principal](../esso/how-to-restore-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="2972b-125">[How to Restore the Master Secret](../esso/how-to-restore-the-master-secret.md) </span></span>  
 <span data-ttu-id="2972b-126">[Serveur de secret principal](../esso/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="2972b-126">[Master Secret Server](../esso/master-secret-server.md) </span></span>  
 [<span data-ttu-id="2972b-127">Gestion du secret principal</span><span class="sxs-lookup"><span data-stu-id="2972b-127">Managing the Master Secret</span></span>](../esso/managing-the-master-secret.md)