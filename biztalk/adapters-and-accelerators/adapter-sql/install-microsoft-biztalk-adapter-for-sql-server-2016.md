---
title: "Installez l’adaptateur Microsoft BizTalk pour SQL Server - 2016 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcc6b94e-1cac-4b90-8567-05b33caa9bf3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bab2a1edc7f3f19a8f76a041472a8c6d01b7743d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="install-microsoft-biztalk-adapter-for-sql-server---2016"></a>Installez l’adaptateur Microsoft BizTalk pour SQL Server - 2016
Installer le [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] inclus avec [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].

 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut être utilisé avec :  
  
-   Une application .NET  
  
-   Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]  
  
 Selon la façon dont vous utilisez les adaptateurs, les logiciels requis varient.  
 
  
<a name="BKMK_prereq_NET"></a>   
## <a name="prerequisites-when-using-the-adapter-with-a-net-application"></a>Configuration requise lors de l’utilisation de la carte avec une Application .NET  
Installer les logiciels suivants sur l’ordinateur sur lequel vous écrivez des applications .NET qui consomment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Installez le logiciel dans l’ordre répertorié.  

||
|---|
|-Windows Server 2016 <br />-Windows Server 2012 R2 <br />-Windows 10 <br />-Windows 8.1    |
|.NET Framework 4.6.*x*|
|Visual Studio 2015|
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]|
|Bibliothèques de client de SQL Server. Consultez le [versions prises en charge](#BKMK_SuppLOB) (dans cette rubrique).|

<a name="BKMK_prereq_BTS"></a>     
## <a name="prerequisites-when-using-the-adapter-with-biztalk-server"></a>Configuration requise lors de l’utilisation de l’adaptateur avec BizTalk Server  
Installer les logiciels suivants sur l’ordinateur où vous utilisez la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Installer le logiciel dans l’ordre indiqué.  

||
|---|
|-Windows Server 2016 <br />-Windows Server 2012 R2 <br />-Windows 10 <br />-Windows 8.1    |
|.NET Framework 4.6.*x*|
|Visual Studio 2015|
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> Installer le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] inclus avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Pour installer, procédez comme un **personnalisé** (sélectionnez **du complément de BizTalk Server**) ou **Complete** installation de le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].|
|[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]|
|Bibliothèques de client de SQL Server. Consultez le [versions prises en charge](#BKMK_SuppLOB) (dans cette rubrique).|

<a name="BKMK_SuppLOB"></a>   
## <a name="supported-sql-server-versions-and-client-libraries"></a>Les versions de SQL Server prises en charge et des bibliothèques clientes  
 La section suivante présente les versions prises en charge de SQL Server et le client, les bibliothèques requises par les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
-   **Les versions de serveur prises en charge**: SQL Server 2016, SQL Server 2014
  
-   **Prise en charge des versions de client**: Microsoft [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)] offres groupées de la DLL du client requises pour se connecter à SQL Server. Il est inutile d’installer explicitement n’importe quel client dll sur votre ordinateur.  
  
-   **Pilotes requis**:  
  
    -   Si vous utilisez les UDT fournis avec les versions de SQL Server, par exemple, géographie, assurez-vous que les DLL suivantes sont présentes sur l’ordinateur où vous utilisez l’adaptateur pour effectuer des opérations sur SQL Server. Par exemple, si vous créez des projets BizTalk pour effectuer des opérations sur SQL Server, ces DLL doit être présent sur l’ordinateur sur lequel BizTalk Server est en cours d’exécution.  
  
        -   Assurez-vous que Microsoft.SqlServer.Types.dll est ajouté au GAC.  
  
        -   Assurez-vous que SqlServerSpatial.dll est disponible dans le dossier System32.  
  
         Vous pouvez installer ces DLL sur l’ordinateur en exécutant le programme d’installation de SQL Server et en sélectionnant **outils de gestion – de base** et **outils de gestion – complet** dans la **sélection des fonctionnalités**page de l’Assistant.  
  
    -   Si vous utilisez l’adaptateur pour effectuer des opérations sur des colonnes de types de données FILESTREAM, assurez-vous que vous avez SQL Client Connectivity SDK est installé. Vous pouvez installer le SDK de connectivité Client SQL, exécutez le programme d’installation de SQL Server et sélectionnez **SQL Client Connectivity SDK** dans les **sélection des fonctionnalités** page de l’Assistant. L’adaptateur utilise le sqlncli10.dll, installé avec le SDK de connectivité Client SQL, pour effectuer des opérations FILESTREAM.  
  
    -   Si vous créez votre propre UDT dans SQL Server, assurez-vous que les assemblys respectives pour les UDT sont ajoutés dans le GAC.  
  
