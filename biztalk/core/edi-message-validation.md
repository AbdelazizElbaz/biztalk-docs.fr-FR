---
title: Validation des messages EDI | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f34561-d280-48bb-b1dd-ce37b87c5023
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21439969bc8e23b5b9901077c14a98128aa64c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-message-validation"></a>Validation des messages EDI
Les données EDI sont transmises sous forme de fichiers délimités (sans balise autodescriptive). Les règles de codage appliquent donc des règles de formatage strictes pour garantir que l'application de destination peut analyser correctement les informations et les utiliser en vue du traitement en aval.  
  
 Le pipeline de réception EDI et le pipeline d'envoi EDI des fonctionnalités EDI et AS2 de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] réalisent une série de validations. Certaines sont effectuées systématiquement ; d'autres seulement si elles sont activées dans les propriétés de l'accord ou dans le schéma. Pour plus d’informations sur la configuration de la validation, consultez [la Validation d’un EDI de l’échange est configuré](../core/how-validation-of-an-edi-interchange-is-configured.md).  
  
 La validation d'un échange EDI implique plusieurs types de validation différents, comme décrit dans les rubriques suivantes.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration de la Validation d’un échange EDI](../core/how-validation-of-an-edi-interchange-is-configured.md)  
  
-   [Validation structurelle EDI](../core/edi-structural-validation.md)  
  
-   [Validation des propriétés de contrat](../core/agreement-properties-validation.md)  
  
-   [Validation de Type (élément de données) EDI](../core/edi-type-data-element-validation.md)  
  
-   [Validation étendue (BTS-XSD)](../core/extended-bts-xsd-validation.md)  
  
-   [Validation de schéma](../core/schema-validation2.md)  
  
-   [Validation de Segment de champ croisée](../core/cross-field-segment-validation.md)