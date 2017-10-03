---
title: "Mettre à jour ou désinstaller le 2016 de pack d’adaptateur BizTalk | Documents Microsoft"
description: "Utilisez l’Assistant Installation ou msiexec pour modifier ou désinstaller 2016 BAP inclus dans BizTalk Server ; y compris de supprimer les liaisons et de supprimer les RFC personnalisés"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3d6c001-1005-4d7b-a143-eaa37b48f898
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51c30fa3b107113991a8b4893fa2626a53d67159
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-or-uninstall-the-biztalk-adapter-pack-2016"></a>Mettre à jour ou désinstaller le 2016 de pack d’adaptateur BizTalk
Comment modifier ou désinstaller le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].

<a name="BKMK_Modify_Adap"></a>
## <a name="change-or-update-the-installation"></a>Modifier ou mettre à jour de l’installation  
Avant d’exécuter l’Assistant Installation pour modifier le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, assurez-vous que le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] est installé. 
  
 Vous pouvez modifier l’installation en mode interactif (l’Assistant d’installation), ou en mode silencieux (la ligne de commande).
  
### <a name="use-the-setup-wizard"></a>Utilisez l’Assistant Installation  
  
1.  Connectez-vous avec un compte qui est membre du groupe Administrateurs de BizTalk Server.  
  
2.  Dans **programmes et fonctionnalités**, sélectionnez **désinstaller un programme**.  
  
3.  Avec le bouton droit **Microsoft BizTalk Adapter Pack**, puis sélectionnez **modification**.  
  
4.  Dans l’écran de bienvenue, sélectionnez **suivant**.  
  
5.  Dans **modifier, réparer ou supprimer l’installation**:  
  
    -   Pour sélectionner les composants à installer, sélectionnez **modification** et accédez à l’étape 6.  
  
    -   Pour réparer les erreurs dans l’installation la plus récente, sélectionnez **réparer** et accédez à l’étape 7.  
  
    -   Pour supprimer la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] à partir de l’ordinateur, sélectionnez **supprimer** et passez à l’étape 10.  
  
6.  Si vous avez choisi de modifier l’installation :  
  
    -   Développez le **Microsoft BizTalk Adapter Pack** nœud de choisir d’installer les adaptateurs de base, les fournisseurs de données .NET Framework ou les deux.  
  
    -   Développez le **Base cartes** nœud de choisir d’installer toutes les cartes ou des cartes spécifiques.  
  
    -   Développez le **ADO fournisseurs** nœud de choisir d’installer tous les fournisseurs ou des fournisseurs spécifiques.  
  
    -   Sélectionnez **Suivant**.  
  
    -   Sélectionnez **modification**, puis sélectionnez **Terminer**.  
  
7.  Si vous avez choisi réparer l’installation, dans le **prêt à réparer Microsoft BizTalk Adapter Pack** boîte de dialogue, sélectionnez **réparer**. L’Assistant démarre la réparation de l’installation.  
  
8.  Si nécessaire, modifiez vos préférences concernant le choix d’amélioration du produit, puis sélectionnez **OK**. 
  
9. Sélectionnez **Terminer**.  
  
10. Si vous avez choisi de supprimer les adaptateurs, dans le **prêt à supprimer de Microsoft BizTalk Adapter Pack** boîte de dialogue, sélectionnez **supprimer**, puis sélectionnez **Terminer**.  
  
### <a name="use-msiexec-in-silent-mode"></a>Utiliser msiexec en mode silencieux  
  
1.  Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] programme d’installation.  
  
2.  Exécutez une commande semblable à la suivante :  
  
    > [!NOTE]
    >  Pour modifier la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation en mode sans assistance sur une plateforme x64 64, les commandes suivantes, remplacez `AdaptersSetup.msi` avec `AdaptersSetup64.msi`.  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature ADDLOCAL=SapBaseAdapterFeature  
    ```  
  
     Cette commande supprime le [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]et installe le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].  
  
     À l’aide des valeurs différentes pour le `REMOVE` et `ADDLOCAL` propriétés, vous pouvez ajouter ou supprimer des composants spécifiques. Reportez-vous au tableau dans **installer en mode silencieux** à [BAP d’installation](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md) pour plus d’informations sur les valeurs que vous pouvez utiliser pour ces propriétés.  
  
     Vous pourrez également effectuer une réparation en mode silencieux à l’aide de l’option /f dans le cadre de la commande msiexec. Exemple :  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn /f  
    ```  
  
     Vous pouvez utiliser diverses combinaisons avec l’option /f. Pour plus d’informations sur le type de commande msiexec `msiexec` sur la ligne de commande, puis appuyez sur `ENTER`. Ou accédez à [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).  
  
    > [!IMPORTANT]
    >  Lors de la modification du [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation en mode silencieux, vous ne pouvez pas modifier vos préférences pour vous inscrire ou de refuser le CEIP. Les préférences de que celle choisie lors de l’installation reste, même si vous définissez explicitement la CEIP_OPTIN à true ou false.  

## <a name="uninstall-or-remove-the-biztalk-adapter-pack"></a>Désinstaller ou supprimer le Pack d’adaptateurs BizTalk  
  
> [!IMPORTANT]
>  Si vous avez créé des tables dans la base de données SQL Server pour travailler avec la fonctionnalité tRFC de la [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], vous devez les supprimer manuellement avant de désinstaller le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] d’installation copie un `SapAdapter-DbScript-Uninstall.sql` de fichiers en général au  *\<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]* . Exécuter ce fichier pour supprimer les tables que vous avez créé.  
  
