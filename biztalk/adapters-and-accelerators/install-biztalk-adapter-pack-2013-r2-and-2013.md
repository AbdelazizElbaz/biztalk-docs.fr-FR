---
title: "Installation de BizTalk, l’adaptateur R2 Pack 2013 et 2013 | Documents Microsoft"
description: "Conditions préalables et les étapes d’installation BAP 2013 R2 et 2013 BAP inclus dans BizTalk Server"
ms.custom: 
ms.date: 2015-12-09
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9980953a-8d38-476f-af38-4f4214ba61f2
caps.latest.revision: "107"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8bc1ebbdaf2973f4749da6c0832d49204588b6c
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="install-biztalk-adapter-pack-2013-r2-and-2013"></a>Installer 2013 et BizTalk adaptateur Pack 2013 R2
Ce document répertorie la configuration logicielle requise et les étapes pour installer l’agent Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] (LOB) fournis avec BizTalk Server 2013 ou [!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)].  
  
## <a name="change-log"></a>Journal des modifications  
  
|Date|Modifier|  
|---|---|  
|Mars 2016|Dans **après l’installation en cours...** , ajouté des étapes pour configurer l’adaptateur de base de données Oracle pour utiliser la nouvelle version de Oracle.DataAccess.dll.|  
  
<a name="BKMK_Prereqs"></a>   
## <a name="software-prerequisites"></a>Configuration logicielle requise  
 Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] peuvent être utilisés à partir de :  
  
-   Une application .NET  
  
-   Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   Une interface ADO  
  
-   Un portail de Microsoft SharePoint  
  
 Selon la façon dont vous utilisez les adaptateurs, les logiciels requis varient.  
  
### <a name="prerequisites-when-using-a-net-application"></a>Configuration requise lors de l’utilisation d’une application .NET  
Lorsque vous utilisez une application .NET pour consommer les adaptateurs, les logiciels suivants sont requis sur votre ordinateur de développement (l’ordinateur sur lequel vous créez l’application .NET). Installer le logiciel dans l’ordre indiqué.
  
|BizTalk adaptateur Pack 2013 R2|Pack d’adaptateurs BizTalk 2013|  
|---|---|  
|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]R2, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], Windows 8.1, Windows 7 SP1|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1, Windows 8, Windows 7 SP1|  
|[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]|Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]|  
|Visual Studio 2013|Visual Studio 2012|  
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|  
|Les clients d’application d’entreprise et les logiciels associés. Consultez [prise en charge des Versions des applications Enterprise](#BKMK_SuppLOB).|Les clients d’application d’entreprise et les logiciels associés. Consultez [prise en charge des Versions des applications Enterprise](#BKMK_SuppLOB).|  

### <a name="prerequisites-when-using-a-biztalk-server"></a>Configuration requise lors de l’utilisation d’un serveur BizTalk Server  
Lorsque vous utilisez un serveur BizTalk Server pour utiliser les adaptateurs, les logiciels suivants sont requis sur votre serveur BizTalk Server. Installer le logiciel dans l’ordre indiqué.
  
|BizTalk adaptateur Pack 2013 R2|Pack d’adaptateurs BizTalk 2013|  
|---|---|  
|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]R2, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], Windows 8.1, Windows 7 SP1|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1, Windows 8, Windows 7 SP1|  
|[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]|Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]|  
|Visual Studio 2013|Visual Studio 2012|  
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]<br /><br /> Installer le [!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)] pour [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] inclus avec le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]. Pour installer, procédez comme un **personnalisé** (sélectionnez **du complément de BizTalk Server**) ou **Complete** installation de le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]<br /><br /> Installer le [!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)] pour [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] inclus avec le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]. Pour installer, procédez comme un **personnalisé** (sélectionnez **du complément de BizTalk Server**) ou **Complete** installation de le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].|  
|BizTalk Server 2013 R2|BizTalk Server 2013|  
|Les clients d’application d’entreprise et les logiciels associés. Consultez [prise en charge des Versions des applications Enterprise](#BKMK_SuppLOB).|Les clients d’application d’entreprise et les logiciels associés. Consultez [prise en charge des Versions des applications Enterprise](#BKMK_SuppLOB).|  

### <a name="prerequisites-when-using-ado"></a>Configuration requise lors de l’utilisation d’ADO  
 Le  **[!INCLUDE[adaptersap](../includes/adaptersap-md.md)]**  et  **[!INCLUDE[adaptersiebel](../includes/adaptersiebel-md.md)]**  inclure une couche d’ADO ( *[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]*  et  *[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]* ). Cette couche de ADO peut être utilisée pour écrire un client ADO.NET pour se connecter à un système SAP ou le système Siebel. Vous pouvez également utiliser la couche d’ADO avec SQL Server Integration Services (SSIS) pour importer et exporter des données à partir de l’application métier et SQL Server Reporting Services (SSRS) pour générer des rapports pour présenter les données à partir des systèmes métier.  
  
> [!NOTE]
>  À l’aide du fournisseur ADO avec SSRS est prise en charge uniquement pour les  *[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]* .  
  
Le logiciel suivant est requis sur l’ordinateur qui utilise le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] avec une interface ADO. Installer le logiciel dans l’ordre indiqué.
  
|BizTalk adaptateur Pack 2013 R2|Pack d’adaptateurs BizTalk 2013|  
|---|---|  
|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]R2, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], Windows 8.1, Windows 7 SP1|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1, Windows 8, Windows 7 SP1|  
|[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]|Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]|  
|Visual Studio 2013|Visual Studio 2012|  
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|  
|[!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)], [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]|[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]|  
|Les clients d’application d’entreprise et les logiciels associés. Consultez [prise en charge des Versions des applications Enterprise](#BKMK_SuppLOB).|Les clients d’application d’entreprise et les logiciels associés. Consultez [prise en charge des Versions des applications Enterprise](#BKMK_SuppLOB).|  

### <a name="prerequisites-when-using-microsoft-sharepoint"></a>Configuration requise lors de l’utilisation de Microsoft SharePoint  
 L’objectif de l’utilisation des adaptateurs Microsoft SharePoint doit afficher les données à partir d’une application métier dans un portail SharePoint.  
  
Une installation par défaut avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] et SharePoint peut être un seul ordinateur ou utiliser des ordinateurs distincts pour différentes tâches. Le tableau suivant récapitule la configuration logicielle requise pour chaque ordinateur. Si vous utilisez un seul ordinateur, tous les logiciels sont requis sur cet ordinateur. Installer le logiciel dans l’ordre indiqué.  
  
