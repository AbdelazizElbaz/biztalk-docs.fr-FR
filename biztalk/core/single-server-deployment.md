---
title: "Déploiement mono-serveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters, deploying
- configuring [Windows SharePoint Services adapters], customizing
- deploying, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, installing
- Windows SharePoint Services adapters, configuring
- configuring [Windows SharePoint Services adapters], single-server deployment
- Windows SharePoint Services adapters, single-server deployment
ms.assetid: 94ba8241-9a30-46ca-b962-721e2d00f420
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38bb6aa65a77c5473ac2934bd2bd0c59268eb2af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-server-deployment"></a><span data-ttu-id="9b3c7-102">Déploiement monoserveur</span><span class="sxs-lookup"><span data-stu-id="9b3c7-102">Single-Server Deployment</span></span>
<span data-ttu-id="9b3c7-103">Cette rubrique décrit les considérations relatives à la configuration et au déploiement monoserveur de l'adaptateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-103">This topic discusses single-server setup and deployment considerations for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapter for Windows SharePoint Services.</span></span>  
  
## <a name="installing-the-windows-sharepoint-services-adapter-in-a-single-server-deployment"></a><span data-ttu-id="9b3c7-104">Installation de l'adaptateur Windows SharePoint Services dans un déploiement monoserveur</span><span class="sxs-lookup"><span data-stu-id="9b3c7-104">Installing the Windows SharePoint Services adapter in a single-server deployment</span></span>  
 <span data-ttu-id="9b3c7-105">Le composant de service Web adaptateur Windows SharePoint Services installe le logiciel nécessaire à l’adaptateur Windows SharePoint Services traiter les documents entrants et sortants via Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-105">Selecting the Windows SharePoint Service adapter Web service component installs the necessary software for the Windows SharePoint Services adapter to process incoming and outgoing documents through Windows SharePoint Services.</span></span> <span data-ttu-id="9b3c7-106">Ce service Web doit être installé sur le même serveur que Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-106">This Web service must be installed on the server where Windows SharePoint Services is installed.</span></span> <span data-ttu-id="9b3c7-107">Le service Web de l'adaptateur peut traiter plusieurs sites SharePoint, y compris le site Web qui héberge les services BAS, quel que soit leur emplacement (sur le même site IIS ou sur des sites IIS différents).</span><span class="sxs-lookup"><span data-stu-id="9b3c7-107">The adapter Web service can handle multiple SharePoint sites including the Web site that hosts Business Activity Services (BAS), regardless of whether they are on the same IIS site or on different IIS sites.</span></span>  
  
 <span data-ttu-id="9b3c7-108">L’adaptateur Windows SharePoint Services comprend trois composants :</span><span class="sxs-lookup"><span data-stu-id="9b3c7-108">The Windows SharePoint Services adapter has three components:</span></span>  
  
-   <span data-ttu-id="9b3c7-109">composants d'exécution ;</span><span class="sxs-lookup"><span data-stu-id="9b3c7-109">Runtime components</span></span>  
  
-   <span data-ttu-id="9b3c7-110">composants de conception ;</span><span class="sxs-lookup"><span data-stu-id="9b3c7-110">Design time components</span></span>  
  
-   <span data-ttu-id="9b3c7-111">service Web de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-111">Adapter Web service</span></span>  
  
 <span data-ttu-id="9b3c7-112">Les composants d'exécution de l'adaptateur sont installés et configurés automatiquement par le composant d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b3c7-112">The adapter runtime is installed and configured automatically by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Runtime feature.</span></span> <span data-ttu-id="9b3c7-113">Les composants de conception de l'adaptateur sont installés et configurés avec les autres fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b3c7-113">The adapter design time components are installed and configured with the other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features.</span></span> <span data-ttu-id="9b3c7-114">Vous interagissez avec les composants de conception en créant des ports Windows SharePoint Services via les outils inclus dans les outils d'administration, les outils de développement, et les composants Kit de développement logiciel (SDK) ou d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b3c7-114">You interact with the design time components by creating Windows SharePoint Services ports through tools that are included in the Administration Tools, Developer Tools, and SDK or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Runtime features.</span></span> <span data-ttu-id="9b3c7-115">Vous ne pouvez pas personnaliser les options de configuration des composants d'exécution et de conception.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-115">You cannot customize any configuration options for runtime and design time components.</span></span> <span data-ttu-id="9b3c7-116">Vous pouvez seulement personnaliser les options du service Web Adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-116">You can customize only the Windows SharePoint Service adapter Web service options.</span></span>  
  
 <span data-ttu-id="9b3c7-117">Seuls les membres du groupe Hôtes avec SharePoint activé disposent des autorisations nécessaires pour appeler le service Web de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-117">Only members of the SharePoint Enabled Hosts group have permissions to invoke the adapter Web service.</span></span> <span data-ttu-id="9b3c7-118">Pour plus d’informations sur les autorisations Windows SharePoint Services requis par l’exécution de l’adaptateur Windows SharePoint Services, consultez la section sécurité [quel est l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="9b3c7-118">For more information about the Windows SharePoint Services permissions needed by the Windows SharePoint Services adapter runtime, see the security section in [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b3c7-119">Le composant de service Web Adaptateur Windows SharePoint Services est automatiquement sélectionné si vous choisissez d'installer les services BAS.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-119">The Windows SharePoint Services adapter Web service component will be automatically selected if you choose to install BAS.</span></span>  
  
