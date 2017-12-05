---
title: "Résoudre les problèmes d’Installation avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, installation
- installation, troubleshooting
ms.assetid: f9f066d9-37b6-4a18-9f60-d0931ea91a18
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff49285df7e43103f2ad7441cbc82b96bb59eaa4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-installation-issues-with-the-siebel-adapter"></a><span data-ttu-id="acba8-102">Résoudre les problèmes d’Installation avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="acba8-102">Troubleshoot Installation Issues with the Siebel adapter</span></span>
<span data-ttu-id="acba8-103">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation copie les fichiers binaires du produit sur l’ordinateur et enregistre les liaisons pour chaque carte.</span><span class="sxs-lookup"><span data-stu-id="acba8-103">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation copies the product binaries on the computer and registers the bindings for each adapter.</span></span> <span data-ttu-id="acba8-104">Cette section décrit les techniques de dépannage pour résoudre les erreurs d’installation.</span><span class="sxs-lookup"><span data-stu-id="acba8-104">This section discusses troubleshooting techniques to resolve installation errors.</span></span>  
  
## <a name="setup-logging"></a><span data-ttu-id="acba8-105">Journalisation de l’installation</span><span class="sxs-lookup"><span data-stu-id="acba8-105">Setup Logging</span></span>  
 <span data-ttu-id="acba8-106">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation effectue la tâche standard de l’installation du [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acba8-106">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="acba8-107">En outre, le programme d’installation effectue également certaines actions personnalisées, telles que l’inscription des liaisons de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="acba8-107">Additionally, the setup also performs certain custom actions such as registering the adapter bindings.</span></span> <span data-ttu-id="acba8-108">Vous pouvez enregistrer les messages pour les actions standards, ainsi que personnalisées effectuées par le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="acba8-108">You can log messages for both the standard as well as custom actions performed by the setup.</span></span>  
  
-   <span data-ttu-id="acba8-109">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation installe les fichiers spécifiques de l’adaptateur à l’aide d’un fichier MSI.</span><span class="sxs-lookup"><span data-stu-id="acba8-109">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter specific files using an MSI.</span></span> <span data-ttu-id="acba8-110">Par conséquent, la journalisation pour le programme d’installation sera l’enregistrement du fichier MSI standard.</span><span class="sxs-lookup"><span data-stu-id="acba8-110">Hence, the logging for the setup will be the standard MSI logging.</span></span>  
  
-   <span data-ttu-id="acba8-111">Journaux pour les actions personnalisées effectuées par le programme d’installation sont disponibles dans % TEMP%\adaptersetup.log.</span><span class="sxs-lookup"><span data-stu-id="acba8-111">Logs for the custom actions performed by the setup program are available at %TEMP%\adaptersetup.log.</span></span> <span data-ttu-id="acba8-112">Si le suivi dans le fichier journal échoue, les traces sont également disponibles dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="acba8-112">If the tracing to the log file fails, the traces are also available in the event log.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="acba8-113">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="acba8-113">Known Issues</span></span>  
  
### <a name="setup-fails-to-register-adapter-bindings"></a><span data-ttu-id="acba8-114">Le programme d’installation ne parvient pas à inscrire des liaisons de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="acba8-114">Setup fails to register adapter bindings</span></span>  
 <span data-ttu-id="acba8-115">**Problème**</span><span class="sxs-lookup"><span data-stu-id="acba8-115">**Problem**</span></span>  
  
 <span data-ttu-id="acba8-116">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant installation ne parvient pas à inscrire le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] liaison ou le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], mais poursuit l’installation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="acba8-116">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding or the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], but proceeds with the adapter installation.</span></span>  
  
 <span data-ttu-id="acba8-117">**Cause**</span><span class="sxs-lookup"><span data-stu-id="acba8-117">**Cause**</span></span>  
  
 <span data-ttu-id="acba8-118">Cela peut entraîner des problèmes dans l’installation de WCF, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] l’installation ou le fichier machine.config est endommagé.</span><span class="sxs-lookup"><span data-stu-id="acba8-118">This might result due to problems with WCF installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config being corrupt.</span></span> <span data-ttu-id="acba8-119">Liaisons de l’adaptateur sont écrites dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="acba8-119">The adapter bindings are written to the machine.config file.</span></span>  
  
 <span data-ttu-id="acba8-120">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="acba8-120">**Resolution**</span></span>  
  
