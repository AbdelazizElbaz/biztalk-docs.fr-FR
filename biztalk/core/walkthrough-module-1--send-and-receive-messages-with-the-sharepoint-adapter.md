---
title: "Procédure pas à pas : Module 1 - envoi et réception de Messages avec Windows SharePoint Services adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services, creating sites
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapter tutorials, receiving messages
- security, Windows SharePoint Services
- creating, Windows SharePoint Services site
- Windows SharePoint Services, security
- Windows SharePoint Services, document libraries
- Windows SharePoint Services adapters, security
- Windows SharePoint Services
- Windows SharePoint Services adapter tutorials, sending messages
ms.assetid: 6494aef5-bb1d-4a41-8186-1d49625a1013
caps.latest.revision: "41"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8e83297233c4f8ac51ad90f488437a6c259691a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="walkthrough-module-1---sending-and-receiving-messages-with-the-windows-sharepoint-services-adapter"></a><span data-ttu-id="63c46-102">Procédure pas à pas : Module 1 - envoi et réception de Messages avec l’adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="63c46-102">Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter</span></span>
<span data-ttu-id="63c46-103">Cette procédure décrit la configuration de Windows SharePoint Services et de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de manière à ce que vous puissiez envoyer et recevoir un message via l'adaptateur Windows SharePoint Services et le routage basé sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="63c46-103">This walkthrough shows you how to configure Windows SharePoint Services and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] so you can send and receive a message using the Windows SharePoint Services Adapter and content-based routing (CBR).</span></span> <span data-ttu-id="63c46-104">Ce dernier dispense de l'inscription aux messages pour les messages liés à des ports spécifiques.</span><span class="sxs-lookup"><span data-stu-id="63c46-104">Content-based routing eliminates the need for message subscription for messages that are deterministically bound to specific ports.</span></span> <span data-ttu-id="63c46-105">Il offre également plus de souplesse aux utilisateurs souhaitant acheminer des messages en se basant sur les propriétés d'enveloppe ou simplement sur les propriétés de configuration des ports de réception.</span><span class="sxs-lookup"><span data-stu-id="63c46-105">It also provides additional flexibility for users who want to route messages based on envelope properties or simply based on receive port configuration properties.</span></span> <span data-ttu-id="63c46-106">Pour une présentation de l’adaptateur Windows SharePoint Services, consultez [quel est l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="63c46-106">For an introduction to the Windows SharePoint Services adapter, see [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="63c46-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="63c46-107">Prerequisites</span></span>  
 <span data-ttu-id="63c46-108">La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="63c46-108">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
