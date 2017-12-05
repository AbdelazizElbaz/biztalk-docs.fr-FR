---
title: "Schémas de message pour l’interrogation et les opérations de TypedPolling de l’adaptateur SQL dans BizTalk | Documents Microsoft"
description: "L’interrogation et TypedPolling message structure utilisée par l’adaptateur SQL dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e900307-2c9c-493b-81c9-67af3e143eeb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cd6a281bfca73e74f23ce25bb9fa08761a07789
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-schemas-for-the-polling-and-typedpolling-operations"></a><span data-ttu-id="6650f-103">Schémas de message pour l’interrogation et les opérations de TypedPolling</span><span class="sxs-lookup"><span data-stu-id="6650f-103">Message Schemas for the Polling and TypedPolling Operations</span></span>
<span data-ttu-id="6650f-104">Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces d’interrogation et de TypedPolling entrant operations pour retourner le jeu de résultats de la requête d’interrogation à un client de carte.</span><span class="sxs-lookup"><span data-stu-id="6650f-104">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces the Polling and TypedPolling inbound operations to return the result set of the polling query to an adapter client.</span></span>  
  
 <span data-ttu-id="6650f-105">Vous configurez les opérations d’interrogation et TypedPolling en définissant les propriétés de liaison dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6650f-105">You configure the Polling and TypedPolling operations by setting binding properties in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="6650f-106">Pour plus d’informations sur ces propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="6650f-106">For more information about these binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="6650f-107">Vous définissez la **PollingStatement** liaison de propriété pour spécifier une instruction SQL (SELECT ou EXEC \<procédure stockée\>) pour la requête d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="6650f-107">You set the **PollingStatement** binding property to specify a SQL statement (SELECT or EXEC \<stored procedure\>) for the polling query.</span></span> <span data-ttu-id="6650f-108">Le jeu de résultats de cette requête est retourné sous forme de données à votre code dans l’opération d’interrogation et en tant que données fortement typées dans l’opération TypedPolling.</span><span class="sxs-lookup"><span data-stu-id="6650f-108">The result set of this query is returned as data to your code in the Polling operation, and as strongly-typed data in the TypedPolling operation.</span></span> <span data-ttu-id="6650f-109">La structure du jeu de résultats est déterminée par les métadonnées que l’adaptateur met en évidence pour la requête spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6650f-109">The structure of the result set is determined by the metadata that the adapter surfaces for the specified query.</span></span>  
  
## <a name="polling-message-structure"></a><span data-ttu-id="6650f-110">Structure des messages d’interrogation</span><span class="sxs-lookup"><span data-stu-id="6650f-110">Polling message structure</span></span> 
  
<span data-ttu-id="6650f-111">**Opération**:`Polling`</span><span class="sxs-lookup"><span data-stu-id="6650f-111">**Operation**: `Polling`</span></span>

<span data-ttu-id="6650f-112">**Message XML**:</span><span class="sxs-lookup"><span data-stu-id="6650f-112">**XML Message**:</span></span>  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <Polling xmlns="http://schemas.microsoft.com/Sql/2008/05/Polling">
    <PolledData>
      <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">
        <any>[Value]</any>
        <any>[Value]</any>
        …
        </DataSet>
    </PolledData>
 </Polling>
```

<span data-ttu-id="6650f-113">**Description**: le message entrant envoyé par le serveur SQL Server pour les clients de la carte.</span><span class="sxs-lookup"><span data-stu-id="6650f-113">**Description**: The inbound message that is sent by the SQL Server to the adapter clients.</span></span>  


## <a name="typedpolling-message-structure"></a><span data-ttu-id="6650f-114">Structure de message TypedPolling</span><span class="sxs-lookup"><span data-stu-id="6650f-114">TypedPolling message structure</span></span> 

<span data-ttu-id="6650f-115">**Opération**:`TypedPolling`</span><span class="sxs-lookup"><span data-stu-id="6650f-115">**Operation**: `TypedPolling`</span></span>

<span data-ttu-id="6650f-116">**Message XML**:</span><span class="sxs-lookup"><span data-stu-id="6650f-116">**XML Message**:</span></span>  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <TypedPollingResultSet xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedPolling">
    <COLUMN1>[Value]</Column1>
    <COLUMN2>[Value]</Column2>
    …
  </TypedPollingResultSet>
```

<span data-ttu-id="6650f-117">**Description**: le message entrant fortement typée qui est envoyé par le serveur SQL Server pour les clients de la carte.</span><span class="sxs-lookup"><span data-stu-id="6650f-117">**Description**: The strongly-typed inbound message that is sent by the SQL Server to the adapter clients.</span></span>
  
## <a name="message-action-for-the-polling-and-typedpolling-operations"></a><span data-ttu-id="6650f-118">Action du message pour l’interrogation et les opérations de TypedPolling</span><span class="sxs-lookup"><span data-stu-id="6650f-118">Message Action for the Polling and TypedPolling Operations</span></span>  
 <span data-ttu-id="6650f-119">L’action du message pour le :</span><span class="sxs-lookup"><span data-stu-id="6650f-119">The message action for the:</span></span>  
  
-   <span data-ttu-id="6650f-120">Opération d’interrogation est « interrogation ».</span><span class="sxs-lookup"><span data-stu-id="6650f-120">Polling operation is “Polling.”</span></span>  
  
-   <span data-ttu-id="6650f-121">L’opération TypedPolling est « TypedPolling. »</span><span class="sxs-lookup"><span data-stu-id="6650f-121">TypedPolling operation is “TypedPolling.”</span></span>  
  
