---
title: "Étape 9 : Créer et déployer l’adaptateur Echo | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ead10ab-1acf-47c5-ad16-dc6938601906
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b9a4985629427e44b8ca85f324c89ab719cf249
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-9-build-and-deploy-the-echo-adapter"></a><span data-ttu-id="ddcbc-102">Étape 9 : Créer et déployer l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="ddcbc-102">Step 9: Build and Deploy the Echo Adapter</span></span>
<span data-ttu-id="ddcbc-103">![Étape 9 de 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")</span><span class="sxs-lookup"><span data-stu-id="ddcbc-103">![Step 9 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")</span></span>  
  
 <span data-ttu-id="ddcbc-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="ddcbc-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="ddcbc-105">Dans cette étape, vous allez effectuer les tâches nécessaires au déploiement de l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-105">In this step, you will perform the tasks necessary to deploy the Echo Adapter.</span></span> <span data-ttu-id="ddcbc-106">Cela implique de tous les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ddcbc-106">This involves all of the following:</span></span>  
  
-   <span data-ttu-id="ddcbc-107">Créer un fichier de nom fort et l’assigner à l’assembly d’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="ddcbc-107">Create a strong name file and assign it to the Echo Adapter assembly</span></span>  
  
-   <span data-ttu-id="ddcbc-108">Générez l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="ddcbc-108">Build the Echo Adapter</span></span>  
  
-   <span data-ttu-id="ddcbc-109">Publication de l’assembly dans le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="ddcbc-109">Publish the assembly into the GAC</span></span>  
  
