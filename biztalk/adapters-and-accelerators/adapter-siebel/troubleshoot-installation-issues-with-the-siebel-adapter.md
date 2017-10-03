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
ms.openlocfilehash: 9b254f317740b8fcff0bc97dc0891ae19fb8d594
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-installation-issues-with-the-siebel-adapter"></a>Résoudre les problèmes d’Installation avec l’adaptateur Siebel
Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation copie les fichiers binaires du produit sur l’ordinateur et enregistre les liaisons pour chaque carte. Cette section décrit les techniques de dépannage pour résoudre les erreurs d’installation.  
  
## <a name="setup-logging"></a>Journalisation de l’installation  
 Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation effectue la tâche standard de l’installation du [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. En outre, le programme d’installation effectue également certaines actions personnalisées, telles que l’inscription des liaisons de l’adaptateur. Vous pouvez enregistrer les messages pour les actions standards, ainsi que personnalisées effectuées par le programme d’installation.  
  
-   Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation installe les fichiers spécifiques de l’adaptateur à l’aide d’un fichier MSI. Par conséquent, la journalisation pour le programme d’installation sera l’enregistrement du fichier MSI standard.  
  
-   Journaux pour les actions personnalisées effectuées par le programme d’installation sont disponibles dans % TEMP%\adaptersetup.log. Si le suivi dans le fichier journal échoue, les traces sont également disponibles dans le journal des événements.  
  
## <a name="known-issues"></a>Problèmes connus  
  
### <a name="setup-fails-to-register-adapter-bindings"></a>Le programme d’installation ne parvient pas à inscrire des liaisons de l’adaptateur  
 **Problème**  
  
 Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant installation ne parvient pas à inscrire le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] liaison ou le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], mais poursuit l’installation de l’adaptateur.  
  
 **Cause**  
  
 Cela peut entraîner des problèmes dans l’installation de WCF, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] l’installation ou le fichier machine.config est endommagé. Liaisons de l’adaptateur sont écrites dans le fichier machine.config.  
  
 **Résolution**  
  
Inscrire manuellement le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] liaison et [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] en procédant comme suit : 
  
1.  Accédez au fichier machine.config sur l’ordinateur. Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système > : \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.  
  
     Dans ce chemin d’accès, \<version > correspond à la version du .NET Framework.  
  
2.  Ouvrez le fichier à l’aide d’un éditeur de texte.  
  
3.  Pour inscrire le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] liaison :  
  
    1.  Recherchez l’élément « system.serviceModel » et ajoutez le code suivant dans cette section :  
  
        ```  
        <client>  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
        </client>  
        ```  
  
    2.  Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.  
  
    3.  Recherchez manquants [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] liaison. Ajoutez la section suivante sous le nœud « bindingElementExtensions ».  
  
         Pour [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], ajoutez :  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.  
  
    5.  Recherchez manquants [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] liaison. Ajoutez les sections suivantes sous le nœud « bindingExtensions ».  
  
         Pour [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], ajoutez :  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
        > [!NOTE]
        >  Pour plus d’informations sur la façon de déterminer la clé publique, consultez [détermination de la clé publique et la Version](#BKMK_PubKey).  
  
4.  Pour inscrire le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]:  
  
    1.  Recherchez l’élément DbProviderFactories sous le nœud system.data.  
  
    2.  Recherchez manquants [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]. Ajoutez la section suivante sous le nœud DbProviderFactories.  
  
         Pour [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], ajoutez :  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  Enregistrez et fermez le fichier machine.config.  
  
####  <a name="BKMK_PubKey"></a>Détermination de la clé publique et la Version  
 Les étapes suivantes pour déterminer la clé publique pour [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ou [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].  
  
###### <a name="to-determine-the-public-key"></a>Pour déterminer la clé publique  
  
1.  Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.  
  
2.  Avec le bouton droit de la DLL pour lesquels vous souhaitez public key et select **propriétés**. Le tableau suivant répertorie le nom des DLL pour chaque fournisseur et la carte.  
  
    |Fournisseur de carte/ADO|Nom de la DLL|  
    |---------------------------|---------------------|  
    |[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]|Microsoft.Adapters.Siebel|  
    |[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]|Microsoft.Data.SiebelClient|  
  
3.  Sur le **général** onglet, la valeur par rapport à la **jeton de clé publique** étiquette spécifie la clé publique pour la DLL. De même, la valeur par rapport à la **Version** étiquette Spécifie le numéro de version de la DLL.  
  
4.  Copiez la clé publique, puis cliquez sur **Annuler**.  
  
## <a name="see-also"></a>Voir aussi  
[Dépanner l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)