---
title: "Problèmes connus dans le portail BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e681e910-c664-479c-86f3-a6ae0ec97775
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0aa12d0f25a004f2e713f360e00c0f0c1192d304
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-in-the-bam-portal"></a><span data-ttu-id="0d6a4-102">Problèmes connus dans le portail BAM</span><span class="sxs-lookup"><span data-stu-id="0d6a4-102">Known Issues in the BAM Portal</span></span>
<span data-ttu-id="0d6a4-103">Cette rubrique contient des informations destinées à vous aider à identifier et à résoudre les problèmes que vous pouvez rencontrer lorsque vous utilisez le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-103">This topic contains information to help you identify and resolve issues that can occur while you are using the BAM portal.</span></span>  
  
## <a name="errors-are-generated-when-the-bam-portal-and-internet-explorer-7-or-internet-explorer-8-are-on-the-same-computer-and-the-security-settings-are-set-to-low"></a><span data-ttu-id="0d6a4-104">Des erreurs sont générées lorsque le portail BAM et Internet Explorer 7 ou Internet Explorer 8 sont installés sur le même ordinateur et que les paramètres de sécurité ne sont pas élevés</span><span class="sxs-lookup"><span data-stu-id="0d6a4-104">Errors Are Generated When the BAM Portal and Internet Explorer 7 or Internet Explorer 8 Are on the Same Computer and the Security Settings Are Set to Low</span></span>  
 <span data-ttu-id="0d6a4-105">**Problème**</span><span class="sxs-lookup"><span data-stu-id="0d6a4-105">**Problem**</span></span>  
  
 <span data-ttu-id="0d6a4-106">Lorsque vous utilisez Internet Explorer 7 ou Internet Explorer 7 ou Internet Explorer 8 avec [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)], [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] vous pouvez rencontrer le message d’erreur **erreur serveur dans ' / BAM' Application** sous les éléments suivants circonstances :</span><span class="sxs-lookup"><span data-stu-id="0d6a4-106">When using Internet Explorer 7 or Internet Explorer 7 or Internet Explorer 8 with [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)], [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] you may encounter the error message **Server Error in '/BAM' Application** under the following circumstances:</span></span>  
  
-   <span data-ttu-id="0d6a4-107">Lorsque vous cliquez sur une activité associée qui pointe vers une instance d'activité inexistante</span><span class="sxs-lookup"><span data-stu-id="0d6a4-107">While clicking a related activity that points to a non-existing activity instance.</span></span>  
  
-   <span data-ttu-id="0d6a4-108">Tout en cliquant sur le **enregistrer l’alerte** bouton dans le scénario suivant :</span><span class="sxs-lookup"><span data-stu-id="0d6a4-108">While clicking the **Save Alert** button in the following scenario:</span></span>  
  
    -   <span data-ttu-id="0d6a4-109">Vous créez une requête sur le **ActivitySearch** page, puis cliquez sur **définir l’alerte**.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-109">You create a query on the **ActivitySearch** page and then click **Set Alert**.</span></span>  
  
    -   <span data-ttu-id="0d6a4-110">Vous renseignez les champs d’alerte, puis sur **enregistrer l’alerte**.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-110">You complete the alert fields and then click **Save Alert**.</span></span>  
  
    -   <span data-ttu-id="0d6a4-111">Vous cliquez sur le bouton Précédent.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-111">You click the back button.</span></span>  
  
    -   <span data-ttu-id="0d6a4-112">Vous cliquez sur le **enregistrer l’alerte** bouton Nouveau.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-112">You click the **Save Alert** button again.</span></span>  
  
 <span data-ttu-id="0d6a4-113">**Cause**</span><span class="sxs-lookup"><span data-stu-id="0d6a4-113">**Cause**</span></span>  
  
 <span data-ttu-id="0d6a4-114">Lorsque vous exécutez [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] et Internet Explorer 7 ou Internet Explorer 8 avec un niveau de sécurité peu élevé, les requêtes Web sont exécutées avec de faibles privilèges.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-114">When running [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] and Internet Explorer 7 or Internet Explorer 8 with the security level set to low, Web requests are executed with low privileges.</span></span> <span data-ttu-id="0d6a4-115">Pour répondre aux exigences de sécurité intégrée de Windows, Internet Explorer transmet un jeton d'utilisateur avec des privilèges minimaux.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-115">To fulfill the Windows integrated security challenge, Internet Explorer passes a user token with low privileges.</span></span>  
  
 <span data-ttu-id="0d6a4-116">Si vous utilisez Internet Explorer sur l'ordinateur sur lequel le portail BAM est installé et que vous définissez un niveau de sécurité faible dans Internet Explorer, le portail emprunte l'identité de l'utilisateur possédant le jeton associé à de faibles privilèges.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-116">If you are using Internet Explorer on the same computer as the one on which the BAM portal is installed, and you set the security level in Internet Explorer to low, the portal impersonates the user with the low privileges token.</span></span> <span data-ttu-id="0d6a4-117">Ce jeton n'accorde pas le droit d'écrire dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-117">This token does not have the permissions to write to the event log.</span></span> <span data-ttu-id="0d6a4-118">Si le portail rencontre une erreur, il tente de la noter dans le journal des événements mais n'y parvient pas en raison des faibles privilèges du jeton d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-118">If the portal encounters an error, it attempts to log it to the event log and will fail since the reduced privileges of the user token are not sufficient to access the event log.</span></span>  
  
 <span data-ttu-id="0d6a4-119">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="0d6a4-119">**Resolution**</span></span>  
  
 <span data-ttu-id="0d6a4-120">Si vous voulez aller sur Internet à partir de l'ordinateur local, vous devez ajouter l'adresse http://localhost à la liste des sites de confiance.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-120">If you need to browse from the local computer, you should add http://localhost to the list of trusted sites.</span></span>  
  