<span data-ttu-id="acba8-121">Inscrire manuellement le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] liaison et [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="acba8-121">Manually register the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding and [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] using the following steps:</span></span> 
  
1.  <span data-ttu-id="acba8-122">Accédez au fichier machine.config sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="acba8-122">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="acba8-123">Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="acba8-123">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
     <span data-ttu-id="acba8-124">Dans ce chemin d’accès, \<version\> est la version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="acba8-124">In this path, \<version\> is the version of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="acba8-125">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="acba8-125">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="acba8-126">Pour inscrire le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] liaison :</span><span class="sxs-lookup"><span data-stu-id="acba8-126">To register the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding:</span></span>  
  
    1.  <span data-ttu-id="acba8-127">Recherchez l’élément « system.serviceModel » et ajoutez le code suivant dans cette section :</span><span class="sxs-lookup"><span data-stu-id="acba8-127">Search for the element "system.serviceModel" and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="acba8-128">Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="acba8-128">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="acba8-129">Recherchez manquants [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="acba8-129">Look for the missing [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding.</span></span> <span data-ttu-id="acba8-130">Ajoutez la section suivante sous le nœud « bindingElementExtensions ».</span><span class="sxs-lookup"><span data-stu-id="acba8-130">Add the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="acba8-131">Pour [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="acba8-131">For [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], add:</span></span>  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="acba8-132">Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="acba8-132">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="acba8-133">Recherchez manquants [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="acba8-133">Look for the missing [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding.</span></span> <span data-ttu-id="acba8-134">Ajoutez les sections suivantes sous le nœud « bindingExtensions ».</span><span class="sxs-lookup"><span data-stu-id="acba8-134">Add the following sections under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="acba8-135">Pour [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="acba8-135">For [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], add:</span></span>  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="acba8-136">Pour plus d’informations sur la façon de déterminer la clé publique, consultez [détermination de la clé publique et la Version](#BKMK_PubKey).</span><span class="sxs-lookup"><span data-stu-id="acba8-136">For information about how to determine the public key, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  
  
4.  <span data-ttu-id="acba8-137">Pour inscrire le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="acba8-137">To register the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="acba8-138">Recherchez l’élément DbProviderFactories sous le nœud system.data.</span><span class="sxs-lookup"><span data-stu-id="acba8-138">Search for the element DbProviderFactories under the system.data node.</span></span>  
  
    2.  <span data-ttu-id="acba8-139">Recherchez manquants [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acba8-139">Look for the missing [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].</span></span> <span data-ttu-id="acba8-140">Ajoutez la section suivante sous le nœud DbProviderFactories.</span><span class="sxs-lookup"><span data-stu-id="acba8-140">Add the following section under the DbProviderFactories node.</span></span>  
  
         <span data-ttu-id="acba8-141">Pour [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="acba8-141">For [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], add:</span></span>  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  <span data-ttu-id="acba8-142">Enregistrez et fermez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="acba8-142">Save and close the machine.config file.</span></span>  
  
####  <a name="BKMK_PubKey"></a><span data-ttu-id="acba8-143">Détermination de la clé publique et la Version</span><span class="sxs-lookup"><span data-stu-id="acba8-143">Determining the Public Key and Version</span></span>  
 <span data-ttu-id="acba8-144">Les étapes suivantes pour déterminer la clé publique pour [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ou [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acba8-144">Perform the following steps to determine the public key for [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] or [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].</span></span>  
  
###### <a name="to-determine-the-public-key"></a><span data-ttu-id="acba8-145">Pour déterminer la clé publique</span><span class="sxs-lookup"><span data-stu-id="acba8-145">To determine the public key</span></span>  
  
1.  <span data-ttu-id="acba8-146">Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.</span><span class="sxs-lookup"><span data-stu-id="acba8-146">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="acba8-147">Avec le bouton droit de la DLL pour lesquels vous souhaitez public key et select **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="acba8-147">Right-click the DLL for which you want the public key and select **Properties**.</span></span> <span data-ttu-id="acba8-148">Le tableau suivant répertorie le nom des DLL pour chaque fournisseur et la carte.</span><span class="sxs-lookup"><span data-stu-id="acba8-148">The following table lists the name of the DLLs for each adapter and provider.</span></span>  
  
    |<span data-ttu-id="acba8-149">Fournisseur de carte/ADO</span><span class="sxs-lookup"><span data-stu-id="acba8-149">Adapter/ADO Provider</span></span>|<span data-ttu-id="acba8-150">Nom de la DLL</span><span class="sxs-lookup"><span data-stu-id="acba8-150">Name of the DLL</span></span>|  
    |---------------------------|---------------------|  
    |[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]|<span data-ttu-id="acba8-151">Microsoft.Adapters.Siebel</span><span class="sxs-lookup"><span data-stu-id="acba8-151">Microsoft.Adapters.Siebel</span></span>|  
    |[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]|<span data-ttu-id="acba8-152">Microsoft.Data.SiebelClient</span><span class="sxs-lookup"><span data-stu-id="acba8-152">Microsoft.Data.SiebelClient</span></span>|  
  
3.  <span data-ttu-id="acba8-153">Sur le **général** onglet, la valeur par rapport à la **jeton de clé publique** étiquette spécifie la clé publique pour la DLL.</span><span class="sxs-lookup"><span data-stu-id="acba8-153">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="acba8-154">De même, la valeur par rapport à la **Version** étiquette Spécifie le numéro de version de la DLL.</span><span class="sxs-lookup"><span data-stu-id="acba8-154">Similarly, value against the **Version** label specifies the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="acba8-155">Copiez la clé publique, puis cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="acba8-155">Copy the public key, and then click **Cancel**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acba8-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acba8-156">See Also</span></span>  
[<span data-ttu-id="acba8-157">Dépanner l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="acba8-157">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)