<a name="BKMK_Compat"></a>   
## <a name="64-bit-support"></a>prise en charge 64 bits 

Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut s’exécuter dans une instance d’hôte 32 bits ou 64 bits.

 Pour plus d’informations sur les scénarios d’installation pris en charge pour les 32 bits et 64 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [32 bits et 64 bits de scénarios installent](#BKMK_Install_Scenarios) (dans cette rubrique).
  
<a name="BKMK_Install_Adap"></a>   
## <a name="install-the-sql-adapter"></a>Installer l’adaptateur SQL  
 Assurez-vous que vous avez les composants requis installés avant d’installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Consultez [.NET prerequisites](#BKMK_prereq_NET) (dans cette rubrique), ou [conditions préalables de BizTalk Server](#BKMK_prereq_BTS) (dans cette rubrique).
  
 Vous pouvez installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] des deux manières suivantes :  
  
-   **En mode interactif** à l’aide de l’Assistant Installation
  
-   **En mode silencieux** à l’aide de msiexec dans la ligne de commande  
  
    > [!IMPORTANT]
    >  Vous devez disposer des privilèges d’administrateur sur l’ordinateur sur lequel vous installez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], indépendamment de si vous installez à l’aide de l’Assistant ou la ligne de commande.    

### <a name="BKMK_Install_Scenarios"></a>scénarios d’installation de 32 bits et 64 bits
 Avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut être utilisé pour :  
  
-   [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]au moment du design (lors de la génération des métadonnées pour les opérations).  
  
-   Moment du design de console Administration de BizTalk Server (pour créer des ports physiques).  
  
    > [!NOTE]
    >  Console d’Administration de BizTalk Server s’exécute comme une application de la Console MMC (Microsoft Management Console) 32 bits.  
  
