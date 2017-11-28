---
title: "Résoudre les problèmes d’installation de l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation issues, troubleshooting
- troubleshooting, installation issues
ms.assetid: 2054b725-d657-4039-b83b-119571935f62
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d245742fb89dd9eb91137d3a5f945af13b97161
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-installation-issues-with-the-oracle-database-adapter"></a><span data-ttu-id="bd2b8-102">Résoudre les problèmes d’installation de l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd2b8-102">Troubleshoot installation issues with the Oracle Database adapter</span></span>
<span data-ttu-id="bd2b8-103">Installation de Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copie les fichiers binaires du produit sur l’ordinateur et enregistre les liaisons pour chaque carte.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-103">Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter.</span></span> <span data-ttu-id="bd2b8-104">Cette section présente l’utilisation de techniques de dépannage pour résoudre les erreurs d’installation et répertorie certains problèmes connus.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-104">This section discusses using troubleshooting techniques to resolve installation errors, and also lists some known issues.</span></span>  
  
## <a name="logging-messages-for-setup-actions"></a><span data-ttu-id="bd2b8-105">Messages de journalisation pour les Actions d’installation</span><span class="sxs-lookup"><span data-stu-id="bd2b8-105">Logging Messages for Setup Actions</span></span>  
 <span data-ttu-id="bd2b8-106">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation effectue la tâche standard de l’installation du [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd2b8-106">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="bd2b8-107">En outre, le programme d’installation effectue également certaines actions personnalisées, telles que l’inscription des liaisons de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-107">Additionally, the setup also performs certain custom actions such as registering the adapter bindings.</span></span> <span data-ttu-id="bd2b8-108">Vous pouvez enregistrer les messages pour les deux les actions standards, ainsi que personnalisés que le programme d’installation exécute.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-108">You can log messages for both the standard as well as custom actions that the setup performs.</span></span>  
  
-   <span data-ttu-id="bd2b8-109">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation installe les fichiers spécifiques à l’adaptateur à l’aide d’un fichier MSI.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-109">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter-specific files using an MSI.</span></span> <span data-ttu-id="bd2b8-110">Par conséquent, la journalisation pour le programme d’installation est l’enregistrement du fichier MSI standard.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-110">Therefore, the logging for the setup is the standard MSI logging.</span></span> 
  
-   <span data-ttu-id="bd2b8-111">Tous les journaux pour le programme d’installation effectue les actions personnalisées sont disponibles à % TEMP%\adaptersetup.log.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-111">All logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log.</span></span> <span data-ttu-id="bd2b8-112">Si le suivi dans le fichier journal échoue, les traces sont également disponibles dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-112">If the tracing to the log file fails, the traces are also available in the event log.</span></span>  
  
##  <span data-ttu-id="bd2b8-113"><a name="BKMK_OraDBBinding"></a>Le programme d’installation ne parvient pas à inscrire des liaisons de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="bd2b8-113"><a name="BKMK_OraDBBinding"></a> Setup fails to register adapter bindings</span></span>  
 <span data-ttu-id="bd2b8-114">**Problème**</span><span class="sxs-lookup"><span data-stu-id="bd2b8-114">**Problem**</span></span>  
  
 <span data-ttu-id="bd2b8-115">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant installation ne parvient pas à inscrire des liaisons de l’adaptateur, mais poursuit l’installation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-115">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the adapter bindings, but proceeds with the adapter installation.</span></span>  
  
 <span data-ttu-id="bd2b8-116">**Cause**</span><span class="sxs-lookup"><span data-stu-id="bd2b8-116">**Cause**</span></span>  
  
 <span data-ttu-id="bd2b8-117">Cela peut entraîner des problèmes dans [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation ou dans le fichier machine.config est endommagé.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-117">This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span> <span data-ttu-id="bd2b8-118">Liaisons de l’adaptateur sont écrites dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-118">The adapter bindings are written to the machine.config file.</span></span>  
  
 <span data-ttu-id="bd2b8-119">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="bd2b8-119">**Resolution**</span></span>  
  
<span data-ttu-id="bd2b8-120">Inscrire manuellement le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] liaison :</span><span class="sxs-lookup"><span data-stu-id="bd2b8-120">Manually register the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding:</span></span> 
  
1.  <span data-ttu-id="bd2b8-121">Accédez au fichier machine.config sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-121">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="bd2b8-122">Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système > : \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-122">For example, on a 32-bit platform, the machine.config is available under \<system drive>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
     <span data-ttu-id="bd2b8-123">Dans ce chemin d’accès, \<version > correspond à la version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-123">In this path, \<version> is the version of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="bd2b8-124">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-124">Open the file by using a text editor.</span></span>  
  
3.  <span data-ttu-id="bd2b8-125">Pour inscrire le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] liaison :</span><span class="sxs-lookup"><span data-stu-id="bd2b8-125">To register the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding:</span></span>  
  
    1.  <span data-ttu-id="bd2b8-126">Recherchez l’élément « system.serviceModel » et ajoutez le code suivant dans cette section :</span><span class="sxs-lookup"><span data-stu-id="bd2b8-126">Search for the element "system.serviceModel" and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="bd2b8-127">Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-127">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="bd2b8-128">Recherchez manquants [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-128">Look for the missing [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding.</span></span> <span data-ttu-id="bd2b8-129">Ajoutez la section suivante sous le nœud « bindingElementExtensions ».</span><span class="sxs-lookup"><span data-stu-id="bd2b8-129">Add the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="bd2b8-130">Pour [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="bd2b8-130">For [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="bd2b8-131">Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-131">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="bd2b8-132">Recherchez manquants [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-132">Look for the missing [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding.</span></span> <span data-ttu-id="bd2b8-133">Ajoutez la section suivante sous le nœud « bindingExtensions ».</span><span class="sxs-lookup"><span data-stu-id="bd2b8-133">Add the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="bd2b8-134">Pour [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="bd2b8-134">For [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="bd2b8-135">Pour plus d’informations sur la façon de déterminer la clé publique et la version, consultez [détermination de la clé publique et la Version](#BKMK_PubKey).</span><span class="sxs-lookup"><span data-stu-id="bd2b8-135">For information about how to determine the public key and the version, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  
  
4.  <span data-ttu-id="bd2b8-136">Enregistrez et fermez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-136">Save and close the machine.config file.</span></span>  
  
####  <span data-ttu-id="bd2b8-137"><a name="BKMK_PubKey"></a>Détermination de la clé publique et la Version</span><span class="sxs-lookup"><span data-stu-id="bd2b8-137"><a name="BKMK_PubKey"></a> Determining the Public Key and Version</span></span>  
 <span data-ttu-id="bd2b8-138">Les étapes suivantes pour déterminer la clé publique pour [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd2b8-138">Perform the following steps to determine the public key for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
1.  <span data-ttu-id="bd2b8-139">Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-139">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="bd2b8-140">Avec le bouton droit de la DLL pour laquelle vous souhaitez que la clé publique et la version, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-140">Right-click the DLL for which you want the public key and the version, and then select **Properties**.</span></span> <span data-ttu-id="bd2b8-141">Le tableau suivant répertorie le nom de la DLL pour [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd2b8-141">The following table lists the name of the DLL for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
    |<span data-ttu-id="bd2b8-142">Adaptateur</span><span class="sxs-lookup"><span data-stu-id="bd2b8-142">Adapter</span></span>|<span data-ttu-id="bd2b8-143">Nom de la DLL</span><span class="sxs-lookup"><span data-stu-id="bd2b8-143">Name of the DLL</span></span>|  
    |-------------|---------------------|  
    |[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]|<span data-ttu-id="bd2b8-144">Microsoft.Adapters.OracleDB</span><span class="sxs-lookup"><span data-stu-id="bd2b8-144">Microsoft.Adapters.OracleDB</span></span>|  
  
3.  <span data-ttu-id="bd2b8-145">Sur le **général** onglet, la valeur par rapport à la **jeton de clé publique** étiquette spécifie la clé publique pour la DLL.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-145">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="bd2b8-146">De même, la valeur par rapport à la **Version** étiquette Spécifie le numéro de version de la DLL.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-146">Similarly, value against the **Version** label specifies the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="bd2b8-147">Copiez la clé publique, puis cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-147">Copy the public key, and then click **Cancel**.</span></span>  
  
##  <span data-ttu-id="bd2b8-148"><a name="BKMK_ConsumeBinding"></a>Erreur lors de l’utilisation du complément Consume Adapter Service ou l’ajouter Adapter Service Reference plug-in sur une installation 64 bits</span><span class="sxs-lookup"><span data-stu-id="bd2b8-148"><a name="BKMK_ConsumeBinding"></a> Error while using the Consume Adapter Service add-in or Add Adapter Service Reference plug-in on a 64-bit installation</span></span>  
 <span data-ttu-id="bd2b8-149">**Problème**</span><span class="sxs-lookup"><span data-stu-id="bd2b8-149">**Problem**</span></span>  
  
 <span data-ttu-id="bd2b8-150">À l’aide de la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] sur un ordinateur 64 bits exécutant la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] entraîne l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="bd2b8-150">Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:</span></span>  
  
```  
No valid adapters are installed on this machine  
```  
  
 <span data-ttu-id="bd2b8-151">**Cause**</span><span class="sxs-lookup"><span data-stu-id="bd2b8-151">**Cause**</span></span>  
  
 <span data-ttu-id="bd2b8-152">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-152">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="bd2b8-153">Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-153">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="bd2b8-154">Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-154">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="bd2b8-155">Toutefois, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] s’exécute comme un processus 32 bits et par conséquent, lorsque vous lancez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], le plug-in vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-155">However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="bd2b8-156">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="bd2b8-156">**Resolution**</span></span>  
  
-   <span data-ttu-id="bd2b8-157">Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-157">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bd2b8-158">Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-158">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="bd2b8-159">Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-159">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
-   <span data-ttu-id="bd2b8-160">Installez les versions 32 bits et 64 bits d’Oracle Data Access Components pour Client Oracle 11.1.0.6 avec le jeu de correctifs 11.1.0.7.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-160">Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bd2b8-161">Pour vous assurer que votre application fonctionne avec la version la plus récente de ODP.NET, vous devez avoir « Stratégie dll » installé sur l’ordinateur et enregistré dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-161">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="bd2b8-162">Pour plus d’informations, consultez [le fournisseur de données Oracle pour .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) sur le site Web d’Oracle.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-162">For more information, see [Oracle Data Provider for .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) on Oracle's website.</span></span>  
  
##  <span data-ttu-id="bd2b8-163"><a name="BKMK_InvalidBinding"></a>Erreur de liaison non valide lors de la configuration des ports de carte de base de données Oracle dans la Console Administration de BizTalk Server sur une installation 64 bits</span><span class="sxs-lookup"><span data-stu-id="bd2b8-163"><a name="BKMK_InvalidBinding"></a> Invalid binding error while configuring Oracle database adapter ports in BizTalk Server Administration Console on a 64-bit installation</span></span>  
 <span data-ttu-id="bd2b8-164">**Problème**</span><span class="sxs-lookup"><span data-stu-id="bd2b8-164">**Problem**</span></span>  
  
 <span data-ttu-id="bd2b8-165">Lorsque vous essayez de configurer un port de l’adaptateur dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous obtenez l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="bd2b8-165">When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:</span></span>  
  
```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "oracleDBBinding".  
Verify the binding extension is registered in machine.config."  
```  
  
 <span data-ttu-id="bd2b8-166">**Cause**</span><span class="sxs-lookup"><span data-stu-id="bd2b8-166">**Cause**</span></span>  
  
 <span data-ttu-id="bd2b8-167">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-167">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="bd2b8-168">Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-168">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="bd2b8-169">Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-169">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="bd2b8-170">Toutefois, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration s’exécute comme un processus 32 bits et par conséquent, lorsque vous configurez un port de l’adaptateur, il vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-170">However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="bd2b8-171">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="bd2b8-171">**Resolution**</span></span>  
  
-   <span data-ttu-id="bd2b8-172">Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-172">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bd2b8-173">Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-173">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="bd2b8-174">Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-174">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
-   <span data-ttu-id="bd2b8-175">Installez les versions 32 bits et 64 bits d’Oracle Data Access Components pour Client Oracle 11.1.0.6 avec le jeu de correctifs 11.1.0.7.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-175">Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bd2b8-176">Pour vous assurer que votre application fonctionne avec la version la plus récente de ODP.NET, vous devez avoir « Stratégie dll » installé sur l’ordinateur et enregistré dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-176">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="bd2b8-177">Pour plus d’informations, consultez [le fournisseur de données Oracle pour .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) sur le site Web d’Oracle.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-177">For more information, see [Oracle Data Provider for .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) on Oracle website.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="bd2b8-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd2b8-178">See Also</span></span>  
[<span data-ttu-id="bd2b8-179">Dépanner l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd2b8-179">Troubleshoot the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)