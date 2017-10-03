---
title: "Montée en puissance parallèle du niveau SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling, MessageBox database
- scaling, scaling out
- SQL Server, scaling
- MessageBox database, scaling
- scaling, strategies
ms.assetid: d5b2ebba-401e-4fde-8818-407fa626043a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 702c253a0135c1dc4af4cea15a9b47c77792586f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-out-the-sql-server-tier"></a>Évolution horizontale du niveau SQL Server
Pour chaque groupe BizTalk, vous ajoutez une base de données principale MessageBox. Toutes les bases de données MessageBox suivantes que vous ajoutez sont des bases de données secondaires. La base de données principale MessageBox gère tous les abonnements et le routage des messages. Elle permet également la publication de messages. Les bases de données secondaires MessageBox publient des messages uniquement lorsqu'elles sont configurées pour ce faire.  
  
## <a name="how-to-add-a-secondary-messagebox-database"></a>Ajout d'une base de données secondaire MessageBox  
 Il existe deux façons d'ajouter des bases de données secondaires MessageBox :  
  
-   Ajoutez la base de données secondaire MessageBox sur le même serveur physique.  
  
     Procédez de la sorte si le serveur physique MessageBox existant dispose de suffisamment de ressources UC et E/S et s'il est engorgé uniquement par un conflit de verrouillage. Créez la base de données secondaire MessageBox sur des lecteurs d'E/S distincts.  
  
     Avantages :  
  
    -   La marge d'UC supplémentaire peut être utilisée par un autre MessageBox.  
  
    -   Moins de licences serveur SQL sont requises.  
  
    -   Le tronçon réseau est éliminé.  
  
-   Ajoutez la base de données secondaire MessageBox sur un autre serveur physique.  
  
     Dans ce cas utilisez un serveur physique dédié avec sa propre E/S en tant que base de données MessageBox supplémentaire.  
  
 La figure suivante montre un scénario dans lequel le niveau SQL subit une évolution horizontale d'une base de données MessageBox vers trois bases de données MessageBox.  
  
 ![Montée en puissance parallèle de MSGBOX](../core/media/scaleoutmsgbox.gif "ScaleOutMSGBOX")  
  
## <a name="when-to-scale-out-the-messagebox-database"></a>Quand procéder à l'évolution horizontale de la base de données MessageBox  
  
-   La base de données MessageBox devient le goulot d'étranglement. Ces engorgements peuvent être notamment :  
  
    -   **Processeur** en cas de scénarios d’orchestration très coûteux et complexes, la base de données MessageBox consomme des ressources du processeur élevées. L'ajout d'une autre base de données MessageBox dans laquelle la publication est activée doit aider à augmenter le débit.  
  
    -   **Contention de verrouillage** des scénarios complexes avec plusieurs instances d’hôte ou orchestrations ont tendance à créer des conflits de verrouillage sur la base de données MessageBox. Là encore, l'ajout d'une autre base de données MessageBox dans laquelle la publication est activée doit aider à augmenter le débit.  
  
-   L'évolution verticale ne résout pas l'engorgement. Par exemple, si la base de données principale MessageBox est liée par un conflit de verrouillage, l'évolution horizontale est la seule option possible.  
  
-   L'évolution verticale est trop onéreuse. Par exemple, si la mise à niveau du serveur à quatre processeurs vers un serveur à huit processeurs est plus coûteuse que d'ajouter un autre ordinateur à quatre processeurs, l'évolution horizontale est plus intéressante.  
  
## <a name="when-you-cant-scale-out-the-sql-tier"></a>Cas dans lesquels l'évolution horizontale du niveau SQL est impossible  
 En théorie, le niveau SQL doit pouvoir évoluer horizontalement tant que la base de données principale MessageBox ne devient pas le goulot d'étranglement. Pour cela, faites de la base de données principale MessageBox une base de données MessageBox n'acceptant pas la publication afin qu'elle n'effectue que le routage. Toutefois, dès que la base de données principale est engorgée par un conflit de verrouillage, vous ne pouvez plus faire évoluer horizontalement le niveau SQL.  
  
## <a name="scale-out-strategies-and-considerations"></a>Stratégies et recommandations en matière d'évolution horizontale  
  
-   Faites évoluer la base de données principale MessageBox verticalement puis horizontalement.  
  
-   Montée en charge horizontale de 1 à 3 bases de données MessageBox SQL au lieu de 1 à 2. Envisagez la topologie de serveur SQL 1 illustrée la figure ci-dessus intitulée « 4 BizTalk Server, la topologie du serveur SQL 1 » et supposent que le serveur SQL server est lié à l’UC, en d’autres termes, le traitement de l’UC est un goulot d’étranglement. Si vous n'ajoutez qu'une base de données MessageBox à cette topologie, la base de données principale Messagebox restera liée à l'UC et la base de données secondaire MessageBox sera sous-utilisée. Le facteur d’échelle est donc presque de 1. Si vous désactivez la publication sur la base de données principale MessageBox et dédiez la base de données principale MessageBox uniquement pour effectuer un routage, la base de données secondaire MessageBox effectuera la publication. Cependant, cela ne permettra pas d'augmenter le débit global dans la mesure où la base de données secondaire MessageBox devient le seul éditeur et demeure l'engorgement. Par conséquent, le meilleur moyen de procéder à une évolution horizontale dans ce scénario consiste à ajouter 2 bases de données secondaires MessageBox et à désactiver la publication sur la base de données principale MessageBox.  
  
-   La base de données principale MessageBox devient à terme le goulot d'étranglement. Par conséquent, l'ordinateur physique hébergeant la base de données principale MessageBox doit être plus rapide et plus puissant.  
  
-   Pour limiter l'envoi de données sur le réseau (et la surcharge DTC associée), pensez à installer plusieurs bases de données MessageBox sur le même ordinateur physique, avec des lecteurs dédiés. Vérifiez dans le même temps que l'ordinateur hébergeant ces bases de données n'est pas engorgé car les ressources sont partagées par plusieurs bases de données MessageBox.  
  
-   Toutes les bases de données secondaires MessageBox doivent utiliser du matériel comparable parce que le travail est réparti de manière homogène entre les bases de données MessageBox acceptant la publication.  
  
-   Puisque vous pouvez faire évoluer horizontalement des bases de données secondaires MessageBox tant que la base de données principale MessageBox n'est pas engorgée, ces bases secondaires peuvent s'exécuter sur des ordinateurs possédant des ressources d'UC inférieures à celles requises par le serveur de la base de données principale MessageBox.  
  
## <a name="see-also"></a>Voir aussi  
 [Évolution horizontale du niveau de BizTalk Server](../core/scaling-out-the-biztalk-server-tier.md)   
 [Mise à l’échelle verticale du niveau de BizTalk Server](../core/scaling-up-the-biztalk-server-tier.md)   
 [L’évolution verticale du niveau SQL Server](../core/scaling-up-the-sql-server-tier.md)   
 [Mise à l’échelle des hôtes de réception](../core/scaled-out-receiving-hosts.md)   
 [Mise à l’échelle des hôtes de traitement](../core/scaled-out-processing-hosts.md)   
 [Mise à l’échelle des hôtes d’envoi](../core/scaled-out-sending-hosts.md)   
 [À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [Bases de données à grande échelle](../core/scaled-out-databases.md)   
 [Mise en cluster les bases de données BizTalk Server](../core/clustering-the-biztalk-server-databases1.md)