---
title: "Étape 16 : Démarrer l’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, starting
- message enrichment tutorial, orchestrations
ms.assetid: a9032b0b-1497-4f6a-8474-a94c14976be0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5256d33dc6751db34d1d827624d2dbe2644639e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-16-start-the-orchestration"></a>Étape 16 : Démarrer l’Orchestration
Dans cette étape, vous inscrivez le service afin d’associer le processus d’entreprise que vous avez créée dans l’orchestration à l’environnement physique dans lequel l’orchestration sera exécuté. En outre, vous démarrez le traitement de l’orchestration afin que vous puissiez tester votre application.  
  
### <a name="to-start-the-orchestration"></a>Pour démarrer l'orchestration  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration de la console, dans le volet d’arborescence de la console, sous **Orchestrations**, avec le bouton droit **BTAHL7_Project.Doorbell_Orchestration**, puis cliquez sur **Enlist** .  
  
2.  Avec le bouton droit **BTAHL7_Project.Doorbell_Orchestration**, puis cliquez sur **Démarrer**.  
  
    > [!NOTE]
    >  Vérifiez que vous avez démarré le **MLLPSendPort** port d’envoi et activé le **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort** emplacement de réception.  
  
 Passez à [étape 17 : créer l’Application WSClient](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)