---
title: "Schémas de message pour l’OP2 Composite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0164ea07-a373-430b-b569-3e29df1d081b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1014ea162e9fab33aa6630d0cdb4eb774f91031
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-composite-operation"></a><span data-ttu-id="b6420-102">Schémas de message pour l’opération Composite</span><span class="sxs-lookup"><span data-stu-id="b6420-102">Message Schemas for the Composite Operation</span></span>
<span data-ttu-id="b6420-103">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] vous permet d’exécuter des opérations composites sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="b6420-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] enables you to execute composite operations on the Oracle database.</span></span> <span data-ttu-id="b6420-104">Une opération composite peut contenir plusieurs opérations et dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="b6420-104">A composite operation can contain multiple operations, and in any order.</span></span> <span data-ttu-id="b6420-105">Pour plus d’informations sur les opérations peuvent être incluses dans une opération composite, consultez [exécuter des opérations composites dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="b6420-105">For information about which operations can be included in a composite operation, see [Run Composite Operations in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md).</span></span>  
  
 <span data-ttu-id="b6420-106">Pour plus d’informations sur la façon d’effectuer des opérations composites à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [exécuter des opérations composites sur la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="b6420-106">For information about how to perform composite operations using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Run Composite Operations on Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span></span>  
  
## <a name="message-structure-for-the-composite-operation"></a><span data-ttu-id="b6420-107">Structure de message pour l’opération Composite</span><span class="sxs-lookup"><span data-stu-id="b6420-107">Message Structure for the Composite Operation</span></span>  
 <span data-ttu-id="b6420-108">Parce qu’une opération composite contient plusieurs opérations individuelles ; la structure d’une opération composite contient des structures de message des opérations individuelles.</span><span class="sxs-lookup"><span data-stu-id="b6420-108">Because a composite operation contains multiple individual operations; the message structure of a composite operation contains message structures of the individual operations.</span></span> <span data-ttu-id="b6420-109">Le message d’opération composite suit un modèle d’échange de message demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="b6420-109">The composite operation message follows a request-response message exchange pattern.</span></span>  
  
 <span data-ttu-id="b6420-110">Le tableau suivant montre la structure des messages de demande et de réponse d’une opération composite qui contient une opération d’insertion, une procédure stockée empaquetée qui n’accepte pas les paramètres d’entrée et une opération de suppression.</span><span class="sxs-lookup"><span data-stu-id="b6420-110">The following table shows the structure of the request and response messages of a composite operation that contains an Insert operation, a packaged stored procedure that does not take any input parameters, and a Delete operation.</span></span>  
  
|<span data-ttu-id="b6420-111">Opération</span><span class="sxs-lookup"><span data-stu-id="b6420-111">Operation</span></span>|<span data-ttu-id="b6420-112">Message XML</span><span class="sxs-lookup"><span data-stu-id="b6420-112">XML Message</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6420-113">Demande d’opération composite</span><span class="sxs-lookup"><span data-stu-id="b6420-113">Composite Operation Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <RECORDSET>       <[TABLE_NAME]RECORDINSERT>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>         …       </[TABLE_NAME]RECORDINSERT>    </RECORDSET>   </Insert>   <[SP_NAME] xmlns="[VERSION]/[SCHEMA]/Procedure" />   <Delete xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <FILTER>[WHERE_clause]</FILTER>   </Delete> </Request>`|  
|<span data-ttu-id="b6420-114">Réponse de l’opération composite</span><span class="sxs-lookup"><span data-stu-id="b6420-114">Composite Operation Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <InsertResult>[value]</InsertResult>    </InsertResponse>   <[SP_NAME]Response xmlns="[VERSION]/[SCHEMA]/Procedure">     <[PRM1_NAME]>value1<[PRM1_NAME]>     <[PRM2_NAME]>value2</[PRM2_NAME]>     …   </[SP_NAME]Response>    <DeleteResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 <span data-ttu-id="b6420-115">[VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.OracleDB/2007/03</span><span class="sxs-lookup"><span data-stu-id="b6420-115">[VERSION] = The message version string; for example, http://Microsoft.LobServices.OracleDB/2007/03</span></span>  
  
 <span data-ttu-id="b6420-116">[PROJECT_NAME] = nom du projet BizTalk qui contient le schéma de l’opération composite.</span><span class="sxs-lookup"><span data-stu-id="b6420-116">[PROJECT_NAME] = Name of the BizTalk project that contains the composite operation schema.</span></span>  
  
 <span data-ttu-id="b6420-117">[COMPOSITE_SCHEMA_NAME] = nom du schéma d’opération composite donné par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b6420-117">[COMPOSITE_SCHEMA_NAME] = Name of the composite operation schema given by the user.</span></span>  
  
 <span data-ttu-id="b6420-118">[Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.</span><span class="sxs-lookup"><span data-stu-id="b6420-118">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="b6420-119">[Nom_table] = nom de la table ; par exemple, les employés.</span><span class="sxs-lookup"><span data-stu-id="b6420-119">[TABLE_NAME] = Name of the table; for example, EMPLOYEE.</span></span>  
  
 <span data-ttu-id="b6420-120">[FIELD1_NAME] = nom du champ de Table ; par exemple, un nom.</span><span class="sxs-lookup"><span data-stu-id="b6420-120">[FIELD1_NAME] = Table field name; for example, NAME.</span></span>  
  
 <span data-ttu-id="b6420-121">[SP_NAME] = la procédure stockée empaquetée à être exécutés ; par exemple, ADD_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="b6420-121">[SP_NAME] = The packaged stored procedure to be executed; for example, ADD_EMP_DETAILS.</span></span>  
  
 <span data-ttu-id="b6420-122">[PRM1_NAME] = le nom du paramètre Oracle dans la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="b6420-122">[PRM1_NAME] = The name of the Oracle parameter in the stored procedure.</span></span>  
  
## <a name="message-action-for-the-composite-operation"></a><span data-ttu-id="b6420-123">Action de message pour l’opération Composite</span><span class="sxs-lookup"><span data-stu-id="b6420-123">Message Action for the Composite Operation</span></span>  
 <span data-ttu-id="b6420-124">L’action du message pour l’opération composite est « http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation ».</span><span class="sxs-lookup"><span data-stu-id="b6420-124">The message action for the composite operation is “http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation.”</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6420-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6420-125">See Also</span></span>  
 [<span data-ttu-id="b6420-126">Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="b6420-126">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)