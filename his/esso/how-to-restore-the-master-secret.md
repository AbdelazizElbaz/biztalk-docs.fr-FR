---
title: Comment restaurer le Secret principal | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b331c9c5-ca90-4a05-b3f6-59db88bf73dc
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 5e640f2762ed9f9cc03a7795062c98a6aa76a59d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-restore-the-master-secret"></a><span data-ttu-id="dac3c-102">Comment restaurer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="dac3c-102">How to Restore the Master Secret</span></span>
<span data-ttu-id="dac3c-103">Dans le cadre des procédures de récupération de données, vous devrez peut-être restaurer le secret pour réutiliser les données existantes.</span><span class="sxs-lookup"><span data-stu-id="dac3c-103">As part of data recovery procedures, you might have to restore the master secret to reuse existing data.</span></span> <span data-ttu-id="dac3c-104">Pour effectuer cette tâche, vous devez vous connecter le serveur de secret principal en utilisant un compte qui est un administrateur Windows et un administrateur Single Sign-On (SSO).</span><span class="sxs-lookup"><span data-stu-id="dac3c-104">To perform this task, you must log on to the master secret server by using an account that is both a Windows administrator and a Single Sign-On (SSO) administrator.</span></span>  
  
### <a name="to-restore-the-master-secret-using-the-mmc-snap-in"></a><span data-ttu-id="dac3c-105">Pour restaurer le secret principal à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="dac3c-105">To restore the master secret using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="dac3c-106">Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="dac3c-106">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="dac3c-107">Dans le volet d’étendue du composant logiciel enfichable ENTSSO Microsoft Management Console (MMC), développez le **Enterprise Single Sign-On** nœud.</span><span class="sxs-lookup"><span data-stu-id="dac3c-107">In the scope pane of the ENTSSO Microsoft Management Console (MMC) Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="dac3c-108">Avec le bouton droit **système**, puis cliquez sur **restaurer le Secret**.</span><span class="sxs-lookup"><span data-stu-id="dac3c-108">Right-click **System**, and then click **Restore Master Secret**.</span></span>  
  
### <a name="to-restore-the-master-secret-using-the-command-line"></a><span data-ttu-id="dac3c-109">Pour restaurer le secret principal à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="dac3c-109">To restore the master secret using the command line</span></span>  
  
1.  <span data-ttu-id="dac3c-110">Sur le **Démarrer** menu, cliquez sur **programmes**, puis cliquez sur **Accessoires**.</span><span class="sxs-lookup"><span data-stu-id="dac3c-110">On the **Start** menu, click **Programs**, and then click **Accessories**.</span></span> <span data-ttu-id="dac3c-111">Avec le bouton droit **invite de commandes**, puis cliquez sur **exécuter en tant que...** .</span><span class="sxs-lookup"><span data-stu-id="dac3c-111">Right-click **Command Prompt**, and then click **Run As…**.</span></span>  
  
2.  <span data-ttu-id="dac3c-112">Sélectionnez l’administrateur approprié, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="dac3c-112">Select the appropriate Administrator, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="dac3c-113">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="dac3c-113">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="dac3c-114">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="dac3c-114">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="dac3c-115">Type `ssoconfig –restoresecret <restore file>`, où  *\<restaurer le fichier >* est le chemin d’accès et le nom du fichier dans lequel le secret est stocké.</span><span class="sxs-lookup"><span data-stu-id="dac3c-115">Type `ssoconfig –restoresecret <restore file>`, where *\<restore file>* is the path and name of the file where the master secret is stored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac3c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dac3c-116">See Also</span></span>  
 <span data-ttu-id="dac3c-117">[Comment générer le Secret principal](../esso/how-to-generate-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="dac3c-117">[How to Generate the Master Secret](../esso/how-to-generate-the-master-secret.md) </span></span>  
 <span data-ttu-id="dac3c-118">[Comment sauvegarder le Secret principal](../esso/how-to-back-up-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="dac3c-118">[How to Back Up the Master Secret](../esso/how-to-back-up-the-master-secret.md) </span></span>  
 <span data-ttu-id="dac3c-119">[Serveur de secret principal](../esso/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="dac3c-119">[Master Secret Server](../esso/master-secret-server.md) </span></span>  
 [<span data-ttu-id="dac3c-120">Gestion du secret principal</span><span class="sxs-lookup"><span data-stu-id="dac3c-120">Managing the Master Secret</span></span>](../esso/managing-the-master-secret.md)