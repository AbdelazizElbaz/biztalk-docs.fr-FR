---
title: "Résoudre les problèmes d’Installation avec l’adaptateur SQl | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48778158-6064-4731-be72-1af855ebe373
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ba1d7e105a1ea09724950f4c0f8b778e45dad46
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-installation-issues-with-the-sql-adapter"></a><span data-ttu-id="4969a-102">Résoudre les problèmes d’Installation avec l’adaptateur SQl</span><span class="sxs-lookup"><span data-stu-id="4969a-102">Troubleshoot Installation Issues with the SQl adapter</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="4969a-103">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est disponible en tant que dans le cadre de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] ainsi que d’un adaptateur séparé.</span><span class="sxs-lookup"><span data-stu-id="4969a-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is available as part of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] as well as a separate adapter.</span></span> <span data-ttu-id="4969a-104">Si vous accédez à cette rubrique pour connaître les problèmes d’installation de le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] qui est distinct de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], toutes les références à la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation doit être interprétée comme [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="4969a-104">If you are accessing this topic to know about installation issues with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] that is separate from the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], all references to the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Setup must be interpreted as [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] Setup.</span></span>  
  
 <span data-ttu-id="4969a-105">Installation de Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copie les fichiers binaires du produit sur l’ordinateur et enregistre les liaisons pour chaque carte.</span><span class="sxs-lookup"><span data-stu-id="4969a-105">Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter.</span></span> <span data-ttu-id="4969a-106">Cette section aborde l’utilisation de techniques de dépannage pour résoudre les erreurs d’installation.</span><span class="sxs-lookup"><span data-stu-id="4969a-106">This section discusses using troubleshooting techniques to resolve installation errors.</span></span>  
  
## <a name="logging-messages-for-setup-actions"></a><span data-ttu-id="4969a-107">Messages de journalisation pour les Actions d’installation</span><span class="sxs-lookup"><span data-stu-id="4969a-107">Logging Messages for Setup Actions</span></span>  
 <span data-ttu-id="4969a-108">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation effectue la tâche standard de l’installation du [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4969a-108">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="4969a-109">En outre, le programme d’installation effectue également certaines actions personnalisées, telles que l’inscription des liaisons de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="4969a-109">Additionally, the setup also performs certain custom actions such as registering the adapter bindings.</span></span> <span data-ttu-id="4969a-110">Vous pouvez enregistrer les messages pour les deux les actions standards, ainsi que personnalisés que le programme d’installation exécute.</span><span class="sxs-lookup"><span data-stu-id="4969a-110">You can log messages for both the standard as well as custom actions that the setup performs.</span></span>  
  
-   <span data-ttu-id="4969a-111">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation installe les fichiers spécifiques à l’adaptateur à l’aide d’un fichier MSI.</span><span class="sxs-lookup"><span data-stu-id="4969a-111">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter-specific files using an MSI.</span></span> <span data-ttu-id="4969a-112">Par conséquent, la journalisation pour le programme d’installation est l’enregistrement du fichier MSI standard.</span><span class="sxs-lookup"><span data-stu-id="4969a-112">Therefore, the logging for the setup is the standard MSI logging.</span></span>  
  
-   <span data-ttu-id="4969a-113">Tous les journaux pour le programme d’installation effectue les actions personnalisées sont disponibles à % TEMP%\adaptersetup.log.</span><span class="sxs-lookup"><span data-stu-id="4969a-113">All logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log.</span></span> <span data-ttu-id="4969a-114">Si le suivi dans le fichier journal échoue, les traces sont également disponibles dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="4969a-114">If the tracing to the log file fails, the traces are also available in the event log.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="4969a-115">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="4969a-115">Known Issues</span></span>  
 <span data-ttu-id="4969a-116">Voici les erreurs les plus courantes que vous pouvez rencontrer lors de l’installation du [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], ainsi que leur cause probable et de la résolution.</span><span class="sxs-lookup"><span data-stu-id="4969a-116">The following are the most common errors you might encounter when installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], along with their probable cause and resolution.</span></span>  
  
  
  
