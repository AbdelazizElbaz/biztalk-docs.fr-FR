---
title: "Mise à niveau de BizTalk Accelerator pour SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ede2af21-4c7d-4f9e-b255-1ada86eda68d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c4e95d248103d99b4b7f50dc925fb220211530f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="upgrade-biztalk-accelerator-for-swift"></a>Mise à niveau de BizTalk Accelerator pour SWIFT
Mise à niveau [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)] sur le serveur BizTalk. 

### <a name="before-you-upgrade"></a>Avant la mise à niveau

* L’utilisateur qui exécute la mise à niveau doit être un membre du groupe Administrateurs de BizTalk Server.
* Le service SQL Server (MSSQLSERVER) doit être en cours d’exécution lorsque vous effectuez un [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] mise à niveau.
* N’exécutez pas une installation sans assistance de mise à niveau vers [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)].
* Mise à niveau de BizTalk Server, puis mettre à niveau [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)].
* L’exécution de BizTalk Server doit être installée pour le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] mise à niveau pour installer les composants d’exécution. Si l’exécution de BizTalk Server n’est pas installée avant le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] mise à niveau, puis le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] composants ne seront pas installé, et les assemblys précédentes à partir du Global Assembly Cache (GAC) sont supprimés.
* Lorsque vous installez [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], le MessagePack est installé. Les versions existantes de la MessagePack sont remplacées pendant la mise à niveau.
* Mise à niveau vers [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] en exécutant la [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] installation. Le programme d’installation migre existants [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] informations de configuration. 
* La mise à niveau ne pouvez pas supprimer les raccourcis et les dossiers des toutes les fonctionnalités déconseillées.

## <a name="supported-upgrade-paths"></a>Chemins de mise à niveau pris en charge  
 Le tableau suivant répertorie la prise en charge [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] versions qui peuvent être mis à niveau. « Oui » signifie que la version peut être mis à niveau. « Non » signifie que la version ne peut pas être mis à niveau. Si le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] version n’est pas répertoriée, cette version ne peut pas être mis à niveau.  

||[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]|[!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)]|BizTalk Server 2013|
|---|---|---|---|  
|[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] 2013|Oui|Oui|Non|  
|[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] 2010|Non|Oui|Oui|  


## <a name="upgrade-a4swift"></a>Mise à niveau A4SWIFT

1. Sauvegardez le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] base de données et votre SWIFT schémas de message. Les mises à niveau du programme installation le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] base de données.

2. Sauvegardez tous les fichiers dans le `%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT` et `%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT MessagePack` dossiers que vous avez mis à jour.
  
3. Annuler le déploiement des projets, les artefacts BizTalk ou les assemblys qui ont des références à un de le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] MessagePack assemblys.

4. Dans Visual Studio, manuellement annuler le déploiement de tous les [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] assemblys dans l’ordre suivant :

* Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration
* Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas
* Microsoft.Solutions.FinancialServices.SWIFT.MrsrService
* Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.

5. Exécutez le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] le programme d’installation pour mettre à niveau.

> [!NOTE] 
> Lorsque vous mettez à niveau [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], la mise à niveau supprime les autorisations d’accès pour le **A4SWIFT administrateurs** et **A4SWIFT utilisateurs** de groupes à partir du `%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT\Service` dossier.         
        
## <a name="post-upgrade-steps"></a>Étapes post-mise à niveau

1. À l’aide de [BTSTask.exe](../../core/btstask-command-line-reference.md) (%programfiles%\Microsoft BizTalk Server), redéployez manuellement les assemblys A4SWIFT dans l’ordre suivant :
* Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas
* Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration

    > [!NOTE]
    > Il est inutile de redéployer `Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas`. L’installation redéploie cet assembly.

    > [!IMPORTANT] 
    > Avant de régénérer et redéployer votre projet de schémas dans l’étape précédente, supprimer les anciennes versions de `A4SWIFT Base Types.xsd` et `SWIFT Common Data Types.xsd` à partir du projet de schéma, remplacez-les par les versions de Message Pack de ces schémas, puis créer et déployer les schémas projet. Si vous ne substituez pas ces schémas, vous ne serez pas en mesure de générer et déployer le projet de schémas.

2. Régénérer et déployer des projets ou assemblys que vous avez utilisé avec les versions antérieures de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] ou Message Pack.
3. Si vous avez apporté des modifications aux schémas de Message SWIFT Pack, apportez ces modifications dans les nouveaux schémas de Message Pack, puis créer et déployer ces schémas.
4. Annuler le déploiement des stratégies BRE existantes qui ont été installés avec les versions précédentes de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]. Puis installer et déployer les stratégies correspondantes plus récente à partir de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] les fichiers d’installation. Faire cela manuellement ou à l’aide de la **BREDeployment** outil.

    > [!NOTE] 
    > Bien que le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] mise à niveau ne provoque pas les problèmes avec les fonctionnalités du moteur de règles d’entreprise (BRE), nous vous conseillons de remplacer les versions précédentes de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] stratégies BRE avec les dernières stratégies Message Pack BRE, comme certaines stratégies BRE mis à jour pour chaque Message Pack.
    
5. Si vous avez personnalisé les fichiers dans le `%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT` dossier, puis appliquer les mêmes modifications pour les versions plus récentes.
6. Supprimer **a4swift_limited** en tant que membre du rôle db_denydatareader, comme suit :
    1. Ouvrez SQL Server Management Studio. Dans Management Studio, développez **bases de données**, développez **BizTalk Accelerator pour SWIFT**, puis sélectionnez **rôles**.
    2. Double-cliquez sur **a4swift_limited**. Sélectionnez **autorisations**et activez pour `Bic11` et `Bic10`. Sélectionnez **OK**et fermer les propriétés.
    3. Double-cliquez sur **db_denydatareader**. Dans le champ utilisateur, sélectionnez **a4swift_limited**, puis sélectionnez **supprimer**. Sélectionnez **OK**.

7. Exécutez le script QFERollUpDBUpdate :

    > [!NOTE]
    > Vous devez être un membre de la **A4Swift administrateurs** groupe pour exécuter le script QFERollUpDBUpdate.
    
    1. Ouvrez SQL Server Management Studio. Dans Management Studio, cliquez sur Nouvelle requête. 
    2. Sélectionnez le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] base de données à partir de la liste déroulante. 
    3. Dans l’Explorateur Windows, accédez à `%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT\Scripts`et faites glisser le **QFERollUpDBUpdate.sql** de fichiers dans le nouveau volet de requête, puis sélectionnez **Execute**.
    
    
## <a name="upgrading-in-a-multi-server-environment"></a>La mise à niveau dans un environnement multiserveur

Dans un multi-serveur [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] environnement, sur tous les serveurs, mise à niveau de BizTalk Server, puis mettre à niveau [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]. Migrez vos serveur dans l'ordre suivant :

* Le serveur hébergeant le groupe BizTalk
* Chaque nœud de traitement
* Le serveur du portail BAM


## <a name="next-steps"></a>Étapes suivantes
[Configurer BizTalk Accelerator pour SWIFT](../../adapters-and-accelerators/accelerator-swift/configure-biztalk-accelerator-for-swift.md)