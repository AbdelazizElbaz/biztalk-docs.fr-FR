---
title: "Résoudre les problèmes d’Installation avec l’adaptateur SAP | Documents Microsoft"
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
ms.assetid: fdfdaf44-c32d-43a5-998d-02032c0b9211
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc33d5d15ef876e18a5a17fa33944dd7d1b36461
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-installation-issues-with-the-sap-adapter"></a><span data-ttu-id="edfeb-102">Résoudre les problèmes d’Installation avec l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="edfeb-102">Troubleshoot Installation Issues with the SAP adapter</span></span>
<span data-ttu-id="edfeb-103">Installation de Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copie les fichiers binaires du produit sur l’ordinateur et enregistre les liaisons pour chaque carte.</span><span class="sxs-lookup"><span data-stu-id="edfeb-103">Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter.</span></span> <span data-ttu-id="edfeb-104">Cette section décrit les techniques de dépannage pour résoudre les erreurs d’installation.</span><span class="sxs-lookup"><span data-stu-id="edfeb-104">This section discusses troubleshooting techniques to resolve installation errors.</span></span>  
  
## <a name="logging-messages-for-setup-actions"></a><span data-ttu-id="edfeb-105">Messages de journalisation pour les Actions d’installation</span><span class="sxs-lookup"><span data-stu-id="edfeb-105">Logging Messages for Setup Actions</span></span>  
 <span data-ttu-id="edfeb-106">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation effectue la tâche standard de l’installation du [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="edfeb-106">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="edfeb-107">En outre, le programme d’installation effectue également certaines actions personnalisées, telles que l’inscription des liaisons de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="edfeb-107">Additionally, the setup also performs certain custom actions such as registering the adapter bindings.</span></span> <span data-ttu-id="edfeb-108">Vous pouvez enregistrer les messages pour les deux les actions standards, ainsi que personnalisés que le programme d’installation exécute.</span><span class="sxs-lookup"><span data-stu-id="edfeb-108">You can log messages for both the standard as well as custom actions that the setup performs.</span></span>  
  
-   <span data-ttu-id="edfeb-109">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation installe les fichiers spécifiques de l’adaptateur à l’aide d’un fichier MSI.</span><span class="sxs-lookup"><span data-stu-id="edfeb-109">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter specific files using an MSI.</span></span> <span data-ttu-id="edfeb-110">Par conséquent, la journalisation pour le programme d’installation est l’enregistrement du fichier MSI standard.</span><span class="sxs-lookup"><span data-stu-id="edfeb-110">Hence, the logging for the setup is the standard MSI logging.</span></span>  
  
-   <span data-ttu-id="edfeb-111">Journaux pour le programme d’installation effectue les actions personnalisées sont disponibles à % TEMP%\adaptersetup.log.</span><span class="sxs-lookup"><span data-stu-id="edfeb-111">Logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log.</span></span> <span data-ttu-id="edfeb-112">Si le suivi dans le fichier journal échoue, les traces sont également disponibles dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="edfeb-112">If the tracing to the log file fails, the traces are also available in the event log.</span></span>  
  
##  <a name="BKMK_SAPSetupBinding"></a><span data-ttu-id="edfeb-113">Le programme d’installation ne parvient pas à inscrire des liaisons de l’adaptateur ou des fournisseurs de données</span><span class="sxs-lookup"><span data-stu-id="edfeb-113">Setup fails to register adapter bindings or data providers</span></span>  
 <span data-ttu-id="edfeb-114">**Problème**</span><span class="sxs-lookup"><span data-stu-id="edfeb-114">**Problem**</span></span>  
  
 <span data-ttu-id="edfeb-115">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant installation ne parvient pas à inscrire des liaisons de l’adaptateur ou [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], mais poursuit l’installation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="edfeb-115">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the adapter bindings or the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], but proceeds with the adapter installation.</span></span>  
  
 <span data-ttu-id="edfeb-116">**Cause**</span><span class="sxs-lookup"><span data-stu-id="edfeb-116">**Cause**</span></span>  
  
 <span data-ttu-id="edfeb-117">Cela peut entraîner des problèmes dans [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation ou dans le fichier machine.config est endommagé.</span><span class="sxs-lookup"><span data-stu-id="edfeb-117">This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span> <span data-ttu-id="edfeb-118">Liaisons de l’adaptateur sont écrites dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="edfeb-118">The adapter bindings are written to the machine.config file.</span></span>  
  
 <span data-ttu-id="edfeb-119">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="edfeb-119">**Resolution**</span></span>  
  
 <span data-ttu-id="edfeb-120">Vous devez inscrire manuellement le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] liaison ou le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="edfeb-120">You should manually register the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding or the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
