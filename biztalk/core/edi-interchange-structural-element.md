---
title: "Élément structurel d’un échange EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03f47ae2-fa0f-4d88-a700-85f3d515d2d0
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc07ae40a3665b47b446b61e24954ca9c588a6a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-interchange-structural-element"></a>Élément structurel d'un échange EDI
L'échange est l'élément structurel de plus haut niveau d'un message EDI. Il contient un ensemble d'un ou plusieurs groupes échangés par deux partenaires. La destination d'un échange doit être un partenaire commercial unique. Les échanges peuvent contenir des documents informatisés/messages d'un ou plusieurs types.  
  
 Dans le cadre d'un échange, celui-ci, ainsi que les groupes et les documents informatisés/messages qu'il inclut sont définis par des en-têtes. Les segments, les éléments de données et les sous-éléments sont délimités par des séparateurs. Chaque séparateur a une valeur par défaut, mais peut être défini à l'aide d'un autre caractère par le tiers. Dans les échanges EDIFACT, les caractères sélectionnés pour être utilisés comme séparateurs au sein de l'échange sont définis dans un en-tête d'échange UNA distinct. Dans les échanges X12, les séparateurs sont définis dans l'en-tête d'échange ISA. Le séparateur d'éléments de données correspond au caractère situé en quatrième position et le terminateur de segment de données est le caractère situé en dernière position. Les autres séparateurs X12 et l'ensemble des séparateurs EDIFACT sont définis par des champs : par exemple, le séparateur de composants X12 est défini par le champ ISA16 et le séparateur d'éléments de données EDIFACT est défini par le champ UNA2.  
  
 L'échange inclut une enveloppe qui définit le message EDI. Celle-ci doit commencer par un en-tête d'échange (ISA dans X12 ou UNA/UNB dans EDIFACT) et doit se terminer par un code de fin d'échange (IEA/UNZ). L'en-tête d'échange inclut les éléments qui définissent l'expéditeur et le destinataire, une date et une heure, un numéro de version, un numéro de contrôle qui correspond à l'en-tête et au code de fin, ainsi que d'autres informations.  
  
 Les champs ISA12 et GS8 (pour les échanges X12) et le champ UNH2 (pour les échanges EDIFACT) incluent les informations de version nécessaires à la détection du schéma.  
  
 Le code de fin d'échange est associé à un élément qui indique le nombre de groupes au sein de l'échange.  
  
> [!NOTE]
>  L'en-tête de sécurité fonctionnel, l'en-tête d'assurance fonctionnel, le segment de valeur de sécurité fonctionnel et les segments de code de fin de sécurité n'entrent pas dans le cadre de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI et AS2. Si un échange avec ces segments est reçu, il est interrompu avec un journal des erreurs indiquant qu'il s'agit de segments non identifiés.