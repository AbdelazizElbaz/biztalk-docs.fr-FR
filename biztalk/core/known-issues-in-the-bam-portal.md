---
title: "Problèmes connus avec le portail BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e681e910-c664-479c-86f3-a6ae0ec97775
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61cbfa298590c62b359045b6c7372501d8ef397e
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="known-issues-in-the-bam-portal"></a><span data-ttu-id="776ca-102">Problèmes connus dans le portail BAM</span><span class="sxs-lookup"><span data-stu-id="776ca-102">Known Issues in the BAM Portal</span></span>
<span data-ttu-id="776ca-103">Cette rubrique contient des informations destinées à vous aider à identifier et à résoudre les problèmes que vous pouvez rencontrer lorsque vous utilisez le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="776ca-103">This topic contains information to help you identify and resolve issues that can occur while you are using the BAM portal.</span></span>  
  
## <a name="errors-occur-when-the-bam-portal-and-ie-are-on-the-same-computer-and-security-settings-are-low"></a><span data-ttu-id="776ca-104">Erreurs se produisent lorsque le portail BAM et Internet Explorer sont sur le même ordinateur et les paramètres de sécurité faible</span><span class="sxs-lookup"><span data-stu-id="776ca-104">Errors occur when the BAM Portal and IE are on the same computer, and Security Settings are Low</span></span>  
 <span data-ttu-id="776ca-105">**Problème**</span><span class="sxs-lookup"><span data-stu-id="776ca-105">**Problem**</span></span>  
  
 <span data-ttu-id="776ca-106">Lorsque vous utilisez Internet Explorer, vous pouvez rencontrer le message d’erreur **erreur serveur dans ' / BAM' Application** dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="776ca-106">When using Internet Explorer, you may encounter the error message **Server Error in '/BAM' Application** under the following circumstances:</span></span>  
  
-   <span data-ttu-id="776ca-107">Lorsque vous cliquez sur une activité associée qui pointe vers une instance d'activité inexistante</span><span class="sxs-lookup"><span data-stu-id="776ca-107">While clicking a related activity that points to a non-existing activity instance.</span></span>  
  
