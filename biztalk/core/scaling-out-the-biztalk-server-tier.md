---
title: "Évolution horizontale du niveau de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, scaling
- scaling, planning
- scaling, load balancing
- host instances, scaling
- scaling, examples
- fault tolerance
- scaling, scaling out
- scaling, fault tolerance
- NLB system, scaling
- scaling, host instances
ms.assetid: 01d1ab20-d7a9-4d0b-a61e-65e56fe5010e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35674e89d8f8104a35718531f2a87f95e8bc67e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-out-the-biztalk-server-tier"></a>Évolution horizontale du niveau BizTalk Server
Pour faire évoluer horizontalement le niveau BizTalk, ajoutez du matériel à la topologie existante. Il est recommandé d'ajouter du matériel dans les scénarios suivants :  
  
-   BizTalk Server devient un goulot d'étranglement qui peut avoir pour origine un des problèmes suivants :  
  
-   UC : si le scénario utilise des pipelines, des mappages ou des orchestrations qui sollicitent beaucoup l'UC, les serveurs BizTalk Server n'auront pas de marge au niveau de l'UC.  
  
-   E/s et mémoire : si les ordinateurs existants ont atteint leur limite maximale de mémoire et e/s, la seule façon d’ajouter des ressources est d’ajouter un autre ordinateur physique.  
  
-   L'évolution verticale est une solution trop onéreuse. Prenons, par exemple, la topologie à un serveur BizTalk dans laquelle l'unité centrale BizTalk a atteint sa capacité maximale. S'il revient moins cher d'ajouter des ordinateurs à processeurs doubles supplémentaires que de mettre à niveau le processeur double et d'installer un processeur quadruple, vous devriez, à la place, faire évoluer horizontalement votre système.  
  
-   L'évolution verticale ne résout pas le goulot d'étranglement. Elle ne fonctionne pas dans les scénarios suivants :  
  
    -   Les E/S sont au niveau maximal sur l'ordinateur BizTalk ; il vous faut donc un autre ordinateur pour les monter en charge.  
  
    -   La mémoire est au niveau maximal pour le système d'exploitation. Dans ce scénario, le seul moyen de monter en charge le système consiste à ajouter un ordinateur BizTalk supplémentaire à la topologie.  
  
 Dans certains scénarios, vous pouvez utiliser des serveurs dédiés pour recevoir des messages, en envoyer et les traiter. Si vous utilisez des serveurs dédiés, il est plus facile d'isoler les problèmes et d'effectuer les opérations de maintenance sur un ordinateur sans atteindre les performances des autres. Vous pouvez ajouter ces ordinateurs en faisant évoluer horizontalement le niveau BizTalk.  
  
## <a name="when-you-cant-scale-out-the-biztalk-tier"></a>Cas dans lesquels l'évolution horizontale du niveau BizTalk est impossible  
  
-   La base de données MessageBox est le goulot d'étranglement.  
  
-   Un adaptateur devient le goulot d'étranglement. Par exemple, si vous utilisez l'adaptateur SQL, quand vous augmentez le nombre de récepteurs BizTalk, les conflits de verrouillage augmentent sur la base de données SQL d'où l'adaptateur BizTalk SQL extrait des données. Cela limite vos possibilités d'évolution horizontale par unité de cet adaptateur.  
  
 La figure suivante illustre comment vous pouvez faire évoluer horizontalement le niveau BizTalk.  
  
 ![Montée en puissance parallèle BTS](../core/media/scaleoutbts.gif "ScaleOutBTS")  
  
 Elle présente une topologie BizTalk ayant fait l'objet d'une évolution horizontale d'un serveur BizTalk à deux serveurs BizTalk. Dans la topologie à un serveur, trois instances de l'hôte partagent les ressources de l'ordinateur BizTalk. Dans la topologie à deux serveurs, l'hôte de transmission est installé sur un serveur différent qui atteint un débit supérieur.  
  
## <a name="considerations-when-scaling-out-the-biztalk-tier"></a>Considérations à prendre en compte lors de l'évolution horizontale du niveau BizTalk  
 Avant d'ajouter un autre ordinateur BizTalk, observez les recommandations suivantes :  
  
#### <a name="how-do-i-configure-the-system-for-load-balancing-and-fault-tolerance-when-i-scale-out-the-biztalk-tier"></a>Comment configure-t-on le système pour l'équilibrage de la charge et la tolérance de pannes lorsque le niveau BizTalk fait l'objet d'une évolution horizontale ?  
 Le choix d'une technologie d'équilibrage de la charge et de tolérance de pannes dépend de l'adaptateur utilisé dans le scénario. Avec des adaptateurs SOAP et HTTP, il est conseillé d'utiliser la technologie d'équilibrage de la charge réseau (NLB). Pour plus d'informations, reportez-vous à votre documentation NLB.  
  
#### <a name="how-do-i-refactor-the-host-instances"></a>Comment refactorise-t-on les instances de l'hôte ?  
 Aucune règle n'indique comment vous devez refactoriser les instances de l'hôte lorsque vous faites évoluer horizontalement le niveau BizTalk. La factorisation des instances de l'hôte dépend de la complexité du scénario. Les exemples suivants illustrent la factorisation des instances de l'hôte.  
  
