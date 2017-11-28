---
title: "Schémas de message pour le Composite Operation1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 768473ef-da8d-4e58-86cb-597c28ded49c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b22861d36693ab3ef487e5e3d0b86544f048e95
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-composite-operation"></a><span data-ttu-id="50ec8-102">Schémas de message pour l’opération Composite</span><span class="sxs-lookup"><span data-stu-id="50ec8-102">Message Schemas for the Composite Operation</span></span>
<span data-ttu-id="50ec8-103">Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] vous permet d’exécuter des opérations composites dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="50ec8-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] enables you to execute composite operations in Oracle E-Business Suite.</span></span> <span data-ttu-id="50ec8-104">Une opération composite peut contenir plusieurs opérations et dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="50ec8-104">A composite operation can contain multiple operations, and in any order.</span></span> <span data-ttu-id="50ec8-105">Pour plus d’informations sur les opérations peuvent être incluses dans une opération composite, consultez [prise en charge des opérations composites](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md).</span><span class="sxs-lookup"><span data-stu-id="50ec8-105">For information about which operations can be included in a composite operation, see [Support for Composite Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md).</span></span>  
  
 <span data-ttu-id="50ec8-106">Pour plus d’informations sur la façon d’effectuer des opérations composites à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [exécuter des opérations composites sur la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="50ec8-106">For information about how to perform composite operations using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Run Composite Operations on Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span></span>  
  
## <a name="message-structure-for-the-composite-operation"></a><span data-ttu-id="50ec8-107">Structure de message pour l’opération Composite</span><span class="sxs-lookup"><span data-stu-id="50ec8-107">Message Structure for the Composite Operation</span></span>  
 <span data-ttu-id="50ec8-108">Dans la mesure où une opération composite contient plusieurs opérations individuelles ; la structure d’une opération composite contient des structures de message des opérations individuelles.</span><span class="sxs-lookup"><span data-stu-id="50ec8-108">Since a composite operation contains multiple individual operations; the message structure of a composite operation contains message structures of the individual operations.</span></span> <span data-ttu-id="50ec8-109">Le message d’opération composite suit un modèle d’échange de message demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="50ec8-109">The composite operation message follows a request-response message exchange pattern.</span></span>  
  
 <span data-ttu-id="50ec8-110">Le tableau suivant montre la structure des messages de demande et de réponse d’une opération composite qui contient une opération d’insertion, une procédure stockée empaquetée qui n’accepte pas les paramètres d’entrée et une opération de suppression.</span><span class="sxs-lookup"><span data-stu-id="50ec8-110">The following table shows the structure of the request and response messages of a composite operation that contains an Insert operation, a packaged stored procedure that does not take any input parameters, and a Delete operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50ec8-111">Consultez les descriptions de l’entité après le tableau.</span><span class="sxs-lookup"><span data-stu-id="50ec8-111">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="50ec8-112">Opération</span><span class="sxs-lookup"><span data-stu-id="50ec8-112">Operation</span></span>|<span data-ttu-id="50ec8-113">Message XML</span><span class="sxs-lookup"><span data-stu-id="50ec8-113">XML Message</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50ec8-114">Demande d’opération composite</span><span class="sxs-lookup"><span data-stu-id="50ec8-114">Composite Operation Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <Recordset>       <InsertRecord>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>           <InLineValue>[value]</InlineValue>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>           <InLineValue>[value]</InlineValue>         …       <InsertRecord>    </RECORDSET>   </Insert>   <[SP_NAME] xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/[SCHEMA]/[APP_NAME]" />   <Delete xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <FILTER>[WHERE_clause]</FILTER>   </Delete> </Request>`|  
|<span data-ttu-id="50ec8-115">Réponse de l’opération composite</span><span class="sxs-lookup"><span data-stu-id="50ec8-115">Composite Operation Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <InsertResult>[value]</InsertResult>    </InsertResponse>   <[SP_NAME]Response xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Procedures/[SCHEMA]">     <[PRM1_NAME]>value1<[PRM1_NAME]>     <[PRM2_NAME]>value2</[PRM2_NAME]>     …   </[SP_NAME]Response>    <DeleteResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 <span data-ttu-id="50ec8-116">Descriptions de l’entité :</span><span class="sxs-lookup"><span data-stu-id="50ec8-116">Entity descriptions:</span></span>  
  
 <span data-ttu-id="50ec8-117">[PROJECT_NAME] = nom du projet BizTalk qui contient le schéma de l’opération composite.</span><span class="sxs-lookup"><span data-stu-id="50ec8-117">[PROJECT_NAME] = Name of the BizTalk project that contains the composite operation schema.</span></span>  
  
 <span data-ttu-id="50ec8-118">[COMPOSITE_SCHEMA_NAME] = nom du schéma d’opération composite donné par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="50ec8-118">[COMPOSITE_SCHEMA_NAME] = Name of the composite operation schema given by the user.</span></span>  
  
 <span data-ttu-id="50ec8-119">[Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.</span><span class="sxs-lookup"><span data-stu-id="50ec8-119">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="50ec8-120">[Nom_table] = nom de la table ; par exemple, les employés.</span><span class="sxs-lookup"><span data-stu-id="50ec8-120">[TABLE_NAME] = Name of the table; for example, EMPLOYEE.</span></span>  
  
 <span data-ttu-id="50ec8-121">[FIELD1_NAME] = nom du champ de Table ; par exemple, un nom.</span><span class="sxs-lookup"><span data-stu-id="50ec8-121">[FIELD1_NAME] = Table field name; for example, NAME.</span></span>  
  
 <span data-ttu-id="50ec8-122">[SP_NAME] = la procédure stockée empaquetée à être exécutés ; par exemple, ADD_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="50ec8-122">[SP_NAME] = The packaged stored procedure to be executed; for example, ADD_EMP_DETAILS.</span></span>  
  
 <span data-ttu-id="50ec8-123">[Nom_application] = nom de l’Application Oracle qui contient la procédure stockée empaquetée.</span><span class="sxs-lookup"><span data-stu-id="50ec8-123">[APP_NAME] = Name of the Oracle Application that contains the packaged stored procedure.</span></span>  
  
 <span data-ttu-id="50ec8-124">[PRM1_NAME] = le nom du paramètre dans la procédure stockée package Oracle.</span><span class="sxs-lookup"><span data-stu-id="50ec8-124">[PRM1_NAME] = The name of the Oracle parameter in the packaged stored procedure.</span></span>  
  
## <a name="message-action-for-the-composite-operation"></a><span data-ttu-id="50ec8-125">Action de message pour l’opération Composite</span><span class="sxs-lookup"><span data-stu-id="50ec8-125">Message Action for the Composite Operation</span></span>  
 <span data-ttu-id="50ec8-126">L’action du message pour l’opération composite est « CompositeOperation ».</span><span class="sxs-lookup"><span data-stu-id="50ec8-126">The message action for the composite operation is “CompositeOperation.”</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ec8-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50ec8-127">See Also</span></span>  
 [<span data-ttu-id="50ec8-128">Messages et des schémas de Message pour l’adaptateur BizTalk pour Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="50ec8-128">Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)