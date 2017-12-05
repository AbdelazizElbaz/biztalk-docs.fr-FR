---
title: "Vue d’ensemble du scénario | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac14328d-c373-49da-a899-4b3ca7d6dc0a
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab36aa51d2dd28651895818caa781c49bf366f50
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="scenario-overview"></a>Vue d’ensemble du scénario
Cette rubrique fournit une vue d’ensemble de tests de charge terminée par le serveur BizTalk groupe produit afin d’évaluer l’évolutivité de BizTalk Server lors de l’exécution sur du matériel d’entreprise modernes.  
  
 Tous les tests a été effectuée dans un environnement isolé à l’aide d’un matériel dédié. Plus de 200 des séries de tests ont été effectuées et tous les résultats ont été validés par le groupe de produits BizTalk Server.  
  
 Les tests ont été effectuées à l’aide d’un scénario de messagerie et un scénario d’Orchestration ; les deux scénarios utilisées de l’adaptateur BizTalk WCF-NetTcp.  
  
 Pour évaluer les performances maximales possibles du moteur de BizTalk Server, aucun composant de pipeline personnalisé ont été utilisés ; et seulement une orchestration unique et très simple a été utilisée pour le scénario d’Orchestration. Optimisations de performances décrits dans [optimisation des performances](../technical-guides/optimizing-performance.md) ont été appliquées à l’environnement et sont entièrement documentées dans [Observations et recommandations](../technical-guides/observations-and-recommendations.md).  
  
## <a name="test-goals"></a>Objectifs de test  
 Les objectifs de la charge de test exécutées inclus les éléments suivants :  
  
1.  Fournir générales de dimensionnement et de la mise à l’échelle des conseils pour BizTalk Server :  
  
    1.  Quantifier l’impact de l’ajout des ordinateurs supplémentaires pour le groupe BizTalk Server. Pour ce test, les performances d’une solution BizTalk Server a été mesuré lorsque le groupe BizTalk Server est en cours d’exécution un, deux, trois ou quatre ordinateurs exécutant BizTalk Server.  
  
    2.  Quantifier l’impact de l’ajout de bases de données BizTalk MessageBox supplémentaires à un groupe BizTalk Server. Pour ce test, les performances d’une solution BizTalk Server a été mesuré lorsque le groupe a été configuré pour utiliser une base de données MessageBox ou quatre bases de données MessageBox.  
  
        > [!NOTE]  
        >  Test avec deux bases de données MessageBox ne faisait pas, car il est peu, le cas échéant, gain de performances lors de la mise à l’échelle d’une à deux bases de données MessageBox. En fait, mise à l’échelle d’une à deux bases de données MessageBox peut nuire aux performances. Pour plus d’informations sur la montée en puissance parallèle de la MessageBox, consultez [mise à l’échelle du niveau SQL Server](../core/scaling-up-the-sql-server-tier.md).
  
2.  Fournissent des conseils de dimensionnement et de mise à l’échelle pour les scénarios suivants :  
  
    1.  Scénario de messagerie unidirectionnel WCF-NetTcp  
  
    2.  Scénario d’Orchestration unidirectionnel WCF-NetTcp  
  
## <a name="test-measurements-used"></a>Mesures de test utilisées  
Performances de BizTalk Server a été mesuré à l’aide des critères suivants :  
  
1.  **Le débit global** – mesuré avec le  **BizTalk : messagerie (*nom d’hôte*) \Documents reçus / s ** et  **BizTalk : messagerie (*nom d’hôte*) \Documents traitées / s ** compteurs de performances du serveur BizTalk de réception et le traitement des ordinateurs hôtes.  
  
2.  **L’utilisation du processeur** – mesuré avec le **\Processor(_Total)\\% temps processeur** compteurs de performance sur le serveur BizTalk Server] et les ordinateurs SQL Server. Tous les résultats des tests ont été examinés plus en détail et les goulots d’étranglement de performances sont décrits dans [Observations et recommandations](../technical-guides/observations-and-recommendations.md).  
  
