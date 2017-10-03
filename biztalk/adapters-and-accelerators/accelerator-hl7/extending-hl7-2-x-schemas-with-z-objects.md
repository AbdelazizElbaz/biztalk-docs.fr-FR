---
title: "Extension des schémas 2.X HL7 avec des objets Z | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas, Z objects
- Z objects, extending 2.X schemas
ms.assetid: 0980d919-eb81-4c65-b0f7-f17f7cfef6b3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a27ef2bea3e13904f04449a5b77d05672c2b2d94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extending-hl7-2x-schemas-with-z-objects"></a>Extension des schémas 2.X HL7 avec des objets Z
L’organisation HL7 définit HL7 2.X, schémas et attend que tous les expéditeurs et destinataires de reconnaître et utiliser ces schémas comme les définit par l’organisation. Conformes aux schémas garantit l’interopérabilité. Toutefois, la norme HL7 permet de personnaliser HL7 existant schémas 2.X à vos besoins locales spécifiques. Vous pouvez également définir des objets et des schémas entièrement nouvelles. Pour ce faire avec ce que le HL7 standard appelle les objets Z.  
  
 Le HL7 standard ne définit pas la valeur des objets de Z. Les schémas HL7 publiées n’incluent pas les. Vous les définissez localement et que vous les utilisez en accord avec toutes les parties locales. L’organisation HL7 réserve tous les type de message, d’événements déclencheurs, segment, type de données et les noms de tables commençant par « Z » pour cet usage local. En raison du préfixe, la norme HL7 appelle ces objets objets définis par site Z.  
  
> [!NOTE]
>  Lorsque vous ajoutez un objet de Z à un schéma HL7 existant, vous risquez de plusieurs versions de ce schéma. La meilleure façon de gérer ces versions multiples consiste à utiliser la fonctionnalité de Namespace dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. Vous pouvez trouver cette fonctionnalité sur le **Validation** onglet [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration (au niveau du tiers). Vous devez également modifier la propriété de l’espace de noms du schéma que vous déployez pour ce projet.  
  
 Dans la création ou le traitement Z des objets, vous devez suivre les règles de l’organisation HL7 a établi pour les objets Z...  
  
 Lorsque vous ajoutez un objet de Z à un schéma existant ou créer un nouveau schéma de message Z, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] utilise le schéma avec l’ou les objets Z pour traiter le message encodé HL7. Ce type d’objet de Z est un objet Z déclaré. Vous pouvez également utiliser un segment Z non déclaré, le moteur d’intégration ne traitera pas selon le schéma de message. Pour plus d’informations sur ce type de segment de Z, consultez [gestion des Segments de Z non déclaré](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création de Segments de Z déclaré](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)  
  
-   [Création de Types de données personnalisés dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)  
  
-   [Création de Tables personnalisées dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)  
  
-   [Extension des énumérations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)  
  
-   [Personnalisation des Messages via des objets de plan](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md)