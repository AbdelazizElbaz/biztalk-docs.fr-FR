---
title: "Comment activer l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], creating
- SSO, enabling
- maps [SSO], creating
- managing [SSO], enabling
- SSO, maps
- SSO, applications
- creating, applications [SSO]
- managing [SSO], creating affiliate applications
ms.assetid: dda89d15-6b70-4c40-b658-2f6cbdd545c8
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f51b07bc34779643124efd5b249373301f7e47b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-sso"></a><span data-ttu-id="f3e84-102">Comment activer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="f3e84-102">How to Enable SSO</span></span>
<span data-ttu-id="f3e84-103">Vous pouvez activer le système d'authentification unique à l'aide du composant logiciel enfichable MMC ou de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="f3e84-103">You can enable the entire Enterprise Single Sign-On (SSO) system by using either the MMC Snap-In or the command line.</span></span>  
  
 <span data-ttu-id="f3e84-104">Après avoir exécuté la commande d'activation, il y a un court délai avant l'activation de tous les serveurs d'authentification unique, le temps que chaque serveur interroge la base de données SSO pour obtenir les dernières informations globales.</span><span class="sxs-lookup"><span data-stu-id="f3e84-104">After you run the enabling command, there is a short delay before all Single Sign-On Servers are enabled, as each polls the SSO database for the latest global information.</span></span>  
  
 <span data-ttu-id="f3e84-105">Si vous souhaitez configurer les applications associées et les mappages du système SSO, vous devez également créer une application associée.</span><span class="sxs-lookup"><span data-stu-id="f3e84-105">If you want to configure affiliate applications and mappings in the SSO system, you must also create an affiliate application.</span></span> <span data-ttu-id="f3e84-106">Après la création d'une application associée par un administrateur SSO, un administrateur d'application peut y apporter des modifications, et les utilisateurs d'application (utilisateurs finaux) peuvent créer leurs propres mappages.</span><span class="sxs-lookup"><span data-stu-id="f3e84-106">After an SSO affiliate administrator creates an affiliate application, an application administrator can make changes to it, and application users (end-users) can create their own mappings.</span></span> <span data-ttu-id="f3e84-107">Pour plus d’informations, consultez [la gestion des Applications associées](../core/managing-affiliate-applications.md) et [gestion des mappages d’utilisateur](../core/managing-user-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="f3e84-107">For more information, see [Managing Affiliate Applications](../core/managing-affiliate-applications.md) and [Managing User Mappings](../core/managing-user-mappings.md).</span></span>  
  
### <a name="to-enable-the-sso-system-using-the-mmc-snap-in"></a><span data-ttu-id="f3e84-108">Pour activer le système SSO à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="f3e84-108">To enable the SSO system using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="f3e84-109">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="f3e84-109">Click **Start**, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="f3e84-110">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="f3e84-110">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="f3e84-111">Avec le bouton droit **système**, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="f3e84-111">Right-click **System**, and then click **Enable**.</span></span>  
  
### <a name="to-enable-the-sso-system-using-the-command-line"></a><span data-ttu-id="f3e84-112">Pour activer le système SSO à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="f3e84-112">To enable the SSO system using the command line</span></span>  
  
1.  <span data-ttu-id="f3e84-113">Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="f3e84-113">Click **Start**, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="f3e84-114">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="f3e84-114">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="f3e84-115">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="f3e84-115">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="f3e84-116">Type **ssomanage – enablesso**.</span><span class="sxs-lookup"><span data-stu-id="f3e84-116">Type **ssomanage –enablesso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3e84-117">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="f3e84-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-enable-sso-to-create-affiliate-applications-and-mappings"></a><span data-ttu-id="f3e84-118">Pour activer SSO en vue de créer des applications associées et des mappages</span><span class="sxs-lookup"><span data-stu-id="f3e84-118">To enable SSO to create affiliate applications and mappings</span></span>  
  
1.  <span data-ttu-id="f3e84-119">Connectez-vous en tant qu'administrateur SSO ou administrateur d'applications associées à SSO au serveur SSO, ou sur un ordinateur hébergeant des sous-services d'administration SSO.</span><span class="sxs-lookup"><span data-stu-id="f3e84-119">Log on as an SSO administrator or SSO affiliate administrator to the SSO Server, or on a computer that has the SSO administration sub services of SSO.</span></span>  
  
2.  <span data-ttu-id="f3e84-120">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="f3e84-120">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
3.  <span data-ttu-id="f3e84-121">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="f3e84-121">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="f3e84-122">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="f3e84-122">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="f3e84-123">Type **ssomanage - enablesso** pour activer le service Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="f3e84-123">Type **ssomanage -enablesso** to enable the Enterprise Single Sign-On service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3e84-124">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="f3e84-124">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="f3e84-125">Connectez-vous en tant qu'administrateur d'applications associées à SSO.</span><span class="sxs-lookup"><span data-stu-id="f3e84-125">Log on as an SSO affiliate administrator.</span></span>  
  
6.  <span data-ttu-id="f3e84-126">Type **ssomanage - createapps  *\<fichier de l’application >***  pour créer une application associée, où \<fichier de l’application > est le fichier XML qui contient les définitions les applications associées.</span><span class="sxs-lookup"><span data-stu-id="f3e84-126">Type **ssomanage -createapps *\<application file>*** to create an affiliate application, where \<application file> is the XML file that contains definitions for the affiliate applications.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3e84-127">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="f3e84-127">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e84-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3e84-128">See Also</span></span>  
 <span data-ttu-id="f3e84-129">[Comment configurer le serveur d’authentification unique](../core/how-to-set-the-sso-server.md) </span><span class="sxs-lookup"><span data-stu-id="f3e84-129">[How to Set the SSO Server](../core/how-to-set-the-sso-server.md) </span></span>  
 <span data-ttu-id="f3e84-130">[Comment désactiver l’authentification unique](../core/how-to-disable-sso.md) </span><span class="sxs-lookup"><span data-stu-id="f3e84-130">[How to Disable SSO](../core/how-to-disable-sso.md) </span></span>  
 <span data-ttu-id="f3e84-131">[Comment mettre à jour la base de données SSO](../core/how-to-update-the-sso-database.md) </span><span class="sxs-lookup"><span data-stu-id="f3e84-131">[How to Update the SSO Database](../core/how-to-update-the-sso-database.md) </span></span>  
 [<span data-ttu-id="f3e84-132">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="f3e84-132">Using SSO</span></span>](../core/using-sso.md)