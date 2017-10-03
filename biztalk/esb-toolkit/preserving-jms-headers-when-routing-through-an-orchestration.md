---
title: "Conserver les en-têtes JMS lors du routage via une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9a59ff3-0cbf-499f-92b2-cf5b808d8b3f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 362f41919a050b08bdba9c70c7771698ab71ce33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="preserving-jms-headers-when-routing-through-an-orchestration"></a>Préservation des en-têtes JMS lors du routage via une Orchestration
Dans ce cas de figure, les composants fournis avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extraire les en-têtes de Message Service JMS (Java) à partir d’un message entrant et les reconstruit ensuite dans le message sortant. Cela montre conservation des en-tête de message JMS et l’accès au contexte d’en-tête à partir d’à l’intérieur d’une orchestration, comme illustré dans la Figure 1.  
  
 ![Conservation de JMS](../esb-toolkit/media/ch3-preservingjms.gif "Ch3-PreservingJMS")  
  
 **Figure 1**  
  
 **Conservation des informations d’en-tête JMS tout au long d’une orchestration ESB et traitement**  
  
 L’exemple de composant de MQRFH2 JMS fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure et se compose de trois éléments suivants :  
  
-   Partie 1 illustre la conservation de l’en-tête de haute fidélité comme un message transite d’IBM WebSphere MQ, ESB et BizTalk Server et revenir à IBM WebSphere MQ.  
  
-   Partie 2 illustre comment le code dans une orchestration ESB peut accéder aux propriétés d’en-tête MQRFH2. Dans ce cas, le code modifie une propriété d’en-tête JMS pour spécifier le nom de file d’attente de destination.  
  
-   Partie 3 illustre une file d’attente des messages de chargement en masse et montre comment l’application achemine les messages pour les files d’attente de destination spécifiés en tant que partie du contenu du message.  
  
 Pour plus d’informations, consultez [installer et exécuter l’exemple de composant JMS MQRFH2](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md).