-   Durée d’exécution BizTalk (pendant l’envoi et réception de messages à partir d’applications métier).  
  
 Vous pouvez avoir une installation où vous effectuez toutes ces tâches sur le même ordinateur ou sur des ordinateurs différents. Étant donné que les deux [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et MMC de BizTalk sont des processus 32 bits, vous devez installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur l’ordinateur où vous souhaitez effectuer les tâches au moment du design. Les scénarios suivants sont pris en charge pour l’installation de le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur les plateformes 32 bits et 64 bits.  
  
#### <a name="32-bit-install-scenarios"></a>scénarios d’installation 32 bits  
 Les scénarios suivants sont pris en charge lors de l’installation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur une plateforme 32 bits.  
  
|Conception de Visual Studio|Moment du design MMC de BizTalk|Durée d’exécution de BizTalk|Durée d’exécution Visual moment du design Studio et/ou de conception BizTalk MMC + BizTalk|  
|---|---|---|---|  
|-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> -Installer les clients 32 bits et autres DLL requise.|-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> -Installer les clients 32 bits et autres DLL requise.|-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> -Installer les clients 32 bits et autres DLL requise.|-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> -Installer les clients 32 bits et autres DLL requise.|  
  
#### <a name="64-bit-install-scenarios"></a>scénarios d’installation 64 bits  
 Les scénarios suivants sont pris en charge lors de l’installation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur une plateforme 64 bits.  
  
> [!NOTE]
>  Sur n’importe quel ordinateur où vous souhaitez effectuer des tâches au moment du design à l’aide [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou MMC de BizTalk, vous devez installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
|Conception de Visual Studio|Moment du design MMC de BizTalk|Durée d’exécution de BizTalk|Durée d’exécution Visual moment du design Studio et/ou de conception BizTalk MMC + BizTalk|  
|---|---|---|---|  
|-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> -Installer les clients 32 bits et autres DLL requise.|-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> -Installer les clients 32 bits et autres DLL requise.|**Pour un processus de BizTalk 32 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> -Installer les clients 32 bits et autres DLL requise.<br /><br /> **Pour un processus BizTalk de 64 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> -Installer 64 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> -Installez des clients 64 bits et autres DLL requise.|**Pour un processus de BizTalk 32 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> -Installer les clients 32 bits et autres DLL requise.<br /><br /> **Pour un processus BizTalk de 64 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> -Installer 64 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> -Installez des clients 64 bits et autres DLL requise.<br /><br /> -Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> -Installer les clients 32 bits et autres DLL requise.|  
  
<a name="BKMK_Install_wizard"></a>   
### <a name="install-the-adapter-in-interactive-mode"></a>Installer l’adaptateur en mode interactif  
Effectuez les étapes suivantes pour installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à l’aide de l’Assistant installation.  
  
1.  Exécutez le programme d’installation.  
  
    > [!NOTE]
    >  Si vous installez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur un ordinateur virtuel, l’Assistant installation ne peut pas continuer au-delà d’une boîte de dialogue informant que la vérification de l’espace disque disponible. Dans ce cas, nous vous recommandons d’utiliser l’option d’installation sans assistance. Pour plus d’informations, consultez [installer l’adaptateur SQL en mode silencieux](#BKMK_SilentInst) (dans cette rubrique).
  
2.  Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.  
  
3.  Lisez et acceptez le contrat de licence utilisateur final (CLUF), puis cliquez sur **suivant**.  
  
4.  Dans le **dossier de Destination** boîte de dialogue, spécifiez l’emplacement où vous souhaitez installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], cliquez sur **suivant**, puis cliquez sur **installer**.  
  
5.  Dans le **Customer Experience Improvement Program** boîte de dialogue, spécifiez si vous souhaitez inscrire pour le programme (amélioration). Dans le cadre de ce programme pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous allez partager les données suivantes avec Microsoft :  
  
    -   Les données relatives au matériel de l’ordinateur sur lequel vous installez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
    -   Les données relatives à des versions de SQL Server que vous utilisez pour vous connecter à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
     Spécifiez votre choix et cliquez sur **OK**.  
  
    > [!NOTE]
    >  Vous pouvez toujours modifier vos préférences concernant l’inscription pour CEIP en exécutant le programme d’installation en mode réparation à partir du panneau.  
  
6.  Cliquez sur **Terminer**.  
  
<a name="BKMK_SilentInst"></a>   
### <a name="install-the-sql-adapter-in-silent-mode"></a>Installer l’adaptateur SQL en mode silencieux 
Effectuez les étapes suivantes pour effectuer une installation sans assistance de [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à l’aide de la `msiexec` commande.  
  
1.  Ouvrez une invite de commandes et accédez au dossier où vous avez le programme d’installation.  
  
2.  Exécutez la commande suivante pour installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  
  
    > [!NOTE]
    >  Pour effectuer une installation sans assistance sur une plateforme x64 64, les commandes suivantes, remplacez SqlAdapterSetup.msi SqlAdapterSetup64.msi.  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn  
    ```  
  
     Vous pouvez également choisir d’inscrire pour CEIP dans le cadre de l’installation sans assistance. Dans le cadre de ce programme pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous allez partager les données suivantes avec Microsoft :  
  
    -   Le matériel de l’ordinateur sur lequel vous installez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
    -   Les versions de SQL Server que vous utilisez pour vous connecter à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
     Pour vous inscrire pour CEIP, exécutez la commande suivante :  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn CEIP_OPTIN=true  
    ```  
  
     Par défaut, l’option a la valeur false.  
  
     Pour plus d’informations sur la `msiexec` de commandes, tapez `msiexec` sur la ligne de commande et appuyez sur `ENTER`, ou consultez [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).  
  
<a name="BKMK_PostInst"></a>   
## <a name="post-installation-tasks"></a>Tâches de post-installation  
  
<a name="BKMK_Register_Bindings"></a>   
#### <a name="register-the-bindings"></a>Inscrire les liaisons  
Effectuez ces étapes *uniquement* si l’Assistant installation ne parvient pas à inscrire des liaisons de l’adaptateur dans le fichier machine.config.  
  
1.  Accédez au fichier machine.config sur l’ordinateur. Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.  
  
2.  Ouvrez le fichier à l’aide d’un éditeur de texte.  
  
3.  Pour enregistrer des liaisons de l’adaptateur :  
  
    1.  Recherchez l’élément « system.serviceModel » et ajoutez le code suivant dans cette section :  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.  
  
    3.  Ajoutez la section suivante sous le nœud « bindingElementExtensions ».  
  
         Pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], ajoutez :  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.  
  
    5.  Ajoutez la section suivante sous le nœud « bindingExtensions ».  
  
         Pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], ajoutez :  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  Pour plus d’informations sur la façon de déterminer la clé publique, consultez [détermination de la clé publique et la Version](#BKMK_PubKey).  
  
4.  Enregistrez et fermez le fichier machine.config.  
  
<a name="BKMK_PubKey"></a>   
#### <a name="determining-the-public-key-and-version"></a>Détermination de la clé publique et la Version  
Effectuez les étapes suivantes pour déterminer la clé publique et la version pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
1.  Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.  
  
2.  Avec le bouton droit de la DLL pour laquelle vous souhaitez que la clé publique, puis sélectionnez **propriétés**. Le tableau suivant répertorie le nom des DLL pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
    |Adaptateur|Nom de la DLL|  
    |---|---|  
    |[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]|Microsoft.Adapters.Sql.dll|  
  
3.  Sur le **général** onglet, la valeur par rapport à la **jeton de clé publique** étiquette spécifie la clé publique pour la DLL. De même, la valeur par rapport à la **Version** étiquette Spécifie le numéro de version de la DLL.  
  
4.  Copiez la clé publique, puis cliquez sur **Annuler**.  
  
<a name="BKMK_Modify_Adap"></a>   
## <a name="update-or-change-the-sql-adapter-installation"></a>Mettre à jour ou de modifier l’installation de l’adaptateur SQL  
 Procédez comme suit pour modifier le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation. Assurez-vous que vous avez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installé avant d’exécuter l’Assistant Installation pour modifier le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.  
  
 Vous pouvez modifier le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation des deux manières suivantes :  
  
-   **En mode interactif** en exécutant l’Assistant installation.  
  
-   **En mode silencieux** à l’aide de la ligne de commande.  
  
#### <a name="update-the-sql-adapter-installation-in-interactive-mode"></a>Mise à jour de l’installation de l’adaptateur SQL en mode interactif  
  
1.  Cliquez sur **Démarrer**, puis cliquez sur **le panneau de configuration**.  
  
2.  Dans le panneau de configuration, double-cliquez sur **programmes et fonctionnalités**.  
  
3.  Dans le **programmes et fonctionnalités** fenêtre, sélectionnez **l’adaptateur Microsoft BizTalk pour SQL Server**, puis cliquez sur **modification**.  
  
4.  Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.  
  
5.  Dans le **modifier, réparer ou supprimer l’installation** boîte de dialogue, cliquez sur **réparer**.  
  
6.  Dans le **prêt à réparer l’adaptateur Microsoft BizTalk pour SQL Server** boîte de dialogue, cliquez sur **réparer**.  
  
7.  Si nécessaire, modifiez vos préférences concernant le choix d’amélioration du produit, puis cliquez sur **OK**.  
  
8.  Cliquez sur **Terminer**.  
  
#### <a name="update-the-sql-adapter-installation-in-silent-mode"></a>Mise à jour de l’installation de l’adaptateur SQL en mode silencieux  
  
1.  Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] programme d’installation.  
  
2.  Exécutez la commande suivante :  
  
    > [!NOTE]
    >  Pour modifier la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation en mode silencieux sur une plateforme x64 64, les commandes suivantes, remplacez SqlAdapterSetup.msi par SqlAdapterSetup64.msi.  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn /f  
    ```  
  
    > [!IMPORTANT]
    >  Lors de la modification du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation en mode silencieux, vous ne pouvez pas modifier vos préférences pour vous inscrire ou de refuser le CEIP. Les préférences reste le même que vous avez spécifié pendant l’installation, même si vous définissez explicitement la CEIP_OPTIN à true ou false.  
  
     Pour plus d’informations sur la `msiexec` type de commande `msiexec` sur la ligne de commande et appuyez sur `ENTER`, ou consultez [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).  
  
<a name="BKMK_Remove_Adap"></a>   
## <a name="uninstall-or-remove-the-sql-adapter"></a>Désinstaller ou supprimer l’adaptateur SQL  
 Procédez comme suit pour supprimer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à partir de votre ordinateur. Assurez-vous que vous avez le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installé avant d’exécuter l’Assistant Installation pour supprimer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 Vous pouvez supprimer la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] des deux manières suivantes :  
  
-   **En mode interactif** en exécutant l’Assistant installation.  
  
-   **En mode silencieux** à l’aide de la ligne de commande.  
  
#### <a name="uninstall-the-sql-adapter-in-interactive-mode"></a>Désinstaller l’adaptateur SQL en mode interactif  
  
1.  Cliquez sur **Démarrer**, puis cliquez sur **le panneau de configuration**.  
  
2.  Dans le panneau de configuration, double-cliquez sur **programmes et fonctionnalités**.  
  
3.  Dans le **Ajout / Suppression de programmes** fenêtre, sélectionnez **l’adaptateur Microsoft BizTalk pour SQL Server**, puis cliquez sur **supprimer**.  
  
4.  Dans la boîte de dialogue, cliquez sur **Oui**.  
  
#### <a name="uninstall-the-sql-adapter-in-silent-mode"></a>Désinstaller l’adaptateur SQL en mode silencieux  
  
1.  Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] programme d’installation.  
  
2.  Exécutez la commande suivante :  
  
    > [!NOTE]
    >  Pour supprimer la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] en mode silencieux sur une plateforme x64 64, les commandes suivantes, remplacez SqlAdapterSetup.msi par SqlAdapterSetup64.msi.  
  
    ```  
    msiexec /x SqlAdapterSetup.msi /qn  
    ```  
  
     Cette commande supprime le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à partir de l’ordinateur.  
  
     Pour plus d’informations sur la `msiexec` de commandes, tapez `msiexec` sur la ligne de commande et appuyez sur `ENTER`, ou consultez [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).  
  
<a name="BKMK_PostRemove"></a>   
### <a name="post-uninstall-task"></a>Tâche post-désinstallation  
 Si le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] le programme d’installation ne parvient pas à supprimer les liaisons de l’adaptateur lors de la suppression du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous devez les supprimer manuellement. La section suivante décrit comment supprimer manuellement les liaisons pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
Effectuez ces étapes *uniquement* si l’Assistant installation ne parvient pas à supprimer les liaisons de l’adaptateur à partir du fichier machine.config.  
  
1.  Accédez au fichier machine.config sur l’ordinateur. Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.  
  
    -   Pour Microsoft .NET Framework 3.5 SP1, \< *version* \> est la version v2.0.50727 du .NET Framework.  
  
    -   Pour Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \< *version* \> est la version v4.0.30319 du .NET Framework.  
  
2.  Ouvrez le fichier à l’aide d’un éditeur de texte.  
  
3.  Pour supprimer l’inscription de la liaison de la carte :  
  
    1.  Recherchez l’élément « system.serviceModel » et supprimer les éléments suivants figurant dans l’élément :  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
  
        ```  
  
    2.  Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.  
  
    3.  Supprimez la section suivante sous le nœud « bindingElementExtensions ».  
  
         Pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], supprimer :  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.  
  
    5.  Supprimez la section suivante sous le nœud « bindingExtensions ».  
  
         Pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], supprimer :  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
4.  Enregistrez et fermez le fichier machine.config.  
  
## <a name="see-also"></a>Voir aussi
[Installer l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/install-the-sql-adapter.md)  
[Présentation de l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)