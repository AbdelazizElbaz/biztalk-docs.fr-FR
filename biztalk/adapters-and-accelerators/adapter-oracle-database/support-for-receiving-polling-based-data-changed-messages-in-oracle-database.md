---
title: "Prise en charge pour la réception des Messages de modification de données reposant sur l’interrogation dans la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- notifications, polling-based
- post-polling
- POLLINGSTMT
- polling interval
- polling
ms.assetid: 9ff29d3f-ebb1-4d82-9106-150f939cbd9e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d8a29901672ba11f3ac48220f7096b2c355fc2e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-receiving-polling-based-data-changed-messages-in-oracle-database"></a>Prise en charge pour la réception des Messages de modification de données reposant sur l’interrogation dans la base de données Oracle
Le[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] permet aux programmes clients recevoir des messages à partir de la base de données Oracle pour l’informer des modifications apportées aux données stockées dans une base de données Oracle. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge la réception de messages « basées sur l’interrogation » dans laquelle l’adaptateur exécute une requête SELECT spécifié, une procédure stockée, fonction, ou de procédure ou dans un package, récupère les données et fournit le résultat au client régulièrement intervalles de temps. Pour activer cette option, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose une opération POLLINGSTMT. En outre, toutes les procédures stockées, fonctions et procédures et fonction dans des packages sont exposées comme opérations entrantes pour l’interrogation.  
  
 L’adaptateur offre deux moyens de l’interrogation de la base de données Oracle :  
  
-   **À l’aide des instructions SELECT**. Vous pouvez spécifier une instruction SELECT simple pour interroger les tables et les vues dans la base de données Oracle. L’adaptateur s’exécute l’instruction SELECT à des intervalles spécifiés et retourne le résultat pour les clients de la carte.  
  
-   **À l’aide de procédures stockées, des fonctions, ou des procédures ou des fonctions dans un package**. Vous pouvez spécifier une procédure stockée, fonction ou procédure ou une fonction dans un package pour interroger la base de données Oracle. L’adaptateur s’exécute le message de demande à des intervalles spécifiés et retourne le résultat pour les clients de la carte.  
  
## <a name="polling-operation-workflow"></a>Workflow d’opération d’interrogation  
 Une opération d’interrogation standard à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] implique les opérations suivantes :  
  
1.  Les clients de l’adaptateur doivent spécifier **d’interrogation** en tant que l’opération entrante dans le **InboundOperationType** propriété de liaison. La valeur par défaut pour cette propriété de liaison est **d’interrogation**.  
  
2.  Les clients de l’adaptateur doivent spécifier une instruction SELECT pour le **PolledDataAvailableStatement** propriété pour déterminer si donnée n’est disponible pour l’interrogation de liaison. L’exécution de cette instruction, si la première colonne de la première ligne du jeu de résultats retourné contient une valeur entière positive, il est date disponible pour l’interrogation. Par défaut, la valeur de cette propriété de liaison est définie `Select 1 FROM DUAL`, ce qui implique que l’adaptateur doit continuer d’interrogation même si la table interrogée a des données ou non.  
  
3.  Les clients de l’adaptateur doivent spécifier un intervalle d’interrogation pour le **PollingInterval** liaison de propriété pour définir l’intervalle en secondes, à laquelle l’instruction spécifiée dans le **PolledDataAvailableStatement** propriété de liaison est exécutée. À la fin de chaque intervalle d’interrogation, l’instruction disponibles des données interrogées est exécutée et le jeu de résultats est retourné.  
  
4.  Les clients de l’adaptateur doivent spécifier une instruction SELECT ou une procédure stockée pour le **PollingStatement** propriété de liaison.  
  
    -   Si vous souhaitez interroger une table ou une vue, vous devez spécifier une requête SELECT dans cette propriété de liaison.  
  
    -   Si vous souhaitez interroger à l’aide d’une procédure stockée, fonction ou procédure ou une fonction dans un package, vous devez spécifier le message de demande pour l’opération respective dans cette propriété de liaison.  
  
     L’instruction dans le **PollingStatement** propriété de liaison est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison à l’étape 1.  
  
5.  Les clients de l’adaptateur doivent spécifier une action pour l’opération d’interrogation dans le **PollingAction** propriété de liaison. L’action de l’interrogation d’une opération spécifique est déterminée à partir des métadonnées générées pour l’opération en utilisant la macro complémentaire Consume Adapter Service.  
  
    > [!NOTE]
    >  Si vous demandent une table ou vue à l’aide d’une instruction SELECT dans la **PollingStatement** propriété de liaison, vous ne souhaitez pas spécifier de valeur pour le **PollingAction** propriété de liaison. La valeur par défaut Null, la valeur est passée dans ce cas.  
  