|Ordinateur sur lequel vous exécutez l’Assistant développement d’adaptateurs WCF|Ordinateur sur lequel vous hébergez le service WCF|Ordinateur sur lequel vous pouvez utiliser SharePoint Designer pour définir les Types de contenu externe|Ordinateur sur lequel vous utilisez SharePoint pour présenter les informations à partir d’une application métier|  
|---|---|---|---|  
|**BAP 2013 R2**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2<br/>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>Windows 8.1<br/>Windows 7 SP1</li><li>[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]</li><li> Visual Studio 2013</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>Clients d’application respectifs d’entreprise et les logiciels associés. Consultez [prise en charge des Versions des applications Enterprise](#BKMK_SuppLOB).</li></ul> **BAP 2013**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1<br/>Windows 8<br/>Windows 7 SP1</li><li>Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</li><li>Visual Studio 2012</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>Clients d’application respectifs d’entreprise et les logiciels associés. Consultez [prise en charge des Versions des applications Enterprise](#BKMK_SuppLOB).</li></ul>|**BAP 2013 R2**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2<br/>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>Windows 8.1<br/>Windows 7 SP1</li><li>[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>Clients d’application respectifs d’entreprise et les logiciels associés. Consultez [prise en charge des Versions des applications Enterprise](#BKMK_SuppLOB).</li><li>La version d'Internet Information Services (IIS) fournie avec le système d'exploitation. Ko 224609 répertorie les versions.</li></ul>**BAP 2013**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1<br/>Windows 8<br/>Windows 7 SP1</li><li>Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>Clients d’application respectifs d’entreprise et les logiciels associés. Consultez [prise en charge des Versions des applications Enterprise](#BKMK_SuppLOB).</li><li>La version d'Internet Information Services (IIS) fournie avec le système d'exploitation. Ko 224609 répertorie les versions.</li></ul>|Kit de développement (SDK) de Microsoft Office SharePoint Server|Mise à jour de Microsoft Office serveurs Infrastructure. Téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=128344](http://go.microsoft.com/fwlink/?LinkId=128344).|  
  
<a name="BKMK_SuppLOB"></a>   
## <a name="supported-enterprise-application-versions"></a>Versions d’application pris en charge d’entreprise  

Pour afficher les versions de système LOB spécifiques qui sont pris en charge par le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], consultez  **[systèmes de prise en charge de métier (LOB)](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx)**. 

Cette section répertorie des informations supplémentaires pour chaque adaptateur, comme n’importe quel client DLL requis pour chaque carte.  
  
### <a name="oracle-database-adapter"></a>Adaptateur de base de données Oracle  
  
-   Facultatif : Si vous utilisez des transactions distribuées avec la base de données Oracle, installez **Oracle Services pour Microsoft Transaction Server** (qui fait partie de l’installation du client Oracle) sur l’ordinateur exécutant le client de la carte.  
  
