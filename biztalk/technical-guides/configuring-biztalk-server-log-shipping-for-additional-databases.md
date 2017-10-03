---
title: "Configuration des journaux de BizTalk Server pour les bases de données supplémentaires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
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
ms.openlocfilehash: 4b16b1d262b07ecaa62e87456f10bece225b3b34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-biztalk-server-log-shipping-for-additional-databases"></a>Configuration des journaux de BizTalk Server pour les bases de données supplémentaires
Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], travaux ajouté à la tâche de sauvegarde de BizTalk Server est automatiquement ajoutés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction. Vous n’avez pas à effectuer des étapes supplémentaires pour configurer l’envoi de journaux pour les nouvelles bases de données sont ajoutées à la tâche de sauvegarde de BizTalk Server. Toutefois, veillez à ajouter des bases de données personnalisées comme approprié sous le \<OtherDatabases > section du fichier SampleUpdateInfo.xml, comme décrit à l’étape 22 de [comment configurer le système de Destination pour l’envoi de journaux](http://go.microsoft.com/fwlink/?LinkId=151402) (http : / / go.microsoft.com/fwlink/ ? LinkId = 151402) dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="see-also"></a>Voir aussi  
 [Journaux de configuration de BizTalk Server](../technical-guides/configuring-biztalk-server-log-shipping.md)