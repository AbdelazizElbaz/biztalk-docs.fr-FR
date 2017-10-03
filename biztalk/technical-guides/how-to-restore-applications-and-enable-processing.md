---
title: "La restauration des Applications et d’activer le traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83144965-a51a-481a-afd6-7f573b69badb
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65ae913d45f45b13458294863714823a41ff4e44
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-restore-applications-and-enable-processing"></a>La restauration des Applications et d’activer le traitement
Configurer les applications dans le groupe BizTalk et activer le traitement de l’application après avoir suivi les étapes décrites dans la rubrique [comment mettre à jour les ordinateurs Runtime](../technical-guides/how-to-update-the-runtime-computers.md).  
  
### <a name="to-enable-application-configuration-and-restore-application-processing"></a>Pour activer la configuration de l’application et de restauration de traitement de l’application  
  
1.  Exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Installation msi sur chaque serveur BizTalk server dans le groupe.  
  
2.  Exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fichier MSI de Configuration d’Application sur un serveur dans le groupe pour configurer l’application pour le site de récupération d’urgence. Les noms pour les emplacements de réception et envoyer des ports restent les mêmes. Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fichier MSI de Configuration d’Application met à jour les liaisons de sorte que ces artefacts pointent vers les emplacements appropriés dans l’environnement de récupération d’urgence.  
  
    > [!NOTE]  
    >  Si les emplacements de réception et d’envoyer des ports ne sont pas affectés par la perte du site de production, il ne peut pas être nécessaire de reconfigurer l’application à des emplacements spécifiques de la récupération d’urgence.  
  
3.  Restauration de traitement de l’application en activant l’application de tous les emplacements de réception, ports d’envoi et les instances d’hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’ordinateurs de l’exécution](../technical-guides/recovering-the-runtime-computers.md)