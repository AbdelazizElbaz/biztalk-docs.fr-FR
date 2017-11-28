---
title: "Déployer et tester l’application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2c86d5f-1849-4b7d-8061-23f156245f5b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56b390ef87ac2ea58d91be2ff16a50f2c3748db2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploy-and-test-the-application"></a><span data-ttu-id="bfa70-102">Déployer et tester l'application</span><span class="sxs-lookup"><span data-stu-id="bfa70-102">Deploy and test the application</span></span>
> [!NOTE]
>  <span data-ttu-id="bfa70-103">Ce didacticiel s'applique uniquement à [!INCLUDE[prague](../includes/prague-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bfa70-103">This tutorial applies to [!INCLUDE[prague](../includes/prague-md.md)] only.</span></span>  
  
 <span data-ttu-id="bfa70-104">Dans cette rubrique, nous allons générer, déployer, configurer et tester l’application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bfa70-104">In this topic, we build, deploy, configure, and test the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
## <a name="build-and-deploy-the-application"></a><span data-ttu-id="bfa70-105">Créer et déployer l'application</span><span class="sxs-lookup"><span data-stu-id="bfa70-105">Build and deploy the application</span></span>  
  
1.  <span data-ttu-id="bfa70-106">Dans l’Explorateur de solutions, cliquez sur le nom de projet BizTalk, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-106">In the Solution Explorer, right-click the BizTalk project name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="bfa70-107">Dans la page Propriété, cliquez sur l'onglet Signature, activez la case à cocher Signer l'assembly, puis dans la liste déroulante choisissez l'option permettant de créer un nouveau fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="bfa70-107">On the Property page, click the Signing tab, select the Sign the assembly check box, and from the drop-down choose the option to create a new strong name key file.</span></span> <span data-ttu-id="bfa70-108">Suivez les instructions pour créer le fichier.</span><span class="sxs-lookup"><span data-stu-id="bfa70-108">Follow the prompts to create the file.</span></span>  
  
3.  <span data-ttu-id="bfa70-109">Enregistrez les modifications apportées au projet.</span><span class="sxs-lookup"><span data-stu-id="bfa70-109">Save changes to the project.</span></span> <span data-ttu-id="bfa70-110">Dans l’Explorateur de solutions, cliquez sur le nom de la solution, puis cliquez sur **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-110">In Solution Explorer, right-click the solution name, and then click **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="bfa70-111">Une fois le projet construit avec succès, dans l’Explorateur de solutions, cliquez sur le nom de la solution, puis cliquez sur **déployer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-111">After project builds successfully, in the Solution Explorer, right-click the solution name, and then click **Deploy Solution**.</span></span>  
  
## <a name="configure-the-application"></a><span data-ttu-id="bfa70-112">Configurez l'application</span><span class="sxs-lookup"><span data-stu-id="bfa70-112">Configure the application</span></span>  
 <span data-ttu-id="bfa70-113">Pour configurer l'application, dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], créez les ports d'envoi et de solution, puis reliez-les à l'orchestration et aux ports Envoi/Réception logiques créés dans le cadre de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="bfa70-113">To configure the application, in [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], create the send and receive ports and then bind them to the orchestration and the logical send/receive ports created as part of the orchestration.</span></span>  
  
1.  <span data-ttu-id="bfa70-114">Créez un port de réception à travers lequel un bon de commande JSON est reçu par l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bfa70-114">Create a receive port through which a JSON purchase order is received by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
    1.  <span data-ttu-id="bfa70-115">Dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **BizTalk Application 1**, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-115">In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Application 1**, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
    2.  <span data-ttu-id="bfa70-116">Fournissez un nom pour le port de réception, puis dans le volet gauche, cliquez sur **emplacements de réception**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-116">Provide a name for the receive port, and then from the left pan, click **Receive Locations**.</span></span> <span data-ttu-id="bfa70-117">Dans le **emplacements de réception** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-117">In the **Receive Locations** tab, click **New**.</span></span>  
  
    3.  <span data-ttu-id="bfa70-118">Spécifiez un nom pour l’emplacement de réception, sélectionnez le type de port **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-118">Specify a name for the receive location, select the port type as **FILE**, and then click **Configure**.</span></span>  
  
    4.  <span data-ttu-id="bfa70-119">Indiquez l'emplacement du dossier où l'emplacement de réception enlèvera le bon de commande JSON entrant.</span><span class="sxs-lookup"><span data-stu-id="bfa70-119">Provide the folder location from where the receive location will pick the incoming JSON purchase order.</span></span> <span data-ttu-id="bfa70-120">Spécifiez `*.json` en tant que le masque de fichier, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-120">Specify `*.json` as the file mask and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="bfa70-121">À partir de la **Pipeline de réception** liste déroulante, sélectionnez **JSONToXml**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-121">From the **Receive Pipeline** drop-down, select **JSONToXml**.</span></span> <span data-ttu-id="bfa70-122">Vous avez créé ce pipeline de réception personnalisé dans l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bfa70-122">You created this custom receive pipeline in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span> <span data-ttu-id="bfa70-123">Cliquez sur le bouton de sélection **(...)**  bouton suivant pour le pipeline, puis sous **étape 1 – Deocde Component**, indiquez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="bfa70-123">Right-click the ellipsis **(…)** button next to the pipeline, and then under **Stage 1 – Deocde Component**, provide the following values:</span></span>  
  
        -   <span data-ttu-id="bfa70-124">RootNode-`ROOT`</span><span class="sxs-lookup"><span data-stu-id="bfa70-124">RootNode - `ROOT`</span></span>  
  
        -   <span data-ttu-id="bfa70-125">RootNodeNamespace –`http://BTSJSON`.</span><span class="sxs-lookup"><span data-stu-id="bfa70-125">RootNodeNamespace –`http://BTSJSON`.</span></span>  
  
         <span data-ttu-id="bfa70-126">Ces valeurs représentent l'espace de noms cible et le nom de nœud racine du schéma du bon de commande XML qui a été généré à partir du bon de commande JSON via l'Assistant Schéma de JSON.</span><span class="sxs-lookup"><span data-stu-id="bfa70-126">These values represent the target namespace and the root node name of the XML purchase order schema that was generated from the JSON purchase order using the JSON schema wizard.</span></span>  
  
    6.  <span data-ttu-id="bfa70-127">Cliquez sur **OK** jusqu'à ce que vous quittez toutes les boîtes de dialogue Ouvrir.</span><span class="sxs-lookup"><span data-stu-id="bfa70-127">Click **OK** until you exit all open dialog boxes.</span></span>  
  