-   Pour votre application de fonctionner avec la version la plus récente de ODP.NET, installez le **stratégie DLL** et inscrire les DLL dans le GAC. Consultez [le fournisseur de données Oracle pour .NET FAQ](http://www.oracle.com/technetwork/database/windows/faq-093106.html).  

### <a name="oracle-e-business-adapter"></a>Adaptateur Oracle E-Business  
  
-   Facultatif : Pour utiliser les transactions distribuées avec la base de données Oracle, installez **Oracle Services pour Microsoft Transaction Server** (qui fait partie de l’installation du client Oracle) sur l’ordinateur exécutant le client de la carte.  
  
-   Pour votre application de fonctionner avec la version la plus récente de ODP.NET, installez le **stratégie DLL** et inscrire les DLL dans le GAC. Consultez [le fournisseur de données Oracle pour .NET FAQ](http://www.oracle.com/technetwork/database/windows/faq-093106.html).  
  
### <a name="sap-adapter"></a>Adaptateur SAP  
  
-   Le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] requiert la version Unicode du SDK RFC indépendamment de si le système SAP est Unicode ou non-Unicode.  
  
-   **Pilotes requis**: le tableau suivant répertorie les DLL requises par le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] pour interagir avec le système SAP. La plupart des packages qui contiennent ces DLL doit être téléchargée à partir de SAP Service Marketplace. Pour obtenir les téléchargements à partir de SAP Service Marketplace : 
  
    1.  Installer le Gestionnaire de téléchargement disponible à partir de SAP Service Marketplace.  
  
    2.  Configurer le Gestionnaire de téléchargement à l’aide de vos informations d’identification pour le système SAP Service Marketplace.  
  
    3.  Être autorisé par l’administrateur SAP dans votre organisation pour télécharger le logiciel à partir du site Web du service SAP. Cela est nécessaire, car l’accès au centre de Distribution de logiciels SAP est restreint par un objet d’autorisation de télécharger le logiciel. Cela garantit que le logiciel est téléchargé uniquement par les utilisateurs autorisés.  
  
    4.  Installer le programme SAPCAR ne, ce qui est requis pour extraire les fichiers des packages que vous téléchargez à partir de SAP Service Marketplace. SAPCAR n’est également disponible à partir de SAP Service Marketplace.  
  
     Pour la version 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], vous devez disposer les versions correspondantes de 32 bits et 64 bits de ces DLL.  
  
    -   Sur un ordinateur 32 bits, la version 32 bits des DLL doit être ajoutée au dossier C:\Windows\System32.  
  
    -   Sur un ordinateur 64 bits, la version 32 bits des DLL doit être ajoutée au dossier C:\Windows\SysWow64. La version 64 bits des DLL doit être ajoutée au dossier C:\Windows\System32.  
  
    |Version du client SAP|Pilotes requis|  
    |------------------------|----------------------|  
    |6.4|**Pack d’adaptateurs BizTalk 2013 uniquement**<br /><br /> - **UNICODE DU KIT DE DÉVELOPPEMENT LOGICIEL RFC 6.40 SAP**. Cette option est disponible dans le cadre de SNOTE<sup> * </sup> 27517. Les instructions pour télécharger le Kit de développement sont disponibles dans [http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691). Après avoir téléchargé et extrait le Kit de développement, vous pouvez copier toutes les DLL dans les dossiers \rfcsdk\bin et \rfcsdk\lib vers l’emplacement pertinent mentionné précédant cette table. <br /> <br /> -DLL sont disponibles à partir de SAP dans le cadre de **R3DLLINST.zip**. Il contient des DLL d’exécution de Microsoft et peut être téléchargé à partir du site SAP. Consultez SNOTE<sup> * </sup> 684106 pour plus d’informations. Vous pouvez télécharger le fichier .zip de [http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693). Ce lien a une option « Pièces jointes » à partir duquel vous pouvez télécharger le package.<br /><br /> -Si vous utilisez des Communications de réseau sécurisée (SNC) SAP pour se connecter à un système SAP, vous devez également les DLL appropriées à partir de SAP. Ces DLL sont différentes pour les plateformes 32 bits et 64 bits et sont disponibles avec SNOTE<sup> * </sup> 352295. Vous pouvez télécharger les DLL à partir de [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032). Ce lien a une option « Pièces jointes » à partir duquel vous pouvez télécharger le package. Les noms de DLL sont :<br /><br /> - **Pour 32 bits**: gsskrb5.dll, gssntlm.dll<br /><br /> -  **Pour 64 bits x86**: gx64krb5.dll, gx64ntlm.dll|  
    |7.0|- **UNICODE DU KIT DE DÉVELOPPEMENT LOGICIEL RFC 7.00 SAP**. Cette option est disponible dans le cadre de SNOTE<sup> * </sup> 27517. Les instructions pour télécharger le Kit de développement sont disponibles dans [http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691). Après avoir téléchargé et extrait le Kit de développement logiciel, copiez toutes les DLL dans les dossiers \rfcsdk\bin et \rfcsdk\lib et à l’emplacement approprié mentionné précédant cette table. <br /> <br /> -DLL sont disponibles à partir de SAP dans le cadre de **R3DLLINST.zip**. Il contient des DLL d’exécution de Microsoft et peut être téléchargé à partir du site SAP. Consultez SNOTE<sup> * </sup> 684106 pour plus d’informations. Vous pouvez télécharger le fichier .zip de [http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693). Ce lien a une option « Pièces jointes » à partir duquel vous pouvez télécharger le package.<br /><br /> -Si vous utilisez des Communications de réseau sécurisée (SNC) SAP pour se connecter à un système SAP, vous devez également les DLL appropriées à partir de SAP. Ces DLL sont différentes pour les plateformes 32 bits et 64 bits et sont disponibles avec SNOTE<sup> * </sup> 352295. Vous pouvez télécharger les DLL à partir de [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032). Ce lien a une option « Pièces jointes » à partir duquel vous pouvez télécharger le package. Les noms de DLL sont :<br /><br /> - **Pour 32 bits**: gsskrb5.dll, gssntlm.dll<br /><br /> - **Pour 64 bits x86**: gx64krb5.dll, gx64ntlm.dll|  
    |7.1|- **UNICODE DU KIT DE DÉVELOPPEMENT LOGICIEL RFC 7.10 SAP**. Cette option est disponible dans le cadre de SNOTE<sup> * </sup> 27517. Les instructions pour télécharger le Kit de développement sont disponibles dans [http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691). Après avoir téléchargé et extrait le Kit de développement, vous pouvez copier toutes les DLL dans les dossiers \rfcsdk\bin et \rfcsdk\lib vers l’emplacement pertinent mentionné précédant cette table. <br /> <br /> -DLL sont disponibles à partir de SAP dans le cadre de **R3DLLINST.zip**. Il contient des DLL d’exécution de Microsoft et peut être téléchargé à partir du site SAP. Consultez SNOTE<sup> * </sup> 684106 pour plus d’informations. Vous pouvez télécharger le fichier .zip de [http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693). Ce lien a une option « Pièces jointes » à partir duquel vous pouvez télécharger le package.<br /><br /> -Microsoft Visual C++ les DLL d’exécution requis pour les clients SAP 7.1 sont disponibles sur les liens suivants :<br /><br /> - **Pour les clients de SAP 7.1 32 bits**: Vcredist_x86.exe de [http://go.microsoft.com/fwlink/?LinkId=107086](http://go.microsoft.com/fwlink/?LinkId=107086).<br /><br /> -                                 **Pour les clients SAP 7.1 de 64 bits**: Vcredist_x64.exe à partir de [http://go.microsoft.com/fwlink/?LinkId=107087](http://go.microsoft.com/fwlink/?LinkId=107087).<br /><br /> -Si vous utilisez des Communications de réseau sécurisée (SNC) SAP pour se connecter à un système SAP, vous devez également les DLL appropriées à partir de SAP. Ces DLL sont différentes pour les plateformes 32 bits et 64 bits et sont disponibles avec SNOTE<sup> * </sup> 352295. Vous pouvez télécharger les DLL à partir de [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032). Ce lien a une option « Pièces jointes » à partir duquel vous pouvez télécharger le package. Les noms de DLL sont :<br /><br /> - **Pour 32 bits**: gsskrb5.dll, gssntlm.dll<br /><br /> - **Pour 64 bits x86**: gx64krb5.dll, gx64ntlm.dll|  
  
     * SNOTEs sont les notes de publication qui accompagnent les correctifs disponibles par SAP.  

### <a name="siebel-adapter"></a>Adaptateur Siebel  
Aucune étape supplémentaire.
  
### <a name="sql-adapter"></a>Adaptateur SQL  
  
**Pilotes requis**:  
  
-   **Pour SQL Server 2005**: Si vous créez des Types de définis par l’utilisateur (UDT) dans SQL Server, assurez-vous que les assemblys respectives pour les UDT sont ajoutés dans le GAC.  
  
-   **Pour SQL Server 2014, SQL Server 2012, SQL Server 2008 R2, SQL Server 2008 SP1**:  
  
    -   Si vous utilisez les UDT fournis avec les versions de SQL Server, par exemple, géographie, assurez-vous que les DLL suivantes sont présentes sur l’ordinateur où vous utilisez l’adaptateur pour effectuer des opérations sur SQL Server. Par exemple, si vous créez des projets BizTalk pour effectuer des opérations sur SQL Server, ces DLL doit être présent sur l’ordinateur sur lequel BizTalk Server est en cours d’exécution.  
  
        -   Assurez-vous que Microsoft.SqlServer.Types.dll est ajouté au GAC.  
  
        -   Assurez-vous que SqlServerSpatial.dll est disponible dans le dossier System32.    
        
        Vous pouvez installer ces DLL sur l’ordinateur en exécutant le programme d’installation de SQL Server et en sélectionnant **outils de gestion – de base** et **outils de gestion – complet** dans la **sélection des fonctionnalités**page de l’Assistant.          
  
    -   Si vous utilisez l’adaptateur pour effectuer des opérations sur des colonnes de types de données FILESTREAM, assurez-vous que vous avez SQL Client Connectivity SDK est installé. Vous pouvez installer le SDK de connectivité Client SQL, exécutez le programme d’installation de SQL Server et sélectionnez **SQL Client Connectivity SDK** dans les **sélection des fonctionnalités** page de l’Assistant. L’adaptateur utilise le sqlncli10.dll, installé avec le SDK de connectivité Client SQL, pour effectuer des opérations FILESTREAM.  

    -   Si vous créez votre propre UDT dans SQL Server, assurez-vous que les assemblys respectives pour les UDT sont ajoutés dans le GAC.

## <a name="64-bit-support"></a>prise en charge 64 bits

L’adaptateur Siebel est pris en charge dans une instance d’hôte 32 bits. Il n’est pas pris en charge pour exécuter l’adaptateur Siebel dans une instance d’hôte 64 bits. 

Toutes les autres cartes peuvent s’exécuter dans une instance d’hôte 32 bits ou 64 bits. 


  
 Pour plus d’informations sur les scénarios d’installation pris en charge pour l’installation 32 bits et 64 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], consultez [scénarios d’installation de BizTalk Adapter Pack sur les plateformes 32 bits et 64 bits](#BKMK_Install_Scenarios).  
  
<a name="BKMK_Install_Adap"></a>   
## <a name="installing-the-biztalk-adapter-pack"></a>L’installation de BizTalk Adapter Pack  
 Vous assurer que tous les [les composants logiciels requis](#BKMK_Prereqs) sont installés avant d’installer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Vous pouvez installer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] des deux manières suivantes :  
  
-   **En mode interactif**: exécuter l’Assistant Installation  
  
-   **En mode silencieux**: utiliser la ligne de commande  
  
    > [!IMPORTANT]
    >  Vous devez disposer des privilèges d’administrateur sur l’ordinateur sur lequel vous installez le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], indépendamment de si vous installez à l’aide de l’Assistant ou la ligne de commande.  

### <a name="typical-vs-custom-installation"></a>Installation personnalisée d’installation par défaut et  
Cette section répertorie les types d’installation et les fonctionnalités qui sont installées avec chaque option :  
  
-   Le **standard** et **Complete** options installer toutes les cartes, avec les fournisseurs de données associé. Vous n’avez pas de l’option de choix d’une carte spécifique d’installation.  
  
-   Le **personnalisé** option installe une ou plusieurs cartes, avec les fournisseurs de données associé. Vous pouvez choisir les adaptateurs à installer. Si vous choisissez d’installer un fournisseur de données, vous devez également installer l’adaptateur correspondant. Toutefois, vous pouvez installer un adaptateur sans installer le fournisseur de données correspondant. Cela en développant le **ADO fournisseurs** nœud, puis en sélectionnant les fournisseurs que vous ne souhaitez pas installer. Consultez [installation de BizTalk Adapter Pack en Mode interactif](#BKMK_Install_wizard).  
  
     Par exemple, si vous installez le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], vous devez également installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]. Toutefois, vous pouvez installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] sans installer le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].  
  
