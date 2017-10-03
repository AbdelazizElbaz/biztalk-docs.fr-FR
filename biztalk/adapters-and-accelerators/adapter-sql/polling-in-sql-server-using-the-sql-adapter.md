---
title: "L’interrogation dans SQL Server à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c31b3cda-c05e-46db-827b-6c47a53d1a3a
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d01bc3d004da60b98e0132aa3c8e04442a45426
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="polling-in-sql-server-using-the-sql-adapter"></a>L’interrogation dans SQL Server à l’aide de l’adaptateur SQL
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]permet aux clients d’adaptateur recevoir des messages de modification de données à partir de la base de données SQL Server. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge la réception des messages de « basées sur l’interrogation » dans laquelle l’adaptateur exécute une instruction SQL spécifiée (instruction SELECT ou procédure stockée), récupère ou met à jour les données et fournit le résultat au client de carte à intervalles réguliers de heure.  
  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose les opérations suivantes pour l’interrogation :  
  
-   **L’interrogation**: vous permet de recevoir des messages de modification de données périodiques pour les tables SQL Server ou des vues. Les messages ne sont pas fortement typée.  
  
-   **TypedPolling**: vous permet de recevoir des messages de fortement typée de la base de données SQL Server. Vous devez utiliser cette opération si vous souhaitez mapper les éléments dans le message d’interrogation avec n’importe quel autre schéma.  
  
-   **XmlPolling**. Vous permet d’utiliser les instructions SELECT ou des procédures stockées qui utilisent une clause FOR XML et de retournent des données en tant que messages XML. Cette opération renvoie le message d’interrogation en tant qu’un message XML.  
  
     Pour plus d’informations sur la clause FOR XML, consultez [http://go.microsoft.com/fwlink/?LinkId=131402](http://go.microsoft.com/fwlink/?LinkId=131402).  
  
 Pour plus d’informations sur l’interrogation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [Messages basés sur la réception d’interrogation de données modifiées à partir de SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md).  
  
## <a name="polling"></a>Interrogation  
 Une opération d’interrogation standard à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] implique les opérations suivantes :  
  
1.  Les clients de l’adaptateur doivent spécifier `Polling` en tant que l’opération entrante dans le **InboundOperationType** propriété de liaison. La valeur par défaut pour cette propriété de liaison est `Polling`.  
  
2.  Les clients de l’adaptateur doivent spécifier une instruction SQL pour le **PolledDataAvailableStatement** propriété qui détermine si donnée n’est disponible pour l’interrogation de liaison. La première colonne de la première ligne du premier jeu de résultats retourné sur l’exécution de cette instruction contient une valeur entière. Si aucune donnée n’est disponible pour l’interrogation, la valeur de retour est 0 (zéro). Si les données est disponible, la valeur de retour est supérieure à zéro.  
  
3.  Les clients de l’adaptateur doivent spécifier un intervalle d’interrogation pour le **PollingIntervalInSeconds** liaison de propriété pour définir l’intervalle selon lequel l’instruction dans le **PolledDataAvailableStatement** liaison propriété est exécutée. À la fin de chaque intervalle d’interrogation, l’instruction disponibles des données interrogées est exécutée et le jeu de résultats est retourné.  
  
4.  Les clients de l’adaptateur doivent spécifier une instruction SQL de l’interrogation (instruction SELECT ou procédure stockée) pour le **PollingStatement** propriété de liaison. Si des données sont disponibles pour l’interrogation (déterminé par le **PolledDataAvailableStatement** propriété de liaison), l’adaptateur exécute l’instruction d’interrogation pour obtenir et mettre à jour (le cas échéant) les données dans la base de données SQL Server. Lorsque le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est utilisé avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], la même transaction est également utilisée pour envoyer le message à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
5.  Les clients de carte peuvent utiliser le **PollWhileDataFound** liaison de propriété pour ignorer l’intervalle d’interrogation et l’interrogation de façon permanente des données et celui où elle est disponible.  
  
6.  Les jeux de résultats renvoyés suite à l’exécution de l’instruction d’interrogation sont envoyées au client de carte en tant que le message entrant.  
  
> [!NOTE]
>  Une opération XmlPolling nécessite les mêmes étapes que l’opération d’interrogation.  
  
