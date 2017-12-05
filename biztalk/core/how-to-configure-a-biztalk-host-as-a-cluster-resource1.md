---
title: "Comment configurer un hôte BizTalk en tant qu’un Cluster de Resource1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation, high availability
- clustering, servers
- hosts, multiple
- hosts, high availability
- Windows Server cluster
- databases, clustering
- clustering, fail-overs
- Windows Server cluster, about Windows Server cluster
- installation, planning
- clustering, databases
- clustering, best practices
- clustering, unclustering
- clustering, configuring
- installation, clustering
ms.assetid: bcd656d2-8dd6-49fc-9c42-ef5c884e52c4
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a18548394980912796daf1100f700fd03e72f294
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-a-biztalk-host-as-a-cluster-resource"></a>Configuration d'un hôte BizTalk en tant que ressource de cluster
Cette rubrique décrit les étapes à suivre pour configurer un hôte BizTalk en tant que ressource de cluster. Pour effectuer les opérations décrites dans la présente rubrique, vous devez avoir configuré au moins deux serveurs BizTalk dans un groupe BizTalk en tant que membres d'un cluster de serveurs Windows. Pour plus d'informations sur la configuration d'un cluster de serveurs Windows Server, consultez l'aide en ligne de Windows Server.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk pour pouvoir configurer ou annuler sa mise en cluster.  
  
## <a name="considerations-and-known-issues"></a>Considérations diverses et problèmes connus  
  
-   Pour que vous puissiez exécuter une instance d'un hôte BizTalk en cluster sur BizTalk Server, un serveur BizTalk Server doit être configuré en tant que nœud d'un cluster de basculement Windows Server. Pour plus d'informations sur la configuration d'un nœud dans un cluster de serveurs, consultez l'aide en ligne de Windows Server.  
  
-   Vous ne peuvent pas basculer un hôte BizTalk en cluster pour une instance d’hôte dont l’option **désactiver instance d’hôte de démarrer** définie. Vérifiez que toutes les instances d’hôte de l’hôte BizTalk en cluster n’ont pas de cette option est activée. Cette option est définie dans la console Administration de BizTalk Server sur le **propriétés de l’Instance hôte** page.  
  
-   Lorsque vous mettez en cluster un hôte BizTalk, une ressource de cluster correspondante est créée dans le groupe de ressources de clusters spécifié. Une fois la ressource de cluster créée, chaque nœud disponible du cluster est ajouté comme propriétaire possible de cette ressource. Étant donné qu'une ressource de cluster peut être basculée vers n'importe quel nœud de la liste de propriétaires possibles, vous devez ajouter une instance de l'hôte à tous les nœuds disponibles d'un cluster avant de mettre en cluster un hôte BizTalk. Toute tentative de basculement d'un hôte BizTalk mis en cluster sur un ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui ne contient pas d'instance de cet hôte échoue.  
  
    > [!NOTE]
    >  Pour empêcher un hôte BizTalk mis en cluster de s'exécuter ou de basculer sur un nœud de cluster donné, supprimez celui-ci de la liste de propriétaires possibles de la ressource de cluster créée lors de la mise en cluster de l'hôte BizTalk. Vous pouvez modifier la liste des propriétaires possibles d'une ressource de cluster à l'aide de l'interface de gestion du cluster de basculement Windows Server.  
  
-   Lors de la mise en cluster d'un hôte BizTalk, assurez-vous que le groupe de clusters, le service mis en cluster ou l'application auquel vous ajoutez l'hôte contient une ressource Nom de réseau et une ressource Adresse IP. Si le groupe de clusters cible contient ces ressources, la ressource Nom de réseau est ajoutée en tant que dépendance à l'hôte BizTalk mis en cluster. Si ces ressources ne sont pas disponibles, l'hôte BizTalk ne fonctionnera pas correctement en tant que ressource mise en cluster.  
  
