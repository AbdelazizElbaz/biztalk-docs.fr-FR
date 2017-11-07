---
title: "En cours d’exécution Orchestrations2 | Documents Microsoft"
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
- creating strong name keys
- compiling orchestrations
- host instances, stopping and restarting
- deployment, orchestrations
- orchestrations, compiling
- orchestrations, deploying
- stopping host instances
- restarting host instances
ms.assetid: a098d552-d302-44f6-9af9-d77d16549fd3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a2d6ef6752965c1f20c695dacb06ff348089054
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="running-orchestrations"></a>Orchestrations en cours d’exécution
Les procédures suivantes expliquent comment construire, déployer, lier et démarrer une orchestration.  
  
## <a name="creating-a-strong-name-key"></a>Création d'une clé de nom fort  
  
#### <a name="to-create-a-strong-name-key"></a>Pour créer une clé de nom fort  
  
1.  Ouvrir un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes.  
  
2.  Accédez aux répertoires d'un projet existant, puis appuyez sur ENTRÉE.  
  
     Exemple :  
  
     **\<lecteur > : \Adapter_Install\biztalk\my_project**  
  
3.  Tapez ce qui suit à l'invite de commandes, puis appuyez sur ENTRÉE :  
  
     `sn -k SSOSchedule.snk`  
  
## <a name="compiling-and-deploying-an-orchestration"></a>Compilation et déploiement d'une orchestration  
  
#### <a name="to-compile-and-deploy-an-orchestration"></a>Pour compiler et déployer une orchestration  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Explorateur de solutions, cliquez sur le **SSOSchedule** le projet, puis sélectionnez **propriétés**.  
  
2.  Cliquez sur **propriétés communes**, puis développez le **Assembly** nœud.  
  
3.  Entrez le chemin d’accès à SSOSchedule.snk dans les **fichier de clé d’Assembly** zone de texte.  
  
4.  Vérifiez que configuration\déploiement\serveur est un point (.) ou le nom de votre ordinateur, puis cliquez sur **OK**.  
  
5.  Dans l’Explorateur de solutions, cliquez sur **SSOSchedule**, puis cliquez sur **reconstruire**.  
  
6.  Avec le bouton droit **SSOSchedule**, puis cliquez sur **déployer**.  
  
## <a name="starting-the-orchestration"></a>Démarrage de l'orchestration  
  
#### <a name="to-start-the-orchestration"></a>Pour démarrer l'orchestration  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server.**  
  
2.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez l’élément application, puis sur **Orchestrations**.  
  
3.  Dans le volet de détails, cliquez sur l’orchestration, sur **Démarrer**.  
  
## <a name="stopping-and-restarting-a-host-instance"></a>Arrêt et redémarrage d'une instance de l'hôte  
 Une l'exemple déployé, vous devez redémarrer l'instance de l'hôte.  
  
#### <a name="to-stop-and-restart-a-host-instance"></a>Pour arrêter et redémarrer une instance de l'hôte  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server.**  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur  **Instances de l’hôte**.  
  
3.  Dans le volet droit, cliquez sur l’instance d’hôte (par exemple, le nom d’ordinateur), puis cliquez sur **arrêter**.  
  
     L’état de l’instance d’hôte devient **arrêté**.  
  
4.  Dans le volet droit, cliquez sur l’instance d’hôte, puis cliquez sur **Démarrer**.  
  
     L’état de l’instance d’hôte devient **attente de démarrage**.  
  
     Pour modifier l’état à **en cours d’exécution** et cliquez sur **Actualiser**, ou cliquez sur l’instance d’hôte, puis cliquez **Actualiser**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser l’adaptateur](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)