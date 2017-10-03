---
title: Configuration logicielle requise pour BizTalk adaptateur Pack 2016 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65a063ca-37ae-420b-9d48-e6730caf17e3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0b33203d1e8e5b36c9fb8a54167c111a427b244
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="software-prerequisites-for-biztalk-adapter-pack-2016"></a>Configuration logicielle requise pour BizTalk adaptateur Pack 2016
Répertorie la configuration logicielle requise pour Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] (LOB) inclus avec [!INCLUDE[bts2016_md](../includes/bts2016-md.md)].
  
Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] peuvent être utilisés à partir de :  
  
-   Une application .NET  
  
-   Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   Une interface ADO  
  
-   Un portail de Microsoft SharePoint  
  
 Selon la façon dont vous utilisez les adaptateurs, les logiciels requis varient.  
  
## <a name="prerequisites-when-using-a-net-application"></a>Configuration requise lors de l’utilisation d’une application .NET  
Lorsque vous utilisez une application .NET pour consommer les adaptateurs, les logiciels suivants sont requis sur votre ordinateur de développement (l’ordinateur sur lequel vous créez l’application .NET). Installer le logiciel dans l’ordre indiqué.
  
|BizTalk Adapter Pack 2016|
|---|
|<ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1  </li></ul>|
|.NET Framework 4.6.*x*|
|Visual Studio 2015|
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|
|Les clients d’application d’entreprise et les logiciels associés. Consultez **prise en charge des versions des applications enterprise** (dans cette rubrique).|

## <a name="prerequisites-when-using-biztalk-server"></a>Configuration requise lors de l’utilisation de BizTalk Server  
Lorsque vous utilisez un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour consommer les adaptateurs, les logiciels suivants sont requis sur votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Installer le logiciel dans l’ordre indiqué.
 
|BizTalk Adapter Pack 2016|
|---|
|<ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1  </li></ul>|
|.NET Framework 4.6.*x*|
|Visual Studio 2015|
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]<br /><br /> Installer le [!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)] pour [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] inclus avec le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]. Pour installer, procédez comme un **personnalisé** (sélectionnez **du complément de BizTalk Server**) ou **Complete** installation de le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].|
|[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]|
|Les clients d’application d’entreprise et les logiciels associés. Consultez **prise en charge des versions des applications enterprise** (dans cette rubrique).|

## <a name="prerequisites-when-using-ado"></a>Configuration requise lors de l’utilisation d’ADO  
 Le  **[!INCLUDE[adaptersap](../includes/adaptersap-md.md)]**  et  **[!INCLUDE[adaptersiebel](../includes/adaptersiebel-md.md)]**  inclure une couche d’ADO ( *[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]*  et  *[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]* ) qui peuvent utiliser pour écrire un client ADO.NET pour se connecter à un système SAP ou le système Siebel. Vous pouvez également utiliser la couche d’ADO avec SQL Server Integration Services (SSIS) pour importer et exporter des données à partir de l’application métier et SQL Server Reporting Services (SSRS) pour générer des rapports pour présenter les données à partir des systèmes métier.  
  
> [!NOTE]
>  À l’aide du fournisseur ADO avec SSRS est prise en charge uniquement pour les [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].  
  
Le logiciel suivant est requis sur l’ordinateur qui utilise le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] avec une interface ADO. Installer le logiciel dans l’ordre indiqué.  

|BizTalk Adapter Pack 2016|
|---|
|<ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1  </li></ul>|
|.NET Framework 4.6.*x*|
|Visual Studio 2015|
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|
|<ul><li>Microsoft SQL Server 2016</li><li>Microsoft SQL Server 2014 SP1</li></ul> |
|Les clients d’application d’entreprise et les logiciels associés. Consultez **prise en charge des versions des applications enterprise** (dans cette rubrique).|

## <a name="prerequisites-when-using-sharepoint"></a>Configuration requise lors de l’utilisation de SharePoint  
L’objectif de l’utilisation des adaptateurs Microsoft SharePoint doit afficher les données à partir d’une application métier dans un portail SharePoint.  
  
Une installation par défaut avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] et SharePoint peut utiliser un seul ordinateur ou utiliser des ordinateurs distincts pour différentes tâches. Le tableau suivant répertorie la configuration logicielle requise pour chaque ordinateur. Si vous utilisez un seul ordinateur, tous les logiciels doivent être installé sur cet ordinateur. Installer le logiciel dans l’ordre indiqué.  
  
