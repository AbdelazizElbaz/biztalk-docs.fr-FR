---
title: "Avertissement : XPath de corps d’enregistrement introuvable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.recordBodyXPathNotFound
ms.assetid: d46e0732-08ce-4292-84d8-56dc020063e2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebd6640aa469fe9383b615d70235ab488c8798f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---record-body-xpath-not-found"></a>Avertissement : XPath de corps d’enregistrement introuvable
**Code d’erreur**  
  
 BEC1008  
  
 **Explication**  
  
 Le **XPath de corps** propriété du nœud racine indiqué dans le schéma d’enveloppe a été trouvée vide ou faisant référence à un nœud qui n’existe pas. Schémas d’enveloppe, tel que spécifié par le **enveloppe** propriété de la **schéma** nœud, doit être une valeur valide le **XPath de corps** propriété de la racine spécifiée nœud de référence dans le schéma.  
  
 Si aucun nœud référence de racine ne spécifié par le **référence de racine** propriété de la **schéma** nœud, le premier nœud racine dans le schéma, le nœud de référence de racine par défaut, est requis pour qu’une valeur valide dans sa  **XPath de corps** propriété. **XPath de corps** valeurs de propriété sont utilisées pour identifier le schéma de chacun des messages contenus dans l’enveloppe.  
  
 **Action de l’utilisateur**  
  
 Sélectionnez le nœud racine indiqué, puis sélectionnez la valeur de la **XPath de corps** propriété qui identifie correctement le schéma du corps du message associé.