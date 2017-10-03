---
title: "Prise en charge pour les appels entrants à l’aide de l’interrogation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae02a93a-808f-4774-a2c4-efdf39a4d49a
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8533ce2829fec956819b311fd6b8f99479f40d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-inbound-calls-using-polling"></a>Prise en charge pour les appels entrants à l’aide de l’interrogation
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] permet aux programmes clients recevoir des messages à partir d’Oracle E-Business Suite pour signaler les modifications apportées aux données dans Oracle E-Business Suite. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la réception de messages « basées sur l’interrogation » dans laquelle l’adaptateur exécute une instruction SQL spécifiée, procédure stockée, fonction ou une procédure dans un package, récupère les données et fournit le résultat au client à intervalles réguliers de heure.  
  
> [!NOTE]
>  Vous pouvez également définir le contexte des applications pour l’opération d’interrogation dans [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Il est obligatoire de définir le contexte des applications pour l’opération d’interrogation si l’opération est effectuée sur une table d’interface ou une vue de l’interface. Pour plus d’informations sur le contexte des applications et comment le configurer, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
 Une opération d’interrogation standard à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] implique les opérations suivantes :  
  
1.  Les clients de l’adaptateur doivent spécifier `Polling` en tant que l’opération entrante dans le **InboundOperationType** propriété de liaison. La valeur par défaut pour cette propriété de liaison est **d’interrogation**.  
  
2.  Les clients de l’adaptateur doivent spécifier une instruction SELECT pour le **PolledDataAvailableStatement** propriété pour déterminer si donnée n’est disponible pour l’interrogation de liaison. Si la première colonne de la première ligne du premier jeu de résultats retourné lors de l’exécution de cette instruction contient une valeur entière positive, date est disponible pour l’interrogation.  
  
3.  Les clients de l’adaptateur doivent spécifier un intervalle d’interrogation pour le **PollingInterval** liaison de propriété pour définir l’intervalle en secondes, à laquelle l’instruction spécifiée dans le **PolledDataAvailableStatement** propriété de liaison est exécutée. À la fin de chaque intervalle d’interrogation, l’instruction disponibles des données interrogées est exécutée et le jeu de résultats est retourné.  
  
4.  Les clients de l’adaptateur doivent spécifier une instruction SELECT ou une procédure stockée pour le **PollingInput** propriété de liaison. Si vous souhaitez interroger une table ou une vue, vous devez spécifier une instruction SELECT pour cette propriété de liaison. Si vous souhaitez interroger à l’aide d’une procédure stockée, vous devez spécifier le message de requête entière pour cette propriété de liaison.  
  
     L’instruction dans le **PollingInput** propriété de liaison est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison à l’étape 2.  
  
5.  Les clients de l’adaptateur doivent spécifier une action pour l’opération d’interrogation dans le **PollingAction** propriété de liaison. L’action de l’interrogation d’une opération spécifique est déterminée à partir des métadonnées générées pour l’opération en utilisant la macro complémentaire Consume Adapter Service.  
  
6.  Les clients de carte peuvent utiliser le **PollWhileDataFound** liaison de propriété pour ignorer l’intervalle d’interrogation et l’interrogation de façon permanente des données et celui où elle est disponible.  
  
    > [!IMPORTANT]
    >  Si vous définissez la valeur de la **PollWhileDataFound** True à la propriété de liaison, les clients de la carte en continu interrogent des données à partir d’Oracle et dans le processus d’ouvrir et fermer les connexions à la base de données Oracle dans une boucle. Comme la vitesse à laquelle les connexions sont ouvertes par ODP.NET est supérieure aux connexions en cours de fermeture, les connexions s’épuiser après un certain temps, et une exception est levée. Pour contourner ce problème, assurez-vous que la valeur de la **UseOracleConnectionPool** est définie sur True, et une valeur appropriée est mentionnée dans le **IncrPoolSize** liaison de propriété pour contrôler le nombre de connexions qui peut être ouverte par les clients de la carte.  
  
