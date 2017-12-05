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
ms.openlocfilehash: 0dc2603a2e86d29797919fb51c3985c384ff9580
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-installation-issues-with-the-oracle-database-adapter"></a>Résoudre les problèmes d’installation de l’adaptateur de base de données Oracle
Installation de Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copie les fichiers binaires du produit sur l’ordinateur et enregistre les liaisons pour chaque carte. Cette section présente l’utilisation de techniques de dépannage pour résoudre les erreurs d’installation et répertorie certains problèmes connus.  
  
## <a name="logging-messages-for-setup-actions"></a>Messages de journalisation pour les Actions d’installation  
 Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation effectue la tâche standard de l’installation du [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. En outre, le programme d’installation effectue également certaines actions personnalisées, telles que l’inscription des liaisons de l’adaptateur. Vous pouvez enregistrer les messages pour les deux les actions standards, ainsi que personnalisés que le programme d’installation exécute.  
  
-   Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation installe les fichiers spécifiques à l’adaptateur à l’aide d’un fichier MSI. Par conséquent, la journalisation pour le programme d’installation est l’enregistrement du fichier MSI standard. 
  
-   Tous les journaux pour le programme d’installation effectue les actions personnalisées sont disponibles à % TEMP%\adaptersetup.log. Si le suivi dans le fichier journal échoue, les traces sont également disponibles dans le journal des événements.  
  
##  <a name="BKMK_OraDBBinding"></a>Le programme d’installation ne parvient pas à inscrire des liaisons de l’adaptateur  
 **Problème**  
  
 Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant installation ne parvient pas à inscrire des liaisons de l’adaptateur, mais poursuit l’installation de l’adaptateur.  
  
 **Cause**  
  
 Cela peut entraîner des problèmes dans [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation ou dans le fichier machine.config est endommagé. Liaisons de l’adaptateur sont écrites dans le fichier machine.config.  
  
 **Résolution**  
  
Inscrire manuellement le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] liaison : 
  
1.  Accédez au fichier machine.config sur l’ordinateur. Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.  
  
     Dans ce chemin d’accès, \<version\> est la version du .NET Framework.  
  
2.  Ouvrez le fichier à l’aide d’un éditeur de texte.  
  
3.  Pour inscrire le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] liaison :  
  
    1.  Recherchez l’élément « system.serviceModel » et ajoutez le code suivant dans cette section :  
  
        ```  
        <client>  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
        </client>  
        ```  
  
    2.  Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.  
  
    3.  Recherchez manquants [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] liaison. Ajoutez la section suivante sous le nœud « bindingElementExtensions ».  
  
         Pour [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], ajoutez :  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.  
  
    5.  Recherchez manquants [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] liaison. Ajoutez la section suivante sous le nœud « bindingExtensions ».  
  
         Pour [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], ajoutez :  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  Pour plus d’informations sur la façon de déterminer la clé publique et la version, consultez [détermination de la clé publique et la Version](#BKMK_PubKey).  
  
4.  Enregistrez et fermez le fichier machine.config.  
  
####  <a name="BKMK_PubKey"></a>Détermination de la clé publique et la Version  
 Les étapes suivantes pour déterminer la clé publique pour [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
1.  Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.  
  
2.  Avec le bouton droit de la DLL pour laquelle vous souhaitez que la clé publique et la version, puis sélectionnez **propriétés**. Le tableau suivant répertorie le nom de la DLL pour [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
    |Adaptateur|Nom de la DLL|  
    |-------------|---------------------|  
    |[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]|Microsoft.Adapters.OracleDB|  
  
3.  Sur le **général** onglet, la valeur par rapport à la **jeton de clé publique** étiquette spécifie la clé publique pour la DLL. De même, la valeur par rapport à la **Version** étiquette Spécifie le numéro de version de la DLL.  
  
4.  Copiez la clé publique, puis cliquez sur **Annuler**.  
  
##  <a name="BKMK_ConsumeBinding"></a>Erreur lors de l’utilisation du complément Consume Adapter Service ou l’ajouter Adapter Service Reference plug-in sur une installation 64 bits  
 **Problème**  
  
 À l’aide de la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] sur un ordinateur 64 bits exécutant la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] entraîne l’erreur suivante :  
  
```  
No valid adapters are installed on this machine  
```  
  
 **Cause**  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config. Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits. Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config. Toutefois, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] s’exécute comme un processus 32 bits et par conséquent, lorsque vous lancez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], le plug-in vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.  
  
 **Résolution**  
  
-   Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.  
  
    > [!IMPORTANT]
    >  Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.  
  
-   Installez les versions 32 bits et 64 bits d’Oracle Data Access Components pour Client Oracle 11.1.0.6 avec le jeu de correctifs 11.1.0.7.  
  
    > [!NOTE]
    >  Pour vous assurer que votre application fonctionne avec la version la plus récente de ODP.NET, vous devez avoir « Stratégie dll » installé sur l’ordinateur et enregistré dans le GAC. Pour plus d’informations, consultez [le fournisseur de données Oracle pour .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) sur le site Web d’Oracle.  
  
##  <a name="BKMK_InvalidBinding"></a>Erreur de liaison non valide lors de la configuration des ports de carte de base de données Oracle dans la Console Administration de BizTalk Server sur une installation 64 bits  
 **Problème**  
  
 Lorsque vous essayez de configurer un port de l’adaptateur dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous obtenez l’erreur suivante :  
  
```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "oracleDBBinding".  
Verify the binding extension is registered in machine.config."  
```  
  
 **Cause**  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est une liaison WCF personnalisée, qui est enregistrée sous System.ServiceModel dans le fichier machine.config. Une plateforme 64 bits comprend les fichiers machine.config deux un utilisés par les applications 32 bits et l’autre est utilisé par les applications 64 bits. Par conséquent, lorsque vous installez la version 64 bits de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], l’Assistant d’installation enregistre les liaisons dans la version 64 bits du fichier machine.config. Toutefois, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration s’exécute comme un processus 32 bits et par conséquent, lorsque vous configurez un port de l’adaptateur, il vérifie les liaisons dans la version 32 bits du fichier machine.config et échoue et affiche une erreur.  
  
 **Résolution**  
  
-   Installez les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sur une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.  
  
    > [!IMPORTANT]
    >  Vous devez disposer uniquement une version 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Installation côte à côte de 32 bits et 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un seul ordinateur n’est pas pris en charge.  
  
-   Installez les versions 32 bits et 64 bits d’Oracle Data Access Components pour Client Oracle 11.1.0.6 avec le jeu de correctifs 11.1.0.7.  
  
    > [!NOTE]
    >  Pour vous assurer que votre application fonctionne avec la version la plus récente de ODP.NET, vous devez avoir « Stratégie dll » installé sur l’ordinateur et enregistré dans le GAC. Pour plus d’informations, consultez [le fournisseur de données Oracle pour .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) sur le site Web d’Oracle. 
  
## <a name="see-also"></a>Voir aussi  
[Dépanner l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)