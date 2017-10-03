---
title: Sauvegarde des Applications BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b51e3ae6-08ed-48ca-8977-13f46144a5fa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d125a1430aa2d044abba7632fa31a9c89f2bc50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-biztalk-server-applications"></a>Sauvegarde d'applications BizTalk Server
Pour être certain de pouvoir récupérer un système BizTalk Server après une défaillance matérielle, il est important de conserver des sauvegardes correctement effectuées. Dans le cadre de la conservation des sauvegardes, exportez vos applications BizTalk sur un serveur distant avant de les sauvegarder.  
  
 Ensuite, lors de la restauration des bases de données BizTalk Server et de la réinstallation de BizTalk Server, importez ces applications. Pour plus d’informations sur comment exporter et importer des applications, consultez [déploiement et la gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md).  
  
 Vous devez exporter les fichiers .msi de toutes les applications BizTalk déployées sur l'ordinateur, puis les enregistrer dans l'emplacement de sauvegarde (autre serveur). Les fichiers .msi permettent de réinstaller les ressources requises par BizTalk Server après avoir récupéré l'ordinateur de destination. Vous devez vérifier que les fichiers .msi incluent toutes les ressources requises et que vous avez spécifié les actions à effectuer lors de l'installation .msi de ces ressources. Si votre application BizTalk dépend d'un assembly utilisateur ou d'autres fichiers DLL non inclus dans les fichiers .msi, vous devez les sauvegarder séparément.  
  
 Le processus d'exportation de l'application est identique pour les scénarios de routage basé sur le contenu et les scénarios disposant d'orchestrations. Vous devez répéter ce processus après chaque modification apportée aux applications BizTalk. Pour plus d’informations, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde d’un ordinateur exécutant BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md)