<a name="BKMK_Install_Scenarios"></a>   
### <a name="scenarios-for-installing-the-biztalk-adapter-pack-on-32-bit-and-64-bit-platforms"></a>Scénarios d’installation de BizTalk Adapter Pack sur les plateformes 32 bits et 64 bits  
 Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] peut être utilisé pour : 
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]au moment du design (lors de la génération des métadonnées pour les opérations sur les applications métiers)
  
-   Moment du design console Administration de BizTalk Server (pour créer des ports physiques)
  
    > [!NOTE]
    >  Console d’Administration de BizTalk Server s’exécute comme une application de la Console MMC (Microsoft Management Console) 32 bits.  
  
-   Durée d’exécution BizTalk (pendant l’envoi et réception de messages à partir d’applications métier)

Vous pouvez utiliser un ordinateur unique pour toutes ces tâches, ou utiliser des ordinateurs distincts. Étant donné que les deux [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et MMC de BizTalk sont des processus 32 bits, vous devez installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] sur l’ordinateur où vous effectuez les tâches de conception. 

#### <a name="scenarios-for-installing-the-biztalk-adapter-pack-on-a-32-bit-platform"></a>Scénarios d’installation de BizTalk Adapter Pack sur une plateforme 32 bits  
 Les scénarios pris en charge sur une plateforme 32 bits sont les suivantes :  
  
|Pour le moment du design Visual Studio|Moment du design pour la console MMC de BizTalk|Pour le moment de l’exécution de BizTalk|Pour la conception de Visual Studio heure et/ou de conception BizTalk MMC + BizTalk moment de l’exécution|  
|---|---|---|---|  
|-Installer 32 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.|-Installer 32 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.|-Installer 32 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.|-Installer 32 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.|  
  
#### <a name="scenarios-for-installing-the-biztalk-adapter-pack-on-a-64-bit-platform"></a>Scénarios d’installation de BizTalk Adapter Pack sur une plateforme 64 bits  
 Les scénarios pris en charge sur une plateforme 64 bits sont les suivantes :  
  
