---
title: "Comment créer des schémas pour les enveloppes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1c991c-447f-497e-803c-1cb8cad2846b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7308a093f9f95ce2342f268554deb67193aea053
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-schemas-for-envelopes"></a>Créer des schémas pour les enveloppes

## <a name="overview"></a>Vue d'ensemble
Après avoir créé un schéma de message XML, comme décrit dans [création de schémas pour les Messages XML](../core/how-to-create-schemas-for-xml-messages.md), définissez le **enveloppe** propriété de la **schéma** nœud **Oui**. En fonction de certaines caractéristiques de votre schéma d'enveloppe, par exemple selon qu'il y a plusieurs nœuds racine, vous devrez définir plusieurs autres propriétés propres aux enveloppes. Pour plus d’informations, consultez [schémas d’enveloppe](../core/envelope-schemas.md).  
  
 La propriété XPath de corps de l'enveloppe pointe sur l'élément qui contient les éléments de document. L'élément réel vers lequel XPath pointe n'appartient pas au document.  
  
## <a name="see-also"></a>Voir aussi  
-  [Gestion des schémas dans des projets](../core/managing-schemas-within-projects.md)
-  **Enveloppe** propriété[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]