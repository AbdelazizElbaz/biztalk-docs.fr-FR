---
title: "Comment afficher les informations de base de données SSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO], viewing SSO database
- SSO database, viewing
- viewing, SSO database
ms.assetid: 0ebadd2e-6ea5-460c-b0a8-f48589e6bf1c
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1328e6066af0d19c68657728f8dc7777ba62f12d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-display-the-sso-database-information"></a><span data-ttu-id="8c5cc-102">Comment afficher les informations de base de données SSO</span><span class="sxs-lookup"><span data-stu-id="8c5cc-102">How to Display the SSO Database Information</span></span>
<span data-ttu-id="8c5cc-103">Vous pouvez afficher les informations de la base de données SSO à l'aide du composant logiciel enfichable MMC ou de l'utilitaire de ligne de commande (ssomanage).</span><span class="sxs-lookup"><span data-stu-id="8c5cc-103">You can view SSO database information by using the MMC Snap-In or the command line (ssomanage) utility.</span></span>  
  
### <a name="to-display-the-sso-database-information-using-the-mmc-snap-in"></a><span data-ttu-id="8c5cc-104">Pour afficher les informations de la base de données SSO à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="8c5cc-104">To display the SSO database information using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="8c5cc-105">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-105">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="8c5cc-106">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="8c5cc-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="8c5cc-107">Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-107">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="8c5cc-108">Cliquez sur les onglets dans le **propriétés système** boîte de dialogue pour afficher les informations de base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-108">Click the tabs on the  **System Properties** dialog box to view SSO database information.</span></span>  
  
### <a name="to-display-the-sso-database-information-using-the-command-line"></a><span data-ttu-id="8c5cc-109">Pour afficher les informations de la base de données SSO à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="8c5cc-109">To display the SSO database information using the command line</span></span>  
  
1.  <span data-ttu-id="8c5cc-110">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-110">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="8c5cc-111">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-111">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="8c5cc-112">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-112">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="8c5cc-113">Type **ssomanage – displaydb**.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-113">Type **ssomanage –displaydb**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c5cc-114">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-114">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-display-the-sso-database-the-sso-server-is-connected-to-using-the-command-line"></a><span data-ttu-id="8c5cc-115">Pour afficher la base de données SSO à laquelle le serveur d'authentification unique est connecté à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="8c5cc-115">To display the SSO database the SSO Server is connected to using the command line</span></span>  
  
1.  <span data-ttu-id="8c5cc-116">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-116">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="8c5cc-117">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-117">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="8c5cc-118">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-118">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="8c5cc-119">Type **ssomanage – showdb**.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-119">Type **ssomanage –showdb**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c5cc-120">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
 <span data-ttu-id="8c5cc-121">Le tableau suivant décrit les valeurs affichées grâce à ces procédures.</span><span class="sxs-lookup"><span data-stu-id="8c5cc-121">The following table describes the values displayed by these procedures.</span></span>  
  