## <a name="scaling-out-the-processing-tier-and-the-database-tier"></a>Montée en puissance parallèle de la couche de traitement et de la couche de base de données  
BizTalk Server permet d’ajouter facilement des fonctions de niveau de traitement accrue en ajoutant un ou plusieurs ordinateurs BizTalk Server à un groupe BizTalk Server existant. BizTalk Server gère les fonctionnalités de niveau de base de données accrue grâce à l’ajout de bases de données MessageBox.  
  
Pour fournir la montée en charge les métriques pour BizTalk Server, les tests ont été effectués avec un, deux, trois et fourBizTalk, serveurs de base de données. Pour illustrer l’impact de l’évolution horizontale du niveau de la base de données, ces tests ont été effectuées sur des systèmes à la fois unique et multiple-MessageBox.  
  
## <a name="testing-scenarios"></a>Scénarios de test  
 Le flux des messages dans l’environnement BizTalk Server pour ces scénarios est décrit en détail ci-dessous.  
  
### <a name="messaging-test-scenario"></a>Scénario de test de messagerie  
 ![Scénario de messagerie](../technical-guides/media/messagingscenario.gif "MessagingScenario")  
  
1.  La Visual Studio 2010 Ultimate édition un test de charge fonctionnalité génère un message XML et l’envoie à l’ordinateur exécutant BizTalk Server avec le transport NetTcp.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur le test de charge Visual Studio 2010 Ultimate Édition, consultez le lien hypertexte « « [test de l’Application](http://go.microsoft.com/fwlink/?LinkID=208247) (http://go.microsoft.com/fwlink/?LinkID=208247).  
    >   
    >  Pour plus d’informations sur comment nous avons utilisé la Visual Studio 2010 Ultimate édition un test de charge des fonctionnalités dans notre environnement de test, consultez [à l’aide de Visual Studio pour faciliter les tests automatisés](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md).  
  
2.  Le message XML est reçu par un serveur BizTalk Server emplacement que l’adaptateur de réception utilise WCF-NetTcp de réception. L’emplacement de réception est configuré pour utiliser le pipeline PassThruReceive, qui n’effectue aucun traitement du message.  
  
3.  Le Gestionnaire de point de terminaison (EPM) de BizTalk Server publie le message dans la base de données MessageBox de BizTalk.  
  
4.  Un port d’envoi de BizTalk Server qui utilise l’adaptateur d’envoi WCF-NetTcp s’abonne aux messages publiés par l’emplacement de réception et récupère le message à partir de la BizTalk MessageBox. Le port d’envoi utilise le pipeline PassThruTransmit, qui n’effectue aucun traitement du message.  
  
5.  Le message est remis au serveur principal service WCF par l’adaptateur d’envoi WCF-NetTcp.  
  
### <a name="orchestration-test-scenario"></a>Scénario de test d’orchestration  
 ![Flux du scénario d’orchestration](../technical-guides/media/orchestrationscenarioflow.gif "OrchestrationScenarioFlow")  
  
1.  La Visual Studio 2010 Ultimate édition un test de charge fonctionnalité génère un message XML et l’envoie à l’ordinateur exécutant BizTalk Server à l’aide du transport NetTcp.  
  
2.  Le message XML est reçu par un serveur BizTalk Server utilise WCF-NetTcp adaptateur de réception de port de réception. Le port de réception est configuré pour utiliser le PassThruReceive, qui n’effectue aucun traitement du message de pipeline.  
  
3.  Le message est remis à une Orchestration simple, qui se compose uniquement d’un port de réception (lié au port de réception WCF à partir de l’étape 2) et un port d’envoi (lié au port d’envoi WCF à partir de l’étape 4). Variables de message sont « non typées », c'est-à-dire qu’ils utilisent un Type de Message « » de « System.XML.XmlDocument ». L’orchestration reçoit simplement le message via son port de réception et envoie le message via son port d’envoi. Aucun traitement de message est exécuté.  
  
4.  Un port d’envoi unidirectionnel BizTalk Server qui utilise l’adaptateur d’envoi WCF-NetTcp s’abonne aux messages publiés par l’orchestration et récupère le message à partir de la BizTalk MessageBox. Le port d’envoi utilise le pipeline PassThruTransmit, qui n’effectue aucun traitement du message.  
  
5.  Le message est remis au serveur principal service WCF par l’adaptateur d’envoi WCF-NetTcp.  
  
## <a name="hardware-configuration"></a>Configuration matérielle  
  
### <a name="lab-hardware-diagram-and-specifications"></a>Spécifications et diagramme de matériel de laboratoire  
 La configuration du matériel utilisée pour le laboratoire est illustrée ci-dessous. Pour répondre facilement à échelle hors les niveaux de traitement et de base de données, le matériel de laboratoire suivant a été utilisé :  
  
-   Deux ordinateurs Hewlett Packard DL-380 de classe entreprise et deux ordinateurs de la classe Dell R710 Enterprise pour le niveau de traitement BizTalk Server.  
  
-   Quatre ordinateurs classe Dell R900 Enterprise pour la couche de base de données, de fournir une fonctionnalité multi-MessageBox.  
  
 Un diagramme du matériel utilisé dans le laboratoire est fourni ci-dessous :  
  
 ![Infrastructure du Guide de performances](../technical-guides/media/performanceguideinfrastructure.gif "PerformanceGuideInfrastructure")  
  
 Le tableau suivant fournit des informations plus spécifiques sur le matériel utilisé dans le laboratoire.  
  
|Nom|Modèle|Type de processeur|Nombre d'unités centrales|Nombre de cœurs/processeur|Architecture d’UC|Mémoire|Système d'exploitation|Logiciel|  
|----------|-----------|--------------|--------------------|--------------------------|----------------------|------------|----------------------|--------------|  
|R710-01|Dell PowerEdge R710|Intel Xeon X5570|2 x 2,93 GHz|4|x64|72 GO|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|R710-02|Dell PowerEdge R710|Intel Xeon X5570|2 x 2,93 GHz|4|x64|72 GO|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|DL380G7-01|Hewlett-Packard DL380 G7|Intel Xeon X5670|2 x 2,93 GHz|6|x64|192 GO|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|DL380G7-02|Hewlett-Packard DL380 G7|Intel Xeon X5670|2 x 2,93 GHz|6|x64|192 GO|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|DL380-01|Hewlett Packard DL380|Intel Xeon 5150|2 x 2,66 GHz|2|x64|8 GO|Windows Server 2008 R2 Enterprise Edition|DB de Test de charge SQL Server 2008 R2<br /><br /> Visual Studio 2010<br /><br /> Service principal WCF|  
|DL380-02|Hewlett Packard DL380|Intel Xeon E5335|2 x 2,00 GHz|4|x64|8 GO|Windows Server 2008 R2 Enterprise Edition|Contrôleur de Test de charge Visual Studio 2010|  
|DL380-03|Hewlett Packard DL380|Intel Xeon E5335|2 x 2,00 GHz|4|x64|8 GO|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 Load Test Agent|  
|DL380-04|Hewlett Packard DL380|Intel Xeon E5335|2 x 2,00 GHz|4|x64|8 GO|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 Load Test Agent.<br /><br /> Analyseur de performances de ligne de commande|  
|R805-06|Dell PowerEdge R805|Cœurs de processeur AMD Opteron 2354|2 x 2,2 GHz|4|x64|32 Go|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 Load Test Agent|  
|R805-07|Dell PowerEdge R805|Cœurs de processeur AMD Opteron 2354|2 x 2,2 GHz|4|x64|32 Go|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 Load Test Agent|  
|R900-03|Dell PowerEdge R900|Intel Xeon E7330|4 x 2,4 GHz|4|x64|64 Go|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 avec mise à jour Cumulative 4|  
|R900-04|Dell PowerEdge R900|Intel Xeon E7330|4 x 2,4 GHz|4|x64|64 Go|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 avec mise à jour Cumulative 4|  
|R900-05|Dell PowerEdge R900|Intel Xeon E7330|4 x 2,4 GHz|4|x64|64 Go|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 avec mise à jour Cumulative 4|  
|R900-06|Dell PowerEdge R900|Intel Xeon E7330|4 x 2,4 GHz|4|x64|64 Go|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 avec mise à jour Cumulative 4|  
  
### <a name="storage-area-network-configuration"></a>Configuration de réseau de zone de stockage  
 Le diagramme suivant décrit la configuration de réseau SAN de zone de stockage utilisée pour l’environnement lab.  
  
 ![Informations SAN](../technical-guides/media/saninformation.gif "SANinformation")  
  
### <a name="emc-clariion-cx4-960-san-configuration"></a>Configuration EMC CLARiiON CX4-960 SAN  
  
|Processeur de service et les informations relatives au Cache|Configuration du numéro d’unité logique|  
|---------------------------------------------|-----------------------|  
|Deux processeurs Service, chacun avec :<br /><br /> -La taille du cache de lecture : 2 000 Mo.<br />-Taille du cache d’écriture : 8000 Mo.<br />-Deux ports frontaux liées au commutateur Fibre. 4 Gbits/s par port.|-64 disques (Go 268, 15k tr/min, Fibre Channel, Seagate.<br />-Huit 8 disques RAID 1 + 0, constitués de groupes à partir de ces 64 disques.<br />-Chaque serveur de base de données a été assigné 5 metaLUN configurés uniformément à partir de ces groupes RAID.|  
  
 Il est important de déterminer le débit maximal réalisable d’un réseau SAN et comparer cette valeur à la charge prévue sur le réseau SAN de production. Cela permettra d’éviter les dépenses inattendus pour le matériel SAN lors du déplacement de votre application à partir d’un environnement d’assurance de test/qualité dans un environnement de production. Par exemple, le débit maximal disponible pour le réseau SAN peut-être être plus que suffisant pour votre application dans un environnement de test de bac à sable. Toutefois, si d’autres applications serveur utilisent le réseau SAN en production, débit SAN disponible est peut-être insuffisant et peut devenir un goulot d’étranglement.  
  
 Lorsque vous évaluez les performances de votre réseau SAN, considérez les points suivants :  
  
1.  **Quel est le débit maximal réalisable du réseau SAN ?** -Il est mesuré à l’aide le plus petit dénominateur commun, en termes de débit, de l’adaptateur de bus hôte (HBA) dans le serveur, le débit du réseau SAN du commutateur et la vitesse des cartes de contrôleur de réseau SAN.  
  
2.  **Les autres applications utilisent le réseau SAN en production ?** – Envisagez d’autres applications faire utiliser du réseau SAN dans l’environnement de production. Si d’autres sinon applications gourmandes en e/s telles que Exchange Server ou base de données utilisent le réseau SAN en production, le montant du débit du réseau SAN disponible pour votre ordinateur exécutant BizTalk Server est réduit en conséquence.  
  
 Pour l’environnement lab, un réseau SAN dédié a été utilisé. Chacun des quatre ordinateurs SQL Server a été connecté au réseau SAN commutateur avec deux adaptateurs de bus hôte (HBA), 4 Gbits/s en fournissant un débit potentiel total de 8 Gbits/s par serveur. Le réseau SAN avait deux processeurs de service, et chaque processeur de service que deux ports frontaux liées au commutateur Fibre, en fournissant un débit potentiel total de 16 Gbits/s entre le réseau SAN et le commutateur.  
  
 La configuration de LUN suivante a été utilisée pour chacun des quatre ordinateurs exécutant SQL Server dans l’environnement de test.  
  
|Lettre de lecteur|Nom de volume|Fichiers|Taille du numéro d’unité logique (Go)|  
|------------------|-----------------|-----------|---------------------|  
|C|Lecteur C local|MASTER, MSDB et MODEL|136|  
|H|Data_Tempdb|Fichiers de données TempDB|50|  
|I|Logs_Tempdb|Fichiers journaux de TempDB|50|  
|J|Data_BtsMsgBox|Fichiers de données BizTalk MsgBoxDB + (sur Master MsgBox) base de données Mgmt, base de données SSO, les fichiers de données de base de données DTA|120|  
|K|Logs_BtsMsgBox|Fichiers de journaux de BizTalk MsgBoxDB + (sur Master MsgBox) fichiers journaux de base de données Mgmt, base de données SSO, base de données DTA|120|  
|O|Logs_Spare|Pas utilisé pour les fichiers SQL. Utilisé pour stocker les fichiers DTCLog, en tant que MSDTC provoquer des e/s du disque fréquentes, surtout dans un environnement multi-MessageBox.|20|  
  
### <a name="sqlio-test-results"></a>Résultats des tests SQLIO  
 Nous avons utilisé l’outil SQLIO pour évaluer et de mesurer la capacité d’entrée/sortie de la configuration de réseau SAN de zone de stockage utilisée dans notre environnement de laboratoire. Comme l’indique le nom de l’outil, SQLIO est un outil précieux pour mesurer l’impact du système de fichiers d’e/s sur les performances de SQL Server. 

Pour mesurer la capacité d’entrée/sortie de la configuration de réseau SAN de zone de stockage pour les applications de base de données SQL Server, consultez [analyse les caractéristiques d’e/s et dimensionnement des systèmes de stockage pour les Applications de base de données SQL Server](https://msdn.microsoft.com/library/ee410782(SQL.100).aspx).  
  
 Pour notre test SQLIO, les problèmes d’utilitaire sqlio.exe 8K demandes de lecture à partir de 8 threads et maintenir une profondeur de file d’attente d’e/s de 8. Nous avons utilisé les paramètres suivants :  
  
-   Tous les tests utilisé 8 threads de traitement, chacun exécuté pendant 60 secondes.  
  
-   8 Ko aléatoire écrit dans les fichiers de données.  
  
-   lit de 8 Ko aléatoire aux fichiers de données.  
  
-   Tous les fichiers sont dimensionnés à 25 Go.  
  
-   Les lecteurs de disque à être testées sont lecteur h, i, j : et K.  
  
 Les lignes de commande SQLIO utilisés décrits ci-dessous :  
  
-   **Pour les lectures**: sqlio - kR-s60 - frandom-o8-t8-M8 -LS-FParam.txt  
  
-   **Pour les écritures**: sqlio -kW-s60 - frandom-o8-t8-M8 -LS-FParam.txt  
  
 Le fichier Param.txt contient les éléments suivants :  
  
-   **Nombre de disques :** h, i, j : et K  
  
-   **Emplacement physique des fichiers tests**:  
  
    -   H:\testfile.dat 2 25000 de 0 x 0  
  
    -   I:\testfile.dat 2 25000 de 0 x 0  
  
    -   J:\testfile.dat 2 25000 de 0 x 0  
  
    -   K:\testfile.dat 2 25000 de 0 x 0  
  
 Le tableau suivant répertorie les résultats des tests :  
  
-   8 Ko aléatoire lit à partir de fichiers de test de 25 Go simultanément sur j : LUN h, i, k : (les numéros d’unités logiques utilisées pour tous les fichiers de notre base de données)  
  
    ###  
  
    |Opérations d’entrée/sortie par seconde (e/s par seconde)|Mégaoctets par seconde (Mo/s)|Latence moyenne|  
    |------------------------------------------------------|---------------------------------------|---------------------|  
    |10662.67|83.30|5 ms|  
  
-   8 Ko aléatoire écrit dans les fichiers de test de 25 Go simultanément sur j : LUN h, i, k : (les numéros d’unités logiques utilisées pour tous les fichiers de notre base de données)  
  
    ###  
  
    |Opérations d’entrée/sortie par seconde (e/s par seconde)|Mégaoctets par seconde (Mo/s)|Latence moyenne|  
    |------------------------------------------------------|---------------------------------------|---------------------|  
    |31527.95|246.31|1 ms|  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à l’échelle d’un environnement BizTalk Server de production](../technical-guides/scaling-a-production-biztalk-server-environment.md)