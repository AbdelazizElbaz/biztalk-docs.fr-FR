---
title: "Schémas de message pour la méthode ExecuteNonQuery, ExecuteReader et ExecuteScalar Operations1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aa5fdb2-1e7f-4a34-a1e5-c16d8fb477d5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b42ed9075ad16708f835786fd1fd09b414d06ebb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-executenonquery-executereader-and-executescalar-operations"></a><span data-ttu-id="0ec4e-102">Schémas de message pour la méthode ExecuteNonQuery, ExecuteReader et d’opérations de ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="0ec4e-102">Message Schemas for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>
<span data-ttu-id="0ec4e-103">Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] expose les opérations sortantes ExecuteNonQuery, ExecuteReader et ExecuteScalar au niveau racine pour exécuter des instructions SQL arbitraires ou des blocs de PL/SQL dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="0ec4e-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes the ExecuteNonQuery, ExecuteReader, and ExecuteScalar outbound operations at the root level to execute any arbitrary SQL statements or PL/SQL blocks in Oracle E-Business Suite.</span></span>  
  
 <span data-ttu-id="0ec4e-104">Pour plus d’informations sur :</span><span class="sxs-lookup"><span data-stu-id="0ec4e-104">For more information about:</span></span>  
  
-   <span data-ttu-id="0ec4e-105">Ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0ec4e-105">These operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).</span></span>  
  
-   <span data-ttu-id="0ec4e-106">Effectuez ces opérations à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [ExecuteReader, ExecuteScalar ou opérations ExecuteNonQuery dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).</span><span class="sxs-lookup"><span data-stu-id="0ec4e-106">Performing these operations using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).</span></span>  
  
## <a name="message-structure-for-the-executenonquery-executereader-and-executescalar-operations"></a><span data-ttu-id="0ec4e-107">Structure de message pour la méthode ExecuteNonQuery, ExecuteReader et d’opérations de ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="0ec4e-107">Message Structure for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>  
 <span data-ttu-id="0ec4e-108">Les messages dans ces opérations suivent un modèle d’échange de message demande-réponse, et le tableau suivant illustre la structure de ces messages de demande et de réponse.</span><span class="sxs-lookup"><span data-stu-id="0ec4e-108">The messages in these operations follow a request-response message exchange pattern, and the following table shows the structure of these request and response messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ec4e-109">Consultez les descriptions de l’entité après le tableau.</span><span class="sxs-lookup"><span data-stu-id="0ec4e-109">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="0ec4e-110">Opération</span><span class="sxs-lookup"><span data-stu-id="0ec4e-110">Operation</span></span>|<span data-ttu-id="0ec4e-111">Message XML</span><span class="sxs-lookup"><span data-stu-id="0ec4e-111">XML Message</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0ec4e-112">ExecuteNonQuery demande</span><span class="sxs-lookup"><span data-stu-id="0ec4e-112">ExecuteNonQuery Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQuery xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query>   <OutputRefCursorNames>     <string>[stringvalue1]</string>     <string>[stringvalue2]</string>     …   </OutputRefCursorNames> </ExecuteNonQuery>`|  
|<span data-ttu-id="0ec4e-113">ExecuteNonQuery réponse</span><span class="sxs-lookup"><span data-stu-id="0ec4e-113">ExecuteNonQuery Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQueryResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteNonQueryResult>[value]</ExecuteNonQueryResult>   <OutputRefCursors>     <DataSet>       <Any>[value]</Any>       <Any>[value]</Any>       …     </DataSet>   </OutputRefCursors> </ExecuteNonQueryResponse>`|  
|<span data-ttu-id="0ec4e-114">ExecuteReader demande</span><span class="sxs-lookup"><span data-stu-id="0ec4e-114">ExecuteReader Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteReader xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query> </ExecuteReader>`|  
|<span data-ttu-id="0ec4e-115">ExecuteReader réponse</span><span class="sxs-lookup"><span data-stu-id="0ec4e-115">ExecuteReader Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteReaderResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteReaderResult>     <Any>[value]</Any>     <Any>[value]</Any>       …   </ExecuteReaderResult> </ExecuteReaderResponse>`|  
|<span data-ttu-id="0ec4e-116">ExecuteScalar demande</span><span class="sxs-lookup"><span data-stu-id="0ec4e-116">ExecuteScalar Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalar xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query> </ExecuteScalar>`|  
|<span data-ttu-id="0ec4e-117">ExecuteScalar réponse</span><span class="sxs-lookup"><span data-stu-id="0ec4e-117">ExecuteScalar Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalarResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteScalarResult>[value]</ExecuteScalarResult> </ExecuteScalarResponse>`|  
  
 <span data-ttu-id="0ec4e-118">Descriptions de l’entité :</span><span class="sxs-lookup"><span data-stu-id="0ec4e-118">Entity descriptions:</span></span>  
  
 <span data-ttu-id="0ec4e-119">[Bloc PL/SQL] = l’intégralité du bloc PL/SQL à exécuter.</span><span class="sxs-lookup"><span data-stu-id="0ec4e-119">[PL/SQL block] = The entire PL/SQL block to be executed.</span></span>  
  
 <span data-ttu-id="0ec4e-120">[stringvalue1] = une valeur dans le tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="0ec4e-120">[stringvalue1] = A value in the array of strings.</span></span>  
  
