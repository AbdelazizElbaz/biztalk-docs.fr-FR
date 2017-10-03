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
ms.openlocfilehash: e6e7440742c5bb8efb8d867ecc96447390336b84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-and-disable-host-initiated-sso"></a><span data-ttu-id="b31fe-102">Activer et de désactivation de l’authentification unique initiée par</span><span class="sxs-lookup"><span data-stu-id="b31fe-102">How to Enable and Disable Host Initiated SSO</span></span>
<span data-ttu-id="b31fe-103">Par défaut, l'authentification unique initiée par l'hôte n'est pas activée dans le système d'authentification unique et doit l'être par l'administrateur de cette authentification.</span><span class="sxs-lookup"><span data-stu-id="b31fe-103">By default, host initiated Single Sign-On is not enabled in the Single Sign-On system, and must be enabled by the SSO Administrator.</span></span>  
  
### <a name="to-enable-host-initiated-sso-using-the-mmc-snap-in"></a><span data-ttu-id="b31fe-104">Pour activer l'authentification initiée par l'hôte à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="b31fe-104">To enable host initiated SSO using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="b31fe-105">Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="b31fe-105">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="b31fe-106">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="b31fe-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="b31fe-107">Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b31fe-107">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b31fe-108">Cliquez sur le **Options** onglet.</span><span class="sxs-lookup"><span data-stu-id="b31fe-108">Click the **Options** tab.</span></span>  
  
5.  <span data-ttu-id="b31fe-109">Sélectionnez le **l’authentification unique initiée par l’hôte de l’activer** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b31fe-109">Select the **Enable host initiated SSO** box, and click **OK**.</span></span>  
  
### <a name="to-enable-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="b31fe-110">Pour activer l'authentification unique initiée par l'hôte à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b31fe-110">To enable host initiated SSO using the command line</span></span>  
  
1.  <span data-ttu-id="b31fe-111">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="b31fe-111">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="b31fe-112">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b31fe-112">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b31fe-113">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b31fe-113">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="b31fe-114">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="b31fe-114">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="b31fe-115">Type **ssomanage-activer hisso**.</span><span class="sxs-lookup"><span data-stu-id="b31fe-115">Type **ssomanage -enable hisso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b31fe-116">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b31fe-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
 <span data-ttu-id="b31fe-117">La désactivation de l'authentification unique s'applique à tout le système d'authentification unique, et toutes les opérations en rapport avec l'hôte l'ayant initiée sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="b31fe-117">Disabling SSO applies to the entire SSO system, and all operations related to host initiated SSO are turned off.</span></span>  
  
#### <a name="to-disable-host-initiated-sso-using-the-mmc-snap-in"></a><span data-ttu-id="b31fe-118">Pour désactiver l'authentification initiée par l'hôte à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="b31fe-118">To disable host initiated SSO using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="b31fe-119">Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="b31fe-119">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="b31fe-120">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="b31fe-120">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="b31fe-121">Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b31fe-121">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b31fe-122">Cliquez sur le **Options** onglet.</span><span class="sxs-lookup"><span data-stu-id="b31fe-122">Click the **Options** tab.</span></span>  
  
5.  <span data-ttu-id="b31fe-123">Désactivez le **l’authentification unique initiée par l’hôte de l’activer** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b31fe-123">Clear the **Enable host initiated SSO** box, and click **OK**.</span></span>  
  
#### <a name="to-disable-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="b31fe-124">Pour désactiver l'authentification unique initiée par l'hôte à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b31fe-124">To disable host initiated SSO using the command line</span></span>  
  
1.  <span data-ttu-id="b31fe-125">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="b31fe-125">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="b31fe-126">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b31fe-126">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b31fe-127">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b31fe-127">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="b31fe-128">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="b31fe-128">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="b31fe-129">Type **ssomanage-désactiver hisso** selon le cas.</span><span class="sxs-lookup"><span data-stu-id="b31fe-129">Type **ssomanage -disable hisso** as appropriate.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b31fe-130">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b31fe-130">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b31fe-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b31fe-131">See Also</span></span>  
 [<span data-ttu-id="b31fe-132">L’authentification unique initiée par l’hôte</span><span class="sxs-lookup"><span data-stu-id="b31fe-132">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)