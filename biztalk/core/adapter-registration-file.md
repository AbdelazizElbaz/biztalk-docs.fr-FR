---
title: "Fichier d’inscription de carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6750f0ed-4411-4a63-a7fe-f66132cd1e22
caps.latest.revision: "35"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c38d00cbaf5d34aa880f5efd1d9e9a59d59c4e0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="adapter-registration-file"></a><span data-ttu-id="46b5f-102">Fichier d'inscription de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="46b5f-102">Adapter Registration File</span></span>
<span data-ttu-id="46b5f-103">Une fois le code de l'adaptateur personnalisé correctement généré, il doit être inscrit auprès de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46b5f-103">After the custom adapter code has been successfully built it must be registered with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="46b5f-104">Pour ce faire, il convient de mettre à jour le Registre à l'aide des paramètres appropriés de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="46b5f-104">You do this by updating the registry with the appropriate adapter settings.</span></span> <span data-ttu-id="46b5f-105">Vous pouvez écrire manuellement un fichier de Registre, mais il y a un risque d'erreurs en raison de la précision et de la complexité des informations que vous devrez entrer.</span><span class="sxs-lookup"><span data-stu-id="46b5f-105">You can manually write a registry file, but this is prone to errors due to the preciseness and complexity of the information that you need to enter.</span></span> <span data-ttu-id="46b5f-106">Il est conseillé d'exécuter l'Assistant Registre d'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="46b5f-106">A better decision is to run the Adapter Registry Wizard.</span></span> <span data-ttu-id="46b5f-107">Cet Assistant vous propose les mêmes options que si vous génériez un fichier de Registre en partant de zéro et il réduit le risque d'erreurs dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="46b5f-107">The Adapter Registry Wizard gives you all the same options as creating a registry file from scratch, and reduces the likelihood of errors in the file.</span></span> <span data-ttu-id="46b5f-108">Pour plus d’informations sur cet Assistant, consultez [Assistant Registre d’adaptateur](../core/adapter-registry-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="46b5f-108">For more information about the Adapter Registry Wizard, see [Adapter Registry Wizard](../core/adapter-registry-wizard.md).</span></span>  
  
 <span data-ttu-id="46b5f-109">Le fichier StaticAdapterManagement.reg et DynamicAdapterManagement.reg sont trouvent dans  *\<lecteur\>*: \Program Files\Microsoft Server\SDK\Samples\AdaptersDevelopment\File l’adaptateur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="46b5f-109">The StaticAdapterManagement.reg file and DynamicAdapterManagement.reg file are located at *\<drive\>*:\Program Files\Microsoft BizTalk Server\SDK\Samples\AdaptersDevelopment\File Adapter.</span></span> <span data-ttu-id="46b5f-110">Lorsque vous exécutez un de ces fichiers (vous pouvez double-cliquer dessus ou faites un clic droit et sélectionnez **fusion**), il inscrit l’exemple d’adaptateur file dans le Registre et installe l’assembly dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="46b5f-110">When you run one of these files (you can double-click it or right-click it and and select **Merge**), it registers the sample file adapter with the registry and installs the assembly into the global assembly cache.</span></span> <span data-ttu-id="46b5f-111">Pour enregistrer votre adaptateur personnalisé, la meilleure méthode consiste à créer un fichier de Registre en utilisant l'Assistant Registre d'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="46b5f-111">To register your custom adapter the best option is to create a new registry file by using the Adapter Registry Wizard.</span></span> <span data-ttu-id="46b5f-112">Si votre adaptateur statique personnalisé est identique à l'adaptateur exemple, et que vous décidiez à la place de modifier le fichier de Registre existant, ouvrez le fichier StaticAdapterManagement.reg et modifiez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="46b5f-112">If your custom static adapter is similar to the sample adapter, and you decide to modify the existing registry file instead, open and modify the following properties in the StaticAdapterManagement.reg file:</span></span>  
  
-   <span data-ttu-id="46b5f-113">**Contraintes**</span><span class="sxs-lookup"><span data-stu-id="46b5f-113">**Constraints**</span></span>  
  
-   <span data-ttu-id="46b5f-114">**InboundTypeName**</span><span class="sxs-lookup"><span data-stu-id="46b5f-114">**InboundTypeName**</span></span>  
  
