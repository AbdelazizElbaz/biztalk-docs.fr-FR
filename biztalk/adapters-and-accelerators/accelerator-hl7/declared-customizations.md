---
title: "Déclaré personnalisations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- declared customizations
- Z objects, declared customizations
- customizing, Z objects
- customizing, declared customizations
ms.assetid: 484655e9-8bfa-4643-bbe6-4ef69cbd83ad
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 767fdd543b1cb5d87bf3ec1c1943ac81d91c6ea4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="declared-customizations"></a>Personnalisations déclarées
Avec des personnalisations déclarées, vous avez la possibilité de modification ou ajout de messages de HL7. Vous pouvez même définir un nouveau type de message. Pour cela, dans une des manières suivantes :  
  
-   Modification de la définition d’un message en définissant un nouvel événement de message type ou d’un déclencheur  
  
-   Ajout d’un nouveau segment à un type de message existant  
  
-   Modification du type de données d’une partie de message existante (segment, champ, composant ou sous-composant)  
  
-   Modification des valeurs possibles que vous pouvez utiliser dans une partie de message existante  
  
    > [!NOTE]
    >  Vous pouvez modifier les valeurs d’énumération utilisées dans les objets de Z déclarées ou le standard dans les schémas HL7. Pour ce faire, consultez [énumérations d’extension](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md).  
  
 Vous modifiez ou que vous ajoutez aux messages de HL7 en ajoutant, en conservant et en associant des objets personnalisés dans les types de messages actuellement définis. Les normes HL7 appellent ces objets personnalisés « Objets Z » pour les différencier des objets existants qui sont conformes à la norme HL7. L’Éditeur BizTalk vous permet de définir les objets Z. Vous montre également comment utiliser l’Éditeur BizTalk pour utiliser les fonctionnalités qui se propagent de mises à jour à un objet Z sur tous les événements de déclencheur et messages abstraits qui l’incluent. Pour plus d’informations sur la création d’objets de Z, consultez [HL7 d’extension des schémas 2.X avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md).  
  
 Vous pouvez utiliser des objets de Z à attribuer des définitions locales aux segments que vous utilisez de façons non spécifiées dans la norme HL7. Vous apportez ces modifications aux schémas BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Assistant de configuration installé sur votre ordinateur. Vous pouvez ensuite partager ces schémas modifiés avec d’autres [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] installations avec laquelle vous échangez des messages.  
  
## <a name="types-of-z-objects"></a>Types d’objets de Z  
 La norme HL7 (2.X) prend actuellement en charge les formes de personnalisation suivantes :  
  
-   **Événements de déclencheur personnalisé.** Si vous sur un réseau local et le besoin d’une nouvelle structure de message, ou à un événement déclencheur qui n’est pas inclus dans la norme de prendre en charge, vous pouvez créer un nouvel événement de déclencheur à l’aide d’un préfixe de Z, par exemple, Z05. Dans ce cas, vous devez créer un nouveau schéma de message local en définissant le message abstrait et le modèle de segments inclus.  
  
-   **Segments personnalisés.** Si vous êtes sur un réseau local, dans le contexte d’un événement déclencheur déjà pris en charge et ayant besoin de données supplémentaires, vous pouvez créer un nouveau segment ou des segments et incluent les éléments de données que vous souhaitez conserver dans le segment. Vous devez spécifier les éléments dans le segment à l’aide des types de données HL7 existants. Vous pouvez créer des segments Z personnalisés dans l’Éditeur BizTalk, en créant un nouvel enregistrement dans le schéma. Pour plus d’informations, consultez [création des Segments déclaré Z](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md). Vous pouvez également ajouter un segment de Z à la base de données Access et ajout de ce segment de Z à la structure du message. Pour plus d’informations, consultez [résolution des erreurs de base de données](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md).  
  
-   **Sous-types de données personnalisé.** HL7 fournit une liste de types de données pris en charge, par exemple, texte mis en forme, analysé l’image, les données audio. Toutefois, si vous souhaitez définir des types de données supplémentaires, vous pouvez effectuer en faisant précéder la mnémonique utilisée avec un « Z », créant ainsi une données Z entrer.  
  
    > [!NOTE]
    >  Il n’est pas autorisée dans les limites de la norme, pour créer de nouveaux types de données ou pour ajouter des éléments à un segment existant. Toujours inférieur est autorisée à prendre un élément qui n’est pas actuellement utilisé et redéfinir pour répondre à des fins supplémentaires. En revanche, les organisations qui prennent en charge les interfaces héritées peuvent doivent prendre en charge de ces pratiques.  
  
-   **Tables personnalisées.** D’objets existants dans les messages ont une plage limitée de valeurs spécifiques, telles que définies par des énumérations dans les tables définies par les schémas HL7 courants. Vous pouvez modifier ces énumérations pour activer des valeurs supplémentaires en créant des tables Z.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisations non déclarées](../../adapters-and-accelerators/accelerator-hl7/undeclared-customizations.md)   
 [Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)