6.  Les clients de carte peuvent utiliser le **PollWhileDataFound** liaison de propriété pour ignorer l’intervalle d’interrogation et l’interrogation de façon permanente des données et celui où elle est disponible.  
  
    > [!IMPORTANT]
    >  Si vous définissez la valeur de la **PollWhileDataFound** True à la propriété de liaison, les clients de la carte en continu interrogent des données à partir d’Oracle et dans le processus d’ouvrir et fermer les connexions à la base de données Oracle dans une boucle. Comme la vitesse à laquelle les connexions sont ouvertes par ODP.NET est supérieure aux connexions en cours de fermeture, les connexions s’épuiser après un certain temps, et une exception est levée. Pour contourner ce problème, assurez-vous que la valeur de la **UseOracleConnectionPool** est définie sur True, et une valeur appropriée est mentionnée dans le **IncrPoolSize** liaison de propriété pour contrôler le nombre de connexions qui peut être ouverte par les clients de la carte.  
  
7.  Les clients de l’adaptateur peuvent spécifier une instruction de sondage consécutives, un bloc d’Oracle PL/SQL, pour le **PostPollStatement** propriété de liaison. L’instruction spécifiée dans cette propriété de liaison est exécutée après l’instruction spécifiée dans le **PollingStatement** propriété de liaison est exécutée.  
  
 L’adaptateur encapsule l’instruction d’interrogation et l’instruction après interrogation dans une transaction et la valeur de délai d’attente de transaction est définie comme la valeur spécifiée pour le **PollingInterval** propriété de liaison. Par conséquent, il est essentiel pour spécifier une valeur de délai d’attente qui est supérieure ou égale à la durée nécessaire pour traiter le message entrant et envoyer une réponse. Si le temps pris par le programme client de consommer le message ou d’exécuter la requête d’interrogation après est supérieure à la valeur de délai d’attente, la transaction est restaurée. Si la durée est inférieure à la valeur de délai d’attente, l’adaptateur valide la transaction et « mise en veille » du temps restant dans l’interrogation avant d’effectuer l’interrogation suivante.  
  
 L’adaptateur supprime toutes les réponses d’interrogation vide en provenance de la base de données Oracle.  
  
## <a name="differences-between-polling-and-notification"></a>Différences entre l’interrogation et la Notification  
 Bien que l’interrogation et la notification sont les deux opérations entrantes et informent les clients de l’adaptateur sur les modifications de données dans la base de données Oracle, le tableau suivant illustre certaines différences entre les deux. Les différences suivantes vous aideront à choisir une opération selon vos besoins :  
  
|Interrogation|Notification|  
|-------------|------------------|  
|L’interrogation est prise en charge pour toutes les versions de base de données Oracle sont pris en charge par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|La notification est pris en charge uniquement pour les versions de base de données Oracle 10.2 et versions ultérieures.|  
|Vous pouvez configurer l’intervalle d’interrogation pour vérifier les données disponibles pour l’interrogation à intervalles réguliers ou instantanément comme et lorsque les données sont disponibles. **Conseil :** interrogation peut vous fournir un meilleur débit dans les scénarios où les modifications de données sont produisent en permanence, et vous ne souhaitez pas être averti de chaque modification en tant qu’et lorsque cela se produit. Au lieu de cela, vous spécifiez un intervalle d’interrogation après laquelle vous souhaitez être averti de toutes les modifications qui se sont produites depuis la dernière notification de modification.|La notification de modification de données est toujours instantanée.|  
|L’interrogation est lancée par l’adaptateur. L’adaptateur exécute une instruction SQL pour confirmer que les données sont disponibles pour l’interrogation et initialise l’interrogation par l’exécution de l’instruction d’interrogation des données seront disponibles pour l’interrogation.|Notification est initiée par la base de données Oracle. L’instruction de notification émise par l’adaptateur simplement fait en sorte que la base de données pour lancer la notification au cas où une modification du jeu de résultats de l’instruction. La notification est une fonctionnalité de la base de données Oracle.|  
|Vous pouvez utiliser l’instruction d’interrogation pour lire ou mettre à jour des données dans la base de données Oracle.|Vous pouvez utiliser l’instruction de notification à lire uniquement les données dans une base de données Oracle.|  
|L’interrogation vous informe sur les données réelles qui ont été modifiées.|Notification informe uniquement sur le type de données, telles que Insert, Update et Delete.|  
  
 Pour plus d’informations sur :  
  
-   Comment l’adaptateur prend en charge la réception de messages basés sur l’interrogation à partir de la base de données Oracle, consultez [recevoir des messages d’interrogation de données modifiées](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).  
  
-   Réception de messages de reposant sur l’interrogation de l’utilisation de base de données Oracle [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [appeler les fonctions et les procédures de base de données Oracle à l’aide de Biztalk Server](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md).  
  
-   Réception d’interrogation des messages à partir de la base de données Oracle à l’aide du modèle de service WCF, consultez [Messages basés sur la réception d’interrogation de données modifiées à partir de SQL Server à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md).  
  
-   Réception d’interrogation des messages à partir de la base de données Oracle à l’aide du modèle de canal WCF, consultez [Messages basés sur la réception d’interrogation de données modifiées à partir de SQL Server à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md).  
  
-   Structure et les actions SOAP pour effectuer une requête d’interrogation des messages, consultez [des schémas de Message pour les opérations d’interrogation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)