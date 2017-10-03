---
title: Commande RemoveApp | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 323290ae-8498-4ad6-9b06-a1d54640250e
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9808b43ba07434793403d175885694f67530dae0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="removeapp-command"></a>Commande RemoveApp
Supprime d'une base de données de gestion BizTalk une application BizTalk ou tous les artefacts que cette base de données contient. Cela ne désinstallera pas l’application. Pour obtenir des instructions à ce sujet, consultez [comment désinstaller une Application BizTalk](../core/how-to-uninstall-a-biztalk-application.md).  
  
 L'opération de suppression échoue dans les cas suivants :  
  
-   **L’application n’est pas arrêtée.** Pour obtenir des instructions sur l’arrêt d’une application, consultez [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md). Le **ApplicationManager** l’exemple de kit de développement logiciel est installé dans le  *\<exemples de chemin >\\*répertoire Admin\ExplorerOM\ montre comment démarrer ou arrêter par programme un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.  
  
-   **Autres applications contiennent des références à l’application.** Si d'autres applications contiennent des références à l'application que vous souhaitez supprimer, vous devez d'abord supprimer les références dans les autres applications. Pour obtenir des instructions, consultez [comment supprimer une référence à une autre Application](../core/how-to-remove-a-reference-to-another-application.md).  
  
-   **L’application contient un groupe de ports d’envoi dont un port d’envoi dans une autre application est un membre.** Dans ce cas, vous devez désinscrire le port d'envoi membre avant de supprimer l'application. Pour obtenir des instructions, consultez [comment désinscrire un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-unenlist-a-send-port-or-send-port-group.md).  
  
-   **L’application contient un port d’envoi qui est référencé par un tiers.** Vous pouvez supprimer la référence du tiers ou placer le port d'envoi dans une application différente. Pour obtenir des instructions sur la réalisation de ces tâches, consultez [comment afficher ou modifier un tiers](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca) ou [comment déplacer un artefact vers une autre Application](../core/how-to-move-an-artifact-to-a-different-application.md).  
  
-   **L’application est l’application par défaut.** Si vous souhaitez la supprimer, vous devez d'abord définir une autre application en tant qu'application par défaut. Pour obtenir des instructions, consultez [la modification de l’Application par défaut](../core/how-to-change-the-default-application.md).  
  
-   **Une orchestration dans l’application est inscrite, démarré, ou a une instance suspendue.** Pour plus d’informations sur les orchestrations, consultez [la gestion des Orchestrations](../core/managing-orchestrations.md).  
  
> [!NOTE]
>  Si l’application contient une stratégie qui se trouve dans un état déployé, la stratégie n’est pas supprimée de la base de données du moteur de règles et continue à afficher dans le dossier stratégies sous le \<tous les artefacts > nœud d’application de la console Administration de BizTalk console. Si vous ajoutez la stratégie à une autre application, elle reste à l'état déployé.  
  
## <a name="usage"></a>Utilisation  
 **« ApplicationName » BTSTask RemoveApp :** *valeur* [**/Server :***valeur*] [**/Database :**  *valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis| Description|  
|---------------|--------------|-----------------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Oui|Nom de l'application BizTalk à supprimer. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
|**/ Serveur** (ou **/S**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/D**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask RemoveApp /ApplicationName:MyApplication**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)   
 [Annulation du déploiement des Applications BizTalk](../core/undeploying-biztalk-applications.md)