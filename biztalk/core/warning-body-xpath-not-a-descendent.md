---
title: 'Avertissement : XPath de corps est pas un descendant. | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.bodyXPathNotDescendant
ms.assetid: bfeff370-9b84-4fd9-81e9-1e54b166f561
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70b5d228e1119bc7c569b45cc6795f3f5b8454ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---body-xpath-not-a-descendent"></a>Avertissement : XPath de corps est pas un descendant.
**Code d’erreur**  
  
 BEC1004  
  
 **Explication**  
  
 Le **XPath de corps** propriété du nœud racine indiqué dans le schéma d’enveloppe fait référence à un nœud qui n’est pas un descendant de ce nœud racine, en fonction des besoins. Cette erreur ne doit pas se produire si le **XPath de corps** propriété est modifiée en dehors de l’Éditeur BizTalk.  
  
 **Action de l’utilisateur**  
  
 Sélectionnez le nœud racine indiqué et sélectionnez la valeur de la **XPath de corps** propriété qui identifie correctement le nœud de niveau supérieur du corps du message associé.