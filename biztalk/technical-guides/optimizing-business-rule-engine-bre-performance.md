---
title: "Optimisation des performances du moteur (BRE) règle métier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c271b059-174d-4e8b-88b5-c3f408a97f1f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14c3adf32ac06d80c1aab8f870d82156470097a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-business-rule-engine-bre-performance"></a>Optimisation des performances du moteur (BRE) règle métier
Les facteurs suivants doivent être pris en compte lors de l’implémentation du moteur de règles d’entreprise (BRE) dans une solution BizTalk Server :  
  
## <a name="fact-types"></a>Types de faits  
 Le moteur de règles prend moins de temps pour l’accès aux faits .NET par rapport au temps que nécessaire pour les faits XML et de la base de données access. Si vous avez le choix de l’utilisation de faits .NET, XML ou de base de données dans une stratégie, vous devez envisager d’utiliser des faits .NET pour améliorer les performances.  
  
## <a name="data-table-vs-data-connection"></a>Table de données et la connexion de données  
 Lorsque la taille du jeu de données est petite (< 10 ou ainsi), le **TypedDataTable** liaison fournit de meilleures performances que la **DataConnection** liaison. Toutefois, le **DataConnection** liaison offre de meilleures performances que la **TypedDataTable** liaison lorsque le jeu de données est importante (supérieur ou égal à 10 lignes environ). Par conséquent, vous devez décider s’il faut utiliser le **DataConnection** liaison ou **TypedDataTable** liaison basée sur la taille estimée du jeu de données.  
  
## <a name="fact-retrievers"></a>Extracteurs de faits  
 Un extracteur de faits implémente des méthodes standards qui sont généralement utilisés pour fournir des faits à long terme et à variation lente au moteur de règles avant l’exécution d’une stratégie. Le moteur met en cache ces faits et les utilise pendant plusieurs cycles d'exécution. Au lieu de soumettre un fait de statique ou relativement statique chaque fois que vous appelez le moteur de règles, vous devez créer un extracteur de faits qui envoie le fait pour la première fois, puis met à jour en mémoire uniquement lorsque cela est nécessaire.  
  
## <a name="rule-priority"></a>Priorité de la règle  
 Le paramètre de priorité d’une règle peut varier de chaque côté de **0**, avec le plus grand nombre, ayant une priorité plus élevée. Actions sont exécutées dans l’ordre de priorité la plus élevée à la priorité la plus faible. Lorsque la stratégie implémente le comportement de chaînage avant à l’aide de **Assert/mise à jour** des appels, le chaînage des propriétés peuvent être optimisées à l’aide du paramètre de priorité. Par exemple, supposons que **règle2** a une dépendance sur une valeur définie par **règle1**. En donnant **règle1** une priorité plus élevée signifie que **règle2** s’exécutera uniquement après **règle1** est activé et met à jour la valeur. À l’inverse, si **règle2** ont été reçoit une priorité plus élevée, il pourrait déclencher qu’une seule fois et puis déclenchent après avoir **règle1** est activé et le fait de mettre à jour qui **Rule2** est l’utilisation d’une condition. Alors que cela peut indiquer un résultat correct, ce qui donne **règle1** une priorité plus élevée dans ce scénario pour de meilleures performances.  
  
## <a name="update-calls"></a>Appels de mise à jour  
 La fonction de mise à jour entraîne de toutes les règles à l’aide de faits mis à jour pour être réévalué. Appels de fonction de mise à jour peuvent être coûteuses en particulier si un grand ensemble de règles est réévalué lors de la mise à jour des faits. Il existe des situations où ce comportement peut être évité. Par exemple, respectez les règles suivantes.  
  
 **Règle1 :**  
  
```  
IF PurchaseOrder.Amount > 5   
THEN StatusObj.Flag = true; Update(StatusObj)  
```  
  
 **Règle2 :**  
  
```  
IF PurchaseOrder.Amount <= 5   
THEN StatusObj.Flag = false; Update(StatusObj)  
```  
  
 Toutes les règles restantes de l’utilisation de la stratégie **StatusObj.Flag** dans leurs conditions. Par conséquent, lorsque **mise à jour** est appelée sur le **StatusObj** de l’objet, toutes les règles sont réévaluées. Quelle que soit la valeur de la **quantité** champ est, toutes les règles, à l’exception **règle1** ou **Rule2** sont évaluées à deux reprises, une fois avant la **mise à jour** appeler et une seule fois après le **mise à jour** appeler.  
  
 Pour atténuer associé surcharge, vous pouvez définir la valeur de la **indicateur** au champ **false** avant d’appeler la stratégie et puis uniquement **règle1** dans la stratégie pour définir l’indicateur . Dans ce cas, **mise à jour** est appelée uniquement si la valeur de la **quantité** champ est supérieure à 5 et le **mise à jour** fonction n’est pas appelée si la valeur de  **Quantité** est inférieur ou égal à 5. Par conséquent, toutes les règles, à l’exception **règle1** ou **règle2** sont évaluées deux fois uniquement si la valeur de la **quantité** champ est supérieure à 5.  
  
## <a name="usage-of-logical-or-operators"></a>Utilisation des opérateurs OR logiques  
 À l’aide d’un nombre croissant d’opérateurs OR logiques dans les conditions crée des permutations supplémentaires qui étendent le réseau d’analyse du moteur de règles. À partir d’un point de vue des performances, il est préférable de la fractionner les conditions dans des règles atomiques qui ne contiennent pas les opérateurs OR logiques.  
  