|Pour le moment du design Visual Studio|Moment du design pour la console MMC de BizTalk|Pour le moment de l’exécution de BizTalk|Pour la conception de Visual Studio heure et/ou de conception BizTalk MMC + BizTalk moment de l’exécution|  
|---|---|---|---|  
|-Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.|-Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.|**Pour un processus de BizTalk 32 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.<br /><br /> **Pour un processus BizTalk de 64 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 64 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer 64 bits LOB client et autres DLL requise.|**Pour un processus de BizTalk 32 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.<br /><br /> **Pour un processus BizTalk de 64 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 64 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer 64 bits LOB client et autres DLL requise.<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.|  
  
> [!NOTE]
>  Sur n’importe quel ordinateur où vous souhaitez effectuer des tâches de conception, à l’aide [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] ou MMC de BizTalk, vous devez installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  
  
<a name="BKMK_Install_wizard"></a>   
### <a name="installing-the-biztalk-adapter-pack-in-interactive-mode"></a>L’installation de BizTalk Adapter Pack en mode interactif  
Effectuez les étapes suivantes pour installer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] à l’aide de l’Assistant installation.  
  
1.  À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] support d’installation, exécutez **Setup.exe**.  
  
2.  Sélectionnez **installer des adaptateurs Microsoft BizTalk**. Dans la fenêtre suivante, sélectionnez **installer Microsoft BizTalk Adapter Pack** ou **installer Microsoft BizTalk Adapter Pack (x64)**, selon votre plateforme.  
  
    > [!NOTE]
    >  Si vous installez le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] sur un ordinateur virtuel, l’Assistant installation ne peut pas continuer au-delà d’une boîte de dialogue informant que la vérification de l’espace disque disponible. Dans ce cas, nous vous recommandons d’utiliser l’option d’installation sans assistance. Consultez [l’installation de BizTalk Adapter Pack en Mode silencieux](#BKMK_SilentInst) (dans cette rubrique).  
  
3.  Dans l’écran de bienvenue, sélectionnez **suivant**.  
  
4.  Acceptez le contrat de licence utilisateur final (CLUF), puis sélectionnez **suivant**.  
  
5.  Dans **choisir le Type d’installation**:  
  
    -   Pour installer les fonctionnalités les plus courantes, sélectionnez **standard**.  
  
    -   Pour sélectionner les cartes que vous souhaitez installer, sélectionnez **personnalisé**, puis passez à l’étape suivante.  
  
    -   Pour installer toutes les fonctionnalités, sélectionnez **Complete**.  
  
        > [!IMPORTANT]
        >  Pour installer uniquement l’adaptateur que vous utilisez pour interagir avec votre application d’entreprise, sélectionnez le **personnalisé** installation.  
  
6. **Requis** uniquement si vous choisissez l’installation personnalisée. Si vous avez choisi le **standard** ou **Complete** installation, puis ignorez cette étape et passez à l’étape 7.  
  
    1.  Dans **installation personnalisée**, développez **Base adaptateurs** pour voir les adaptateurs disponibles.  
  
    2.  Pour les cartes que vous ne souhaitez pas, sélectionnez l’icône en regard de la carte, puis **totalité de cette fonctionnalité n’est pas disponible**.  
  
    3.  Développez **ADO fournisseurs**, puis sélectionnez les fournisseurs que vous ne souhaitez pas installer.  
  
    4.  Sélectionnez **Suivant**.  
  
7.  Sélectionnez **Installer**.  
  
8.  Dans **Customer Experience Improvement Program**, vous pouvez choisir de les inscrire. Si vous inscrivez, vous pouvez partager les données suivantes avec Microsoft :  
  
    -   Les données relatives au matériel de l’ordinateur sur lequel vous installez le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  
  
    -   Les données relatives aux versions enterprise application vous utilisez avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  
  
     Sélectionnez **OK**. [CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699) fournit plus d’informations.  
  
    > [!NOTE]
    >  Vous pouvez toujours modifier ce paramètre en exécutant le programme d’installation en mode de réparation à partir de **programmes**.  
  
9. Sélectionnez **Terminer**.  
  
<a name="BKMK_SilentInst"></a>   
### <a name="installing-the-biztalk-adapter-pack-in-silent-mode"></a>L’installation de BizTalk Adapter Pack en mode silencieux  
 Utilisez le **msiexec** commande pour effectuer une installation sans assistance. Dans le cadre de la commande msiexec, entrez les composants individuels que vous souhaitez installer. Le tableau suivant répertorie les valeurs pour chaque composant dans le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Utilisez ces valeurs pour installer (ou supprimer) des composants spécifiques. Pour installer (ou supprimer) plusieurs composants, vous pouvez utiliser une combinaison de ces valeurs séparées par une virgule.  
  
|Nom du composant|Valeur correspondante pour les propriétés de ligne de commande|  
|---|---|  
|[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]|DbFeature|  
|[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]|OracleEBSFeature|  
|[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]|SapBaseAdapterFeature|  
|[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]|SiebelBaseAdapterFeature|  
|[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]|SqlFeature|  
|[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]|SapAdoFeature<br /><br /> **Remarque**: vous devez fournir cette valeur uniquement si vous installez le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] également.|  
|[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]|SiebelAdoFeature<br /><br /> **Remarque**: vous devez fournir cette valeur uniquement si vous installez le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] également.|  
|Tous les composants|ALL|  
  
> [!IMPORTANT]
>  Les noms de fonctionnalités respectent la casse.  
  
 Les étapes suivantes vous montrent comment effectuer une installation silencieuse de [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] pour les différents composants.  
  
##### <a name="install-in-silent-mode"></a>Installer en mode silencieux  
  
1.  Ouvrez une invite de commandes et accédez à la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] racine dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.  
  
