---
title: "Étape 5 : Créer un accord de mise en miroir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, mirror agreements
- loopback tutorial, creating mirror agreements
- agreements, mirror agreements
ms.assetid: 6aa70b1e-7d38-49f7-9d5f-f008cbe3df66
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e0ddb7c7dcad8bb278b318cdc599640b479baafa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-create-a-mirror-agreement"></a>Étape 5 : Créer un accord de mise en miroir
Dans cette étape, vous utilisez l’utilitaire de bouclage pour créer un accord de mise en miroir en simulant le partenaire commercial sur le même ordinateur que celui sur lequel vous avez configuré l’organisation d’origine. L’utilitaire de bouclage est un outil de ligne de commande.  
  
### <a name="to-create-a-mirror-agreement-using-the-loopback-utility"></a>Pour créer un accord de mise en miroir à l’aide de l’utilitaire de bouclage  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l’invite de commandes, accédez au \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK. Tapez la commande suivante et appuyez sur **entrée**:  
  
    ```  
    Loopback /enable HOME  
    ```  
  
3.  Une fois la commande exécutée à l’étape 2 terminée, tapez la commande suivante dans l’invite de commandes, puis appuyez sur **entrée**:  
  
    ```  
    Loopback /mirror "Trade Agreement"   
    ```  
  
 L’utilitaire de bouclage crée automatiquement les ports d’envoi pour l’organisation d’origine (initiateur) et d’un accord commercial de mise en miroir pour l’organisation partenaire. Le partenaire utilise les deux nouveaux ports d’envoi pour communiquer avec l’organisation d’origine.  
  
> [!NOTE]
>  L’accord commercial doit remettre en miroir chaque fois que vous mettez à jour l’accord commercial d’origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 6 : Démarrer des Orchestrations](../../adapters-and-accelerators/accelerator-rosettanet/step-6-start-orchestrations.md)