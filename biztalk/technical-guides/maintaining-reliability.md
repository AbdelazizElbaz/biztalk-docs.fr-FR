---
title: "La fiabilité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09cdce13-a75b-44d7-8388-7a868bb51c69
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb1f956c0f3b09ee51d3dd9d05f64dbd3eeeab3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="maintaining-reliability"></a>La fiabilité
Cette section fournit des informations sur la façon dont vous pouvez résoudre les problèmes de fiabilité avec un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système. Ces problèmes peuvent être détectés par les vérifications de maintenance de routine qui sont exécutées dans le [Maintenance de Routine des listes de contrôle](../technical-guides/routine-maintenance-checklists.md) section de ce document.  
  
 Outre les rubriques de cette section, les autres rubriques de ce document résoudre les problèmes de fiabilité. Ces rubriques sont répertoriées dans [rubriques connexes](../technical-guides/maintaining-reliability.md#BKMK_Related) ci-dessous.  
  
## <a name="testing-group-failover"></a>Test de basculement de groupe  
 Effectuez les procédures de cette section dans le cadre des vérifications de fiabilité qui doit être effectuée chaque mois. Ces procédures incluent test de la stratégie de basculement de groupe et vérifier si les ressources du groupe peuvent basculer.  
  
> [!NOTE]  
>  Si l’ordinateur est joint à un domaine, les membres du groupe Admins du domaine doivent être en mesure d’effectuer cette procédure.  
  
> [!NOTE]  
>  Pour effectuer les procédures de cette section, vous devez être connecté en tant que membre du groupe Administrateurs sur l’ordinateur local, ou avoir reçu l’autorisation appropriée.  
  
 Procédez comme suit pour tester le basculement du groupe sur les ordinateurs exécutant Windows Server 2008.  
  
#### <a name="to-test-a-group-failover-policy"></a>Pour tester une stratégie de basculement de groupe  
  
1.  Vérifiez que vous avez installé le **le Clustering de basculement** fonctionnalité au moins deux ordinateurs exécutant Windows Server 2008 afin de créer un Cluster de basculement Windows à deux nœuds. Pour obtenir des instructions sur la façon d’installer cette fonctionnalité, consultez [installer la fonctionnalité de Clustering de basculement](http://go.microsoft.com/fwlink/?LinkId=157259) (http://go.microsoft.com/fwlink/?LinkId=157259).  
  
2.  Ouvrez Gestion du Cluster de basculement en cliquant sur **Démarrer**, puis sur **outils d’administration**, puis en cliquant sur **gestion du Cluster de basculement**.  
  
3.  Dans l’arborescence de la console, développez le nœud de cluster, le **Services et Applications** nœud, cliquez sur l’instance en cluster de l’application à l’échec du basculement, puis cliquez sur **propriétés**.  
  
4.  Sur le **basculement** onglet, définissez **nombre maximal d’échecs dans la période spécifiée** sur 0, puis cliquez sur **OK**.  
  
5.  Dans l’arborescence de la console, développez le **Services et Applications** nœud.  
  
6.  Dans le volet de détails, cliquez sur une ressource, puis cliquez sur **propriétés**.  
  
7.  Sur le **stratégies** onglet, définissez **nombre maximal de redémarrages dans la période spécifiée** sur 0, puis cliquez sur **OK**.  
  
8.  Avec le bouton droit de la ressource, cliquez sur **autres Actions**, puis cliquez sur **simuler une panne de cette ressource**. Vérifiez si le groupe réagit en fonction de la stratégie que vous avez spécifié à l’étape précédente.  
  
9. Cliquez sur l’instance en cluster de l’application à l’échec du basculement, puis cliquez sur **propriétés**.  
  
10. Sur le **basculement** onglet, définissez **nombre maximal d’échecs dans la période spécifiée** sur 1, puis cliquez sur **OK**.  
  
11. Avec le bouton droit de la ressource et sélectionnez **mettre cette ressource en ligne**.  
  
#### <a name="to-test-whether-group-resources-can-fail-over"></a>Pour vérifier si les ressources du groupe peuvent basculer  
  
1.  Vérifiez que vous avez installé le **le Clustering de basculement** fonctionnalité sur l’ordinateur exécutant Windows Server 2008. Pour obtenir des instructions sur la façon d’installer cette fonctionnalité, consultez [installer la fonctionnalité de Clustering de basculement](http://go.microsoft.com/fwlink/?LinkId=157259) (http://go.microsoft.com/fwlink/?LinkId=157259).  
  
2.  Ouvrez Gestion du Cluster de basculement en cliquant sur **Démarrer**, puis sur **outils d’administration**, puis en cliquant sur **gestion du Cluster de basculement**.  
  
3.  Dans l’arborescence de la console, développez le nœud de cluster, le **Services et Applications** nœud, puis cliquez sur l’instance en cluster de l’application à être basculé.  
  
4.  Sur le **Action** menu, cliquez sur **déplacer ce service ou cette application vers un autre nœud**, puis cliquez sur le nœud auquel l’application doit être effectuée.  
  
5.  Dans le **Confirmez action** boîte de dialogue zone, choisissez de déplacer vers le nœud sélectionné.  
  
6.  Assurez-vous que le nœud auquel vous avez déplacé l’application est répertorié sur la **propriétaire actuel** dans le volet de détails de l’application.  
  
##  <a name="BKMK_BTSGrp"></a>Vous être assuré de plusieurs serveurs appartiennent à un groupe BizTalk  
 Pour garantir la fiabilité d’un système, au moins deux serveurs BizTalk physiques doivent être membre du groupe BizTalk.  Si vous avez besoin ajouter un serveur à un groupe BizTalk, tenez compte les éléments suivants :  
  
-   Un serveur peut uniquement être associé à un groupe BizTalk. Si un serveur appartient déjà à un autre groupe, vous devez le supprimer de son groupe actuel avant de l'ajouter à un nouveau groupe. Pour plus d’informations sur la suppression d’un serveur à partir d’un groupe BizTalk, consultez « Pour supprimer un serveur d’un groupe » dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=155577](http://go.microsoft.com/fwlink/?LinkId=155577).  
  
-   Il n'y a pas d'interaction entre les groupes BizTalk associés à différents serveurs dans un environnement BizTalk Server, excepté dans le cadre d'échanges de message.  
  
-   Le composant d'exécution de BizTalk Server doit être installé sur l'ordinateur que vous voulez ajouter au groupe BizTalk.  
  
> [!NOTE]  
>  Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté en tant que membre du groupe Administrateurs de l’authentification unique et en tant que membre du groupe Administrateurs Windows.  
  
#### <a name="to-determine-whether-at-least-two-physical-biztalk-servers-are-part-of-the-biztalk-group"></a>Pour déterminer si au moins deux serveurs BizTalk physiques font partie du groupe BizTalk  
  
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration en cliquant sur **Démarrer**, en pointant sur **tous les programmes**, en pointant sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis en cliquant sur **Administration de BizTalk Server**.  
  
2.  Développez le [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] nœud, développez le **groupe BizTalk** nœud, puis développez le **paramètres de plateforme** nœud.  
  
3.  Cliquez sur le **serveurs** nœud. Vérifiez que plus d’un serveur est répertorié dans le **serveurs** volet.  
  
    > [!NOTE]  
    >  Pour afficher des informations sur le serveur, cliquez sur le serveur, pointez sur **vue**, puis cliquez sur **Page Hub du groupe**.  
  
#### <a name="to-add-a-server-to-a-biztalk-group"></a>Pour ajouter un serveur à un groupe BizTalk  
  
1.  Sur l’ordinateur que vous souhaitez ajouter à un groupe BizTalk, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis cliquez sur  **Configuration de BizTalk Server**.  
  
2.  Dans **Configuration de Microsoft BizTalk Server 2010**, sélectionnez **configuration personnalisée**.  
  
3.  Dans **nom du serveur de base de données**, tapez le nom du serveur SQL pour le groupe BizTalk auquel associer le serveur.  
  
4.  Dans **informations d’identification du Service**, tapez le nom d’utilisateur et un mot de passe que les services utilisera, puis cliquez sur **configurer**.  
  
5.  Dans l’arborescence de navigation sur le côté gauche de l’écran, cliquez sur **Enterprise SSO**.  
  
6.  Sur le **Enterprise Single Sign-On** , cliquez sur **joindre un système SSO existant**.  
  
    > [!NOTE]  
    >  Assurez-vous que le nom du serveur et le nom de la base de données pointent vers le serveur de base de données SSO principal pour le groupe BizTalk auquel associer le serveur.  
  
7.  Dans l’arborescence de navigation sur le côté gauche de l’écran, cliquez sur **groupe**.  
  
8.  Sur le **groupe** , cliquez sur **joindre un groupe BizTalk existant**.  
  
    > [!NOTE]  
    >  Assurez-vous que le nom du serveur et le nom de la base de données pointent vers les bases de données pour le groupe BizTalk auquel associer le serveur.  
  
9. Dans la barre de menus, cliquez sur **appliquer la Configuration** pour configurer Enterprise Single Sign-On et que le groupe sur cet ordinateur.  
  
##  <a name="BKMK_Related"></a> Sections connexes  
  
-   Pour plus d’informations sur la vérification de disques défaillants dans le matériel RAID, consultez « Affichage Propriétés du disque » dans l’aide du produit Windows Server 2003 à [http://go.microsoft.com/fwlink/?linkid=104161](http://go.microsoft.com/fwlink/?linkid=104161).  
  
-   Pour plus d’informations sur la vérification de manuellement pour les messages suspendus, consultez « Investigating Orchestration, Port et échecs de messages » dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkID=154512](http://go.microsoft.com/fwlink/?LinkID=154512).  
  
-   Pour plus d’informations sur vous assurant que chaque hôte dispose d’une instance en cours d’exécution au moins deux serveurs physiques de BizTalk, consultez [haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md).  
  
-   Pour plus d’informations sur vous assurant que chaque hôte dispose d’une instance en cours d’exécution au moins deux serveurs physiques de BizTalk, consultez [mise à l’échelle des hôtes de réception](../technical-guides/scaling-out-receiving-hosts.md).  
  
-   Pour plus d’informations sur vous être assuré que le basculement pour les services cluster tout a été testés, consultez [Clustering du serveur de secret principal](../technical-guides/clustering-the-master-secret-server.md).  
  
-   Pour plus d’informations à propos de s’assurer que les bases de données BizTalk sont mis en cluster sous les Services SQL, consultez [Clustering le Databases2 serveur BizTalk](../technical-guides/clustering-the-biztalk-server-databases2.md).  
  
-   Pour plus d’informations sur la détermination de si n’importe quel code instable est utilisé (nécessitant des hôtes distincts), consultez [haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md).  
  
-   Pour plus d’informations sur l’exécution du test fonctionnel de toutes les nouvelles applications BizTalk, consultez [tester une Application](../technical-guides/testing-an-application.md)