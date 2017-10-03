---
title: "Récupération d’urgence pour les ordinateurs exécutant BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10a2c26d-55d5-45d1-9fb1-e0664f005c21
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac655c10aaa443f9971fc40f7301a9e608e0e7eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="disaster-recovery-for-computers-running-biztalk-server"></a>Récupération d'urgence pour les ordinateurs exécutant BizTalk Server
Si l'ordinateur exécutant BizTalk Server dans votre organisation rencontre une défaillance matérielle irrécupérable, vous devez le remplacer par un ordinateur identique. Cela suppose que les bases de données BizTalk Server soient intactes, et que la défaillance affecte l'un des ordinateurs exécutant BizTalk Server.  
  
 Une des approches possibles consiste à conserver une image actualisée de chaque ordinateur exécutant BizTalk Server dans votre installation. Lorsqu'un ordinateur rencontre une défaillance matérielle, l'action de récupération consiste simplement à déployer l'image stockée sur un nouvel ordinateur. Les rubriques relatives à la récupération d'urgence proposent des solutions pour les situations dans lesquelles le stockage de telles images est impossible.  
## <a name="recovering-different-editions-of-biztalk-server"></a>Récupération des différentes éditions de BizTalk Server  
 L'approche de récupération diffère selon l'édition de BizTalk Server exécutée sur l'ordinateur.  
  
 Pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Édition Développeur et [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Édition Entreprise, l'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] par plusieurs ordinateurs est autorisée. En cas de défaillance d'un des ordinateurs exécutant BizTalk Server, vous pouvez préparer un ordinateur de remplacement à joindre au groupe BizTalk existant. Cet ordinateur peut être doté du même nom ou d'un autre nom.  
  
 Pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Édition Standard, vous ne pouvez pas joindre d'ordinateur à un groupe BizTalk. Cette approche n'est donc pas adaptée. À la place, vous devez définir un nouvel ordinateur et restaurer les paramètres de configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] afin d'utiliser cet ordinateur en remplacement. Pour plus d’informations, consultez [comment récupérer le groupe BizTalk](../core/how-to-recover-the-biztalk-group.md).  
  
## <a name="recovery-phases"></a>Étapes de Récupération  
 La récupération d'un ordinateur exécutant BizTalk Server comprend trois étapes :  
  
1.  **Préparation de la plate-forme de Base**  
  
     Cette étape a trait à la préparation d'un ordinateur avec la plateforme de base incluant le système d'exploitation, les composants logiciels requis et les composants BizTalk Server appropriés. Ce guide part du principe que vous disposez d'un ordinateur doté de la plateforme de base, des composants logiciels requis et des composants BizTalk Server avant de restaurer la configuration de BizTalk Server. Ce guide ne décrit pas la restauration de la plateforme de base.  
  
2.  **Restauration de la Configuration de BizTalk Server**  
  
     Cette étape part du principe que vous disposez d'un enregistrement des fonctionnalités configurées sur l'ordinateur défaillant, notamment une copie du fichier de configuration BizTalk Server pour cet ordinateur. Ce guide fournit des instructions relatives à la restauration de la configuration de BizTalk Server.  
  
3.  **Restauration des Applications BizTalk**  
  
     Cette étape a trait à la restauration des assemblys .NET connectés aux applications hébergées par les processus BizTalk Server sur l'ordinateur de remplacement. Les artefacts nécessaires (par exemple, assemblys utilisateur autres que les assemblys BizTalk) doivent être installés à leurs emplacements respectifs ou dans le GAC (Global Assembly Cache) de l'ordinateur. Ce guide fournit des instructions relatives à cette étape. Aucun autre script ou outil ne permet toutefois de restaurer les applications BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration de BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md)