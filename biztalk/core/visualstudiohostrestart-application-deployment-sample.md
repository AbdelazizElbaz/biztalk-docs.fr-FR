---
title: "VisualStudioHostRestart (exemple de déploiement d’Application) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0b82627-1552-479d-a083-cdc9fe4843c3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d98a3a5e497a4476de897c8008f3a9976812209a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="visualstudiohostrestart-application-deployment-sample"></a>VisualStudioHostRestart (exemple de déploiement d'application)
Cette rubrique décrit l'utilisation de l'exemple de script VisualStudioHostRestart pour redémarrer l'instance d'un hôte exécutée sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur l'ordinateur local. Vous pouvez utiliser ce script lors du redéploiement des assemblys dans Visual Studio afin que le moteur d'exécution BizTalk Server récupère les modifications immédiatement. Vous pouvez également utiliser l'option pour redémarrer les instances de l'hôte, que vous pouvez définir dans les propriétés de déploiement du projet. Pour plus d’informations, consultez [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple de script effectue les actions ci-dessous dans l'ordre suivant :  
  
1.  arrêt des instances de l'hôte In-process sur l'ordinateur local ;  
  
2.  démarrage des instances de l'hôte In-process sur l'ordinateur local.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L’exemple se trouve dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dossier d’installation, comme suit :  *\<exemples de chemin\>*\Application Deployment\VisualStudioHostRestart.  
  
 L'exemple inclut le fichier suivant :  
  
-   RestartBizTalkHostInstances.vbs  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Les procédures suivantes permettent d'exécuter l'exemple.  
  
### <a name="to-run-the-sample"></a>Pour exécuter l’exemple  
  
-   Exécutez RestartBizTalkHostInstances.vbs.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications (dossier d’exemples BizTalk Server)](../core/application-deployment-biztalk-server-samples-folder.md)   
 [Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)   
 [Déploiement des applications BizTalk](../core/deploying-biztalk-applications.md)