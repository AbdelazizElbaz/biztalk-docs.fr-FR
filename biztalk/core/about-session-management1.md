---
title: "À propos de la Session Management1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1848619-d97a-4f1e-ba94-59861bd7aedf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 336deb34e5587e64c5177cd0a439c756cf0f2b61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-session-management"></a>À propos de la gestion des sessions
L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld crée une session de connexion permettant d'envoyer un appel au serveur JD Edwards OneWorld. Lorsque l'appel est terminé, la session est placée dans un pool afin d'être réutilisée lors d'un appel suivant. L'adaptateur crée plusieurs sessions de connexion afin de traiter des appels simultanés en direction du serveur JD Edwards OneWorld. Le pool est régulièrement nettoyé afin de supprimer les sessions qui ne sont plus nécessaires.  
  
 L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld fournit deux propriétés de contexte de message permettant de contrôler le moment d'exécution des appels au sein d'une même session.  
  
|Nom|Type|Valeur par défaut|  
|----------|----------|-------------|  
|JDE.SessionID|int|0|  
|JDE.ReserveSession|boolean|false|  
  
 La gestion de session n'est pas requise si la fonction commerciale nécessite un appel unique au serveur JD Edwards OneWorld. L'adaptateur peut récupérer toute session disponible et celle-ci reste accessible pour tout appel suivant. Dans ce scénario, vous pouvez ignorer les propriétés de contexte de message étant donné que leur valeur par défaut est appropriée.  
  
 Certaines fonctionnalités de JD Edwards OneWorld, telles que la création de SalesOrder, nécessitent d'effectuer plusieurs appels au serveur JD Edwards OneWorld. Le premier appel effectué à BeginDoc crée un élément SalesOrder vide. Chaque appel suivant effectué à EditLine lui ajoute un élément de ligne. Pour terminer, l'appel effectué à EndDoc termine SalesOrder.  
  
```  
BeginDoc  
   EditLine  
   EditLine  
   ...  
EndDoc  
```  
  
 Pour que cette opération réussisse, tous les appels passés à SalesOrder doivent être effectués sous la même session. Pour ce faire, affectez des propriétés de contexte de message pour indiquer à l'adaptateur les actions que la session doit effectuer. Pour SalesOrder par exemple, voici les valeurs qui doivent être affectées aux propriétés de contexte de message afin de gérer la session JD OneWorld :  
  
|Fonction|SessionID|ReserveSession|  
|--------------|---------------|--------------------|  
|BeginDoc|0|true|  
|EditLine|Copié de la réponse BeginDoc|true|  
|EditLine|Copié de la réponse BeginDoc|true|  
|EndDoc|Copié de la réponse BeginDoc|false|  
  
-   Pour le premier appel, l'adaptateur est libre de choisir une session disponible (car la valeur de SessionID est zéro).  
  
-   L'adaptateur renvoie l'élément SessionID qui a été utilisé dans la réponse BeginDoc.  
  
-   La propriété ReserveSession indique à l'adaptateur de réserver cette session pour des appels ultérieurs qui exigent explicitement l'utilisation de celle-ci. Ainsi, aucun autre appel ne pourra réutiliser accidentellement la session, car celle-ci est réservée.  
  
-   En attribuant à l'élément SessionID la valeur renvoyée dans BeginDoc, les appels suivants peuvent passer une requête pour la session.  
  
-   La propriété ReserveSession est définie sur true, du moins jusqu'au dernier appel de la série.  
  
-   Le dernier appel définit la propriété ReserveSession sur false ; de cette manière, la session devient disponible pour n'importe quel appel ultérieur. Toutefois, l'orchestration peut décider de conserver la session pour effectuer d'autres appels.  
  
 Si la session reste inactive pendant un certain moment, elle est récupérée par le garbage collector (ramasse-miettes), même si, par erreur, la session est toujours réservée.  
  
 Pour plus de détails sur les propriétés de contexte de message, consultez la documentation de BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des propriétés de contexte de Message](../core/using-message-context-properties2.md)   
 [Comment attribuer des valeurs de propriété de contexte de Message](../core/how-to-assign-message-context-property-values2.md)   
 [Didacticiel : Utilisation de l’adaptateur BizTalk pour JD Edwards OneWorld](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-oneworld.md)