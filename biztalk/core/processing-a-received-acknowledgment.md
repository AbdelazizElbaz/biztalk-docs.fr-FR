---
title: "Le traitement d’un accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67f67a95-7368-40c2-a162-6ffc9de076fc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60236295e1e3bdd97a42d2f620de42129646494c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-a-received-acknowledgment"></a>Traitement d'un accusé de réception
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] attend un accusé de réception technique si la propriété concernée est spécifiée dans l'accord. Pour X12, il s’agit du **TA1 attendu** propriété dans le **accusés de réception** page de l’accord unidirectionnel, dans le **propriétés de l’accord** boîte de dialogue ou à partir de l’accord de secours Propriétés. Pour EDIFACT, il s’agit le **réception du message (CONTRL) attendu** propriété dans le **accusés de réception** page de l’accord unidirectionnel, dans le **propriétés de l’accord** boîte de dialogue zone ou à partir des propriétés de l’accord de secours. Lorsque l'accord récepteur traite le message reçu, il génère l'accusé de réception technique comme résultat de la valeur ISA14 ou UNB9 du message.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] attend une notification de transactions opérationnelles pour le codage X12 ou EDIFACT si la propriété concernée est spécifiée dans l'accord. Pour X12, cette propriété est la **997 attendu** dans les **accusés de réception** page de l’accord unidirectionnel, dans le **propriétés de l’accord** boîte de dialogue ou à partir de l’accord de secours Propriétés. Pour EDIFACT, cette propriété est la **accusé de réception (CONTRL) attendu** propriété dans le **accusés de réception** page de l’accord unidirectionnel, dans le **propriétés de l’accord** boîte de dialogue ou à partir des propriétés de l’accord de secours. Lorsque l'accord récepteur traite le message reçu, il génère l'accusé de réception technique comme résultat de la valeur ISA14 ou UNB9 du message.  
  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit l'accusé de réception d'un message EDI, il le valide à l'aide des schémas de contrôle d'accusé de réception. Ces schémas sont X12_\<numéro de version > _997.xsd ou X12\_\<numéro de version > _TA1.xsd pour X12, EFACT\_\<numéro de Version > _CONTRL.xsd pour EDIFACT et X12_00501_997.xsd pour HIPAA 5010.  
  
 Lorsque le pipeline de réception traite l'accusé de réception entrant, il le met en correspondance avec l'échange EDI envoyé. Le pipeline dépose alors l’accusé de réception dans la MessageBox. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]ne pas traiter l’accusé de réception. Celui-ci est interrompu, sauf si vous définissez un mécanisme pour le traiter. Pour traiter l'accusé de réception, vous pouvez définir un port d'envoi qui y est abonné et le déposer ensuite dans un dossier dans lequel les accusés de réception seront régulièrement supprimés.  
  
## <a name="see-also"></a>Voir aussi  
 [Structure d’accusé de réception EDI](../core/edi-acknowledgment-structure.md)   
 [Envoi d’un accusé de réception EDI](../core/sending-an-edi-acknowledgment.md)