-   <span data-ttu-id="776ca-108">Tout en cliquant sur le **enregistrer l’alerte** bouton dans le scénario suivant :</span><span class="sxs-lookup"><span data-stu-id="776ca-108">While clicking the **Save Alert** button in the following scenario:</span></span>  
  
    -   <span data-ttu-id="776ca-109">Vous créez une requête sur le **ActivitySearch** page, puis cliquez sur **définir l’alerte**.</span><span class="sxs-lookup"><span data-stu-id="776ca-109">You create a query on the **ActivitySearch** page and then click **Set Alert**.</span></span>  
  
    -   <span data-ttu-id="776ca-110">Vous renseignez les champs d’alerte, puis sur **enregistrer l’alerte**.</span><span class="sxs-lookup"><span data-stu-id="776ca-110">You complete the alert fields and then click **Save Alert**.</span></span>  
  
    -   <span data-ttu-id="776ca-111">Vous cliquez sur le bouton Précédent.</span><span class="sxs-lookup"><span data-stu-id="776ca-111">You click the back button.</span></span>  
  
    -   <span data-ttu-id="776ca-112">Vous cliquez sur le **enregistrer l’alerte** bouton Nouveau.</span><span class="sxs-lookup"><span data-stu-id="776ca-112">You click the **Save Alert** button again.</span></span>  
  
 <span data-ttu-id="776ca-113">**Cause**</span><span class="sxs-lookup"><span data-stu-id="776ca-113">**Cause**</span></span>  
  
 <span data-ttu-id="776ca-114">Exécutez Internet Explorer avec le niveau de sécurité lorsque la valeur basse, requêtes Web sont exécutées avec de faibles privilèges.</span><span class="sxs-lookup"><span data-stu-id="776ca-114">When running Internet Explorer with the security level set to low, Web requests are executed with low privileges.</span></span> <span data-ttu-id="776ca-115">Pour répondre aux exigences de sécurité intégrée de Windows, Internet Explorer transmet un jeton d'utilisateur avec des privilèges minimaux.</span><span class="sxs-lookup"><span data-stu-id="776ca-115">To fulfill the Windows integrated security challenge, Internet Explorer passes a user token with low privileges.</span></span>  
  
 <span data-ttu-id="776ca-116">Si vous utilisez Internet Explorer sur l'ordinateur sur lequel le portail BAM est installé et que vous définissez un niveau de sécurité faible dans Internet Explorer, le portail emprunte l'identité de l'utilisateur possédant le jeton associé à de faibles privilèges.</span><span class="sxs-lookup"><span data-stu-id="776ca-116">If you are using Internet Explorer on the same computer as the one on which the BAM portal is installed, and you set the security level in Internet Explorer to low, the portal impersonates the user with the low privileges token.</span></span> <span data-ttu-id="776ca-117">Ce jeton n'accorde pas le droit d'écrire dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="776ca-117">This token does not have the permissions to write to the event log.</span></span> <span data-ttu-id="776ca-118">Si le portail rencontre une erreur, il tente de la noter dans le journal des événements mais n'y parvient pas en raison des faibles privilèges du jeton d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="776ca-118">If the portal encounters an error, it attempts to log it to the event log and will fail since the reduced privileges of the user token are not sufficient to access the event log.</span></span>  
  
 <span data-ttu-id="776ca-119">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="776ca-119">**Resolution**</span></span>  
  
 <span data-ttu-id="776ca-120">Si vous voulez aller sur Internet à partir de l'ordinateur local, vous devez ajouter l'adresse http://localhost à la liste des sites de confiance.</span><span class="sxs-lookup"><span data-stu-id="776ca-120">If you need to browse from the local computer, you should add http://localhost to the list of trusted sites.</span></span>  
  
#### <a name="add-localhost-to-the-list-of-trusted-sites"></a><span data-ttu-id="776ca-121">Ajouter localhost à la liste des sites de confiance</span><span class="sxs-lookup"><span data-stu-id="776ca-121">Add localhost to the list of trusted sites</span></span>  
  
1.  <span data-ttu-id="776ca-122">Dans Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="776ca-122">In Internet Explorer, click **Tools**, and then click **Internet Options**.</span></span>  
  
2.  <span data-ttu-id="776ca-123">Cliquez sur le **sécurité** onglet, puis cliquez sur **Sites de confiance** dans les **sélectionner une zone pour afficher ou modifier les paramètres de sécurité** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="776ca-123">Click the **Security** tab, and then click **Trusted Sites** in the **Select a zone to view or change security settings** window.</span></span>  
  
3.  <span data-ttu-id="776ca-124">Cliquez sur le **Sites** bouton.</span><span class="sxs-lookup"><span data-stu-id="776ca-124">Click the **Sites** button.</span></span>  
  
4.  <span data-ttu-id="776ca-125">Dans le **ajouter ce site Web à la zone** zone de texte, tapez **http://localhost**.</span><span class="sxs-lookup"><span data-stu-id="776ca-125">In the **Add this website to the zone** text box, type **http://localhost**.</span></span> <span data-ttu-id="776ca-126">Si le **exiger un serveur sécurisé (https :) pour tous les sites dans cette zone** case à cocher est activée, désactivez-la, puis cliquez sur le **ajouter** bouton.</span><span class="sxs-lookup"><span data-stu-id="776ca-126">If the **Require server verification (https:) for all sites in this zone** check box is selected, clear it and then click the **Add** button.</span></span> <span data-ttu-id="776ca-127">Le site, le http://localhost, apparaît dans le **sites Web** liste.</span><span class="sxs-lookup"><span data-stu-id="776ca-127">The site, http://localhost, will appear in the **Websites** list.</span></span>  
  
