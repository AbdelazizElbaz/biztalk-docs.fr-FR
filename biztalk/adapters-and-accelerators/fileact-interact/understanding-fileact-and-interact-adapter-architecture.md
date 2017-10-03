---
title: "Présentation des adaptateurs FileAct et interagir l’Architecture de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f97a7fe-20df-4509-bb6e-53743c3a57df
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c04d0ba8b1c2bbd99a71e3d76c8d7ad60c251147
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understanding-fileact-and-interact-adapter-architecture"></a>Présentation des adaptateurs FileAct et interagir l’Architecture de l’adaptateur
L’adaptateur SWIFT est basée sur l’infrastructure d’adaptateurs BizTalk. Selon les classifications des adaptateurs dans BizTalk Server, les adaptateurs SWIFT, adaptateurs FileAct et InterAct, représentent les éléments suivants :  
  
-   Adaptateur personnalisé. Il s’agit d’un adaptateur personnalisé spécialement conçue pour interagir avec le réseau rapide à l’aide d’une norme propriétaire appelée FileAct et Interact.  
  
-   Adaptateur de transport. Cet adaptateur permet des applications de logiciels d’entreprise envoyer et recevoir des messages avec le réseau rapide.  
  
-   Non transactionnel. L’adaptateur ne fait pas utiliser de n’importe quel objet de transaction pour interagir avec le réseau rapide.  
  
-   Isolé. L’adaptateur de réception s’exécute dans un processus séparé et les adaptateurs d’envoi régulière dans le processus.  
  
 Pour plus d’informations sur l’infrastructure d’adaptateurs BizTalk, consultez le « quel est l’infrastructure d’adaptateurs ? » rubrique dans l’aide de BizTalk Server.  
  
 L’illustration suivante montre une vue d’ensemble de l’architecture d’adaptateurs FileAct et InterAct.  
  
 ![](../../adapters-and-accelerators/fileact-interact/media/035ebb05-ce11-447c-b56b-ba8b41e07e50.gif "035ebb05-ce11-447c-b56b-ba8b41e07e50")  
  
> [!NOTE]
>  Microsoft [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] prend en charge uniquement les API de lien SWIFTNet (SNL) en mode strict.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [SWIFTNet Client et serveur](../../adapters-and-accelerators/fileact-interact/swiftnet-client-and-server.md)  
  
-   [Architecture de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md)  
  
-   [Architecture de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)  
  
-   [Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)  
  
-   [Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)