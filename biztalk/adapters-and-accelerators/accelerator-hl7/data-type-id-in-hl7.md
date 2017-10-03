---
title: "ID de Type de données dans HL7 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types, data type ID
- data types, messages
- messages, data types
ms.assetid: d1412886-ff0b-4333-b01e-1c3ae45240e2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c5778e772d21cb5f9c6759c127c92ebe74b6f5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-type-id-in-hl7"></a>ID de Type de données dans HL7
Dans le cas de HL7 V2.1, l’ID de type de données est un espace réservé pour les types de données non défini. Voici quelques exemples de son utilisation :  
  
-   Le type de données sous la forme d’un champ ST est SI (ID de séquence).  
  
-   Le type de données sous la forme d’un champ NM est champs composites.  
  
 Voici quelques exemples de spécifiquement les types de données composites définis :  
  
-   CK : ID Composite avec chiffre de vérification. Exemple :  
  
    ```  
    |128952^6^M11|  
    ```  
  
-   NC : Composite ID et nom. Exemple :  
  
    ```  
    |12372^RIGGINS^JOHN^""^MD|  
    |12372|  
    |^RIGGINS^JOHN^""^MD|  
    ```  
  
-   CQ : Quantité Composite avec des unités. Exemple :  
  
    ```  
    |123.7^ML|  
    ```  
  
-   CE : Codé de l’élément. Exemple :  
  
    ```  
    |54.21^Laparoscopy^I9C^42112^^AS4|  
    ```  
  
 Ce type de données est localisé et définie sur le site. En outre, HL7 V2.1 ne fournit pas de la couverture de ce type de données dans la base de données HL7 accès. Pour la génération de vos schémas, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) suppose que les types de données de version 2.2 du HL7 sont valides et utilise ces informations pour générer les schémas. Selon l’utilisation dans le schéma, un type de données approprié doit être utilisé, ce qui signifie que que le type de données doit être remplacé par CK, CQ, CE, ST ^ SI et ainsi de suite.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../adapters-and-accelerators/accelerator-hl7/data-types.md)   
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)