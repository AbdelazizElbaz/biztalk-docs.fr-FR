---
title: Validation structurelle EDI | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87086614-5616-441d-915c-2979c63c6e2f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 505b9ac55eff0b6adb249d11788308f03902f1d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-structural-validation"></a>Validation structurelle EDI
Les spécifications EDI pour le codage X12 et EDIFACT définissent des règles et des conventions spécifiques pour la structure des échanges EDI. Le Désassembleur EDI dans EDIReceivePipeline vérifie que l'enveloppe de chaque message reçu respecte ces règles de structure. EDISendPipeline crée chaque message à envoyer en respectant ces règles et valide l'enveloppe avant l'envoi.  
  
 La validation structurelle permet de garantir que les en-têtes et les codes de fin requis sont présents. Les vérifications d'intégrité structurelle incluent des vérifications de classement et de comptage des segments et des boucles. Ces vérifications sont toujours effectuées pour s'assurer que le document sera analysé ou sérialisé correctement. Cette validation est effectuée même si le **Validation de Type EDI** et/ou **Validation étendue** options sont désactivées. Un échange dont les validations structurelles de base échouent est suspendu, même si le **Validation de Type EDI** et/ou **Validation étendue** options sont désactivées.  
  
 Les valeurs des éléments de données des en-têtes et les codes de fin, et la façon dont en-têtes et les codes de fin et les éléments de données sont séparés, sont déterminées par l'accord. Elles sont validées au moyen du processus de validation du schéma.  
  
 Pour plus d’informations sur l’enveloppe et le contenu dans chaque ensemble d’en-têtes et codes de fin, consultez [Structure des messages EDI](../core/edi-message-structure.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des messages EDI](../core/edi-message-validation.md)