## <a name="strongly-typed-polling"></a>Interrogation fortement typée  
 Une opération de type interrogation fortement typée à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] implique les opérations suivantes :  
  
1.  Les clients de l’adaptateur doivent spécifier `TypedPolling` en tant que l’opération entrante dans le **InboundOperationType** propriété de liaison. La valeur par défaut pour cette propriété de liaison est `Polling`.  
  
2.  Les clients de l’adaptateur doivent spécifier un ID entrant dans le cadre de l’URI de connexion. L’ID d’entrée peut être n’importe quelle chaîne et est ajouté à l’espace de noms standard de l’opération TypedPolling pour empêcher les collisions d’espace de noms.  
  
3.  Le reste des étapes sont les mêmes que les étapes 2 à 6 répertoriés dans l’opération d’interrogation décrite dans la section précédente.  
  
 Pour obtenir des informations détaillées sur les propriétés de liaison relatives à l’interrogation et l’interrogation fortement typée, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
> [!NOTE]
>  Plusieurs jeux de résultats peut être retourné suite à l’exécution de l’instruction d’interrogation. Si les jeux de résultats ne contiennent pas toutes les lignes, aucun message est envoyé au client de carte.  
  
 L’illustration ci-dessous fournit des informations sur le flux de travail d’interrogation dans [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Deux scénarios pour le workflow d’interrogation sont notamment :  
  
1.  Lorsque la valeur de la **PollWhileDataFound** a la valeur « False » (valeur par défaut).  
  
2.  Lorsque la valeur de la **PollWhileDataFound** a la valeur « True ».  
  
 ![Workflow d’interrogation &#40; PollWhileDataFound &#61; False &#41; ] (../../adapters-and-accelerators/adapter-sql/media/15598c14-3a62-4b8d-90bf-84e004a386db.gif "15598c14-3a62-4b8d-90bf-84e004a386db") ![d’interrogation de flux de travail &#40; PollWhileDataFound &#61; La valeur true &#41; ] (../../adapters-and-accelerators/adapter-sql/media/c20535be-ea45-4456-8b62-4d4585cb1d8c.gif "c20535be-ea45-4456-8b62-4d4585cb1d8c")  
  
## <a name="differences-between-polling-and-query-notification"></a>Différences entre l’interrogation et la Notification de requête  
 Bien que l’interrogation et la requête de notification sont les deux opérations entrantes et informer les clients de l’adaptateur sur les modifications de données dans la base de données SQL Server, le tableau suivant répertorie quelques différences entre les deux. Les différences suivantes vous aideront à choisir une opération selon vos besoins :  
  
|Interrogation|Notification de requête|  
|-------------|------------------------|  
|L’interrogation est lancée par l’adaptateur. L’adaptateur exécute une instruction pour vérifier si les données sont disponibles pour l’interrogation et initialise l’interrogation par l’exécution de l’instruction d’interrogation des données seront disponibles pour l’interrogation.|Notification de requête est lancée par SQL Server. L’instruction de notification émise par l’adaptateur simplement fait en sorte que la base de données pour lancer la notification au cas où une modification du jeu de résultats de l’instruction.|  
|Vous pouvez utiliser l’instruction d’interrogation pour lire ou mettre à jour des données dans une table de base de données SQL Server.|Vous pouvez utiliser l’instruction de notification de requête à lire uniquement les données dans une table de base de données SQL Server.|  
|L’interrogation vous informe sur les données réelles qui ont été modifiées.|Notification de requête indique uniquement sur le type de données, telles que Insert, Update et Delete.|  
|La notification de modification de données dépend de l’intervalle d’interrogation, et les clients de la carte sont informés des changements de données à la fin de chaque intervalle d’interrogation. **Conseil :** interrogation peut vous fournir un meilleur débit dans les scénarios où les modifications de données sont produisent en permanence, et vous ne souhaitez pas être averti de chaque modification en tant qu’et lorsque cela se produit. Au lieu de cela, vous spécifiez un intervalle d’interrogation après laquelle vous souhaitez être averti de toutes les modifications qui se sont produites depuis la dernière notification de modification de données.|La notification de modification de données est instantanée.|  
  
 Pour plus d’informations sur la notification de requête dans [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)], consultez [recevoir des Notifications de requête SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)