---
title: "Pipelines par défaut | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, PassThruTransmit
- pipelines, PassThruReceive
- pipelines, XMLTransmit
- pipelines, StsReceive
- pipelines, StsSend
- pipelines, StsFileReceive
- Microsoft.BizTalk.KwTpm.StsDefaultPipelines.EnvSchema XML envelope
- pipelines, XMLReceive
- pipelines, backward compatibility
- Microsoft.BizTalk.DefaultPipelines assembly
- pipelines, default
ms.assetid: 7d82bb2c-c7f1-44a1-9e1b-89b0bb806845
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ceb3f06f2e2b57ec37bc4a95a385574de594940
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="default-pipelines"></a>Pipelines par défaut
Lorsque vous créez une application, les pipelines par défaut sont créés et déployés par défaut et apparaissent dans l'assembly Microsoft.BizTalk.DefaultPipelines, dans le dossier \References de chaque projet BizTalk. Ces pipelines ne peuvent pas être modifiés dans le Concepteur de pipeline. Ils peuvent être sélectionnés au moment de la configuration d'un port d'envoi ou d'un emplacement de réception dans l'Explorateur BizTalk. Cette rubrique décrit ce que sont les pipelines par défaut et explique quand les utiliser.  
  
> [!NOTE]
>  Les pipelines d'envoi et de réception XML ne prennent pas en charge les documents XML de taille supérieure à 4 gigaoctets.  
  
## <a name="passthrureceive-pipeline"></a>Pipeline PassThruReceive  
 Le pipeline de réception de transfert n'a pas de composants. Il est utilisé dans le cadre des scénarios de transfert simples, quand aucun traitement de charge de message n'est nécessaire. On s'en sert généralement lorsque la source et la destination du message sont connues et que le message ne requiert ni validation, ni codage, ni désassemblage. Il est fréquemment utilisé avec le pipeline d'envoi de transfert.  
  
 Ne comportant pas de désassembleur, le pipeline de réception de transfert ne peut pas servir pour acheminer des messages vers des orchestrations.  
  
> [!NOTE]
>  Le pipeline de réception de transfert ne prend pas en charge la promotion des propriétés.  
  
## <a name="passthrutransmit-pipeline"></a>Pipeline PassThruTransmit  
 Le pipeline d'envoi de transfert n'a pas de composants. On s'en sert généralement lorsque aucun traitement de document n'est nécessaire avant l'envoi du message vers une destination.  
  
## <a name="xmlreceive-pipeline"></a>Pipeline XMLReceive  
 Le pipeline de réception XML est composé des phases suivantes :  
  
-   **Décoder.** Vide  
  
-   **Désassembler.** contient le composant Désassembleur XML.  
  
-   **Valider.** Vide  
  
-   **Résoudretiers.** exécute le composant Résolution du tiers, qui résout l'objet du certificat ou l'ID de sécurité source vers l'ID de tiers.  
  
## <a name="xmltransmit-pipeline"></a>Pipeline XMLTransmit  
 Le pipeline d'envoi XML est composé des phases suivantes :  
  
-   **Préassembler.** Vide  
  
-   **Assembler.** contient le composant Assembleur XML.  
  
-   **Encoder.** Vide  
  
## <a name="see-also"></a>Voir aussi  
 [Types de Pipelines](../core/types-of-pipelines.md)   
 [Types de composants de Pipeline](../core/types-of-pipeline-components.md)   
 [Modèles de pipeline](../core/pipeline-templates.md)   
 [Composants de pipeline](../core/pipeline-components.md)   
 [À propos des Pipelines, des étapes et des composants](../core/about-pipelines-stages-and-components.md)