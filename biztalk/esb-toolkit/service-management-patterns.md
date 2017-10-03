---
title: "Gestion des modèles de service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fea915c-0074-472e-909b-fbbd88d7359c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a48639fb2a540b5b2597b34ad95ee390b4382c34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="service-management-patterns"></a>Modèles de service de gestion
## <a name="repair-and-resubmit"></a>Réparer et soumettez à nouveau  
 Le modèle de réparation et soumettez à nouveau définit une solution dans laquelle un service ne peut pas traiter un message et doit normalement externaliser son état dans le formulaire du message ayant échoué, le contenu du message soit disponible pour l’activation de réparer et puis soumettez à nouveau à un service Pour continuer le traitement du message.  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]inclut des mécanismes par le Microsoft BizTalk les exceptions de messagerie et d’orchestration peuvent être normalisées et exposées pour une action supplémentaire. Lorsque vous concevez une solution ESB, il est important de compte de gestion des exceptions de. Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] comprend un exemple d’application de portail de gestion ESB qui montre comment les exceptions peuvent être affichées et gérées. Pour plus d’informations sur la réparation et la soumettre à nouveau les exceptions à l’aide de l’exemple d’application de portail de gestion ESB, consultez [réparation et soumettre à nouveau les Messages](../esb-toolkit/repairing-and-resubmitting-messages.md).