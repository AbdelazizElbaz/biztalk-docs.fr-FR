---
title: "La gestion des Segments de Z non déclaré | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Z segments, 2.X schemas
- 2.X schemas, undeclared Z segments
- segments, undeclared [Z objects]
- Z objects, undeclared segments
ms.assetid: 8878bc93-1833-4bfc-b80e-305e4144739e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ff982aedee39ed60820a9f03db11d7e4d051a34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-undeclared-z-segments"></a>La gestion des Segments de Z non déclaré
Il existe deux types de segments de Z : déclaré segments à Z et les segments Z non déclarés. Pendant qu’elles sont similaires dans la mesure où les utiliser à des fins local, ils sont très différents de la façon de les utiliser.  
  
 Vous incluez la définition d’un segment de Z déclaré dans un schéma de message, et [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) utilise pour traiter un message, tout comme un schéma défini par la norme HL7. Aucun schéma ne définit un segment de Z non déclaré. Vous incluez un segment non déclaré de Z à la fin d’un message, et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] traverse sans traitement par rapport à un schéma. L’analyseur et le sérialiseur ne valident pas il. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]la traite comme un objet binaire volumineux (BLOB). La seule pour vérifier que [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] est sur un plan non déclaré segment consiste à vérifier que l’objet BLOB n’inclut pas les balises de schéma de trois caractères existant.  
  
 Vous incluez le segment Z non déclaré en tant que la troisième partie, ou Z, d’un message à parties multiples. Le message inclut l’en-tête, le corps et la partie Z. La partie Z possède un ID de segment commençant par la lettre « Z ».  
  
> [!NOTE]
>  Le Zpart doit toujours contenir des données. Spécification de valeur null pour les résultats de flux de données dans une condition d’erreur. Si aucune donnée n’est incluse dans le Zpart, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] insère le mot « Vide » dans le Zpart. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]utilise la propriété de contexte **ZPartPresent** pour déterminer s’il faut sérialiser la partie Z.  
  
> [!CAUTION]
>  [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]a testé les Zsegments des jeux de caractères ANSI, avec le résultat que le comportement Zsegment avec des caractères ANSI est prévisible. Toutefois, à l’aide d’autres jeux de caractères dans Zsegments peut entraîner un comportement imprévisible.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Création de Segments de Z déclaré](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [Création de Types de données personnalisés dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [Création de Tables personnalisées dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)