2.  Exécutez les commandes suivantes, selon ce que vous souhaitez installer :  
  
    > [!NOTE]
    >  Pour effectuer une installation sans assistance sur une plateforme x64 64, remplacez `AdaptersSetup.msi` avec `AdaptersSetup64.msi` dans les commandes suivantes.  
  
    -   Pour effectuer une installation complète, qui installe tous les adaptateurs, y compris les fournisseurs de données .NET Framework, tapez :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=ALL  
        ```  
  
    -   Pour installer uniquement le [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=DbFeature  
        ```  
  
    -   Pour installer uniquement le [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=OracleEBSFeature  
        ```  
  
    -   Pour installer uniquement le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature  
        ```  
  
    -   Pour installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] avec [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature  
        ```  
  
    -   Pour installer uniquement le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature  
        ```  
  
    -   Pour installer le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] avec [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature,SiebelAdoFeature  
        ```  
  
    -   Pour installer uniquement le [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SqlFeature  
        ```  
  
    -   Pour installer tous les adaptateurs de base, tapez :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SiebelBaseAdapterFeature,DbFeature,OracleEBSFeature,SqlFeature  
        ```  
  
    -   Pour installer les deux fournisseurs de données .NET Framework, tapez :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapAdoFeature,SiebelAdoFeature  
        ```  
  
    -   N’importe quel type d’installation personnalisée en répartissant les composants par une virgule. Par exemple, pour installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] avec la [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]et le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature,SiebelBaseAdapterFeature  
        ```  
  
    -   Vous pouvez également choisir d’inscrire pour CEIP dans le cadre de l’installation sans assistance. Type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn CEIP_OPTIN=true  
        ```  
  
         Par défaut, l’option est false. 
  
        > [!IMPORTANT]
        >  Lors de l’installation du [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] version d’évaluation en mode silencieux, l’option par défaut pour CEIP est true.  
  
     Pour plus d’informations sur le type de commande msiexec `msiexec` sur la ligne de commande et appuyez sur `ENTER`. Ou accédez à [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).
  
<a name="BKMK_PostInst"></a>   
### <a name="after-installing-the-biztalk-adapter-pack"></a>Après l’installation de BizTalk Adapter Pack  
 Vous devrez peut-être effectuer les tâches suivantes après avoir installé le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], basé sur les opérations que vous voulez faire avec chaque carte :  
  
