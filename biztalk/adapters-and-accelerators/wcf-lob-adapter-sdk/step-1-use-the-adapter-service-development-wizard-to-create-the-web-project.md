---
title: "Étape 1 : Utiliser l’Assistant développement d’adaptateurs pour créer le projet Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ea0e33c-0d8d-4656-a6f0-3008b90f93f8
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1144b7e6827882b37f6f9991a7315cdc3cdbb88d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-use-the-adapter-service-development-wizard-to-create-the-web-project"></a><span data-ttu-id="ff369-102">Étape 1 : Utiliser l’Assistant développement d’adaptateurs pour créer le projet Web</span><span class="sxs-lookup"><span data-stu-id="ff369-102">Step 1: Use the Adapter Service Development Wizard to Create the Web Project</span></span>
<span data-ttu-id="ff369-103">![Étape 1 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span><span class="sxs-lookup"><span data-stu-id="ff369-103">![Step 1 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span></span>  
  
 <span data-ttu-id="ff369-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="ff369-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="ff369-105">Dans cette étape, vous créez un projet à l’aide de Visual Studio et le [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff369-105">In this step, you create a project using Visual Studio and the [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)].</span></span> <span data-ttu-id="ff369-106">Le [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)] recueille des informations sur la carte, les opérations et les configurations de point de terminaison et génère un projet Web qui peut ensuite être déployé sur IIS.</span><span class="sxs-lookup"><span data-stu-id="ff369-106">The [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)] collects information about the adapter, operations, and endpoint configurations, and generates a Web project that can then be deployed to IIS.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ff369-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ff369-107">Prerequisites</span></span>  
 <span data-ttu-id="ff369-108">Vous devez générer et déployer l’exemple Echo décrit dans [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) avant de commencer ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="ff369-108">You must build and deploy the Echo sample described in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) before beginning this tutorial.</span></span>  
  
### <a name="to-start-the-adapter-service-development-wizard"></a><span data-ttu-id="ff369-109">Pour démarrer l’Assistant développement d’adaptateurs</span><span class="sxs-lookup"><span data-stu-id="ff369-109">To start the Adapter Service Development Wizard</span></span>  
  
1.  <span data-ttu-id="ff369-110">Démarrez Visual Studio et, à la **fichier** menu, pointez sur **nouveau**, puis cliquez sur **Site Web**.</span><span class="sxs-lookup"><span data-stu-id="ff369-110">Start Visual Studio and then on the **File** menu, point to **New**, and then click **Web Site**.</span></span>  
  
2.  <span data-ttu-id="ff369-111">Dans le **nouveau Site Web** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ff369-111">In the **New Web Site** dialog box, perform the following actions:</span></span>  
  
    |<span data-ttu-id="ff369-112">Utiliser</span><span class="sxs-lookup"><span data-stu-id="ff369-112">Use this</span></span>|<span data-ttu-id="ff369-113">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ff369-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ff369-114">**Langage**</span><span class="sxs-lookup"><span data-stu-id="ff369-114">**Language**</span></span>|<span data-ttu-id="ff369-115">Cliquez sur **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="ff369-115">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="ff369-116">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="ff369-116">**Templates**</span></span>|<span data-ttu-id="ff369-117">Cliquez sur **Service d’adaptateur WCF**.</span><span class="sxs-lookup"><span data-stu-id="ff369-117">Click **WCF Adapter Service**.</span></span>|  
    |<span data-ttu-id="ff369-118">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="ff369-118">**Location**</span></span>|<span data-ttu-id="ff369-119">Sélectionnez **système de fichiers**, puis tapez **C:\Tutorials\EchoWeb** en tant que le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="ff369-119">Select **File System**, and then type **C:\Tutorials\EchoWeb** as the path.</span></span>|  
  
3.  <span data-ttu-id="ff369-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ff369-120">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="ff369-121">Sur le **page d’accueil**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="ff369-121">On the **Welcome page**, click **Next**.</span></span>  
  
### <a name="to-select-the-adapter-and-uri"></a><span data-ttu-id="ff369-122">Pour sélectionner l’adaptateur et l’URI</span><span class="sxs-lookup"><span data-stu-id="ff369-122">To select the adapter and URI</span></span>  
  
1.  <span data-ttu-id="ff369-123">Sur le **choisissez les opérations pour générer un contrat de service** page, sélectionnez **echoAdapterBindingV2** à partir de la **sélectionner une liaison** déroulante liste, puis cliquez sur  **Configurer**.</span><span class="sxs-lookup"><span data-stu-id="ff369-123">On the **Choose the operations to generate a service contract** page, select **echoAdapterBindingV2** from the **Select a binding** drop-down list, and then click **Configure**.</span></span>  
  
2.  <span data-ttu-id="ff369-124">Sur le **sécurité** onglet de la **configurer l’adaptateur** boîte de dialogue, définissez **type d’information d’identification Client** à **nom d’utilisateur**, puis définissez le  **Informations d’identification utilisateur** comme suit :</span><span class="sxs-lookup"><span data-stu-id="ff369-124">On the **Security** tab of the **Configure Adapter** dialog box, set **Client Credential type** to **Username**, and then set the **User name credentials** as follows:</span></span>  
  
    |<span data-ttu-id="ff369-125">Propriété</span><span class="sxs-lookup"><span data-stu-id="ff369-125">Property</span></span>|<span data-ttu-id="ff369-126">Valeur</span><span class="sxs-lookup"><span data-stu-id="ff369-126">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="ff369-127">**Nom d'utilisateur**</span><span class="sxs-lookup"><span data-stu-id="ff369-127">**User name**</span></span>|<span data-ttu-id="ff369-128">username</span><span class="sxs-lookup"><span data-stu-id="ff369-128">username</span></span>|  
    |<span data-ttu-id="ff369-129">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="ff369-129">**Password**</span></span>|<span data-ttu-id="ff369-130">password</span><span class="sxs-lookup"><span data-stu-id="ff369-130">password</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="ff369-131">Le nom d’utilisateur et un mot de passe entré ici sont uniquement utilisées pour se connecter à l’adaptateur lors de l’exécution de la procédure dans l’Assistant et ne sont pas conservées une fois l’Assistant terminé.</span><span class="sxs-lookup"><span data-stu-id="ff369-131">The user name and password entered here are only used to connect to the adapter while performing the steps in the wizard, and are not preserved after the wizard completes.</span></span>  
  
3.  <span data-ttu-id="ff369-132">Cliquez sur le **propriétés URI** onglet, puis définissez les propriétés comme suit :</span><span class="sxs-lookup"><span data-stu-id="ff369-132">Click the **URI Properties** tab, and then set the properties as follows:</span></span>  
  
    |<span data-ttu-id="ff369-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="ff369-133">Property</span></span>|<span data-ttu-id="ff369-134">Valeur</span><span class="sxs-lookup"><span data-stu-id="ff369-134">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="ff369-135">**Application**</span><span class="sxs-lookup"><span data-stu-id="ff369-135">**Application**</span></span>|<span data-ttu-id="ff369-136">LobApplication</span><span class="sxs-lookup"><span data-stu-id="ff369-136">LobApplication</span></span>|  
    |<span data-ttu-id="ff369-137">**EnableAuthentication**</span><span class="sxs-lookup"><span data-stu-id="ff369-137">**EnableAuthentication**</span></span>|<span data-ttu-id="ff369-138">True</span><span class="sxs-lookup"><span data-stu-id="ff369-138">True</span></span>|  
    |<span data-ttu-id="ff369-139">**Nom d’hôte**</span><span class="sxs-lookup"><span data-stu-id="ff369-139">**Hostname**</span></span>|<span data-ttu-id="ff369-140">lobhostname</span><span class="sxs-lookup"><span data-stu-id="ff369-140">lobhostname</span></span>|  
    |<span data-ttu-id="ff369-141">**EchoInUpperCase**</span><span class="sxs-lookup"><span data-stu-id="ff369-141">**EchoInUpperCase**</span></span>|<span data-ttu-id="ff369-142">False</span><span class="sxs-lookup"><span data-stu-id="ff369-142">False</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="ff369-143">Les propriétés de l’URI sélectionnées ici permet de créer le \< **client**\>\<**point de terminaison** \> éléments dans le fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="ff369-143">The URI properties selected here will be used to create the \<**client**\>\<**endpoint**\> elements in the web.config file.</span></span>  
  
4.  <span data-ttu-id="ff369-144">Cliquez sur le **propriétés de liaison** onglet. Notez les valeurs par défaut, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ff369-144">Click the **Binding Properties** tab. Note the default values, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ff369-145">Les valeurs de liaison permet de générer le \< **liaisons**\>\<**echoAdapterBindingV2** \> éléments dans le fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="ff369-145">The binding values will be used to generate the \<**bindings**\>\<**echoAdapterBindingV2**\> elements in the web.config file.</span></span>  
  
### <a name="to-select-the-contract-and-operations"></a><span data-ttu-id="ff369-146">Pour sélectionner le contrat et les opérations</span><span class="sxs-lookup"><span data-stu-id="ff369-146">To select the contract and operations</span></span>  
  
1.  <span data-ttu-id="ff369-147">Sur le **choisissez les opérations pour générer un contrat de service** , cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="ff369-147">On the **Choose the operations to generate a service contract** page, click **Connect**.</span></span>  
  
2.  <span data-ttu-id="ff369-148">Dans le **sélectionner une catégorie** d’arborescence, sélectionnez **catégorie principale**.</span><span class="sxs-lookup"><span data-stu-id="ff369-148">In the **Select a category** tree, select **Main Category**.</span></span> <span data-ttu-id="ff369-149">Cette opération remplit le **catégories et opérations disponibles** liste.</span><span class="sxs-lookup"><span data-stu-id="ff369-149">This populates the **Available categories and operations** list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ff369-150">Vous pouvez également entrer un terme à rechercher dans le **recherche dans la catégorie** champ à rechercher toutes les opérations qui contiennent le terme de recherche.</span><span class="sxs-lookup"><span data-stu-id="ff369-150">You can also enter a search term in the **Search in category** field to find any operations that contain the search term.</span></span>  
  
3.  <span data-ttu-id="ff369-151">Dans le **catégories et opérations disponibles** liste, sélectionnez **EchoGreetings** et cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="ff369-151">In the **Available categories and operations** list, select **EchoGreetings** and click **Add**.</span></span> <span data-ttu-id="ff369-152">Cette opération déplace l’opération EchoGreetings le **ajouté des catégories et opérations** liste.</span><span class="sxs-lookup"><span data-stu-id="ff369-152">This moves the EchoGreetings operation to the **Added categories and operations** list.</span></span> <span data-ttu-id="ff369-153">Les opérations sélectionnées ici seront exposées à des applications clientes via le code du proxy client généré par l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="ff369-153">The operations selected here will be exposed to client applications through the client proxy code generated by the wizard.</span></span>  
  
     <span data-ttu-id="ff369-154">![Sélectionnez le contrat et les opérations](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/de497b32-c820-480f-84f3-a9d0d2ded86b.gif "de497b32-c820-480f-84f3-a9d0d2ded86b")</span><span class="sxs-lookup"><span data-stu-id="ff369-154">![Select Contract and Operations](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/de497b32-c820-480f-84f3-a9d0d2ded86b.gif "de497b32-c820-480f-84f3-a9d0d2ded86b")</span></span>  
  
4.  <span data-ttu-id="ff369-155">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="ff369-155">Click **Next**.</span></span>  
  
### <a name="to-configure-service-and-endpoint-behavior"></a><span data-ttu-id="ff369-156">Pour configurer le comportement de service et de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="ff369-156">To configure service and endpoint behavior</span></span>  
  
1.  <span data-ttu-id="ff369-157">Sur le **configurer les comportements de service et de point de terminaison** , entrez les valeurs suivantes pour **Configuration de comportement de Service**:</span><span class="sxs-lookup"><span data-stu-id="ff369-157">On the **Configure service and endpoint behaviors** page, enter the following values for **Service Behavior Configuration**:</span></span>  
  
    |<span data-ttu-id="ff369-158">Propriété</span><span class="sxs-lookup"><span data-stu-id="ff369-158">Property</span></span>|<span data-ttu-id="ff369-159">Valeur</span><span class="sxs-lookup"><span data-stu-id="ff369-159">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="ff369-160">**EnableMetadataExchange**</span><span class="sxs-lookup"><span data-stu-id="ff369-160">**EnableMetadataExchange**</span></span>|<span data-ttu-id="ff369-161">True</span><span class="sxs-lookup"><span data-stu-id="ff369-161">True</span></span>|  
    |<span data-ttu-id="ff369-162">**IncludeExceptionDetailsinFault**</span><span class="sxs-lookup"><span data-stu-id="ff369-162">**IncludeExceptionDetailsinFault**</span></span>|<span data-ttu-id="ff369-163">True</span><span class="sxs-lookup"><span data-stu-id="ff369-163">True</span></span>|  
    |<span data-ttu-id="ff369-164">**Nom**</span><span class="sxs-lookup"><span data-stu-id="ff369-164">**Name**</span></span>|<span data-ttu-id="ff369-165">customServiceBehavior</span><span class="sxs-lookup"><span data-stu-id="ff369-165">customServiceBehavior</span></span>|  
    |<span data-ttu-id="ff369-166">**UseServiceCertificate**</span><span class="sxs-lookup"><span data-stu-id="ff369-166">**UseServiceCertificate**</span></span>|<span data-ttu-id="ff369-167">False</span><span class="sxs-lookup"><span data-stu-id="ff369-167">False</span></span>|  
  
     <span data-ttu-id="ff369-168">Ces valeurs sont utilisées pour remplir la \< **serviceBehaviors**\>.</span><span class="sxs-lookup"><span data-stu-id="ff369-168">These values are used to populate the \<**serviceBehaviors**\>.</span></span>  
  
2.  <span data-ttu-id="ff369-169">Entrez les valeurs suivantes pour **Configuration de comportement de point de terminaison**:</span><span class="sxs-lookup"><span data-stu-id="ff369-169">Enter the following values for **Endpoint Behavior Configuration**:</span></span>  
  
    |<span data-ttu-id="ff369-170">Propriété</span><span class="sxs-lookup"><span data-stu-id="ff369-170">Property</span></span>|<span data-ttu-id="ff369-171">Valeur</span><span class="sxs-lookup"><span data-stu-id="ff369-171">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="ff369-172">**Nom**</span><span class="sxs-lookup"><span data-stu-id="ff369-172">**Name**</span></span>|<span data-ttu-id="ff369-173">customEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="ff369-173">customEndpointBehavior</span></span>|  
    |<span data-ttu-id="ff369-174">**AuthenticationType**</span><span class="sxs-lookup"><span data-stu-id="ff369-174">**AuthenticationType**</span></span>|<span data-ttu-id="ff369-175">**HTTPUsernamePassword**</span><span class="sxs-lookup"><span data-stu-id="ff369-175">**HTTPUsernamePassword**</span></span>|  
    |<span data-ttu-id="ff369-176">**UsernameHeader**</span><span class="sxs-lookup"><span data-stu-id="ff369-176">**UsernameHeader**</span></span>|<span data-ttu-id="ff369-177">MyUserHeader</span><span class="sxs-lookup"><span data-stu-id="ff369-177">MyUserHeader</span></span>|  
    |<span data-ttu-id="ff369-178">**PasswordHeader**</span><span class="sxs-lookup"><span data-stu-id="ff369-178">**PasswordHeader**</span></span>|<span data-ttu-id="ff369-179">MyPassHeader</span><span class="sxs-lookup"><span data-stu-id="ff369-179">MyPassHeader</span></span>|  
  
     <span data-ttu-id="ff369-180">Ces valeurs permet de spécifier le **adapterSecurityBridgeType** dans le <**endpointBehaviors** élément web.confg.</span><span class="sxs-lookup"><span data-stu-id="ff369-180">These values will be used to specify the **adapterSecurityBridgeType** in the <**endpointBehaviors** element in web.confg.</span></span>  
  
     <span data-ttu-id="ff369-181">![Configuration de point de terminaison](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/3fd5784c-64e5-47c1-9a6f-10f12f77f726.gif "3fd5784c-64e5-47c1-9a6f-10f12f77f726")</span><span class="sxs-lookup"><span data-stu-id="ff369-181">![Endpoint Configuration](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/3fd5784c-64e5-47c1-9a6f-10f12f77f726.gif "3fd5784c-64e5-47c1-9a6f-10f12f77f726")</span></span>  
  
3.  <span data-ttu-id="ff369-182">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="ff369-182">Click **Next**</span></span>  
  
### <a name="to-configure-the-binding"></a><span data-ttu-id="ff369-183">Pour configurer la liaison</span><span class="sxs-lookup"><span data-stu-id="ff369-183">To configure the binding</span></span>  
  
1.  <span data-ttu-id="ff369-184">Sur le **configurer la liaison de point de terminaison de service et l’adresse** page, sélectionnez le **BindingConfiguration** entrée dans **configurer la liaison pour le contrat et l’adresse**, et puis cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="ff369-184">On the **Configure the service endpoint binding and address** page, select the **BindingConfiguration** entry in **Configure the address and binding for the contract**, and then click the ellipsis (**…**) button.</span></span>  
  
2.  <span data-ttu-id="ff369-185">Dans le **personnaliser la liaison de** boîte de dialogue, définissez **Mode** à **TransportWithMessageCredential**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ff369-185">In the **Customize Binding** dialog box, set **Mode** to **TransportWithMessageCredential**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="ff369-186">Cliquez sur **appliquer**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="ff369-186">Click **Apply**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="ff369-187">Sur le **Résumé** page, passez en revue les contrats et les opérations sélectionnées pour ce projet, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="ff369-187">On the **Summary** page, review the contracts and operations selected for this project, and then click **Finish**.</span></span> <span data-ttu-id="ff369-188">Vous verrez la solution EchoWeb, qui contient les fichiers projet créés par le[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff369-188">You will be presented with the EchoWeb solution, which contains the project files created by the [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="ff369-189">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="ff369-189">What did I just do?</span></span>  
 <span data-ttu-id="ff369-190">Dans cette étape, vous avez utilisé le [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)] pour générer un site Web qui, projeter le moment où il est publié sur le serveur IIS, hébergera développé par l’adaptateur de l’écho dans [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) dans IIS.</span><span class="sxs-lookup"><span data-stu-id="ff369-190">In this step, you used the [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)] to generate a Web project that, when published to IIS, will host the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) in the IIS process.</span></span> <span data-ttu-id="ff369-191">Le projet Web résultant permet des clients WCF et les Services Web accéder aux opérations sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="ff369-191">The resulting Web project allows Web Services and WCF clients to access the selected operations.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ff369-192">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ff369-192">Next Steps</span></span>  
 <span data-ttu-id="ff369-193">Pour générer et déployer le projet Web, passez à [étape 2 : déployer le projet Web](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)</span><span class="sxs-lookup"><span data-stu-id="ff369-193">To build and deploy the Web project, proceed to [Step 2: Deploy the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff369-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff369-194">See Also</span></span>  
 [<span data-ttu-id="ff369-195">Didacticiel 1 : Développer l’adaptateur Echo</span><span class="sxs-lookup"><span data-stu-id="ff369-195">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)