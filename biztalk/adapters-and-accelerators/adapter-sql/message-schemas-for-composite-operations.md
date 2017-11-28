---
title: "Schémas de message pour des opérations composites | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d80c023b-1912-43d4-be29-eb9e1b323593
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b89c354baea2ddb46abf549752dc09699b9c9695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-composite-operations"></a><span data-ttu-id="03a48-102">Schémas de message pour des opérations composites</span><span class="sxs-lookup"><span data-stu-id="03a48-102">Message Schemas for Composite Operations</span></span>
<span data-ttu-id="03a48-103">Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] vous permet d’exécuter des opérations composites sur la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="03a48-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] enables you to execute composite operations on the SQL Server database.</span></span> <span data-ttu-id="03a48-104">Une opération composite peut contenir plusieurs opérations, y compris l’insertion, mise à jour et supprimer des opérations sur les tables et les vues et les opérations sur les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="03a48-104">A composite operation can contain multiple operations including the Insert, Update, and Delete operations on the tables and views, and operations on stored procedures.</span></span> <span data-ttu-id="03a48-105">Une opération composite peut inclure ces opérations dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="03a48-105">A composite operation can include these operations in any order.</span></span>  
  
 <span data-ttu-id="03a48-106">Pour plus d’informations sur :</span><span class="sxs-lookup"><span data-stu-id="03a48-106">For more information about:</span></span>  
  
-   <span data-ttu-id="03a48-107">Des opérations composites, consultez [prise en charge des opérations composites](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md).</span><span class="sxs-lookup"><span data-stu-id="03a48-107">Composite operations, see [Support for Composite Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md).</span></span>  
  
-   <span data-ttu-id="03a48-108">Comment effectuer des opérations composites à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [exécuter des opérations composites dans SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="03a48-108">How to perform composite operations using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Run composite operations in SQL Server  using the SQL adapter](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
## <a name="message-structure-for-the-composite-operation"></a><span data-ttu-id="03a48-109">Structure de message pour l’opération Composite</span><span class="sxs-lookup"><span data-stu-id="03a48-109">Message Structure for the Composite Operation</span></span>  
 <span data-ttu-id="03a48-110">Dans la mesure où une opération composite contient plusieurs opérations individuelles ; la structure d’une opération composite contient des structures de message des opérations individuelles.</span><span class="sxs-lookup"><span data-stu-id="03a48-110">Since a composite operation contains multiple individual operations; the message structure of a composite operation contains message structures of the individual operations.</span></span> <span data-ttu-id="03a48-111">Une opération composite contient des opérations sur les tables, vues et procédures stockées, le message d’opération composite suit un modèle d’échange de message demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="03a48-111">As a composite operation contains operations on tables, views, and stored procedures, the composite operation message follows a request-response message exchange pattern.</span></span>  
  
 <span data-ttu-id="03a48-112">Le tableau suivant montre la structure des messages de demande et de réponse d’une opération composite qui contient une opération d’insertion, une procédure stockée qui n’accepte pas les paramètres d’entrée et une opération de suppression.</span><span class="sxs-lookup"><span data-stu-id="03a48-112">The following table shows the structure of the request and response messages of a composite operation that contains an Insert operation, a stored procedure that does not take any input parameters, and a Delete operation.</span></span>  
  
|<span data-ttu-id="03a48-113">Opération</span><span class="sxs-lookup"><span data-stu-id="03a48-113">Operation</span></span>|<span data-ttu-id="03a48-114">Message XML</span><span class="sxs-lookup"><span data-stu-id="03a48-114">XML Message</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03a48-115">Demande d’opération composite</span><span class="sxs-lookup"><span data-stu-id="03a48-115">Composite Operation Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <Rows>       <[TABLE_NAME]>         <[FIELD1_NAME]>[Value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[Value1]</[FIELD2_NAME]>         …       </[TABLE_NAME]>     </Rows>   </Insert>   <[SP_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]" />   <Delete xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <Rows>       <[TABLE_NAME]>         <[FIELD1_NAME]>[Value1]</[FIELD1_NAME]>       </[TABLE_NAME]>     </Rows>   </Delete> </Request>`|  
|<span data-ttu-id="03a48-116">Réponse de l’opération composite</span><span class="sxs-lookup"><span data-stu-id="03a48-116">Composite Operation Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <InsertResult>       <long>[value]</long>      </InsertResult>   </InsertResponse>   <[SP_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]">     <[SP_NAME]Result>       <DataSet>         <any>[Value]</any>          <any>[Value]</any>          …       </DataSet>     </[SP_NAME]Result>     <ReturnValue>[value]</ReturnValue>    </[SP_NAME]Response>   <DeleteResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 <span data-ttu-id="03a48-117">[PROJECT_NAME] = nom du projet BizTalk qui contient le schéma de l’opération composite.</span><span class="sxs-lookup"><span data-stu-id="03a48-117">[PROJECT_NAME] = Name of the BizTalk project that contains the composite operation schema.</span></span>  
  
 <span data-ttu-id="03a48-118">[COMPOSITE_SCHEMA_NAME] = nom du schéma d’opération composite donné par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="03a48-118">[COMPOSITE_SCHEMA_NAME] = Name of the composite operation schema given by the user.</span></span>  
  
 <span data-ttu-id="03a48-119">[Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.</span><span class="sxs-lookup"><span data-stu-id="03a48-119">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
 <span data-ttu-id="03a48-120">[Nom_table] = nom de la table ; par exemple, les employés.</span><span class="sxs-lookup"><span data-stu-id="03a48-120">[TABLE_NAME] = Name of the table; for example, Employee.</span></span>  
  
 <span data-ttu-id="03a48-121">[FIELD1_NAME] = nom du champ de Table ; par exemple, un nom.</span><span class="sxs-lookup"><span data-stu-id="03a48-121">[FIELD1_NAME] = Table field name; for example, NAME.</span></span>  
  
 <span data-ttu-id="03a48-122">[SP_NAME] = la procédure stockée à exécuter ; par exemple, ADD_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="03a48-122">[SP_NAME] = The stored procedure to be executed; for example, ADD_EMP_DETAILS.</span></span>  
  
## <a name="message-action-for-the-composite-operation"></a><span data-ttu-id="03a48-123">Action de message pour l’opération Composite</span><span class="sxs-lookup"><span data-stu-id="03a48-123">Message Action for the Composite Operation</span></span>  
 <span data-ttu-id="03a48-124">L’action du message pour l’opération composite est « CompositeOperation ».</span><span class="sxs-lookup"><span data-stu-id="03a48-124">The message action for the composite operation is “CompositeOperation.”</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a48-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03a48-125">See Also</span></span>  
 [<span data-ttu-id="03a48-126">Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="03a48-126">Messages and Message Schemas for BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)