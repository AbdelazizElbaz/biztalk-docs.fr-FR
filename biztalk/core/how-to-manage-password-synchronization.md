---
title: "Comment gérer la synchronisation de mot de passe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Password Synchronization [SSO], managing
- managing [SSO], disabling features
- managing [SSO], enabling features
- Password Synchronization [SSO], SSOMANAGE command line utility
- SSO database, SSOMANAGE command line utility
- managing, Password Synchronization [SSO]
- SSO database, database settings
- SSOMANAGE command line utility
ms.assetid: 033e63f2-e5b0-4400-99c3-145679d9b84e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2939fd0594c878e3a5f1416d0b1e871b78ba3858
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-password-synchronization"></a><span data-ttu-id="59ee8-102">Comment gérer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="59ee8-102">How to Manage Password Synchronization</span></span>
<span data-ttu-id="59ee8-103">Le composant logiciel enfichable MMC et l'utilitaire de ligne de commande SSOMANAGE permettent d'activer ou de désactiver les fonctionnalités d'authentification unique, ainsi que d'afficher les paramètres de la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="59ee8-103">Use the MMC Snap-in or the SSOMANAGE command line utility to enable or disable SSO features, and to display current SSO database settings.</span></span>  
  
### <a name="to-manage-features-or-display-settings-using-the-mmc-snap-in"></a><span data-ttu-id="59ee8-104">Pour gérer les fonctionnalités ou afficher les paramètres à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="59ee8-104">To manage features or display settings using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="59ee8-105">Cliquez avec le bouton droit sur la fonctionnalité ou la base de données appropriée.</span><span class="sxs-lookup"><span data-stu-id="59ee8-105">Right-click the appropriate feature or database.</span></span>  
  
2.  <span data-ttu-id="59ee8-106">Cliquez sur l'élément de menu approprié.</span><span class="sxs-lookup"><span data-stu-id="59ee8-106">Click the appropriate menu item.</span></span>  
  
### <a name="to-enable-sso-features-using-the-command-line"></a><span data-ttu-id="59ee8-107">Pour activer les fonctionnalités d'authentification unique à l'aide de l'utilitaire de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="59ee8-107">To enable SSO features using the command line</span></span>  
  
1.  <span data-ttu-id="59ee8-108">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="59ee8-108">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="59ee8-109">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="59ee8-109">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="59ee8-110">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="59ee8-110">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="59ee8-111">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="59ee8-111">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="59ee8-112">Type **ssomanage-activer** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="59ee8-112">Type **ssomanage -enable** and press Enter.</span></span>  
  
### <a name="to-disable-sso-features-using-the-command-line"></a><span data-ttu-id="59ee8-113">Pour désactiver les fonctionnalités d'authentification unique à l'aide de l'utilitaire de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="59ee8-113">To disable SSO features using the command line</span></span>  
  
1.  <span data-ttu-id="59ee8-114">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="59ee8-114">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="59ee8-115">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="59ee8-115">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="59ee8-116">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="59ee8-116">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="59ee8-117">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="59ee8-117">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="59ee8-118">Type **ssomanage-désactiver** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="59ee8-118">Type **ssomanage -disable** and press Enter.</span></span>  
  
### <a name="to-display-current-database-settings-using-the-command-line"></a><span data-ttu-id="59ee8-119">Pour afficher les paramètres de base de données actuels à l'aide de l'utilitaire de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="59ee8-119">To display current database settings using the command line</span></span>  
  
1.  <span data-ttu-id="59ee8-120">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="59ee8-120">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="59ee8-121">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="59ee8-121">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="59ee8-122">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="59ee8-122">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="59ee8-123">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="59ee8-123">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="59ee8-124">Type **ssomanage - displaydb** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="59ee8-124">Type **ssomanage -displaydb** and press Enter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ee8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59ee8-125">See Also</span></span>  
 [<span data-ttu-id="59ee8-126">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="59ee8-126">Password Synchronization</span></span>](../core/password-synchronization2.md)