-   <span data-ttu-id="63c46-109">Vous devez disposer d’un déploiement de serveur unique avec une installation complète de BizTalk Server s’exécutant [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63c46-109">You must have a single-server deployment with a complete installation of BizTalk Server running on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].</span></span>  
  
 <span data-ttu-id="63c46-110">Pour plus d’informations sur l’utilisation de l’adaptateur Windows SharePoint Services dans un déploiement multiserveur, consultez [configuration et déploiement de l’adaptateur Windows SharePoint Services](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="63c46-110">For information about using the Windows SharePoint Services adapter in a multiserver deployment, see [Setting Up and Deploying the Windows SharePoint Services Adapter](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="configure-windows-sharepoint-services"></a><span data-ttu-id="63c46-111">Configurer Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="63c46-111">Configure Windows SharePoint Services</span></span>  
 <span data-ttu-id="63c46-112">Cette procédure permet de créer un site Web de niveau supérieur SharePoint contenant trois bibliothèques de documents.</span><span class="sxs-lookup"><span data-stu-id="63c46-112">In this procedure you create a SharePoint top-level Web site that contains three document libraries.</span></span> <span data-ttu-id="63c46-113">L'adaptateur Windows SharePoint Services utilise ces bibliothèques pour déplacer un message d'une bibliothèque source vers une bibliothèque de destination.</span><span class="sxs-lookup"><span data-stu-id="63c46-113">The Windows SharePoint Services adapter uses these libraries to move a message from a source library to a destination library.</span></span> <span data-ttu-id="63c46-114">Ce message est également archivé dans une bibliothèque de documents.</span><span class="sxs-lookup"><span data-stu-id="63c46-114">This message is also archived in a document library.</span></span> <span data-ttu-id="63c46-115">Cette procédure permet de créer le site Windows Sharepoint Services auquel accède l'adaptateur Windows Sharepoint Services au cours de cette procédure pas à pas, ainsi que de définir les droits d'accès des utilisateurs à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="63c46-115">This procedure must be done to provide the Windows Sharepoint Services site that is accessed by the Windows Sharepoint Services adapter in this walkthrough and to set user rights to enable access to this site.</span></span>  
  
#### <a name="create-a-windows-sharepoint-services-site"></a><span data-ttu-id="63c46-116">Pour créer un site Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="63c46-116">Create a Windows SharePoint Services site</span></span>  
  
1.  <span data-ttu-id="63c46-117">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Administration centrale de SharePoint.**</span><span class="sxs-lookup"><span data-stu-id="63c46-117">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration.**</span></span>  
  
2.  <span data-ttu-id="63c46-118">Sous **Configuration du serveur virtuel**, cliquez sur **créer un site Web de niveau supérieur**.</span><span class="sxs-lookup"><span data-stu-id="63c46-118">Under **Virtual Server Configuration**, click **Create a top-level Web site**.</span></span>  
  
3.  <span data-ttu-id="63c46-119">Sous **liste des serveurs virtuels**, sélectionnez le site Web que vous avez installé l’adaptateur Windows SharePoint Services sur.</span><span class="sxs-lookup"><span data-stu-id="63c46-119">Under **Virtual Server List**, select the Web site that you installed the Windows SharePoint Services Adapter on.</span></span> <span data-ttu-id="63c46-120">Par exemple, `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="63c46-120">For example, `Default Web Site`.</span></span>  
  
4.  <span data-ttu-id="63c46-121">Dans le **adresse de Site Web** section, dans le **nom de l’URL** , tapez `WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="63c46-121">In the **Web Site Address** section, in the **URL name** field, type `WSSAdapterWalkthrough`.</span></span>  
  
5.  <span data-ttu-id="63c46-122">Dans le **Site propriétaire de la Collection** section, dans le **champ nom d’utilisateur,** tapez un nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="63c46-122">In the **Site Collection Owner** section, in the **User name field,** type a user name.</span></span> <span data-ttu-id="63c46-123">Cet utilisateur correspond au propriétaire du site Web et n'a besoin d'aucune autorisation spéciale dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63c46-123">This user will be the owner for the Web site and does not need special permissions in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
6.  <span data-ttu-id="63c46-124">Dans le **Site propriétaire de la Collection** section, dans le **messagerie** , tapez une adresse de messagerie.</span><span class="sxs-lookup"><span data-stu-id="63c46-124">In the **Site Collection Owner** section, in the **E-mail** field, type in an e-mail address.</span></span>  
  
7.  <span data-ttu-id="63c46-125">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63c46-125">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="63c46-126">Sur le **premier niveau Site créé avec succès** , cliquez sur le nouveau site Web de niveau supérieur vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="63c46-126">On the **Top-Level Site Successfully Created** page, click the new top-level Web site you just created.</span></span> <span data-ttu-id="63c46-127">Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="63c46-127">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
9. <span data-ttu-id="63c46-128">Sélectionnez le **Site d’équipe** modèle dans la liste des modèles, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63c46-128">Select the **Team Site** template from the list of templates, and then click **OK**.</span></span> <span data-ttu-id="63c46-129">La page d'accueil du site Web d'équipe s'affiche.</span><span class="sxs-lookup"><span data-stu-id="63c46-129">This will open the Team Web Site Home page.</span></span>  
  
#### <a name="create-a-source-document-library"></a><span data-ttu-id="63c46-130">Pour créer une bibliothèque de documents « sources »</span><span class="sxs-lookup"><span data-stu-id="63c46-130">Create a "Source" document library</span></span>  
  
1.  <span data-ttu-id="63c46-131">Dans la page accueil du Site Web Team, dans la barre de navigation supérieure, cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="63c46-131">On the Team Web Site Home page, on the top navigation bar, click **Create**.</span></span>  
  
2.  <span data-ttu-id="63c46-132">Sous **bibliothèques de documents**, cliquez sur **bibliothèque de documents**.</span><span class="sxs-lookup"><span data-stu-id="63c46-132">Under **Document Libraries**, click **Document Library**.</span></span>  
  
3.  <span data-ttu-id="63c46-133">Dans le **nom et Description** section, dans le **champ nom,** type `Source`.</span><span class="sxs-lookup"><span data-stu-id="63c46-133">In the **Name and Description** section, in the **Name field,** type `Source`.</span></span>  
  
4.  <span data-ttu-id="63c46-134">Dans le **Navigation** section, sélectionnez **Oui** pour afficher cette bibliothèque de formulaires dans la barre de lancement rapide.</span><span class="sxs-lookup"><span data-stu-id="63c46-134">In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.</span></span>  
  
5.  <span data-ttu-id="63c46-135">Dans le **modèle de Document** section, dans le **modèle de Document** la liste déroulante, sélectionnez `None`.</span><span class="sxs-lookup"><span data-stu-id="63c46-135">In the **Document Template** section, in the **Document Template** drop-down list, select `None`.</span></span>  
  
6.  <span data-ttu-id="63c46-136">Cliquez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="63c46-136">Click **Create**.</span></span> <span data-ttu-id="63c46-137">La bibliothèque de documents est créée et vous êtes redirigé vers la bibliothèque vide.</span><span class="sxs-lookup"><span data-stu-id="63c46-137">The document library will be created and you will be redirected to the empty library.</span></span>  
  
#### <a name="create-a-destination-document-library"></a><span data-ttu-id="63c46-138">Pour créer une bibliothèque de documents de « destination »</span><span class="sxs-lookup"><span data-stu-id="63c46-138">Create a "Destination" document library</span></span>  
  
1.  <span data-ttu-id="63c46-139">Dans la page accueil du Site Web Team, dans la barre de navigation supérieure, cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="63c46-139">On the Team Web Site Home page, on the top navigation bar, click **Create**.</span></span>  
  
2.  <span data-ttu-id="63c46-140">Sous **bibliothèques de documents**, cliquez sur **bibliothèque de documents**.</span><span class="sxs-lookup"><span data-stu-id="63c46-140">Under **Document Libraries**, click **Document Library**.</span></span>  
  
3.  <span data-ttu-id="63c46-141">Dans le **nom et Description** section, dans le **champ nom**, type `Destination`.</span><span class="sxs-lookup"><span data-stu-id="63c46-141">In the **Name and Description** section, in the **Name field**, type `Destination`.</span></span>  
  
4.  <span data-ttu-id="63c46-142">Dans le **Navigation** section, sélectionnez **Oui** pour afficher cette bibliothèque de formulaires dans la barre de lancement rapide.</span><span class="sxs-lookup"><span data-stu-id="63c46-142">In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.</span></span>  
  
5.  <span data-ttu-id="63c46-143">Dans le **modèle de Document** section, dans le **modèle de Document** la liste déroulante, sélectionnez `None`.</span><span class="sxs-lookup"><span data-stu-id="63c46-143">In the **Document Template** section, in the **Document Template** drop-down list, select `None`.</span></span>  
  
6.  <span data-ttu-id="63c46-144">Cliquez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="63c46-144">Click **Create**.</span></span> <span data-ttu-id="63c46-145">La bibliothèque de documents est créée et vous êtes redirigé vers la bibliothèque vide.</span><span class="sxs-lookup"><span data-stu-id="63c46-145">The document library will be created and you will be redirected to the empty library.</span></span>  
  
#### <a name="create-an-archive-document-library"></a><span data-ttu-id="63c46-146">Pour créer une bibliothèque de documents « d'archive »</span><span class="sxs-lookup"><span data-stu-id="63c46-146">Create an "Archive" document library</span></span>  
  
1.  <span data-ttu-id="63c46-147">Dans la page accueil du Site Web Team, dans la barre de navigation supérieure, cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="63c46-147">On the Team Web Site Home page, on the top navigation bar, click **Create**.</span></span>  
  
2.  <span data-ttu-id="63c46-148">Sous **bibliothèques de documents**, cliquez sur **bibliothèque de documents**.</span><span class="sxs-lookup"><span data-stu-id="63c46-148">Under **Document Libraries**, click **Document Library**.</span></span>  
  
3.  <span data-ttu-id="63c46-149">Dans le **nom** et la section de Description, dans le **champ nom**, type `Archive`.</span><span class="sxs-lookup"><span data-stu-id="63c46-149">In the **Name** and Description section, in the **Name field**, type `Archive`.</span></span>  
  
4.  <span data-ttu-id="63c46-150">Dans le **Navigation** section, sélectionnez **Oui** pour afficher cette bibliothèque de formulaires dans la barre de lancement rapide.</span><span class="sxs-lookup"><span data-stu-id="63c46-150">In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.</span></span>  
  
5.  <span data-ttu-id="63c46-151">Dans le **modèle de Document** section, dans le **modèle de Document** la liste déroulante, sélectionnez `None`.</span><span class="sxs-lookup"><span data-stu-id="63c46-151">In the **Document Template** section, in the **Document Template** drop-down list, select `None`.</span></span>  
  
6.  <span data-ttu-id="63c46-152">Cliquez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="63c46-152">Click **Create**.</span></span> <span data-ttu-id="63c46-153">La bibliothèque de documents est créée et vous êtes redirigé vers la bibliothèque vide.</span><span class="sxs-lookup"><span data-stu-id="63c46-153">The document library will be created and you will be redirected to the empty library.</span></span>  
  
7.  <span data-ttu-id="63c46-154">Fermez le site Web `WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="63c46-154">Close the `WSSAdapterWalkthrough` Web site.</span></span>  
  
8.  <span data-ttu-id="63c46-155">Fermer le **Administration centrale de SharePoint** site Web.</span><span class="sxs-lookup"><span data-stu-id="63c46-155">Close the **SharePoint Central Administration** Web site.</span></span>  
  
#### <a name="configure-windows-security"></a><span data-ttu-id="63c46-156">Pour configurer la sécurité de Windows</span><span class="sxs-lookup"><span data-stu-id="63c46-156">Configure Windows security</span></span>  
  
1.  <span data-ttu-id="63c46-157">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="63c46-157">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="63c46-158">Dans l’arborescence de la console, développez **utilisateurs et groupes locaux**, puis cliquez sur **groupes**.</span><span class="sxs-lookup"><span data-stu-id="63c46-158">In the console tree, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
3.  <span data-ttu-id="63c46-159">Avec le bouton droit le **hôtes avec SharePoint activé** , cliquez sur **ajouter au groupe**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="63c46-159">Right-click the **SharePoint Enabled Hosts** group, click **Add to Group**, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="63c46-160">Dans le **boîte de dialogue Sélectionnez utilisateurs, ordinateurs ou groupes**, sous **Entrez les noms des objets à sélectionner**, tapez le nom du compte que vous avez configuré l’Instance d’hôte BizTalk Server pour s’exécuter sous, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63c46-160">In the **Select Users, Computers, or Groups dialog box**, under **Enter the object names to select**, type the name of the account that you configured the BizTalk Server Host Instance to run under, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="63c46-161">Dans l’arborescence de la console, développez **Services et Applications**, puis cliquez sur **Services**.</span><span class="sxs-lookup"><span data-stu-id="63c46-161">In the console tree, expand **Services and Applications**, and then click **Services**.</span></span>  
  
6.  <span data-ttu-id="63c46-162">Avec le bouton droit **groupe BizTalk des services BizTalk : < Nom_hôte_biztalk >**, puis cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="63c46-162">Right-click **BizTalk Service BizTalk Group: <BizTalk_Host_Name>**, and then click **Restart**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63c46-163"><Nom_hôte_BizTalk> correspond au nom de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="63c46-163"><BizTalk_Host_Name> is the name of your host.</span></span> <span data-ttu-id="63c46-164">Par défaut, il s’agit de `BizTalkServerApplication`.</span><span class="sxs-lookup"><span data-stu-id="63c46-164">By Default, this is `BizTalkServerApplication`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63c46-165">L'adhésion ne prend pas effet tant que le service n'a pas été redémarré.</span><span class="sxs-lookup"><span data-stu-id="63c46-165">Membership does not take effect until the service is restarted.</span></span>  
  
7.  <span data-ttu-id="63c46-166">Fermer **gestion de l’ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="63c46-166">Close **Computer Management**.</span></span>  
  
#### <a name="configure-sharepoint-security"></a><span data-ttu-id="63c46-167">Pour configurer la sécurité de SharePoint</span><span class="sxs-lookup"><span data-stu-id="63c46-167">Configure SharePoint security</span></span>  
  
1.  <span data-ttu-id="63c46-168">Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé</span><span class="sxs-lookup"><span data-stu-id="63c46-168">Open a Web browser and navigate to the URL of the site you created.</span></span> <span data-ttu-id="63c46-169">Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="63c46-169">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="63c46-170">Dans la page accueil du Site Web Team, dans la barre de navigation supérieure, cliquez sur **paramètres du Site**.</span><span class="sxs-lookup"><span data-stu-id="63c46-170">On the Team Web Site Home page, on the top navigation bar, click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="63c46-171">Sous **Administration**, cliquez sur **gérer les utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="63c46-171">Under **Administration**, click **Manage users**.</span></span>  
  
4.  <span data-ttu-id="63c46-172">Cliquez sur **Ajouter des utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="63c46-172">Click **Add Users**.</span></span>  
  
5.  <span data-ttu-id="63c46-173">Dans **étape 1 : choisissez les utilisateurs**, tapez le nom du compte que le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Instance d’hôte est en cours d’exécution sous.</span><span class="sxs-lookup"><span data-stu-id="63c46-173">In **Step 1: Choose Users**, type the name of the account that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Host Instance is running under.</span></span>  
  
6.  <span data-ttu-id="63c46-174">Dans **étape 2 : choisissez les groupes de sites**, sélectionnez le **lecteur** et **collaborateur** cases à cocher.</span><span class="sxs-lookup"><span data-stu-id="63c46-174">In **Step 2: Choose Site Groups**, select the **Reader** and **Contributor** check boxes.</span></span>  
  
7.  <span data-ttu-id="63c46-175">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="63c46-175">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="63c46-176">Désactivez le **envoyer le message suivant pour informer ces utilisateurs qu’ils ont été ajoutés à présent** case à cocher, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="63c46-176">Clear the **Send the following e-mail to let these users now they've been added** check box, and then click **Finish**.</span></span>  
  
9. <span data-ttu-id="63c46-177">Fermez le site Web `WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="63c46-177">Close the `WSSAdapterWalkthrough` Web site.</span></span>  
  
## <a name="create-and-configure-the-biztalk-server-ports"></a><span data-ttu-id="63c46-178">Pour créer et configurer les ports BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="63c46-178">Create and configure the BizTalk Server ports</span></span>  
 <span data-ttu-id="63c46-179">Cette procédure permet de créer et de configurer les ports de réception, les emplacements de réception et les ports d'envoi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="63c46-179">In this procedure you will create and configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive ports, receive locations, and send ports for the Windows SharePoint Services adapter.</span></span> <span data-ttu-id="63c46-180">Ces ports représentent des points d'entrée allant vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou sortant de celui-ci dont disposent les documents reçus et envoyés par l'adaptateur Windows Sharepoint Services.</span><span class="sxs-lookup"><span data-stu-id="63c46-180">These ports are points of entry into and out of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for documents received and sent by the Windows Sharepoint Services adapter.</span></span>  
  
#### <a name="create-the-receive-port"></a><span data-ttu-id="63c46-181">Créer le port de réception</span><span class="sxs-lookup"><span data-stu-id="63c46-181">Create the receive port</span></span>  
  
1.  <span data-ttu-id="63c46-182">Cliquez sur **Démarrer**, **tous les programmes**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="63c46-182">Click **Start**, **All Programs**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration.**</span></span>  
  
2.  <span data-ttu-id="63c46-183">Développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, avec le bouton droit **Ports de réception**, cliquez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel...**</span><span class="sxs-lookup"><span data-stu-id="63c46-183">Expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, right-click **Receive Ports**, click **New**, and then click **One-way Receive Port…**</span></span>  
  
3.  <span data-ttu-id="63c46-184">Dans le **propriétés du Port de réception** boîte de dialogue **général**, type `FromSource` dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="63c46-184">In the **Receive Port Properties** dialog box, under **General**, type `FromSource` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="63c46-185">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63c46-185">Click **OK**.</span></span>  
  
#### <a name="create-the-receive-location"></a><span data-ttu-id="63c46-186">Pour créer un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="63c46-186">Create the receive location</span></span>  
  
1.  <span data-ttu-id="63c46-187">Dans le **Console Administration de BizTalk**, avec le bouton droit le **emplacements de réception** nœud, cliquez sur **nouveau**, puis cliquez sur **l’emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="63c46-187">In the **BizTalk Administration Console**, right-click the **Receive Locations** node, click **New**, and then click **One-way Receive Location**.</span></span>  
  
2.  <span data-ttu-id="63c46-188">Dans le **sélectionner un Port de réception** boîte de dialogue, sélectionnez `FromSource`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63c46-188">In the **Select a Receive Port** dialog box, select `FromSource`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="63c46-189">Dans le **propriétés de l’emplacement de réception** boîte de dialogue **général**, type `SourceLocation` dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="63c46-189">In the **Receive Location Properties** dialog box, under **General**, type `SourceLocation` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="63c46-190">Dans le **Transport** section, dans le **Type** la liste déroulante, sélectionnez `Windows``SharePoint``Services`.</span><span class="sxs-lookup"><span data-stu-id="63c46-190">In the **Transport** section, in the **Type** drop-down list, select `Windows``SharePoint``Services`.</span></span>  
  
5.  <span data-ttu-id="63c46-191">Cliquez sur **configurer** pour configurer les propriétés de l’adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="63c46-191">Click **Configure** to configure the Windows SharePoint Services adapter properties.</span></span>  
  
6.  <span data-ttu-id="63c46-192">Dans le **Port du Service Web adaptateur** propriété, tapez le numéro de port du serveur virtuel sur lequel le service Web de l’adaptateur Windows SharePoint Services a été installé.</span><span class="sxs-lookup"><span data-stu-id="63c46-192">In the **Adapter Web Service Port** property, type the port number of the virtual server where the Windows SharePoint Services adapter Web service was installed.</span></span> <span data-ttu-id="63c46-193">Par défaut, il s’agit de port 80.</span><span class="sxs-lookup"><span data-stu-id="63c46-193">By default, this is port 80.</span></span>  
  
7.  <span data-ttu-id="63c46-194">Type `Archive` dans les **emplacement d’Archive** propriété.</span><span class="sxs-lookup"><span data-stu-id="63c46-194">Type `Archive` in the **Archive Location** property.</span></span>  
  
8.  <span data-ttu-id="63c46-195">Type `10` dans les **fréquence d’interrogation** propriété.</span><span class="sxs-lookup"><span data-stu-id="63c46-195">Type `10` in the **Polling Interval** property.</span></span>  
  
9. <span data-ttu-id="63c46-196">Tapez l’URL de votre site SharePoint dans le **ShareP**oint propriété Url du Site.</span><span class="sxs-lookup"><span data-stu-id="63c46-196">Type the URL to your SharePoint site in the **ShareP**oint Site Url property.</span></span> <span data-ttu-id="63c46-197">Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="63c46-197">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
10. <span data-ttu-id="63c46-198">Type `Source` pour le **bibliothèque de documents Source** propriété.</span><span class="sxs-lookup"><span data-stu-id="63c46-198">Type `Source` for the **Source Document Library** property.</span></span>  
  
11. <span data-ttu-id="63c46-199">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63c46-199">Click **OK**.</span></span>  
  
12. <span data-ttu-id="63c46-200">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, sélectionnez `BizTalkServerApplication` comme le **Gestionnaire de réception**.</span><span class="sxs-lookup"><span data-stu-id="63c46-200">In the **Receive Location Properties** dialog box, select `BizTalkServerApplication` as the **Receive handler**.</span></span>  
  
13. <span data-ttu-id="63c46-201">Dans le **pipeline de réception** la liste déroulante, sélectionnez `PassThruReceive`.</span><span class="sxs-lookup"><span data-stu-id="63c46-201">In the **Receive pipeline** drop-down list, select `PassThruReceive`.</span></span>  
  
14. <span data-ttu-id="63c46-202">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63c46-202">Click **OK**.</span></span>  
  
#### <a name="create-the-send-port"></a><span data-ttu-id="63c46-203">Pour créer un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="63c46-203">Create the send port</span></span>  
  
1.  <span data-ttu-id="63c46-204">Dans le **Console Administration de BizTalk**, avec le bouton droit le **Ports d’envoi** nœud, cliquez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique** .</span><span class="sxs-lookup"><span data-stu-id="63c46-204">In the **BizTalk Administration Console**, right-click the **Send Ports** node, click **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="63c46-205">Dans le **propriétés de Port d’envoi** boîte de dialogue **général**, type `SendToDestination` dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="63c46-205">In the **Send Port Properties** dialog box, under **General**, type `SendToDestination` in the **Name** field.</span></span>  
  
3.  <span data-ttu-id="63c46-206">Dans le **Transport** section, sélectionnez `Windows SharePoint Services` pour le type.</span><span class="sxs-lookup"><span data-stu-id="63c46-206">In the **Transport** section, select `Windows SharePoint Services` for the type.</span></span>  
  
4.  <span data-ttu-id="63c46-207">Cliquez sur **configurer** pour configurer les propriétés de l’adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="63c46-207">Click **Configure** to configure the Windows SharePoint Services adapter properties.</span></span>  
  
5.  <span data-ttu-id="63c46-208">Dans le **Port du Service Web adaptateur** propriété, tapez le numéro de port du serveur virtuel sur lequel le service Web de l’adaptateur Windows SharePoint Services a été installé.</span><span class="sxs-lookup"><span data-stu-id="63c46-208">In the **Adapter Web Service Port** property, type the port number of the virtual server where the Windows SharePoint Services adapter Web service was installed.</span></span> <span data-ttu-id="63c46-209">Par défaut, il s’agit de port 80.</span><span class="sxs-lookup"><span data-stu-id="63c46-209">By default, this is port 80.</span></span>  
  
6.  <span data-ttu-id="63c46-210">Tapez dans `Destination` pour le **dossier de Destination** propriété.</span><span class="sxs-lookup"><span data-stu-id="63c46-210">Type in `Destination` for the **Destination Folder** property.</span></span>  
  
7.  <span data-ttu-id="63c46-211">Tapez dans `PurchaseOrder1-%MessageID%.xml` pour le **nom de fichier** propriété.</span><span class="sxs-lookup"><span data-stu-id="63c46-211">Type in `PurchaseOrder1-%MessageID%.xml` for the **Filename** property.</span></span>  
  
8.  <span data-ttu-id="63c46-212">Définir le **remplacer** propriété `Yes`.</span><span class="sxs-lookup"><span data-stu-id="63c46-212">Set the **Overwrite** property to `Yes`.</span></span>  
  
9. <span data-ttu-id="63c46-213">Tapez l’URL de votre site SharePoint dans le **Url du Site SharePoint** propriété.</span><span class="sxs-lookup"><span data-stu-id="63c46-213">Type in the URL to your SharePoint site in the **SharePoint Site Url** property.</span></span> <span data-ttu-id="63c46-214">Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="63c46-214">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
10. <span data-ttu-id="63c46-215">Définir le **intégration de Microsoft Office** propriété `No`.</span><span class="sxs-lookup"><span data-stu-id="63c46-215">Set the **Microsoft Office Integration** property to `No`.</span></span>  
  
11. <span data-ttu-id="63c46-216">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63c46-216">Click **OK**.</span></span>  
  
12. <span data-ttu-id="63c46-217">Dans le **boîte de dialogue Propriétés de Port d’envoi**, dans le **Gestionnaire d’envoi** la liste déroulante, sélectionnez `BizTalkServerApplication`.</span><span class="sxs-lookup"><span data-stu-id="63c46-217">In the **Send Port Properties dialog box**, in the **Send handler** drop-down list, select `BizTalkServerApplication`.</span></span>  
  
13. <span data-ttu-id="63c46-218">Dans le **pipeline d’envoi** la liste déroulante, sélectionnez `PassThruTransmit`.</span><span class="sxs-lookup"><span data-stu-id="63c46-218">In the **Send pipeline** drop-down list, select `PassThruTransmit`.</span></span>  
  
14. <span data-ttu-id="63c46-219">Cliquez sur le **filtres** onglet.</span><span class="sxs-lookup"><span data-stu-id="63c46-219">Click the **Filters** tab.</span></span>  
  
15. <span data-ttu-id="63c46-220">Sélectionnez `WSS.InListName` dans les **propriété** champ.</span><span class="sxs-lookup"><span data-stu-id="63c46-220">Select `WSS.InListName` in the **Property** field.</span></span>  
  
16. <span data-ttu-id="63c46-221">Sélectionnez `==` dans les **opérateur** champ.</span><span class="sxs-lookup"><span data-stu-id="63c46-221">Select `==` in the **Operator** field.</span></span>  
  
17. <span data-ttu-id="63c46-222">Type `Source` dans les **valeur** champ.</span><span class="sxs-lookup"><span data-stu-id="63c46-222">Type `Source` in the **Value** field.</span></span>  
  
18. <span data-ttu-id="63c46-223">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63c46-223">Click **OK**.</span></span>  
  
## <a name="enable-and-start-the-receive-location-and-receive-port"></a><span data-ttu-id="63c46-224">Pour activer et démarrer l'emplacement et le port de réception</span><span class="sxs-lookup"><span data-stu-id="63c46-224">Enable and start the receive location and receive port</span></span>  
 <span data-ttu-id="63c46-225">Ces procédures permettent d'activer l'emplacement de réception et de démarrer le port de réception.</span><span class="sxs-lookup"><span data-stu-id="63c46-225">In these procedures you enable the receive location and start the receive port.</span></span> <span data-ttu-id="63c46-226">Vous devez mener à bien cette procédure afin de permettre à l'adaptateur Windows Sharepoint Services d'envoyer et de recevoir des messages via le port d'envoi et l'emplacement de réception spécifiés.</span><span class="sxs-lookup"><span data-stu-id="63c46-226">This procedure must be completed to allow the Windows Sharepoint Services adapter to send and receive messages through the specified send port and receive location.</span></span>  
  
#### <a name="enable-the-receive-location"></a><span data-ttu-id="63c46-227">Pour activer l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="63c46-227">Enable the receive location</span></span>  
  
1.  <span data-ttu-id="63c46-228">Dans le **Console Administration de BizTalk**, cliquez sur le **emplacements de réception** nœud.</span><span class="sxs-lookup"><span data-stu-id="63c46-228">In the **BizTalk Administration Console**, click the **Receive Locations** node.</span></span>  
  
2.  <span data-ttu-id="63c46-229">Avec le bouton droit `SourceLocation`, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="63c46-229">Right-click `SourceLocation`, and then click **Enable**.</span></span>  
  
#### <a name="start-the-send-port"></a><span data-ttu-id="63c46-230">Pour démarrer le port d'envoi</span><span class="sxs-lookup"><span data-stu-id="63c46-230">Start the send port</span></span>  
  
1.  <span data-ttu-id="63c46-231">Dans le **Console Administration de BizTalk**, cliquez sur le **Ports d’envoi** nœud.</span><span class="sxs-lookup"><span data-stu-id="63c46-231">In the **BizTalk Administration Console**, click the **Send Ports** node.</span></span>  
  
2.  <span data-ttu-id="63c46-232">Avec le bouton droit `SendToDestination`, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="63c46-232">Right-click `SendToDestination`, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="63c46-233">Fermer le **Console Administration de BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="63c46-233">Close the **BizTalk Administration Console**.</span></span>  
  
## <a name="sending-a-message-through-the-system"></a><span data-ttu-id="63c46-234">Pour envoyer un message via le système</span><span class="sxs-lookup"><span data-stu-id="63c46-234">Sending a message through the system</span></span>  
 <span data-ttu-id="63c46-235">Cette procédure permet de créer un document XML et de le télécharger sur le site Web Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="63c46-235">In this procedure you create an XML document and upload it to the Windows SharePoint Services Web site.</span></span> <span data-ttu-id="63c46-236">L'adaptateur Windows SharePoint Services prend ce message, l'archive dans la bibliothèque de documents d'archive, puis l'envoie dans la bibliothèque de documents de destination.</span><span class="sxs-lookup"><span data-stu-id="63c46-236">The Windows SharePoint Services adapter will take that message, archive it in the Archive document library, and then send it to the Destination document library.</span></span> <span data-ttu-id="63c46-237">Cette procédure montre comment un document circule depuis un site Web SharePoint, via [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vers un site Web SharePoint Services, à l'aide de l'adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="63c46-237">This procedure demonstrates how a document flows from a Sharepoint web site, through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and to a Sharepoint Services Web site using the Windows Sharepoint Services adapter.</span></span>  
  
#### <a name="create-a-working-directory"></a><span data-ttu-id="63c46-238">Pour créer un répertoire de travail</span><span class="sxs-lookup"><span data-stu-id="63c46-238">Create a working directory</span></span>  
  
-   <span data-ttu-id="63c46-239">Créez un répertoire sur votre ordinateur appelé **WSSAdapterWalkthrough**.</span><span class="sxs-lookup"><span data-stu-id="63c46-239">Create a directory on your computer called **WSSAdapterWalkthrough**.</span></span> <span data-ttu-id="63c46-240">Par exemple, `C:\WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="63c46-240">For example, `C:\WSSAdapterWalkthrough`.</span></span>  
  
#### <a name="create-an-xml-file"></a><span data-ttu-id="63c46-241">Pour créer un fichier XML</span><span class="sxs-lookup"><span data-stu-id="63c46-241">Create an XML file</span></span>  
  
1.  <span data-ttu-id="63c46-242">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Accessoires**, puis cliquez sur **le bloc-notes.**</span><span class="sxs-lookup"><span data-stu-id="63c46-242">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Notepad.**</span></span>  
  
2.  <span data-ttu-id="63c46-243">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="63c46-243">Type the following:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <PurchaseOrder>  
        <ID>1001</ID>  
        <FirstName>John</FirstName>  
        <LastName>Doe</LastName>  
        <Amount>750</Amount>  
    </PurchaseOrder>  
    ```  
  
3.  <span data-ttu-id="63c46-244">Enregistrez le fichier dans votre répertoire de travail sous le nom `PurchaseOrder1.xml`</span><span class="sxs-lookup"><span data-stu-id="63c46-244">Save the file in your working directory as `PurchaseOrder1.xml`.</span></span> <span data-ttu-id="63c46-245">Par exemple, `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`.</span><span class="sxs-lookup"><span data-stu-id="63c46-245">For example, `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`.</span></span>  
  
#### <a name="upload-the-xml-file"></a><span data-ttu-id="63c46-246">Pour télécharger le fichier XML</span><span class="sxs-lookup"><span data-stu-id="63c46-246">Upload the XML file</span></span>  
  
1.  <span data-ttu-id="63c46-247">Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé lors de la tâche précédente</span><span class="sxs-lookup"><span data-stu-id="63c46-247">Open a Web browser and navigate to the URL of the site you created in the last task.</span></span> <span data-ttu-id="63c46-248">Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="63c46-248">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="63c46-249">Sur le côté gauche, sous **Documents**, cliquez sur **Source**.</span><span class="sxs-lookup"><span data-stu-id="63c46-249">On the left side, under **Documents**, click **Source**.</span></span>  
  
3.  <span data-ttu-id="63c46-250">Cliquez sur **télécharger un Document**.</span><span class="sxs-lookup"><span data-stu-id="63c46-250">Click **Upload Document**.</span></span>  
  
4.  <span data-ttu-id="63c46-251">Dans le **nom** , tapez ou accédez au fichier XML que vous avez créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="63c46-251">In the **Name** box, type or browse to the XML file you created above.</span></span> <span data-ttu-id="63c46-252">Par exemple, `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`, puis cliquez sur **enregistrer et fermer**.</span><span class="sxs-lookup"><span data-stu-id="63c46-252">For example, `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`, and then click **Save and Close**.</span></span> <span data-ttu-id="63c46-253">Le fichier doit s'afficher dans la liste.</span><span class="sxs-lookup"><span data-stu-id="63c46-253">You should now be able to see the file in the list.</span></span>  
  
5.  <span data-ttu-id="63c46-254">Actualisez la fenêtre du navigateur.</span><span class="sxs-lookup"><span data-stu-id="63c46-254">Refresh the browser window.</span></span> <span data-ttu-id="63c46-255">Le fichier `PurchaseOrder1.xml` n'apparaît plus dans cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="63c46-255">The `PurchaseOrder1.xml` file will no longer be listed in this library.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63c46-256">Comme la fréquence d'interrogation est définie sur 10 secondes, il peut être nécessaire d'actualiser plusieurs fois le navigateur.</span><span class="sxs-lookup"><span data-stu-id="63c46-256">You may have to refresh the browser a few times since the polling interval is set at 10 seconds.</span></span>  
  
6.  <span data-ttu-id="63c46-257">Dans la barre de navigation supérieure, cliquez sur **Documents et listes**.</span><span class="sxs-lookup"><span data-stu-id="63c46-257">On the top navigation bar, click **Documents and Lists**.</span></span>  
  
7.  <span data-ttu-id="63c46-258">Sous **bibliothèques de documents**, cliquez sur **Destination**.</span><span class="sxs-lookup"><span data-stu-id="63c46-258">Under **Document Libraries**, click **Destination**.</span></span>  
  
8.  <span data-ttu-id="63c46-259">Dans la bibliothèque de documents de Destination, vous voyez maintenant votre message répertorié.</span><span class="sxs-lookup"><span data-stu-id="63c46-259">In the Destination Document Library, you will now see your message listed.</span></span> <span data-ttu-id="63c46-260">Vous trouverez également une copie archivée dans la bibliothèque de documents d'archive.</span><span class="sxs-lookup"><span data-stu-id="63c46-260">You will also find a copy archived in the Archive Document Library.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63c46-261">Si le message n'apparaît pas dans la bibliothèque de documents de destination, consultez la rubrique « Dépannage de l'adaptateur Windows SharePoint Services » dans l'Aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63c46-261">If the message does not appear in the Destination Document Library, refer to "Troubleshooting the Windows SharePoint Services Adapter" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="63c46-262">Résumé</span><span class="sxs-lookup"><span data-stu-id="63c46-262">Summary</span></span>  
 <span data-ttu-id="63c46-263">Au cours de cette procédure, vous avez découvert la configuration de Windows SharePoint Services et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de manière à envoyer et recevoir un message via l'adaptateur Windows SharePoint Services et le routage basé sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="63c46-263">In this walkthrough you have seen how to configure Windows SharePoint Services and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] so you can send and receive a message using the Windows SharePoint Services adapter and content-based routing (CBR).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="63c46-264">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="63c46-264">Next Steps</span></span>  
 <span data-ttu-id="63c46-265">Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : Module 2 - intégration d’Office avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md) procédure pas à pas, ce qui permet de compléter le travail que vous avez terminé avec cette procédure pas à pas et l’affiche vous l’intégration d’Office à l’adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="63c46-265">Now that you have completed this walkthrough, perform the [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md) walkthrough, which expands on the work you have done with this walkthrough and shows you how to integrate Office with the Windows SharePoint Services adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c46-266">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63c46-266">See Also</span></span>  
 <span data-ttu-id="63c46-267">[Nouveautés de l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="63c46-267">[What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md) </span></span>  
 [<span data-ttu-id="63c46-268">Procédures pas à pas relatives à l’adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="63c46-268">Windows SharePoint Services Adapter Walkthroughs</span></span>](../core/windows-sharepoint-services-adapter-walkthroughs.md)