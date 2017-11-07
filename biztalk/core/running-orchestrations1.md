---
title: "En cours d’exécution Orchestrations1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong name keys, creating
- orchestrations
- host instances, stopping and restarting
- orchestrations, compiling
- orchestrations, deploying
ms.assetid: b992bdba-630d-4f28-aca8-c568f3c27968
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b4559a3d362d0d778c4d60cc485fa79e8e05efe
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="running-orchestrations"></a>Orchestrations en cours d’exécution
Les procédures suivantes expliquent comment construire, déployer, lier et démarrer une orchestration.  
  
## <a name="creating-a-strong-name-key"></a>Création d'une clé de nom fort  
  
#### <a name="to-create-a-strong-name-key"></a>Pour créer une clé de nom fort  
  
1.  Démarrez une invite de commandes [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Accédez à un projet existant, par exemple, \<lecteur > : \Adapter_Install\biztalk2010\my_project.  
  
3.  Tapez la commande suivante à l'invite, puis appuyez sur ENTRÉE :  
  
     `sn -k SSOSchedule.snk`  
  
## <a name="compiling-and-deploying-an-orchestration"></a>Compilation et déploiement d'une orchestration  
  
#### <a name="to-compile-and-deploy-an-orchestration"></a>Pour compiler et déployer une orchestration  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur le projet SSOSchedule, puis sélectionnez **propriétés**.  
  
2.  Cliquez sur **propriétés communes**, puis développez le **Assembly** nœud.  
  
3.  Entrez le chemin d’accès à SSOSchedule.snk dans les **fichier de clé d’Assembly** zone de texte.  
  
4.  Vérifiez que configuration\déploiement\serveur contient un point (.) ou le nom de votre ordinateur, puis cliquez sur **OK**.  
  
5.  Dans l’Explorateur de solutions, cliquez sur **SSOSchedule**, puis cliquez sur **reconstruire**.  
  
6.  Cliquez sur le **SSOSchedule**, puis cliquez sur **déployer**.  
  
## <a name="starting-the-orchestration"></a>Démarrage de l'orchestration  
  
#### <a name="to-start-the-orchestration"></a>Pour démarrer l'orchestration  
  
1.  Dans la console Administration de BizTalk Server, sélectionnez l'orchestration que vous souhaitez démarrer.  
  
2.  Avec le bouton droit de l’orchestration, puis cliquez sur **Démarrer**.  
  
## <a name="stopping-and-restarting-a-host-instance"></a>Arrêt et redémarrage d'une instance de l'hôte  
 Une fois l'exemple déployé, vous devez redémarrer l'instance de l'hôte.  
  
#### <a name="to-stop-and-restart-a-host-instance"></a>Pour arrêter et redémarrer une instance de l'hôte  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis sélectionnez **Administration de BizTalk Server.**  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, double-cliquez sur le **Microsoft BizTalk Server (local)** nœud, puis développez **hôtes**.  
  
3.  Dans le volet gauche, sélectionnez le **BizTalkServerApplication**.  
  
4.  Dans le volet droit, cliquez sur l’instance d’hôte (par exemple, le nom d’ordinateur), puis cliquez sur **arrêter**.  
  
     L’état de l’instance d’hôte devient **arrêté**.  
  
5.  Dans le volet droit, cliquez sur l’instance d’hôte, puis cliquez sur **Démarrer**.  
  
     L’état de l’instance d’hôte devient **attente de démarrage**.  
  
     Pour modifier l’état à **en cours d’exécution**, cliquez sur **Actualiser**, ou cliquez sur l’instance d’hôte, puis cliquez **Actualiser**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de la carte](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)