---
title: "Étape 5 : Configurer les Pages Web du partenaire commercial | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38c3054d-932a-42b6-a821-8b30604d8426
caps.latest.revision: "38"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3f1dce6a68dc334f9f5f30b1aae938ada6f612a
ms.sourcegitcommit: 9aaed443492b74729171fef79c634bff561af929
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2017
---
# <a name="step-5-configure-the-trading-partner-web-pages"></a><span data-ttu-id="e52bb-102">Étape 5 : Configurer les Pages Web du partenaire commercial</span><span class="sxs-lookup"><span data-stu-id="e52bb-102">Step 5: Configure the Trading Partner Web Pages</span></span>
<span data-ttu-id="e52bb-103">![L’étape 5 de 11](../core/media/tut-step5-of-11.gif "Tut_Step5_of_11")</span><span class="sxs-lookup"><span data-stu-id="e52bb-103">![Step 5 of 11](../core/media/tut-step5-of-11.gif "Tut_Step5_of_11")</span></span>  
  
 <span data-ttu-id="e52bb-104">Au cours de cette étape, vous allez effectuer les tâches suivantes pour configurer les pages Web d'un partenaire commercial :</span><span class="sxs-lookup"><span data-stu-id="e52bb-104">In this step, you perform the following tasks to set up trading partner Web pages:</span></span>  
  
-   <span data-ttu-id="e52bb-105">Activer le filtre ISAPI de réception HTTP BTS requis pour le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="e52bb-105">Enable the BTS HTTP Receive ISAPI filter that is required for HTTP transport.</span></span>  
  
-   <span data-ttu-id="e52bb-106">Configurer un dossier et une page aspx pour acheminer l'accusé de réception 997 vers l'organisation partenaire Fabrikam via le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="e52bb-106">Set up a folder and an aspx page to route the 997 acknowledgment to the partner organization Fabrikam using HTTP transport.</span></span> <span data-ttu-id="e52bb-107">Le répertoire virtuel Fabrikam dépose l’accusé de réception 997 dans le \\dossier _997ToFabrikam, qui est appelé dans le paramètre Destination_URL du port de 997 envoi.</span><span class="sxs-lookup"><span data-stu-id="e52bb-107">The Fabrikam virtual directory drops the 997 acknowledgment into the \\_997ToFabrikam folder, which is called out in the Destination_URL setting of the 997 send port.</span></span>  
  
-   <span data-ttu-id="e52bb-108">Configurer la page ASPX pour acheminer le message original vers l'organisation d'origine Contoso.</span><span class="sxs-lookup"><span data-stu-id="e52bb-108">Set up the ASPX page to route the original message to the home organization Contoso.</span></span> <span data-ttu-id="e52bb-109">Le répertoire virtuel Contoso utilise BTSHttpReceive.dll pour recevoir le message AS2 et l'envoyer à l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="e52bb-109">The Contoso virtual directory uses BTSHttpReceive.dll to receive the AS2 message and submit it to the receive location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e52bb-110">Les procédures incluses dans cette rubrique s'appliquent à IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="e52bb-110">The procedures provided in this topic are for IIS 7.0.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e52bb-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e52bb-111">Prerequisites</span></span>  
 <span data-ttu-id="e52bb-112">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e52bb-112">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-enable-the-bts-isapi-filter"></a><span data-ttu-id="e52bb-113">Pour activer le filtre ISAPI BTS</span><span class="sxs-lookup"><span data-stu-id="e52bb-113">To enable the BTS ISAPI Filter</span></span>  
  
1.  <span data-ttu-id="e52bb-114">Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-114">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="e52bb-115">Sélectionnez l’entrée de serveur Web racine et dans le **affichage des fonctionnalités**, double-cliquez sur **mappages de gestionnaires** puis, dans le **Actions** volet, cliquez sur **ajouter un mappage de scripts**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-115">Select the root Web server entry and in the **Features View**, double-click **Handler Mappings** and then in the **Actions** pane, click **Add Script Map**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e52bb-116">La configuration du mappage de scripts au niveau du serveur Web entraîne l'application de ce mappage à tous les sites Web enfants.</span><span class="sxs-lookup"><span data-stu-id="e52bb-116">Configuring the script mapping at the Web server level will cause this mapping to apply to all child Web sites.</span></span> <span data-ttu-id="e52bb-117">Si vous souhaitez limiter le mappage à un site Web ou un dossier virtuel spécifique, sélectionnez le site ou le dossier cible plutôt que le serveur Web.</span><span class="sxs-lookup"><span data-stu-id="e52bb-117">If you wish to restrict the mapping to a specific Web site or virtual folder, select the target site or folder instead of the Web server.</span></span>  
  
