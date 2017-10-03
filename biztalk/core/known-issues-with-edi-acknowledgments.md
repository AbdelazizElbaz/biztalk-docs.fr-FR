---
title: "Problèmes connus avec les accusés de réception EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a769a78e-8a49-4aa4-899e-e9f54fdd5f37
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f02ef54ed8786f8ead12e16fad880040dbcadc8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-acknowledgments"></a>Problèmes connus avec les accusés de réception EDI
Cette rubrique décrit les problèmes connus avec les accusés de réception EDI dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="ak102-in-a-997-acknowledgment-can-be-negative"></a>AK102 dans un accusé de réception 997 peut être négatif  
 L'élément de données AK102 (numéro de contrôle du groupe) dans un accusé de réception X12 997 peut être une valeur négative. Un accusé de réception avec un élément de données AK102 négatif transmet la validation effectuée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], même si un numéro de contrôle du groupe négatif n'a pas de signification.  
  
## <a name="a-contrl-receipt-may-report-a-status-of-accepted-when-part-of-the-message-is-rejected"></a>Une réception CONTRL peut indiquer un état Accepté quand une partie du message est rejetée  
 Une réception CONTRL (ou accusé de réception technique EDIFACT) signale l'état « Rejeté » uniquement lorsque le message EDIFACT entrant est un doublon ou lorsqu'il y a des erreurs dans l'enveloppe (par exemple, un problème de jeu de caractères). L'échange EDIFACT n'indique pas l'état « Échange accepté avec des erreurs » dans l'accusé de réception technique CONTRL, contrairement à l'échange X12 dans le champ TA104 de l'accusé de réception TA1. Si une partie du message EDIFACT est acceptée, l'accusé de réception technique CONTRL indique l'état « Accepté ». Dans certains scénarios, une partie du message est rejetée, mais l'accusé de réception technique CONTRL indique toujours l'état « Accepté ». Dans ce cas, l'élément UCI5 peut indiquer l'erreur.  
  
## <a name="x12-acknowledgments-will-show-accepted-for-a-preserved-interchange-suspend-interchange-on-error-when-a-group-header-or-trailer-is-in-error"></a>Les accusés de réception X12 indiquent l'état Accepté pour un échange préservé (suspendre l'échange en cas d'erreur) quand un en-tête ou un code de fin de groupe génère une erreur  
 Si l'option de traitement par lot entrant pour un message X12 est définie sur « Préserver l'échange : suspendre l'échange en cas d'erreur », alors qu'un champ de l'en-tête ou du code de fin de groupe n'est pas valide, l'état est indiqué comme Accepté dans les accusés de réception TA1 et 997. Le rapport d'état EDI et les détails du document informatisé indiquent également un état Accepté. Cela se produit même si l'échange est suspendu, et une erreur dans l'Observateur d'événements indique que l'échange a été suspendu.  
  
 L'accusé de réception TA1 indique un état Accepté parce qu'il est destiné à confirmer l'exactitude de l'en-tête ISA et du code de fin IEA, mais pas l'exactitude de l'en-tête GS et du code de fin GE. Toutefois, l'accusé de réception 997 affiche également un état Accepté.  
  
## <a name="if-groups-in-an-interchange-have-the-same-name-the-status-report-will-show-twice-as-many-acknowledgments"></a>Si des groupes d'un échange portent le même nom, le rapport d'état indique deux fois plus d'accusés de réception  
 Si BizTalk Server traite un échange EDI englobant plusieurs groupes du même nom, le Échange EDI et état ACK corrélé indique deux fois plus d'accusés de récpetion fonctionnels que prévu. Par exemple, si deux groupes inclus dans un échange portent le même nom, le rapport d'état indique quatre accusés de réception au lieu de deux.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus avec le traitement EDI](../core/known-issues-with-edi-processing.md)   
 [Envoi d’un accusé de réception EDI](../core/sending-an-edi-acknowledgment.md)   
 [Le traitement d’un accusé de réception](../core/processing-a-received-acknowledgment.md)   
 [Configuration des accusés de réception EDI](../core/configuring-edi-acknowledgments.md)