#### <a name="to-install-the-windows-sharepoint-services-adapter"></a><span data-ttu-id="9b3c7-120">Pour installer l'adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="9b3c7-120">To install the Windows SharePoint Services adapter</span></span>  
  
1.  <span data-ttu-id="9b3c7-121">Installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-121">Install BizTalk Server.</span></span> <span data-ttu-id="9b3c7-122">Pour plus d’informations, consultez [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).</span><span class="sxs-lookup"><span data-stu-id="9b3c7-122">For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).</span></span>  
  
2.  <span data-ttu-id="9b3c7-123">Sur le **Installation des composants** écran sous **composants disponibles**, sous **des logiciels supplémentaires**, sélectionnez **adaptateur Windows SharePoint Services Service Web**.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-123">On the **Component Installation** screen, under **Available Components**, under **Additional Software**, select **Windows SharePoint Services Adapter Web service**.</span></span>  
  
## <a name="configuring-the-windows-sharepoint-services-adapter-web-service-in-a-single-server-deployment"></a><span data-ttu-id="9b3c7-124">Configuration du service Web Adaptateur Windows SharePoint Services dans un déploiement monoserveur</span><span class="sxs-lookup"><span data-stu-id="9b3c7-124">Configuring the Windows SharePoint Services adapter Web service in a single-server deployment</span></span>  
 <span data-ttu-id="9b3c7-125">L'adaptateur Windows SharePoint Services est configuré à l'aide de la configuration de base ou d'une configuration personnalisée.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-125">You can configure the Windows SharePoint Services adapter using either a basic configuration or a custom configuration.</span></span> <span data-ttu-id="9b3c7-126">Pour plus d’informations sur ces outils, consultez [vue d’ensemble de la Configuration de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72).</span><span class="sxs-lookup"><span data-stu-id="9b3c7-126">For more information about these tools, see [Configuration Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72).</span></span>  
  
### <a name="using-a-basic-configuration"></a><span data-ttu-id="9b3c7-127">Utilisation d'une configuration de base</span><span class="sxs-lookup"><span data-stu-id="9b3c7-127">Using a basic configuration</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9b3c7-128"> permet de configurer le serveur à l'aide des paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-128"> allows you to configure the server by using default settings.</span></span> <span data-ttu-id="9b3c7-129">Ceux-ci sont configurés à l'aide du nom du serveur de base de données, du nom d'utilisateur et du mot de passe que vous entrez dans l'Assistant Configuration.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-129">The default settings for the server are configured using the database server name, user name, and password that you enter into the configuration wizard.</span></span> <span data-ttu-id="9b3c7-130">Lorsque vous configurez le service Web Adaptateur Windows SharePoint Services à l'aide de la configuration de base, les événements suivants se produisent :</span><span class="sxs-lookup"><span data-stu-id="9b3c7-130">When you configure the Windows SharePoint Services adapter Web service using a basic configuration, the following happens:</span></span>  
  
-   <span data-ttu-id="9b3c7-131">Le groupe Windows Hôtes avec SharePoint activé est créé.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-131">The SharePoint Enabled Hosts Windows group is created.</span></span>  
  
-   <span data-ttu-id="9b3c7-132">Le site Web par défaut est utilisé pour héberger l'adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-132">The Default Web Site is used to host the Windows SharePoint Services Adapter</span></span>  
  
-   <span data-ttu-id="9b3c7-133">Le pool d’applications BTSSharePointAdapterWSAppPool est créé et configuré pour s’exécuter sous le compte qui est également utilisé pour exécuter le pool d’applications Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-133">The BTSSharePointAdapterWSAppPool application pool is created and configured to run under the account that is also used to run the Windows SharePoint Services application pool.</span></span>  
  
