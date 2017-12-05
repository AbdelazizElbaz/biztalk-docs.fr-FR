---
title: "Valider les étapes d’installation pour 2016 de pack d’adaptateur BizTalk | Documents Microsoft"
description: "Étapes à effectuer après avoir installé BAP 2016, y compris ajoutent l’adaptateur pour l’Administration de BizTalk, la mise à jour Oracle et inscription des liaisons de l’adaptateur."
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8946bfe-92bb-470d-bec4-9bc3a07ce0d2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17bd0a76cacb35563448f31f79c2275c79b92ab8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="post-installation-steps-for-biztalk-adapter-pack-2016"></a><span data-ttu-id="03a7d-103">Valider les étapes d’installation de BizTalk adaptateur Pack 2016</span><span class="sxs-lookup"><span data-stu-id="03a7d-103">Post installation steps for BizTalk Adapter Pack 2016</span></span>
<span data-ttu-id="03a7d-104">Après avoir installé le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], quelques étapes consécutives à l’installation.</span><span class="sxs-lookup"><span data-stu-id="03a7d-104">After you install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], there are some post-installation steps.</span></span> <span data-ttu-id="03a7d-105">Cette rubrique décrit ces étapes.</span><span class="sxs-lookup"><span data-stu-id="03a7d-105">This topic lists these steps.</span></span>   

## <a name="add-the-adapter-to-biztalk-administration"></a><span data-ttu-id="03a7d-106">Ajouter l’adaptateur à l’Administration de BizTalk</span><span class="sxs-lookup"><span data-stu-id="03a7d-106">Add the adapter to BizTalk Administration</span></span>
  
1.  <span data-ttu-id="03a7d-107">Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="03a7d-107">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="03a7d-108">Développez le **groupe BizTalk**, développez **paramètres de plateforme**, puis sélectionnez **cartes**.</span><span class="sxs-lookup"><span data-stu-id="03a7d-108">Expand the **BizTalk Group**, expand **Platform Settings**, and then select **Adapters**.</span></span>  
  
