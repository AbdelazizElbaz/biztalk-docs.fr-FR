---
title: "Considérations sur les performances lors de l’utilisation du moteur de règles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e9020c2-5152-40f6-940b-d4ce4081f069
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c24a1c6ffb278d257e16c192e5fc7d827df70e24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="performance-considerations-when-using-the-rule-engine"></a>Considérations relatives aux performances lors de l'utilisation du moteur de règles
Cette rubrique explique comment le moteur de règles s'exécute dans divers scénarios et avec différentes valeurs pour les paramètres de configuration/réglage.  
  
## <a name="fact-types"></a>Types de faits  
 Le moteur de règles met moins de temps pour accéder aux faits .NET que pour accéder à ceux de base de données et XML. Si vous avez le choix, utilisez les faits .NET pour obtenir de meilleures performances.  
  
## <a name="data-table-vs-data-connection-binding"></a>Table de données Visual Studio. Liaison de connexion de données  
 Lorsque la taille du jeu de données est petite (moins de 10 lignes environ), le **TypedDataTable** liaison offre de meilleures performances que la **DataConnection** liaison. Lorsque le jeu de données est important (supérieur ou égal à 10 lignes environ), le **DataConnection** liaison offre de meilleures performances que la **TypedDataTable** liaison. Par conséquent, vous devez décider s’il faut utiliser le **DataConnection** liaison ou le **TypedDataTable** liaison basée sur la taille estimée du jeu de données.  
  
## <a name="fact-retrievers"></a>Extracteurs de faits  
 Vous pouvez créer un extracteur de faits, c'est-à-dire un objet qui implémente des méthodes standard et les utilise généralement pour fournir des faits à long terme et variant peu au moteur de règles avant l'exécution de la stratégie. Le moteur met en cache ces faits et les utilise pendant plusieurs cycles d'exécution. Plutôt que d'envoyer un fait statique ou relativement statique chaque fois que vous appelez le moteur de règles, créez un extracteur de faits qui envoie le fait la première fois, puis le met à jour en mémoire uniquement lorsque cela s'avère nécessaire.  
  
## <a name="rule-priority"></a>Priorité de la règle  
 Le paramètre de priorité d’une règle peut varier de chaque côté de **0**, avec le plus grand nombre, ayant une priorité plus élevée. Les actions sont exécutées de la priorité la plus élevée à la priorité la plus faible. Lorsque la stratégie implémente le comportement de chaînage avant à l’aide de **Assert/mise à jour** des appels, le chaînage des propriétés peuvent être optimisées à l’aide du paramètre de priorité. Par exemple, supposons que **règle2** a une dépendance sur une valeur qui est définie par **règle1**. En donnant **règle1** une priorité plus élevée signifie que **règle2** s’exécutera uniquement après avoir **règle1** est activé et met à jour la valeur. À l’inverse, si **règle2** est reçoit une priorité plus élevée, il peut déclencher une seule fois et puis déclenchent après avoir **règle1** est activé et met à jour le fait que **Rule2** utilise dans une condition. Cela peut ou ne pas générer des résultats corrects, mais il est évident que deux déclenchement ont un impact sur les performances par rapport à un seul.  
  
## <a name="update-calls"></a>Appels de mise à jour  
 Le **mise à jour** fonction met à jour un fait qui existe dans la mémoire de travail du moteur de règles et entraîne de toutes les règles qui utilisent le fait mis à jour dans les conditions de réévaluation. **Mise à jour** les appels de fonction peuvent être coûteux, en particulier si de nombreuses règles doivent être réévaluées en raison de la mise à jour des faits. Dans certains cas, la réévaluation des règles peut être évitée. Prenons par exemple les règles suivantes :  
  
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
  
 Toutes les règles restantes de l’utilisation de la stratégie **StatusObj.Flag** dans leurs conditions. Par conséquent, lorsque **mise à jour** est appelée sur le **StatusObj** de l’objet, toutes les règles sont réévaluées. Quelle que soit la valeur de la **quantité** champ est, toutes les règles, à l’exception **règle1** et **Rule2** sont évaluées à deux reprises, une fois avant la **mise à jour** appel et une fois après le **mise à jour** appeler.  
  
 Au lieu de cela, vous pouvez définir la valeur de la **indicateur** au champ **false** avant de vous appeler la stratégie, puis utiliser uniquement **règle1** dans la stratégie pour définir l’indicateur. Dans ce cas, **mise à jour** est appelé uniquement si la valeur de la **quantité** champ est supérieure à 5, et **mise à jour** n’est pas appelé si le montant est inférieur ou égal à 5. Par conséquent, toutes les règles, à l’exception **règle1** et **règle2** sont évaluées deux fois uniquement si la valeur de la **quantité** champ est supérieure à 5.  
  
