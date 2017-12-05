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
# <a name="adapter-registration-file"></a>Fichier d'inscription de l'adaptateur
Une fois le code de l'adaptateur personnalisé correctement généré, il doit être inscrit auprès de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour ce faire, il convient de mettre à jour le Registre à l'aide des paramètres appropriés de l'adaptateur. Vous pouvez écrire manuellement un fichier de Registre, mais il y a un risque d'erreurs en raison de la précision et de la complexité des informations que vous devrez entrer. Il est conseillé d'exécuter l'Assistant Registre d'adaptateur. Cet Assistant vous propose les mêmes options que si vous génériez un fichier de Registre en partant de zéro et il réduit le risque d'erreurs dans le fichier. Pour plus d’informations sur cet Assistant, consultez [Assistant Registre d’adaptateur](../core/adapter-registry-wizard.md).  
  
 Le fichier StaticAdapterManagement.reg et DynamicAdapterManagement.reg sont trouvent dans  *\<lecteur\>*: \Program Files\Microsoft Server\SDK\Samples\AdaptersDevelopment\File l’adaptateur BizTalk. Lorsque vous exécutez un de ces fichiers (vous pouvez double-cliquer dessus ou faites un clic droit et sélectionnez **fusion**), il inscrit l’exemple d’adaptateur file dans le Registre et installe l’assembly dans le global assembly cache. Pour enregistrer votre adaptateur personnalisé, la meilleure méthode consiste à créer un fichier de Registre en utilisant l'Assistant Registre d'adaptateur. Si votre adaptateur statique personnalisé est identique à l'adaptateur exemple, et que vous décidiez à la place de modifier le fichier de Registre existant, ouvrez le fichier StaticAdapterManagement.reg et modifiez les propriétés suivantes :  
  
-   **Contraintes**  
  
-   **InboundTypeName**  
  
-   **InboundAssemblyPath**  
  
-   **OutboundTypeName**  
  
-   **OutboundAssemblyPath**  
  
-   **AdapterMgmtTypeName**  
  
-   **AdapterMgmtAssemblyPath**  
  
-   **PropertyNameSpace**  
  
> [!NOTE]
>  Pour **OutboundAssemblyPath** et **AdapterMgmtAssemblyPath** nous recommandons que vous n'incluez pas le chemin d’accès local dans la valeur de propriété, car la configuration pourrait échouer lors de l’installation sur différents emplacements du serveur. Il vaut mieux utiliser un nom fort et l'installer dans le GAC (Global Assembly Cache).  
  
 Vous avez deux possibilités pour spécifier le type .NET implémentant le récepteur de l'adaptateur, l'émetteur de l'adaptateur et la gestion de l'adaptateur :  
  
1.  Installez la carte dans un dossier et spécifiez * TypeName et \*AssemblyPath où \*TypeName est de type. Nom complet de la classe et \*AssemblyPath est le chemin d’accès et le nom de l’assembly.  
  
2.  Installez l’adaptateur dans le global assembly cache et spécifiez uniquement * TypeName où \*TypeName est de type. AssemblyQualifiedName de la classe. Il s'agit de l'option recommandée.  
  
 Tous les adaptateurs doivent avoir les clés de Registre suivantes avec le GUID spécifié :  
  
-   **Implémentation des catégories\\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}**  
  
-   **« InboundProtocol_PageProv » = « {2DE93EE6-CB01-4007-93E9-C3D71689A281} »**  
  
-   **« OutboundProtocol_PageProv » = « {2DE93EE6-CB01-4007-93E9-C3D71689A283} »**  
  
-   **« ReceiveLocation_PageProv » = « {2DE93EE6-CB01-4007-93E9-C3D71689A280} »**  
  
-   **« TransmitLocation_PageProv » = « {2DE93EE6-CB01-4007-93E9-C3D71689A282} »**  
  
 Les adaptateurs basés sur la structure d'adaptateur doivent utiliser ces GUID spécifiques pour le gestionnaire d'envoi et de réception et les pages de propriétés de l'emplacement. Notez que si un adaptateur est un adaptateur d’envoi uniquement il a juste besoin le **OutboundProtocol_PageProv**et **TransmitLocation_PageProv**GUID. De même qu’un adaptateur de réception uniquement nécessite simplement la **InboundProtocol_PageProv** et **ReceiveLocation_PageProv** GUID.  
  
 Le code suivant est issu du fichier StaticAdapterManagement.reg et le code correspondant au fichier DynamicAdapterManagement.reg est quasiment identique. Pour plus d’informations sur chacune des propriétés du Registre, consultez [inscription d’un adaptateur](../core/registering-an-adapter.md). Après avoir apporté les modifications nécessaires au fichier de Registre, enregistrez le fichier et exécutez-le.  
  
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
  
### <a name="to-register-the-static-sample-adapter"></a>Pour enregistrer l'exemple d'adaptateur statique  
  
1.  Effectuez la procédure pour exécuter l'exemple d'adaptateur de fichier dans le SDK. Pour plus d’informations, consultez [l’adaptateur File (exemple BizTalk Server)](../core/file-adapter-biztalk-server-sample.md).  
  
2.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**, puis cliquez sur **Explorateur Windows**.  
  
3.  Accédez au lecteur d’installation de BizTalk Server, puis accédez à  **<**  `drive` **> : \Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\SDK\Samples L’adaptateur \AdaptersUsage\File**.  
  
4.  Pour ajouter l’exemple d’adaptateur au Registre, double-cliquez sur **StaticAdapterManagement.reg**. (Si vous souhaitez ajouter l’adaptateur de fichier dynamique au Registre, exécutez **DynamicAdapterManagement.reg** à la place et utiliser ce fichier si nécessaire.)  
  
    > [!NOTE]
    >  Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'est pas installé sur le lecteur C de votre ordinateur, vous devez modifier le fichier StaticAdapterManagement.reg pour indiquer le chemin d'installation approprié. Recherchez le fichier C: et remplacez-le par le lecteur d’installation correct.  
  
5.  Dans le **Éditeur du Registre** boîte de dialogue, cliquez sur **Oui** à ajouter l’exemple d’adaptateur au Registre, puis cliquez sur **OK** pour fermer la boîte de dialogue, vérifier que les informations ont été ajouté au Registre.  
  
6.  Pour fermer l’Explorateur Windows, dans le **fichier** menu, cliquez sur **fermer**.  
  
     L'adaptateur statique exemple est désormais inscrit auprès de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].