3.  <span data-ttu-id="03a7d-109">Avec le bouton droit **cartes**, sélectionnez **nouveau**, puis sélectionnez **carte**.</span><span class="sxs-lookup"><span data-stu-id="03a7d-109">Right-click **Adapters**, select **New**, and select **Adapter**.</span></span>  
  
     <span data-ttu-id="03a7d-110">![Ajouter un adaptateur](../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span><span class="sxs-lookup"><span data-stu-id="03a7d-110">![Add an adapter](../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span></span>  
  
4.  <span data-ttu-id="03a7d-111">Dans le **propriétés de l’adaptateur**, sélectionnez une carte dans la liste déroulante, telle que **WCF SAP**, puis entrez un nom, tel que **WCF SAP**.</span><span class="sxs-lookup"><span data-stu-id="03a7d-111">In the **Adapter Properties**, select an adapter from the drop-down list, such as **WCF-SAP**, and then enter a name, such as **WCF-SAP**.</span></span>  
  
     <span data-ttu-id="03a7d-112">![Ajouter un adaptateur SAP à BizTalk](../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")</span><span class="sxs-lookup"><span data-stu-id="03a7d-112">![Add SAP Adapter to BizTalk](../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")</span></span>  
  
5.  <span data-ttu-id="03a7d-113">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="03a7d-113">Select **OK**.</span></span>  

## <a name="use-a-newer-oracledataaccessdll-version"></a><span data-ttu-id="03a7d-114">Utilisez une version plus récente de Oracle.DataAccess.dll</span><span class="sxs-lookup"><span data-stu-id="03a7d-114">Use a newer Oracle.DataAccess.dll version</span></span>  

<span data-ttu-id="03a7d-115">Lorsque vous configurez un port à utiliser l’adaptateur WCF-OracleDB ou utiliser Visual Studio pour consommer un adaptateur généré, un message s’affiche que l’adaptateur doit Oracle.DataAccess.dll version 2.111.7.0.</span><span class="sxs-lookup"><span data-stu-id="03a7d-115">When you configure a port to use the WCF-OracleDB adapter or use Visual Studio to consume a generated adapter, a message displays that the adapter needs Oracle.DataAccess.dll version 2.111.7.0.</span></span> <span data-ttu-id="03a7d-116">Pour résoudre ce message, installez une version prise en charge de Oracle.DataAccess.dll (consultez [prise en charge de la liste des versions](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)), puis mettez à jour le `bindingRedirect` élément dans le fichier de configuration OracleDB en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="03a7d-116">To resolve this message, install a supported Oracle.DataAccess.dll version (see [supported version list](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)), and then update the `bindingRedirect` element in the OracleDB configuration file using the following steps:</span></span>  
  
1.  <span data-ttu-id="03a7d-117">Sur le serveur BizTalk Server, accédez aux dossiers suivants :</span><span class="sxs-lookup"><span data-stu-id="03a7d-117">On the BizTalk Server, go to the following folders:</span></span>  
  
     <span data-ttu-id="03a7d-118">*lecteur*: \Program Files\Microsoft BizTalk Adapter Pack (x64) \bin</span><span class="sxs-lookup"><span data-stu-id="03a7d-118">*drive*:\Program Files\Microsoft BizTalk Adapter Pack(x64)\bin</span></span>  
  
     <span data-ttu-id="03a7d-119">*lecteur*: \Program fichiers (x86) \Microsoft BizTalk Adapter Pack\bin</span><span class="sxs-lookup"><span data-stu-id="03a7d-119">*drive*:\Program Files (x86)\Microsoft BizTalk Adapter Pack\bin</span></span>  
  
2.  <span data-ttu-id="03a7d-120">Ouvrez le fichier Microsoft.Adapters.OracleDB.config.</span><span class="sxs-lookup"><span data-stu-id="03a7d-120">Open the Microsoft.Adapters.OracleDB.config file.</span></span>  
  
3.  <span data-ttu-id="03a7d-121">Recherchez la section suivante, puis copier/coller les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="03a7d-121">Find the following section, and then copy/paste the following:</span></span>  
  
    ```  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
              <dependentAssembly>  
                        <assemblyIdentity name="Oracle.DataAccess" publicKeyToken="89b483f429c47342" culture="neutral" />  
                        <bindingRedirect oldVersion="2.111.7.00" newVersion="2.112.1.00"/>  
              </dependentAssembly>  
    </assemblyBinding>  
  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="03a7d-122">Dans cet exemple, nous avons défini *newVersion* à 2.112.1.00.</span><span class="sxs-lookup"><span data-stu-id="03a7d-122">In this example, we set *newVersion* to 2.112.1.00.</span></span> <span data-ttu-id="03a7d-123">Définissez cette valeur à la version que vous avez installé.</span><span class="sxs-lookup"><span data-stu-id="03a7d-123">Set this value to the version you have installed.</span></span>  
  
> [!IMPORTANT]
> - <span data-ttu-id="03a7d-124">S’il existe plusieurs serveurs BizTalk Server dans ce groupe, apporter cette modification sur tous les serveurs BizTalk du groupe.</span><span class="sxs-lookup"><span data-stu-id="03a7d-124">If there are multiple BizTalk Servers in this group, make this change on all the BizTalk servers in the group.</span></span>  
> - <span data-ttu-id="03a7d-125">Le *newVersion* valeur doit être mis à jour en fonction de la version du fichier Oracle.DataAccess.dll installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="03a7d-125">The *newVersion* value needs to be updated based on the version of the Oracle.DataAccess.dll file installed on the computer.</span></span>  <span data-ttu-id="03a7d-126">Oracle.DataAccess.dll est inclus avec le Client Oracle que vous installez à partir d’Oracle.</span><span class="sxs-lookup"><span data-stu-id="03a7d-126">Oracle.DataAccess.dll is included with the Oracle Client you install from Oracle.</span></span>  <span data-ttu-id="03a7d-127">Vous devez installer uniquement une version de Client Oracle est [pris en charge par BizTalk Adapter Pack](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx).</span><span class="sxs-lookup"><span data-stu-id="03a7d-127">You must only install an Oracle Client version that is [supported by the BizTalk Adapter Pack](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx).</span></span>  
  
## <a name="create-sql-server-database-objects-sap-adapter-only"></a><span data-ttu-id="03a7d-128">Créer des objets de base de données SQL Server (adaptateur SAP uniquement)</span><span class="sxs-lookup"><span data-stu-id="03a7d-128">Create SQL Server Database objects (SAP adapter only)</span></span>  
 <span data-ttu-id="03a7d-129">Pour appeler tRFCs dans un système SAP, exécutez le *SapAdapter-DbScript-Install.sql* script SQL.</span><span class="sxs-lookup"><span data-stu-id="03a7d-129">To invoke tRFCs in an SAP system, run the *SapAdapter-DbScript-Install.sql* SQL script.</span></span> <span data-ttu-id="03a7d-130">Ce script est installé avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation et crée des objets de base de données dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="03a7d-130">This script is installed with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, and creates database objects in SQL Server.</span></span> <span data-ttu-id="03a7d-131">Le script est généralement installé sur  *\<lecteur d’installation\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]* .</span><span class="sxs-lookup"><span data-stu-id="03a7d-131">The script is typically installed at *\<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]*.</span></span> <span data-ttu-id="03a7d-132">Vous pouvez exécuter ce script sur toute base de données SQL Server, tant que vous entrez son nom de base de données lors de l’utilisation de l’adaptateur pour appeler tRFCs.</span><span class="sxs-lookup"><span data-stu-id="03a7d-132">You can run this script against any SQL Server database, as long as you enter that database name while using the adapter to invoke tRFCs.</span></span>
  
## <a name="register-the-adapter-bindings"></a><span data-ttu-id="03a7d-133">Inscrire des liaisons de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="03a7d-133">Register the adapter bindings</span></span>
<span data-ttu-id="03a7d-134">Lors de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, l’Assistant installation peut échouer enregistrer des liaisons de l’adaptateur ou le fournisseur de données .NET Framework pour mySAP Business Suite.</span><span class="sxs-lookup"><span data-stu-id="03a7d-134">During the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, the setup wizard may fail to register the adapter bindings or the .NET Framework Data Provider for mySAP Business Suite.</span></span> <span data-ttu-id="03a7d-135">Et le programme d’installation poursuit l’installation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="03a7d-135">And the setup proceeds with the adapter installation.</span></span> <span data-ttu-id="03a7d-136">Cela peut être dû à l’installation de Windows Communication Foundation (WCF), le [!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)] installation ou dans le fichier machine.config est endommagé.</span><span class="sxs-lookup"><span data-stu-id="03a7d-136">This may be caused by the Windows Communication Foundation (WCF) installation, the [!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="03a7d-137">Effectuez les étapes suivantes *uniquement* si l’Assistant installation ne parvient pas à inscrire des liaisons de l’adaptateur, les fournisseurs de données .NET Framework dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="03a7d-137">Complete the following steps *only* if the setup wizard fails to register the adapter bindings, or .NET Framework Data Providers in the machine.config file.</span></span>  
  
1.  <span data-ttu-id="03a7d-138">Accédez au fichier machine.config sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="03a7d-138">Go to the machine.config file on the computer.</span></span> <span data-ttu-id="03a7d-139">Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous  *\<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG*.</span><span class="sxs-lookup"><span data-stu-id="03a7d-139">For example, on a 32-bit platform, the machine.config is available under *\<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG*.</span></span>  
  
2.  <span data-ttu-id="03a7d-140">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="03a7d-140">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="03a7d-141">Enregistrer des liaisons de l’adaptateur :</span><span class="sxs-lookup"><span data-stu-id="03a7d-141">Register the adapter bindings:</span></span>  
  
    1.  <span data-ttu-id="03a7d-142">Recherchez le `system.serviceModel` élément et ajoutez le code suivant dans cette section :</span><span class="sxs-lookup"><span data-stu-id="03a7d-142">Search for the `system.serviceModel` element, and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
          <endpoint binding="oracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="03a7d-143">Recherchez le `bindingElementExtensions` élément sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="03a7d-143">Search for the `bindingElementExtensions` element under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="03a7d-144">Recherchez la liaison de l’adaptateur manquant.</span><span class="sxs-lookup"><span data-stu-id="03a7d-144">Look for the missing adapter binding.</span></span> <span data-ttu-id="03a7d-145">Ajoutez les sections suivantes sous la `bindingElementExtensions` nœud, en fonction de la liaison de l’adaptateur manquant.</span><span class="sxs-lookup"><span data-stu-id="03a7d-145">Add the following sections under the `bindingElementExtensions` node, depending on the missing adapter binding.</span></span> <span data-ttu-id="03a7d-146">Vous devez enregistrer toutes les liaisons si l’Assistant installation ne parvient pas à inscrire.</span><span class="sxs-lookup"><span data-stu-id="03a7d-146">You must register all the bindings if the setup wizard fails to register any.</span></span>  
  
         <span data-ttu-id="03a7d-147">Pour le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-147">For the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], add:</span></span>  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="03a7d-148">Pour le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-148">For the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], add:</span></span>  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="03a7d-149">Pour le [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-149">For the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="03a7d-150">Pour le [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-150">For the [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], add:</span></span>  
  
        ```  
        <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="03a7d-151">Pour le [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-151">For the [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="03a7d-152">Recherchez le `bindingExtensions` élément sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="03a7d-152">Search for the `bindingExtensions` element under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="03a7d-153">Recherchez la liaison de l’adaptateur manquant.</span><span class="sxs-lookup"><span data-stu-id="03a7d-153">Look for the missing adapter binding.</span></span> <span data-ttu-id="03a7d-154">Ajoutez les sections suivantes sous la `bindingExtensions` nœud, en fonction de la liaison de l’adaptateur manquant.</span><span class="sxs-lookup"><span data-stu-id="03a7d-154">Add the following sections under the `bindingExtensions` node, depending on the missing adapter binding.</span></span> <span data-ttu-id="03a7d-155">Vous devez enregistrer toutes les liaisons si l’Assistant installation ne parvient pas à inscrire.</span><span class="sxs-lookup"><span data-stu-id="03a7d-155">You must register all the bindings if the setup wizard fails to register any.</span></span>  
  
         <span data-ttu-id="03a7d-156">Pour [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-156">For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], add:</span></span>  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="03a7d-157">Pour [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-157">For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], add:</span></span>  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="03a7d-158">Pour [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-158">For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="03a7d-159">Pour [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-159">For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], add:</span></span>  
  
        ```  
        <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS,Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="03a7d-160">Pour [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-160">For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="03a7d-161">Pour obtenir la valeur de clé publique, consultez **déterminer la clé publique et la version** (dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="03a7d-161">To get the public key value, see **Determine the public key and version** (in this topic).</span></span>  
  
4.  <span data-ttu-id="03a7d-162">Inscrire les fournisseurs de données .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="03a7d-162">Register the .NET Framework data providers:</span></span>  
  
    1.  <span data-ttu-id="03a7d-163">Recherchez le `DbProviderFactories` élément sous le nœud system.data.</span><span class="sxs-lookup"><span data-stu-id="03a7d-163">Search for the `DbProviderFactories` element under the system.data node.</span></span>  
  
    2.  <span data-ttu-id="03a7d-164">Recherchez les fournisseurs de données .NET Framework manquante.</span><span class="sxs-lookup"><span data-stu-id="03a7d-164">Look for the missing .NET Framework Data Providers.</span></span> <span data-ttu-id="03a7d-165">Ajoutez les sections suivantes sous la `DbProviderFactories` nœud, en fonction du fournisseur manquant.</span><span class="sxs-lookup"><span data-stu-id="03a7d-165">Add the following sections under the `DbProviderFactories` node, depending on the missing provider.</span></span> <span data-ttu-id="03a7d-166">Vous devez inscrire tous les fournisseurs de si l’Assistant installation ne parvient pas à inscrire.</span><span class="sxs-lookup"><span data-stu-id="03a7d-166">You must register all the providers if the setup wizard fails to register any.</span></span>  
  
         <span data-ttu-id="03a7d-167">Pour le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-167">For the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], add:</span></span>  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
            description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="03a7d-168">Pour le [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="03a7d-168">For the [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], add:</span></span>  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  <span data-ttu-id="03a7d-169">Enregistrez et fermez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="03a7d-169">Save and close the machine.config file.</span></span>  
  
## <a name="determine-the-public-key-and-version"></a><span data-ttu-id="03a7d-170">Déterminer la version et la clé publique</span><span class="sxs-lookup"><span data-stu-id="03a7d-170">Determine the public key and version</span></span>  
 <span data-ttu-id="03a7d-171">Effectuez les étapes suivantes pour déterminer la version d’un adaptateur ou le fournisseur de données .NET Framework et la clé publique.</span><span class="sxs-lookup"><span data-stu-id="03a7d-171">Complete the following steps to determine the public key and version for an adapter or the .NET Framework Data Provider.</span></span>  
  
1.  <span data-ttu-id="03a7d-172">Accédez au répertoire Windows, généralement *C:\WINDOWS\assembly*.</span><span class="sxs-lookup"><span data-stu-id="03a7d-172">Go to the Windows directory, typically *C:\WINDOWS\assembly*.</span></span>  
  
2.  <span data-ttu-id="03a7d-173">Avec le bouton droit de la DLL pour laquelle vous souhaitez que la clé publique, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="03a7d-173">Right-click the DLL for which you want the public key, and then select **Properties**.</span></span> <span data-ttu-id="03a7d-174">Le tableau suivant répertorie le nom des DLL pour chaque fournisseur et la carte :</span><span class="sxs-lookup"><span data-stu-id="03a7d-174">The following table lists the name of the DLLs for each adapter and provider:</span></span>  
  
    |<span data-ttu-id="03a7d-175">Adaptateur/.NET Framework Data Provider</span><span class="sxs-lookup"><span data-stu-id="03a7d-175">Adapter/.NET Framework Data Provider</span></span>|<span data-ttu-id="03a7d-176">Nom de la DLL</span><span class="sxs-lookup"><span data-stu-id="03a7d-176">Name of the DLL</span></span>|  
    |---|---|  
    |[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]|<span data-ttu-id="03a7d-177">Microsoft.Adapters.SAP</span><span class="sxs-lookup"><span data-stu-id="03a7d-177">Microsoft.Adapters.SAP</span></span>|  
    |[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]|<span data-ttu-id="03a7d-178">Microsoft.Adapters.Siebel</span><span class="sxs-lookup"><span data-stu-id="03a7d-178">Microsoft.Adapters.Siebel</span></span>|  
    |[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]|<span data-ttu-id="03a7d-179">Microsoft.Adapters.OracleDB</span><span class="sxs-lookup"><span data-stu-id="03a7d-179">Microsoft.Adapters.OracleDB</span></span>|  
    |[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]|<span data-ttu-id="03a7d-180">Microsoft.Adapters.OracleEBS</span><span class="sxs-lookup"><span data-stu-id="03a7d-180">Microsoft.Adapters.OracleEBS</span></span>|  
    |[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]|<span data-ttu-id="03a7d-181">Microsoft.Adapters.Sql.dll</span><span class="sxs-lookup"><span data-stu-id="03a7d-181">Microsoft.Adapters.Sql.dll</span></span>|  
    |[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]|<span data-ttu-id="03a7d-182">Microsoft.Data.SAPClient</span><span class="sxs-lookup"><span data-stu-id="03a7d-182">Microsoft.Data.SAPClient</span></span>|  
    |[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]|<span data-ttu-id="03a7d-183">Microsoft.Data.SiebelClient</span><span class="sxs-lookup"><span data-stu-id="03a7d-183">Microsoft.Data.SiebelClient</span></span>|  
  
3.  <span data-ttu-id="03a7d-184">Sur le **général** onglet, le **jeton de clé publique** valeur est la clé publique pour la DLL.</span><span class="sxs-lookup"><span data-stu-id="03a7d-184">On the **General** tab, the **Public Key Token** value is the public key for the DLL.</span></span> <span data-ttu-id="03a7d-185">Le **Version** valeur est le numéro de version de la DLL.</span><span class="sxs-lookup"><span data-stu-id="03a7d-185">The **Version** value is the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="03a7d-186">Copiez la clé publique, puis **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="03a7d-186">Copy the public key, and then select **Cancel**.</span></span>  
  
## <a name="install-the-custom-rfcs"></a><span data-ttu-id="03a7d-187">Installez les RFC personnalisés</span><span class="sxs-lookup"><span data-stu-id="03a7d-187">Install the custom RFCs</span></span>  
<span data-ttu-id="03a7d-188">Obligatoire uniquement *si* vous souhaitez utiliser le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03a7d-188">Required only *if* you want to use the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="03a7d-189">Consultez [installer les RFC personnalisés](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md) dans le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] documentation.</span><span class="sxs-lookup"><span data-stu-id="03a7d-189">See [Install Custom RFCs](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md) in the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] documentation.</span></span> 
  
> [!IMPORTANT]
>  <span data-ttu-id="03a7d-190">Si vous utilisez une version antérieure des RFC personnalisés fournis avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], puis vous devez les mettre à niveau pour les documents RFC fournis avec cette version.</span><span class="sxs-lookup"><span data-stu-id="03a7d-190">If you are using an earlier version of the custom RFCs provided with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], then you must upgrade them to the RFCs provided with this release.</span></span> <span data-ttu-id="03a7d-191">Cela en supprimant les RFC antérieures, puis installer les RFC inclus avec cette version.</span><span class="sxs-lookup"><span data-stu-id="03a7d-191">Do this by removing the earlier RFCs, and then installing the RFCs included with this release.</span></span>  

## <a name="install-the-enterprise-applications"></a><span data-ttu-id="03a7d-192">Installer les applications d’entreprise</span><span class="sxs-lookup"><span data-stu-id="03a7d-192">Install the enterprise applications</span></span>  
<span data-ttu-id="03a7d-193">Pour les étapes et des conseils pour installer les systèmes métier entreprise différente, nous vous recommandons de qu'utiliser les guides d’installation fournis par le système de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="03a7d-193">For the steps and guidance to install the different enterprise LOB systems, we recommend you use the installation guides provided by the enterprise system.</span></span> <span data-ttu-id="03a7d-194">Également faire référence à la documentation de l’adaptateur pour les modifications de configuration spécifique, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="03a7d-194">Also refer to its adapter documentation for specific configuration changes, if any.</span></span>   

## <a name="installation-and-post-installation-checklist"></a><span data-ttu-id="03a7d-195">Liste de vérification installation et après l’installation</span><span class="sxs-lookup"><span data-stu-id="03a7d-195">Installation and post-installation checklist</span></span>  
  
-   <span data-ttu-id="03a7d-196">Assurez-vous que vous avez installé tous les [les composants logiciels requis](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md) avec l’option d’installation correct.</span><span class="sxs-lookup"><span data-stu-id="03a7d-196">Make sure you installed all the [software prerequisites](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md) with the correct installation option.</span></span>
  
-   <span data-ttu-id="03a7d-197">Assurez-vous que vous disposez de la version prise en charge des applications métier enterprise installée sur votre ordinateur où vous avez installé le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03a7d-197">Make sure you have the supported version of the enterprise LOB applications installed on your computer where you installed the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="03a7d-198">Consultez [systèmes de prise en charge de métier (LOB)](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx).</span><span class="sxs-lookup"><span data-stu-id="03a7d-198">See [Supported Line-of-Business (LOB) systems](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx).</span></span>  
  
-   <span data-ttu-id="03a7d-199">Pour installer uniquement l’adaptateur pour le système métier que vous souhaitez vous connecter, vérifiez que vous avez installé le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] à l’aide de la **personnalisé** option d’installation.</span><span class="sxs-lookup"><span data-stu-id="03a7d-199">To install only the adapter for the enterprise LOB system you want to connect, make sure you installed the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] using the **Custom** installation option.</span></span> <span data-ttu-id="03a7d-200">Assurez-vous que vous n’avez pas utilisé le **Complete** option d’installation.</span><span class="sxs-lookup"><span data-stu-id="03a7d-200">Make sure you did not use the **Complete** installation option.</span></span> <span data-ttu-id="03a7d-201">Consultez [l’installation de BizTalk Adapter Pack](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md).</span><span class="sxs-lookup"><span data-stu-id="03a7d-201">See [Installing the BizTalk Adapter Pack](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md).</span></span>  
  
-   <span data-ttu-id="03a7d-202">Si vous souhaitez effectuer des appels tRFC au système SAP en utilisant le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], assurez-vous de créer les tables requises dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="03a7d-202">If you want to make tRFC calls to the SAP system using the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], make sure you create the required tables in a SQL Server database.</span></span> <span data-ttu-id="03a7d-203">Consultez **les objets de créer une base de données SQL Server** (dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="03a7d-203">See **Create SQL Server Database objects** (in this topic).</span></span>
  
-   <span data-ttu-id="03a7d-204">Lors de l’exécution du [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] Assistant installation, vous risquez d’obtenir un message d’erreur indiquant l’échec de la configuration inscrire les liaisons.</span><span class="sxs-lookup"><span data-stu-id="03a7d-204">While running the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] setup wizard, you may get an error message that states the setup failed to register the bindings.</span></span> <span data-ttu-id="03a7d-205">Dans ce cas, inscrivez-le manuellement.</span><span class="sxs-lookup"><span data-stu-id="03a7d-205">If so, register them manually.</span></span> <span data-ttu-id="03a7d-206">Consultez **enregistrer des liaisons de l’adaptateur** (dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="03a7d-206">See **Register the adapter bindings** (in this topic).</span></span>  
  
-   <span data-ttu-id="03a7d-207">Si vous avez choisi d’installer le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)] dans le cadre de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, veillez à installer les RFC personnalisés sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="03a7d-207">If you chose to install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)] as part of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, make sure you install the custom RFCs on the SAP system.</span></span> <span data-ttu-id="03a7d-208">Consultez [installer les RFC personnalisés](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span><span class="sxs-lookup"><span data-stu-id="03a7d-208">See [Install Custom RFCs](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>

## <a name="more-good-info"></a><span data-ttu-id="03a7d-209">Plus d’informations correct</span><span class="sxs-lookup"><span data-stu-id="03a7d-209">More good info</span></span>
[<span data-ttu-id="03a7d-210">Modifier ou supprimer le Pack d’adaptateurs BizTalk</span><span class="sxs-lookup"><span data-stu-id="03a7d-210">Change or remove the BizTalk Adapter Pack</span></span>](../adapters-and-accelerators/update-or-uninstall-the-biztalk-adapter-pack-2016.md)  
[<span data-ttu-id="03a7d-211">BizTalk Adapter Pack Forum aux questions</span><span class="sxs-lookup"><span data-stu-id="03a7d-211">BizTalk Adapter Pack FAQ</span></span>](../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)