---
title: "Interaction des Messages de la carte pour l’échange | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b443b8a-4e56-47f1-8d91-5c807fd54ccc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d19e10940e6a83c24e9397f0df94d0fc54e4da38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-messages-for-business-exchange"></a>Interaction des Messages de la carte pour l’échange
Il existe quatre messages dans le cycle de bout en bout pour l’adaptateur InterAct. Ces messages sont des primitives de SWIFTNet. Le premier et le dernier message constituent les primitives du côté client, SwInt:ExchangeRequest et SwInt:ExchangeResponse. Les deux messages central comprennent les primitives du côté serveur, SwInt:HandleRequest et SwInt:HandleResponse.  
  
 À ce niveau de simplification, il existe six étapes dans le cycle de message de bout en bout :  
  
1.  L’application cliente prépare le message de demande.  
  
2.  L’application cliente transmet le message de demande à SWIFTNet.  
  
3.  SWIFTNet traite le message de demande et l’envoie à l’application serveur.  
  
4.  L’application serveur reçoit le message de demande à partir de SWIFTNet.  
  
5.  L’application serveur prépare le message de réponse.  
  
6.  L’application serveur transmet le message de réponse à SWIFTNet.  
  
7.  SWIFTNet traite le message de réponse et l’envoie à l’application cliente.  
  
8.  L’application cliente reçoit le message de réponse de SWIFTNet.  
  
 La figure suivante illustre l’échange de messages InterAct.  
  
 ![Échange de messages interAct](../../adapters-and-accelerators/fileact-interact/media/12fbebc6-5ab7-4d7f-9f94-4069b22161fa.gif "12fbebc6-5ab7-4d7f-9f94-4069b22161fa")  
  
## <a name="see-also"></a>Voir aussi  
 [Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [Composants d’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [Application cliente de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [Application de serveur de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [Interagir de magasin de l’adaptateur et le transfert](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [Interagir l’Architecture de sécurité de carte](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [Interagir remise fiable de bout en bout pour l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [Interagir l’état de la carte d’analyse](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [Interagir carte de non-répudiation](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)