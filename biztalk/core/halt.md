---
title: "Arrêter | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Halt function [Business Rules Engine]
ms.assetid: 468ba6dd-2bb2-4787-a824-1f5455508efd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07ca8091d4ff4405704314d72939758c7600a71a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="halt"></a>Interrompre
Vous pouvez utiliser la **arrêter** fonction pour arrêter l’exécution du moteur de règles en cours. Le **arrêter** fonction prend un paramètre de type `Boolean`. Si vous spécifiez la valeur `true` pour le paramètre, le moteur de règles efface également l'agenda contenant les règles candidates en attente.  
  
 Le **Policy.Execute** (méthode) est essentiellement un wrapper autour de le **RuleEngine.Execute** (méthode). Son code est similaire au code suivant :  
  
```  
RuleEngine.Assert(facts);   
RuleEngine.Execute();   
RuleEngine.Retract(facts);  
```  
  
 Si vous utilisez la **Policy.Execute** méthode pour exécuter une stratégie, le moteur de règles rend le contrôle à la **Policy.Execute** (méthode) lorsque le **arrêter** fonction est exécutée. Le **Policy.Execute** méthode retire les faits et retourne le contrôle à l’appelant. Dans ce cas, l'exécution interrompue de la stratégie ne peut être reprise. La même chose se produit lorsque vous utilisez la **appeler règles** forme pour appeler la stratégie.  
  
 Toutefois, si vous utilisez la **RuleEngine.Execute** (méthode) directement pour exécuter la stratégie, vous pouvez reprendre l’exécution interrompue de la stratégie avec la prochaine en attente de l’activation de la règle en appelant simplement **RuleEngine.Execute** Nouveau (à condition que vous ne pas qu’aucun objet nécessaire entre les deux appels). Voici l'exemple de code permettant de reprendre l'exécution interrompue de la stratégie :  
  
```  
//assert facts into working memory of the rule engine instance  
RuleEngine.Assert(facts);   
//execute the policy  
RuleEngine.Execute();   
//policy invokes the Halt method when executing actions.   
//control is returned to here when the Halt method is invoked  
  
//when engine is halted do the following  
//Add your code here  
  
//To resume the halted rule engine execution  
RuleEngine.Execute();  
//retract or remove facts frm the working memory of the rule engine  
RuleEngine.Retract(facts);  
```  
  
 Notez que la **Policy.Execute** méthode met en cache les instances du moteur de règles pour de meilleures performances. Lorsque vous utilisez la **RuleEngine.Execute** directement la méthode, le moteur de règles instances ne sont pas mises en cache.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de contrôle du moteur](../core/engine-control-functions.md)