5.  <span data-ttu-id="776ca-128">Si nécessaire, restaurez la **exiger un serveur sécurisé (https :) pour tous les sites dans cette zone** case à cocher à son état d’origine.</span><span class="sxs-lookup"><span data-stu-id="776ca-128">If necessary, restore the **Require server verification (https:) for all sites in this zone** check box to its original state.</span></span>  
  
6.  <span data-ttu-id="776ca-129">Cliquez sur le **fermer** bouton, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="776ca-129">Click the **Close** button, and then click **OK**.</span></span>  
  
## <a name="bam-portal-aggregations-do-not-populate-existing-data-when-using-an-ip-address-as-a-url-in-internet-explorer"></a><span data-ttu-id="776ca-130">Agrégations du portail BAM ne remplissent pas les données existantes lors de l’utilisation d’une adresse IP en tant qu’URL dans Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="776ca-130">Bam Portal Aggregations Do Not Populate Existing Data When Using an IP Address as a URL in Internet Explorer</span></span>
 <span data-ttu-id="776ca-131">**Problème**</span><span class="sxs-lookup"><span data-stu-id="776ca-131">**Problem**</span></span>  
  
 <span data-ttu-id="776ca-132">Lorsque vous utilisez une adresse IP en tant qu’URL avec Internet Explorer pour afficher le portail BAM, les agrégations affichent le message suivant : « aucun détail.</span><span class="sxs-lookup"><span data-stu-id="776ca-132">When using an IP address as a URL with Internet Explorer to view the BAM portal, aggregations display the following message: "No detail.</span></span> <span data-ttu-id="776ca-133">La requête n'a pas pu être traitée. »</span><span class="sxs-lookup"><span data-stu-id="776ca-133">The query could not be processed."</span></span>  
  
 <span data-ttu-id="776ca-134">**Cause**</span><span class="sxs-lookup"><span data-stu-id="776ca-134">**Cause**</span></span>  
  
 <span data-ttu-id="776ca-135">Les paramètres de sécurité par défaut dans Internet Explorer peuvent empêcher l’accès à des sites à l’aide des adresses IPv4 et IPv6 en tant qu’URL.</span><span class="sxs-lookup"><span data-stu-id="776ca-135">The default security settings in Internet Explorer may prevent access to sites using IPv4 and IPv6 addresses as URLs.</span></span>  
  
 <span data-ttu-id="776ca-136">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="776ca-136">**Resolution**</span></span>  
  
 <span data-ttu-id="776ca-137">Ajoutez l'adresse du site à la liste des sites de confiance et activez l'accès aux sources de données sur les domaines.</span><span class="sxs-lookup"><span data-stu-id="776ca-137">Add the site address to the trusted sites list and enable access to data sources across domains.</span></span>  
  
#### <a name="add-the-ip-address-to-the-trusted-sites-list"></a><span data-ttu-id="776ca-138">Ajouter l’adresse IP à la liste des sites de confiance</span><span class="sxs-lookup"><span data-stu-id="776ca-138">Add the IP address to the trusted sites list</span></span>  
  
1.  <span data-ttu-id="776ca-139">Dans Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="776ca-139">In Internet Explorer, click **Tools**, and then click **Internet Options**.</span></span>  
  
2.  <span data-ttu-id="776ca-140">Cliquez sur le **sécurité** onglet, puis cliquez sur le **sites de confiance** zone de sécurité.</span><span class="sxs-lookup"><span data-stu-id="776ca-140">Click the **Security** tab, and then click the **Trusted sites** security zone.</span></span>  
  
3.  <span data-ttu-id="776ca-141">Cliquez sur le **Sites** bouton.</span><span class="sxs-lookup"><span data-stu-id="776ca-141">Click the **Sites** button.</span></span>  
  
