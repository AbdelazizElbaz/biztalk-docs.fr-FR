---
title: "Exemples d’adaptateur de base de données Oracle | Documents Microsoft"
description: "Exemples d’adaptateur WCF de base de données Oracle qui peuvent être utilisés avec BizTalk Server, modèle de service WCF et modèle de canal WCF"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 744f19ce-3126-4745-92dd-4f68443180fc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5bfef9fcfce65d8aede1cd905a53469c565977f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="samples-for-the-oracle-database-adapter"></a><span data-ttu-id="9a837-103">Exemples de l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="9a837-103">Samples for the Oracle Database adapter</span></span>
<span data-ttu-id="9a837-104">Exemples de [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] sont classés ainsi :</span><span class="sxs-lookup"><span data-stu-id="9a837-104">Samples for [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] are categorized into:</span></span>  
  
-   <span data-ttu-id="9a837-105">Les exemples [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a837-105">[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] samples</span></span>  
  
-   <span data-ttu-id="9a837-106">Exemples de modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="9a837-106">WCF service model samples</span></span>  
  
-   <span data-ttu-id="9a837-107">Exemples de modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="9a837-107">WCF channel model samples</span></span>  

  
<span data-ttu-id="9a837-108">Les exemples sont disponibles au [Pack adaptateurs BizTalk 2010 : exemples d’adaptateur de base de données Oracle](https://www.microsoft.com/download/details.aspx?id=4675).</span><span class="sxs-lookup"><span data-stu-id="9a837-108">The samples are available at [BizTalk Adapter Pack 2010: Oracle Database adapter samples](https://www.microsoft.com/download/details.aspx?id=4675).</span></span> <span data-ttu-id="9a837-109">Les scripts SQL pour créer les tables et les packages utilisés dans les exemples sont inclus.</span><span class="sxs-lookup"><span data-stu-id="9a837-109">The SQL scripts for creating the tables and packages used in the samples are included.</span></span> 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
<span data-ttu-id="9a837-110">La liste suivante décrit les exemples.</span><span class="sxs-lookup"><span data-stu-id="9a837-110">The following list describes the samples.</span></span>
  
## <a name="biztalk-server-samples"></a><span data-ttu-id="9a837-111">Exemples de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9a837-111">BizTalk Server samples</span></span>
  
|<span data-ttu-id="9a837-112">Exemple de nom de répertoire</span><span class="sxs-lookup"><span data-stu-id="9a837-112">Sample Directory Name</span></span>|<span data-ttu-id="9a837-113"> Description</span><span class="sxs-lookup"><span data-stu-id="9a837-113">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="9a837-114">Func_RecordTypes</span><span class="sxs-lookup"><span data-stu-id="9a837-114">Func_RecordTypes</span></span>|<span data-ttu-id="9a837-115">Montre comment utiliser les paramètres de type d’enregistrement et de retourner des valeurs à l’aide des procédures et des fonctions du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a837-115">Demonstrates how to use RECORD type parameters and return values in functions and procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>|  
|<span data-ttu-id="9a837-116">Func_RefCursor</span><span class="sxs-lookup"><span data-stu-id="9a837-116">Func_RefCursor</span></span>|<span data-ttu-id="9a837-117">Montre comment utiliser des paramètres REF CURSOR dans des fonctions et procédures à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a837-117">Demonstrates how to use REF CURSOR parameters in functions and procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>|  
|<span data-ttu-id="9a837-118">InvokeFunction</span><span class="sxs-lookup"><span data-stu-id="9a837-118">InvokeFunction</span></span>|<span data-ttu-id="9a837-119">Montre comment appeler une fonction dans la base de données d’Oracle avec le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a837-119">Demonstrates how to invoke a function in Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>|  
|<span data-ttu-id="9a837-120">InvokeOverloadedProc</span><span class="sxs-lookup"><span data-stu-id="9a837-120">InvokeOverloadedProc</span></span>|<span data-ttu-id="9a837-121">Montre comment appeler des fonctions surchargées et les procédures à l’aide de base de données Oracle le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a837-121">Demonstrates how to invoke with overloaded functions and procedures in Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>|  
|<span data-ttu-id="9a837-122">Operate_BFILE</span><span class="sxs-lookup"><span data-stu-id="9a837-122">Operate_BFILE</span></span>|<span data-ttu-id="9a837-123">Montre comment utiliser les types d’Oracle BFILE dans les procédures d’Oracle à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a837-123">Demonstrates how to use Oracle BFILE types in Oracle procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>|  
|<span data-ttu-id="9a837-124">Operate_LOB</span><span class="sxs-lookup"><span data-stu-id="9a837-124">Operate_LOB</span></span>|<span data-ttu-id="9a837-125">Montre comment effectuer des opérations ReadLOB et UpdateLOB sur les tables avec des types de données LOB à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a837-125">Demonstrates how to perform ReadLOB and UpdateLOB operations on tables with LOB data types using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>|  
|<span data-ttu-id="9a837-126">PollingQuery</span><span class="sxs-lookup"><span data-stu-id="9a837-126">PollingQuery</span></span>|<span data-ttu-id="9a837-127">Montre comment configurer une requête d’interrogation et de recevoir les résultats à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a837-127">Demonstrates how to configure a polling query and receive the results using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>|  
|<span data-ttu-id="9a837-128">SelectAccTable</span><span class="sxs-lookup"><span data-stu-id="9a837-128">SelectAccTable</span></span>|<span data-ttu-id="9a837-129">Montre comment effectuer une requête select sur une table de base de données Oracle à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a837-129">Demonstrates how to perform a select query on an Oracle database table using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>|  
|<span data-ttu-id="9a837-130">SqlExec</span><span class="sxs-lookup"><span data-stu-id="9a837-130">SqlExec</span></span>|<span data-ttu-id="9a837-131">Montre comment exécuter des requêtes paramétrables à l’aide de l’opération SQLEXECUTE sur une base de données Oracle à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a837-131">Demonstrates how to perform parameterized queries using the SQLEXECUTE operation on an Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>|  
  
## <a name="wcf-service-model-samples"></a><span data-ttu-id="9a837-132">Exemples de modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="9a837-132">WCF service model samples</span></span>  
  
|<span data-ttu-id="9a837-133">Exemple de nom de répertoire</span><span class="sxs-lookup"><span data-stu-id="9a837-133">Sample Directory Name</span></span>|<span data-ttu-id="9a837-134"> Description</span><span class="sxs-lookup"><span data-stu-id="9a837-134">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="9a837-135">OracleBfileTypeSM</span><span class="sxs-lookup"><span data-stu-id="9a837-135">OracleBfileTypeSM</span></span>|<span data-ttu-id="9a837-136">Montre comment utiliser des types d’Oracle BFILE dans des opérations de base SQL signalées pour les tables Oracle et en tant que paramètres aux procédures d’Oracle.</span><span class="sxs-lookup"><span data-stu-id="9a837-136">Demonstrates how to use Oracle BFILE types in basic SQL operations surfaced for Oracle tables and as parameters to Oracle procedures.</span></span>|  
|<span data-ttu-id="9a837-137">OracleOverloadsSM</span><span class="sxs-lookup"><span data-stu-id="9a837-137">OracleOverloadsSM</span></span>|<span data-ttu-id="9a837-138">Montre comment appeler des fonctions surchargées et les procédures dans un package.</span><span class="sxs-lookup"><span data-stu-id="9a837-138">Demonstrates how to invoke overloaded functions and procedures in a package.</span></span>|  
|<span data-ttu-id="9a837-139">OraclePollingSM</span><span class="sxs-lookup"><span data-stu-id="9a837-139">OraclePollingSM</span></span>|<span data-ttu-id="9a837-140">Montre comment configurer une requête d’interrogation et de recevoir les résultats.</span><span class="sxs-lookup"><span data-stu-id="9a837-140">Demonstrates how to configure a polling query and receive the results.</span></span>|  
|<span data-ttu-id="9a837-141">OracleRecordTypesSM</span><span class="sxs-lookup"><span data-stu-id="9a837-141">OracleRecordTypesSM</span></span>|<span data-ttu-id="9a837-142">Montre comment utiliser les paramètres de type d’enregistrement et de retourner des valeurs dans les procédures et fonctions.</span><span class="sxs-lookup"><span data-stu-id="9a837-142">Demonstrates how to use RECORD type parameters and return values in functions and procedures.</span></span>|  
|<span data-ttu-id="9a837-143">OracleRefCursorsSM</span><span class="sxs-lookup"><span data-stu-id="9a837-143">OracleRefCursorsSM</span></span>|<span data-ttu-id="9a837-144">Montre comment utiliser des paramètres REF CURSOR dans des fonctions et procédures</span><span class="sxs-lookup"><span data-stu-id="9a837-144">Demonstrates how to use REF CURSOR parameters in functions and procedures</span></span>|  
|<span data-ttu-id="9a837-145">OracleTransactedDmlSM</span><span class="sxs-lookup"><span data-stu-id="9a837-145">OracleTransactedDmlSM</span></span>|<span data-ttu-id="9a837-146">Montre comment effectuer des opérations sur la base de données Oracle dans une transaction à l’aide du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="9a837-146">Demonstrates how to perform operations on the Oracle database in a transaction using the WCF service model.</span></span>|  
  
## <a name="wcf-channel-model-samples"></a><span data-ttu-id="9a837-147">Exemples de modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="9a837-147">WCF channel model samples</span></span>  
  
|<span data-ttu-id="9a837-148">Exemple de nom de répertoire</span><span class="sxs-lookup"><span data-stu-id="9a837-148">Sample Directory Name</span></span>|<span data-ttu-id="9a837-149"> Description</span><span class="sxs-lookup"><span data-stu-id="9a837-149">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="9a837-150">OraclePollingCM</span><span class="sxs-lookup"><span data-stu-id="9a837-150">OraclePollingCM</span></span>|<span data-ttu-id="9a837-151">Montre comment configurer une requête d’interrogation et de recevoir les résultats.</span><span class="sxs-lookup"><span data-stu-id="9a837-151">Demonstrates how to configure a polling query and receive the results.</span></span>|  
|<span data-ttu-id="9a837-152">OracleStreamingDemo</span><span class="sxs-lookup"><span data-stu-id="9a837-152">OracleStreamingDemo</span></span>|<span data-ttu-id="9a837-153">Montre comment effectuer la diffusion en continu de bout en bout des données LOB à l’aide de l’opérations Select UpdateLOB et la table</span><span class="sxs-lookup"><span data-stu-id="9a837-153">Demonstrates how to perform end-to-end streaming of LOB data using the UpdateLOB and table Select operations</span></span>|  
|<span data-ttu-id="9a837-154">OracleTransactedDmlCM</span><span class="sxs-lookup"><span data-stu-id="9a837-154">OracleTransactedDmlCM</span></span>|<span data-ttu-id="9a837-155">Montre comment effectuer des opérations sur la base de données Oracle dans une transaction à l’aide du modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="9a837-155">Demonstrates how to perform operations on the Oracle database in a transaction using the WCF channel model.</span></span>|  
  

## <a name="see-also"></a><span data-ttu-id="9a837-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a837-156">See Also</span></span>  
[<span data-ttu-id="9a837-157">Développer votre application Oracle Database</span><span class="sxs-lookup"><span data-stu-id="9a837-157">Develop your Oracle Database applications</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)