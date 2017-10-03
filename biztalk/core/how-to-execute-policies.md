---
title: "L’exécution de stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, policies
- Business Rules Framework, code samples
- Business Rules Framework, programming
ms.assetid: 90d28d9d-0204-47de-a927-26e284c886e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b0aa834150f0d5c84ebb4c757769a2be38f3942
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-execute-policies"></a>L’exécution des stratégies
L’exemple de code suivant montre comment appeler le moteur de règles pour une stratégie d’exécution par programme à l’aide de la **stratégie** classe dans le **Microsoft.RuleEngine** assembly.  
  
```  
xmlDocument = IncomingXMLMessage.XMLCase;  
typedXmlDocument = new Microsoft.RuleEngine.TypedXmlDocument("Microsoft.Samples.BizTalk.LoansProcessor.Case",xmlDocument);  
policy = new Microsoft.RuleEngine.Policy("LoanProcessing");  
policy.Execute(typedXmlDocument);  
OutgoingXMLMessage.XMLCase = xmlDocument;  
policy.Dispose();  
```  
  
## <a name="important-methods-of-the-policy-class"></a>Méthodes importantes de la classe Stratégie  
 Le tableau suivant présente les méthodes importantes de la classe Stratégie et leurs descriptions.  
  
|Méthode de la classe Stratégie| Description|  
|--------------------------------|-----------------|  
|Execute|Ajoute les faits à court terme spécifiés dans la mémoire de travail du moteur de règles et exécute la stratégie à l'aide de l'algorithme correspondance-résolution des conflits-action. Pour plus d’informations sur l’algorithme de l’Action de résolution de conflit de correspondance, consultez [évaluation de Condition et exécution d’Action](../core/condition-evaluation-and-action-execution.md) .|  
|Dispose|Libère les ressources utilisées par le moteur de règles pour l'exécution de la stratégie.|  
|Désactiver|Efface ou réinitialise la mémoire de travail et l'agenda de l'instance de moteur de règles créée pour l'exécution de la stratégie.|  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode Policy.Dispose](../core/policy-dispose-method.md)