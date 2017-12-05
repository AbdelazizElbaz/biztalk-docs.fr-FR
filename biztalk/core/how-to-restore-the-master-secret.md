---
title: Comment restaurer le Secret principal | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], restoring
- Master Secret server, restoring
- restoring, Master Secret server
ms.assetid: 68e133c5-4591-4d76-9a3b-c9564ff1aa60
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9241c8d9c5f6e41f47199211d0215c16526951d6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-restore-the-master-secret"></a><span data-ttu-id="970a6-102">Comment restaurer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="970a6-102">How to Restore the Master Secret</span></span>
<span data-ttu-id="970a6-103">Dans le cadre des procédures de récupération des données, vous devrez peut-être restaurer le secret principal afin de réutiliser les données existantes.</span><span class="sxs-lookup"><span data-stu-id="970a6-103">As part of data recovery procedures, you may need to restore the master secret to re-use existing data.</span></span> <span data-ttu-id="970a6-104">À cette fin, vous devez ouvrir une session sur le serveur de secret principal à l'aide d'un compte à la fois Administrateur Windows et Administrateur SSO.</span><span class="sxs-lookup"><span data-stu-id="970a6-104">In order to perform this task, you must log on to the master secret server with an account that is both a Windows administrator and an SSO administrator.</span></span>  
  
### <a name="to-restore-the-master-secret-using-the-mmc-snap-in"></a><span data-ttu-id="970a6-105">Pour restaurer le secret principal à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="970a6-105">To restore the master secret using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="970a6-106">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="970a6-106">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="970a6-107">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="970a6-107">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="970a6-108">Avec le bouton droit **système**, puis cliquez sur **restaurer le Secret**.</span><span class="sxs-lookup"><span data-stu-id="970a6-108">Right-click **System**, and then click **Restore Secret**.</span></span>  
  
### <a name="to-restore-the-master-secret-using-the-command-line"></a><span data-ttu-id="970a6-109">Pour restaurer le secret principal à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="970a6-109">To restore the master secret using the command line</span></span>  
  
1.  <span data-ttu-id="970a6-110">Sur le **Démarrer** menu, cliquez sur **tous les programmes**, puis cliquez sur **Accessoires**.</span><span class="sxs-lookup"><span data-stu-id="970a6-110">On the **Start** menu, click **All Programs**, and then click **Accessories**.</span></span> <span data-ttu-id="970a6-111">Avec le bouton droit **invite de commandes**, puis cliquez sur **exécuter en tant que...** .</span><span class="sxs-lookup"><span data-stu-id="970a6-111">Right-click **Command Prompt**, and then click **Run As…**.</span></span>  
  
2.  <span data-ttu-id="970a6-112">Sélectionnez l’administrateur approprié, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="970a6-112">Select the appropriate Administrator, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="970a6-113">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="970a6-113">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="970a6-114">Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="970a6-114">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="970a6-115">Type **ssoconfig – restoreSecret \<restaurer le fichier\>**, où  **\<restaurer le fichier\>**  est le chemin d’accès et le nom du fichier où le secret principal stockées.</span><span class="sxs-lookup"><span data-stu-id="970a6-115">Type **ssoconfig –restoreSecret \<restore file\>**, where **\<restore file\>** is the path and name of the file where the master secret is stored.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="970a6-116">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="970a6-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="970a6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="970a6-117">See Also</span></span>  
 <span data-ttu-id="970a6-118">[Comment générer le Secret principal](../core/how-to-generate-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="970a6-118">[How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md) </span></span>  
 <span data-ttu-id="970a6-119">[Comment sauvegarder le Secret principal](../core/how-to-back-up-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="970a6-119">[How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md) </span></span>  
 <span data-ttu-id="970a6-120">[Serveur de secret principal](../core/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="970a6-120">[Master Secret Server](../core/master-secret-server.md) </span></span>  
 [<span data-ttu-id="970a6-121">Gestion du secret principal</span><span class="sxs-lookup"><span data-stu-id="970a6-121">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)