---
title: Comment configurer la synchronisation de mot de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Password Synchronization [SSO], replay files
- Password Synchronization [SSO], maximum age
- SSOCONFIG command line utility
- Password Synchronization [SSO], SSOCONFIG command line utility
- Password Synchronization [SSO], configuring
- configuring, Password Synchronization [SSO]
ms.assetid: 04000dfc-02b9-4d50-babe-8bc8a07a33b7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2e8348cdf78db3e95ed75e5d83e6ea53bdffdee
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-password-synchronization"></a><span data-ttu-id="c6257-102">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c6257-102">How to Configure Password Synchronization</span></span>
<span data-ttu-id="c6257-103">L'utilitaire de ligne de commande SSOCONFIG permet de configurer les paramètres de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c6257-103">Use the SSOCONFIG command line utility to configure your password synchronization settings.</span></span>  
  
### <a name="to-specify-the-directory-for-replay-files"></a><span data-ttu-id="c6257-104">Pour spécifier le répertoire des fichiers de relecture</span><span class="sxs-lookup"><span data-stu-id="c6257-104">To specify the directory for replay files</span></span>  
  
1.  <span data-ttu-id="c6257-105">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="c6257-105">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="c6257-106">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6257-106">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c6257-107">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="c6257-107">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="c6257-108">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="c6257-108">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="c6257-109">Type **ssoconfig - replayfiles \<répertoire des fichiers de relecture\> &#124; - par défaut** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="c6257-109">Type **ssoconfig -replayfiles \<replay files directory\> &#124; -default** and press Enter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6257-110">Les fichiers de relecture ne sont pas supprimés quand vous modifiez le compte de service.</span><span class="sxs-lookup"><span data-stu-id="c6257-110">Replay files are not deleted when you change the service account.</span></span> <span data-ttu-id="c6257-111">Si vous modifiez celui-ci, vous devrez supprimer les fichiers de relecture manuellement.</span><span class="sxs-lookup"><span data-stu-id="c6257-111">If you change this account, you will need to delete the replay files manually.</span></span>  
  
#### <a name="to-display-or-change-maximum-password-synchronization-age"></a><span data-ttu-id="c6257-112">Pour afficher ou modifier l'ancienneté maximale de la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c6257-112">To display or change maximum password synchronization age</span></span>  
  
1.  <span data-ttu-id="c6257-113">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="c6257-113">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="c6257-114">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6257-114">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c6257-115">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="c6257-115">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="c6257-116">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="c6257-116">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="c6257-117">Type **ssoconfig - syncage \<durée de vie maximale en heures\>**  et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="c6257-117">Type **ssoconfig -syncage \<maximum password age in hours\>** and press Enter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6257-118">L'utilitaire SSOCONFIG utilise l'heure de l'ordinateur SQL Server comme heure système.</span><span class="sxs-lookup"><span data-stu-id="c6257-118">The SSOCONFIG utility uses the time on the SQL Server computer as its system time.</span></span> <span data-ttu-id="c6257-119">Prenez cet élément en compte lorsque vous utilisez une commande en relation avec l'heure.</span><span class="sxs-lookup"><span data-stu-id="c6257-119">Remember this when using any commands related to time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6257-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6257-120">See Also</span></span>  
 [<span data-ttu-id="c6257-121">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c6257-121">Password Synchronization</span></span>](../core/password-synchronization2.md)