#### <a name="to-add-localhost-to-the-list-of-trusted-sites"></a><span data-ttu-id="0d6a4-121">Pour ajouter localhost à la liste des sites de confiance</span><span class="sxs-lookup"><span data-stu-id="0d6a4-121">To add localhost to the list of trusted sites</span></span>  
  
1.  <span data-ttu-id="0d6a4-122">Dans Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-122">In Internet Explorer, click **Tools**, and then click **Internet Options**.</span></span>  
  
2.  <span data-ttu-id="0d6a4-123">Cliquez sur le **sécurité** onglet, puis cliquez sur **Sites de confiance** dans les **sélectionner une zone pour afficher ou modifier les paramètres de sécurité** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-123">Click the **Security** tab, and then click **Trusted Sites** in the **Select a zone to view or change security settings** window.</span></span>  
  
3.  <span data-ttu-id="0d6a4-124">Cliquez sur le **Sites** bouton.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-124">Click the **Sites** button.</span></span>  
  
4.  <span data-ttu-id="0d6a4-125">Dans le **ajouter ce site Web à la zone** zone de texte, tapez **http://localhost**.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-125">In the **Add this website to the zone** text box, type **http://localhost**.</span></span> <span data-ttu-id="0d6a4-126">Si le **exiger un serveur sécurisé (https :) pour tous les sites dans cette zone** case à cocher est activée, désactivez-la, puis cliquez sur le **ajouter** bouton.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-126">If the **Require server verification (https:) for all sites in this zone** check box is selected, clear it and then click the **Add** button.</span></span> <span data-ttu-id="0d6a4-127">Le site, le http://localhost, apparaît dans le **sites Web** liste.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-127">The site, http://localhost, will appear in the **Websites** list.</span></span>  
  
5.  <span data-ttu-id="0d6a4-128">Si nécessaire, restaurez la **exiger un serveur sécurisé (https :) pour tous les sites dans cette zone** case à cocher à son état d’origine.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-128">If necessary, restore the **Require server verification (https:) for all sites in this zone** check box to its original state.</span></span>  
  
6.  <span data-ttu-id="0d6a4-129">Cliquez sur le **fermer** bouton, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-129">Click the **Close** button, and then click **OK**.</span></span>  
  
## <a name="bam-portal-aggregations-do-not-populate-existing-data-when-using-an-ip-address-as-a-url-in-internet-explorer-7"></a><span data-ttu-id="0d6a4-130">Les agrégations du portail BAM n'indiquent pas les données existantes lorsqu'une adresse IP est utilisée en tant qu'URL dans Internet Explorer 7</span><span class="sxs-lookup"><span data-stu-id="0d6a4-130">Bam Portal Aggregations Do Not Populate Existing Data When Using an IP Address as a URL in Internet Explorer 7</span></span>  
 <span data-ttu-id="0d6a4-131">**Problème**</span><span class="sxs-lookup"><span data-stu-id="0d6a4-131">**Problem**</span></span>  
  
 <span data-ttu-id="0d6a4-132">Lorsque vous utilisez une adresse IP en tant qu’URL avec Internet Explorer 7 ou Internet Explorer 8 et [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)], [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] pour afficher le portail BAM, les agrégations affichent le message suivant : « aucun détail.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-132">When using an IP address as a URL with Internet Explorer 7 or Internet Explorer 8 and [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)], [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] to view the BAM portal, aggregations display the following message: "No detail.</span></span> <span data-ttu-id="0d6a4-133">La requête n'a pas pu être traitée. »</span><span class="sxs-lookup"><span data-stu-id="0d6a4-133">The query could not be processed."</span></span>  
  
 <span data-ttu-id="0d6a4-134">**Cause**</span><span class="sxs-lookup"><span data-stu-id="0d6a4-134">**Cause**</span></span>  
  
 <span data-ttu-id="0d6a4-135">Les paramètres de sécurité par défaut d'Internet Explorer 7 ou Internet Explorer 8 empêchent l'accès aux sites lorsque les adresses IPv4 et IPv6 sont utilisées en tant qu'URL.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-135">The default security settings in Internet Explorer 7 or Internet Explorer 8 prevents access to sites using IPv4 and IPv6 addresses as URLs.</span></span>  
  
 <span data-ttu-id="0d6a4-136">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="0d6a4-136">**Resolution**</span></span>  
  
 <span data-ttu-id="0d6a4-137">Ajoutez l'adresse du site à la liste des sites de confiance et activez l'accès aux sources de données sur les domaines.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-137">Add the site address to the trusted sites list and enable access to data sources across domains.</span></span>  
  
