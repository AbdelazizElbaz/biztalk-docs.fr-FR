---
title: "Collecte des Exceptions et la persistance de la charge utile à l’aide du processeur d’Exception ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52650eed-e760-4ade-bc3f-2b5b2a1c43ff
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9dd0ec42ab60636202a8ff99fa8fab8d96a95a19
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="collecting-exceptions-and-persisting-the-payload-using-the-esb-exception-processor"></a>Collecte des Exceptions et la persistance de la charge utile à l’aide du processeur d’Exception ESB
Dans ce cas de figure, le Gestionnaire d’exceptions pour une orchestration publie un message d’erreur ESB dans la boîte de Message BizTalk Server, ou bien le mécanisme de routage des messages a échoué BizTalk génère un message d’erreur. Un port d’envoi, préconfiguré avec le composant de pipeline encodeur d’Exception ESB, s’abonne à des types de message d’erreur. Il traite les messages d’erreur, puis les en tant que fichiers de disque que vous pouvez consulter à l’aide d’InfoPath, comme illustré dans la Figure 1.  
  
 ![Collecte de charge utile d’Exceptions](../esb-toolkit/media/ch3-collectingexceptionspayload.gif "Ch3-CollectingExceptionsPayload")  
  
 **Figure 1**  
  
 **Capture d’un message d’erreur et les rend persistantes dans un fichier de disque**  
  
 La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut les éléments suivants :  
  
-   **Un préconfigurés port d’envoi qui utilise le pipeline d’envoi ESB erreur processeur.** Vous pouvez configurer ce port d’envoi en fonction de vos besoins spécifiques.  
  
-   **L’exemple de gestionnaire d’exceptions Message persistance personnalisée.** Cet exemple montre comment un gestionnaire d’exceptions génériques faiblement couplée peut recevoir des messages d’erreur, extraire les messages BizTalk Server qu’ils contiennent, normalisent et enrichissement les messages et les écrivent sous forme de fichiers de disque dans le système de fichiers.  
  
-   **L’exemple de routage des messages a échoué BizTalk.** Cet exemple montre comment l’infrastructure de gestion d’Exception ESB normaliser et enrichir les messages d’erreur en mode natif par le mécanisme de routage des messages d’échec dans BizTalk Server.  
  
 Pour plus d’informations, consultez [exécution de l’exemple Gestionnaire de Message de persistance personnalisé Exception](../esb-toolkit/running-the-message-persisting-custom-exception-handler-sample.md) et [le BizTalk Échec de routage ESB traitement exemple de Message en cours d’exécution](../esb-toolkit/running-the-biztalk-failed-message-routing-esb-processing-sample.md).