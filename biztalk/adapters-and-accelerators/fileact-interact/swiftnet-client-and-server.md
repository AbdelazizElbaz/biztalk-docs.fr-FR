---
title: SWIFTNet Client et serveur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89d9f54f-af16-4f14-bbe4-8306758320d8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ea3a1b974a26f90d03bb65675c1c4e8966720f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swiftnet-client-and-server"></a>SWIFTNet Client et serveur
SWIFT utilise les termes du contrat client et serveur pour décrire l’envoi et la réception. Un client SWIFT est un processus qui appelle le lien SWIFTNet (SNL) pour lancer la communication sur SWIFTNet. Dans BizTalk Server, il s’agit de l’adaptateur d’envoi. Un serveur SWIFT est un programme qui est appelé par le SNL lorsque le trafic arrive sur SWIFTNet. Dans BizTalk Server, il s’agit de l’adaptateur de réception.  
  
 Ne confondez pas le client SWIFT et le serveur avec le client d’entreprise et le serveur. Par exemple, un client (organisation) s’appuie sur les services fournis par un serveur (organisation). Si le serveur (organisation) souhaite établir une communication avec le client (organisation), il doit utiliser une application cliente SNL pour ce faire, et le client (organisation) doit disposer d’une application du serveur SNL pour recevoir le trafic entrant. Cela est décrit dans la figure suivante.  
  
 ![Relation SWIFTNet entre le client et le serveur](../../adapters-and-accelerators/fileact-interact/media/7ad5d877-19d4-431f-9358-d5ae278cf945.gif "7ad5d877-19d4-431f-9358-d5ae278cf945")  
  
 SNL suppose que les applications client et serveur sont des fichiers exécutables démarrés à partir de l’invite de commandes. À la fois la liaison à la DLL de l’API SNL, qui communique avec le processus d’instance SNL réel.  
  
## <a name="snl-client-applications"></a>Applications clientes SNL  
 Les applications clientes SNL s’appuient sur l’API SwCall décrites ci-dessous. Techniquement parlant, une application cliente classique peut être décrite comme suit :  
  
```  
Main:  
  Initialize SNL API  
  Repeat  
    Call SwCall API  
  Until shutdown  
```  
  
 ID du processus client SNL applications doivent s’exécuter dans un processus, car SNL fait référence à du contexte du client par SNL synchronise les appels qui utilisent des ressources Tuxedo SwCall. Par conséquent, qu’un thread client unique à la fois peut exécuter efficacement un SwCall.  
  
 Le client prend en charge le mode de communication synchrone. Cela signifie que le retour sur le SWCall se produit lorsque la réponse est renvoyée à partir du serveur. Le SwCall suivant peut être effectué qu’après ce retour.  
  
## <a name="snl-server-applications"></a>Applications du serveur SNL  
 Applications du serveur SNL sont légèrement plus complexes que les applications clientes. Applications serveur inscrivent des fonctions de rappel avant d’effectuer un appel bloquant dans la DLL SNL. Techniquement parlant, une application classique de serveur peut être décrite comme suit :  
  
```  
Main:  
  Initialize SNL API  
  Call SwRegisterSwCallback, registering the Callback function  
  Call SwServer, block and receive callbacks  
  
Callback(Request):  
  Process Request  
  Return Response  
```  
  
 L’application de serveur peut appeler l’API SwCall dans la fonction de rappel. Dans certains cas, il doit appeler SwCall pour être en mesure de produire le résultat souhaité ou réponse. Toutefois, une application serveur ne peut jamais lancer une communication sur le réseau. Une application serveur ne peut jamais être une application cliente.  
  
 Dans l’illustration suivante, l’appel intitulé **initialiser** est une abstraction pour le processus d’initialisation SNL API, ce qui nécessite plusieurs appels. L’appel étiqueté **SwCallback()** est répétée plusieurs fois, et l’appel étiqueté **SwCall()** est facultatif.  
  
 ![Serveur SNL](../../adapters-and-accelerators/fileact-interact/media/42395775-cdbc-4e36-8b36-566caefa2aaf.gif "42395775-cdbc-4e36-8b36-566caefa2aaf")  
  
 Tous les appels entre le serveur et la DLL de l’API SNL sont C standard en appelant les appels de fonctions synchrones convention.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des adaptateurs FileAct et interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md)   
 [Architecture de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md)   
 [Architecture de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)