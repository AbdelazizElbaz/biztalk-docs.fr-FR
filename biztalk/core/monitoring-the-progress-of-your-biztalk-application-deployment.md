---
title: "Surveillance de la progression du déploiement de votre Application BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring, deploying
- applications, monitoring
- deploying [applications], monitoring
- monitoring, applications
ms.assetid: a69a8288-0203-440f-9805-52786525e193
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4eaa81067f5a413c689a4a51ac6b102d80782e2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-the-progress-of-your-biztalk-application-deployment"></a>Surveillance de la progression du déploiement de votre application BizTalk
Vous pouvez surveiller la progression du déploiement de votre application BizTalk de deux manières :  
  
-   **Journal d’installation BizTalk**: vous pouvez consulter l’installation du journal de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère. Les journaux d’installation se trouvent dans %SystemDrive%\Documents and paramètres\\<*utilisateur actuel*> Data\Microsoft\\[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]\Deployment.  
  
-   **Journal des événements local**: vous pouvez suivre la progression d’une installation dans le journal des événements local. Vous pouvez ainsi suivre les actions d'installation personnalisée pour chaque serveur.  
  
-   **Journal de Windows Installer**: le programme d’installation de Microsoft Windows crée un fichier journal sur l’ordinateur local qui enregistre les actions d’une action personnalisée. Vous pouvez spécifier ce fichier journal à l'aide de l'option /log de la commande msiexec. Pour plus d'informations, consultez la documentation de Microsoft Installer.  
  
> [!IMPORTANT]
>  Le déploiement ou l'annulation du déploiement d'un schéma de propriété peut exposer des données sensibles, et par la suite les exposer lors du suivi. Chaque fois qu'un assembly contenant un schéma de propriété est déployé ou que son déploiement est annulé, l'observateur d'événements consigne un événement dans le journal des événements des applications Windows. Vous devez rechercher ces messages dans le journal des événements afin de vous assurer que l'ensemble des activités de déploiement d'assembly sont conformes à vos stratégies en matière de traitement des données sensibles. (Le message généré dans le journal des événements pour le déploiement est : « l’utilisateur « {{1} » déployé l’assembly « {0} » qui contient les schémas de propriété. » Le message généré dans le journal des événements pour l’annulation du déploiement est : « l’utilisateur « {{1} » a annulé déploiement de l’assembly « {0} » qui contient les schémas de propriété ».)  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’Applications BizTalk](../core/deploying-biztalk-applications.md)