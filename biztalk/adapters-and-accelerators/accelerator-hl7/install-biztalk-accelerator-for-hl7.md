---
title: Installer BizTalk Accelerator pour HL7 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52347742-f858-47bb-bc73-1a6095ea9e8e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ad01c0b3966985efdceea421de85778266a294c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-biztalk-accelerator-for-hl7"></a>Installer BizTalk Accelerator pour HL7

## <a name="hardware-and-software-requirements"></a>Configuration matérielle et logicielle requise

La configuration matérielle et logicielle minimale requise est identique à [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]. 

|  |Configuration requise pour BizTalk  |Configuration requise de SQL et du système d’exploitation |  
|---------|---------|--------- | 
| [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] | [Configurations logicielle et matérielle pour BizTalk Server 2016](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) | **Exigences matérielles et logicielles de SQL Server**: <br/>[SQL Server 2016](https://msdn.microsoft.com/library/ms143506(v=sql.130).aspx)<br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/><br/>**Configuration matérielle de Windows Server**: <br/>[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/server-basics)<br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx) |
| [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] <br/><br/> [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] 2013 | [Configurations matérielle et logicielle requises pour BizTalk Server 2013 et 2013 R2](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) |**Exigences matérielles et logicielles de SQL Server**: <br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/>[SQL Server 2012](https://msdn.microsoft.com/library/ms143506(v=sql.110).aspx)<br/>[SQL Server 2008 R2](https://msdn.microsoft.com/library/ms143506(v=sql.105).aspx)<br/><br/>**Configuration matérielle de Windows Server**: <br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)<br/>[Windows Server 2008 R2](https://technet.microsoft.com/library/dd379511(v=ws.10).aspx)  |

> [!TIP]
> La configuration matérielle répertoriée correspond au minimum nécessaire. Chaque environnement est différent et il est très probable que votre environnement nécessite plus. Consultez [recommandations pour l’installation, le dimensionnement, déploiement et maintenance d’une Solution BizTalk Server](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx)

## <a name="install-hl7"></a>Installer HL7

### <a name="before-you-begin"></a>Avant de commencer

* Les fichiers d’installation HL7 accelerator se trouvent dans `BizTalk Server <version>\BizTalk Accelerators` sur la [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] ISO, emplacement de téléchargement, le partage réseau, ou chaque fois que vous avez téléchargé le [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] programme.
* L’utilisateur de l’installation et la configuration [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] doit être membre du groupe Administrateurs de BizTalk et un membre du groupe Administrateurs sur le serveur SQL Server où le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] les données sont stockées.
* L’ordinateur et l’utilisateur connecté doivent avoir accès au contrôleur de domaine principal (PDC). Si le programme d’installation ne parvient pas à accéder au contrôleur de domaine principal, puis l’installation échoue et ne se poursuive.  
* BizTalk Server doit avoir les composants de base installé et configuré, y compris un hôte BizTalkServerApplication de 32 bits à la norme en dehors de la zone cartes, Enterprise Single Sign-on (SSO), le groupe et le Runtime.
* Lecture la [installation problèmes connus](../../adapters-and-accelerators/accelerator-hl7/installation-known-issues.md).
*  [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]est disponible dans les éditions Enterprise et Standard. Le tableau suivant indique la compatibilité entre les différentes éditions de [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
    |Édition de[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] |Édition compatible de[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]|  
    |---|---|  
    |Enterprise Edition|Enterprise Edition|  
    |Standard Edition|Édition Enterprise ou Standard|  
    |Developer Edition|Enterprise Edition|  

### <a name="default-installation"></a>Installation par défaut

1. Exécutez le [!INCLUDE[btaBTAHL7NoNumber_md](../../includes/btabtahl7nonumber-md.md)] (A4HL7) **setup.exe** en tant qu’administrateur. 
  
    > [!TIP]
    >  En commençant par [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)] et les versions ultérieures, le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] installation inclut un package d’installation 32 bits et un package d’installation 64 bits.
    > 
    > Sur un ordinateur 32 bits, installez uniquement le package 32 bits. Sur un ordinateur 64 bits, installez 32 bits **ou** package 64 bits. Le package 64 bits permet à l'adaptateur et aux pipelines de s'exécuter en mode 32 bits et 64 bits.  
  
