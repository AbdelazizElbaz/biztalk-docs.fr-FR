---
title: "Validation avec des règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, process management solutions
- process management solution tutorial, validating
- business rules, validating
- process management solution tutorial, business rules
ms.assetid: a67f3781-629a-4157-9a27-3b73d7a5a3a8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8926cf8bd95c2b90c7d16151b47f8893120b812e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validation-with-business-rules"></a>Validation avec des règles d’entreprise
Une méthode courante pour effectuer une validation consiste à créer un ensemble de règles d'entreprise à l'aide de l'infrastructure des règles d'entreprise. Vous pouvez ensuite utiliser la forme Appeler règles dans l'orchestration où vous voulez effectuer la validation.  
  
 Dans l’application de gestion des processus métier, les **Validation** orchestration utilise des règles d’entreprise pour tester la validité de la commande.  
  
 À l’aide de l’infrastructure des règles d’entreprise permet de modifier les règles sans avoir à recompiler et redéployer le **Validation** orchestration. Le compromis est que, pour les ensembles de règles simples, vous pouvez être en mesure d'enregistrer la durée de traitement en codant la logique dans l'orchestration.  
  
 Pour plus d’informations sur l’utilisation de l’infrastructure des règles d’entreprise, consultez [création et à l’aide des règles d’entreprise](../core/creating-and-using-business-rules.md). Pour plus d’informations sur la forme Appeler règles, consultez [l’utilisation de la forme de règles d’appeler](../core/how-to-use-the-call-rules-shape.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Logique du Gestionnaire de processus](../core/process-manager-logic.md)