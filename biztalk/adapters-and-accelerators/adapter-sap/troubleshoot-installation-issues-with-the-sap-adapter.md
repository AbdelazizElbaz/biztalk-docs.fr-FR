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
ms.openlocfilehash: cf06cc866249e929c9ddf368f4594af58af1d6fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-installation-issues-with-the-sap-adapter"></a>Résoudre les problèmes d’Installation avec l’adaptateur SAP
Installation de Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copie les fichiers binaires du produit sur l’ordinateur et enregistre les liaisons pour chaque carte. Cette section décrit les techniques de dépannage pour résoudre les erreurs d’installation.  
  
## <a name="logging-messages-for-setup-actions"></a>Messages de journalisation pour les Actions d’installation  
 Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation effectue la tâche standard de l’installation du [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. En outre, le programme d’installation effectue également certaines actions personnalisées, telles que l’inscription des liaisons de l’adaptateur. Vous pouvez enregistrer les messages pour les deux les actions standards, ainsi que personnalisés que le programme d’installation exécute.  
  
-   Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation installe les fichiers spécifiques de l’adaptateur à l’aide d’un fichier MSI. Par conséquent, la journalisation pour le programme d’installation est l’enregistrement du fichier MSI standard.  
  
-   Journaux pour le programme d’installation effectue les actions personnalisées sont disponibles à % TEMP%\adaptersetup.log. Si le suivi dans le fichier journal échoue, les traces sont également disponibles dans le journal des événements.  
  
##  <a name="BKMK_SAPSetupBinding"></a>Le programme d’installation ne parvient pas à inscrire des liaisons de l’adaptateur ou des fournisseurs de données  
 **Problème**  
  
 Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant installation ne parvient pas à inscrire des liaisons de l’adaptateur ou [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], mais poursuit l’installation de l’adaptateur.  
  
 **Cause**  
  
 Cela peut entraîner des problèmes dans [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation ou dans le fichier machine.config est endommagé. Liaisons de l’adaptateur sont écrites dans le fichier machine.config.  
  
 **Résolution**  
  
 Vous devez inscrire manuellement le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] liaison ou le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
### <a name="register-the-adapter-bindings-or-the-data-provider"></a>Inscrire des liaisons de l’adaptateur ou le fournisseur de données  
  
1.  Accédez au fichier machine.config sur l’ordinateur. Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système > : \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.  
  
     Dans ce chemin d’accès, \<version > correspond à la version du .NET Framework.  
  
2.  Ouvrez le fichier à l’aide d’un éditeur de texte.  
  
3.  Pour inscrire le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] liaison :  
  
    1.  Recherchez l’élément « system.serviceModel » et ajoutez le code suivant dans cette section :  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
        </client>  
        ```  
  
    2.  Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.  
  
    3.  Recherchez manquants [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] liaison. Ajoutez la section suivante sous le nœud « bindingElementExtensions ».  
  
         Pour [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], ajoutez :  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.  
  
    5.  Recherchez manquants [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] liaison. Ajoutez la section suivante sous le nœud « bindingExtensions ».  
  
         Pour [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], ajoutez :  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
        > [!NOTE]
        >  Pour plus d’informations sur la façon de déterminer la clé publique, consultez [détermination de la clé publique et la Version](#BKMK_PubKey).  
  
4.  Pour inscrire le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:  
  
    1.  Recherchez l’élément « DbProviderFactories » sous le nœud « system.data ».  
  
    2.  Recherchez manquants [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]. Ajoutez la section suivante sous le nœud « DbProviderFactories ».  
  
         Pour [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], ajoutez :  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient" description=".NET Framework Data Provider for mySAP Business Suite" type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  Enregistrez et fermez le fichier machine.config.  
  
###  <a name="BKMK_PubKey"></a>Détermination de la clé publique et la Version  
 Les étapes suivantes pour déterminer la clé publique pour [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ou [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
1.  Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.  
  
2.  Avec le bouton droit de la DLL pour laquelle vous souhaitez que la clé publique, puis sélectionnez **propriétés**. Le tableau suivant répertorie le nom des DLL pour [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
    |Fournisseur de données/carte|Nom de la DLL|  
    |----------------------------|---------------------|  
    |[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]|Microsoft.Adapters.SAP|  
    |[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]|Microsoft.Data.SAPClient|  
  
3.  Sur le **général** onglet, la valeur par rapport à la **jeton de clé publique** étiquette spécifie la clé publique pour la DLL. De même, la valeur par rapport à la **Version** étiquette Spécifie le numéro de version de la DLL.  
  
4.  Copiez la clé publique, puis cliquez sur **Annuler**.  
  
##  <a name="BKMK_SAPConsumeBinding"></a>Aucune carte valides n’est erreur installés

 **Problème**  
  
 À l’aide de la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] sur un ordinateur 64 bits exécutant la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] entraîne l’erreur suivante :  
  
```  
No valid adapters are installed on this machine  
```  
  
 **Cause**  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config. Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits. Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config. Toutefois, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] s’exécute comme un processus 32 bits et par conséquent, lorsque vous lancez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], le plug-in vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.  
  
 **Résolution**  
  
-   Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.  
  
    > [!IMPORTANT]
    >  Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.  
  
-   Ajoutez les versions 32 bits et 64 bits des DLL du client pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] (par exemple, librfc32u.dll) à la variable de chemin d’accès. La version 32 bits des DLL doit être ajoutée au dossier de C:\Windows\SysWow64. La version 64 bits des DLL doit être ajoutée au dossier C:\Windows\System32.  
  
    > [!IMPORTANT]
    >  Si l’adaptateur (32 ou 64 bits) est en cours d’exécution sur un ordinateur qui possède un système d’exploitation de 64 bits, et que vous écrivez une application à l’aide de l’adaptateur, vous devez marquer l’application vers le même type (32 ou 64 bits) en tant que l’adaptateur. En outre, la version du SDK RFC (32 ou 64 bits) doit être identique à la version de l’adaptateur (32 ou 64 bits).  
    >   
    >  Par exemple, si un adaptateur 32 bits s’exécute sur un ordinateur avec un système d’exploitation de 64 bits, l’application cliente de carte doit être marquée comme 32 bits.  
  
     Pour plus d’informations sur la DLL du client SAP, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).  
  
##  <a name="BKMK_SAPInvalidBinding"></a>Erreur de liaison non valide lors de la configuration des ports d’adaptateur SAP  
 **Problème**  
  
 Lorsque vous essayez de configurer un port de l’adaptateur dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous obtenez l’erreur suivante :  
  
```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "sapBinding".  
Verify the binding extension is registered in machine.config."  
```  
  
 **Cause**  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config. Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits. Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config. Toutefois, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration s’exécute comme un processus 32 bits et par conséquent, lorsque vous configurez un port de l’adaptateur, il vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.  
  
 **Résolution**  
  
-   Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.  
  
    > [!IMPORTANT]
    >  Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.  
  
-   Ajoutez les versions 32 bits et 64 bits des DLL du client pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] (par exemple, librfc32u.dll) à la variable de chemin d’accès. La version 32 bits des DLL doit être ajoutée au dossier de C:\Windows\SysWow64. La version 64 bits des DLL doit être ajoutée au dossier C:\Windows\System32.  
  
    > [!IMPORTANT]
    >  Si l’adaptateur (32 ou 64 bits) est en cours d’exécution sur un ordinateur qui possède un système d’exploitation de 64 bits, et que vous écrivez une application à l’aide de l’adaptateur, vous devez marquer l’application vers le même type (32 ou 64 bits) en tant que l’adaptateur. En outre, la version du SDK RFC (32 ou 64 bits) doit être identique à la version de l’adaptateur (32 ou 64 bits).  
    >   
    >  Par exemple, si un adaptateur 32 bits s’exécute sur un ordinateur avec un système d’exploitation de 64 bits, l’application cliente de carte doit être marquée comme 32 bits.  
  
     Pour plus d’informations sur la DLL du client SAP, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).
  
## <a name="see-also"></a>Voir aussi  
[Résoudre les problèmes de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)