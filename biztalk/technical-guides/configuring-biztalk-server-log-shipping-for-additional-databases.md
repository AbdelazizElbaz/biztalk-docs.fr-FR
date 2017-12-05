---
title: "Configurer les journaux de BizTalk pour les bases de données supplémentaires | Documents Microsoft"
description: "Ajouter des bases de données personnalisées à la tâche de sauvegarde de BizTalk Server et pour l’envoi de journaux de BizTalk Server"
ms.custom: 
ms.date: 11/01/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc2ae67-5cb9-4d53-9bf7-c88f84914960
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b1ceb760a5f842f8c24a372d793e0074114b81f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="configuring-biztalk-server-log-shipping-for-additional-databases"></a>Configuration des journaux de BizTalk Server pour les bases de données supplémentaires

## <a name="overview"></a>Vue d'ensemble
Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], travaux ajouté à la tâche de sauvegarde de BizTalk Server est automatiquement ajoutés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction. Vous n’avez pas à effectuer des étapes supplémentaires pour configurer l’envoi de journaux pour les nouvelles bases de données sont ajoutées à la tâche de sauvegarde de BizTalk Server. Toutefois, veillez à ajouter des bases de données personnalisées comme approprié sous le \<OtherDatabases\> section du fichier SampleUpdateInfo.xml. [Configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md) et [sauvegarde des personnalisé bases de données](../core/how-to-back-up-custom-databases.md) fournit quelques conseils.
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de la copie des journaux de transaction BizTalk Server](../technical-guides/configuring-biztalk-server-log-shipping.md)