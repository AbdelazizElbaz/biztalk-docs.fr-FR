---
title: "Validation étendue (BTS-XSD) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f225115d-8890-4149-8e46-d1bc8af17e62
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed147515b48a23c55e552710d6a76d6df981edd7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extended-bts-xsd-validation"></a>Validation étendue (BTS-XSD)
Le pipeline de réception EDI et le pipeline d'envoi EDI effectuent une validation étendue uniquement si le schéma a été personnalisé à l'aide d'éléments d'un type de données autre qu'EDI. Ces éléments ajoutés ne sont pas validés via la validation EDI. Ils sont donc soumis à la validation étendue. La validation étendue utilise `System.Xml.XmlValidatingReader` et comprend toutes les vérifications qui peuvent être définies dans un XSD standard.  
  
 Vous pouvez configurer la validation étendue pour tous les messages à destination ou en provenance d'un tiers. Pour cela, sélectionnez le **Validation étendue** case à cocher dans la **Validation** page (sous la **paramètres des documents informatisés** section pour X12 ou EDIFACT), dans le onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue. Vous pouvez activer la validation étendue sans activer la validation EDI, ou vice versa.  
  
 La validation étendue comprend les vérifications suivantes :  
  
-   Exigences en matière d'éléments de données et répétitions autorisées  
  
-   Énumérations  
  
-   Validation de la longueur de l'élément de données (min/max).  
  
> [!IMPORTANT]
>  La validation étendue du traitement par lot des messages côté envoi EDI n'est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des messages EDI](../core/edi-message-validation.md)