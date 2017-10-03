---
title: "Composants d’adaptateur interAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aad60b57-4cc8-44b9-98f5-e5a2ba3a41e2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e909e49713377172d01540f4c8e660756d68ed72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-components"></a>Composants d’adaptateur interAct
L’adaptateur InterAct a un client et un composant serveur. Notez qu’il peut y avoir une installation (minimale) A4SWIFT sur le même ordinateur en tant que la passerelle de Alliance SWIFT (trous) s’il exécute Windows Server. Notez également que le lien SWIFTNet (SNL) peut se trouver sur un ordinateur distinct dans les trous. L’adaptateur d’API (interface) fournie par SWIFT de programmation d’applications à distance sont utilisée pour communiquer à partir d’A4SWIFT avec les trous, quel que soit l’emplacement des composants.  
  
 La figure ci-dessous illustre l’emplacement où résident les composants comprenant la chaîne entière d’adaptateur et les communications liée à l’adaptateur InterAct.  
  
 ![Composants interAct](../../adapters-and-accelerators/fileact-interact/media/cf257c5a-3668-4aff-bce9-7acc6eb672bd.gif "cf257c5a-3668-4aff-bce9-7acc6eb672bd")  
  
 Dans l’illustration suivante, l’application cliente utilise A4SWIFT et l’adaptateur InterAct. BizTalk Server est l’intergiciel (middleware), qui communique avec l’adaptateur hôte API à distance via TCP/IP.  
  
 ![Application cliente interAct](../../adapters-and-accelerators/fileact-interact/media/7aeada39-6264-498b-92e8-303eb0cf369b.gif "7aeada39-6264-498b-92e8-303eb0cf369b")  
  
 Dans l’illustration suivante, l’application serveur utilise A4SWIFT et l’adaptateur InterAct. BizTalk Server est l’intergiciel (middleware), qui communique avec l’adaptateur hôte API à distance via TCP/IP.  
  
 ![Application serveur interAct](../../adapters-and-accelerators/fileact-interact/media/51cbae6a-41e9-4a50-9574-5e86bc04ddba.gif "51cbae6a-41e9-4a50-9574-5e86bc04ddba")  
  
## <a name="see-also"></a>Voir aussi  
 [Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [Interaction des Messages de la carte pour l’échange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [Application cliente de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [Application de serveur de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [Interagir de magasin de l’adaptateur et le transfert](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [Interagir l’Architecture de sécurité de carte](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [Interagir remise fiable de bout en bout pour l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [Interagir l’état de la carte d’analyse](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [Interagir carte de non-répudiation](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)