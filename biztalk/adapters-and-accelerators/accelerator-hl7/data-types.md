---
title: "Types de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types, messages
- messages, data types
ms.assetid: 7a758289-1629-48a0-843d-6f6773bd5ba6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8580b4f6c2a3f1a9f461b112bb4125f1a11ebbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-types"></a>Types de données
La spécification de type de données est un outil important pour le partitionnement de la complexité de la norme HL7 et il est essentielle de comprendre le contenu des données d’un champ HL7. Certains types de données sont simples et contient uniquement un composant, et certains contiennent de nombreux composants et les sous-composants. Par exemple, nom du Patient PID.5 a les type de données XPN dans la Version 2.4. Ce type de données prend en charge les subdivisions courantes d’un nom de langue anglaise, par exemple, nom de famille, prénom, deuxième prénom, ainsi que suffixe, préfixe, nom de code de type et plage de validité (date) de nom.  
  
 Dans les nouvelles versions HL7, vous pouvez ajouter, mais pas supprimer les types de données. Si vous ajoutez un contenu à un type de données, en ajoutant de nouveaux composants ou des sous-composants, vous pouvez uniquement les ajouter à la fin de la structure dans laquelle elles sont imbriquées. Dans certains cas, l’organisation HL7 fusionnée existante pour former de nouveaux types de données. Cela conduit à la nécessité de prendre en charge les éléments qui ont été précédemment sous-composants dans les types de données d’origine.  
  
 Les fonctions suivantes de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge ces exigences :  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]prend en charge les types de données standard pour toutes les versions de HL7 à partir de la version 2.1.  
  
-   Vous pouvez limiter les types de données lorsque cela est approprié lorsque vous développez des interfaces.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [ID de Type de données dans HL7 2.1](../../adapters-and-accelerators/accelerator-hl7/data-type-id-in-hl7.md)