-   <span data-ttu-id="46b5f-115">**InboundAssemblyPath**</span><span class="sxs-lookup"><span data-stu-id="46b5f-115">**InboundAssemblyPath**</span></span>  
  
-   <span data-ttu-id="46b5f-116">**OutboundTypeName**</span><span class="sxs-lookup"><span data-stu-id="46b5f-116">**OutboundTypeName**</span></span>  
  
-   <span data-ttu-id="46b5f-117">**OutboundAssemblyPath**</span><span class="sxs-lookup"><span data-stu-id="46b5f-117">**OutboundAssemblyPath**</span></span>  
  
-   <span data-ttu-id="46b5f-118">**AdapterMgmtTypeName**</span><span class="sxs-lookup"><span data-stu-id="46b5f-118">**AdapterMgmtTypeName**</span></span>  
  
-   <span data-ttu-id="46b5f-119">**AdapterMgmtAssemblyPath**</span><span class="sxs-lookup"><span data-stu-id="46b5f-119">**AdapterMgmtAssemblyPath**</span></span>  
  
-   <span data-ttu-id="46b5f-120">**PropertyNameSpace**</span><span class="sxs-lookup"><span data-stu-id="46b5f-120">**PropertyNameSpace**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46b5f-121">Pour **OutboundAssemblyPath** et **AdapterMgmtAssemblyPath** nous recommandons que vous n'incluez pas le chemin d’accès local dans la valeur de propriété, car la configuration pourrait échouer lors de l’installation sur différents emplacements du serveur.</span><span class="sxs-lookup"><span data-stu-id="46b5f-121">For **OutboundAssemblyPath** and **AdapterMgmtAssemblyPath** we recommend that you not include the local path in the property value, because the configuration could break when installed on different server locations.</span></span> <span data-ttu-id="46b5f-122">Il vaut mieux utiliser un nom fort et l'installer dans le GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="46b5f-122">A better choice is to use a strong name and install it in the global assembly cache.</span></span>  
  
 <span data-ttu-id="46b5f-123">Vous avez deux possibilités pour spécifier le type .NET implémentant le récepteur de l'adaptateur, l'émetteur de l'adaptateur et la gestion de l'adaptateur :</span><span class="sxs-lookup"><span data-stu-id="46b5f-123">You have two options for specifying the .NET type that implements the adapter receiver, adapter transmitter, and adapter management:</span></span>  
  
1.  <span data-ttu-id="46b5f-124">Installez la carte dans un dossier et spécifiez * TypeName et \*AssemblyPath où \*TypeName est de type. Nom complet de la classe et \*AssemblyPath est le chemin d’accès et le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="46b5f-124">Install the adapter to a folder and specify *TypeName and \*AssemblyPath where \*TypeName is type.FullName of the class and \*AssemblyPath is the path and file name of the assembly.</span></span>  
  
2.  <span data-ttu-id="46b5f-125">Installez l’adaptateur dans le global assembly cache et spécifiez uniquement * TypeName où \*TypeName est de type. AssemblyQualifiedName de la classe.</span><span class="sxs-lookup"><span data-stu-id="46b5f-125">Install the adapter in the global assembly cache and specify just *TypeName where \*TypeName is type.AssemblyQualifiedName of the class.</span></span> <span data-ttu-id="46b5f-126">Il s'agit de l'option recommandée.</span><span class="sxs-lookup"><span data-stu-id="46b5f-126">This is the recommended option.</span></span>  
  
 <span data-ttu-id="46b5f-127">Tous les adaptateurs doivent avoir les clés de Registre suivantes avec le GUID spécifié :</span><span class="sxs-lookup"><span data-stu-id="46b5f-127">All adapters must have the following registry keys with the specified GUID:</span></span>  
  
-   <span data-ttu-id="46b5f-128">**Implémentation des catégories\\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}**</span><span class="sxs-lookup"><span data-stu-id="46b5f-128">**Implemented Categories\\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}**</span></span>  
  
-   <span data-ttu-id="46b5f-129">**« InboundProtocol_PageProv » = « {2DE93EE6-CB01-4007-93E9-C3D71689A281} »**</span><span class="sxs-lookup"><span data-stu-id="46b5f-129">**"InboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A281}"**</span></span>  
  
