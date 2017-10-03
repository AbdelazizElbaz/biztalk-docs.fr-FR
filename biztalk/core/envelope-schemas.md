---
title: "Les schémas d’enveloppe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af296c30-95dc-4fef-9aa3-bea2f2cd8caf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03c44f1a5d9797ec09cc164789148287c98b4399
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="envelope-schemas"></a>Schémas d’enveloppe

## <a name="overview"></a>Vue d'ensemble
Vous pouvez créer un schéma d'enveloppe de la même façon que vous pouvez créer un schéma XML pour un document commercial. Vous pouvez créer un schéma à partir d'un message d'instance d'enveloppe XML bien formé ou à partir de représentations de définition de type de document (DTD) ou XDR (XML-Data Reduced) du schéma d'enveloppe. Vous pouvez également créer un schéma en association ou non avec d'autres schémas. Les schémas d'enveloppe étant généralement beaucoup plus petits et moins compliqués que la plupart des schémas de document commercial, la création de schémas d'enveloppe est une alternative viable dans la majorité des cas.  
  
 Pour définir un schéma en tant qu’un schéma d’enveloppe, vous devez définir le **enveloppe** propriété de la **schéma** nœud à la valeur **Oui**. Lorsque vous définissez un schéma d’enveloppe, vous devez faire de l’enveloppe **XPath de corps** au nœud parent qui contient uniquement le \<tout > élément enfant. Pour que l'assembleur XML utilise l'enveloppe, le nœud parent ne doit pas contenir d'autres éléments.  
  
 Lorsque vous définissez **enveloppe** propriété **Oui**, cela signifie que le contenu réel du message d’instance XML (appelé corps du message) est présent à l’intérieur de la racine **enregistrement**  nœud de ce schéma, tel que spécifié par le **XPath de corps** propriété de ce nœud. Par conséquent, vous devez également définir des propriétés supplémentaires sur la base de diverses conditions :  
  
-   Si un schéma d’enveloppe a une racine unique, vous devez définir le **XPath de corps** propriété pour cette racine.  
  
-   Si un schéma d’enveloppe a plusieurs racines et **référence de racine** propriété n’est pas définie, vous devez définir le **XPath de corps** propriété pour toutes les racines.  
  
-   Si un schéma d’enveloppe a plusieurs racines et **référence de racine** est définie, vous devez définir le **XPath de corps** propriété de la racine correspondante **enregistrement** nœud. Vous pouvez éventuellement définir le **XPath de corps** propriété pour les racines restantes.  
  
-   Qu’un schéma d’enveloppe possède une ou plusieurs racines, en définissant le **[référence de racine** propriété n’est pas requise.  

Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="see-also"></a>Voir aussi  
 [Différents Types de schémas BizTalk](../core/different-types-of-biztalk-schemas.md)   
 [Comment créer des schémas pour les enveloppes](../core/how-to-create-schemas-for-envelopes.md)