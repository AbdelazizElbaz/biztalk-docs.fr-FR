---
title: Segment et champ | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, segments
- messages, fields
- segments, messages
ms.assetid: e68864e6-590c-47f3-8c9e-81831aec2642
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca948748bc30f8c8a56f7c257b775b37a990625
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="segment-and-field"></a>Segment et champ
Une table de segment définit un segment de HL7. Chaque définition des segments suit le modèle indiqué ci-dessous.  
  
|SEQ|LEN|TYPE DE DONNÉES|S’ABONNER|RP / #|TBL #|ÉLÉMENT #|NOM DE L’ÉLÉMENT|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|1|4|SI|O|||00104|Définir l’ID - PID|  
|2|20|CX|B|||00105|Identification de patient|  
|3|250|CX|R|O||00106|Liste de patients identificateur|  
|4|20|CX|B|O||00107|Identification de Patient autre - PID|  
|5|250|XPN|R|O||00108|Nom du patient|  
|..||||||||  
|..||||||||  
|37|80|ST|O|||01541|Déformation|  
|38|250|CE|O|2|0429|01542|Code de classe de production|  
  
 HL7 inclut également les définitions pour chaque champ de texte. La balise de segment de trois caractères et le numéro de séquence identifient de façon unique chaque champ dans un segment. Par exemple, dans le cas du segment d’Identification de Patient, la balise PID et le numéro de séquence « 5 » identifient le champ nom du patient. L’encodage et l’interface de documentation XML utilisent cette convention pour identifier les champs dans des segments. La définition des segments inclut également la déclaration de type de données pour chaque champ, ainsi que le numéro de la table qui s’applique aux éléments codés.  
  
 Dans les nouvelles versions, vous pouvez uniquement ajouter des champs à la fin d’un segment, et vous ne pouvez pas supprimer les champs. Si un champ ajouté remplace les fonctionnalités d’un champ existant, le premier champ reste pour la compatibilité descendante. (Ceci peut être observé par le « B » dans la colonne éventuellement ci-dessus pour PID.2 et PID.3.)  
  
 Les fonctions suivantes de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge ces exigences :  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]prend en charge les segments standards pour toutes les versions de HL7 à partir de la version 2.1.  
  
-   Lorsque vous construisez des spécifications de l’interface et implémentez des interfaces, vous pouvez étiqueter les champs sont facultatifs dans la norme comme étant obligatoires ou non pris en charge, selon les exigences fonctionnelles.  
  
-   Vous pouvez créer Z lorsque cela est nécessaire pour la localisation des segments.  
  
-   Vous pouvez redéfinir la sémantique des champs ou ajouter des champs à des segments lorsque cela est nécessaire pour la localisation. Notez que cela se situe sous le titre de la localisation autorisée. Toutefois, dans certains cas, vous devez cette fonctionnalité pour prendre en charge les interfaces héritées ou les interfaces à des systèmes hérités.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)