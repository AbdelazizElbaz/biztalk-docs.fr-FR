---
title: "Configuration d’un hôte de suivi dédié | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f997bcc2-08fd-4e9a-ba44-542ec8460d6d
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3651d91f9c4b28fae30182ed6ddd18cde1bb3f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-dedicated-tracking-host"></a>Configuration d’un hôte de suivi dédié
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]est optimisé pour le débit, afin de l’orchestration principale et les moteurs de messagerie ne pas réellement déplacent événements ou des messages directement aux bases de données de suivi BizTalk (DTA) ou l’analyse BAM (Business Activity), car cela aurait transférer ces moteurs leur principal tâche d’exécution de processus d’entreprise. Au lieu de cela, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] laisse les événements et les messages dans la base de données MessageBox et les marque comme nécessitant un déplacement vers les bases de données des suivis BizTalk ou d’analyse BAM. Un processus en arrière-plan (l’hôte de suivi), puis déplace les événements pour les bases de données des suivis BizTalk et l’analyse BAM, tout en un SQL Server Agent travail copie les messages suivis à la base de données des suivis BizTalk.  
  
## <a name="advantages-of-using-a-dedicated-tracking-host"></a>Avantages de l’utilisation d’un hôte de suivi dédié  
 Un hôte BizTalk qui héberge le suivi est chargé de déplacer le DTA et BAM de données de suivi à partir de la base de données MessageBox pour les bases de données de suivi BizTalk (DTA) et d’importation principale BAM. Ce déplacement de données de suivi a un impact sur les performances d’autres artefacts BizTalk qui s’exécutent dans le même ordinateur hôte qui héberge le suivi. Par conséquent, vous devez utiliser un hôte dédié qui ne fait rien, mais le suivi de l’hôte.  
  
 À l’aide d’un hôte de suivi dédié vous permet également d’arrêter les autres hôtes BizTalk sans interférer avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de suivi. Le déplacement des données en dehors de la base de données de suivi est essentiel pour une intégrité [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système. Si l’hôte BizTalk responsable du déplacement des données de suivi dans le groupe BizTalk est arrêté, le service de décodage de données de suivi ne fonctionnera pas. L’impact de ce est comme suit :  
  
-   HAT des données de suivi n’est pas déplacé à partir de la base de données MessageBox à la base de données des suivis BizTalk.  
  
-   Données de suivi BAM n’est pas déplacé à partir de la base de données MessageBox à la base de données d’importation principale BAM.  
  
-   Étant donné que les données ne sont pas déplacées, il ne peut pas être supprimé à partir de la base de données MessageBox.  
  
-   Lorsque le service de décodage de données de suivi est arrêté, le suivi des intercepteurs seront toujours exécuter et écrire des données de suivi dans la base de données MessageBox. Si les données ne sont pas déplacées, cela entraîne la base de données MessageBox à être saturé, ce qui affecte les performances au fil du temps. Même si les propriétés personnalisées ne sont pas suivies ou les profils de l’analyse BAM ne sont pas définies, par défaut des données de suivi sont effectuées (telles que le pipeline de réception / envoyer des événements et des événements de l’orchestration). Si vous ne souhaitez pas exécuter le service de décodage de données de suivi, désactivez tous les suivi afin qu’aucun des intercepteurs d’enregistrement des données dans la base de données. Pour désactiver le suivi global, consultez [la désactivation du suivi Global](http://go.microsoft.com/fwlink/?LinkId=154193) (http://go.microsoft.com/fwlink/?LinkId=154193) utilisez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] la console Administration pour désactiver le suivi des événements de manière sélective.  
  
## <a name="optimizing-performance-for-a-dedicated-tracking-host"></a>Optimisation des performances pour un hôte de suivi dédié  
 Cet hôte doit être exécuté sur au moins deux ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (pour assurer la redondance dans les cas un tombe en panne). Pour des performances optimales, vous devez avoir suivi au moins une instance de l’hôte par base de données MessageBox. Le nombre réel de suivi des instances d’hôte doit être N + 1, où N = nombre de bases de données MessageBox. Le « + 1 » est pour assurer la redondance. Il en existe aucun avantage à l’ajout de plus, car le suivi qu’une seule instance de l’hôte ne peut déplacer les données pour une base de données MessageBox spécifique. Par conséquent, le verrouillage doit être jamais un problème. La supplémentaires d’une instance de l’hôte de suivi est ajouté pour la tolérance de panne ; Si un des suivi héberge instances échoue, l’instance supplémentaire suppose les droits de l’instance a échoué.  
  
 Un suivi instance d’hôte déplace les données de suivi pour les bases de données MessageBox spécifiques, mais il y aura jamais l’hôte de suivi plus d’une instance de déplacer les données d’une base de données MessageBox spécifique. Par exemple, si vous avez trois bases de données MessageBox et que deux instances de l’hôte de suivi, une des instances de l’hôte doit déplacer les données de deux bases de données MessageBox. Ajout d’une troisième instance de l’hôte de suivi distribue le suivi des hôtes de travail à un autre ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans ce scénario, ajout d’une quatrième instance de l’hôte de suivi ne serait pas distribuer n’importe quel hôte de suivi plus de travail, mais cela permet de fournir un fichier extra suivi d’instance d’hôte pour la tolérance de panne.  
  
 Pour plus d’informations sur le service Bus d’événements BAM, consultez les rubriques suivantes dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aider à :  
  
-   [La gestion de Service Bus d’événements BAM](http://go.microsoft.com/fwlink/?LinkId=154194) (http://go.microsoft.com/fwlink/?LinkId=154194)  
  
-   [Création d’Instances de Service Bus d’événements BAM](http://go.microsoft.com/fwlink/?LinkId=154195) (http://go.microsoft.com/fwlink/?LinkId=154195)  
  
## <a name="configuring-a-dedicated-tracking-host"></a>Configuration d’un hôte de suivi dédié  
 Pour effectuer la procédure de cette section, vous devez disposer des droits d’utilisateur suivants pour modifier les propriétés de l’hôte pour permettre le suivi de l’hôte :  
  
-   Vous devez être un membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  
  
-   Les droits suivants sont requis dans SQL Server :  
  
    -   Vous devez être un administrateur SQL Server ou un membre de la *db_owner* ou *db_securityadmin* rôles de base de données SQL Server dans la base de données (BizTalk DTADb), (des bases de données MessageBox (BizTalkMsgBoxDb) et la base de données d’importation principale BAM (BAMPrimaryImport).  
  
    -   Vous devez être membre du rôle sysadmin SQL Server sur tous les ordinateurs où il existe des bases de données MessageBox, ou un membre de la *db_owner* ou *db_ddladmin* rôle SQL Server pour toutes les bases de données MessageBox.  
  
#### <a name="to-enable-host-tracking"></a>Pour activer le suivi de l’hôte  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **hôtes**.  
  
3.  Dans le volet de détails, cliquez sur l’ordinateur hôte que vous souhaitez modifier, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés de l’hôte** boîte de dialogue le **général** onglet, activez ou désactivez **Options - Autoriser le suivi de hôte**, puis cliquez sur **OK**.  
  
     Cette case à cocher doit être activée pour indiquer que l'hôte charge le composant de suivi BizTalk pour traiter l'analyse du fonctionnement et les données d'entreprise. Si vous activez cette case, l'hôte actuel disposera d'un accès en lecture et en écriture aux tables de suivi de la base de données MessageBox et à la base de données des suivis. Par conséquent, les objets exécutés sur cet hôte bénéficieront aussi d'un accès en lecture/écriture à ces bases de données.  
  
     Si vous désactivez cette case, l'hôte disposera uniquement d'un accès en écriture aux tables de suivi de la base de données MessageBox et n'aura pas accès à la base de données des suivis BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Configuration de BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)