|Ordinateur sur lequel vous exécutez l’Assistant développement d’adaptateurs WCF|Ordinateur sur lequel vous hébergez le service WCF|Ordinateur sur lequel vous pouvez utiliser SharePoint Designer pour définir les Types de contenu externe| 
|---|---|---|  
|<ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1</li><br/><br/><li>.NET Framework 4.6.*x*</li><br/><br/><li>Visual Studio 2015</li><br/><br/><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><br/><br/><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><br/><br/><li>Les clients d’application d’entreprise et les logiciels associés. Consultez **prise en charge des versions des applications enterprise** (dans cette rubrique).</li></ul> | <ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1</li><br/><br/><li>.NET Framework 4.6.*x*</li><br/><br/><li>Visual Studio 2015</li><br/><br/><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><br/><br/><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><br/><br/><li>Les clients d’application d’entreprise et les logiciels associés. Consultez **prise en charge des versions des applications enterprise** (dans cette rubrique).</li><br /><br /><li>La version d'Internet Information Services (IIS) fournie avec le système d'exploitation. [Ko 224609](https://support.microsoft.com/kb/224609) répertorie les versions.</li> </ul>| Kit de développement logiciel de Microsoft SharePoint (SDK)|
  
<a name="BKMK_SuppLOB"></a>   
## <a name="supported-enterprise-application-versions"></a>Versions d’application pris en charge d’entreprise  
Pour connaître les versions de système LOB spécifiques qui sont pris en charge par BizTalk Adapter Pack, consultez  **[systèmes de prise en charge de métier (LOB)](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx)**.

Cette section répertorie des informations supplémentaires pour chaque adaptateur, comme n’importe quel client DLL requis pour chaque carte.  
  
### <a name="oracle-database-adapter"></a>Adaptateur de base de données Oracle  
  
-   Facultatif : Si vous utilisez des transactions distribuées avec la base de données Oracle, installez **Oracle Services pour Microsoft Transaction Server** (qui fait partie de l’installation du client Oracle) sur l’ordinateur exécutant le client de la carte.  
  
-   Pour votre application de fonctionner avec la version la plus récente de ODP.NET, installez le **stratégie DLL** et inscrire les DLL dans le GAC. Consultez [le fournisseur de données Oracle pour .NET FAQ](http://www.oracle.com/technetwork/database/windows/faq-093106.html).  

### <a name="oracle-e-business-adapter"></a>Adaptateur Oracle E-Business  
  
-   Facultatif : Pour utiliser les transactions distribuées avec la base de données Oracle, installez **Oracle Services pour Microsoft Transaction Server** (qui fait partie de l’installation du client Oracle) sur l’ordinateur exécutant le client de la carte.  
  
-   Pour votre application de fonctionner avec la version la plus récente de ODP.NET, installez le **stratégie DLL** et inscrire les DLL dans le GAC. Consultez [le fournisseur de données Oracle pour .NET FAQ](http://www.oracle.com/technetwork/database/windows/faq-093106.html).  
  
### <a name="sap-adapter"></a>Adaptateur SAP  
  
-   Le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] requiert la version Unicode du SDK RFC indépendamment de si le système SAP est Unicode ou non-Unicode.  
  
-   **Pilotes requis**: le tableau suivant répertorie les DLL requises par le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] pour interagir avec le système SAP :  
  
    |Version du client SAP|Pilotes requis|  
    |---|---|  
    |7.2|- **UNICODE DU KIT DE DÉVELOPPEMENT LOGICIEL RFC 7.10 SAP**. Cette option est disponible dans le cadre de SNOTE<sup> * </sup> 27517. Les instructions pour télécharger le Kit de développement sont disponibles dans [http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691). Après avoir téléchargé et extrait le Kit de développement, vous pouvez copier toutes les DLL dans les dossiers \rfcsdk\bin et \rfcsdk\lib vers l’emplacement pertinent mentionné précédant cette table. <br /> <br /> -DLL sont disponibles à partir de SAP dans le cadre de **R3DLLINST.zip**. Il contient des DLL d’exécution de Microsoft et peut être téléchargé à partir du site SAP. Consultez SNOTE<sup> * </sup> 684106 pour plus d’informations. Vous pouvez télécharger le fichier .zip de [http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693). Ce lien a une option « Pièces jointes » à partir duquel vous pouvez télécharger le package.<br /><br /> -Microsoft Visual C++ les DLL d’exécution requis pour les clients SAP 7.1 sont disponibles sur les liens suivants :<br /><br /> - **Pour les clients de SAP 7.1 32 bits**: Vcredist_x86.exe de [http://go.microsoft.com/fwlink/?LinkId=107086](http://go.microsoft.com/fwlink/?LinkId=107086).<br /><br /> -                                 **Pour les clients SAP 7.1 de 64 bits**: Vcredist_x64.exe à partir de [http://go.microsoft.com/fwlink/?LinkId=107087](http://go.microsoft.com/fwlink/?LinkId=107087).<br /><br /> -Si vous utilisez des Communications de réseau sécurisée (SNC) SAP pour se connecter à un système SAP, vous devez également les DLL appropriées à partir de SAP. Ces DLL sont différentes pour les plateformes 32 bits et 64 bits et sont disponibles avec SNOTE<sup> * </sup> 352295. Vous pouvez télécharger les DLL à partir de [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032). Ce lien a une option « Pièces jointes » à partir duquel vous pouvez télécharger le package. Les noms de DLL sont :<br /><br /> - **Pour 32 bits**: gsskrb5.dll, gssntlm.dll<br /><br /> - **Pour 64 bits x86**: gx64krb5.dll, gx64ntlm.dll|  
  
     > [!TIP]
     > SNOTEs sont les notes de publication qui accompagnent les correctifs disponibles par SAP.  

    La plupart des packages qui contiennent ces DLL doit être téléchargée à partir de SAP Service Marketplace. Pour obtenir les téléchargements à partir de SAP Service Marketplace : 
  
    1.  Installer le Gestionnaire de téléchargement disponible à partir de SAP Service Marketplace.  
  
    2.  Configurer le Gestionnaire de téléchargement à l’aide de vos informations d’identification pour le système SAP Service Marketplace.  
  
    3.  Être autorisé par l’administrateur SAP dans votre organisation pour télécharger le logiciel à partir du site Web du service SAP. Cela est nécessaire, car l’accès au centre de Distribution de logiciels SAP est restreint par un objet d’autorisation de télécharger le logiciel. Cela garantit que le logiciel est téléchargé uniquement par les utilisateurs autorisés.  
  
    4.  Installer le programme SAPCAR ne, ce qui est requis pour extraire les fichiers des packages que vous téléchargez à partir de SAP Service Marketplace. SAPCAR n’est également disponible à partir de SAP Service Marketplace.  
  
     Pour la version 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], vous devez disposer les versions correspondantes de 32 bits et 64 bits de ces DLL.  
  
    -   Sur un ordinateur 32 bits, la version 32 bits des DLL doit être ajoutée au dossier C:\Windows\System32.  
  
    -   Sur un ordinateur 64 bits, la version 32 bits des DLL doit être ajoutée au dossier C:\Windows\SysWow64. La version 64 bits des DLL doit être ajoutée au dossier C:\Windows\System32.  
    
    
### <a name="siebel-adapter"></a>Adaptateur Siebel  
Aucune étape supplémentaire.
  
### <a name="sql-adapter"></a>Adaptateur SQL  
  
**Pilotes requis** pour SQL Server 2014 :  
  
-   Si vous utilisez les UDT fournis avec les versions de SQL Server, par exemple, géographie, assurez-vous que les DLL suivantes sont présentes sur l’ordinateur où vous utilisez l’adaptateur pour effectuer des opérations sur SQL Server. Par exemple, si vous créez des projets BizTalk pour effectuer des opérations sur SQL Server, ces DLL doit être présent sur l’ordinateur sur lequel BizTalk Server est en cours d’exécution.  
  
    -   Assurez-vous que Microsoft.SqlServer.Types.dll est ajouté au GAC.  
  
    -   Assurez-vous que SqlServerSpatial.dll est disponible dans le dossier System32.    
        
    Vous pouvez installer ces DLL sur l’ordinateur en exécutant le programme d’installation de SQL Server et en sélectionnant **outils de gestion – de base** et **outils de gestion – complet** dans la **sélection des fonctionnalités**page de l’Assistant.          
  
-   Si vous utilisez l’adaptateur pour effectuer des opérations sur des colonnes de types de données FILESTREAM, assurez-vous que vous avez SQL Client Connectivity SDK est installé. Vous pouvez installer le SDK de connectivité Client SQL, exécutez le programme d’installation de SQL Server et sélectionnez **SQL Client Connectivity SDK** dans les **sélection des fonctionnalités** page de l’Assistant. L’adaptateur utilise le sqlncli10.dll, installé avec le SDK de connectivité Client SQL, pour effectuer des opérations FILESTREAM.  

-   Si vous créez votre propre UDT dans SQL Server, assurez-vous que les assemblys respectives pour les UDT sont ajoutés dans le GAC.

## <a name="64-bit-host-instance-support"></a>prise en charge des instances hôte 64 bits

L’adaptateur Siebel est pris en charge dans une instance d’hôte 32 bits. Il n’est pas pris en charge pour exécuter l’adaptateur Siebel dans une instance d’hôte 64 bits. 

Toutes les autres cartes peuvent s’exécuter dans une instance d’hôte 32 bits ou 64 bits. 
  
 Pour plus d’informations sur les scénarios d’installation pris en charge pour l’installation 32 bits et 64 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], consultez **32 bits et 64 bits de scénarios installent** à [BAP d’installation](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md).  
 
## <a name="next-step"></a>Étape suivante
[Installer BizTalk Adapter Pack](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md)  