-   Si vous annulez la configuration d'un serveur BizTalk Server/nœud de cluster répertorié comme propriétaire possible d'un hôte BizTalk mis en cluster, la ressource de cluster de l'instance d'hôte est mise hors connexion dans le cluster Windows. Pour annuler la configuration d'un ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] répertorié en tant que propriétaire possible d'un hôte BizTalk sans mettre hors connexion la ressource de cluster de l'instance d'hôte, procédez comme suit :  
  
    -   Dans l'interface de gestion du cluster de basculement Windows Server, basculez l'hôte en cluster vers un ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] différent de l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dont vous allez annuler la configuration.  
  
    -   Dans la console Administration de BizTalk Server, sélectionnez l’instance de l’hôte BizTalk en cluster qui correspond à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur dont vous souhaitez annuler la configuration.  
  
    -   Supprimez l'instance hôte. Si une erreur s'affiche, choisissez l'option permettant de forcer la suppression de l'instance hôte.  
  
    -   Annulez la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Lorsqu'un hôte BizTalk est configuré en tant qu'hôte mis en cluster, une ressource correspondante de cluster est créée dans le groupe de ressources de clusters spécifié sur le cluster.  
  
     Par défaut, une ressource d’hôte BizTalk en cluster est configurée avec les valeurs de redémarrage suivantes sur un cluster de basculement Windows Server qui sont disponibles sur le **stratégies** onglet de la **propriétés** boîte de dialogue pour la ressource de cluster :  
  
    |Option|Valeur|  
    |------------|-----------|  
    |Si la ressource échoue, tentez un redémarrage sur le nœud actuel.|**True** <br />Le service de cluster tente de redémarrer la ressource lorsqu'elle s'arrête.|  
    |Période de redémarrage (mm:ss) :|**15:00** <br />Indique la période au cours de laquelle les tentatives de démarrage sont comptées.|  
    |Nombre maximal de redémarrages au cours de la période spécifiée :|**1** <br />Spécifie le nombre maximal de tentatives de redémarrage autorisées au cours de la **période de redémarrage (mm : ss)** .|  
    |Si le redémarrage échoue, faire basculer toutes les ressources dans ce service ou cette application.|**True** <br />Le service de cluster tente de redémarrer la ressource en basculant tous les groupe de ressources sur un autre nœud du cluster.|  
    |Si tous les redémarrages échouent de nouveau, commencez le redémarrage après la période spécifiée (hh:mm) :|**1:00** <br />Spécifie la période d’attente prolongée après laquelle le service de Cluster commence une autre série de tentatives de redémarrage.|  
    |Délai d'attente (mm:ss) :|**3:00** <br />Spécifie la durée pendant laquelle que la ressource va pouvoir faire pour passer l’état en ligne et hors connexion avant que le service de Cluster met la ressource en l’état d’échec.|  
  
     Les valeurs de redémarrage par défaut imposent au cluster de basculement Windows Server de tenter de redémarrer une instance de l'hôte BizTalk en cluster ayant échoué 1 fois dans un délai de 15 secondes. Étant donné que la **si le redémarrage n’aboutit pas, faire basculer toutes les ressources dans ce service ou cette application** a la valeur **True**, toute tentative de redémarrage fera basculer le groupe de ressources de cluster vers un autre cluster nœud. Si une instance ayant échoué d’un hôte BizTalk en cluster ne peut pas être redémarrée dans le nombre spécifié de tentatives au cours de la période spécifiée, l’hôte BizTalk en cluster supposera un état **n’a pas pu** dans la gestion du Cluster de basculement interface. Si un hôte BizTalk en cluster suppose un état **n’a pas pu** puis il doit être démarré manuellement dans la gestion du Cluster de basculement.  
  
     Par défaut, une ressource d’hôte BizTalk en cluster est configurée avec les valeurs de redémarrage suivantes sur un cluster de serveurs qui sont disponibles sur le **avancé** onglet de la **propriétés** boîte de dialogue pour le cluster ressource :  
  
    |**Option**|**Valeur**|  
    |----------------|---------------|  
    |Redémarrer|**True**<br /><br /> Le service de cluster tente de redémarrer la ressource lorsqu'elle s'arrête.|  
    |Affecter le groupe|**True**<br /><br /> Le service de cluster tente de redémarrer la ressource en basculant tous les groupe de ressources sur un autre nœud du cluster.|  
    |Seuil de redémarrage|**3**<br /><br /> Spécifie le nombre maximal de tentatives de redémarrage autorisées au cours de la **période de redémarrage**. Si le nombre de tentatives de redémarrage dépasse le **seuil de redémarrage** pendant la **période de redémarrage** ensuite la ressource de cluster suppose un état **n’a pas pu** et le Cluster service n’essaie pas de plus de démarrages.|  
    |Période de redémarrage|**900 secondes**<br /><br /> Indique la période au cours de laquelle les tentatives de démarrage sont comptées. Le **période de redémarrage** est initialisé lors de la première tentative de redémarrage. Le nombre de tentatives de redémarrage est réinitialisé sur zéro si la **seuil de redémarrage** n’est pas dépassé pendant la durée de la **période de redémarrage**.|  
  
     Les valeurs de redémarrage par défaut imposent au cluster Windows Server de tenter de redémarrer jusqu'à trois fois dans un délai de 900 secondes une instance ayant échoué de l'hôte BizTalk mis en cluster. Étant donné que la **affecter le groupe** a la valeur **True**, toute tentative de redémarrage fera basculer le groupe de ressources de cluster vers un autre nœud de cluster. Si une instance ayant échoué d’un hôte BizTalk en cluster ne peut pas être redémarrée dans le nombre spécifié de tentatives au cours de la période spécifiée, alors que l’hôte BizTalk en cluster supposera un état **n’a pas pu** dans administrateur de Cluster. Si un hôte BizTalk en cluster suppose un état **n’a pas pu**, puis il doit être démarré manuellement dans l’administrateur de Cluster.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-configure-a-biztalk-host-as-a-cluster-resource"></a>Pour configurer un hôte BizTalk en tant que ressource de cluster  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, développez **Administration de BizTalk Server**, cliquez pour développer **groupe BizTalk [\<nom_serveur\>:\<gestion base de données\>]**, cliquez pour développer **paramètres de plateforme**, puis cliquez pour développer **hôtes**. La liste des hôtes apparaît sous le dossier.  
  