2.  Dans la page de bienvenue, sélectionnez **suivant**.  
  
3.  Accepter la **contrat de licence**, puis sélectionnez **suivant**.  
  
4.  Entrez votre nom d’utilisateur et votre organisation, puis sélectionnez **suivant**.  
  
5.  Sélectionnez le **standard** le programme d’installation, puis sélectionnez **suivant**.  
  
6.  Le **compte de Service de journalisation** page fournit automatiquement les groupes suivants les autorisations de journalisation : 

  * Administrateurs BizTalk Server
  * Utilisateurs d'applications BizTalk
  * Opérateurs interentreprises BizTalk Server
  * Opérateurs BizTalk Server

    Sélectionnez **Suivant**. 

7. Passez en revue le résumé, puis sélectionnez **suivant**.  

8. Pour le **dossier de Destination**, sélectionnez **suivant** à utiliser le dossier par défaut. Ou bien, sélectionnez **modification** pour choisir un autre dossier d’installation. 

9. Dans **enregistrement des informations de base de données**, entrez les informations suivantes, puis sélectionnez **suivant**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom du serveur de base de données**|La valeur par défaut est le nom du serveur. <br/><br/>**Remarque** le nom du serveur par défaut est le nom de l’ordinateur sur lequel réside la base de données BizTalkMgmtDb. Vous ne pouvez pas modifier cette valeur.|  
    |**Nom de la base de données HL7**|Entrez le nom de la base de données qui contient les données pour votre [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] solution, ou acceptez le paramètre par défaut, qui est **BTAHL7**. <br/><br/>**Remarque** vous devez utiliser le caractère ANSI-ASCII défini par les exigences de la base de données ; [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] ne prend pas en charge les autres jeux de caractères.|  
    | **Tester la connexion** | Sélectionnez cette option pour confirmer la connectivité SQL Server. |
  
    > [!NOTE]
    >  Si la base de données déjà sélectionné existe, un message s’affiche. Sélectionnez **OK** pour continuer.  
    
10. Sélectionnez **Installer**.
  
11. Sélectionnez **Terminer** lorsque terminée.  
  
    > [!TIP] 
    > Sélectionnez **lancer le didacticiel** pour installer le didacticiel de bout en bout. 
    
### <a name="custom-installation"></a>Installation personnalisée
1. Exécutez le [!INCLUDE[btaBTAHL7NoNumber_md](../../includes/btabtahl7nonumber-md.md)] (A4HL7) **setup.exe** en tant qu’administrateur. 
  
    > [!TIP]
    >  En commençant par [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)] et les versions ultérieures, le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] installation inclut un package d’installation 32 bits et un package d’installation 64 bits. 
    > 
    > Sur un ordinateur 32 bits, installez uniquement le package 32 bits. Sur un ordinateur 64 bits, installez 32 bits **ou** package 64 bits. Le package 64 bits permet à l'adaptateur et aux pipelines de s'exécuter en mode 32 bits et 64 bits.  
  
2.  Dans la page de bienvenue, sélectionnez **suivant**.  
  
3.  Accepter la **contrat de licence**, puis sélectionnez **suivant**.  
  
4.  Entrez votre nom d’utilisateur et un mot de passe, puis **suivant**.  
  
5. Sélectionnez **personnalisé**, puis sélectionnez **suivant**.  
  