## <a name="message-action-for-the-executenonquery-executereader-and-executescalar-operations"></a><span data-ttu-id="0ec4e-121">Action du message pour la méthode ExecuteNonQuery, ExecuteReader et d’opérations de ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="0ec4e-121">Message Action for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>  
 <span data-ttu-id="0ec4e-122">Le tableau suivant répertorie les actions de message utilisés par les opérations ExecuteNonQuery, ExecuteReader et ExecuteScalar.</span><span class="sxs-lookup"><span data-stu-id="0ec4e-122">The following table shows the message actions that are used by the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations.</span></span>  
  
|<span data-ttu-id="0ec4e-123">Opération</span><span class="sxs-lookup"><span data-stu-id="0ec4e-123">Operation</span></span>|<span data-ttu-id="0ec4e-124">Action</span><span class="sxs-lookup"><span data-stu-id="0ec4e-124">Action</span></span>|  
|---------------|------------|  
|<span data-ttu-id="0ec4e-125">ExecuteNonQuery demande</span><span class="sxs-lookup"><span data-stu-id="0ec4e-125">ExecuteNonQuery Request</span></span>|<span data-ttu-id="0ec4e-126">GenericOp/ExecuteNonQuery</span><span class="sxs-lookup"><span data-stu-id="0ec4e-126">GenericOp/ExecuteNonQuery</span></span>|  
|<span data-ttu-id="0ec4e-127">ExecuteNonQuery réponse</span><span class="sxs-lookup"><span data-stu-id="0ec4e-127">ExecuteNonQuery Response</span></span>|<span data-ttu-id="0ec4e-128">GenericOp/ExecuteNonQuery/réponse</span><span class="sxs-lookup"><span data-stu-id="0ec4e-128">GenericOp/ExecuteNonQuery/response</span></span>|  
|<span data-ttu-id="0ec4e-129">ExecuteReader demande</span><span class="sxs-lookup"><span data-stu-id="0ec4e-129">ExecuteReader Request</span></span>|<span data-ttu-id="0ec4e-130">GenericOp/ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="0ec4e-130">GenericOp/ExecuteReader</span></span>|  
|<span data-ttu-id="0ec4e-131">ExecuteReader réponse</span><span class="sxs-lookup"><span data-stu-id="0ec4e-131">ExecuteReader Response</span></span>|<span data-ttu-id="0ec4e-132">GenericOp/ExecuteReader/réponse</span><span class="sxs-lookup"><span data-stu-id="0ec4e-132">GenericOp/ExecuteReader/response</span></span>|  
|<span data-ttu-id="0ec4e-133">ExecuteScalar demande</span><span class="sxs-lookup"><span data-stu-id="0ec4e-133">ExecuteScalar Request</span></span>|<span data-ttu-id="0ec4e-134">GenericOp/ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="0ec4e-134">GenericOp/ExecuteScalar</span></span>|  
|<span data-ttu-id="0ec4e-135">ExecuteScalar réponse</span><span class="sxs-lookup"><span data-stu-id="0ec4e-135">ExecuteScalar Response</span></span>|<span data-ttu-id="0ec4e-136">GenericOp/ExecuteScalar/réponse</span><span class="sxs-lookup"><span data-stu-id="0ec4e-136">GenericOp/ExecuteScalar/response</span></span>|