|<span data-ttu-id="8c5cc-122">Propriété</span><span class="sxs-lookup"><span data-stu-id="8c5cc-122">Property</span></span>|<span data-ttu-id="8c5cc-123">Valeur</span><span class="sxs-lookup"><span data-stu-id="8c5cc-123">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="8c5cc-124">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8c5cc-124">SQL Server</span></span>|<span data-ttu-id="8c5cc-125">**\<Nom du serveur SQL >**</span><span class="sxs-lookup"><span data-stu-id="8c5cc-125">**\<SQL Server name>**</span></span>|  
|<span data-ttu-id="8c5cc-126">Base de données de l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="8c5cc-126">Single Sign-On database</span></span>|<span data-ttu-id="8c5cc-127">**\<Nom de base de données SQL Server >**</span><span class="sxs-lookup"><span data-stu-id="8c5cc-127">**\<SQL Server database name>**</span></span>|  
|<span data-ttu-id="8c5cc-128">Nom du serveur de secret de l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="8c5cc-128">Single Sign-On Secret Server name</span></span>|<span data-ttu-id="8c5cc-129">**\<Nom du serveur de l’authentification unique >**</span><span class="sxs-lookup"><span data-stu-id="8c5cc-129">**\<Single Sign-On Server name>**</span></span>|  
|<span data-ttu-id="8c5cc-130">Compte des administrateurs de l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="8c5cc-130">Single Sign-On Administrators account</span></span>|<span data-ttu-id="8c5cc-131">Domaine\nom du compte</span><span class="sxs-lookup"><span data-stu-id="8c5cc-131">Domain\account name</span></span>|  
|<span data-ttu-id="8c5cc-132">Compte des administrateurs d'applications associées à authentification unique</span><span class="sxs-lookup"><span data-stu-id="8c5cc-132">Single Sign-On Affiliate Administrators account</span></span>|<span data-ttu-id="8c5cc-133">Domaine\nom du compte</span><span class="sxs-lookup"><span data-stu-id="8c5cc-133">Domain\account name</span></span>|  
|<span data-ttu-id="8c5cc-134">Taille de la table d'audit pour les applications supprimées (nombre d'entrées d'audit)</span><span class="sxs-lookup"><span data-stu-id="8c5cc-134">Size of audit table for deleted applications (number of audit entries)</span></span>|<span data-ttu-id="8c5cc-135">1 000 (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8c5cc-135">1,000 (default)</span></span>|  
|<span data-ttu-id="8c5cc-136">Taille de la table d'audit pour les mappages d'utilisateurs supprimés (nombre d'entrées d'audit)</span><span class="sxs-lookup"><span data-stu-id="8c5cc-136">Size of audit table for deleted user mappings (number of audit entries)</span></span>|<span data-ttu-id="8c5cc-137">1 000 (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8c5cc-137">1,000 (default)</span></span>|  
|<span data-ttu-id="8c5cc-138">Taille de la table d'audit pour les recherches d'informations d'identification externes (nombre d'entrées d'audit)</span><span class="sxs-lookup"><span data-stu-id="8c5cc-138">Size of audit table for external credential lookups (number of audit entries)</span></span>|<span data-ttu-id="8c5cc-139">1 000 (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8c5cc-139">1,000 (default)</span></span>|  
|<span data-ttu-id="8c5cc-140">Délai d'attente du ticket (en minutes)</span><span class="sxs-lookup"><span data-stu-id="8c5cc-140">Ticket timeout (in minutes)</span></span>|<span data-ttu-id="8c5cc-141">2 (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="8c5cc-141">2 (default)</span></span><br /><br /> <span data-ttu-id="8c5cc-142">Cette valeur doit être un nombre entier compris entre 1 et 525 600</span><span class="sxs-lookup"><span data-stu-id="8c5cc-142">This value can be an integer from1 through 525,600</span></span>|  
|<span data-ttu-id="8c5cc-143">Délai d'attente du cache des informations d'identification (en minutes)</span><span class="sxs-lookup"><span data-stu-id="8c5cc-143">Credential cache timeout (in minutes)</span></span>|<span data-ttu-id="8c5cc-144">60 (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8c5cc-144">60 (default)</span></span>|  
|<span data-ttu-id="8c5cc-145">État de l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="8c5cc-145">Single Sign-On Status</span></span>|<span data-ttu-id="8c5cc-146">Activé/désactivé</span><span class="sxs-lookup"><span data-stu-id="8c5cc-146">Enabled/disabled</span></span>|  
|<span data-ttu-id="8c5cc-147">Tickets autorisés</span><span class="sxs-lookup"><span data-stu-id="8c5cc-147">Tickets allowed</span></span>|<span data-ttu-id="8c5cc-148">Oui/non (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8c5cc-148">Yes/no (default)</span></span>|  
|<span data-ttu-id="8c5cc-149">Valider les tickets</span><span class="sxs-lookup"><span data-stu-id="8c5cc-149">Validate tickets</span></span>|<span data-ttu-id="8c5cc-150">Oui (par défaut)/non</span><span class="sxs-lookup"><span data-stu-id="8c5cc-150">Yes (default)/no</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c5cc-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c5cc-151">See Also</span></span>  
 <span data-ttu-id="8c5cc-152">[Comment configurer les Tickets d’authentification unique](../core/how-to-configure-the-sso-tickets.md) </span><span class="sxs-lookup"><span data-stu-id="8c5cc-152">[How to Configure the SSO Tickets](../core/how-to-configure-the-sso-tickets.md) </span></span>  
 [<span data-ttu-id="8c5cc-153">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="8c5cc-153">Using SSO</span></span>](../core/using-sso.md)