---
title: "Appeler des fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, invoke functions and procedures using the WCF service model
- WCF service model, invoking functions and procedures
ms.assetid: 806fc803-3640-42d6-bdf9-53b08f9c7c50
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f1fac59fc77b0cf52abe789db8feb2305043708
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="8eccd-102">Appeler des fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="8eccd-102">Invoke Functions and Procedures in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="8eccd-103">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence des procédures, fonctions et des packages en tant qu’opérations.</span><span class="sxs-lookup"><span data-stu-id="8eccd-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces procedures, functions, and packages as operations.</span></span> <span data-ttu-id="8eccd-104">Dans le modèle de service WCF, ces opérations sont représentées en tant que méthodes sur un client WCF.</span><span class="sxs-lookup"><span data-stu-id="8eccd-104">In the WCF service model these operations are represented as methods on a WCF client.</span></span> <span data-ttu-id="8eccd-105">Le modèle de service WCF et le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="8eccd-105">The WCF service model and the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:</span></span>  
  
-   <span data-ttu-id="8eccd-106">**Prend en charge les fonctions**.</span><span class="sxs-lookup"><span data-stu-id="8eccd-106">**Support functions**.</span></span> <span data-ttu-id="8eccd-107">La valeur de retour de la fonction d’Oracle est présentée comme la valeur de retour de la méthode de client WCF.</span><span class="sxs-lookup"><span data-stu-id="8eccd-107">The RETURN value of the Oracle function is surfaced as the return value of the WCF client method.</span></span> <span data-ttu-id="8eccd-108">Paramètres Oracle sont signalées en tant que paramètres (avec la direction appropriée tel que défini ci-dessous) à la méthode de client WCF.</span><span class="sxs-lookup"><span data-stu-id="8eccd-108">Oracle parameters are surfaced as parameters (with the appropriate direction as defined below) to the WCF client method.</span></span>  
  
-   <span data-ttu-id="8eccd-109">**Prend en charge les procédures**.</span><span class="sxs-lookup"><span data-stu-id="8eccd-109">**Support procedures**.</span></span> <span data-ttu-id="8eccd-110">Le premier paramètre de la procédure d’Oracle est présenté comme la valeur de retour de la méthode de client WCF.</span><span class="sxs-lookup"><span data-stu-id="8eccd-110">The first OUT parameter of the Oracle procedure is surfaced as the return value of the WCF client method.</span></span> <span data-ttu-id="8eccd-111">Tous les autres paramètres Oracle sont signalées en tant que paramètres (avec la direction appropriée tel que défini ci-dessous) à la méthode de client WCF.</span><span class="sxs-lookup"><span data-stu-id="8eccd-111">All other Oracle parameters are surfaced as parameters (with the appropriate direction as defined below) to the WCF client method.</span></span>  
  
-   <span data-ttu-id="8eccd-112">**Prend en charge les packages Oracle**.</span><span class="sxs-lookup"><span data-stu-id="8eccd-112">**Support Oracle packages**.</span></span> <span data-ttu-id="8eccd-113">Le nom de l’opération et l’espace de noms de ses types de paramètre sont qualifiés par le nom du package.</span><span class="sxs-lookup"><span data-stu-id="8eccd-113">The name of the operation and the namespace of its parameter types are qualified by the package name.</span></span>  
  
-   <span data-ttu-id="8eccd-114">**Surchargée de prise en charge des fonctions et procédures**.</span><span class="sxs-lookup"><span data-stu-id="8eccd-114">**Support overloaded functions and procedures**.</span></span>  
  
-   <span data-ttu-id="8eccd-115">**Prise en charge IN, OUT et IN, OUT pour les types de données Oracle base pour les fonctions et procédures**.</span><span class="sxs-lookup"><span data-stu-id="8eccd-115">**Support IN, OUT and IN OUT parameters for basic Oracle data types for both procedures and functions**.</span></span> <span data-ttu-id="8eccd-116">Les paramètres de sortie sont exposés en tant que **hors** paramètres dans la méthode de client WCF et dans les paramètres sont exposés en tant que **ref** paramètres.</span><span class="sxs-lookup"><span data-stu-id="8eccd-116">OUT parameters are surfaced as **out** parameters on the WCF client method and IN OUT parameters are surfaced as **ref** parameters.</span></span>  
  
