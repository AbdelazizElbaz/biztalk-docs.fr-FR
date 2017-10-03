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
ms.openlocfilehash: 33726ebafc3ed6b3d1ad62bf97019e30493a895e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="post-installation-steps-for-biztalk-adapter-pack-2016"></a>Valider les étapes d’installation de BizTalk adaptateur Pack 2016
Après avoir installé le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], quelques étapes consécutives à l’installation. Cette rubrique décrit ces étapes.   

## <a name="add-the-adapter-to-biztalk-administration"></a>Ajouter l’adaptateur à l’Administration de BizTalk
  
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Développez le **groupe BizTalk**, développez **paramètres de plateforme**, puis sélectionnez **cartes**.  
  
3.  Avec le bouton droit **cartes**, sélectionnez **nouveau**, puis sélectionnez **carte**.  
  
     ![Ajouter un adaptateur](../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")  
  
4.  Dans le **propriétés de l’adaptateur**, sélectionnez une carte dans la liste déroulante, telle que **WCF SAP**, puis entrez un nom, tel que **WCF SAP**.  
  
     ![Ajouter un adaptateur SAP à BizTalk](../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")  
  
5.  Sélectionnez **OK**.  

## <a name="use-a-newer-oracledataaccessdll-version"></a>Utilisez une version plus récente de Oracle.DataAccess.dll  

Lorsque vous configurez un port à utiliser l’adaptateur WCF-OracleDB ou utiliser Visual Studio pour consommer un adaptateur généré, un message s’affiche que l’adaptateur doit Oracle.DataAccess.dll version 2.111.7.0. Pour résoudre ce message, installez une version prise en charge de Oracle.DataAccess.dll (consultez [prise en charge de la liste des versions](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)), puis mettez à jour le `bindingRedirect` élément dans le fichier de configuration OracleDB en procédant comme suit :  
  
1.  Sur le serveur BizTalk Server, accédez aux dossiers suivants :  
  
     *lecteur*: \Program Files\Microsoft BizTalk Adapter Pack (x64) \bin  
  
     *lecteur*: \Program fichiers (x86) \Microsoft BizTalk Adapter Pack\bin  
  
2.  Ouvrez le fichier Microsoft.Adapters.OracleDB.config.  
  
3.  Recherchez la section suivante, puis copier/coller les éléments suivants :  
  
    ```  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
              <dependentAssembly>  
                        <assemblyIdentity name="Oracle.DataAccess" publicKeyToken="89b483f429c47342" culture="neutral" />  
                        <bindingRedirect oldVersion="2.111.7.00" newVersion="2.112.1.00"/>  
              </dependentAssembly>  
    </assemblyBinding>  
  
    ```  
  
    > [!NOTE]
    >  Dans cet exemple, nous avons défini *newVersion* à 2.112.1.00. Définissez cette valeur à la version que vous avez installé.  
  
> [!IMPORTANT]
> - S’il existe plusieurs serveurs BizTalk Server dans ce groupe, apporter cette modification sur tous les serveurs BizTalk du groupe.  
> - Le *newVersion* valeur doit être mis à jour en fonction de la version du fichier Oracle.DataAccess.dll installé sur l’ordinateur.  Oracle.DataAccess.dll est inclus avec le Client Oracle que vous installez à partir d’Oracle.  Vous devez installer uniquement une version de Client Oracle est [pris en charge par BizTalk Adapter Pack](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx).  
  
## <a name="create-sql-server-database-objects-sap-adapter-only"></a>Créer des objets de base de données SQL Server (adaptateur SAP uniquement)  
 Pour appeler tRFCs dans un système SAP, exécutez le *SapAdapter-DbScript-Install.sql* script SQL. Ce script est installé avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation et crée des objets de base de données dans SQL Server. Le script est généralement installé sur  *\<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]* . Vous pouvez exécuter ce script sur toute base de données SQL Server, tant que vous entrez son nom de base de données lors de l’utilisation de l’adaptateur pour appeler tRFCs.
  
## <a name="register-the-adapter-bindings"></a>Inscrire des liaisons de l’adaptateur
Lors de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, l’Assistant installation peut échouer enregistrer des liaisons de l’adaptateur ou le fournisseur de données .NET Framework pour mySAP Business Suite. Et le programme d’installation poursuit l’installation de l’adaptateur. Cela peut être dû à l’installation de Windows Communication Foundation (WCF), le [!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)] installation ou dans le fichier machine.config est endommagé.  

> [!IMPORTANT]
> Effectuez les étapes suivantes *uniquement* si l’Assistant installation ne parvient pas à inscrire des liaisons de l’adaptateur, les fournisseurs de données .NET Framework dans le fichier machine.config.  
  
1.  Accédez au fichier machine.config sur l’ordinateur. Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous  *\<lecteur système > : \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG*.  
  
2.  Ouvrez le fichier à l’aide d’un éditeur de texte.  
  