### <a name="register-the-adapter-bindings-or-the-data-provider"></a><span data-ttu-id="edfeb-121">Inscrire des liaisons de l’adaptateur ou le fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="edfeb-121">Register the adapter bindings or the data provider</span></span>  
  
1.  <span data-ttu-id="edfeb-122">Accédez au fichier machine.config sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="edfeb-122">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="edfeb-123">Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="edfeb-123">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
     <span data-ttu-id="edfeb-124">Dans ce chemin d’accès, \<version\> est la version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="edfeb-124">In this path, \<version\> is the version of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="edfeb-125">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="edfeb-125">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="edfeb-126">Pour inscrire le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] liaison :</span><span class="sxs-lookup"><span data-stu-id="edfeb-126">To register the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding:</span></span>  
  
    1.  <span data-ttu-id="edfeb-127">Recherchez l’élément « system.serviceModel » et ajoutez le code suivant dans cette section :</span><span class="sxs-lookup"><span data-stu-id="edfeb-127">Search for the element "system.serviceModel" and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="edfeb-128">Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="edfeb-128">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="edfeb-129">Recherchez manquants [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="edfeb-129">Look for the missing [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding.</span></span> <span data-ttu-id="edfeb-130">Ajoutez la section suivante sous le nœud « bindingElementExtensions ».</span><span class="sxs-lookup"><span data-stu-id="edfeb-130">Add the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="edfeb-131">Pour [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="edfeb-131">For [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], add:</span></span>  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="edfeb-132">Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="edfeb-132">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="edfeb-133">Recherchez manquants [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="edfeb-133">Look for the missing [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding.</span></span> <span data-ttu-id="edfeb-134">Ajoutez la section suivante sous le nœud « bindingExtensions ».</span><span class="sxs-lookup"><span data-stu-id="edfeb-134">Add the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="edfeb-135">Pour [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="edfeb-135">For [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], add:</span></span>  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="edfeb-136">Pour plus d’informations sur la façon de déterminer la clé publique, consultez [détermination de la clé publique et la Version](#BKMK_PubKey).</span><span class="sxs-lookup"><span data-stu-id="edfeb-136">For information about how to determine the public key, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  
  
4.  <span data-ttu-id="edfeb-137">Pour inscrire le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="edfeb-137">To register the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="edfeb-138">Recherchez l’élément « DbProviderFactories » sous le nœud « system.data ».</span><span class="sxs-lookup"><span data-stu-id="edfeb-138">Search for the element "DbProviderFactories" under the "system.data" node.</span></span>  
  
    2.  <span data-ttu-id="edfeb-139">Recherchez manquants [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="edfeb-139">Look for the missing [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="edfeb-140">Ajoutez la section suivante sous le nœud « DbProviderFactories ».</span><span class="sxs-lookup"><span data-stu-id="edfeb-140">Add the following section under the "DbProviderFactories" node.</span></span>  
  
         <span data-ttu-id="edfeb-141">Pour [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="edfeb-141">For [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], add:</span></span>  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient" description=".NET Framework Data Provider for mySAP Business Suite" type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  <span data-ttu-id="edfeb-142">Enregistrez et fermez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="edfeb-142">Save and close the machine.config file.</span></span>  
  
###  <a name="BKMK_PubKey"></a><span data-ttu-id="edfeb-143">Détermination de la clé publique et la Version</span><span class="sxs-lookup"><span data-stu-id="edfeb-143">Determining the Public Key and Version</span></span>  
 <span data-ttu-id="edfeb-144">Les étapes suivantes pour déterminer la clé publique pour [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ou [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="edfeb-144">Perform the following steps to determine the public key for [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] or [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
1.  <span data-ttu-id="edfeb-145">Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.</span><span class="sxs-lookup"><span data-stu-id="edfeb-145">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="edfeb-146">Avec le bouton droit de la DLL pour laquelle vous souhaitez que la clé publique, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="edfeb-146">Right-click the DLL for which you want the public key, and then select **Properties**.</span></span> <span data-ttu-id="edfeb-147">Le tableau suivant répertorie le nom des DLL pour [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="edfeb-147">The following table lists the name of the DLLs for [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
    |<span data-ttu-id="edfeb-148">Fournisseur de données/carte</span><span class="sxs-lookup"><span data-stu-id="edfeb-148">Adapter/Data Provider</span></span>|<span data-ttu-id="edfeb-149">Nom de la DLL</span><span class="sxs-lookup"><span data-stu-id="edfeb-149">Name of the DLL</span></span>|  
    |----------------------------|---------------------|  
    |[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]|<span data-ttu-id="edfeb-150">Microsoft.Adapters.SAP</span><span class="sxs-lookup"><span data-stu-id="edfeb-150">Microsoft.Adapters.SAP</span></span>|  
    |[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]|<span data-ttu-id="edfeb-151">Microsoft.Data.SAPClient</span><span class="sxs-lookup"><span data-stu-id="edfeb-151">Microsoft.Data.SAPClient</span></span>|  
  
3.  <span data-ttu-id="edfeb-152">Sur le **général** onglet, la valeur par rapport à la **jeton de clé publique** étiquette spécifie la clé publique pour la DLL.</span><span class="sxs-lookup"><span data-stu-id="edfeb-152">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="edfeb-153">De même, la valeur par rapport à la **Version** étiquette Spécifie le numéro de version de la DLL.</span><span class="sxs-lookup"><span data-stu-id="edfeb-153">Similarly, value against the **Version** label specifies the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="edfeb-154">Copiez la clé publique, puis cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="edfeb-154">Copy the public key, and then click **Cancel**.</span></span>  
  
##  <a name="BKMK_SAPConsumeBinding"></a><span data-ttu-id="edfeb-155">Aucune carte valides n’est erreur installés</span><span class="sxs-lookup"><span data-stu-id="edfeb-155">No valid adapters are installed error</span></span>

 <span data-ttu-id="edfeb-156">**Problème**</span><span class="sxs-lookup"><span data-stu-id="edfeb-156">**Problem**</span></span>  
  
 <span data-ttu-id="edfeb-157">À l’aide de la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] sur un ordinateur 64 bits exécutant la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] entraîne l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="edfeb-157">Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:</span></span>  
  
```  
No valid adapters are installed on this machine  
```  
  
 <span data-ttu-id="edfeb-158">**Cause**</span><span class="sxs-lookup"><span data-stu-id="edfeb-158">**Cause**</span></span>  
  
 <span data-ttu-id="edfeb-159">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="edfeb-159">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="edfeb-160">Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits.</span><span class="sxs-lookup"><span data-stu-id="edfeb-160">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="edfeb-161">Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="edfeb-161">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="edfeb-162">Toutefois, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] s’exécute comme un processus 32 bits et par conséquent, lorsque vous lancez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], le plug-in vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.</span><span class="sxs-lookup"><span data-stu-id="edfeb-162">However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="edfeb-163">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="edfeb-163">**Resolution**</span></span>  
  
-   <span data-ttu-id="edfeb-164">Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="edfeb-164">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="edfeb-165">Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="edfeb-165">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="edfeb-166">Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="edfeb-166">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
-   <span data-ttu-id="edfeb-167">Ajoutez les versions 32 bits et 64 bits des DLL du client pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] (par exemple, librfc32u.dll) à la variable de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="edfeb-167">Add both the 32-bit and 64-bit versions of the client DLLs for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] (such as librfc32u.dll) to the PATH variable.</span></span> <span data-ttu-id="edfeb-168">La version 32 bits des DLL doit être ajoutée au dossier de C:\Windows\SysWow64.</span><span class="sxs-lookup"><span data-stu-id="edfeb-168">The 32-bit version of the DLLs must be added to C:\Windows\SysWow64 folder.</span></span> <span data-ttu-id="edfeb-169">La version 64 bits des DLL doit être ajoutée au dossier C:\Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="edfeb-169">The 64-bit version of the DLLs must be added to C:\Windows\System32 folder.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="edfeb-170">Si l’adaptateur (32 ou 64 bits) est en cours d’exécution sur un ordinateur qui possède un système d’exploitation de 64 bits, et que vous écrivez une application à l’aide de l’adaptateur, vous devez marquer l’application vers le même type (32 ou 64 bits) en tant que l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="edfeb-170">If the adapter (32 or 64-bit) is running on a computer that has a 64-bit operating system, and you are using the adapter to write an application, you should mark the application to the same type (32 or 64-bit) as the adapter.</span></span> <span data-ttu-id="edfeb-171">En outre, la version du SDK RFC (32 ou 64 bits) doit être identique à la version de l’adaptateur (32 ou 64 bits).</span><span class="sxs-lookup"><span data-stu-id="edfeb-171">Also, the version of the RFC SDK (32 or 64-bit) must be same as the version of the adapter (32 or 64-bit).</span></span>  
    >   
    >  <span data-ttu-id="edfeb-172">Par exemple, si un adaptateur 32 bits s’exécute sur un ordinateur avec un système d’exploitation de 64 bits, l’application cliente de carte doit être marquée comme 32 bits.</span><span class="sxs-lookup"><span data-stu-id="edfeb-172">For example, if a 32-bit adapter is running on a computer with a 64-bit operating system, the adapter client application must be marked as 32-bit.</span></span>  
  
     <span data-ttu-id="edfeb-173">Pour plus d’informations sur la DLL du client SAP, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span><span class="sxs-lookup"><span data-stu-id="edfeb-173">For more information about the SAP client DLLs, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>  
  
##  <a name="BKMK_SAPInvalidBinding"></a><span data-ttu-id="edfeb-174">Erreur de liaison non valide lors de la configuration des ports d’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="edfeb-174">Invalid binding error while configuring SAP adapter ports</span></span>  
 <span data-ttu-id="edfeb-175">**Problème**</span><span class="sxs-lookup"><span data-stu-id="edfeb-175">**Problem**</span></span>  
  
 <span data-ttu-id="edfeb-176">Lorsque vous essayez de configurer un port de l’adaptateur dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous obtenez l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="edfeb-176">When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:</span></span>  
  
```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "sapBinding".  
Verify the binding extension is registered in machine.config."  
```  
  
 <span data-ttu-id="edfeb-177">**Cause**</span><span class="sxs-lookup"><span data-stu-id="edfeb-177">**Cause**</span></span>  
  
 <span data-ttu-id="edfeb-178">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="edfeb-178">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="edfeb-179">Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits.</span><span class="sxs-lookup"><span data-stu-id="edfeb-179">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="edfeb-180">Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="edfeb-180">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="edfeb-181">Toutefois, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration s’exécute comme un processus 32 bits et par conséquent, lorsque vous configurez un port de l’adaptateur, il vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.</span><span class="sxs-lookup"><span data-stu-id="edfeb-181">However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="edfeb-182">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="edfeb-182">**Resolution**</span></span>  
  
-   <span data-ttu-id="edfeb-183">Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="edfeb-183">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="edfeb-184">Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="edfeb-184">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="edfeb-185">Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="edfeb-185">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
-   <span data-ttu-id="edfeb-186">Ajoutez les versions 32 bits et 64 bits des DLL du client pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] (par exemple, librfc32u.dll) à la variable de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="edfeb-186">Add both the 32-bit and 64-bit versions of the client DLLs for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] (such as librfc32u.dll) to the PATH variable.</span></span> <span data-ttu-id="edfeb-187">La version 32 bits des DLL doit être ajoutée au dossier de C:\Windows\SysWow64.</span><span class="sxs-lookup"><span data-stu-id="edfeb-187">The 32-bit version of the DLLs must be added to C:\Windows\SysWow64 folder.</span></span> <span data-ttu-id="edfeb-188">La version 64 bits des DLL doit être ajoutée au dossier C:\Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="edfeb-188">The 64-bit version of the DLLs must be added to C:\Windows\System32 folder.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="edfeb-189">Si l’adaptateur (32 ou 64 bits) est en cours d’exécution sur un ordinateur qui possède un système d’exploitation de 64 bits, et que vous écrivez une application à l’aide de l’adaptateur, vous devez marquer l’application vers le même type (32 ou 64 bits) en tant que l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="edfeb-189">If the adapter (32 or 64-bit) is running on a computer that has a 64-bit operating system, and you are using the adapter to write an application, you should mark the application to the same type (32 or 64-bit) as the adapter.</span></span> <span data-ttu-id="edfeb-190">En outre, la version du SDK RFC (32 ou 64 bits) doit être identique à la version de l’adaptateur (32 ou 64 bits).</span><span class="sxs-lookup"><span data-stu-id="edfeb-190">Also, the version of the RFC SDK (32 or 64-bit) must be same as the version of the adapter (32 or 64-bit).</span></span>  
    >   
    >  <span data-ttu-id="edfeb-191">Par exemple, si un adaptateur 32 bits s’exécute sur un ordinateur avec un système d’exploitation de 64 bits, l’application cliente de carte doit être marquée comme 32 bits.</span><span class="sxs-lookup"><span data-stu-id="edfeb-191">For example, if a 32-bit adapter is running on a computer with a 64-bit operating system, the adapter client application must be marked as 32-bit.</span></span>  
  
     <span data-ttu-id="edfeb-192">Pour plus d’informations sur la DLL du client SAP, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span><span class="sxs-lookup"><span data-stu-id="edfeb-192">For more information about the SAP client DLLs, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="edfeb-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edfeb-193">See Also</span></span>  
[<span data-ttu-id="edfeb-194">Résoudre les problèmes de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="edfeb-194">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)