## <a name="caching-settings"></a>Paramètres de mise en cache  
 Le moteur de règles utilise deux caches. La première est utilisée par le service de mise à jour et la deuxième est utilisée par chaque processus BizTalk. La première fois qu’une stratégie est utilisée, le processus BizTalk demande les informations de stratégie à partir du service de mise à jour. Le service de mise à jour extrait les informations de stratégie de la base de données du moteur de règles, met en cache et retourne les informations de processus BizTalk. Le processus BizTalk crée un objet de stratégie en fonction de ces informations et stocke l’objet de stratégie dans un cache lorsque l’instance du moteur de règles associé termine l’exécution de la stratégie. Lorsque la même stratégie est à nouveau appelée, le processus BizTalk réutilise l’objet de stratégie à partir du cache si celle-ci est disponible. De même, si le processus BizTalk demande des informations sur une stratégie à partir du service de mise à jour, le service de mise à jour recherche les informations de stratégie dans son cache s’il est disponible. Toutes les 60 secondes, le service de mise à jour vérifie également si les mises à jour la stratégie dans la base de données ont été. S’il existe des mises à jour, le service de mise à jour récupère les informations et met en cache les informations mises à jour.  
  
 Il existe trois paramètres de réglage du moteur de règles associé à ces caches : **CacheEntries**, **CacheTimeout**, et **PollingInterval**. Vous pouvez définir les valeurs de ces paramètres dans le registre ou dans un fichier de configuration. La valeur de la **CacheEntries** paramètre est le nombre maximal d’entrées dans le cache et une valeur de 32 a la valeur par défaut. Vous pouvez souhaiter augmenter la valeur de la **CacheEntries** paramètre pour améliorer les performances dans certains scénarios. Par exemple, supposons que vous utilisez 40 stratégies à plusieurs reprises ; vous n’a pu pour augmenter la valeur de la **CacheEntries** paramètre à 40 afin d’améliorer les performances. Ainsi, le service de mise à jour mettre à jour les détails du cache de jusqu'à 40 stratégies en mémoire.  
  
 La valeur de **CacheTimeout** est la durée en secondes pendant laquelle une entrée est conservée dans le cache du service de mise à jour. En d’autres termes, le **CacheTimeout** valeur fait référence à la durée pendant laquelle une entrée de cache pour une stratégie est conservée dans le cache sans référencé. La valeur par défaut **CacheTimeout** paramètre est 3 600 secondes ou 1 heure. Cela signifie que si l’entrée de cache n’est pas référencée dans l’heure, l’entrée est supprimée. Dans certains cas, il peut être utile d’augmenter la valeur de la **CacheTimeout** paramètre pour améliorer les performances. Par exemple, si une stratégie est appelée toutes les deux heures, de l’exécution de la stratégie serait améliorer les performances en augmentant la **CacheTimeout** paramètre à une valeur supérieure à deux heures.  
  
 Le **PollingInterval** paramètre du moteur de règles définit la durée en secondes pour le service de mise à jour à la base de données du moteur de règle pour les mises à jour. La valeur par défaut pour le **PollingInterval** paramètre est de 60 secondes. Si vous savez que les stratégies de plus mis à jour tout ou sont rarement mis à jour, vous pouvez modifier ce paramètre et une valeur plus élevée pour améliorer les performances.  
  
## <a name="sideeffects-property"></a>Propriété SideEffects  
 Le **ClassMemberBinding**, **Xmldocumentfieldbinding**, et **XmlDocumentFieldBinding** classes possèdent une propriété nommée **SideEffects**. Cette propriété détermine si la valeur du membre, de la colonne ou du champ lié est mise en cache. La valeur par défaut de la **SideEffects** propriété dans le **Xmldocumentfieldbinding** et **XmlDocumentFieldBinding** classes est **false**. La valeur par défaut de la **SideEffects** propriété dans le **ClassMemberBinding** classe est **true**. Par conséquent, lorsqu'une colonne d'une table de base de données ou qu'un champ d'un document XML est accédé pour la deuxième fois ou ultérieurement dans la stratégie, sa valeur est extraite du cache. Toutefois, lorsqu'un membre d'un objet .NET est accédé pour la deuxième fois ou ultérieurement, la valeur est extraite de cet objet, et non pas du cache. Définissant le **SideEffects** propriété de .NET **ClassMemberBinding** à **false** améliore les performances, car la valeur du champ est récupérée à partir du cache à partir de la deuxième fois. Vous pouvez uniquement le faire par programme. L’outil Éditeur des règles d’entreprise n’expose pas le **SideEffects** propriété.  
  
## <a name="instances-and-selectivity"></a>Instances et sélectivité  
 Le **XmlDocumentBinding**, **ClassBinding**, et **DatabaseBinding** classes ont deux propriétés : **Instances** et **Sélectivité**. La valeur des Instances est le nombre attendu d’instances de la classe dans la mémoire de travail. La valeur de **sélectivité** est le pourcentage des instances de classe qui rempliront les conditions de règle. Le moteur de règles utilise ces valeurs pour optimiser l'évaluation des conditions afin que le moins d'instances possible soient utilisées dans les évaluations de conditions dans un premier temps, puis que les instances restantes soient utilisées. Si vous avez une connaissance préalable du nombre d’instances de l’objet, la définition de la **Instances** propriété à cette valeur améliorera les performances. De même, si vous avez une connaissance préalable du pourcentage de ces objets remplissant les conditions, la définition de la **sélectivité** propriété à cette valeur améliorera les performances. Vous pouvez uniquement définir les valeurs de ces paramètres par programme. L'outil Éditeur des règles d'entreprise ne les expose pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances de BizTalk Server](../technical-guides/optimizing-biztalk-server-performance.md)