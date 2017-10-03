---
title: "X12 Codes d’erreur d’accusé de réception TA1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47eb315f-ec99-4e1e-937b-22199255f14f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2ff9001d73f815b0d62a4e83cc64e1288715f90
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="x12-ta1-acknowledgment-error-codes"></a>Codes d'erreur de l'accusé de réception TA1 X12
Cette rubrique répertorie les codes d'erreur utilisés dans les segments d'un accusé de réception TA1 X12. Pour plus d’informations sur ces segments, consultez [X12 accusé de réception TA1](../core/x12-ta1-acknowledgment.md).  
  
 Le tableau suivant indique les codes d'erreur définis par la spécification X12 pris en charge et non pris en charge par les fonctionnalités EDI et AS2 de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les valeurs relatives au comportement du moteur (TA104) sont comme suit :  
  
-   A = accepter  
  
-   E = échange accepté avec des erreurs  
  
-   R = échange rejeté/interrompu  
  
|Condition|Comportement du moteur (valeur TA104)|Valeur TA105|Pris en charge ?|  
|---------------|-------------------------------------|-----------------|----------------|  
|Réussi|Un|000|Oui|  
|Les numéros de contrôle de l'échange dans l'en-tête ISA 13 et le code de fin IEA02 ne correspondent pas|E|001|Oui|  
|La norme n'est pas prise en charge dans ISA11 (Normes de contrôle)|E|002|Oui<br /><br /> (en cas d'incohérence des ID)|  
|La version des contrôles n'est pas prise en charge|E|003|Non<sup>1</sup>|  
|Terminateur de segment est non valide<sup>2</sup>|R|004|Oui|  
|Le qualificateur d'ID de l'échange n'est pas valide pour l'expéditeur|R|005|Oui<br /><br /> (en cas d'incohérence des ID)|  
|ID de l'expéditeur de l'échange non valide|E|006|Oui<sup>3</sup>|  
|Le qualificateur d'ID de l'échange n'est pas valide pour le destinataire|R|007|Oui<br /><br /> (en cas d'incohérence des ID)|  
|ID du récepteur de l'échange non valide|E|008|Ne<sup>3</sup>|  
|ID du récepteur de l'échange inconnu|E|009|Oui|  
|Valeur du qualificateur d'informations d'autorisation non valide|R|010|Oui<br /><br /> (en cas d'incohérence des ID)|  
|Valeur des informations d'autorisation non valide|R|011|Oui<br /><br /> (si le tiers est configuré/valeur)|  
|Valeur du qualificateur d'informations de sécurité non valide|R|012|Oui<br /><br /> (en cas d'incohérence des ID)|  
|Valeur des informations de sécurité non valide|R|013|Oui<br /><br /> (si le tiers est configuré/valeur)|  
|Valeur de la date de l'échange non valide|R|014|Oui|  
|Valeur de l'heure de l'échange non valide|R|015|Oui|  
|Valeur de l'identificateur de normes de l'échange non valide|R|016|Oui|  
|Valeur d’ID de Version de l’échange non valide|R|017|Oui<sup>4</sup>|  
|Valeur du numéro de contrôle de l'échange non valide|R|018|Oui|  
|Valeur d’accusé de réception demandé non valide|E|019|Oui|  
|Valeur d’indicateur de Test non valide|E|020|Oui|  
|Valeur de nombre de groupes inclus non valide|E|021|Oui|  
|Structure de contrôle non valide|R|022|Oui|  
|Fin du fichier (transmission) incorrecte (prématurée)|R|023|Oui|  
|Contenu de l'échange non valide (par exemple, segment GS non valide)|R|024|Oui|  
|Numéro de contrôle de l'échange dupliqué|R<br /><br /> (sur la base des paramètres)|025|Oui|  
|Séparateur d'éléments de données non valide|R|026|Oui|  
|Séparateur d'éléments composites non valide|R|027|Oui|  
|Date de remise non valide dans la demande de remise différée|Non pris en charge|-|-|  
|Heure de remise non valide dans la demande de remise différée|Non pris en charge|-|-|  
|Code temporel de remise non valide dans la demande de remise différée|Non pris en charge|-|-|  
|Catégorie de service non valide|Non pris en charge|-|-|  
  
 <sup>1</sup> code d’erreur 017 est utilisé à la place.  
  
 <sup>2</sup> des combinaisons valides du terminateur de segment sont : char terminateur de Segment uniquement et caractère terminateur de Segment suivi par suffixe 1 et 2 de suffixe.  
  
 <sup>3</sup> pris en charge si la réception d’un échange sur un port de réception nécessitant une authentification. Les propriétés liées à l'ID de l'expéditeur sont examinées et rejetées si elles sont incohérentes. Si les paramètres du tiers ne sont pas disponibles (car non configurés), l'échange est rejeté.  
  
 <sup>4</sup> indique que la valeur enum n’est pas valide.