-   [Configurez la carte de base de données Oracle pour utiliser une version plus récente de Oracle.DataAccess.dll](#BKMK_ConfigNewOracleDLL) dans le fichier de configuration OracleDB.  
  
-   [Créer des objets de base de données SQL Server (uniquement pour l’adaptateur SAP)](#BKMK_CreateSQLServer) pour appeler les RFC transactionnelles (tRFCs) dans un système SAP.  
  
-   [Inscrire des liaisons de l’adaptateur](#BKMK_Register_Bindings) et les fournisseurs de données .NET Framework si l’Assistant installation ne parvient pas à le faire.  
  
-   [Déterminer la clé publique et la Version](#BKMK_PubKey) des fichiers autre carte.  
  
-   [Installer les RFC personnalisés](#BKMK_InstallCustomRFC) si vous avez choisi d’installer le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].  
  
<a name="BKMK_ConfigNewOracleDLL"></a>   
#### <a name="configure-the-oracle-database-adapter-to-use-a-newer-oracledataaccessdll-version"></a>Configurez la carte de base de données Oracle pour utiliser une version plus récente de Oracle.DataAccess.dll  
 Lorsque vous configurez un port à utiliser l’adaptateur WCF-OracleDB ou utiliser Visual Studio pour consommer un adaptateur généré, un message s’affiche que l’adaptateur doit Oracle.DataAccess.dll version 2.111.7.0. Pour résoudre ce message, installez une version prise en charge de Oracle.DataAccess.dll (consultez [prise en charge de la liste des versions](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)), puis mettez à jour le `bindingRedirect` élément dans le fichier de configuration OracleDB. Étapes :  
  
1.  Sur le serveur BizTalk Server, accédez aux dossiers suivants :  
  
     *lecteur*: \Program Files\Microsoft BizTalk Adapter Pack (x64) \bin  
  
     *lecteur*: \Program fichiers (x86) \Microsoft BizTalk Adapter Pack\bin  
  
2.  Ouvrez le fichier Microsoft.Adapters.OracleDB.config.  
  
3.  Recherchez la section suivante et copier/coller les éléments suivants :  
  
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
>  -   S’il existe plusieurs serveurs BizTalk Server dans ce groupe, apporter cette modification sur tous les serveurs BizTalk du groupe.  
> -   Le *newVersion* valeur doit être mis à jour en fonction de la version du fichier Oracle.DataAccess.dll installé sur l’ordinateur.  Oracle.DataAccess.dll est inclus avec le Client Oracle que vous installez à partir d’Oracle.  Vous devez installer uniquement une version de Client Oracle est [pris en charge par BizTalk Adapter Pack](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx).  
  
<a name="BKMK_CreateSQLServer"></a>   
#### <a name="create-sql-server-database-objects-only-for-the-sap-adapter"></a>Créer des objets de base de données SQL Server (uniquement pour l’adaptateur SAP)  
 Pour appeler tRFCs dans un système SAP, exécutez le *SapAdapter-DbScript-Install.sql* script SQL. Ce script est installé avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation et crée des objets de base de données dans SQL Server. Le script est généralement installé sur \<lecteur d’installation\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Vous pouvez exécuter ce script sur toute base de données SQL Server, tant que vous entrez son nom de base de données lors de l’utilisation de l’adaptateur pour appeler tRFCs.  
  
<a name="BKMK_Register_Bindings"></a>   
#### <a name="register-the-adapter-bindings"></a>Inscrire des liaisons de l’adaptateur  
 Lors de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, l’Assistant installation peut échouer enregistrer des liaisons de l’adaptateur ou le fournisseur de données .NET Framework pour mySAP Business Suite, mais le programme d’installation poursuit l’installation de l’adaptateur. Cela peut entraîner des problèmes d’installation de Windows Communication Foundation (WCF), en raison de [!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)] installation ou dans le fichier machine.config est endommagé.  
  
Effectuez ces étapes *uniquement* si l’Assistant installation ne parvient pas à inscrire les liaisons de l’adaptateur ou les fournisseurs de données .NET Framework dans le fichier machine.config.  
  
###### <a name="register-the-adapter-bindings-or-the-net-framework-data-providers"></a>Inscrire des liaisons de l’adaptateur ou les fournisseurs de données .NET Framework  
  
1.  Accédez au fichier machine.config sur l’ordinateur. Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.  
  
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
    >  Pour plus d’informations sur la façon de déterminer la clé publique, consultez [déterminer la clé publique et la Version](#BKMK_PubKey).  
  
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
  
<a name="BKMK_PubKey"></a>   
#### <a name="determine-the-public-key-and-version"></a>Déterminer la Version et la clé publique  
 Effectuez les étapes suivantes pour déterminer la version d’un adaptateur ou le fournisseur de données .NET Framework et la clé publique.  
  
###### <a name="determine-the-public-key"></a>Déterminer la clé publique  
  
1.  Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.  
  
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
  
3.  Sur le **général** onglet, le **jeton de clé publique** valeurs est la clé publique pour la DLL. Le **Version** valeur est le numéro de version de la DLL.  
  
4.  Copiez la clé publique, puis **Annuler**.  
  
<a name="BKMK_InstallCustomRFC"></a>   
#### <a name="install-the-custom-rfcs"></a>Installez les RFC personnalisés  
 Vous ne devez effectuer cette tâche si vous souhaitez utiliser le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]. Pour obtenir des instructions sur l’installation de RFC personnalisés, consultez [installer les RFC personnalisés](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md) dans le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] documentation. 
  
> [!IMPORTANT]
>  Si vous utilisez une version antérieure des RFC personnalisés fournis avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], puis vous devez les mettre à niveau pour les documents RFC fournis avec cette version. Cela en supprimant les RFC antérieures, et ensuite l’installation des RFC inclus dans cette version.  

## <a name="installing-the-enterprise-applications"></a>Installer les Applications d’entreprise  
Pour les étapes et les instructions pour installer les systèmes métier entreprise différente, nous recommendnd que vous utilisez leur installation spécifique Guide. Également faire référence à la documentation de l’adaptateur pour les modifications de configuration spécifique, le cas échéant.   

## <a name="installation-and-post-installation-checklist"></a>Liste de vérification installation et après l’installation  
  
-   Assurez-vous que vous avez installé tous les [les composants logiciels requis](#BKMK_Prereqs) avec l’option d’installation correct.
  
-   Assurez-vous que vous disposez de la version prise en charge des applications métier enterprise installée sur votre ordinateur où vous avez installé le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Consultez [prise en charge des Versions des applications Enterprise](#BKMK_SuppLOB).  
  
-   Pour installer uniquement l’adaptateur pour le système métier que vous souhaitez vous connecter, vérifiez que vous avez installé le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] à l’aide de la **personnalisé** option d’installation. Assurez-vous que vous n’avez pas installé le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] à l’aide de la **Complete** option d’installation. Consultez [l’installation de BizTalk Adapter Pack](#BKMK_Install_Adap).  
  
-   Si vous souhaitez effectuer des appels tRFC au système SAP en utilisant le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], assurez-vous de créer les tables requises dans une base de données SQL Server. Consultez [après l’installation de BizTalk Adapter Pack](#BKMK_PostInst).
  
-   Lors de l’exécution du [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] Assistant installation, vous risquez d’obtenir un message d’erreur indiquant l’échec de la configuration inscrire les liaisons. Dans ce cas, inscrivez-le manuellement. Consultez [après l’installation de BizTalk Adapter Pack](#BKMK_PostInst).  
  
-   Si vous avez choisi d’installer le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)] dans le cadre de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, veillez à installer les RFC personnalisés sur le système SAP. Consultez [après l’installation de BizTalk Adapter Pack](#BKMK_PostInst).  
  
<a name="BKMK_Modify_Adap"></a>   
## <a name="change-the-biztalk-adapter-pack-installation"></a>Modifiez l’installation du Pack d’adaptateurs BizTalk  
 Effectuez les étapes suivantes pour modifier la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation. Assurez-vous que vous avez le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] installé avant d’exécuter l’Assistant Installation pour modifier le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.  
  
 Vous pouvez modifier le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation en mode interactif (l’Assistant d’installation), ou en mode silencieux (la ligne de commande).
  
#### <a name="change-the-bap-installation-in-interactive-mode"></a>Modifiez l’installation BAP en mode interactif  
  
1.  Connectez-vous à l’aide d’un compte qui est membre du groupe Administrateurs de BizTalk Server.  
  
2.  Dans **programmes et fonctionnalités**, sélectionnez **désinstaller un programme**.  
  
3.  Avec le bouton droit **Microsoft BizTalk Adapter Pack**, puis sélectionnez **modification**.  
  
4.  Dans l’écran de bienvenue, sélectionnez **suivant**.  
  
5.  Dans **modifier, réparer ou supprimer l’installation**:  
  
    -   Pour sélectionner les composants à installer, sélectionnez **modification** et accédez à l’étape 6.  
  
    -   Pour réparer les erreurs dans l’installation la plus récente, sélectionnez **réparer** et accédez à l’étape 7.  
  
    -   Pour supprimer Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] à partir de l’ordinateur, sélectionnez **supprimer** et passez à l’étape 10.  
  
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
  
#### <a name="change-the-bap-installation-in-silent-mode"></a>Modifier l’installation en mode silencieux BAP  
  
1.  Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] programme d’installation.  
  
