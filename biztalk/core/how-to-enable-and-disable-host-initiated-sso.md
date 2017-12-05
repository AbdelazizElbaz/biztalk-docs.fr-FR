---
title: "Activer et de désactivation de l’authentification unique initiée par | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host initiated SSO, disabling
- disabling, host initiated SSO
- enabling, host initiated SSO
- host initiated SSO, enabling
ms.assetid: a11d314a-6ff9-4d0a-89c3-c412541c2cec
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1e5783893bbc9091d0a5f1fb3f116b17413bc5d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-and-disable-host-initiated-sso"></a><span data-ttu-id="395d5-102">Activer et de désactivation de l’authentification unique initiée par</span><span class="sxs-lookup"><span data-stu-id="395d5-102">How to Enable and Disable Host Initiated SSO</span></span>
<span data-ttu-id="395d5-103">Par défaut, l'authentification unique initiée par l'hôte n'est pas activée dans le système d'authentification unique et doit l'être par l'administrateur de cette authentification.</span><span class="sxs-lookup"><span data-stu-id="395d5-103">By default, host initiated Single Sign-On is not enabled in the Single Sign-On system, and must be enabled by the SSO Administrator.</span></span>  
  
### <a name="to-enable-host-initiated-sso-using-the-mmc-snap-in"></a><span data-ttu-id="395d5-104">Pour activer l'authentification initiée par l'hôte à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="395d5-104">To enable host initiated SSO using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="395d5-105">Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="395d5-105">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="395d5-106">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="395d5-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="395d5-107">Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="395d5-107">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="395d5-108">Cliquez sur le **Options** onglet.</span><span class="sxs-lookup"><span data-stu-id="395d5-108">Click the **Options** tab.</span></span>  
  
5.  <span data-ttu-id="395d5-109">Sélectionnez le **l’authentification unique initiée par l’hôte de l’activer** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="395d5-109">Select the **Enable host initiated SSO** box, and click **OK**.</span></span>  
  
### <a name="to-enable-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="395d5-110">Pour activer l'authentification unique initiée par l'hôte à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="395d5-110">To enable host initiated SSO using the command line</span></span>  
  
1.  <span data-ttu-id="395d5-111">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="395d5-111">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="395d5-112">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="395d5-112">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="395d5-113">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="395d5-113">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="395d5-114">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="395d5-114">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="395d5-115">Type **ssomanage-activer hisso**.</span><span class="sxs-lookup"><span data-stu-id="395d5-115">Type **ssomanage -enable hisso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="395d5-116">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="395d5-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
 <span data-ttu-id="395d5-117">La désactivation de l'authentification unique s'applique à tout le système d'authentification unique, et toutes les opérations en rapport avec l'hôte l'ayant initiée sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="395d5-117">Disabling SSO applies to the entire SSO system, and all operations related to host initiated SSO are turned off.</span></span>  
  
#### <a name="to-disable-host-initiated-sso-using-the-mmc-snap-in"></a><span data-ttu-id="395d5-118">Pour désactiver l'authentification initiée par l'hôte à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="395d5-118">To disable host initiated SSO using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="395d5-119">Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="395d5-119">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="395d5-120">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="395d5-120">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="395d5-121">Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="395d5-121">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="395d5-122">Cliquez sur le **Options** onglet.</span><span class="sxs-lookup"><span data-stu-id="395d5-122">Click the **Options** tab.</span></span>  
  
5.  <span data-ttu-id="395d5-123">Désactivez le **l’authentification unique initiée par l’hôte de l’activer** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="395d5-123">Clear the **Enable host initiated SSO** box, and click **OK**.</span></span>  
  
#### <a name="to-disable-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="395d5-124">Pour désactiver l'authentification unique initiée par l'hôte à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="395d5-124">To disable host initiated SSO using the command line</span></span>  
  
1.  <span data-ttu-id="395d5-125">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="395d5-125">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="395d5-126">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="395d5-126">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="395d5-127">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="395d5-127">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="395d5-128">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="395d5-128">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="395d5-129">Type **ssomanage-désactiver hisso** selon le cas.</span><span class="sxs-lookup"><span data-stu-id="395d5-129">Type **ssomanage -disable hisso** as appropriate.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="395d5-130">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="395d5-130">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395d5-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="395d5-131">See Also</span></span>  
 [<span data-ttu-id="395d5-132">Authentification unique initiée par l’hôte</span><span class="sxs-lookup"><span data-stu-id="395d5-132">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)