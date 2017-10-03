---
title: "Instanciation et initialisation un adaptateur de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5cb5ba7-e2b5-49d2-adf5-a8df0bb81def
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 565712faecf11b728c4f552798b1e3daebf962f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instantiating-and-initializing-a-receive-adapter"></a>Instanciation et initialisation d'un adaptateur de réception
Dès qu'un adaptateur de réception est instancié, il est initialisé par le moteur de messagerie, et ce dernier appelle QueryInteraface pour IBTTransportControl. Il appelle ensuite IBTTransportControl**. Initialiser** en passant des proxy de transport de l’adaptateur, l’adaptateur la stocke dans une variable membre. Ensuite, le moteur appelle **QueryInterface** pour **IPersistPropertyBag**. Il s’agit d’une interface facultative ; Si l’adaptateur implémente, la configuration du gestionnaire est passée à l’adaptateur dans le **charge** appel de méthode. La dernière étape de l'initialisation d'un adaptateur de réception consiste à transmettre la configuration du point de terminaison à l'adaptateur. Au cours de cette phase le moteur appelle **IBTTransportConfig.AddReceiveEndpoint** une fois pour chaque point de terminaison actif, en passant l’URI pour le point de terminaison, la configuration spécifique de la carte pour le point de terminaison et la configuration de BizTalk pour ce point de terminaison.  
  
 Le schéma ci-dessous illustre cette séquence d'appels d'API : L’adaptateur implémente les interfaces en bleu.  
  
 ![](../core/media/sequence-of-init-calls.gif "Sequence_of_init_calls")  
  
 **Conseil pour l’implémentation :** en général, adaptateurs ne doivent pas empêcher le moteur de messagerie telles que **IBTTransportControl.Initialize**, **IPersistPropertyBag.Load**et **IBTTransportConfig.AddReceiveEndpoint**. Un traitement excessif dans ces appels peut avoir des conséquences négatives sur le délai de démarrage du service.  
  
 Tous les adaptateurs de réception qui disposent d'un ou plusieurs emplacements de réception sont créés au démarrage du service. Tous les adaptateurs de réception sont asynchrones et prennent en charge le traitement par lot. Ils peuvent être de type In-process ou isolés. Pour plus d’informations sur les variables de l’adaptateur de réception, voir [Variables d’adaptateur](../core/adapter-variables.md).