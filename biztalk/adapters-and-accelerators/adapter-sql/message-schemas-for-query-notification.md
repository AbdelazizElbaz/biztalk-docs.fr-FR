---
title: "Schémas de message pour la Notification de requête à l’aide de l’adaptateur SQL dans BizTalk | Documents Microsoft"
description: "Utilisez l’adaptateur SQL pour recevoir des notifications de requête à partir d’une base de données SQL Server dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5183655-64d4-4767-a923-0a575e3708cd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c78c817470bd8acd41f44204653c41e9012d154
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-query-notification"></a><span data-ttu-id="5bb6a-103">Schémas de message de notification de requête</span><span class="sxs-lookup"><span data-stu-id="5bb6a-103">Message Schemas for Query Notification</span></span>
<span data-ttu-id="5bb6a-104">Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] met en évidence l’opération de Notification pour recevoir des notifications de requête à partir de la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-104">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces the Notification operation to receive query notifications from the SQL Server database.</span></span>  
  
 <span data-ttu-id="5bb6a-105">Vous configurez l’opération de Notification en définissant des propriétés de liaison dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5bb6a-105">You configure the Notification operation by setting binding properties in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="5bb6a-106">Pour plus d’informations sur les propriétés liées à la Notification de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5bb6a-106">For more information about the Notification-related binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="5bb6a-107">Vous définissez la **NotificationStatement** liaison de propriété pour spécifier une instruction SQL (SELECT ou EXEC \<procédure stockée >) pour la notification de requête.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-107">You set the **NotificationStatement** binding property to specify a SQL statement (SELECT or EXEC \<stored procedure>) for the query notification.</span></span> <span data-ttu-id="5bb6a-108">Le jeu de résultats de cette requête est retourné en tant que données fortement typées à votre code dans l’opération de Notification.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-108">The result set of this query is returned as strongly-typed data to your code in the Notification operation.</span></span>  
  
## <a name="message-structure-for-the-notification-operation"></a><span data-ttu-id="5bb6a-109">Structure de message pour l’opération de Notification</span><span class="sxs-lookup"><span data-stu-id="5bb6a-109">Message Structure for the Notification operation</span></span>  
 <span data-ttu-id="5bb6a-110">Le tableau suivant montre la structure de message XML pour l’opération de Notification.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-110">The following table shows the XML message structure for the Notification operation.</span></span>  

<span data-ttu-id="5bb6a-111">**Opération**:`Notification`</span><span class="sxs-lookup"><span data-stu-id="5bb6a-111">**Operation**: `Notification`</span></span>

<span data-ttu-id="5bb6a-112">**Message XML**:</span><span class="sxs-lookup"><span data-stu-id="5bb6a-112">**XML message**:</span></span>  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification">
    <Info>Value</Info>
    <Source>Value</Source>
    <Type>Value</Type>
 </Notification>
```

<span data-ttu-id="5bb6a-113">**Description**: c’est le message entrant envoyé par le serveur SQL Server pour les clients de la carte.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-113">**Description**: This is the inbound message that is sent by the SQL Server to the adapter clients.</span></span> <span data-ttu-id="5bb6a-114">Dans le message :</span><span class="sxs-lookup"><span data-stu-id="5bb6a-114">In the message:</span></span>

- <span data-ttu-id="5bb6a-115">Le `<Info>` balise indique la raison de la notification.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-115">The `<Info>` tag indicates the reason for the notification.</span></span> <span data-ttu-id="5bb6a-116">Par exemple, une valeur de « insert » dans cette balise indique que les données a été insérées dans une ou plusieurs des tables référencées dans l’instruction de notification.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-116">For example, an “insert” value in this tag indicates that data has been inserted in one or more of the tables referenced in the notification statement.</span></span>
- <span data-ttu-id="5bb6a-117">Le `<Source>` balise indique la source de la notification.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-117">The `<Source>` tag indicates the source for the notification.</span></span> <span data-ttu-id="5bb6a-118">Par exemple, une valeur de « données » dans cette balise indique une modification de données dans un objet référencé.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-118">For example, a “data” value in this tag indicates a change in the data in a referenced object.</span></span> <span data-ttu-id="5bb6a-119">De même, une valeur de « objet » dans cette balise indique une modification dans un objet référencé.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-119">Similarly, an “object” value in this tag indicates a change in a referenced object.</span></span>
- <span data-ttu-id="5bb6a-120">Le `<Type>` étiquette indique le type de modification des données.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-120">The `<Type>` tag indicates the type of data change.</span></span> <span data-ttu-id="5bb6a-121">Les messages de notification de requête sont de deux types : modifier et de s’abonner.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-121">Query notification messages are of two types: change and subscribe.</span></span> <span data-ttu-id="5bb6a-122">Un « modifier » la valeur dans la `<Type>` balise indique que les résultats de la requête ont changé, tandis qu’une valeur « s’abonner » dans la `<Type>` balise indique qu’une demande d’abonnement a échoué.</span><span class="sxs-lookup"><span data-stu-id="5bb6a-122">A “change” value in the `<Type>` tag indicates that the results of the query have changed, whereas a “subscribe” value in the `<Type>` tag indicates that a subscription request failed.</span></span>

  
## <a name="message-action-for-the-notification-operation"></a><span data-ttu-id="5bb6a-123">Action de message pour l’opération de Notification</span><span class="sxs-lookup"><span data-stu-id="5bb6a-123">Message Action for the Notification Operation</span></span>  
 <span data-ttu-id="5bb6a-124">L’action du message pour l’opération de notification est « Notification ».</span><span class="sxs-lookup"><span data-stu-id="5bb6a-124">The message action for the notification operation is “Notification.”</span></span>  
  