#### <a name="to-add-the-ip-address-to-the-trusted-sites-list"></a><span data-ttu-id="0d6a4-138">Pour ajouter l'adresse IP à la liste des sites de confiance</span><span class="sxs-lookup"><span data-stu-id="0d6a4-138">To add the IP address to the trusted sites list</span></span>  
  
1.  <span data-ttu-id="0d6a4-139">Dans Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-139">In Internet Explorer, click **Tools**, and then click **Internet Options**.</span></span>  
  
2.  <span data-ttu-id="0d6a4-140">Cliquez sur le **sécurité** onglet, puis cliquez sur le **sites de confiance** zone de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-140">Click the **Security** tab, and then click the **Trusted sites** security zone.</span></span>  
  
3.  <span data-ttu-id="0d6a4-141">Cliquez sur le **Sites** bouton.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-141">Click the **Sites** button.</span></span>  
  
4.  <span data-ttu-id="0d6a4-142">Dans **ajouter ce site Web à la zone**, tapez l’adresse IP du portail BAM, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-142">In **Add this website to the zone**, type the IP address of the BAM portal, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="0d6a4-143">Cliquez sur **Fermer**, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-143">Click **Close**, and then click **OK**.</span></span>  
  
#### <a name="to-enable-access-to-data-sources-across-domains"></a><span data-ttu-id="0d6a4-144">Pour activer l'accès aux sources de données sur les domaines</span><span class="sxs-lookup"><span data-stu-id="0d6a4-144">To enable access to data sources across domains</span></span>  
  
1.  <span data-ttu-id="0d6a4-145">Dans Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-145">In Internet Explorer, click **Tools**, and then click **Internet Options**.</span></span>  
  
2.  <span data-ttu-id="0d6a4-146">Cliquez sur le **sécurité** onglet, puis cliquez sur le **Sites de confiance** zone de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-146">Click the **Security** tab, and then click the **Trusted Sites** security zone.</span></span>  
  
3.  <span data-ttu-id="0d6a4-147">Cliquez sur le **niveau personnalisé** bouton que vous faites défiler jusqu'à la **divers** nœud de la **paramètres** arborescence.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-147">Click the **Custom Level** button as you scroll down to the **Miscellaneous** node of the **Settings** tree.</span></span>  
  
4.  <span data-ttu-id="0d6a4-148">Dans le **accéder aux sources de données sur plusieurs domaines** nœud, cliquez sur le **activer la case d’option** bouton, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-148">In the **Access data sources across domains** node, click the **Enable radio** button, and then click **OK**.</span></span>  
  
## <a name="bmexe-does-not-run-in-powershell"></a><span data-ttu-id="0d6a4-149">BM.exe ne s'exécute pas dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d6a4-149">BM.exe does not run in PowerShell</span></span>  
 <span data-ttu-id="0d6a4-150">**Problème**</span><span class="sxs-lookup"><span data-stu-id="0d6a4-150">**Problem**</span></span>  
  
 <span data-ttu-id="0d6a4-151">La commande suivante génère une erreur lors de son exécution dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-151">The following command throws an error when run in PowerShell.</span></span>  
  
```  
bm.exe get-config -FileName:config.xml  
```  
  
 <span data-ttu-id="0d6a4-152">**Cause**</span><span class="sxs-lookup"><span data-stu-id="0d6a4-152">**Cause**</span></span>  
  
 <span data-ttu-id="0d6a4-153">PowerShell n'a pas pu localiser le chemin d'accès des fichiers .exe et config.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-153">PowerShell could not locate the path of .exe and config files.</span></span>  
  
 <span data-ttu-id="0d6a4-154">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="0d6a4-154">**Resolution**</span></span>  
  
 <span data-ttu-id="0d6a4-155">Si vous utilisez bm.exe dans PowerShell, spécifiez le chemin d'accès complet des fichiers .exe et config.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-155">If you use bm.exe in PowerShell, specify the full path of .exe and config files.</span></span> <span data-ttu-id="0d6a4-156">Par exemple : `bm.exe get-config -FileName:config.xml` doit être spécifié en tant que `“%BizTalkPathTracking%”\bm.exe get-config -FileName:”%InstallDir%”\Tracking\config.xml`.</span><span class="sxs-lookup"><span data-stu-id="0d6a4-156">For example: `bm.exe get-config -FileName:config.xml` should be specified as `“%BizTalkPathTracking%”\bm.exe get-config -FileName:”%InstallDir%”\Tracking\config.xml`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6a4-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d6a4-157">See Also</span></span>  
 [<span data-ttu-id="0d6a4-158">Planification pour le portail BAM</span><span class="sxs-lookup"><span data-stu-id="0d6a4-158">Planning for the BAM Portal</span></span>](../core/planning-for-the-bam-portal.md)