---
title: "Message CONTRL EDIFACT comme accusé de réception technique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f2a7564-dbd3-48d0-b0a6-a77a0560459f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8376e3249a102486c1bef4d92a7512c8aa29636c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-contrl-message-as-technical-acknowledgment"></a>Message CONTRL EDIFACT comme accusé de réception technique
Si vous avez sélectionné l'option de génération d'un accusé de réception technique dans les paramètres du profil d'entreprise ou dans l'accord de partenariat commercial (ou dans l'accord de secours si aucun accord n'a été défini entre les deux profils d'entreprise), ou si le champ UNB9 du message est défini sur « 2 », un message CONTRL est généré à la place d'un accusé de réception technique. Cet accusé de réception indique les résultats de la réception de l'échange.  
  
 L'accusé de réception technique CONTRL inclut les segments suivants :  
  
-   L'en-tête de message UNH (obligatoire).  
  
-   La réponse à l'échange UCI qui identifie l'échange de l'objet et indique la nature de la réception de l'échange (obligatoire). Le segment UCI dispose d'une occurrence maximale de 1 ; par conséquent, il signale la première erreur rencontrée dans l'un des segments de contrôle.  
  
-   Le code de fin UNT (obligatoire).  
  
 Une erreur est signalée dans l'élément de données UCI5, « Code d'erreur de syntaxe ». Contrairement aux échanges X12, il n'existe pas de condition « Accepté avec erreurs » pour les échanges EDIFACT.  
  
> [!NOTE]
>  Une réception CONTRL (ou accusé de réception technique EDIFACT) signale l'état « Rejeté » uniquement lorsque le message EDIFACT entrant est un doublon ou lorsqu'il y a des erreurs dans l'enveloppe (par exemple, un problème de jeu de caractères). L'échange EDIFACT n'indique pas l'état « Échange accepté avec des erreurs » dans l'accusé de réception technique CONTRL, contrairement à l'échange X12 dans le champ TA104 de l'accusé de réception TA1. Si une partie du message EDIFACT est acceptée, l'accusé de réception technique CONTRL indique l'état « Accepté ». Dans certains scénarios, une partie du message est rejetée, mais l'accusé de réception technique CONTRL indique toujours l'état « Accepté ». Dans ce cas, l'élément UCI5 peut indiquer l'erreur.  
  
 L'accusé de réception technique CONTRL inclut les éléments de données suivants :  
  
|Éléments Data|Nom|Utilisation|  
|------------------|----------|-----------|  
|UNH1|Numéro de référence du message|-|  
|UNH2|Sous-composants de l'identificateur de message|Les sous-composants sont :<br /><br /> -1 = CONTRL<br /><br /> - 2 = 4<br /><br /> - 3 = 1<br /><br /> -4 = ANNULATION|  
|UCI1|Numéro de contrôle de l'échange|Mappé à partir du champ UNB5 du message reçu.|  
|UCI2|Expéditeur des échanges|Mappé à partir du champ UNB2 du message reçu. Le premier sous-composant (identification) est obligatoire. Le deuxième sous-composant (qualificateur du code) et le troisième composant (adresse de routage inverse) sont facultatifs.|  
|UCI3|Destinataire de l’échange|Mappé à partir du champ UNB3 du message reçu. Le premier sous-composant (identification) est obligatoire. Le deuxième sous-composant (qualificateur du code) est facultatif.|  
|UCI4|Code d'action|Les codes d'action sont les suivants :<br /><br /> -8 si l’échange est accepté.<br /><br /> -7 si l’échange est accepté mais certains documents informatisés sont rejetées.<br /><br /> -4 si l’échange est rejeté en raison d’une erreur dans le segment UNA ou UNB<br /><br /> Il s'agit d'un élément de données obligatoire.|  
|UCI5|Code d'erreur de syntaxe|Identifie la condition d'erreur (le cas échéant). Pour plus d’informations, consultez [Codes d’erreur d’accusé de réception EDIFACT CONTRL](../core/edifact-contrl-acknowledgment-error-codes.md).<br /><br /> Cet élément de données possède un caractère facultatif conditionnel.|  
|UCI6|Balise de segment de service|Identifie le segment disposant de la condition d'erreur spécifiée dans l'élément de données UCI.5.<br /><br /> Cet élément de données possède un caractère facultatif conditionnel.|  
|UCI7|Identification de l'élément de données|Identifie les éléments de données disposant de la condition d'erreur spécifiée dans l'élément de données UCI.5. Les sous-composants du segment UCI7 sont :<br /><br /> -La position de l’élément de données erroné dans le segment (obligatoire)<br /><br /> -La position de l’élément de données composites erroné dans le segment (caractère facultatif conditionnel)<br /><br /> -L’occurrence de l’élément de données erroné dans le segment (caractère facultatif conditionnel)|  
|UCI8|-|-|  
|UNT1|Nombre de segments|-|  
|UNT2|Numéro de référence du message|-|