3.  Enregistrer des liaisons de l’adaptateur :  
  
    1.  Recherchez le `system.serviceModel` élément et ajoutez le code suivant dans cette section :  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
          <endpoint binding="oracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  Recherchez le `bindingElementExtensions` élément sous system.serviceModel\extensions.  
  
    3.  Recherchez la liaison de l’adaptateur manquant. Ajoutez les sections suivantes sous la `bindingElementExtensions` nœud, en fonction de la liaison de l’adaptateur manquant. Vous devez enregistrer toutes les liaisons si l’Assistant installation ne parvient pas à inscrire.  
  
         Pour le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], ajoutez :  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], ajoutez :  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour le [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], ajoutez :  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour le [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], ajoutez :  
  
        ```  
        <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour le [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], ajoutez :  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  Recherchez le `bindingExtensions` élément sous system.serviceModel\extensions.  
  
    5.  Recherchez la liaison de l’adaptateur manquant. Ajoutez les sections suivantes sous la `bindingExtensions` nœud, en fonction de la liaison de l’adaptateur manquant. Vous devez enregistrer toutes les liaisons si l’Assistant installation ne parvient pas à inscrire.  
  
         Pour [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], ajoutez :  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], ajoutez :  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], ajoutez :  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], ajoutez :  
  
        ```  
        <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS,Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], ajoutez :  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  Pour obtenir la valeur de clé publique, consultez **déterminer la clé publique et la version** (dans cette rubrique).  
  
4.  Inscrire les fournisseurs de données .NET Framework :  
  
    1.  Recherchez le `DbProviderFactories` élément sous le nœud system.data.  
  
    2.  Recherchez les fournisseurs de données .NET Framework manquante. Ajoutez les sections suivantes sous la `DbProviderFactories` nœud, en fonction du fournisseur manquant. Vous devez inscrire tous les fournisseurs de si l’Assistant installation ne parvient pas à inscrire.  
  
         Pour le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], ajoutez :  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
            description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         Pour le [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], ajoutez :  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  Enregistrez et fermez le fichier machine.config.  
  
## <a name="determine-the-public-key-and-version"></a>Déterminer la version et la clé publique  
 Effectuez les étapes suivantes pour déterminer la version d’un adaptateur ou le fournisseur de données .NET Framework et la clé publique.  
  
1.  Accédez au répertoire Windows, généralement *C:\WINDOWS\assembly*.  
  
2.  Avec le bouton droit de la DLL pour laquelle vous souhaitez que la clé publique, puis sélectionnez **propriétés**. Le tableau suivant répertorie le nom des DLL pour chaque fournisseur et la carte :  
  
    |Adaptateur/.NET Framework Data Provider|Nom de la DLL|  
    |---|---|  
    |[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]|Microsoft.Adapters.SAP|  
    |[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]|Microsoft.Adapters.Siebel|  
    |[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]|Microsoft.Adapters.OracleDB|  
    |[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]|Microsoft.Adapters.OracleEBS|  
    |[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]|Microsoft.Adapters.Sql.dll|  
    |[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]|Microsoft.Data.SAPClient|  
    |[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]|Microsoft.Data.SiebelClient|  
  
3.  Sur le **général** onglet, le **jeton de clé publique** valeur est la clé publique pour la DLL. Le **Version** valeur est le numéro de version de la DLL.  
  
4.  Copiez la clé publique, puis **Annuler**.  
  
## <a name="install-the-custom-rfcs"></a>Installez les RFC personnalisés  
Obligatoire uniquement *si* vous souhaitez utiliser le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]. Consultez [installer les RFC personnalisés](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md) dans le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] documentation. 
  
> [!IMPORTANT]
>  Si vous utilisez une version antérieure des RFC personnalisés fournis avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], puis vous devez les mettre à niveau pour les documents RFC fournis avec cette version. Cela en supprimant les RFC antérieures, puis installer les RFC inclus avec cette version.  

## <a name="install-the-enterprise-applications"></a>Installer les applications d’entreprise  
Pour les étapes et des conseils pour installer les systèmes métier entreprise différente, nous vous recommandons de qu'utiliser les guides d’installation fournis par le système de l’entreprise. Également faire référence à la documentation de l’adaptateur pour les modifications de configuration spécifique, le cas échéant.   

## <a name="installation-and-post-installation-checklist"></a>Liste de vérification installation et après l’installation  
  
-   Assurez-vous que vous avez installé tous les [les composants logiciels requis](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md) avec l’option d’installation correct.
  
-   Assurez-vous que vous disposez de la version prise en charge des applications métier enterprise installée sur votre ordinateur où vous avez installé le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Consultez [systèmes de prise en charge de métier (LOB)](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx).  
  
-   Pour installer uniquement l’adaptateur pour le système métier que vous souhaitez vous connecter, vérifiez que vous avez installé le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] à l’aide de la **personnalisé** option d’installation. Assurez-vous que vous n’avez pas utilisé le **Complete** option d’installation. Consultez [l’installation de BizTalk Adapter Pack](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md).  
  
-   Si vous souhaitez effectuer des appels tRFC au système SAP en utilisant le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], assurez-vous de créer les tables requises dans une base de données SQL Server. Consultez **les objets de créer une base de données SQL Server** (dans cette rubrique).
  
-   Lors de l’exécution du [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] Assistant installation, vous risquez d’obtenir un message d’erreur indiquant l’échec de la configuration inscrire les liaisons. Dans ce cas, inscrivez-le manuellement. Consultez **enregistrer des liaisons de l’adaptateur** (dans cette rubrique).  
  
-   Si vous avez choisi d’installer le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)] dans le cadre de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, veillez à installer les RFC personnalisés sur le système SAP. Consultez [installer les RFC personnalisés](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).

## <a name="more-good-info"></a>Plus d’informations correct
[Modifier ou supprimer le Pack d’adaptateurs BizTalk](../adapters-and-accelerators/update-or-uninstall-the-biztalk-adapter-pack-2016.md)  
[BizTalk Adapter Pack Forum aux questions](../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)