-   <span data-ttu-id="ddcbc-110">Inscrire l’adaptateur d’écho avec le[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddcbc-110">Register the Echo Adapter with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ddcbc-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ddcbc-111">Prerequisites</span></span>  
 <span data-ttu-id="ddcbc-112">Pour réussir cette étape, vous devez être familiarisé avec les fichiers de nom fort et dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-112">To successfully complete this step, you should be familiar with strong name files and the GAC.</span></span> <span data-ttu-id="ddcbc-113">Une compréhension de base [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] configuration est utile, mais n’est pas requis.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-113">A basic understanding of [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] configuration is helpful but not required.</span></span>  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a><span data-ttu-id="ddcbc-114">Pour affecter un nom fort à votre assembly</span><span class="sxs-lookup"><span data-stu-id="ddcbc-114">To assign a strong name to your assembly</span></span>  
  
1.  <span data-ttu-id="ddcbc-115">Dans l’Explorateur de solutions, cliquez sur le **EchoAdapter** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-115">In Solution Explorer, right-click the **EchoAdapter** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="ddcbc-116">Dans la boîte de dialogue Pages de propriétés EchoAdapter, sélectionnez **signature** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-116">In the EchoAdapter Property Pages dialog box, select **Signing** from the left pane.</span></span>  
  
3.  <span data-ttu-id="ddcbc-117">Cliquez sur le **signer l’assembly** onglet.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-117">Click the **Sign the assembly** tab.</span></span>  
  
4.  <span data-ttu-id="ddcbc-118">Choisissez  **\<nouveau... \>**  pour le fichier de nom fort.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-118">Choose **\<new…\>** for the strong name file.</span></span> <span data-ttu-id="ddcbc-119">Lorsque vous y êtes invité pour un nom de fichier, tapez **EchoAdapter.snk**et la protéger mon fichier de clé avec une option de mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-119">When prompted for a file name, type **EchoAdapter.snk**,deselect the protect my key file with a password option, then click **OK**.</span></span>  
  
5.  <span data-ttu-id="ddcbc-120">Cliquez sur le **Application** onglet.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-120">Click the **Application** tab.</span></span>  
  
6.  <span data-ttu-id="ddcbc-121">Remplacez le nom de l’assembly par **Microsoft.Adapters.Samples.EchoV2**.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-121">Change the assembly name to **Microsoft.Adapters.Samples.EchoV2**.</span></span>  
  
7.  <span data-ttu-id="ddcbc-122">Cliquez sur **fichier** dans le menu Visual Studio, puis choisissez **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-122">Click **File** on the Visual Studio menu then choose **Save All**.</span></span>  
  
### <a name="to-build-and-deploy-echo-adapter"></a><span data-ttu-id="ddcbc-123">Pour générer et déployer l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="ddcbc-123">To build and deploy Echo Adapter</span></span>  
  
1.  <span data-ttu-id="ddcbc-124">Dans l’Explorateur de solutions, cliquez sur le **EchoAdapter** de projet, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-124">In Solution Explorer, right-click the **EchoAdapter** project, and then click **Build**.</span></span> <span data-ttu-id="ddcbc-125">Si la build échoue, corrigez les erreurs et essayez de régénérer l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-125">If the build does not succeed, fix any errors and try rebuilding the Echo Adapter.</span></span>  
  
2.  <span data-ttu-id="ddcbc-126">Ouvrez une invite de commandes Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-126">Open a Visual Studio command prompt.</span></span>  
  
3.  <span data-ttu-id="ddcbc-127">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ddcbc-127">Type the following command:</span></span>  
  
     <span data-ttu-id="ddcbc-128">**Gacutil.exe /if «\<**  *chemin d’accès au assembly\Microsoft.Adapters.Samples.EchoV2.dll*  **\>»**</span><span class="sxs-lookup"><span data-stu-id="ddcbc-128">**gacutil.exe /if "\<** *path to assembly\Microsoft.Adapters.Samples.EchoV2.dll* **\>"**</span></span>  
  
     <span data-ttu-id="ddcbc-129">Cette procédure installe l'assembly dans le GAC, en remplaçant tout autre assembly existant sous le même nom.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-129">This installs the assembly to the GAC, overwriting any existing assembly that has the same assembly name.</span></span>  
  
### <a name="to-register-the-echo-adapter-with-windows-communication-foundation"></a><span data-ttu-id="ddcbc-130">Pour inscrire l’adaptateur de l’écho de Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ddcbc-130">To register the Echo Adapter with Windows Communication Foundation</span></span>  
  
1.  <span data-ttu-id="ddcbc-131">Modifiez le fichier machine.config situé dans le dossier de configuration Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-131">Edit the machine.config file located in the Microsoft .NET configuration folder.</span></span> <span data-ttu-id="ddcbc-132">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **bloc-notes \<chemin d’installation de Windows\>\Microsoft.NET\Framework\\< version\>\CONFIG\machine.config**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-132">To do this, click **Start**, click **Run**, type **notepad \<Windows install path\>\Microsoft.NET\Framework\\<version\>\CONFIG\machine.config**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="ddcbc-133">Mettre à jour le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-133">Update the machine.config file.</span></span> <span data-ttu-id="ddcbc-134">Si votre fichier machine.config ne contient pas de section system.serviceModel, ajoutez la section suivante à la fin du fichier de configuration, mais avant la fermeture de balise racine.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-134">If your machine.config does not contain a system.serviceModel section, add the following section at the end of the configuration file but before the closing root tag.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ddcbc-135">Remplacez la version, culture, jeton de clé publique et autres informations spécifiques à l’assembly avec les informations de votre carte.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-135">Replace the version, culture, public key token and other assembly-specific information with your adapter's information.</span></span>  
  
    ```  
    <system.serviceModel>  
      <client>  
        <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
          name="echov2" />  
      </client>  
      <extensions>  
        <bindingElementExtensions>  
          <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
        </bindingElementExtensions>  
        <bindingExtensions>  
          <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
        </bindingExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
     - <span data-ttu-id="ddcbc-136">- OU -</span><span class="sxs-lookup"><span data-stu-id="ddcbc-136">OR -</span></span>  
  
     <span data-ttu-id="ddcbc-137">Si votre fichier machine.config contient une section system.serviceModel, déterminer quels éléments sont manquants et les ajoutant.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-137">If your machine.config contains a system.serviceModel section, determine which elements are missing and add them.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ddcbc-138">Remplacez la version, culture, jeton de clé publique et autres informations spécifiques à l’assembly avec les informations de votre carte.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-138">Replace the version, culture, public key token and other assembly-specific information with your adapter's information.</span></span>  
  
    ```  
    <client>  
      <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
        name="echov2" />  
    </client>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
      </bindingElementExtensions>  
      <bindingExtensions>  
        <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
      </bindingExtensions>  
    </extensions>  
    ```  
  
3.  <span data-ttu-id="ddcbc-139">Enregistrez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-139">Save the machine.config file.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="ddcbc-140">Quoi simplement ?</span><span class="sxs-lookup"><span data-stu-id="ddcbc-140">What Did I Just Do?</span></span>  
 <span data-ttu-id="ddcbc-141">Dans cette étape finale du didacticiel Echo adaptateur, ajouté un nom fort à l’adaptateur d’écho, générés et déployés de l’adaptateur, puis modifié le fichier Machine.config pour inclure des informations sur la carte.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-141">In this final step of the Echo Adapter tutorial, you added a strong name to the Echo Adapter, built and deployed the adapter, then modified Machine.config to include information about the adapter.</span></span> <span data-ttu-id="ddcbc-142">À ce stade, l’adaptateur Echo doit être disponible pour les applications consommatrices.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-142">At this point, the Echo Adapter should be available to consuming applications.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ddcbc-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ddcbc-143">Next Steps</span></span>  
 <span data-ttu-id="ddcbc-144">Ce didacticiel est terminé.</span><span class="sxs-lookup"><span data-stu-id="ddcbc-144">This tutorial is complete.</span></span> <span data-ttu-id="ddcbc-145">Si vous souhaitez tester le fonctionnement de l’adaptateur de l’écho dans un projet .NET, consultez [didacticiel 2 : utiliser l’adaptateur d’écho à partir de .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md).</span><span class="sxs-lookup"><span data-stu-id="ddcbc-145">If you want to test Echo Adapter functionality in a .NET project, see [Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcbc-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddcbc-146">See Also</span></span>  
 <span data-ttu-id="ddcbc-147">[Étape 8 : Implémenter le Gestionnaire d’entrée synchrone de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ddcbc-147">[Step 8: Implement the Synchronous Inbound Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="ddcbc-148">Didacticiel 2 : Utiliser l’adaptateur Echo à partir de .NET</span><span class="sxs-lookup"><span data-stu-id="ddcbc-148">Tutorial 2: Consume the Echo Adapter from .NET</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)