## <a name="use-of-logical-or-operators"></a>Utilisation des opérateurs OR logiques  
 Le moteur de règles est optimisé pour l’exécution logique **AND** opérateurs il reconstruit la règle il analysé sous forme normale disjonctive ainsi que **ou** opérateur est utilisé uniquement au niveau supérieur. À l’aide d’un nombre croissant de logique **ou** opérateurs dans les conditions crée des permutations supplémentaires qui étendent le réseau d’analyse du moteur de règles, et peut prendre beaucoup de temps pour le moteur de règles normaliser la règle. La liste suivante contient des solutions possibles à ce problème.  
  
-   Modifier la règle en forme normale disjonctive ainsi que les **ou** opérateur est uniquement au niveau supérieur. Notez que le développement d'une règle en forme normale disjonctive dans l'Éditeur des règles d'entreprise peut être complexe. Vous pouvez envisager de créer la règle par programme.  
  
-   Développer un composant d’assistance qui effectue la **ou** operations et retourne une valeur booléenne et utiliser le composant dans la règle.  
  
-   Envisagez de fractionner la règle et d'y rechercher un indicateur défini par une règle exécutée précédemment ou utilisez un objet qui est déclaré par une règle précédemment exécutée, comme illustré dans les exemples suivants :  
  
    -   Règle 1 : IF (un == 1 ou un == 3) puis b = true  
  
         Règle 2 : si (b == true) puis...  
  
    -   Règle 1 : IF (un == 1 ou un == 3) puis assert (nouvelle c())  
  
         Règle 2 : IF (c.flag == true) puis...  
  
## <a name="caching-settings"></a>Paramètres de mise en cache  
 Le moteur de règles utilise deux caches. Le premier se trouve dans le service de mise à jour et le deuxième dans chaque processus BizTalk. Lors de la première utilisation d'une stratégie, le processus BizTalk demande les informations de stratégie auprès du service de mise à jour. Le service de mise à jour les extrait de la base de données du moteur de règles, les met en cache et les retourne au processus BizTalk. Le processus BizTalk crée un objet de stratégie en fonction de ces informations et le stocke dans un cache lorsque l'instance de moteur de règles associée termine l'exécution de la stratégie. Lorsque cette même stratégie est de nouveau appelée, le processus BizTalk réutilise l'objet de stratégie disponible dans le cache, le cas échéant.  
  
 De même, si le processus BizTalk demande des informations sur une stratégie auprès du service de mise à jour, ce dernier les recherche d'abord dans son cache. Le service de mise à jour procède également à des vérifications toutes les 60 secondes (1 minute) afin d'identifier les mises à jour éventuelles apportées à la stratégie dans la base de données. Si des mises à jour ont été effectuées, il extrait les informations et les met en cache.  
  
 Il existe trois paramètres de réglage du moteur de règles associé à ces caches : **CacheEntries**, **CacheTimeout**, et **PollingInterval**. Vous pouvez définir les valeurs de ces paramètres dans le registre ou dans un fichier de configuration.  
  
 La valeur de **CacheEntries** est le nombre maximal d’entrées dans le cache. La valeur par défaut **CacheEntries** est 32. Vous pouvez souhaiter augmenter la valeur de la **CacheEntries** paramètre pour améliorer les performances dans certains cas. Supposons par exemple que vous utilisez 40 stratégies de façon répétée. Dans ce cas vous souhaitez augmenter la valeur de **CacheEntries** à 40 afin d’améliorer les performances. Cela permettra au service de mise à jour de mettre en cache les informations de 40 stratégies maximum, et au service BizTalk de mettre en cache jusqu'à 40 instances de stratégie en mémoire. Le cache du service BizTalk peut comporter plusieurs instances d'une stratégie.  
  
 La valeur de **CacheTimeout** est la durée (en secondes) pour les entrées expire dans le cache du service de mise à jour. En d’autres termes, le **CacheTimeout** valeur fait référence à la durée pendant laquelle une entrée de cache pour une stratégie est conservée dans le cache s’il en existe aucune référence à celle-ci. La valeur par défaut **CacheTimeout** est 3 600 secondes (1 heure). Cela signifie que, si l'entrée en mémoire cache n'est pas référencée dans un délai d'une heure, elle est supprimée. Dans certains cas, il pouvez que vous souhaitez augmenter la **CacheTimeout** valeur pour améliorer les performances. Supposons par exemple que la stratégie est appelée toutes les deux heures. Vous pourriez également améliorer les performances de l’exécution de la stratégie en augmentant la valeur de la **CacheTimeout** paramètre une valeur supérieure à deux heures.  
  
 Le **PollingInterval** paramètre pour le moteur de règles définit le délai en secondes pour l’intervalle auquel le service de mise à jour vérifie la base de données du moteur de règles pour les mises à jour. La valeur par défaut pour le **PollingInterval** est 60 secondes (1 minute). Si vous savez que les stratégies ne seront pas mises à jour ou le seront rarement, augmentez cette valeur afin d'améliorer les performances.  
  