3.  <span data-ttu-id="e52bb-118">Dans le **ajouter un mappage de scripts** boîte de dialogue, entrez `BtsHttpReceive.dll` dans les **chemin d’accès de la demande** champ.</span><span class="sxs-lookup"><span data-stu-id="e52bb-118">In the **Add Script Map** dialog box, enter `BtsHttpReceive.dll` in the **Request path** field.</span></span>  
  
4.  <span data-ttu-id="e52bb-119">Dans le **exécutable** , cliquez sur le **points de suspension (...)**  bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive.</span><span class="sxs-lookup"><span data-stu-id="e52bb-119">In the **Executable** field, click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive.</span></span> <span data-ttu-id="e52bb-120">Sélectionnez **BtsHttpReceive.dll**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-120">Select **BtsHttpReceive.dll**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="e52bb-121">Entrez `BizTalk HTTP Receive` dans les `Name` champ, puis cliquez sur **Restrictions des demandes**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-121">Enter `BizTalk HTTP Receive` in the `Name` field, and then click **Request Restrictions**.</span></span>  
  
6.  <span data-ttu-id="e52bb-122">Dans le **Restrictions des demandes** boîte de dialogue, sélectionnez le **verbes** onglet, puis sélectionnez **un des verbes suivants**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-122">In the **Request Restrictions** dialog box, select the **Verbs** tab and then select **One of the following verbs**.</span></span> <span data-ttu-id="e52bb-123">Entrez `POST` le verbe.</span><span class="sxs-lookup"><span data-stu-id="e52bb-123">Enter `POST` as the verb.</span></span>  
  
7.  <span data-ttu-id="e52bb-124">Sur le **accès** onglet, sélectionnez **Script**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-124">On the **Access** tab, select **Script**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="e52bb-125">Cliquez sur **OK** lorsque vous êtes invité à autoriser l’extension ISAPI, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-125">Click **OK** and when prompted to allow the ISAPI extension, click **Yes**.</span></span>  
  
9. <span data-ttu-id="e52bb-126">Cliquez sur l’entrée BTSHttpReceive.dll, puis sélectionnez **modifier les autorisations de fonction**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-126">Right-click the BTSHttpReceive.dll entry, and then select **Edit Feature Permissions**.</span></span>  
  
10. <span data-ttu-id="e52bb-127">Vérifiez que **en lecture**, **Script** et **Execute** sont sélectionnées, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-127">Ensure that **Read**, **Script** and **Execute** are selected, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="e52bb-128">Cliquez sur **affichage des fonctionnalités**, puis double-cliquez sur **Restrictions ISAPI et CGI**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-128">Click **Features View**, and then double-click **ISAPI and CGI Restrictions**.</span></span>  
  
12. <span data-ttu-id="e52bb-129">Assurez-vous qu’il existe une entrée pour BTSHTTPReceive.dll et qui **Restriction** a la valeur **autorisées**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-129">Ensure that an entry for BTSHTTPReceive.dll exists, and that **Restriction** is set to **Allowed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e52bb-130">L'entrée Restrictions ISAPI et CGI pour BTSHTTPReceive.dll est définie automatiquement lors de la création du mappage de scripts.</span><span class="sxs-lookup"><span data-stu-id="e52bb-130">The ISAPI and CGI Restriction entry for BTSHTTPReceive.dll is created automatically when you create the script map.</span></span>  
  
### <a name="to-configure-the-fabrikam-web-page"></a><span data-ttu-id="e52bb-131">Pour configurer la page Web Fabrikam</span><span class="sxs-lookup"><span data-stu-id="e52bb-131">To configure the Fabrikam Web page</span></span>  
  
1.  <span data-ttu-id="e52bb-132">Avec le bouton droit dans le Gestionnaire des services Internet, **Pools d’applications** et sélectionnez **ajouter un Pool d’applications**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-132">In IIS Manager, right-click **Application Pools** and select **Add Application Pool**.</span></span>  
  
2.  <span data-ttu-id="e52bb-133">Dans le **ajouter un Pool d’applications** boîte de dialogue, entrez **BizTalkAppPool** dans **nom**, puis sélectionnez **.NET Framework V4.0.30210** dans le **Version du .NET framework** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e52bb-133">In the **Add Application Pool** dialog box, enter **BizTalkAppPool** in **Name**, and then select **.NET Framework V4.0.30210** in the **.NET Framework version** drop-down list.</span></span> <span data-ttu-id="e52bb-134">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-134">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e52bb-135">Le numéro de version peut varier selon la version de [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] installée sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e52bb-135">The version number may vary depending on the version of [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] installed on the machine.</span></span>  
  
