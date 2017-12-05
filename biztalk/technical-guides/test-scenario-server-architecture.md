---
title: "Architecture du scénario de serveur de test | Documents Microsoft"
ms.custom: 
ms.date: 2015-12-09
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e3afb57-c3ff-4314-9605-cf9fe936e63f
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49a51244b7033c6cebc978a39ad37dd5732fa38d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="test-scenario-server-architecture"></a>Architecture de serveur de scénario de test
Cette rubrique fournit une vue d’ensemble du flux de messages entre les serveurs au cours du test de charge et les architectures de serveur distincts par rapport à laquelle le test de charge a été effectué.  
  
## <a name="overview-of-message-flow-during-load-testing"></a>Vue d’ensemble du flux de messages au cours du test de charge  
 Le diagramme suivant fournit une présentation générale de l’architecture de serveur utilisée pour tous les scénarios de test et le flux des messages entre les serveurs pendant un test de charge.  
  
> [!NOTE]  
>  Chaque architecture de serveur distincts qui a été testé est décrite dans la section **Architecture du serveur de ligne de base**.  
  
 L’illustration suivante fournit une vue d’ensemble du flux du message. Les nombres dans la figure correspondent aux étapes répertoriées ci-dessous l’illustration.  
  
 ![Vue d’ensemble du flux de message](../technical-guides/media/archmsgflow.gif "ArchMsgFlow")  
Vue d'ensemble du flux de messages  
  
1.  Le test de charge est initié par l’ordinateur du contrôleur de l’Agent charge **VSTS_TestController**:  
  
    -   Un projet Visual Studio 2008 sur **VSTS_TestController** est exécutée. Le projet charge une instance de la classe BizUnit, charge le fichier de configuration BizUnit XML spécifié et commence à s’exécuter les étapes définies dans le fichier de configuration BizUnit.  
  
        > [!NOTE]  
        >  Pour plus d’informations sur le fichier de configuration XML utilisé par BizUnit, consultez la rubrique « Définition des Tests à l’aide un fichier de Configuration XML » à [http://go.microsoft.com/fwlink/?LinkId=143432](http://go.microsoft.com/fwlink/?LinkId=143432).  
  
    -   Après avoir effectué les étapes de configuration de Test, l’une des étapes dans le projet BizUnit exécute une commande qui affiche une boîte de dialogue qui vous invite à démarrer un test « amorcer » exécuté pour envoyer des messages d’amorçage à le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
    -   Messages d’amorçage sont envoyées à partir d’un projet de Test de Visual Studio 2008 distinct sur **VSTS_TestController**. Messages d’amorçage sont envoyées à « préchauffage » l’environnement de test en initialisant les caches du système.  
  
    -   Une fois que tous les messages d’amorçage ont été traités ; l’instance de BizUnit charge les compteurs de l’Analyseur de performances pour tous les ordinateurs en cours de test dans la série de tests principal et exécute une commande pour afficher une boîte de dialogue qui vous invite à envoyer des messages pour la série de tests principal.  
  
    -   Le projet Visual Studio 2008 du Test de charge sur **VSTS_TestController** dirige les ordinateurs de l’Agent de Test de charge pour envoyer des messages pour la série de tests principal.  
  
2.  Les ordinateurs de test de soumettre l’Agent de Test de charge des messages à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs spécifiés dans le fichier app.config du projet Visual Studio 2008 du Test de charge sur l’ordinateur de contrôleur de Test de charge (**VSTS_TestController**).  
  
3.  Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs reçoivent les messages envoyés par les ordinateurs de l’Agent de Test de charge, pour ce test de charge que les messages ont été reçus par un moyen de deux emplacement de réception requête-réponse.  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]publie le message dans la base de données MessageBox.  
  
    -   Les messages sont consommés par une orchestration.  
  
    -   L’orchestration est liée à un port qui permet d’appeler le service de calculatrice en aval d’envoi de sollicitation-réponse bidirectionnelle.  
  
    > [!NOTE]  
    >  Le service de calculatrice en aval est basé sur les exemples Windows Communication Foundation décrits à [http://go.microsoft.com/fwlink/?LinkId=141762](http://go.microsoft.com/fwlink/?LinkId=141762). Les exemples Windows Communication Foundation sont disponibles pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=87352](http://go.microsoft.com/fwlink/?LinkId=87352).  
  
4.  Le service de calculatrice consomme la demande à partir de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et retourne une réponse à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] port d’envoi de sollicitation-réponse.  
  
5.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]traite la réponse et stocke le message de réponse dans la base de données MessageBox. Le message de réponse du service web Calculator est ensuite récupéré à partir de la base de données MessageBox par le port de requête-réponse de BizTalk, et la remise d’un message de réponse vers les ordinateurs de l’Agent de Test de charge.  
  