-   <span data-ttu-id="46b5f-130">**« OutboundProtocol_PageProv » = « {2DE93EE6-CB01-4007-93E9-C3D71689A283} »**</span><span class="sxs-lookup"><span data-stu-id="46b5f-130">**"OutboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A283}"**</span></span>  
  
-   <span data-ttu-id="46b5f-131">**« ReceiveLocation_PageProv » = « {2DE93EE6-CB01-4007-93E9-C3D71689A280} »**</span><span class="sxs-lookup"><span data-stu-id="46b5f-131">**"ReceiveLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A280}"**</span></span>  
  
-   <span data-ttu-id="46b5f-132">**« TransmitLocation_PageProv » = « {2DE93EE6-CB01-4007-93E9-C3D71689A282} »**</span><span class="sxs-lookup"><span data-stu-id="46b5f-132">**"TransmitLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A282}"**</span></span>  
  
 <span data-ttu-id="46b5f-133">Les adaptateurs basés sur la structure d'adaptateur doivent utiliser ces GUID spécifiques pour le gestionnaire d'envoi et de réception et les pages de propriétés de l'emplacement.</span><span class="sxs-lookup"><span data-stu-id="46b5f-133">Adapters based on the adapter framework must use these specific GUIDS for send and receive handler and location property pages.</span></span> <span data-ttu-id="46b5f-134">Notez que si un adaptateur est un adaptateur d’envoi uniquement il a juste besoin le **OutboundProtocol_PageProv**et **TransmitLocation_PageProv**GUID.</span><span class="sxs-lookup"><span data-stu-id="46b5f-134">Note that if an adapter is a send-only adapter it just needs the **OutboundProtocol_PageProv**and **TransmitLocation_PageProv**GUIDs.</span></span> <span data-ttu-id="46b5f-135">De même qu’un adaptateur de réception uniquement nécessite simplement la **InboundProtocol_PageProv** et **ReceiveLocation_PageProv** GUID.</span><span class="sxs-lookup"><span data-stu-id="46b5f-135">Similarly a receive-only adapter merely requires the **InboundProtocol_PageProv** and **ReceiveLocation_PageProv** GUIDs.</span></span>  
  
 <span data-ttu-id="46b5f-136">Le code suivant est issu du fichier StaticAdapterManagement.reg et le code correspondant au fichier DynamicAdapterManagement.reg est quasiment identique.</span><span class="sxs-lookup"><span data-stu-id="46b5f-136">The following code is from the StaticAdapterManagement.reg file, and the code for the DynamicAdapterManagement.reg file is almost identical.</span></span> <span data-ttu-id="46b5f-137">Pour plus d’informations sur chacune des propriétés du Registre, consultez [inscription d’un adaptateur](../core/registering-an-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="46b5f-137">For more information about each of the registry properties, see [Registering an Adapter](../core/registering-an-adapter.md).</span></span> <span data-ttu-id="46b5f-138">Après avoir apporté les modifications nécessaires au fichier de Registre, enregistrez le fichier et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="46b5f-138">After making the changes to the registry file, save the file and run it.</span></span>  
  
```  
Windows Registry Editor Version 5.00  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}]  
@="Static DotNetFile Adapter"  
"AppID"="{12A6EBAA-CF68-4B58-B36E-A5A19B22C04E}"  
  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\BizTalk]  
@="BizTalk"  
"TransportType"="Static DotNetFile"  
"Constraints"=dword:00003C0b  
  
"InboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A281}"  
"OutboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A283}"  
"ReceiveLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A280}"  
"TransmitLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A282}"  
  
"InboundEngineCLSID"="{3D4B599E-2202-4bbb-9FC6-7ACA3906E5DE}"  
"InboundTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.DotNetFileReceiver""InboundAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Runtime\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Runtime.dll"  
"OutboundEngineCLSID"="{024DB758-AAF9-415e-A121-4AC245DD49EC}"  
"OutboundTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.DotNetFileTransmitter""OutboundAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Runtime\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Runtime.dll""AdapterMgmtTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.Designtime.StaticAdapterManagement""AdapterMgmtAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Design Time\\Adapter Management\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Designtime.dll""PropertyNameSpace"="http://schemas.microsoft.com/BizTalk/2003/SDK_Samples/Messaging/Transports/dotnetfile-properties"  
"AliasesXML"="<AdapterAliasList><AdapterAlias>DotNetFILE://</AdapterAlias></AdapterAliasList>"  
"ReceiveHandlerPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"SendHandlerPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"ReceiveLocationPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"SendLocationPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\Implemented Categories]  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\Implemented Categories\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}]  
```  
  
### <a name="to-register-the-static-sample-adapter"></a><span data-ttu-id="46b5f-139">Pour enregistrer l'exemple d'adaptateur statique</span><span class="sxs-lookup"><span data-stu-id="46b5f-139">To register the static sample adapter</span></span>  
  
1.  <span data-ttu-id="46b5f-140">Effectuez la procédure pour exécuter l'exemple d'adaptateur de fichier dans le SDK.</span><span class="sxs-lookup"><span data-stu-id="46b5f-140">Complete the procedure to run the file adapter sample in the SDK.</span></span> <span data-ttu-id="46b5f-141">Pour plus d’informations, consultez [l’adaptateur File (exemple BizTalk Server)](../core/file-adapter-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="46b5f-141">For more information, see [File Adapter (BizTalk Server Sample)](../core/file-adapter-biztalk-server-sample.md).</span></span>  
  
2.  <span data-ttu-id="46b5f-142">Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**, puis cliquez sur **Explorateur Windows**.</span><span class="sxs-lookup"><span data-stu-id="46b5f-142">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
3.  <span data-ttu-id="46b5f-143">Accédez au lecteur d’installation de BizTalk Server, puis accédez à  **<**  `drive` **> : \Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\SDK\Samples L’adaptateur \AdaptersUsage\File**.</span><span class="sxs-lookup"><span data-stu-id="46b5f-143">Navigate to the installation drive for BizTalk Server, and then navigate to **<**`drive`**>:\Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**\SDK\Samples\AdaptersUsage\File Adapter**.</span></span>  
  
4.  <span data-ttu-id="46b5f-144">Pour ajouter l’exemple d’adaptateur au Registre, double-cliquez sur **StaticAdapterManagement.reg**. (Si vous souhaitez ajouter l’adaptateur de fichier dynamique au Registre, exécutez **DynamicAdapterManagement.reg** à la place et utiliser ce fichier si nécessaire.)</span><span class="sxs-lookup"><span data-stu-id="46b5f-144">To add the sample adapter to the registry, double-click **StaticAdapterManagement.reg**. (If you want to add the dynamic file adapter to the registry run **DynamicAdapterManagement.reg** instead and use that file everywhere else as appropriate.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="46b5f-145">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'est pas installé sur le lecteur C de votre ordinateur, vous devez modifier le fichier StaticAdapterManagement.reg pour indiquer le chemin d'installation approprié.</span><span class="sxs-lookup"><span data-stu-id="46b5f-145">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is not installed on drive C of your computer, you must modify the StaticAdapterManagement.reg file with the appropriate installation path.</span></span> <span data-ttu-id="46b5f-146">Recherchez le fichier C: et remplacez-le par le lecteur d’installation correct.</span><span class="sxs-lookup"><span data-stu-id="46b5f-146">Search the file for C: and replace it with the correct installation drive.</span></span>  
  
5.  <span data-ttu-id="46b5f-147">Dans le **Éditeur du Registre** boîte de dialogue, cliquez sur **Oui** à ajouter l’exemple d’adaptateur au Registre, puis cliquez sur **OK** pour fermer la boîte de dialogue, vérifier que les informations ont été ajouté au Registre.</span><span class="sxs-lookup"><span data-stu-id="46b5f-147">In the **Registry Editor** dialog box, click **Yes** to add the sample adapter to the registry, and then click **OK** to close the dialog box, verifying that the information was added to the registry.</span></span>  
  
6.  <span data-ttu-id="46b5f-148">Pour fermer l’Explorateur Windows, dans le **fichier** menu, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="46b5f-148">To close Windows Explorer, on the **File** menu, click **Close**.</span></span>  
  
     <span data-ttu-id="46b5f-149">L'adaptateur statique exemple est désormais inscrit auprès de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46b5f-149">The sample static adapter is now registered with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>