##### <a name="scenario-1"></a>Scénario 1  
 Configuration à un serveur BizTalk ; les instances de réception et de transmission de l'hôte sont sur le même ordinateur.  
  
 Supposons qu'il y ait un goulot d'étranglement au niveau de l'unité centrale. Vous ajoutez un autre ordinateur BizTalk identique au groupe pour effectuer l'évolution horizontale qui vous donne deux moyens de factoriser les instances de l'hôte.  
  
 Voici deux solutions à ce problème :  
  
-   **Solution 1**: le plus simple de factorisation dans ce scénario consiste à cloner l’ordinateur hôte instance factorisation à partir du premier ordinateur à un second ordinateur. Ce second ordinateur devient alors une copie exacte du premier en terme de fonctionnalités ; il peut aussi avoir des hôtes de réception et d'envoi. Supposons qu'il y ait un autre goulot d'étranglement ; vous pouvez obtenir un facteur d'échelle de 2 lorsque les ressources de l'unité centrale sont doublées.  
  
-   **Solution 2**: un autre moyen de factoriser les instances d’hôte consiste à isoler la réception et envoi des fonctions sur des ordinateurs différents. Ainsi, un des serveurs BizTalk est dédié à la réception et l'autre à l'envoi.  
  
 **Comparaison de la Solution 1 et 2**  
  
 Dans la solution 1, le nombre d'instances de l'hôte est doublé par rapport à la configuration à un serveur. Cela signifie que les conflits de verrouillage sur le serveur SQL Server vont augmenter. L'ampleur de l'augmentation des conflits de verrouillage détermine le facteur d'échelle. Si elle reste dans les limites acceptables sans qu'il y ait de goulot d'étranglement, vous obtenez un facteur d'échelle de 2.  
  
 L’avantage de la solution 2 est que vous disposez uniquement de deux instances d’hôte, les conflits de verrouillage sur le serveur SQL server ne doivent donc être qu'inférieur par rapport à la solution 1. Toutefois, le facteur d’échelle dépend entièrement de la complexité de la réception et envoi des instances de l’hôte. Vous devez prendre en compte les points ci-après dans la solution 2 :  
  
 Supposons que les instances de réception et de transmission de l'hôte réalisent des performances égales et qu'elles utilisent chacune 50 % de l'unité centrale dans la topologie à un serveur BizTalk. Dans la topologie à deux serveurs, vous installez l'instance de transmission de l'hôte sur un serveur différent de sorte que les instances de réception et de transmission obtiennent toutes deux le double des ressources. Vous devez obtenir un facteur d'échelle de 2 étant donné qu'il n'y a pas d'autre goulot d'étranglement. Cette solution est meilleure que la première parce qu'il n'y a que deux instances de l'hôte et partant, moins de conflits de verrouillage.  
  
 Supposons que l'instance de transmission soit beaucoup plus performante que celle de réception et qu'elle utilise 80 % des ressources de l'unité centrale dans la topologie à un serveur BizTalk. En déplaçant l’instance d’hôte de transmission vers un autre ordinateur, vous bénéficiez uniquement de 20 % de ressources pour que le facteur d’échelle maximal soit 1.2. En outre, l’ordinateur avec l’instance d’hôte de réception utilisera uniquement 20-30 % d’UC par conséquent, l’avantage de l’évolution horizontale est beaucoup moins.  
  
 Prenons la figure suivante qui présente une topologie à quatre serveurs BizTalk : Chaque ordinateur est à la fois récepteur et émetteur, constituant ainsi quatre instances de chaque type (réception et transmission).  
  
 ![Re &#45; les instances d’hôte factorisation](../core/media/refactoringhostinstances.gif "RefactoringHostinstances")  
  
 Cette topologie n'est sans doute pas la meilleure. Vous devez aussi tester d'autres changements de facteurs selon la complexité du scénario. Exemple :  
  
-   Dédiez deux ordinateurs à la réception et deux à la transmission. Vous obtenez ainsi une montée en charge optimale lorsque les instances de réception et d'envoi réalisent des performances égales.  
  
-   Dédiez trois ordinateurs à la réception et un à la transmission si l'instance de réception est plus performante que celle de transmission.  
  
-   Dédiez un ordinateur à la réception et trois à la transmission si l'instance de transmission est plus performante que celle de réception.  
  
 Dans tous les cas, il est conseillé de limiter le nombre d'instances de chaque hôte de sorte à réduire les conflits de verrouillage dans la base de données MessageBox et à exploiter pleinement les ressources de l'ordinateur. La meilleure combinaison de facteurs dépend de la complexité du scénario et du type de goulot d'étranglement. Veillez toujours à tester votre facteur avant de finaliser un changement.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à l’échelle verticale du niveau de BizTalk Server](../core/scaling-up-the-biztalk-server-tier.md)   
 [L’évolution verticale du niveau SQL Server](../core/scaling-up-the-sql-server-tier.md)   
 [Montée en puissance parallèle du niveau SQL Server](../core/scaling-out-the-sql-server-tier.md)   
 [Mise à l’échelle des hôtes de réception](../core/scaled-out-receiving-hosts.md)   
 [Mise à l’échelle des hôtes de traitement](../core/scaled-out-processing-hosts.md)   
 [Mise à l’échelle des hôtes d’envoi](../core/scaled-out-sending-hosts.md)   
 [À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [Bases de données à grande échelle](../core/scaled-out-databases.md)   
 [Mise en cluster les bases de données BizTalk Server](../core/clustering-the-biztalk-server-databases1.md)