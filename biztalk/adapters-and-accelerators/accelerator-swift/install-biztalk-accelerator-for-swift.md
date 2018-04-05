---
title: Installer BizTalk Accelerator pour SWIFT | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- documentation
ms.assetid: 8d492248-fde6-4fd8-be6b-e86ac7d0808b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94e28d5dac74bdbceb0fe4938810779d6ccb5c52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-biztalk-accelerator-for-swift"></a>Installer BizTalk Accelerator pour SWIFT
Installer [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)] sur le serveur BizTalk. 

\<!---Texte précédent
-   [Guide d’installation de BizTalk Accelerator pour SWIFT](http://go.microsoft.com/fwlink/?LinkId=198120)    
-   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Lisezmoi, situé dans le Files\Microsoft BizTalk Accelerator pour SWIFT \Documentation dossier.  
-->

## <a name="hardware-and-software-requirements"></a>Configuration matérielle et logicielle requise

La configuration matérielle et logicielle minimale requise est identique à [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].

|  |Configuration requise pour BizTalk  |Configuration requise de SQL et du système d’exploitation |  
|---------|---------|--------- | 
| [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] | [Configurations logicielle et matérielle pour BizTalk Server 2016](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) | **Exigences matérielles et logicielles de SQL Server**: <br/>[SQL Server 2016](https://msdn.microsoft.com/library/ms143506(v=sql.130).aspx)<br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/><br/>**Configuration matérielle de Windows Server**: <br/>[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/server-basics)<br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx) |
| [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] <br/><br/> [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] 2013 | [Configurations matérielle et logicielle requises pour BizTalk Server 2013 et 2013 R2](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) |**Exigences matérielles et logicielles de SQL Server**: <br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/>[SQL Server 2012](https://msdn.microsoft.com/library/ms143506(v=sql.110).aspx)<br/>[SQL Server 2008 R2](https://msdn.microsoft.com/library/ms143506(v=sql.105).aspx)<br/><br/>**Configuration matérielle de Windows Server**: <br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)<br/>[Windows Server 2008 R2](https://technet.microsoft.com/library/dd379511(v=ws.10).aspx)  |

> [!TIP] 
> La configuration matérielle répertoriée correspond au minimum nécessaire. Chaque environnement est différent et il est très probable que votre environnement nécessite plus. Consultez [Recommandations pour l’installation, le dimensionnement, le déploiement et la maintenance d’une solution BizTalk Server](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx). 

## <a name="install-swift"></a>Installer SWIFT

### <a name="before-you-begin"></a>Avant de commencer

* Connectez-vous à l’aide d’un compte qui est membre de la le groupe d’administrateurs BizTalk Server. 
* Dans le téléchargement de BizTalk Server, le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] le programme d’installation est dans le `\BizTalk Accelerators` dossier.
* BizTalk Server doit être installé, et SQL Server doit être en cours d’exécution.
* Une installation sans assistance est prise en charge, mais n’est pas recommandée en raison de la complexité des étapes de configuration supplémentaires sont nécessaires.
* Le programme d’installation d’A4SWIFT s’exécute toujours avec le `/InstallPlatform` argument. Par conséquent, le programme d’installation installe toujours msvcr71.dll mfc71u.dll, msvcp71.dll et atl71.dll, qui sont requis pour Visual Studio. Le programme d’installation installe ces fichiers DLL dans le `%WINDIR%\System32` dossier, si les DLL ont été précédemment installés.

### <a name="default-installation"></a>Installation par défaut

1. Exécutez le [!INCLUDE[btaA4SWIFTNoVersion_md](../../includes/btaa4swiftnoversion-md.md)] **setup.exe** en tant qu’administrateur.
2. Sélectionnez **Installer**.
3. Entrez votre **nom d’utilisateur**, votre **organisation** et votre clé de produit. Sélectionnez **Suivant**.
4. Lisez le contrat de licence, puis sélectionnez **accepter**.
5. Sélectionnez **Complete**, puis sélectionnez **suivant**.
6. Examinez le **Résumé** page. Pour apporter des modifications, sélectionnez **précédent**.

    Pour activer la connexion automatique après un redémarrage système, sélectionnez **Définir** et entrez le compte de connexion. Cette option est activée uniquement lors de l’installation. Une fois le programme d’installation terminé, ce paramètre est désactivé.

    Sélectionnez **Installer**.
 
7. Sélectionnez **Terminer** lorsque vous avez terminé. Un fichier de journal d’installation est généré dans un dossier temporaire, similaire à : `C:\Users\username\AppData\Local\Setup(111016 xxxxxx).log`.

> [!NOTE] 
> Si **exécuter l’Assistant Configuration** est sélectionné dans la page Installation terminée, le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Assistant Configuration s’exécute automatiquement lorsque vous cliquez sur **Terminer**. 


### <a name="custom-installation"></a>Installation personnalisée

1. Exécutez le [!INCLUDE[btaA4SWIFTNoVersion_md](../../includes/btaa4swiftnoversion-md.md)] **setup.exe** en tant qu’administrateur.
2. Sélectionnez **Installer**.
3. Entrez votre **nom d’utilisateur**, votre **organisation** et votre clé de produit. Sélectionnez **Suivant**.
4. Lisez le contrat de licence, puis sélectionnez **accepter**.
5. Sélectionnez **personnalisé**, puis sélectionnez **suivant**.
6. Sélectionnez vos composants, puis **suivant**:

    | Sélectionnez cette option | Pour effectuer cette opération |
    | --- | --- |
    | Composants A4Swift | Requis pour le processus (résolution de schéma, l’analyse, validation) de messages SWIFT avec BizTalk Server |
    | Réparation de message et le rapprochement | Installer des pipelines, des orchestrations et schémas d’exécution. Crée la base de données A4SWIFT dans SQL Server pour la messagerie, de réparation et rapprochement. |
    | Composants Web pour message repair et new submission | Installe le composant pour Message Repair et New Submission qui créent des services web pour la validation, la sécurité de certificat, l’historique et la recherche BIC. |
    | Kit de développement logiciel (SDK) | Inclut les projets de code et starter kits exemple source pour Visual Studio. | 
    | Utilitaire de déploiement BRE | Utilitaire pour le déploiement de stratégies du moteur de règles d'entreprise (BRE) associées à des types de messages SWIFT déjà déployés. |
    | Didacticiel | Iincludes des instructions et des exemples pour le développement d’une solution rapide dans BizTalk Server. |
    | Outils | Inclut des outils pour le développement d’A4SWIFT. |
    | Source | Installe des exemples de code source pour le développement d’A4SWIFT. |
    
6. Examinez le **Résumé** page. Pour apporter des modifications, sélectionnez **précédent**.

    Sélectionnez **Installer**.
 
7. Sélectionnez **Terminer** lorsque vous avez terminé. Un fichier de journal d’installation est généré dans un dossier temporaire, similaire à : `C:\Users\username\AppData\Local\Setup(111016 xxxxxx).log`.

> [!NOTE]
> Si **exécuter l’Assistant Configuration** est sélectionné dans la page Installation terminée, le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Assistant Configuration s’exécute automatiquement lorsque vous cliquez sur **Terminer**. 

## <a name="next-steps"></a>Étapes suivantes
[Configurer BizTalk Accelerator pour SWIFT](../../adapters-and-accelerators/accelerator-swift/configure-biztalk-accelerator-for-swift.md)