2.  Exécutez une commande semblable à la suivante :  
  
    > [!NOTE]
    >  Pour modifier la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation en mode sans assistance sur une plateforme x64 64, les commandes suivantes, remplacez `AdaptersSetup.msi` avec `AdaptersSetup64.msi`.  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature ADDLOCAL=SapBaseAdapterFeature  
    ```  
  
     Cette commande supprime le [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]et installe le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].  
  
     À l’aide des valeurs différentes pour le `REMOVE` et `ADDLOCAL` propriétés, vous pouvez ajouter ou supprimer des composants spécifiques. Reportez-vous au tableau dans [l’installation de BizTalk Adapter Pack en Mode silencieux](#BKMK_SilentInst) (dans cette rubrique) pour plus d’informations sur les valeurs que vous pouvez utiliser pour ces propriétés.  
  
     Vous pourrez également effectuer une réparation en mode silencieux à l’aide de l’option /f dans le cadre de la commande msiexec. Par exemple :  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn /f  
    ```  
  
     Vous pouvez utiliser diverses combinaisons avec l’option /f. Pour plus d’informations sur le type de commande msiexec `msiexec` sur la ligne de commande, puis appuyez sur `ENTER`. Ou accédez à [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).  
  
    > [!IMPORTANT]
    >  Lors de la modification du [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation en mode silencieux, vous ne pouvez pas modifier vos préférences pour vous inscrire ou de refuser le CEIP. Les préférences de que celle choisie lors de l’installation reste, même si vous définissez explicitement la CEIP_OPTIN à true ou false.  
  
<a name="BKMK_Remove_Adap"></a>   
## <a name="removing-the-biztalk-adapter-pack"></a>Suppression du Pack de l’adaptateur BizTalk  
  
> [!IMPORTANT]
>  Si vous avez créé des tables dans la base de données SQL Server pour travailler avec la fonctionnalité tRFC de la [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], vous devez les supprimer manuellement avant de supprimer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation copie un fichier SapAdapter-DbScript-Uninstall.sql en général au \<lecteur d’installation\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Exécuter ce fichier pour supprimer les tables que vous avez créé.  
  
Effectuez les étapes suivantes pour supprimer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] à partir de votre ordinateur. Assurez-vous que vous avez le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] installé avant d’exécuter l’Assistant Installation pour supprimer les cartes.  
  
 Vous pouvez supprimer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] en mode interactif (Assistant Installation), ou en mode silencieux (ligne de commande).
  
#### <a name="uninstall-the-biztalk-adapter-pack-in-interactive-mode"></a>Désinstaller le Pack de l’adaptateur BizTalk en mode interactif  
  
1.  Dans **programmes et fonctionnalités**, sélectionnez **désinstaller un programme**.  
  
2.  Avec le bouton droit **Microsoft BizTalk Adapter Pack**, puis sélectionnez **désinstallation**.  
  
#### <a name="uninstall-the-biztalk-adapter-pack-in-silent-mode"></a>Désinstallation de BizTalk Adapter Pack en mode silencieux  
  
1.  Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] programme d’installation.  
  
2.  Exécutez la commande suivante :  
  
    > [!NOTE]
    >  Pour supprimer la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] en mode silencieux sur une plateforme x64 64, les commandes suivantes, remplacez `AdaptersSetup.msi` avec `AdaptersSetup64.msi`.  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature  
    ```  
  
     Cette commande supprime le [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)] à partir de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.  
  
     En fournissant des valeurs différentes pour le `REMOVE` propriété, vous pouvez supprimer des composants spécifiques à partir de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation. Reportez-vous au tableau dans [l’installation de BizTalk Adapter Pack en Mode silencieux](#BKMK_SilentInst) (dans cette rubrique) pour plus d’informations sur les valeurs que vous pouvez utiliser pour cette propriété.  
  
     Pour supprimer complètement le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], exécutez la commande suivante :  
  
    ```  
    msiexec /x AdaptersSetup.msi /qn  
    ```  
  
     Pour plus d’informations sur le type de commande msiexec `msiexec` sur la ligne de commande, puis appuyez sur `ENTER`. Ou accédez à [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).
  
<a name="BKMK_PostRemove"></a>   
### <a name="after-removing-the-biztalk-adapter-pack"></a>Après avoir supprimé le Pack d’adaptateurs BizTalk  
 Vous devrez peut-être effectuer les étapes suivantes après avoir supprimé le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]:  
  
-   Supprimer les liaisons de l’adaptateur ou l’inscription du fournisseur de données .NET Framework, si l’Assistant Installation a échoué pour ce faire
  
-   Supprimer les RFC personnalisés, si vous avez choisi d’installer le[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]
  
<a name="BKMK_Remove_Binding"></a>   
#### <a name="remove-the-bindings-or-the-net-framework-data-provider-registration"></a>Supprimer les liaisons ou l’inscription du fournisseur de données .NET Framework  
 Effectuez ces étapes *uniquement* si l’Assistant installation ne parvient pas à supprimer les liaisons de l’adaptateur ou l’inscription du fournisseur de données .NET Framework à partir du fichier machine.config.  
  
###### <a name="remove-the-adapter-bindings-or-net-framework-data-provider-registration"></a>Supprimer les liaisons de l’adaptateur ou l’inscription du fournisseur de données .NET Framework  
  
1.  Accédez au fichier machine.config sur l’ordinateur. Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.  
  
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
  
<a name="BKMK_Remove_SAP_Pro"></a>   
#### <a name="remove-the-custom-rfcs"></a>Supprimer les RFC personnalisés  
Effectuez cette étape pour supprimer les RFC personnalisés que vous avez installé dans le système SAP. Consultez [installer ou supprimer les RFC personnalisés](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).  
  
## <a name="troubleshoot-biztalk-adapter-pack-installation"></a>Résoudre les problèmes d’installation du Pack d’adaptateurs BizTalk  
 Voici certains problèmes que vous pouvez rencontrer lors de l’installation [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Pour une liste complète des problèmes d’installation, consultez **la résolution des problèmes** rubriques pour chaque adaptateur.  
  
-   **Le programme d’installation en cours d’exécution sur un ordinateur 64 bits peut lever une erreur lors de l’accès au fichier de schéma**  
  
     Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] le programme d’installation génère une erreur lors de l’accès à la **Microsoft.Adapters. *\<AdapterName\>*_schema.xml** fichier, mais se poursuit avec l’installation de l’adaptateur.  
  
     **Cause**  
  
     Si les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] sont installés sur le même ordinateur, le fichier de schéma cible utilisé par les deux est la même. Par conséquent, le fichier est installé par 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] peut être utilisé par IIS lorsque le programme d’installation 64 bits tente d’y accéder.  
  
     **Résolution**  
  
     Copiez manuellement le **Microsoft.Adapters. *\<AdapterName\>*_schema.xml** à partir du fichier `C:\Program Files\Microsoft BizTalk Adapter Pack(x64)\IIS Schemas`» à `C:\Windows\System32\inetsrv\config\schema`.  