## <a name="baseline-server-architecture"></a>Architecture de serveur de base  
 Pour l’architecture de serveur de base, le rôle Hyper-V a été pas installé alors que les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et SQL Server ont été installés sur le système d’exploitation hôte. Cela a été effectué pour établir des métriques de performances « ligne de base » de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution sur un environnement matériel physique.  
  
 La figure suivante illustre physique [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et niveaux de SQL Server pour l’Architecture du serveur de ligne de base.  
  
 ![BizTalk physique &#47; Physiques SQL](../technical-guides/media/archphysicalbts-physicalsql.gif "ArchPhysicalBTS_PhysicalSQL")  
Serveur BizTalk physique / physique SQL Server (de base)  
  
-   **BizTalk Server** - 2 ordinateurs BizTalk Server configurés comme suit :  
  
    -   Un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur avec **6** Go de RAM et **8** cœurs de processeurs disponibles.  
  
    -   Un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur avec **3** Go de RAM et **4** cœurs de processeurs disponibles.  
  
    -   Nombre total de 6 + 3 = **9** Go de RAM disponible et 8 + 4 = **12** cœurs de processeurs disponibles pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   **SQL Server** -1 ordinateur SQL Server configurée comme suit :  
  
    -   **8** Go de RAM disponible.  
  
    -   **4** cœurs de processeurs disponibles.  
  
## <a name="virtual-biztalk-server--physical-sql-server"></a>Serveur BizTalk virtuel / physique SQL Server  
 La figure suivante représente le serveur virtuel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et physique [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] niveaux.  
  
 ![BizTalk virtuel &#47; Physiques SQL](../technical-guides/media/archvirtualbts-physicalsql.gif "ArchVirtualBTS_PhysicalSQL")  
Serveur BizTalk virtuel / physique SQL Server  
  
 Pour ce scénario, le test de charge a été effectué sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en cours d’exécution sur des ordinateurs virtuels Hyper-V et SQL Server s’exécutant sur du matériel physique.  
  
> [!NOTE]  
>  L’allocation de cœurs de processeur et mémoire RAM décrite ci-dessous était identique pour les scénarios de chaque ligne de base non, la seule différence étant que certains ordinateurs sont en cours d’exécution sur un ordinateur virtuel Hyper-V ou sur du matériel physique.  
  
-   **BizTalk Server** - 3 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]ordinateurs s configurés comme suit :  
  
    -   3 Go de RAM allouée à chaque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur avec un total de 3 x 3 = **9** Go de RAM disponible pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    -   4 cœurs de processeur alloué à chaque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur avec un total de 3 x 4 = **12** cœurs de processeurs disponibles pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   **SQL Server** -1 ordinateur SQL Server configurée comme suit :  
  
    -   **8** Go de RAM disponible.  
  
    -   **4** cœurs de processeurs disponibles.  
  
## <a name="virtual-biztalk-server--virtual-sql-server"></a>Serveur BizTalk virtuel / virtuel SQL Server  
 La figure suivante illustre une machine virtuelle, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur et un ordinateur virtuel de SQL Server sur Hyper-V distincte des ordinateurs hôtes.  
  
 ![BizTalk virtuel &#47; SQL virtuel](../technical-guides/media/archvirtualbts-virtualsql.gif "ArchVirtualBTS_VirtualSQL")  
Serveur BizTalk virtuel / virtuel SQL Server  
  
 Pour ce scénario, le test de charge a été effectué sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en cours d’exécution sur des ordinateurs virtuels Hyper-V et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] en cours d’exécution sur un ordinateur virtuel Hyper-V. Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs virtuels Hyper-V et le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] machine virtuelle Hyper-V ont été exécutées sur des ordinateurs hôtes Hyper-V distincts.  
  
> [!NOTE]  
>  L’allocation de cœurs de processeur et de RAM pour ce scénario est identique à l’allocation de cœurs de processeur et de RAM pour le **virtuels BizTalk Server / physique SQL Server** scénario, la seule différence étant que [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] a été configuré pour s’exécuter sur un ordinateur virtuel Hyper-V plutôt que de matériel physique.  
  
## <a name="consolidated-environment"></a>Environnement consolidé  
 La figure suivante illustre virtuel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs et un ordinateur virtuel de SQL Server consolidées sur un ordinateur hôte de Hyper-V.  
  
 ![BizTalk virtuel &#47; SQL virtuel &#47; Consolidés](../technical-guides/media/archvirtualbts-virtualsql-consolidated.gif "ArchVirtualBTS_VirtualSQL_Consolidated")  
Environnement consolidé  
  
 Pour ce scénario, le test de charge a été effectué sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en cours d’exécution sur des ordinateurs virtuels Hyper-V et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] en cours d’exécution sur un ordinateur virtuel Hyper-V. Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs virtuels Hyper-V et le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] machine virtuelle Hyper-V ont été exécutées sur le même ordinateur hôte Hyper-V.  
  
> [!NOTE]  
>  L’allocation de cœurs de processeur et de RAM pour ce scénario est identique à l’allocation de cœurs de processeur et de RAM pour le **virtuels BizTalk Server / serveur SQL Server virtuel** scénario, la seule différence étant que les deux le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Ordinateurs virtuels Hyper-V et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateurs virtuels Hyper-V ont été configurés pour s’exécuter sur le même ordinateur hôte Hyper-V.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du scénario de test](../technical-guides/test-scenario-overview.md)