Effectuez les étapes suivantes pour supprimer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] à partir de votre ordinateur. Assurez-vous que vous avez le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] installé avant d’exécuter l’Assistant installation.  
  
 Vous pouvez supprimer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] en mode interactif (Assistant Installation), ou en mode silencieux (ligne de commande).
  
### <a name="uninstall-using-the-setup-wizard"></a>Désinstallation à l’aide de l’Assistant Installation  
  
1.  Dans **programmes et fonctionnalités**, sélectionnez **désinstaller un programme**.  
  
2.  Avec le bouton droit **Microsoft BizTalk Adapter Pack**, puis sélectionnez **désinstallation**.  
  
### <a name="uninstall-in-silent-mode"></a>Désinstaller en mode silencieux  
  
1.  Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] programme d’installation.  
  
2.  Exécutez la commande suivante :  
  
    > [!NOTE]
    >  Pour supprimer la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] en mode silencieux sur une plateforme x64 64, les commandes suivantes, remplacez `AdaptersSetup.msi` avec `AdaptersSetup64.msi`.  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature  
    ```  
  
     Cette commande supprime le [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)] à partir de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.  
  
     En fournissant des valeurs différentes pour le `REMOVE` propriété, vous pouvez supprimer des composants spécifiques à partir de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation. Reportez-vous au tableau dans **installer en mode silencieux** à [BAP d’installation](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md) pour plus d’informations sur les valeurs que vous pouvez utiliser pour cette propriété.  
  
     Pour supprimer complètement le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], exécutez la commande suivante :  
  
    ```  
    msiexec /x AdaptersSetup.msi /qn  
    ```  
  
     Pour plus d’informations sur le type de commande msiexec `msiexec` sur la ligne de commande, puis appuyez sur `ENTER`. Ou accédez à [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).
  
## <a name="remove-the-bindings"></a>Supprimer les liaisons  
 Effectuez ces étapes *uniquement* si l’Assistant installation ne parvient pas à supprimer les liaisons de l’adaptateur ou l’inscription du fournisseur de données .NET Framework à partir du fichier machine.config.  
  
1.  Accédez au fichier machine.config sur l’ordinateur. Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous  *\<lecteur système > : \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG*.  
  
2.  Ouvrez le fichier à l’aide d’un éditeur de texte.  
  
3.  Supprimer l’inscription de la liaison de la carte :  
  
    1.  Recherchez le `system.serviceModel` élément et supprimer les éléments suivants figurant dans l’élément :  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
          <endpoint binding="OracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
  
        ```  
  
    2.  Recherchez le `bindingElementExtensions` élément sous system.serviceModel\extensions.  
  
    3.  Supprimer les sections suivantes sous la `bindingElementExtensions` nœud, en fonction de la liaison d’adaptateur disponibles. Vous devez supprimer toutes les liaisons si l’Assistant installation ne parvient pas à supprimer.  
  
         Pour [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], supprimer :  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], supprimer :  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], supprimer :  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], supprimer :  
  
        ```  
        <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], supprimer :  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  Recherchez le `bindingExtensions` élément sous system.serviceModel\extensions.  
  
    5.  Supprimer les sections suivantes sous la `bindingExtensions` nœud, en fonction de la liaison d’adaptateur disponibles. Vous devez supprimer toutes les liaisons si l’Assistant installation ne parvient pas à supprimer.  
  
         Pour [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], supprimer :  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], supprimer :  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], supprimer :  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], supprimer :  
  
        ```  
        <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], supprimer :  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
4.  Supprimer l’inscription du fournisseur de données .NET Framework :  
  
    -   Recherchez le `DbProviderFactories` élément sous le nœud system.data.  
  
    -   Recherchez les fournisseurs de données .NET Framework qui sont toujours inscrits. Supprimer les sections suivantes sous la `DbProviderFactories` nœud, selon les fournisseurs de données .NET Framework existant. Vous devez supprimer tous les fournisseurs s’ils existent.  
  
         Pour [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], supprimer :  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
            description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], supprimer :  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  Enregistrez et fermez le fichier machine.config.  
  
## <a name="remove-the-custom-rfcs"></a>Supprimer les RFC personnalisés  
Effectuez cette étape pour supprimer les RFC personnalisés que vous avez installé dans le système SAP. Consultez [installer ou supprimer les RFC personnalisés](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).  
  