-   <span data-ttu-id="9b3c7-134">L'application virtuelle BTSharePointAdapterWS est créée et configurée pour être exécutée dans le pool d'applications BTSSharePointAdapterWSAppPool.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-134">The BTSharePointAdapterWS virtual application is created and configured to run in the BTSSharePointAdapterWSAppPool application pool</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b3c7-135">Si ce répertoire virtuel existe déjà, la configuration ne met pas à jour les propriétés dans la métabase.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-135">If this virtual directory already exists, configuration will not update the properties in the metabase.</span></span> <span data-ttu-id="9b3c7-136">Vous devez supprimer le répertoire virtuel et exécutez à nouveau la configuration.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-136">You must delete the virtual directory, and run configuration again.</span></span>  
  
-   <span data-ttu-id="9b3c7-137">L'application virtuelle BTSharePointAdapterWS contient le service Web.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-137">The BTSharePointAdapterWS virtual application contains the Web service</span></span>  
  
 <span data-ttu-id="9b3c7-138">Pour plus d’informations sur la configuration de base, consultez [Configuration de base](http://msdn.microsoft.com/library/abdf3eb5-9779-47ff-bc97-2209eb4b12f5).</span><span class="sxs-lookup"><span data-stu-id="9b3c7-138">For more information about basic configuration, see [Basic Configuration](http://msdn.microsoft.com/library/abdf3eb5-9779-47ff-bc97-2209eb4b12f5).</span></span>  
  
### <a name="using-a-custom-configuration"></a><span data-ttu-id="9b3c7-139">Utilisation d'une configuration personnalisée</span><span class="sxs-lookup"><span data-stu-id="9b3c7-139">Using a custom configuration</span></span>  
 <span data-ttu-id="9b3c7-140">La Configuration de BizTalk Server fournit un niveau d'analyse très détaillé sur l'état de la configuration des composants installés en local sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-140">The BizTalk Server Configuration provides a high-level analysis of the configuration state of the features you have installed on the local computer.</span></span> <span data-ttu-id="9b3c7-141">Il permet de configurer et d'annuler la configuration de composants, de configurer les paramètres de sécurité et d'importer et exporter des configurations d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-141">The tool allows you to configure and unconfigure features, configure security settings, and import and export configurations from other computers.</span></span>  
  
 <span data-ttu-id="9b3c7-142">Utilisez le **le Service Web adaptateur Windows SharePoint Services** page pour configurer l’adaptateur Windows SharePoint Services sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-142">Use the **Windows SharePoint Services Adapter Web Service** page to configure the Windows SharePoint Services adapter on this computer.</span></span> <span data-ttu-id="9b3c7-143">Le tableau suivant répertorie les options de configuration.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-143">The following table lists the configuration options.</span></span>  
  
|<span data-ttu-id="9b3c7-144">Utiliser</span><span class="sxs-lookup"><span data-stu-id="9b3c7-144">Use this</span></span>|<span data-ttu-id="9b3c7-145">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="9b3c7-145">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="9b3c7-146">**Activer l’adaptateur Windows SharePoint Services sur cet ordinateur**</span><span class="sxs-lookup"><span data-stu-id="9b3c7-146">**Enable Windows SharePoint Services Adapter on this computer**</span></span>|<span data-ttu-id="9b3c7-147">Sélectionnez **activer l’adaptateur Windows SharePoint Services sur cet ordinateur** pour activer l’adaptateur sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-147">Select **Enable Windows SharePoint Services Adapter on this computer** to enable the adapter on this computer.</span></span>|  
|<span data-ttu-id="9b3c7-148">**Groupe Windows**</span><span class="sxs-lookup"><span data-stu-id="9b3c7-148">**Windows group**</span></span>|<span data-ttu-id="9b3c7-149">Le **groupe Windows** liste fournit une vue modifiable du groupe BizTalk adaptateur activé Windows hôtes avec SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-149">The **Windows group** list provides a view that you can edit of the BizTalk SharePoint Adapter Enabled Hosts Windows group.</span></span>|  
|<span data-ttu-id="9b3c7-150">**Site Web de l’adaptateur Windows SharePoint Services**</span><span class="sxs-lookup"><span data-stu-id="9b3c7-150">**Windows SharePoint Services Adapter Web site**</span></span>|<span data-ttu-id="9b3c7-151">Sélectionner le site Web destiné à héberger le service Web Adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-151">Select the Web site that will host the Windows SharePoint Service adapter Web service.</span></span>|  
  
 <span data-ttu-id="9b3c7-152">Lorsque vous configurez l’adaptateur Windows SharePoint Services à l’aide d’une configuration personnalisée, les événements suivants se produisent :</span><span class="sxs-lookup"><span data-stu-id="9b3c7-152">When you configure the Windows SharePoint Services adapter using a custom configuration, the following happens:</span></span>  
  
-   <span data-ttu-id="9b3c7-153">Le groupe Windows Hôtes avec SharePoint activé est créé par défaut, sauf si vous spécifiez un autre groupe Windows.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-153">The SharePoint Enabled Hosts Windows group is created by default unless you specify another Windows group</span></span>  
  
-   <span data-ttu-id="9b3c7-154">Le site Web par défaut est utilisé pour héberger l'adaptateur Windows SharePoint Services, sauf si vous spécifiez un autre site Web.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-154">The Default Web Site is used to host the Windows SharePoint Services adapter unless you specify another Web site</span></span>  
  
-   <span data-ttu-id="9b3c7-155">Le pool d'applications BTSSharePointAdapterWSAppPool est créé et configuré pour être exécuté sous le compte également utilisé pour exécuter le pool d'applications Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-155">The BTSSharePointAdapterWSAppPool application pool is created and configured to run under the account that is also used to run the Windows SharePoint Services application pool</span></span>  
  
-   <span data-ttu-id="9b3c7-156">L'application virtuelle BTSharePointAdapterWS est créée et configurée pour être exécutée dans le pool d'applications BTSSharePointAdapterWSAppPool.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-156">The BTSharePointAdapterWS virtual application is created and configured to run in the BTSSharePointAdapterWSAppPool application pool</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b3c7-157">Si ce répertoire virtuel existe déjà, la configuration ne met pas à jour les propriétés dans la métabase.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-157">If this virtual directory already exists, configuration will not update the properties in the metabase.</span></span> <span data-ttu-id="9b3c7-158">Vous devez supprimer le répertoire virtuel et exécutez à nouveau la configuration.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-158">You must delete the virtual directory, and run configuration again.</span></span>  
  
-   <span data-ttu-id="9b3c7-159">L'application virtuelle BTSharePointAdapterWS contient le service Web.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-159">The BTSharePointAdapterWS virtual application contains the Web service</span></span>  
  
 <span data-ttu-id="9b3c7-160">Pour plus d’informations sur le Gestionnaire de configuration personnalisé, consultez [importer et exporter une Configuration de BizTalk Server](../install-and-config-guides/import-and-export-biztalk-server-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="9b3c7-160">For more information about the custom configuration manager, see [Import and Export BizTalk Server Configuration](../install-and-config-guides/import-and-export-biztalk-server-configuration.md).</span></span>  
  
##### <a name="to-configure-the-windows-sharepoint-services-adapter-by-using-a-custom-configuration"></a><span data-ttu-id="9b3c7-161">Pour configurer l’adaptateur Windows SharePoint Services à l’aide d’une configuration personnalisée</span><span class="sxs-lookup"><span data-stu-id="9b3c7-161">To configure the Windows SharePoint Services adapter by using a custom configuration</span></span>  
  
1.  <span data-ttu-id="9b3c7-162">Dans le **Configuration de BizTalk Server**, sélectionnez le **adaptateur SharePoint** nœud.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-162">In the **BizTalk Server Configuration**, select the **SharePoint adapter** node.</span></span>  
  
2.  <span data-ttu-id="9b3c7-163">Sélectionnez **activer l’adaptateur Windows SharePoint Services sur cet ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-163">Select **Enable Windows SharePoint Services Adapter on this computer**.</span></span>  
  
3.  <span data-ttu-id="9b3c7-164">Sous **groupe Windows**, sélectionnez le groupe Windows que vous utiliserez pour l’adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-164">Under **Windows Group**, select the Windows group you will be using for the Windows SharePoint Services adapter.</span></span> <span data-ttu-id="9b3c7-165">Par défaut, ce groupe est Hôtes avec SharePoint activé.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-165">By default, this is SharePoint Enabled Hosts.</span></span>  
  
4.  <span data-ttu-id="9b3c7-166">Dans le **le Site Web adaptateur Windows SharePoint Services** zone déroulante, sélectionnez le site Web où les composants d’adaptateur seront installés.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-166">In the **Windows SharePoint Services Adapter Web Site** drop-down box, select the Web site where the adapter components will be installed.</span></span> <span data-ttu-id="9b3c7-167">Par défaut, il s'agit du site Web par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-167">By default, this is the Default Web Site.</span></span>  
  
5.  <span data-ttu-id="9b3c7-168">Cliquez sur **Appliquer la configuration**.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-168">Click **Apply Configuration**.</span></span>  
  
## <a name="considerations-for-a-single-server-deployment"></a><span data-ttu-id="9b3c7-169">Considérations relatives à un déploiement monoserveur</span><span class="sxs-lookup"><span data-stu-id="9b3c7-169">Considerations for a single-server deployment</span></span>  
 <span data-ttu-id="9b3c7-170">Lorsque vous configurez et déployez l'adaptateur Windows SharePoint Services dans un environnement monoserveur, prenez en compte les considérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9b3c7-170">When you set up and deploy the Windows SharePoint Services adapter in a single-server environment, consider the following:</span></span>  
  
-   <span data-ttu-id="9b3c7-171">Ajoutez le compte de service BizTalk au groupe Windows Hôtes avec SharePoint activé sur ce serveur.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-171">Add the BizTalk Service account to the SharePoint Enabled Hosts Windows group on that server.</span></span>  
  
-   <span data-ttu-id="9b3c7-172">Ajoutez le groupe Hôtes avec SharePoint activé au rôle Contributeurs SharePoint à l'aide de l'outil Administration centrale de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-172">Add the SharePoint Enabled Hosts group to the SharePoint Contributors role using the SharePoint Central Administration tool.</span></span>  
  
-   <span data-ttu-id="9b3c7-173">Sous [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], l'identité sous laquelle le service Web Adaptateur SharePoint est exécuté nécessite les autorisations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9b3c7-173">On [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], the identity under which the SharePoint Adapter Web Service runs needs the following permissions:</span></span>  
  
     <span data-ttu-id="9b3c7-174">**Lecture** autorisations sur le **Program Files\Microsoft BizTalk Server \<version > \Business Activity Services\BTSharePointV3AdapterWS** dossier.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-174">**Read** permissions on the **Program Files\Microsoft BizTalk Server \<version>\Business Activity Services\BTSharePointV3AdapterWS** folder.</span></span> <span data-ttu-id="9b3c7-175">Si vous utilisez une version 64 bits de Windows et BizTalk Server, les autorisations doivent être définies sur le **Program Files (x86) \Microsoft BizTalk Server \<version > \Business Activity Services\BTSharePointV3AdapterWS**</span><span class="sxs-lookup"><span data-stu-id="9b3c7-175">If using a 64-bit version of Windows and BizTalk Server, permissions need to be set on the **Program Files (x86)\Microsoft BizTalk Server \<version>\Business Activity Services\BTSharePointV3AdapterWS**</span></span>  
  
     <span data-ttu-id="9b3c7-176">**Lecture** autorisation sur la clé de Registre suivante : **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server\Extensions\12.0\Secure\ConfigDB**.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-176">**Read** permission on the following registry key: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server\Extensions\12.0\Secure\ConfigDB**.</span></span>  
  
     <span data-ttu-id="9b3c7-177">autorisations de connexion sur le serveur SQL contenant les bases de données SharePoint ;</span><span class="sxs-lookup"><span data-stu-id="9b3c7-177">Logon permissions on the SQL Server that contains the Sharepoint databases.</span></span>  
  
     <span data-ttu-id="9b3c7-178">Un membre de la **Public** et **WSS_Content_Application_Pools** rôles au sein de la base de données de configuration de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-178">A member of the **Public** and **WSS_Content_Application_Pools** roles within the SharePoint configuration database.</span></span>  
  
     <span data-ttu-id="9b3c7-179">Un membre de la **Public** et **propriétaire de la base de données** rôles au sein de la base de données de contenu SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-179">A member of the **Public** and **db owner** roles within the SharePoint content database.</span></span>  
  
-   <span data-ttu-id="9b3c7-180">Le site Web sur lequel vous installez le service Web doit être étendu en tant que site Web SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-180">The Web site that you install the Web service on must be extended as a SharePoint Services Web site.</span></span>  
  
-   <span data-ttu-id="9b3c7-181">Vous pouvez installer et configurer l’adaptateur Windows SharePoint Services à l’aide d’une installation sans assistance.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-181">You can install and configure the Windows SharePoint Services adapter using silent installation.</span></span> <span data-ttu-id="9b3c7-182">Pour plus d’informations, consultez [annexe a : Installation sans assistance](../install-and-config-guides/appendix-a-silent-installation.md).</span><span class="sxs-lookup"><span data-stu-id="9b3c7-182">For more information, see [Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3c7-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b3c7-183">See Also</span></span>  
 <span data-ttu-id="9b3c7-184">[Adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="9b3c7-184">[Windows SharePoint Services Adapter](../core/windows-sharepoint-services-adapter.md) </span></span>  
 [<span data-ttu-id="9b3c7-185">Déploiement multiserveur</span><span class="sxs-lookup"><span data-stu-id="9b3c7-185">Multiserver Deployment</span></span>](../core/multiserver-deployment.md)