3.  <span data-ttu-id="e52bb-136">Sélectionnez **Pools d’applications**, dans le **affichage des fonctionnalités** sélectionnez **BizTalkAppPool**, puis cliquez sur **paramètres avancés** dans les  **Actions** volet.</span><span class="sxs-lookup"><span data-stu-id="e52bb-136">Select **Application Pools**, in the **Features View** select **BizTalkAppPool**, and then click **Advanced Settings** in the **Actions** pane.</span></span>  
  
4.  <span data-ttu-id="e52bb-137">Dans le **paramètres avancés** boîte de dialogue, définissez **Applications Enable 32 bits** à **True**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-137">In the **Advanced Settings** dialog box, set **Enable 32-Bit Applications** to **True**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e52bb-138">Cette étape est uniquement requise sur un ordinateur 64 bits si vous souhaitez exécuter IIS en mode 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e52bb-138">This step is required only on a 64-bit machine if you want IIS to run in a 32-bit mode.</span></span>  
  
5.  <span data-ttu-id="e52bb-139">Sélectionnez **identité** puis cliquez sur le **points de suspension (...)**  bouton.</span><span class="sxs-lookup"><span data-stu-id="e52bb-139">Select **Identity** and then click the **ellipsis (…)** button.</span></span>  
  
6.  <span data-ttu-id="e52bb-140">Dans le **identité du Pool d’applications** boîte de dialogue, sélectionnez **compte personnalisé** puis cliquez sur **définir**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-140">In the **Application Pool Identity** dialog box, select **Custom account** and then click **Set**.</span></span>  
  
7.  <span data-ttu-id="e52bb-141">Entrez le **nom d’utilisateur** et **mot de passe** pour un compte d’utilisateur qui est membre du groupe Administrateurs, entrez le mot de passe **confirmer le mot de passe** puis cliquez sur **OK** trois fois pour retourner le Gestionnaire des services Internet.</span><span class="sxs-lookup"><span data-stu-id="e52bb-141">Enter the **User name** and **Password** for a user account that is a member of the administrators group, enter the password in **Confirm password** and then click **OK** three times to return to the IIS Manager.</span></span>  
  
8.  <span data-ttu-id="e52bb-142">Dans le Gestionnaire des services Internet, ouvrez le **Sites** dossier.</span><span class="sxs-lookup"><span data-stu-id="e52bb-142">In IIS Manager, open the **Sites** folder.</span></span> <span data-ttu-id="e52bb-143">Cliquez sur le **Site Web par défaut**, puis sélectionnez **ajouter une Application**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-143">Right-click the **Default Web Site**, and then select **Add Application**.</span></span>  
  
9. <span data-ttu-id="e52bb-144">Dans le **ajouter une Application** boîte de dialogue, entrez **Fabrikam** dans **Alias**, puis cliquez sur **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-144">In the **Add Application** dialog box, enter **Fabrikam** in **Alias**, and then click **Select**.</span></span>  
  
10. <span data-ttu-id="e52bb-145">Dans le **sélectionner un Pool d’applications** boîte de dialogue, sélectionnez **BizTalkAppPool** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-145">In the **Select Application Pool** dialog box, select **BizTalkAppPool** and click **OK**.</span></span>  
  
11. <span data-ttu-id="e52bb-146">Cliquez sur le **points de suspension (...)**  bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Fabrikam pour le **chemin d’accès physique**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-146">Click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Fabrikam for the **Physical path**.</span></span>  
  
12. <span data-ttu-id="e52bb-147">Cliquez sur **des paramètres de Test** et vérifiez qu’il n’y a aucune erreur affiché dans le **tester la connexion** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e52bb-147">Click **Test Settings** and verify that there are no errors displayed in the **Test Connection** dialog box.</span></span> <span data-ttu-id="e52bb-148">Cliquez sur **Fermer**, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-148">Click **Close**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="e52bb-149">Dans le Gestionnaire des services Internet, sélectionnez le répertoire virtuel Fabrikam et dans **affichage des fonctionnalités**, double-cliquez sur **authentification**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-149">In IIS Manager, select the Fabrikam virtual directory and in **Features View**, double-click **Authentication**.</span></span>  
  