###  <a name="BKMK_SQLSetupBinding"></a><span data-ttu-id="4969a-117">Le programme d’installation ne parvient pas à inscrire des liaisons de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="4969a-117">Setup fails to register adapter bindings</span></span>  
 <span data-ttu-id="4969a-118">**Problème**</span><span class="sxs-lookup"><span data-stu-id="4969a-118">**Problem**</span></span>  
  
 <span data-ttu-id="4969a-119">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant installation ne parvient pas à inscrire des liaisons de l’adaptateur, mais poursuit l’installation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="4969a-119">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Setup Wizard fails to register the adapter bindings, but proceeds with the adapter installation.</span></span>  
  
 <span data-ttu-id="4969a-120">**Cause**</span><span class="sxs-lookup"><span data-stu-id="4969a-120">**Cause**</span></span>  
  
 <span data-ttu-id="4969a-121">Cela peut entraîner des problèmes dans [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation ou dans le fichier machine.config est endommagé.</span><span class="sxs-lookup"><span data-stu-id="4969a-121">This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span> <span data-ttu-id="4969a-122">Liaisons de l’adaptateur sont écrites dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="4969a-122">The adapter bindings are written to the machine.config file.</span></span>  
  
 <span data-ttu-id="4969a-123">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="4969a-123">**Resolution**</span></span>  
  
 <span data-ttu-id="4969a-124">Vous devez inscrire manuellement le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="4969a-124">You should manually register the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding.</span></span>  
  
##### <a name="to-register-the-adapter-binding"></a><span data-ttu-id="4969a-125">Pour inscrire la liaison de la carte</span><span class="sxs-lookup"><span data-stu-id="4969a-125">To register the adapter binding</span></span>  
  
1.  <span data-ttu-id="4969a-126">Accédez au fichier machine.config sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4969a-126">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="4969a-127">Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="4969a-127">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
     <span data-ttu-id="4969a-128">Dans ce chemin d’accès, \<version\> est la version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4969a-128">In this path, \<version\> is the version of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="4969a-129">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="4969a-129">Open the file by using a text editor.</span></span>  
  
3.  <span data-ttu-id="4969a-130">Pour inscrire le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] liaison :</span><span class="sxs-lookup"><span data-stu-id="4969a-130">To register the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding:</span></span>  
  
    1.  <span data-ttu-id="4969a-131">Recherchez l’élément « system.serviceModel » et ajoutez le code suivant dans cette section :</span><span class="sxs-lookup"><span data-stu-id="4969a-131">Search for the element "system.serviceModel" and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="4969a-132">Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="4969a-132">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="4969a-133">Recherchez manquants [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="4969a-133">Look for the missing [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding.</span></span> <span data-ttu-id="4969a-134">Ajoutez la section suivante sous le nœud « bindingElementExtensions ».</span><span class="sxs-lookup"><span data-stu-id="4969a-134">Add the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="4969a-135">Pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="4969a-135">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="4969a-136">Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="4969a-136">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="4969a-137">Recherchez manquants [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="4969a-137">Look for the missing [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding.</span></span> <span data-ttu-id="4969a-138">Ajoutez la section suivante sous le nœud « bindingExtensions ».</span><span class="sxs-lookup"><span data-stu-id="4969a-138">Add the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="4969a-139">Pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="4969a-139">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="4969a-140">Pour plus d’informations sur la façon de déterminer la clé publique et la version, consultez [détermination de la clé publique et la Version](#BKMK_PubKey).</span><span class="sxs-lookup"><span data-stu-id="4969a-140">For information about how to determine the public key and the version, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  
  
4.  <span data-ttu-id="4969a-141">Enregistrez et fermez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="4969a-141">Save and close the machine.config file.</span></span>  
  
####  <a name="BKMK_PubKey"></a><span data-ttu-id="4969a-142">Détermination de la clé publique et la Version</span><span class="sxs-lookup"><span data-stu-id="4969a-142">Determining the Public Key and Version</span></span>  
 <span data-ttu-id="4969a-143">Les étapes suivantes pour déterminer la clé publique pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4969a-143">Perform the following steps to determine the public key for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
###### <a name="to-determine-the-public-key"></a><span data-ttu-id="4969a-144">Pour déterminer la clé publique</span><span class="sxs-lookup"><span data-stu-id="4969a-144">To determine the public key</span></span>  
  
1.  <span data-ttu-id="4969a-145">Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.</span><span class="sxs-lookup"><span data-stu-id="4969a-145">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="4969a-146">Avec le bouton droit de la DLL pour laquelle vous souhaitez que la clé publique et la version, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="4969a-146">Right-click the DLL for which you want the public key and the version, and then select **Properties**.</span></span> <span data-ttu-id="4969a-147">Le tableau suivant répertorie le nom de la DLL pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4969a-147">The following table lists the name of the DLL for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
    |<span data-ttu-id="4969a-148">Adaptateur</span><span class="sxs-lookup"><span data-stu-id="4969a-148">Adapter</span></span>|<span data-ttu-id="4969a-149">Nom de la DLL</span><span class="sxs-lookup"><span data-stu-id="4969a-149">Name of the DLL</span></span>|  
    |-------------|---------------------|  
    |[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]|<span data-ttu-id="4969a-150">Microsoft.Adapters.Sql</span><span class="sxs-lookup"><span data-stu-id="4969a-150">Microsoft.Adapters.Sql</span></span>|  
  
3.  <span data-ttu-id="4969a-151">Sur le **général** onglet, la valeur par rapport à la **jeton de clé publique** étiquette spécifie la clé publique pour la DLL.</span><span class="sxs-lookup"><span data-stu-id="4969a-151">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="4969a-152">De même, la valeur par rapport à la **Version** étiquette Spécifie le numéro de version de la DLL.</span><span class="sxs-lookup"><span data-stu-id="4969a-152">Similarly, value against the **Version** label specifies the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="4969a-153">Copiez la clé publique, puis cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="4969a-153">Copy the public key, and then click **Cancel**.</span></span>  
  
###  <a name="BKMK_SQLConsumeBinding"></a><span data-ttu-id="4969a-154">Erreur lors de l’utilisation du complément Consume Adapter Service ou l’ajouter Adapter Service Reference plug-in sur une installation 64 bits</span><span class="sxs-lookup"><span data-stu-id="4969a-154">Error while using the Consume Adapter Service add-in or Add Adapter Service Reference plug-in on a 64-bit installation</span></span>  
 <span data-ttu-id="4969a-155">**Problème**</span><span class="sxs-lookup"><span data-stu-id="4969a-155">**Problem**</span></span>  
  
 <span data-ttu-id="4969a-156">À l’aide de la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] sur un ordinateur 64 bits exécutant la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] entraîne l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="4969a-156">Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:</span></span>  
  
```  
No valid adapters are installed on this machine  
```  
  
 <span data-ttu-id="4969a-157">**Cause**</span><span class="sxs-lookup"><span data-stu-id="4969a-157">**Cause**</span></span>  
  
 <span data-ttu-id="4969a-158">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="4969a-158">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="4969a-159">Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits.</span><span class="sxs-lookup"><span data-stu-id="4969a-159">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="4969a-160">Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="4969a-160">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="4969a-161">Toutefois, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] s’exécute comme un processus 32 bits et par conséquent, lorsque vous lancez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], le plug-in vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.</span><span class="sxs-lookup"><span data-stu-id="4969a-161">However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="4969a-162">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="4969a-162">**Resolution**</span></span>  
  
 <span data-ttu-id="4969a-163">Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="4969a-163">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4969a-164">Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="4969a-164">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="4969a-165">Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4969a-165">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
###  <a name="BKMK_SQLInvalidBinding"></a><span data-ttu-id="4969a-166">Erreur de liaison non valide lors de la configuration des ports d’adaptateur SQL dans la Console Administration de BizTalk Server sur une installation 64 bits</span><span class="sxs-lookup"><span data-stu-id="4969a-166">Invalid binding error while configuring SQL adapter ports in BizTalk Server Administration Console on a 64-bit installation</span></span>  
 <span data-ttu-id="4969a-167">**Problème**</span><span class="sxs-lookup"><span data-stu-id="4969a-167">**Problem**</span></span>  
  
 <span data-ttu-id="4969a-168">Lorsque vous essayez de configurer un port de l’adaptateur dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous obtenez l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="4969a-168">When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:</span></span>  
  
```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "sqlBinding".  
Verify the binding extension is registered in machine.config."  
```  
  
 <span data-ttu-id="4969a-169">**Cause**</span><span class="sxs-lookup"><span data-stu-id="4969a-169">**Cause**</span></span>  
  
 <span data-ttu-id="4969a-170">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="4969a-170">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="4969a-171">Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits.</span><span class="sxs-lookup"><span data-stu-id="4969a-171">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="4969a-172">Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="4969a-172">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="4969a-173">Toutefois, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration s’exécute comme un processus 32 bits et par conséquent, lorsque vous configurez un port de l’adaptateur, il vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.</span><span class="sxs-lookup"><span data-stu-id="4969a-173">However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="4969a-174">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="4969a-174">**Resolution**</span></span>  
  
 <span data-ttu-id="4969a-175">Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="4969a-175">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4969a-176">Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="4969a-176">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="4969a-177">Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4969a-177">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4969a-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4969a-178">See Also</span></span>  
 [<span data-ttu-id="4969a-179">Résoudre les problèmes de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="4969a-179">Troubleshoot the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)