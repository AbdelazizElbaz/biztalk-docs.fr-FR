---
title: "Problèmes connus d’accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- known issues, acknowledgements
- acknowledgements, known issues
ms.assetid: cb45f80e-ba89-4b3f-a770-4b1cf9b8e220
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af5964e94f2ddc1d53d5259b174f8e551353711d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgments-known-issues"></a>Problèmes connus d’accusés de réception
Cette section contient des informations utiles qui peuvent vous aider à éviter les erreurs de l’accusé de réception (ACK).  
  
## <a name="hl7-v21-acknowledgment-message-accepted-even-if-it-contains-msa6-field"></a>Message d’accusé de réception HL7 V2.1 acceptée, même si elle contient des champs de MSA6  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) accepte un message d’accusé de réception HL7 V2.1 même si contient le champ MSA6.  
  
## <a name="msa-01-value-not-generated-for-commit-acknowledgment-errors"></a>Valeur de compte de service administré-01 ne pas généré pour les erreurs de validation d’accusé de réception  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]ne génère pas un code d’accusé de réception-01 du compte de service administré pour les erreurs d’accusés de réception de la validation (CE).  
  
## <a name="two-way-mllp-adapter-might-not-detect-a-problem-with-an-ack"></a>L’adaptateur MLLP bidirectionnelle peut ne pas détecte un problème avec un accusé de réception  
 Lorsque [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] reçoit un accusé de réception sur un adaptateur MLLP bidirectionnels, l’adaptateur effectue une validation léger sur l’accusé de réception pour déterminer sa validité. Si elle n’est pas valide, le champ MSA1 est extrait et en fonction de sa valeur, l’adaptateur effectue une nouvelle tentative, suspend ou supprime le message d’origine auquel l’accusé de réception a été répond. Toutefois, étant donné que la validation effectuée par l’adaptateur n’est pas une validation complète, il est possible que l’adaptateur ne détecte pas un problème avec les accusés de réception. Par exemple, l’adaptateur peut déterminer que l’accusé de réception est valide et supprimer le message d’origine, tandis que le pipeline est déterminer que l’accusé de réception n’était pas correctement formé et suspendre le message d’accusé de réception.  
  
## <a name="v2xml-acks-with-multiple-errors-will-fail-validation"></a>V2. Accusés de réception XML avec plusieurs erreurs échoue la validation  
 Si un V2 entrant. Message XML contient plusieurs erreurs, la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] analyseur peut générer un V2. ACK XML avec plus d’une erreur dans le champ d’erreur. Une telle V2. XML ACK validation échoue, étant donné que la norme HL7 Spécifie que l’analyseur peut signaler qu’une erreur dans un V2. Champ d’erreur XML ACK.  
  
## <a name="mllp-performance-counters-do-not-count-acks"></a>Les compteurs de performance MLLP ne comptent pas les accusés de réception  
 Une mesure de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] performances sont le nombre de messages traités par un adaptateur MLLP, comme indiqué par les compteurs de performance MLLP. Ce compteur mesure le nombre de messages reçus ou transmis. Toutefois, le nombre ne mesure pas le nombre d’accusés de réception reçus ou envoyés.  
  
## <a name="nak-generated-by-two-way-mllp-adapter"></a>NAK généré par l’adaptateur MLLP bidirectionnelle  
 Lorsqu’un adaptateur MLLP bidirectionnels suspend un message, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère un NAK (accusé de réception négatif) et le place dans la base de données MessageBox. Cela peut être un comportement inattendu. Il pouvez vous souhaitez supprimer le NAK à partir de la base de données MessageBox ou mapper vers un autre message.  
  
## <a name="data-type-of-an-ack-to-a-batch-message"></a>Type de données d’un accusé de réception pour un lot de messages  
 Dans un message d’accusé de réception généré en réponse à un lot de messages, le champ de MSH10 (ID de contrôle de message) est un GUID, plutôt qu’en cours en fonction du type de données du champ MSH10 dans le message du lot.  
  
## <a name="generated-acknowledgments-doc-type"></a>Type de document générée accusés de réception  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]génère des accusés de réception à l’aide du type de document http://[!INCLUDE[btsCoName](../../includes/btsconame-md.md)].com/HealthCare/HL7/2X#ACK_24_GLO_DEF ou http://[!INCLUDE[btsCoName](../../includes/btsconame-md.md)].com/HealthCare/HL7/2X #ACK_25_GLO_DEF. Si le tiers de destination utilise un espace de noms différent, vous devez appliquer un mappage de corps dans le port d’envoi ; Sinon, vous pouvez rencontrer des erreurs de sérialisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)