14. <span data-ttu-id="e52bb-150">Dans **authentification**, sélectionnez **l’authentification anonyme** et vérifiez que le **état** est **activé**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-150">In **Authentication**, select **Anonymous Authentication** and verify that the **Status** is **Enabled**.</span></span> <span data-ttu-id="e52bb-151">Si le **état** est **désactivé**, cliquez sur **activer** dans les **Actions** volet.</span><span class="sxs-lookup"><span data-stu-id="e52bb-151">If the **Status** is **Disabled**, click **Enable** in the **Actions** pane.</span></span>  
  
### <a name="to-configure-the-contoso-web-page"></a><span data-ttu-id="e52bb-152">Pour configurer la page Web Contoso</span><span class="sxs-lookup"><span data-stu-id="e52bb-152">To configure the Contoso Web page</span></span>  
  
1.  <span data-ttu-id="e52bb-153">Dans le Gestionnaire des services Internet, ouvrez le **Sites** dossier.</span><span class="sxs-lookup"><span data-stu-id="e52bb-153">In IIS Manager, open the **Sites** folder.</span></span> <span data-ttu-id="e52bb-154">Cliquez sur le **Site Web par défaut** , puis sélectionnez **ajouter une Application**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-154">Right-click the **Default Web Site** and then select **Add Application**.</span></span>  
  
2.  <span data-ttu-id="e52bb-155">Dans le **ajouter une Application** boîte de dialogue, entrez **Contoso** dans **Alias**, puis cliquez sur **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-155">In the **Add Application** dialog box, enter **Contoso** in **Alias**, and then click **Select**.</span></span>  
  
3.  <span data-ttu-id="e52bb-156">Dans le **sélectionner un Pool d’applications** boîte de dialogue, sélectionnez **BizTalkAppPool** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-156">In the **Select Application Pool** dialog box, select **BizTalkAppPool** and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e52bb-157">Le pool d'applications BizTalkAppPool, créé précédemment lors de la configuration de la page Web Fabrikam, doit être défini sur l'identité d'un utilisateur membre du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="e52bb-157">The BizTalkAppPool was created previously when configuring the Fabrikam Web page, and should be set to the identity of a user that is a member of the administrators group.</span></span>  
  
4.  <span data-ttu-id="e52bb-158">Cliquez sur le **points de suspension (...)**  bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive pour le **chemin d’accès physique**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-158">Click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive for the **Physical path**.</span></span>  
  
5.  <span data-ttu-id="e52bb-159">Cliquez sur **des paramètres de Test** et vérifiez qu’il n’y a aucune erreur affiché dans le **tester la connexion** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e52bb-159">Click **Test Settings** and verify that there are no errors displayed in the **Test Connection** dialog box.</span></span> <span data-ttu-id="e52bb-160">Cliquez sur **Fermer**, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-160">Click **Close**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="e52bb-161">Dans le Gestionnaire des services Internet, sélectionnez le répertoire virtuel Contoso et dans le **affichage des fonctionnalités**, double-cliquez sur **authentification**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-161">In IIS Manager, select the Contoso virtual directory and in the **Features View**, double-click **Authentication**.</span></span>  
  
7.  <span data-ttu-id="e52bb-162">Dans **authentification**, sélectionnez **l’authentification anonyme** et vérifiez que le **état** est **activé**.</span><span class="sxs-lookup"><span data-stu-id="e52bb-162">In **Authentication**, select **Anonymous Authentication** and verify that the **Status** is **Enabled**.</span></span> <span data-ttu-id="e52bb-163">Si le **état** est **désactivé**, cliquez sur **activer** dans les **Actions** volet.</span><span class="sxs-lookup"><span data-stu-id="e52bb-163">If the **Status** is **Disabled**, click **Enable** in the **Actions** pane.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e52bb-164">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e52bb-164">Next Steps</span></span>  
 <span data-ttu-id="e52bb-165">Vous configurez l’emplacement de réception (**Receive_AS2**) pour recevoir le message AS2 de Fabrikam, comme décrit dans [étape 6 : configurer l’emplacement de réception EDI AS2](../core/step-6-configure-the-edi-as2-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="e52bb-165">You configure the receive location (**Receive_AS2**) to receive the AS2 message from Fabrikam, as described in [Step 6: Configure the EDI-AS2 Receive Location](../core/step-6-configure-the-edi-as2-receive-location.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e52bb-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e52bb-166">See Also</span></span>  
 [<span data-ttu-id="e52bb-167">Didacticiel 3 : Didacticiel AS2</span><span class="sxs-lookup"><span data-stu-id="e52bb-167">Tutorial 3: AS2 Tutorial</span></span>](../core/tutorial-3-as2-tutorial.md)