## <a name="sideeffects-property"></a>Propriété SideEffects  
 Le **ClassMemberBinding**, **Xmldocumentfieldbinding**, et **XmlDocumentFieldBinding** classes possèdent une propriété nommée **SideEffects**. Cette propriété détermine si la valeur du membre, de la colonne ou du champ lié est mise en cache. La valeur par défaut de la **SideEffects** propriété dans le **Xmldocumentfieldbinding** et **XmlDocumentFieldBinding** classes est **false**. La valeur par défaut de la **SideEffects** propriété dans le **ClassMemberBinding** classe est **true**. Par conséquent, lorsqu'une colonne d'une table de base de données ou qu'un champ d'un document XML est accédé pour la deuxième fois ou ultérieurement dans la stratégie, sa valeur est extraite du cache. Toutefois, lorsqu'un membre d'un objet .NET est accédé pour la deuxième fois ou ultérieurement, la valeur est extraite de cet objet, et non pas du cache. Définissant le **SideEffects** propriété de .NET **ClassMemberBinding** à **false** améliore les performances, car la valeur du champ est récupérée à partir du cache à partir de la deuxième fois. Vous pouvez uniquement le faire par programme. L’outil Éditeur des règles d’entreprise n’expose pas le **SideEffects** propriété.  
  
## <a name="instances-and-selectivity"></a>Propriétés Instances et Sélectivité  
 Le **XmlDocumentBinding**, **ClassBinding**, et **DatabaseBinding** classes ont deux propriétés : **Instances** et **Sélectivité**. La valeur de **Instances** est le nombre attendu d’instances de la classe dans la mémoire de travail. La valeur de **sélectivité** est le pourcentage des instances de classe qui rempliront les conditions de règle. Le moteur de règles utilise ces valeurs pour optimiser l'évaluation des conditions afin que le moins d'instances possible soient utilisées dans les évaluations de conditions dans un premier temps, puis que les instances restantes soient utilisées. Si vous avez une connaissance préalable du nombre d’instances de l’objet, la définition de la **Instances** propriété à cette valeur améliorera les performances. De même, si vous avez une connaissance préalable du pourcentage de ces objets remplissant les conditions, la définition de la **sélectivité** propriété à cette valeur améliorera les performances. Vous pouvez uniquement définir les valeurs de ces paramètres par programme. L'outil Éditeur des règles d'entreprise ne les expose pas.