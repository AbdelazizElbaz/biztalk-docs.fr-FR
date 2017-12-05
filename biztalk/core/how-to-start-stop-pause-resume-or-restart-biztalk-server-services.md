---
title: "Étapes pour redémarrer les services ou arrêter | Documents Microsoft"
description: "Démarrer, arrêter, suspendre, reprendre ou redémarrer le serveur BizTalk des services, ou d’arrêter l’ordinateur BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d6449ba-2892-49c6-a697-847608d10ec5
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9860625480c2c3e469736989415b4e1510cf6707
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="restart-biztalk-services-or-shut-down-the-biztalk-server"></a>Redémarrez les services BizTalk ou arrêter le serveur BizTalk

Le tableau suivant fournit la liste des services BizTalk Server que vous pouvez démarrer, arrêter, suspendre, reprendre ou redémarrer :  
  
|Nom|Description|Type de démarrage|Dépendances|  
|----------|-----------------|------------------|------------------|  
|Groupe BizTalk des services BizTalk :  *\<BizTalkServerApplication\>*|Fournit le service de l'application de BizTalk Server.|Automatique|-Enterprise Single Sign-On (SSO de) Service<br />-Journal des événements<br />-Appel de procédure distante (RPC)|  
|Service d'authentification unique de l'entreprise|Fournit des services d'authentification unique aux applications d'entreprise.|Automatique|Avec SQL Server installé localement :<br /><br /> -Application système COM +<br />-Appel de procédure distante (RPC)<br />-SQL Server (MSSQLSERVER)<br /><br /> Avec SQL Server installé à distance :<br /><br /> -Application système COM +<br />-Appel de procédure distante (RPC) None|  
|Service de mise à jour du moteur des règles|Signale aux utilisateurs le déploiement ou l'annulation du déploiement des stratégies.|Automatique|Aucune|  
  
 
## <a name="start-stop-pause-resume-or-restart-a-biztalk-server-service"></a>Démarrer, arrêter, suspendre, reprendre ou redémarrer un service BizTalk Server  
 Vous pouvez démarrer, arrêter, suspendre, reprendre ou redémarrer un service BizTalk Server à l’aide de Services.msc, ou à l’aide de l’invite de commandes.

### <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure, vous devez être membre du groupe Administrateurs sur l'ordinateur local, ou l'autorité appropriée doit vous avoir été déléguée. Si l'ordinateur est rattaché à un domaine, les membres du groupe Administrateurs du domaine peuvent être en mesure d'effectuer cette procédure. Pour une sécurité optimale, il est conseillé d'utiliser l'option Exécuter en tant que pour effectuer cette procédure. 
  
### <a name="use-services-in-control-panel"></a>Utiliser les Services dans le panneau de configuration  
  
1.  Ouvrez Services. Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.  
  
2.  Cliquez sur le service BizTalk Server approprié, puis sur **Démarrer**, **arrêter**, **Pause**, **reprise**, ou  **Redémarrez**.  
  
### <a name="use-a-command-prompt"></a>Utilisez une invite de commandes  
  
1.  Dans le menu Démarrer, cliquez sur **invite de commandes**, sélectionnez **plus**, puis sélectionnez **exécuter en tant qu’administrateur**
  
2.  Tapez une des options suivantes, où *ServiceName* est le nom du service BizTalk Server que vous souhaitez démarrer, arrêter, suspendre ou reprendre :  
  
    -   Pour démarrer un service, entrez :  
  
         **Net start** *ServiceName*  
  
    -   Pour arrêter un service, entrez :  
  
         **net stop** *ServiceName*  
  
    -   Pour suspendre un service, entrez :  
  
         **net pause** *ServiceName*  
  
    -   Pour reprendre un service, entrez :  
  
         **NET continue,** *ServiceName*  

    |Service BizTalk|NomService|  
    |---|---|  
    |Groupe BizTalk des services BizTalk : BizTalkServerApplication|btssvc$biztalkserverapplication|  
    |Service d'authentification unique de l'entreprise|Entsso|  
    |Service de mise à jour du moteur des règles|ruleengineupdateservice|
  
## <a name="shut-down-biztalk-server"></a>Arrêt de BizTalk Server  

### <a name="prerequisites"></a>Conditions préalables  
-   Connectez-vous avec un compte qui est membre du groupe Administrateurs local sur le serveur BizTalk que vous souhaitez arrêter. Cette condition est nécessaire pour arrêter les services.  
-   Connectez-vous avec un compte qui est membre du groupe Administrateurs BizTalk Server ou du groupe d’opérateurs BizTalk Server. 

### <a name="task-overview"></a>Vue d’ensemble de la tâche
1.  Désactivez les emplacements de réception, et arrêtez les orchestrations et les ports d'envoi en effectuant un arrêt partiel de chaque application active. Vous devez effectuer un arrêt complet uniquement si vous envisagez de supprimer ou de redéployer une application. Pour plus d’informations, consultez [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
2.  Arrêtez les instances d'hôte. Pour plus d’informations, consultez [comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md).  
  
3.  Arrêtez les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Consultez **comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server** (dans cette rubrique).
  
4.  Arrêtez les services IIS (Internet Information Services) ou les pools d'applications et sites Web [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si vous allez procéder à l'arrêt complet du serveur, ignorez cette étape. Si vous procédez à l'arrêt de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à des fins de maintenance, ou en vue de déployer/d'annuler le déploiement d'une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez effectuer cette étape. L'arrêt des sites Web et pools d'applications associés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'affecte pas l'exécution des autres processus IIS.  
  
     Les modalités d'exécution de cette étape dépendent en partie de la version d'IIS que vous exécutez. IIS 6 permet d’arrêter les pools d’applications et sites Web. Cette version permet également d'arrêter le service d'administration d'IIS pour interrompre toute l'activité d'IIS, notamment les pools d'applications et les sites Web. IIS 7.0 est plus modulaire qu’IIS 6.0, et il n’existe aucun commutateur unique, que vous pouvez utiliser pour arrêter toutes les activités d’IIS 7.0, vous devez arrêter séparément les sites Web et les pools d’applications.  
  
     Pour obtenir la liste des pools d’applications et des applications virtuelles (sites Web et services Web) utilisées par BizTalk Server, consultez [configurer BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).  
  
 Pour plus d’informations sur le démarrage et arrêt des pools d’applications dans IIS, consultez [http://go.microsoft.com/fwlink/?LinkID=140513](http://go.microsoft.com/fwlink/?LinkID=140513).  
  
 Pour plus d’informations sur le démarrage et arrêt du serveur Web dans IIS, consultez [http://go.microsoft.com/fwlink/?LinkId=140695](http://go.microsoft.com/fwlink/?LinkId=140695).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md)   
 [Comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md)   