---
title: "À propos de la Session 2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3ecdb4f-d384-42ac-9776-e7ad14d5f151
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b9d34038acceb0bd52dc598ca48cf5e914d70d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-session-management"></a>À propos de la gestion des sessions
L'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne crée une session de connexion permettant d'envoyer un appel au serveur JD Edwards EnterpriseOne. Lorsque l'appel est terminé, la session est placée dans un pool afin d'être réutilisée lors d'un appel suivant. L'adaptateur crée plusieurs sessions de connexion afin de traiter des appels simultanés en direction du serveur JD Edwards EnterpriseOne. Le pool est régulièrement nettoyé afin de supprimer les sessions qui ne sont plus nécessaires.  
  
 L'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne fournit deux propriétés de contexte de message permettant de contrôler le moment d'exécution des appels au sein d'une même session.  
  
|Nom|Type|Valeur par défaut|  
|----------|----------|-------------|  
|JDE.SessionID|int|0|  
|JDE.ReserveSession|boolean|false|  
  
 La gestion de session n'est pas requise si la fonction commerciale nécessite un appel unique au serveur JD Edwards EnterpriseOne. L'adaptateur peut récupérer toute session disponible et celle-ci reste accessible pour tout appel suivant. Dans ce scénario, vous pouvez ignorer les propriétés de contexte de message étant donné que leur valeur par défaut est appropriée.  
  
 Certaines fonctionnalités de JD Edwards EnterpriseOne, telles que la création de SalesOrder, nécessitent d'effectuer plusieurs appels au serveur JD Edwards EnterpriseOne. Le premier appel effectué à BeginDoc crée un élément SalesOrder vide. Chaque appel suivant effectué à EditLine lui ajoute un élément de ligne. Pour terminer, l'appel effectué à EndDoc termine SalesOrder.  
  
```  
BeginDoc  
   EditLine  
   EditLine  
   ...  
EndDoc  
```  
  
 Pour que cette opération réussisse, tous les appels passés à SalesOrder doivent être effectués sous la même session. Pour ce faire, affectez des propriétés de contexte de message pour indiquer à l'adaptateur les actions que la session doit effectuer. Pour SalesOrder par exemple, les valeurs suivantes sont celles qui doivent être affectées aux propriétés de contexte de message afin de gérer la session JD Edwards EnterpriseOne :  
  
|Fonction|SessionID|ReserveSession|  
|--------------|---------------|--------------------|  
|BeginDoc|0|true|  
|EditLine|Copié de la réponse BeginDoc|true|  
|EditLine|Copié de la réponse BeginDoc|true|  
|EndDoc|Copié à partir de la réponse BeginDoc|false|  
  
-   Pour le premier appel, l'adaptateur est libre de choisir une session disponible (car la valeur de SessionID est zéro).  
  
-   L'adaptateur renvoie l'élément SessionID qui a été utilisé dans la réponse BeginDoc.  
  
-   La propriété ReserveSession indique à l'adaptateur de réserver cette session pour des appels ultérieurs qui exigent explicitement l'utilisation de celle-ci. Ainsi, aucun autre appel ne pourra réutiliser accidentellement la session, car celle-ci est réservée.  
  
-   En attribuant à l'élément SessionID la valeur renvoyée dans BeginDoc, les appels suivants peuvent passer une requête pour la session.  
  
-   La propriété ReserveSession est définie sur true, du moins jusqu'au dernier appel de la série.  
  
-   Le dernier appel définit la propriété ReserveSession sur false ; de cette manière, la session devient disponible pour n'importe quel appel ultérieur. Toutefois, l'orchestration peut décider de conserver la session pour effectuer d'autres appels.  
  
 Si la session reste inactive pendant un certain moment, elle est récupérée par le garbage collector (ramasse-miettes), même si, par erreur, la session est toujours réservée.  
  
 Pour plus de détails sur les propriétés de contexte de message, consultez la documentation de BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des propriétés de contexte de Message](../core/using-message-context-properties1.md)