7.  Les clients de l’adaptateur peuvent spécifier une instruction de sondage consécutives, un bloc d’Oracle PL/SQL, pour le **PostPollStatement** propriété de liaison. L’instruction spécifiée dans cette propriété de liaison est exécutée après l’instruction spécifiée dans le **PollingInput** propriété de liaison est exécutée.  
  
    > [!NOTE]
    >  L’adaptateur exécute l’instruction spécifiée dans le **PollingInput** et **PostPollStatement** propriétés de liaison dans une transaction. Pour plus d’informations sur les transactions dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [en quoi les Transactions de gérer l’adaptateur ?](https://msdn.microsoft.com/library/dd788428.aspx).  
  
 L’adaptateur supprime toutes les réponses d’interrogation vide provenant d’Oracle E-Business Suite.  
  
 L’illustration ci-dessous fournit des informations sur le flux de travail d’interrogation dans [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Deux scénarios pour le workflow d’interrogation sont notamment :  
  
1.  Lorsque la valeur de la **PollWhileDataFound** a la valeur « False » (valeur par défaut).  
  
2.  Lorsque la valeur de la **PollWhileDataFound** a la valeur « True ».  
  
 ![Scénario d’interrogation &#40; PollWhileDataFound &#61; False &#41; ] (../../adapters-and-accelerators/adapter-oracle-ebs/media/e5f00f4c-cc76-4e8b-9991-b4471f9d4865.gif "e5f00f4c-cc76-4e8b-9991-b4471f9d4865") ![d’interrogation scénario &#40; PollWhileDataFound &#61; La valeur true &#41; ] (../../adapters-and-accelerators/adapter-oracle-ebs/media/ebecf64c-a770-4525-9c75-62fdb71e1fb1.gif "ebecf64c-a770-4525-9c75-62fdb71e1fb1")  
  
## <a name="differences-between-polling-and-notification"></a>Différences entre l’interrogation et la Notification  
 Bien que l’interrogation et la notification sont les deux opérations entrantes et informent les clients de l’adaptateur sur les modifications de données dans la base de données Oracle, le tableau suivant répertorie quelques différences entre les deux. Les différences suivantes vous aideront à choisir une opération selon vos besoins :  
  
|Interrogation|Notification|  
|-------------|------------------|  
|L’interrogation est prise en charge pour toutes les versions de base de données Oracle sont pris en charge par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].|Notification est uniquement pris en charge pour les versions de base de données Oracle 10.2 et versions ultérieures.|  
|Vous pouvez configurer l’intervalle d’interrogation pour vérifier les données disponibles pour l’interrogation à intervalles réguliers ou instantanément comme et lorsque les données sont disponibles. **Conseil :** interrogation peut vous fournir un meilleur débit dans les scénarios où les modifications de données sont produisent en permanence, et vous ne souhaitez pas être averti de chaque modification en tant qu’et lorsque cela se produit. Au lieu de cela, vous spécifiez un intervalle d’interrogation après laquelle vous souhaitez être averti de toutes les modifications qui se sont produites depuis la dernière notification de modification.|La notification de modification de données est toujours instantanée.|  
|L’interrogation est lancée par l’adaptateur. L’adaptateur exécute une instruction SQL pour confirmer que les données sont disponibles pour l’interrogation et initialise l’interrogation par l’exécution de l’instruction d’interrogation des données seront disponibles pour l’interrogation.|Notification est initiée par la base de données Oracle. L’instruction de notification émise par l’adaptateur simplement fait en sorte que la base de données pour lancer la notification au cas où une modification du jeu de résultats de l’instruction. La notification est une fonctionnalité de la base de données Oracle.|  
|Vous pouvez utiliser l’instruction d’interrogation pour lire ou mettre à jour des données dans la base de données Oracle.|Vous pouvez utiliser l’instruction de notification à lire uniquement les données dans une base de données Oracle.|  
|L’interrogation vous informe sur les données réelles qui ont été modifiées.|Notification informe uniquement sur le type de données, telles que Insert, Update et Delete.|  
  
 Pour plus d’informations sur :  
  
-   Les propriétés de liaison relatives à l’interrogation, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
-   Réception de messages en fonction de l’interrogation à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [interrogation Oracle E-Business Suite à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)