---
title: Interface du moteur de messagerie | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14241db3-edcf-4449-9ec8-2171a14496c0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a135505240e94fb42e5810a3e7ac71d4c99c34a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messaging-engine-interfaces"></a>Interface du moteur de messagerie
Il existe trois interfaces publiques que les adaptateurs peuvent utiliser pour autoriser les interactions avec le moteur de messagerie. Elles sont définies dans les sections suivantes :  
  
## <a name="ibttransportproxy"></a>IBTTransportProxy  
 Les adaptateurs interagissent toujours avec le moteur de messagerie en utilisant leur propre proxy de transport. Le proxy de transport est utilisé dans les opérations du type création de lots, obtention de la fabrique de messages et inscription des récepteurs isolés auprès du moteur.  
  
## <a name="ibttransportbatch"></a>IBTTransportBatch  
 Cette interface est fournie par le moteur de messagerie et définit les méthodes qui sont utilisées par les adaptateurs pour exécuter des opérations sur les lots de messages. Le moteur de messagerie traite les lots de façon asynchrone.  
  
## <a name="ibtdtccommitconfirm"></a>IBTDTCCommitConfirm  
 Les adaptateurs utilisant des transactions MSDTC (Microsoft Distributed Transaction Coordinator) explicites sur des lots doivent utiliser cette interface pour informer le moteur de l'issue de la transaction utilisant cette interface.