-   <span data-ttu-id="8eccd-117">**IN de prise en charge, la sortie et dans les paramètres REF CURSOR pour les procédures et fonctions, ainsi que les valeurs de retour de fonction**.</span><span class="sxs-lookup"><span data-stu-id="8eccd-117">**Support IN, OUT, and IN OUT REF CURSOR parameters for procedures and functions, as well as function RETURN values**.</span></span> <span data-ttu-id="8eccd-118">Pour plus d’informations, consultez [exécution d’opérations à l’aide de REF CURSOR dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="8eccd-118">For more information, see [Performing Operations Using REF CURSORS in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="8eccd-119">**Prise en charge dans, OUT et dans les enregistrements pour les procédures et fonctions de paramètres de type, ainsi que des valeurs de retour de fonction**.</span><span class="sxs-lookup"><span data-stu-id="8eccd-119">**Support IN, OUT, and IN OUT RECORD type parameters for procedures and functions, as well as function RETURN values**.</span></span> <span data-ttu-id="8eccd-120">Pour plus d’informations, consultez [exécution d’opérations à l’aide des Types d’enregistrements dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="8eccd-120">For more information, see [Performing Operations Using RECORD Types in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="8eccd-121">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="8eccd-121">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="8eccd-122">Les exemples de cette rubrique utilisent le /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT surchargé procédure.</span><span class="sxs-lookup"><span data-stu-id="8eccd-122">The examples in this topic use the /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT overloaded procedure.</span></span> <span data-ttu-id="8eccd-123">Cette procédure lit un enregistrement de la table de SCOTT/compte basée sur un ID de compte ou un nom de compte.</span><span class="sxs-lookup"><span data-stu-id="8eccd-123">This procedure reads a record from the SCOTT/ACCOUNT table based on either an account ID or an account name.</span></span> <span data-ttu-id="8eccd-124">Un script pour générer cette procédure et le tableau est fourni avec les exemples du Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="8eccd-124">A script to generate this procedure and table is supplied with the SDK samples.</span></span> <span data-ttu-id="8eccd-125">Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).</span><span class="sxs-lookup"><span data-stu-id="8eccd-125">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="8eccd-126">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="8eccd-126">The WCF Client Class</span></span>  
 <span data-ttu-id="8eccd-127">Le tableau suivant présente le nom du client WCF et la méthode générée pour les procédures, fonctions et des packages qui la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces.</span><span class="sxs-lookup"><span data-stu-id="8eccd-127">The following table shows the name of the WCF client and the method generated for procedures, functions and packages that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces.</span></span> <span data-ttu-id="8eccd-128">Sauf si une fonction ou procédure est surchargé, un seul client WCF est utilisé pour appeler toutes les fonctions dans un schéma, toutes les procédures dans un schéma, ou toutes les fonctions et procédures dans un package.</span><span class="sxs-lookup"><span data-stu-id="8eccd-128">Unless a function or procedure is overloaded, a single WCF client is used to invoke all of the functions in a schema, all of the procedures in a schema, or all of the functions and procedures in a package.</span></span>  
  
|<span data-ttu-id="8eccd-129">Artefact d’Oracle</span><span class="sxs-lookup"><span data-stu-id="8eccd-129">Oracle Artifact</span></span>|<span data-ttu-id="8eccd-130">Nom de l’opération Client WCF</span><span class="sxs-lookup"><span data-stu-id="8eccd-130">WCF Client Operation Name</span></span>|<span data-ttu-id="8eccd-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="8eccd-131">Example</span></span>|  
|---------------------|-------------------------------|-------------|  
|<span data-ttu-id="8eccd-132">Procédure</span><span class="sxs-lookup"><span data-stu-id="8eccd-132">Procedure</span></span>|<span data-ttu-id="8eccd-133">[SCHÉMA] ProcedureClient. [NOM_PROC]</span><span class="sxs-lookup"><span data-stu-id="8eccd-133">[SCHEMA]ProcedureClient.[PROC_NAME]</span></span>|<span data-ttu-id="8eccd-134">SCOTTProcedureClient.MYPROC</span><span class="sxs-lookup"><span data-stu-id="8eccd-134">SCOTTProcedureClient.MYPROC</span></span>|  
|<span data-ttu-id="8eccd-135">Fonction</span><span class="sxs-lookup"><span data-stu-id="8eccd-135">Function</span></span>|<span data-ttu-id="8eccd-136">[SCHÉMA] FunctionClient. [FUNC_NAME]</span><span class="sxs-lookup"><span data-stu-id="8eccd-136">[SCHEMA]FunctionClient.[FUNC_NAME]</span></span>|<span data-ttu-id="8eccd-137">SCOTTProcedureClient.MYFUNC</span><span class="sxs-lookup"><span data-stu-id="8eccd-137">SCOTTProcedureClient.MYFUNC</span></span>|  
|<span data-ttu-id="8eccd-138">Package (procédure ou fonction)</span><span class="sxs-lookup"><span data-stu-id="8eccd-138">Package (procedure or function)</span></span>|<span data-ttu-id="8eccd-139">[SCHÉMA] Le package [PACKAGE_NAME] Client. [Nom_proc ou FUNC_NAME]</span><span class="sxs-lookup"><span data-stu-id="8eccd-139">[SCHEMA]Package[PACKAGE_NAME]Client.[PROC_NAME or FUNC_NAME]</span></span>|<span data-ttu-id="8eccd-140">SCOTTPackageMYPACKAGEClient.MYPROC</span><span class="sxs-lookup"><span data-stu-id="8eccd-140">SCOTTPackageMYPACKAGEClient.MYPROC</span></span>|  
  
 <span data-ttu-id="8eccd-141">[Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.</span><span class="sxs-lookup"><span data-stu-id="8eccd-141">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="8eccd-142">[Nom_proc] = le nom d’une procédure d’Oracle ; par exemple, MYPROC.</span><span class="sxs-lookup"><span data-stu-id="8eccd-142">[PROC_NAME] = The name of an Oracle procedure; for example, MYPROC.</span></span>  
  
 <span data-ttu-id="8eccd-143">[FUNC_NAME] = le nom d’une fonction d’Oracle ; par exemple, MYFUNC.</span><span class="sxs-lookup"><span data-stu-id="8eccd-143">[FUNC_NAME] = The name of an Oracle function; for example, MYFUNC.</span></span>  
  
 <span data-ttu-id="8eccd-144">[PACKAGE_NAME] = le nom d’un package Oracle.</span><span class="sxs-lookup"><span data-stu-id="8eccd-144">[PACKAGE_NAME] = The name of an Oracle package.</span></span>  
  
 <span data-ttu-id="8eccd-145">La [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] représente Oracle enregistrement paramètres de type et retourner des valeurs, ainsi que les jeux de résultats retournés par les paramètres REF CURSOR en tant que types XML complexes qui contiennent les données de ligne (ou champs) d’un enregistrement d’Oracle.</span><span class="sxs-lookup"><span data-stu-id="8eccd-145">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] represents Oracle RECORD type parameters and return values as well as the result sets returned by REF CURSOR parameters as complex XML types that contain the row data (or fields) of an Oracle record.</span></span> <span data-ttu-id="8eccd-146">Dans le modèle de service WCF, chacun de ces types XML est représentée comme une classe .NET ; les propriétés de la classe représentent les champs du type d’enregistrement ou du jeu de résultats REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="8eccd-146">In the WCF service model, each of these XML types is represented as a .NET class; the properties of the class represent the fields of the RECORD type or REF CURSOR result set.</span></span> <span data-ttu-id="8eccd-147">Types d’enregistrements Oracle sont toujours représentés en tant que classes de .NET fortement typée.</span><span class="sxs-lookup"><span data-stu-id="8eccd-147">Oracle RECORD types are always represented as strongly-typed .NET classes.</span></span> <span data-ttu-id="8eccd-148">Un jeu de résultats REF CURSOR, toutefois, peut être représenté sous forme d’enregistrements faiblement typée soit fortement typée selon si le REF CURSOR elle-même est déclaré comme fortement typée ou faiblement typée.</span><span class="sxs-lookup"><span data-stu-id="8eccd-148">A REF CURSOR result set, however, can be represented as either strongly-typed or weakly-typed records based on whether the REF CURSOR itself is declared as strongly-typed or weakly-typed.</span></span> <span data-ttu-id="8eccd-149">Les classes que représentent REF CURSOR ou enregistrement type paramètres (ou valeurs de retour) sont générées dans un espace de noms unique en fonction de la procédure, une fonction ou un package.</span><span class="sxs-lookup"><span data-stu-id="8eccd-149">The classes that represent REF CURSOR or RECORD type parameters (or return values) are generated in a unique namespace based on the procedure, function, or package.</span></span> <span data-ttu-id="8eccd-150">Le tableau suivant présente ces espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="8eccd-150">The following table shows these namespaces.</span></span>  
  
|<span data-ttu-id="8eccd-151">Artefact d’Oracle</span><span class="sxs-lookup"><span data-stu-id="8eccd-151">Oracle Artifact</span></span>|<span data-ttu-id="8eccd-152">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="8eccd-152">Namespace</span></span>|<span data-ttu-id="8eccd-153">Exemple</span><span class="sxs-lookup"><span data-stu-id="8eccd-153">Example</span></span>|  
|---------------------|---------------|-------------|  
|<span data-ttu-id="8eccd-154">Procédure</span><span class="sxs-lookup"><span data-stu-id="8eccd-154">Procedure</span></span>|<span data-ttu-id="8eccd-155">[BASE_NS].</span><span class="sxs-lookup"><span data-stu-id="8eccd-155">[BASE_NS].</span></span> <span data-ttu-id="8eccd-156">[SCHÉMA]. Procédure. [NOM_PROC]</span><span class="sxs-lookup"><span data-stu-id="8eccd-156">[SCHEMA].Procedure.[PROC_NAME]</span></span>|<span data-ttu-id="8eccd-157">Microsoft.lobservices.OracleDB._2007._03.Scott. Procedure.MYPROC</span><span class="sxs-lookup"><span data-stu-id="8eccd-157">microsoft.lobservices.oracledb._2007._03.SCOTT.Procedure.MYPROC</span></span>|  
|<span data-ttu-id="8eccd-158">Fonction</span><span class="sxs-lookup"><span data-stu-id="8eccd-158">Function</span></span>|<span data-ttu-id="8eccd-159">[BASE_NS].</span><span class="sxs-lookup"><span data-stu-id="8eccd-159">[BASE_NS].</span></span> <span data-ttu-id="8eccd-160">[SCHÉMA]. Fonction. [FUNC_NAME]</span><span class="sxs-lookup"><span data-stu-id="8eccd-160">[SCHEMA].Function.[FUNC_NAME]</span></span>|<span data-ttu-id="8eccd-161">Microsoft.lobservices.OracleDB._2007._03.Scott. Function.MYFUNC</span><span class="sxs-lookup"><span data-stu-id="8eccd-161">microsoft.lobservices.oracledb._2007._03.SCOTT.Function.MYFUNC</span></span>|  
|<span data-ttu-id="8eccd-162">Package (procédure)</span><span class="sxs-lookup"><span data-stu-id="8eccd-162">Package (Procedure)</span></span>|<span data-ttu-id="8eccd-163">[BASE_NS].</span><span class="sxs-lookup"><span data-stu-id="8eccd-163">[BASE_NS].</span></span> <span data-ttu-id="8eccd-164">[SCHÉMA]. Package. [PACKAGE_NAME]. [NOM_PROC]</span><span class="sxs-lookup"><span data-stu-id="8eccd-164">[SCHEMA].Package.[PACKAGE_NAME].[PROC_NAME]</span></span>|<span data-ttu-id="8eccd-165">Microsoft.lobservices.OracleDB._2007._03.Scott. Package.MYPACKAGE.MYPROC</span><span class="sxs-lookup"><span data-stu-id="8eccd-165">microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYPROC</span></span>|  
|<span data-ttu-id="8eccd-166">Package (fonction)</span><span class="sxs-lookup"><span data-stu-id="8eccd-166">Package (Function)</span></span>|<span data-ttu-id="8eccd-167">[BASE_NS].</span><span class="sxs-lookup"><span data-stu-id="8eccd-167">[BASE_NS].</span></span> <span data-ttu-id="8eccd-168">[SCHÉMA]. Package. [PACKAGE_NAME]. [FUNC_NAME]</span><span class="sxs-lookup"><span data-stu-id="8eccd-168">[SCHEMA].Package.[PACKAGE_NAME].[FUNC_NAME]</span></span>|<span data-ttu-id="8eccd-169">Microsoft.lobservices.OracleDB._2007._03.Scott. Package.MYPACKAGE.MYFUNC</span><span class="sxs-lookup"><span data-stu-id="8eccd-169">microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYFUNC</span></span>|  
|<span data-ttu-id="8eccd-170">Jeu d’enregistrements générique (faiblement typée)</span><span class="sxs-lookup"><span data-stu-id="8eccd-170">Generic Record Set (weakly-typed)</span></span>|<span data-ttu-id="8eccd-171">[BASE_NS]</span><span class="sxs-lookup"><span data-stu-id="8eccd-171">[BASE_NS]</span></span>|<span data-ttu-id="8eccd-172">Microsoft.lobservices.OracleDB._2007._03</span><span class="sxs-lookup"><span data-stu-id="8eccd-172">microsoft.lobservices.oracledb._2007._03</span></span>|  
  
 <span data-ttu-id="8eccd-173">[BASE_NS] = la base de l’adaptateur de l’espace de noms ; Microsoft.lobservices.OracleDB._2007._03.</span><span class="sxs-lookup"><span data-stu-id="8eccd-173">[BASE_NS] = The base adapter namespace; microsoft.lobservices.oracledb._2007._03.</span></span>  
  
 <span data-ttu-id="8eccd-174">[Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.</span><span class="sxs-lookup"><span data-stu-id="8eccd-174">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="8eccd-175">[Nom_proc] = le nom d’une procédure d’Oracle ; par exemple : MYPROC.</span><span class="sxs-lookup"><span data-stu-id="8eccd-175">[PROC_NAME] = The name of an Oracle procedure; for example; MYPROC.</span></span>  
  
 <span data-ttu-id="8eccd-176">[FUNC_NAME] = le nom d’une fonction d’Oracle ; par exemple MYFUNC.</span><span class="sxs-lookup"><span data-stu-id="8eccd-176">[FUNC_NAME] = The name of an Oracle function; for example MYFUNC.</span></span>  
  
 <span data-ttu-id="8eccd-177">[PACKAGE_NAME] = le nom d’un package Oracle.</span><span class="sxs-lookup"><span data-stu-id="8eccd-177">[PACKAGE_NAME] = The name of an Oracle package.</span></span>  
  
 <span data-ttu-id="8eccd-178">Pour plus d’informations sur l’utilisent de ces espaces de noms pour les paramètres d’enregistrement, consultez [exécution d’opérations à l’aide des Types d’enregistrements dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="8eccd-178">For information about how these namespaces are used for RECORD parameters, see [Performing Operations Using RECORD Types in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).</span></span> <span data-ttu-id="8eccd-179">Pour plus d’informations sur l’utilisent de ces espaces de noms de paramètres REF CURSOR, consultez [exécution d’opérations à l’aide de REF CURSOR dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="8eccd-179">For information about how these namespaces are used for REF CURSOR parameters, see [Performing Operations Using REF CURSORS in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
 <span data-ttu-id="8eccd-180">En règle générale, les paramètres Oracle et les valeurs de retour mappés comme suit dans la méthode du client WCF :</span><span class="sxs-lookup"><span data-stu-id="8eccd-180">In general, the Oracle parameters and return values are mapped as follows in the WCF client method:</span></span>  
  
-   <span data-ttu-id="8eccd-181">Paramètres Oracle IN sont mappées aux paramètres (entrées) de .NET.</span><span class="sxs-lookup"><span data-stu-id="8eccd-181">Oracle IN parameters are mapped to .NET (input) parameters.</span></span>  
  
-   <span data-ttu-id="8eccd-182">Paramètres OUT Oracle sont mappés vers .NET **hors** paramètres.</span><span class="sxs-lookup"><span data-stu-id="8eccd-182">Oracle OUT parameters are mapped to .NET **out** parameters.</span></span>  
  
-   <span data-ttu-id="8eccd-183">Oracle dans les paramètres sont mappés à .NET **ref** paramètres.</span><span class="sxs-lookup"><span data-stu-id="8eccd-183">Oracle IN OUT parameters are mapped to .NET **ref** parameters.</span></span>  
  
-   <span data-ttu-id="8eccd-184">Les valeurs de retour de fonction sont mappées à la valeur de retour de méthode.</span><span class="sxs-lookup"><span data-stu-id="8eccd-184">Function RETURN values are mapped to the method return value.</span></span>  
  
 <span data-ttu-id="8eccd-185">Toutefois, les deux exceptions importantes existent :</span><span class="sxs-lookup"><span data-stu-id="8eccd-185">However, two important exceptions exist:</span></span>  
  
-   <span data-ttu-id="8eccd-186">Les paramètres dans des REF CURSOR Oracle sont divisées en une chaîne d’entrée et une sortie (**out**) enregistrer ensemble.</span><span class="sxs-lookup"><span data-stu-id="8eccd-186">Oracle IN OUT REF CURSOR parameters are split into an input string and an output (**out**) record set.</span></span> <span data-ttu-id="8eccd-187">C’est parce que le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] représente les paramètres IN REF CUSROR comme des chaînes et des paramètres de sortie REF CURSOR en tant que types complexes (jeux d’enregistrements), elles ne peuvent pas être combinées dans un seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="8eccd-187">This is because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] represents IN REF CUSROR parameters as strings and OUT REF CURSOR parameters as complex types (record sets), these cannot be combined into a single parameter.</span></span>  
  
-   <span data-ttu-id="8eccd-188">Le premier paramètre dans une procédure Oracle est mappé à la valeur de retour de la méthode de client WCF.</span><span class="sxs-lookup"><span data-stu-id="8eccd-188">The first OUT parameter in an Oracle procedure is mapped to the return value of the WCF client method.</span></span> <span data-ttu-id="8eccd-189">Il s’agit de comportement WCF standard.</span><span class="sxs-lookup"><span data-stu-id="8eccd-189">This is standard WCF behavior.</span></span>  
  
 <span data-ttu-id="8eccd-190">L’exemple suivant montre la partie d’une procédure simple de Oracle (chargée dans le schéma SCOTT) et la signature de la méthode de client WCF qui est générée pour l’invoquer.</span><span class="sxs-lookup"><span data-stu-id="8eccd-190">The following example shows part of a simple Oracle procedure (loaded in the SCOTT schema) and the signature of the WCF client method that is generated to invoke it.</span></span> <span data-ttu-id="8eccd-191">La procédure Oracle a trois paramètres et trois paramètres OUT dans trois des paramètres ; Toutefois, la méthode du client WCF ne mappe pas un paramètre pour le premier paramètre de sortie.</span><span class="sxs-lookup"><span data-stu-id="8eccd-191">The Oracle procedure has three IN parameters, three IN OUT parameters, and three OUT parameters; however, the WCF client method does not map a parameter for the first OUT parameter.</span></span> <span data-ttu-id="8eccd-192">Au lieu de cela, il est mappé à la valeur de retour de méthode.</span><span class="sxs-lookup"><span data-stu-id="8eccd-192">Instead it is mapped to the method return value.</span></span>  
  
```  
CREATE or REPLACE PROCEDURE Sample_Procedure   
    (  
     INNUMBER      IN         NUMBER,  
     INVARCHAR     IN         VARCHAR2,  
     INDATE        IN         DATE,  
     INOUTNUMBER   IN OUT     NUMBER,  
     INOUTVARCHAR  IN OUT     VARCHAR,  
     INOUTDATE     IN OUT     DATE,  
     OUTNUMBER     OUT        NUMBER,  
     OUTVARCHAR    OUT        VARCHAR2,  
     OUTDATE       OUT        DATE  
    ) AS   
    BEGIN  
  
        ...  
  
    END;  
    /  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTProcedureClient : System.ServiceModel.ClientBase<SCOTTProcedure>, SCOTTProcedure {  
  
    public System.Nullable<decimal> SAMPLE_PROCEDURE  
       (  
        System.Nullable<decimal> INNUMBER,   
        string INVARCHAR,   
        System.Nullable\<System.DateTime\> INDATE,   
        ref System.Nullable<decimal> INOUTNUMBER,   
        ref string INOUTVARCHAR,   
        ref System.Nullable\<System.DateTime\> INOUTDATE,   
        out string OUTVARCHAR,   
        out System.Nullable\<System.DateTime\> OUTDATE  
        );  
}  
```  
  
### <a name="support-for-overloaded-procedures-functions-and-packages"></a><span data-ttu-id="8eccd-193">Prise en charge des Packages, des fonctions et procédures surchargées</span><span class="sxs-lookup"><span data-stu-id="8eccd-193">Support for Overloaded Procedures, Functions and Packages</span></span>  
 <span data-ttu-id="8eccd-194">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge surchargé procédures, fonctions et des packages en ajoutant une chaîne unique pour l’ID de nœud et l’espace de noms pour chaque artefact surchargé il met en évidence.</span><span class="sxs-lookup"><span data-stu-id="8eccd-194">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports overloaded procedures, functions, and packages by appending a unique string to the node ID and the namespace that it surfaces for each overloaded artifact.</span></span> <span data-ttu-id="8eccd-195">Cette chaîne est « overload1 » pour la première surcharge, « overload2 » pour la surcharge suivante et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="8eccd-195">This string is "overload1" for the first overload, "overload2" for the next overload, and so on.</span></span>  
  
 <span data-ttu-id="8eccd-196">Dans le modèle de service WCF, chaque procédure surchargée ou une fonction est représentée par un client WCF unique.</span><span class="sxs-lookup"><span data-stu-id="8eccd-196">In the WCF service model each overloaded procedure or function is represented by a unique WCF client.</span></span> <span data-ttu-id="8eccd-197">Cela est différent du cas de non surchargée dans laquelle toutes les fonctions dans un schéma, toutes les procédures dans un schéma, ou toutes les procédures et fonctions dans un PACKAGE sont appelées par le même client WCF.</span><span class="sxs-lookup"><span data-stu-id="8eccd-197">This is different from the non-overloaded case in which all of the functions in a SCHEMA, all of the procedures in a SCHEMA, or all of the procedures and functions in a PACKAGE are invoked by the same WCF client.</span></span> <span data-ttu-id="8eccd-198">Le tableau suivant montre le client WCF nom et la méthode générée pour les packages, les fonctions et procédures surchargées.</span><span class="sxs-lookup"><span data-stu-id="8eccd-198">The following table shows the WCF client name and method generated for overloaded procedures, functions, and packages.</span></span>  
  
|<span data-ttu-id="8eccd-199">Artefact d’Oracle</span><span class="sxs-lookup"><span data-stu-id="8eccd-199">Oracle Artifact</span></span>|<span data-ttu-id="8eccd-200">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="8eccd-200">WCF Client Name</span></span>|<span data-ttu-id="8eccd-201">Exemple</span><span class="sxs-lookup"><span data-stu-id="8eccd-201">Example</span></span>|  
|---------------------|---------------------|-------------|  
|<span data-ttu-id="8eccd-202">Package surchargé (procédure)</span><span class="sxs-lookup"><span data-stu-id="8eccd-202">Overloaded Package (Procedure)</span></span>|<span data-ttu-id="8eccd-203">[SCHÉMA] Package [PACKAGE_NAME] [nom_proc]] [OVERLOAD_ID] Client. [NOM_PROC]</span><span class="sxs-lookup"><span data-stu-id="8eccd-203">[SCHEMA]Package[PACKAGE_NAME][PROC_NAME] ][OVERLOAD_ID]Client.[PROC_NAME]</span></span>|<span data-ttu-id="8eccd-204">SCOTTPackageMYPACKAGEMYPROCoverload1Client.MYPROC</span><span class="sxs-lookup"><span data-stu-id="8eccd-204">SCOTTPackageMYPACKAGEMYPROCoverload1Client.MYPROC</span></span>|  
|<span data-ttu-id="8eccd-205">Package surchargé (fonction)</span><span class="sxs-lookup"><span data-stu-id="8eccd-205">Overloaded Package (Function)</span></span>|<span data-ttu-id="8eccd-206">[SCHÉMA] Package [PACKAGE_NAME] [FUNC_NAME]] [OVERLOAD_ID] Client. [FUNC_NAME]</span><span class="sxs-lookup"><span data-stu-id="8eccd-206">[SCHEMA]Package[PACKAGE_NAME][FUNC_NAME] ][OVERLOAD_ID]Client.[FUNC_NAME]</span></span>|<span data-ttu-id="8eccd-207">SCOTTPackageMYPACKAGEMYFUNCoverload1Client.MYFUNC</span><span class="sxs-lookup"><span data-stu-id="8eccd-207">SCOTTPackageMYPACKAGEMYFUNCoverload1Client.MYFUNC</span></span>|  
  
 <span data-ttu-id="8eccd-208">[Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.</span><span class="sxs-lookup"><span data-stu-id="8eccd-208">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="8eccd-209">[Nom_proc] = le nom d’une procédure d’Oracle ; par exemple : MYPROC.</span><span class="sxs-lookup"><span data-stu-id="8eccd-209">[PROC_NAME] = The name of an Oracle procedure; for example; MYPROC.</span></span>  
  
 <span data-ttu-id="8eccd-210">[FUNC_NAME] = le nom d’une fonction d’Oracle ; par exemple MYFUNC.</span><span class="sxs-lookup"><span data-stu-id="8eccd-210">[FUNC_NAME] = The name of an Oracle function; for example MYFUNC.</span></span>  
  
 <span data-ttu-id="8eccd-211">[PACKAGE_NAME] = le nom d’un package Oracle.</span><span class="sxs-lookup"><span data-stu-id="8eccd-211">[PACKAGE_NAME] = The name of an Oracle package.</span></span>  
  
 <span data-ttu-id="8eccd-212">[OVERLOAD_ID] = la chaîne unique qui identifie l’artefact surchargé ; « overload1 », « overload2 » et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="8eccd-212">[OVERLOAD_ID] = The unique string that identifies the overloaded artifact; "overload1", "overload2", and so on.</span></span>  
  
 <span data-ttu-id="8eccd-213">Le tableau suivant présente l’espace de noms généré pour les packages, les fonctions et procédures surchargées.</span><span class="sxs-lookup"><span data-stu-id="8eccd-213">The following table shows the namespace generated for overloaded procedures, functions, and packages.</span></span>  
  
|<span data-ttu-id="8eccd-214">Artefact d’Oracle</span><span class="sxs-lookup"><span data-stu-id="8eccd-214">Oracle Artifact</span></span>|<span data-ttu-id="8eccd-215">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="8eccd-215">Namespace</span></span>|<span data-ttu-id="8eccd-216">Exemple</span><span class="sxs-lookup"><span data-stu-id="8eccd-216">Example</span></span>|  
|---------------------|---------------|-------------|  
|<span data-ttu-id="8eccd-217">Package (procédure)</span><span class="sxs-lookup"><span data-stu-id="8eccd-217">Package (Procedure)</span></span>|<span data-ttu-id="8eccd-218">[BASE_NS].</span><span class="sxs-lookup"><span data-stu-id="8eccd-218">[BASE_NS].</span></span> <span data-ttu-id="8eccd-219">[SCHÉMA]. Package. [PACKAGE_NAME]. [NOM_PROC] [OVERLOAD_ID]</span><span class="sxs-lookup"><span data-stu-id="8eccd-219">[SCHEMA].Package.[PACKAGE_NAME].[PROC_NAME] [OVERLOAD_ID]</span></span>|<span data-ttu-id="8eccd-220">Microsoft.lobservices.OracleDB._2007._03.Scott. Package.MYPACKAGE.MYPROC.overload1</span><span class="sxs-lookup"><span data-stu-id="8eccd-220">microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYPROC.overload1</span></span>|  
|<span data-ttu-id="8eccd-221">Package (fonction)</span><span class="sxs-lookup"><span data-stu-id="8eccd-221">Package (Function)</span></span>|<span data-ttu-id="8eccd-222">[BASE_NS].</span><span class="sxs-lookup"><span data-stu-id="8eccd-222">[BASE_NS].</span></span> <span data-ttu-id="8eccd-223">[SCHÉMA]. Package. [PACKAGE_NAME]. [FUNC_NAME]. [OVERLOAD_ID]</span><span class="sxs-lookup"><span data-stu-id="8eccd-223">[SCHEMA].Package.[PACKAGE_NAME].[FUNC_NAME].[OVERLOAD_ID]</span></span>|<span data-ttu-id="8eccd-224">Microsoft.lobservices.OracleDB._2007._03.Scott. Package.MYPACKAGE.MYFUNC.overload1</span><span class="sxs-lookup"><span data-stu-id="8eccd-224">microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYFUNC.overload1</span></span>|  
|<span data-ttu-id="8eccd-225">Jeu d’enregistrements générique (faiblement typée)</span><span class="sxs-lookup"><span data-stu-id="8eccd-225">Generic Record Set (weakly-typed)</span></span>|<span data-ttu-id="8eccd-226">[BASE_NS]</span><span class="sxs-lookup"><span data-stu-id="8eccd-226">[BASE_NS]</span></span>|<span data-ttu-id="8eccd-227">Microsoft.lobservices.OracleDB._2007._03</span><span class="sxs-lookup"><span data-stu-id="8eccd-227">microsoft.lobservices.oracledb._2007._03</span></span>|  
  
 <span data-ttu-id="8eccd-228">[BASE_NS] = la base de l’adaptateur de l’espace de noms ; Microsoft.lobservices.OracleDB._2007._03.</span><span class="sxs-lookup"><span data-stu-id="8eccd-228">[BASE_NS] = The base adapter namespace; microsoft.lobservices.oracledb._2007._03.</span></span>  
  
 <span data-ttu-id="8eccd-229">[Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.</span><span class="sxs-lookup"><span data-stu-id="8eccd-229">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="8eccd-230">[Nom_proc] = le nom d’une procédure d’Oracle ; par exemple : MYPROC.</span><span class="sxs-lookup"><span data-stu-id="8eccd-230">[PROC_NAME] = The name of an Oracle procedure; for example; MYPROC.</span></span>  
  
 <span data-ttu-id="8eccd-231">[FUNC_NAME] = le nom d’une fonction d’Oracle ; par exemple MYFUNC.</span><span class="sxs-lookup"><span data-stu-id="8eccd-231">[FUNC_NAME] = The name of an Oracle function; for example MYFUNC.</span></span>  
  
 <span data-ttu-id="8eccd-232">[PACKAGE_NAME] = le nom d’un package Oracle.</span><span class="sxs-lookup"><span data-stu-id="8eccd-232">[PACKAGE_NAME] = The name of an Oracle package.</span></span>  
  
 <span data-ttu-id="8eccd-233">[OVERLOAD_ID] = la chaîne unique qui identifie l’artefact surchargé ; « overload1 », « overload2 » et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="8eccd-233">[OVERLOAD_ID] = The unique string that identifies the overloaded artifact; "overload1", "overload2", and so on.</span></span> <span data-ttu-id="8eccd-234">La valeur numérique dans la chaîne est l’ID de la surcharge pour l’artefact gérée par la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="8eccd-234">The numeric value in the string is the overload ID for the artifact maintained by the Oracle database.</span></span>  
  
 <span data-ttu-id="8eccd-235">L’exemple suivant montre les clients WCF et les signatures de méthode générés pour la procédure surchargée GET_ACCOUNT dans le package ACCOUNT_PKG.</span><span class="sxs-lookup"><span data-stu-id="8eccd-235">The following example shows the WCF clients and the method signatures generated for the overloaded GET_ACCOUNT procedure in the ACCOUNT_PKG package.</span></span> <span data-ttu-id="8eccd-236">(Les déclarations d’Oracle sont incluses). Cet exemple montre comment un client WCF unique est généré pour chaque surcharge et comment la méthode générée pour chaque client renvoie un ensemble d’enregistrements d’un espace de noms unique.</span><span class="sxs-lookup"><span data-stu-id="8eccd-236">(The Oracle declarations are included.) This example shows how a unique WCF client is generated for each overload and how the method generated for each client returns a record set in a unique namespace.</span></span>  
  
```  
/* Procedure that takes account ID and returns record for existing account in the ACCOUNT table */  
PROCEDURE get_account(aid IN account.acctid%TYPE, acct OUT account%ROWTYPE) ;  
  
/* Procedure that takes account name and returns record for existing account in the ACCOUNT table */  
PROCEDURE get_account(aname IN account.name%TYPE, acct OUT account%ROWTYPE) ;  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1>, SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1 {  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1.ACCTRECORD GET_ACCOUNT(System.Nullable<decimal> AID);  
}  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2>, SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2 {  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload2.ACCTRECORD GET_ACCOUNT(string ANAME);  
}  
```  
  
## <a name="invoking-functions-and-procedures"></a><span data-ttu-id="8eccd-237">Appel de fonctions et procédures</span><span class="sxs-lookup"><span data-stu-id="8eccd-237">Invoking Functions and Procedures</span></span>  
 <span data-ttu-id="8eccd-238">Pour appeler une fonction ou une procédure à l’aide d’un client WCF, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="8eccd-238">To invoke a function or a procedure by using a WCF client, perform the following steps.</span></span>  
  
1.  <span data-ttu-id="8eccd-239">Générer une classe de client WCF pour la fonction cible, une procédure ou un package.</span><span class="sxs-lookup"><span data-stu-id="8eccd-239">Generate a WCF client class for the target function, procedure, or package.</span></span> <span data-ttu-id="8eccd-240">Cette classe doit contenir des méthodes pour les opérations que vous appellerez sur l’artefact cible.</span><span class="sxs-lookup"><span data-stu-id="8eccd-240">This class should contain methods for the operations that you will invoke on the target artifact.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8eccd-241">Dans le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], la surcharge fonctions et procédures s’affichent dans le **catégories et opérations disponibles** boîte [name].1, [nom].2, [nom].3 et ainsi de suite, où [NAME] est le nom de l’artefact surchargé et la valeur numérique est l’ID de la surcharge de la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="8eccd-241">In the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], overloaded functions and procedures appear in the **Available categories and operations** box as [NAME].1, [NAME].2, [NAME].3, and so on, where [NAME] is the name of the overloaded artifact and the numeric value is the overload ID on the Oracle database.</span></span>  
  
2.  <span data-ttu-id="8eccd-242">Créer une instance de la classe de client WCF et appeler ses méthodes pour appeler la fonction ou procédure.</span><span class="sxs-lookup"><span data-stu-id="8eccd-242">Create an instance of the WCF client class and call its methods to invoke the function or procedure.</span></span>  
  
 <span data-ttu-id="8eccd-243">Pour plus d’informations sur la façon de créer une classe de client WCF et d’appeler des opérations sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [vue d’ensemble du modèle de Service WCF avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="8eccd-243">For more detailed information about how to create a WCF client class and invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Overview of the WCF Service Model with the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).</span></span>  
  
 <span data-ttu-id="8eccd-244">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exécute chaque opération à l’intérieur d’une transaction sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="8eccd-244">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] executes each operation inside of a transaction on the Oracle database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8eccd-245">Les classes qui représentent des REF CURSOR et les paramètres de type d’enregistrement ou de valeurs de retour dans les fonctions ou procédures (et packages) qui sont déclarés dans un espace de noms unique pour chaque fonction ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="8eccd-245">The classes that represent REF CURSOR and RECORD type parameters or return values in functions or procedures (and packages) are declared in a unique namespace for each function or procedure.</span></span> <span data-ttu-id="8eccd-246">Cela signifie, par exemple, un type de PACKAGE REF CURSOR est utilisé comme valeur de retour dans les deux fonctions différentes sera déclaré dans un espace de noms unique pour chaque méthode de client WCF.</span><span class="sxs-lookup"><span data-stu-id="8eccd-246">This means, for example, that a PACKAGE REF CURSOR type that is used as a return value in two different functions will be declared in a unique namespace for each WCF client method.</span></span> <span data-ttu-id="8eccd-247">Vous devez soit déclarer des variables distinctes pour contenir ces différentes valeurs de retour ou un effectué correctement la variable lorsque vous appelez une des méthodes de client WCF.</span><span class="sxs-lookup"><span data-stu-id="8eccd-247">You must either declare separate variables to hold these different return values or appropriately cast the variable when you invoke one of the WCF client methods.</span></span>  
  
 <span data-ttu-id="8eccd-248">L’exemple suivant illustre l’appel de la procédure surchargée /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT pour obtenir des enregistrements de compte à partir de la table /SCOTT/ACCOUNT.</span><span class="sxs-lookup"><span data-stu-id="8eccd-248">The following example demonstrates calling the overloaded /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT procedure to get account records from the /SCOTT/ACCOUNT table.</span></span> <span data-ttu-id="8eccd-249">Tout d’abord un nouvel enregistrement est créé en appelant la procédure /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT.</span><span class="sxs-lookup"><span data-stu-id="8eccd-249">First a new record is created by calling the /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT procedure.</span></span> <span data-ttu-id="8eccd-250">Ensuite, le nouvel enregistrement est en lecture différée deux fois par appelant différentes surcharges de GET_ACCOUNT.</span><span class="sxs-lookup"><span data-stu-id="8eccd-250">Then the new record is read back twice by calling different overloads of GET_ACCOUNT.</span></span> <span data-ttu-id="8eccd-251">Cet exemple utilise trois clients WCF, pour la procédure CREATE_ACCOUNT et un pour les surcharges GET_ACCOUNT.</span><span class="sxs-lookup"><span data-stu-id="8eccd-251">This example uses three WCF clients, one for the CREATE_ACCOUNT procedure and one each for the GET_ACCOUNT overloads.</span></span> <span data-ttu-id="8eccd-252">Alias sont utilisés pour faire la distinction entre les espaces de noms utilisés pour la valeur de retour de GET_ACCOUNT.</span><span class="sxs-lookup"><span data-stu-id="8eccd-252">Aliases are used to distinguish between namespaces used for the return value of GET_ACCOUNT.</span></span> <span data-ttu-id="8eccd-253">Un exemple complet est disponible dans les exemples du Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="8eccd-253">A full sample is available in the SDK samples.</span></span> <span data-ttu-id="8eccd-254">Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).</span><span class="sxs-lookup"><span data-stu-id="8eccd-254">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF Adapter LOB SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF Adapter LOB SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// Alias client namespaces to shorten declarations of "shared" types   
using CREATE_ACCOUNTns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT;  
using GET_ACCOUNT_BY_IDns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1;  
using GET_ACCOUNT_BY_NAMEns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload2;  
  
// This sample demonstrates calling overloaded packaged procedures on Oracle  
// First a new account is created by calling CREATE_ACCOUNT which takes two record parameters  
// Then the information for the new account is returned by calling an overloaded procedure GET_ACCOUNT  
// The first overload returns the account information by account ID  
// The second overload returns the account information by account name  
// Notice that different clients (and namespaces) are created for overloaded procedures and functions  
namespace OracleOverloadsSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            decimal acctId;  
            string newAccountName = "Paula Bento";  
  
            Console.WriteLine("Creating clients");  
            // Create Client for CREATE_ACCOUNT Function  
            SCOTTPackageACCOUNT_PKGClient createAccountClient =   
                new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG");  
            // NOTE: user name and password are case-sensitive  
            createAccountClient.ClientCredentials.UserName.UserName = "SCOTT";  
            createAccountClient.ClientCredentials.UserName.Password = "TIGER";  
  
            // Create Client for GET_ACCOUNT Overload 1 -- takes ACCOUNT ID parameter  
            SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client getAccountByIdClient =   
                new SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1");  
            // NOTE: user name and password are case-sensitive  
            getAccountByIdClient.ClientCredentials.UserName.UserName = "SCOTT";  
            getAccountByIdClient.ClientCredentials.UserName.Password = "TIGER";  
  
            // Create Client for GET_ACCOUNT Overload 2 -- takes ACCOUNT NAME parameter  
            // NOTE: this client can be created from configuration; detail provided here  
            // for demonstration  
            OracleDBBinding overload2Binding = new OracleDBBinding();  
            EndpointAddress overload2EndpointAddress = new EndpointAddress("oracleDB://ADAPTER");  
            SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client getAccountByNameClient =   
                new SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client(overload2Binding, overload2EndpointAddress);  
            // NOTE: user name and password are case-sensitive  
            getAccountByNameClient.ClientCredentials.UserName.UserName = "SCOTT";  
            getAccountByNameClient.ClientCredentials.UserName.Password = "TIGER";  
  
            try  
            {  
                Console.WriteLine("Opening clients -- please wait");  
                // Open clients  
                createAccountClient.Open();  
                getAccountByIdClient.Open();  
                getAccountByNameClient.Open();  
  
                Console.WriteLine("Creating new account");  
                // Create an account record  
                // NOTE: ACCTRECORD is defined in all three namespaces so specify the definition  
                // that corresponds to the client.  
                CREATE_ACCOUNTns.ACCTRECORD acctRec = new CREATE_ACCOUNTns.ACCTRECORD();  
  
                // Set any value for ACCTID -- new account ID is returned by CREATE_ACCOUNT  
                acctRec.ACCTID = 0;  
                acctRec.NAME = newAccountName;  
                acctRec.BALANCE = 10537;  
  
                // Create address record  
                CREATE_ACCOUNTns.ACCOUNT_PKGADDRESS_REC_TYPERECORD addrRec = new CREATE_ACCOUNTns.ACCOUNT_PKGADDRESS_REC_TYPERECORD();  
                addrRec.STREET = "456 Valley Rd";  
                addrRec.CITY = "New York";  
                addrRec.STATE = "NY";  
  
                // Create account  
                acctId = (decimal)createAccountClient.CREATE_ACCOUNT(acctRec, addrRec);  
                Console.WriteLine("New Account Created: AccountId = {0}, Name = {1}, Balance = {2:C}",  
                   acctId, acctRec.NAME, acctRec.BALANCE);  
  
                /* Get new account by Id */  
                GET_ACCOUNT_BY_IDns.ACCTRECORD acctById = getAccountByIdClient.GET_ACCOUNT(acctId);  
                Console.WriteLine("Account Returned by Id: AccountId={0}, Name={1}, Balance={2:C}",  
                    acctById.ACCTID, acctById.NAME, acctById.BALANCE);  
  
                /* Get new account by Name */  
                GET_ACCOUNT_BY_NAMEns.ACCTRECORD acctByName = getAccountByNameClient.GET_ACCOUNT(newAccountName);  
                Console.WriteLine("Account Returned by Name: AccountId={0}, Name={1}, Balance={2:C}",  
                    acctByName.ACCTID, acctByName.NAME, acctByName.BALANCE);  
  
                Console.WriteLine("Hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the Oracle Database");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the Oracle Database");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
                throw ex;  
            }  
            finally  
            {  
                // Close all the clients  
                createAccountClient.Close();  
                getAccountByIdClient.Close();  
                getAccountByNameClient.Close();  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8eccd-255">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8eccd-255">See Also</span></span>  
 [<span data-ttu-id="8eccd-256">Développer des Applications de base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="8eccd-256">Develop Oracle Database Applications by Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)