6.  Sélectionnez les fonctionnalités que vous souhaitez installer, puis sélectionnez **suivant**.  
  
    |Fonctionnalité|Sous-fonction| Description|Installation par défaut|Installation personnalisée|  
    |---|---|---|---|---|  
    |**Moteur**||Valide, traite et achemine les messages.<br /><br /> Vous devez être membre du groupe Administrateurs de BizTalk Server pour installer cette fonctionnalité.|✓|✓|  
    |**Moteur**|Composants du moteur|Processus [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] plate fichier et les messages encodés en XML.|✓|✓|  
    |**Moteur**|Traitement par lot sortant|Crée et achemine [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] traiter par lot des documents au format.|✓|✓|  
    |**Moteur**|Pipelines|Exemple de pipelines pour la génération de votre [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] solution.|✓|✓|  
    |**Adaptateur**||Utilitaires pour activer les connexions de point de terminaison.|✓|✓|  
    |**Adaptateur**|MLLP|Pour activer les connexions basées sur TCP à l’aide de l’adaptateur MLLP [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] protocole MLLP.|✓|✓|  
    |**Adaptateur**|Outil de Test MLLP|Tester l’outil qui émule basée sur MLLP envoyer et recevoir des applications clientes sur des connexions basées sur TCP.|||  
    |**Schémas**||Sélection de HL7 V2. Fichier plat X en fonction des schémas XSD.|✓|✓|  
    |**Artefacts**||Outils permettant de travailler avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] artefacts.||✓|  
    |**Artefacts**|Orchestration|Un exemple d’orchestration que vous pouvez utiliser pour générer votre [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] solution.||✓|  
    |**Autres composants**|Instances de test|Exemple/tester les données que vous pouvez utiliser comme point de départ pour votre [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] solution.|||  
    |**Autres composants**|-|Autres composants de [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)].|✓|✓|  
    |**Autres composants**|Explorateur de configuration|Application que vous utilisez pour définir la journalisation pour les magasins de données, configurez la validation propres au tiers, mappage d’en-tête, le traitement par lot et exigences de l’accusé de réception.|✓|✓|  
    |**Autres composants**|SDK|Contient des utilitaires pour les schémas XML de 2 HL7, telles que les composants et les artefacts nécessaires pour le didacticiel de bout en bout et la MLLP utilitaires.|✓|✓|  
    |**Autres composants**|Fonctionnalités de journalisation|Les composants qui prennent en charge la journalisation des [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] événements.|✓|✓|  
    |**Autres composants**|Projet de démarrage|Plug-in pour [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] qui permet de [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] projet de développement.|✓|✓|  
  
7. Dans **compte de Service de journalisation**, entrez les informations suivantes, puis sélectionnez **suivant**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom du compte**|Entrez le nom de compte que vous souhaitez utiliser pour démarrer le Service de journalisation.|  
    |**Mot de passe**|Entrez le mot de passe pour ce compte.|  
    |**Domaine**|Entrez le nom de domaine pour ce compte.|  
  
8. Lorsque vous y êtes invité **le nom du compte a été accordé d’ouverture de session en tant que service droit**, sélectionnez **OK**.  
  
9. Passez en revue le résumé, puis sélectionnez **suivant**.  
  
10. Pour le **dossier de Destination**, sélectionnez **suivant** à utiliser le dossier par défaut. Ou bien, sélectionnez **modification** pour choisir un autre dossier d’installation.
  
11. Dans **enregistrement des informations de base de données** page, entrez les informations suivantes, puis sélectionnez **suivant**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom du serveur de base de données**|La valeur par défaut est le nom du serveur. <br/><br/>**Remarque** le nom du serveur par défaut est le nom de l’ordinateur sur lequel réside la base de données BizTalkMgmtDb. Vous ne pouvez pas modifier cette valeur.|  
    |**Nom de la base de données HL7**|Entrez le nom de la base de données qui contient les données pour votre [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] solution, ou acceptez le paramètre par défaut ; c'est-à-dire **BTAHL7**. <br/><br/> **Remarque** vous devez utiliser le caractère ANSI-ASCII défini par les exigences de la base de données ; [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] ne prend pas en charge les autres jeux de caractères.|  
  
12. Sélectionnez **Installer**.  
  
15. Sélectionnez **Terminer** lorsque terminée.  
  
    > [!TIP] 
    > Sélectionnez **lancer le didacticiel** pour installer le didacticiel de bout en bout.   
    
## <a name="next-steps"></a>Étapes suivantes
Parcourez quelques didacticiels à [prise en main BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md).