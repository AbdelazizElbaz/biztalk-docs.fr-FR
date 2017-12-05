---
title: "Résoudre les problèmes d’Installation avec l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09b3af20-ab87-44e8-8ded-c19432552be7
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29fbee54262f1b45e3cc9be67c057767a80b325f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-installation-issues-with-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="deb53-102">Résoudre les problèmes d’Installation avec l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="deb53-102">Troubleshoot Installation Issues with the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="deb53-103">Installation de Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copie les fichiers binaires du produit sur l’ordinateur et enregistre les liaisons pour chaque carte.</span><span class="sxs-lookup"><span data-stu-id="deb53-103">Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter.</span></span> <span data-ttu-id="deb53-104">Cette section aborde l’utilisation de techniques de dépannage pour résoudre les erreurs d’installation.</span><span class="sxs-lookup"><span data-stu-id="deb53-104">This section discusses using troubleshooting techniques to resolve installation errors.</span></span>  
  
## <a name="logging-messages-for-setup-actions"></a><span data-ttu-id="deb53-105">Messages de journalisation pour les Actions d’installation</span><span class="sxs-lookup"><span data-stu-id="deb53-105">Logging Messages for Setup Actions</span></span>  
 <span data-ttu-id="deb53-106">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation effectue la tâche standard de l’installation du [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="deb53-106">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="deb53-107">En outre, le programme d’installation effectue également certaines actions personnalisées, telles que l’inscription des liaisons de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="deb53-107">Additionally, the setup also performs certain custom actions such as registering the adapter bindings.</span></span> <span data-ttu-id="deb53-108">Vous pouvez enregistrer les messages pour les deux les actions standards, ainsi que personnalisés que le programme d’installation exécute.</span><span class="sxs-lookup"><span data-stu-id="deb53-108">You can log messages for both the standard as well as custom actions that the setup performs.</span></span>  
  
-   <span data-ttu-id="deb53-109">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation installe les fichiers spécifiques à l’adaptateur à l’aide d’un fichier MSI.</span><span class="sxs-lookup"><span data-stu-id="deb53-109">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter-specific files using an MSI.</span></span> <span data-ttu-id="deb53-110">Par conséquent, la journalisation pour le programme d’installation est l’enregistrement du fichier MSI standard.</span><span class="sxs-lookup"><span data-stu-id="deb53-110">Therefore, the logging for the setup is the standard MSI logging.</span></span> <span data-ttu-id="deb53-111">[Journalisation du programme d’installation Windows](https://msdn.microsoft.com/library/windows/desktop/aa372847.aspx) fournit plus de détails.</span><span class="sxs-lookup"><span data-stu-id="deb53-111">[Windows Installer Logging](https://msdn.microsoft.com/library/windows/desktop/aa372847.aspx) provides more details.</span></span> 
  
-   <span data-ttu-id="deb53-112">Tous les journaux pour le programme d’installation effectue les actions personnalisées sont disponibles à % TEMP%\adaptersetup.log.</span><span class="sxs-lookup"><span data-stu-id="deb53-112">All logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log.</span></span> <span data-ttu-id="deb53-113">Si le suivi dans le fichier journal échoue, les traces sont également disponibles dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="deb53-113">If the tracing to the log file fails, the traces are also available in the event log.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="deb53-114">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="deb53-114">Known Issues</span></span>  
 <span data-ttu-id="deb53-115">Voici les erreurs les plus courantes que vous pouvez rencontrer lors de l’installation du [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], ainsi que leur cause probable et de la résolution.</span><span class="sxs-lookup"><span data-stu-id="deb53-115">The following are the most common errors you might encounter when installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], along with their probable cause and resolution.</span></span>  
  
  
  
###  <a name="BKMK_OraAppBinding"></a><span data-ttu-id="deb53-116">Le programme d’installation ne parvient pas à inscrire des liaisons de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="deb53-116">Setup fails to register adapter bindings</span></span>  
 <span data-ttu-id="deb53-117">**Problème**</span><span class="sxs-lookup"><span data-stu-id="deb53-117">**Problem**</span></span>  
  
 <span data-ttu-id="deb53-118">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant installation ne parvient pas à inscrire des liaisons de l’adaptateur, mais poursuit l’installation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="deb53-118">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the adapter bindings, but proceeds with the adapter installation.</span></span>  
  
 <span data-ttu-id="deb53-119">**Cause**</span><span class="sxs-lookup"><span data-stu-id="deb53-119">**Cause**</span></span>  
  
 <span data-ttu-id="deb53-120">Cela peut entraîner des problèmes dans [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation ou dans le fichier machine.config est endommagé.</span><span class="sxs-lookup"><span data-stu-id="deb53-120">This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span> <span data-ttu-id="deb53-121">Liaisons de l’adaptateur sont écrites dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="deb53-121">The adapter bindings are written to the machine.config file.</span></span>  
  
 <span data-ttu-id="deb53-122">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="deb53-122">**Resolution**</span></span>  
  
 <span data-ttu-id="deb53-123">Vous devez inscrire manuellement le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="deb53-123">You should manually register the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding.</span></span>  
  
##### <a name="to-register-the-adapter-binding"></a><span data-ttu-id="deb53-124">Pour inscrire la liaison de la carte</span><span class="sxs-lookup"><span data-stu-id="deb53-124">To register the adapter binding</span></span>  
  
1.  <span data-ttu-id="deb53-125">Accédez au fichier machine.config sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="deb53-125">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="deb53-126">Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="deb53-126">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
     <span data-ttu-id="deb53-127">Dans ce chemin d’accès, \< *version* \> est la version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="deb53-127">In this path, \<*version*\> is the version of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="deb53-128">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="deb53-128">Open the file by using a text editor.</span></span>  
  
3.  <span data-ttu-id="deb53-129">Pour inscrire le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] liaison :</span><span class="sxs-lookup"><span data-stu-id="deb53-129">To register the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding:</span></span>  
  
    1.  <span data-ttu-id="deb53-130">Recherchez l’élément « system.serviceModel » et ajoutez le code suivant dans cette section :</span><span class="sxs-lookup"><span data-stu-id="deb53-130">Search for the element "system.serviceModel" and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="oracleEBSBinding" contract="IMetadataExchange" name="oracleebs" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="deb53-131">Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="deb53-131">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="deb53-132">Recherchez manquants [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="deb53-132">Look for the missing [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding.</span></span> <span data-ttu-id="deb53-133">Ajoutez la section suivante sous le nœud « bindingElementExtensions ».</span><span class="sxs-lookup"><span data-stu-id="deb53-133">Add the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="deb53-134">Pour [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="deb53-134">For [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="deb53-135">Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="deb53-135">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="deb53-136">Recherchez manquants [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="deb53-136">Look for the missing [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding.</span></span> <span data-ttu-id="deb53-137">Ajoutez la section suivante sous le nœud « bindingExtensions ».</span><span class="sxs-lookup"><span data-stu-id="deb53-137">Add the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="deb53-138">Pour [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="deb53-138">For [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="deb53-139">Pour plus d’informations sur la façon de déterminer la clé publique et la version, consultez [détermination de la clé publique et la Version](#BKMK_PubKey).</span><span class="sxs-lookup"><span data-stu-id="deb53-139">For information about how to determine the public key and the version, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  
  
4.  <span data-ttu-id="deb53-140">Enregistrez et fermez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="deb53-140">Save and close the machine.config file.</span></span>  
  
####  <a name="BKMK_PubKey"></a><span data-ttu-id="deb53-141">Détermination de la clé publique et la Version</span><span class="sxs-lookup"><span data-stu-id="deb53-141">Determining the Public Key and Version</span></span>  
 <span data-ttu-id="deb53-142">Les étapes suivantes pour déterminer la clé publique pour [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="deb53-142">Perform the following steps to determine the public key for [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
###### <a name="to-determine-the-public-key"></a><span data-ttu-id="deb53-143">Pour déterminer la clé publique</span><span class="sxs-lookup"><span data-stu-id="deb53-143">To determine the public key</span></span>  
  
1.  <span data-ttu-id="deb53-144">Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.</span><span class="sxs-lookup"><span data-stu-id="deb53-144">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="deb53-145">Avec le bouton droit de la DLL pour laquelle vous souhaitez que la clé publique et la version, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="deb53-145">Right-click the DLL for which you want the public key and the version, and then select **Properties**.</span></span> <span data-ttu-id="deb53-146">Le tableau suivant répertorie le nom de la DLL pour [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="deb53-146">The following table lists the name of the DLL for [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
    |<span data-ttu-id="deb53-147">Adaptateur</span><span class="sxs-lookup"><span data-stu-id="deb53-147">Adapter</span></span>|<span data-ttu-id="deb53-148">Nom de la DLL</span><span class="sxs-lookup"><span data-stu-id="deb53-148">Name of the DLL</span></span>|  
    |-------------|---------------------|  
    |[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]|<span data-ttu-id="deb53-149">Microsoft.Adapters.OracleEBS</span><span class="sxs-lookup"><span data-stu-id="deb53-149">Microsoft.Adapters.OracleEBS</span></span>|  
  
3.  <span data-ttu-id="deb53-150">Sur le **général** onglet, la valeur par rapport à la **jeton de clé publique** étiquette spécifie la clé publique pour la DLL.</span><span class="sxs-lookup"><span data-stu-id="deb53-150">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="deb53-151">De même, la valeur par rapport à la **Version** étiquette Spécifie le numéro de version de la DLL.</span><span class="sxs-lookup"><span data-stu-id="deb53-151">Similarly, value against the **Version** label specifies the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="deb53-152">Copiez la clé publique, puis cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="deb53-152">Copy the public key, and then click **Cancel**.</span></span>  
  
###  <a name="BKMK_ConsumeOraApp"></a><span data-ttu-id="deb53-153">Erreur lors de l’utilisation du complément Consume Adapter Service ou l’ajouter Adapter Service Reference plug-in sur une installation 64 bits</span><span class="sxs-lookup"><span data-stu-id="deb53-153">Error while using the Consume Adapter Service add-in or Add Adapter Service Reference plug-in on a 64-bit installation</span></span>  
 <span data-ttu-id="deb53-154">**Problème**</span><span class="sxs-lookup"><span data-stu-id="deb53-154">**Problem**</span></span>  
  
 <span data-ttu-id="deb53-155">À l’aide de la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] sur un ordinateur 64 bits exécutant la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] entraîne l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="deb53-155">Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:</span></span>  
  
```  
No valid adapters are installed on this machine  
```  
  
 <span data-ttu-id="deb53-156">**Cause**</span><span class="sxs-lookup"><span data-stu-id="deb53-156">**Cause**</span></span>  
  
 <span data-ttu-id="deb53-157">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="deb53-157">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="deb53-158">Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits.</span><span class="sxs-lookup"><span data-stu-id="deb53-158">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="deb53-159">Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="deb53-159">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="deb53-160">Toutefois, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] s’exécute comme un processus 32 bits et par conséquent, lorsque vous lancez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], le plug-in vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.</span><span class="sxs-lookup"><span data-stu-id="deb53-160">However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="deb53-161">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="deb53-161">**Resolution**</span></span>  
  
-   <span data-ttu-id="deb53-162">Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="deb53-162">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="deb53-163">Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="deb53-163">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="deb53-164">Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="deb53-164">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
-   <span data-ttu-id="deb53-165">Installez les versions 32 bits et 64 bits d’Oracle Data Access Components pour Client Oracle 11.1.0.6 avec le jeu de correctifs 11.1.0.7.</span><span class="sxs-lookup"><span data-stu-id="deb53-165">Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="deb53-166">Pour vous assurer que votre application fonctionne avec la version la plus récente de ODP.NET, vous devez avoir « Stratégie dll » installé sur l’ordinateur et enregistré dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="deb53-166">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="deb53-167">Pour plus d’informations, consultez « Oracle données fournisseur pour .NET FAQ » à [http://go.microsoft.com/fwlink/p/?LinkId=92834](http://go.microsoft.com/fwlink/p/?LinkId=92834).</span><span class="sxs-lookup"><span data-stu-id="deb53-167">For more information, see "Oracle Data Provider for .NET FAQ" at [http://go.microsoft.com/fwlink/p/?LinkId=92834](http://go.microsoft.com/fwlink/p/?LinkId=92834).</span></span>  
  
###  <a name="BKMK_OraAppInvalidBinding"></a><span data-ttu-id="deb53-168">Erreur de liaison non valide lors de la configuration des ports d’adaptateur Oracle E-Business Suite dans la Console Administration de BizTalk Server sur une installation 64 bits</span><span class="sxs-lookup"><span data-stu-id="deb53-168">Invalid binding error while configuring Oracle E-Business Suite adapter ports in BizTalk Server Administration Console on a 64-bit installation</span></span>  
 <span data-ttu-id="deb53-169">**Problème**</span><span class="sxs-lookup"><span data-stu-id="deb53-169">**Problem**</span></span>  
  
 <span data-ttu-id="deb53-170">Lorsque vous essayez de configurer un port de l’adaptateur dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous obtenez l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="deb53-170">When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:</span></span>  
  
```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "oracleEBSBinding".  
Verify the binding extension is registered in machine.config."  
```  
  
 <span data-ttu-id="deb53-171">**Cause**</span><span class="sxs-lookup"><span data-stu-id="deb53-171">**Cause**</span></span>  
  
 <span data-ttu-id="deb53-172">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="deb53-172">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="deb53-173">Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits.</span><span class="sxs-lookup"><span data-stu-id="deb53-173">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="deb53-174">Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="deb53-174">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="deb53-175">Toutefois, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration s’exécute comme un processus 32 bits et par conséquent, lorsque vous configurez un port de l’adaptateur, il vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.</span><span class="sxs-lookup"><span data-stu-id="deb53-175">However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="deb53-176">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="deb53-176">**Resolution**</span></span>  
  
-   <span data-ttu-id="deb53-177">Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="deb53-177">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="deb53-178">Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="deb53-178">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="deb53-179">Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="deb53-179">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
-   <span data-ttu-id="deb53-180">Installez les versions 32 bits et 64 bits d’Oracle Data Access Components pour Client Oracle 11.1.0.6 avec le jeu de correctifs 11.1.0.7.</span><span class="sxs-lookup"><span data-stu-id="deb53-180">Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="deb53-181">Pour vous assurer que votre application fonctionne avec la version la plus récente de ODP.NET, vous devez avoir « Stratégie dll » installé sur l’ordinateur et enregistré dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="deb53-181">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="deb53-182">Pour plus d’informations, consultez « Oracle données fournisseur pour .NET FAQ » à [http://go.microsoft.com/fwlink/p/?LinkId=92834](http://go.microsoft.com/fwlink/p/?LinkId=92834).</span><span class="sxs-lookup"><span data-stu-id="deb53-182">For more information, see "Oracle Data Provider for .NET FAQ" at [http://go.microsoft.com/fwlink/p/?LinkId=92834](http://go.microsoft.com/fwlink/p/?LinkId=92834).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb53-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="deb53-183">See Also</span></span>  
[<span data-ttu-id="deb53-184">Dépannage de l’adaptateur Oracle eBusiness Suite</span><span class="sxs-lookup"><span data-stu-id="deb53-184">Troubleshooting the Oracle EBS adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)