2.  Cliquez sur l’ordinateur hôte que vous souhaitez mettre en cluster et puis **Cluster**.  
  
    > [!NOTE]
    >  Assurez-vous que vous avez créé une instance de l'hôte sur tous les nœuds membres constituant des propriétaires possibles d'un groupe de clusters avant d'ajouter à ce groupe l'hôte BizTalk.  
  
3.  Dans la liste déroulante des groupes de cluster disponibles, sélectionnez le groupe de clusters dans lequel vous souhaitez que l'hôte s'exécute.  
  
    > [!NOTE]
    >  Dès qu'un hôte est mis en cluster, il est mis en ligne et commence à traiter des documents pour tous les gestionnaires d'adaptateur ou les orchestrations configurés pour s'exécuter sur l'hôte.  
  
#### <a name="to-uncluster-a-clustered-biztalk-host"></a>Annulation d’un hôte BizTalk en cluster  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, développez **Administration de BizTalk Server**, cliquez pour développer **groupe BizTalk [\<nom_serveur\>:\<gestion base de données\>]**, cliquez pour développer **paramètres de plateforme**, puis cliquez pour développer **hôtes**. La liste des hôtes apparaît sous le dossier.  
  
2.  Cliquez sur l’ordinateur hôte en cluster que vous souhaitez annuler, puis sélectionnez **Annuler**.  
  
    > [!NOTE]
    >  Lorsque la mise en cluster d'un hôte est annulée, toutes les instances associées à cet hôte sont arrêtées et celui-ci arrête de traiter des documents pour tous les gestionnaires d'adaptateur ou les orchestrations configurés pour s'exécuter sur l'hôte.