4.  <span data-ttu-id="776ca-142">Dans **ajouter ce site Web à la zone**, tapez l’adresse IP du portail BAM, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="776ca-142">In **Add this website to the zone**, type the IP address of the BAM portal, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="776ca-143">Cliquez sur **Fermer**, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="776ca-143">Click **Close**, and then click **OK**.</span></span>  
  
#### <a name="enable-access-to-data-sources-across-domains"></a><span data-ttu-id="776ca-144">Activer l’accès aux sources de données sur plusieurs domaines</span><span class="sxs-lookup"><span data-stu-id="776ca-144">Enable access to data sources across domains</span></span>  
  
1.  <span data-ttu-id="776ca-145">Dans Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="776ca-145">In Internet Explorer, click **Tools**, and then click **Internet Options**.</span></span>  
  
2.  <span data-ttu-id="776ca-146">Cliquez sur le **sécurité** onglet, puis cliquez sur le **Sites de confiance** zone de sécurité.</span><span class="sxs-lookup"><span data-stu-id="776ca-146">Click the **Security** tab, and then click the **Trusted Sites** security zone.</span></span>  
  
3.  <span data-ttu-id="776ca-147">Cliquez sur le **niveau personnalisé** bouton que vous faites défiler jusqu'à la **divers** nœud de la **paramètres** arborescence.</span><span class="sxs-lookup"><span data-stu-id="776ca-147">Click the **Custom Level** button as you scroll down to the **Miscellaneous** node of the **Settings** tree.</span></span>  
  
4.  <span data-ttu-id="776ca-148">Dans le **accéder aux sources de données sur plusieurs domaines** nœud, cliquez sur le **activer la case d’option** bouton, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="776ca-148">In the **Access data sources across domains** node, click the **Enable radio** button, and then click **OK**.</span></span>  
  
## <a name="bmexe-does-not-run-in-powershell"></a><span data-ttu-id="776ca-149">BM.exe ne s'exécute pas dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="776ca-149">BM.exe does not run in PowerShell</span></span>  
 <span data-ttu-id="776ca-150">**Problème**</span><span class="sxs-lookup"><span data-stu-id="776ca-150">**Problem**</span></span>  
  
 <span data-ttu-id="776ca-151">La commande suivante génère une erreur lors de son exécution dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="776ca-151">The following command throws an error when run in PowerShell.</span></span>  
  
```  
bm.exe get-config -FileName:config.xml  
```  
  
 <span data-ttu-id="776ca-152">**Cause**</span><span class="sxs-lookup"><span data-stu-id="776ca-152">**Cause**</span></span>  
  
 <span data-ttu-id="776ca-153">PowerShell n'a pas pu localiser le chemin d'accès des fichiers .exe et config.</span><span class="sxs-lookup"><span data-stu-id="776ca-153">PowerShell could not locate the path of .exe and config files.</span></span>  
  
 <span data-ttu-id="776ca-154">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="776ca-154">**Resolution**</span></span>  
  
 <span data-ttu-id="776ca-155">Si vous utilisez bm.exe dans PowerShell, spécifiez le chemin d'accès complet des fichiers .exe et config.</span><span class="sxs-lookup"><span data-stu-id="776ca-155">If you use bm.exe in PowerShell, specify the full path of .exe and config files.</span></span> <span data-ttu-id="776ca-156">Par exemple : `bm.exe get-config -FileName:config.xml` doit être spécifié en tant que `“%BizTalkPathTracking%”\bm.exe get-config -FileName:”%InstallDir%”\Tracking\config.xml`.</span><span class="sxs-lookup"><span data-stu-id="776ca-156">For example: `bm.exe get-config -FileName:config.xml` should be specified as `“%BizTalkPathTracking%”\bm.exe get-config -FileName:”%InstallDir%”\Tracking\config.xml`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="776ca-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="776ca-157">See Also</span></span>  
 [<span data-ttu-id="776ca-158">Planification du portail BAM</span><span class="sxs-lookup"><span data-stu-id="776ca-158">Planning for the BAM Portal</span></span>](../core/planning-for-the-bam-portal.md)