---
title: "Traitement des accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: acknowledgements, processing
ms.assetid: 705bc12d-69ac-4641-a45e-4f1fab507e4a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b726eb4698eaa9887703d7df01dc0f6cadf5eefc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgments-processing"></a>Traitement des accusés de réception
La spécification HL7 prend en charge l’échange de messages dans deux formats :  
  
-   Mise à jour non sollicitée et son accusé de réception (ACK)  
  
-   Requête et la réponse  
  
 En réponse à un message à partir d’une application à l’origine, l’application répondre répond avec un message qui inclut des données ou une indication des erreurs. L’application d’origine peut s’afficher un état de rejet de l’application de répondeur indiquant que l’application de répondeur n’a pas reçu le message correctement. Dans les deux cas, le processus d’échange de messages implique deux entités, les applications de l’initiateur et répondre. Chacun est un expéditeur et le récepteur de messages. L’application d’origine envoie tout d’abord et reçoit ensuite pendant que le système répond reçoit et envoie ensuite.  
  
## <a name="unsolicited-updates"></a>Mises à jour non sollicités  
 Une mise à jour non sollicité se produit lorsqu’une application métier de line-of-business publie un message, ou démarre un transfert d’informations lorsqu’un événement déclencheur se produit. Par exemple, lorsque les résultats de laboratoire pour un patient sont disponibles, il peut être nécessaire pour envoyer les résultats de laboratoire à plusieurs autres systèmes. Ces mises à jour sont mises à jour non sollicitées, auquel répond un accusé de réception.  
  
## <a name="queries"></a>Requêtes  
 Dans le cas d’une requête, une application qui nécessite des informations envoie une requête vers une autre application, et l’application réceptrice répond à la requête. Par exemple, une application de pharmacie peut envoyer un message de demande qui contient le numéro d’ID du patient dans le système d’entrée de commande (CPOE) et recevoir une réponse contenant les données nécessaires pour permettre le traitement de la commande. Cette opération de demande est une requête et diffère d’une mise à jour non sollicitée. Les informations qui circulent entre les deux applications sont contenues dans la réponse. La réponse elle-même ne nécessite pas un accusé de réception avec un quatrième message. Toutefois, vous pouvez modifier cette dans certains environnements de répondre avec un accusé de réception. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) répond avec un accusé de réception s’ils sont configurés. Pour obtenir un exemple d’un échange de requête/réponse, consultez [Interrogative didacticiel](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Validation des Messages](../../adapters-and-accelerators/accelerator-hl7/validating-messages.md)  
  
-   [Modes d’accusé de réception du Message](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)  
  
-   [Modèle de processus de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md)