2.  <span data-ttu-id="bfa70-128">Créez un port d'envoi pour l'envoi de messages de la facture JSON.</span><span class="sxs-lookup"><span data-stu-id="bfa70-128">Create a send port for sending out JSON invoice messages.</span></span>  
  
    1.  <span data-ttu-id="bfa70-129">Dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **BizTalk Application 1**, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **statique Port d’envoi unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-129">In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Application 1**, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
    2.  <span data-ttu-id="bfa70-130">Spécifiez un nom pour le port d’envoi, sélectionnez le type de port **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-130">Specify a name for the send port, select the port type as **FILE**, and then click **Configure**.</span></span>  
  
    3.  <span data-ttu-id="bfa70-131">Indiquez l'emplacement du dossier où le port d'envoi copie la facture JSON sortante.</span><span class="sxs-lookup"><span data-stu-id="bfa70-131">Provide the folder location where the send port copies the outgoing JSON invoice.</span></span> <span data-ttu-id="bfa70-132">Spécifiez `%MessageID%.json` comme le nom de fichier puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-132">Specify `%MessageID%.json` as the file name and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="bfa70-133">À partir de la **Pipeline d’envoi** liste déroulante, sélectionnez **XmlToJSON**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-133">From the **Send Pipeline** drop-down, select **XmlToJSON**, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="bfa70-134">Cliquez sur **OK** jusqu'à ce que vous quittez toutes les boîtes de dialogue Ouvrir.</span><span class="sxs-lookup"><span data-stu-id="bfa70-134">Click **OK** until you exit all open dialog boxes.</span></span>  
  
3.  <span data-ttu-id="bfa70-135">Enfin, liez les ports logiques que vous avez créés dans le cadre de l'orchestration aux ports physiques que vous venez de créer pour configurer l'application.</span><span class="sxs-lookup"><span data-stu-id="bfa70-135">Finally, bind the logical ports you created as part of the orchestration to the physical ports you created now to configure the application.</span></span>  
  
    1.  <span data-ttu-id="bfa70-136">Avec le bouton droit **BizTalk Application 1**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-136">Right-click **BizTalk Application 1**, and then click **Configure**.</span></span>  
  
    2.  <span data-ttu-id="bfa70-137">Dans le volet gauche, cliquez sur **ProcessPO**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-137">From the left pane, click **ProcessPO**.</span></span> <span data-ttu-id="bfa70-138">Dans le volet droit, associez un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] héberger, mapper les ports logiques aux ports physiques, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-138">From the right pane, associate a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host, map the logical ports to the physical ports, and then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="bfa70-139">Avec le bouton droit **BizTalk Application 1**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="bfa70-139">Right-click **BizTalk Application 1**, and then click **Start**.</span></span>  
  
## <a name="test-the-application"></a><span data-ttu-id="bfa70-140">Tester l'application</span><span class="sxs-lookup"><span data-stu-id="bfa70-140">Test the application</span></span>  
  
1.  <span data-ttu-id="bfa70-141">Accédez à l’exemple que vous avez téléchargé et à partir de la **TestMessage** dossier, copiez **JsonPurchaseOrder.json**et le coller dans le dossier que vous avez associé à l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="bfa70-141">Navigate to the sample you downloaded, and from the **TestMessage** folder, copy **JsonPurchaseOrder.json**, and paste it in the folder you associated with the receive location.</span></span> <span data-ttu-id="bfa70-142">Attendez que le fichier disparaisse.</span><span class="sxs-lookup"><span data-stu-id="bfa70-142">Wait till the file disappears.</span></span>  
  
2.  <span data-ttu-id="bfa70-143">Accédez au dossier que vous avez associé au port d'envoi créé.</span><span class="sxs-lookup"><span data-stu-id="bfa70-143">Navigate to the folder that you associated with the send port you created.</span></span> <span data-ttu-id="bfa70-144">Notez qu’un   ***\<GUID >*.json** fichier est disponible dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="bfa70-144">Notice that a ***\<GUID>*.json** file is available in the folder.</span></span> <span data-ttu-id="bfa70-145">Ouvrez le fichier et vérifiez qu'il s'agit du message de la facture.</span><span class="sxs-lookup"><span data-stu-id="bfa70-145">Open the file and verify that it’s the invoice message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa70-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfa70-146">See Also</span></span>  
 [<span data-ttu-id="bfa70-147">Traitement des messages JSON à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="bfa70-147">Processing JSON messages using BizTalk Server</span></span>](../core/processing-json-messages-using-biztalk-server.md)