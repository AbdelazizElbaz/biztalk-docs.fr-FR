---
title: "Classe SiebelCommand dans l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SiebelCommand
- Data Provider for Siebel, SiebelCommand
- SiebelCommand, supported methods and properties
ms.assetid: 7cba0e47-634b-4878-b480-80fbcbbf5c90
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d268e9a1d5954d703d392070a53c84bd9cee0d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="siebelcommand-class-in-the-siebel-adapter"></a><span data-ttu-id="a6476-102">Classe SiebelCommand dans l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="a6476-102">SiebelCommand class in the Siebel adapter</span></span>
<span data-ttu-id="a6476-103">Après avoir établi une connexion avec le système Siebel, le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] analyse les chaînes de commande Siebel et les paramètres de commande fournis par le client ADO.NET et mappe la commande dans un message de demande WCF.</span><span class="sxs-lookup"><span data-stu-id="a6476-103">After establishing a connection with the Siebel system, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] parses the Siebel command strings and command parameters provided by the ADO.NET client and maps the command into a WCF request message.</span></span> <span data-ttu-id="a6476-104">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] puis envoie la demande à la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et obtient la réponse XML et le contenu du corps de la carte.</span><span class="sxs-lookup"><span data-stu-id="a6476-104">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] then sends the request to the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and obtains the response XML and the body contents from the adapter.</span></span> <span data-ttu-id="a6476-105">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] utilise ensuite le `XMLDataReader` pour récupérer les données relationnelles à partir du corps XML.</span><span class="sxs-lookup"><span data-stu-id="a6476-105">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] then uses the `XMLDataReader` to retrieve the relational data from the XML body.</span></span>  
  
 <span data-ttu-id="a6476-106">À l’aide d’une instance de `Microsoft.Data.SiebelClient.SiebelClientFactory`, un programme client peut obtenir une instance de la `System.Data.Common.DbCommand` classe pour construire une commande Siebel.</span><span class="sxs-lookup"><span data-stu-id="a6476-106">Using an instance of `Microsoft.Data.SiebelClient.SiebelClientFactory`, a client program can obtain an instance of the `System.Data.Common.DbCommand` class to construct a Siebel command.</span></span>  
  
```  
//In this example, factory is an instance of SiebelClientFactory  
DbCommand command = factory.CreateCommand();  
```  
  
 <span data-ttu-id="a6476-107">L’approche suivante peut également être utilisée pour créer une commande :</span><span class="sxs-lookup"><span data-stu-id="a6476-107">Alternatively, the following approach can be used to create a command:</span></span>  
  
```  
//Here connection is an instance of SiebelConnection  
SiebelCommand cmd = (SiebelCommand) connection.CreateCommand();  
cmd.CommandText = "SELECT [Name] as MyName, [City], [Country]  from Account.Account WHERE Name LIKE '3Com*' OPTION 'ViewMode 1'";  
```  
  
 <span data-ttu-id="a6476-108">Le `SiebelCommand` hérite de la classe `DbCommand`.</span><span class="sxs-lookup"><span data-stu-id="a6476-108">The `SiebelCommand` class inherits from `DbCommand`.</span></span>  <span data-ttu-id="a6476-109">Il existe dans l’espace de noms `Microsoft.Data.SiebelClient`.</span><span class="sxs-lookup"><span data-stu-id="a6476-109">It exists in the namespace `Microsoft.Data.SiebelClient`.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="a6476-110">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="a6476-110">Supported Properties</span></span>  
 <span data-ttu-id="a6476-111">Le **SiebelCommand** classe prend en charge les éléments suivants `DbCommand` *protégé* propriétés :</span><span class="sxs-lookup"><span data-stu-id="a6476-111">The **SiebelCommand** class supports the following `DbCommand`*protected* properties:</span></span>  
  
|<span data-ttu-id="a6476-112">Nom</span><span class="sxs-lookup"><span data-stu-id="a6476-112">Name</span></span>|<span data-ttu-id="a6476-113">Get/Set.</span><span class="sxs-lookup"><span data-stu-id="a6476-113">Get/Set</span></span>|<span data-ttu-id="a6476-114"> Description</span><span class="sxs-lookup"><span data-stu-id="a6476-114">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="a6476-115">**DbConnection**</span><span class="sxs-lookup"><span data-stu-id="a6476-115">**DbConnection**</span></span>|<span data-ttu-id="a6476-116">Get et Set</span><span class="sxs-lookup"><span data-stu-id="a6476-116">Get and Set</span></span>|<span data-ttu-id="a6476-117">Il doit contenir sous-jacent `DbConnection` instance à partir duquel le `DbCommand` instance est obtenue.</span><span class="sxs-lookup"><span data-stu-id="a6476-117">This should contain the underlying `DbConnection` instance from which this `DbCommand` instance is obtained.</span></span>|  
|<span data-ttu-id="a6476-118">**DbParameterCollection**</span><span class="sxs-lookup"><span data-stu-id="a6476-118">**DbParameterCollection**</span></span>|<span data-ttu-id="a6476-119">Obtenir</span><span class="sxs-lookup"><span data-stu-id="a6476-119">Get</span></span>|<span data-ttu-id="a6476-120">Obtient la collection de `DbParameter` objets.</span><span class="sxs-lookup"><span data-stu-id="a6476-120">Gets the collection of `DbParameter` objects.</span></span>|  
  
 <span data-ttu-id="a6476-121">`SiebelCommand`prend également en charge les éléments suivants `DbCommand` *public* propriétés :</span><span class="sxs-lookup"><span data-stu-id="a6476-121">`SiebelCommand` also supports the following `DbCommand`*public* properties:</span></span>  
  
|<span data-ttu-id="a6476-122">Nom</span><span class="sxs-lookup"><span data-stu-id="a6476-122">Name</span></span>|<span data-ttu-id="a6476-123">Get/Set.</span><span class="sxs-lookup"><span data-stu-id="a6476-123">Get/Set</span></span>|<span data-ttu-id="a6476-124"> Description</span><span class="sxs-lookup"><span data-stu-id="a6476-124">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="a6476-125">**CommandText**</span><span class="sxs-lookup"><span data-stu-id="a6476-125">**CommandText**</span></span>|<span data-ttu-id="a6476-126">Get et Set</span><span class="sxs-lookup"><span data-stu-id="a6476-126">Get and Set</span></span>|<span data-ttu-id="a6476-127">Il contient l’instruction SQL qui ADO.NET souhaite exécuter.</span><span class="sxs-lookup"><span data-stu-id="a6476-127">This contain the SQL statement that the ADO.NET client wishes to execute.</span></span>|  
|<span data-ttu-id="a6476-128">**CommandType**</span><span class="sxs-lookup"><span data-stu-id="a6476-128">**CommandType**</span></span>|<span data-ttu-id="a6476-129">Get et Set</span><span class="sxs-lookup"><span data-stu-id="a6476-129">Get and Set</span></span>|<span data-ttu-id="a6476-130">Uniquement `CommandType.Text` est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a6476-130">Only `CommandType.Text` is supported.</span></span>|  
|<span data-ttu-id="a6476-131">**Connexion**</span><span class="sxs-lookup"><span data-stu-id="a6476-131">**Connection**</span></span>|<span data-ttu-id="a6476-132">Get et Set</span><span class="sxs-lookup"><span data-stu-id="a6476-132">Get and Set</span></span>|<span data-ttu-id="a6476-133">Cette méthode utilise le `DbConnection` membre.</span><span class="sxs-lookup"><span data-stu-id="a6476-133">This uses the `DbConnection` member.</span></span>|  
|<span data-ttu-id="a6476-134">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="a6476-134">**Parameters**</span></span>|<span data-ttu-id="a6476-135">Obtenir</span><span class="sxs-lookup"><span data-stu-id="a6476-135">Get</span></span>|<span data-ttu-id="a6476-136">Cette méthode utilise le `DbParameterCollection` membre.</span><span class="sxs-lookup"><span data-stu-id="a6476-136">This uses the `DbParameterCollection` member.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="a6476-137">Le `SiebelCommand` classe ignore la `CommandTimeout`, `DesignTimeVisible`, et `DbTransaction` propriétés.</span><span class="sxs-lookup"><span data-stu-id="a6476-137">The `SiebelCommand` class ignores the `CommandTimeout`, `DesignTimeVisible`, and `DbTransaction` properties.</span></span>  
  
## <a name="supported-methods"></a><span data-ttu-id="a6476-138">Méthodes prises en charge</span><span class="sxs-lookup"><span data-stu-id="a6476-138">Supported Methods</span></span>  
 <span data-ttu-id="a6476-139">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge les `DbCommand` *protégé* méthodes :</span><span class="sxs-lookup"><span data-stu-id="a6476-139">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports the following `DbCommand`*protected* methods:</span></span>  
  
|<span data-ttu-id="a6476-140">Nom</span><span class="sxs-lookup"><span data-stu-id="a6476-140">Name</span></span>|<span data-ttu-id="a6476-141"> Description</span><span class="sxs-lookup"><span data-stu-id="a6476-141">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="a6476-142">**CreateDbParameter**</span><span class="sxs-lookup"><span data-stu-id="a6476-142">**CreateDbParameter**</span></span>|<span data-ttu-id="a6476-143">Crée un nouveau `DbParameter` instance.</span><span class="sxs-lookup"><span data-stu-id="a6476-143">Creates a new `DbParameter` instance.</span></span>|  
|<span data-ttu-id="a6476-144">**ExecuteDbDataReader**</span><span class="sxs-lookup"><span data-stu-id="a6476-144">**ExecuteDbDataReader**</span></span>|<span data-ttu-id="a6476-145">Il exécute les commandes SELECT et EXEC et retourne un `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="a6476-145">This executes the SELECT and EXEC commands and returns a `DbDataReader`.</span></span>|  
  
 <span data-ttu-id="a6476-146">`SiebelCommand`prend également en charge les éléments suivants `DbCommand` *public* méthodes :</span><span class="sxs-lookup"><span data-stu-id="a6476-146">`SiebelCommand` also supports the following `DbCommand`*public* methods:</span></span>  
  
|<span data-ttu-id="a6476-147">Nom</span><span class="sxs-lookup"><span data-stu-id="a6476-147">Name</span></span>|<span data-ttu-id="a6476-148"> Description</span><span class="sxs-lookup"><span data-stu-id="a6476-148">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="a6476-149">**CreateParameter**</span><span class="sxs-lookup"><span data-stu-id="a6476-149">**CreateParameter**</span></span>|<span data-ttu-id="a6476-150">Crée un nouveau `DbParameter` par le biais de l’instance`CreateDbParameter().`</span><span class="sxs-lookup"><span data-stu-id="a6476-150">Creates a new `DbParameter` instance through `CreateDbParameter().`</span></span>|  
|<span data-ttu-id="a6476-151">**ExecuteReader**</span><span class="sxs-lookup"><span data-stu-id="a6476-151">**ExecuteReader**</span></span>|<span data-ttu-id="a6476-152">Exécute `CommandText` contre le `Connection` et retourne `DbDataReader` via `ExecuteDbDataReader()`.</span><span class="sxs-lookup"><span data-stu-id="a6476-152">Executes `CommandText` against the `Connection` and returns `DbDataReader` through `ExecuteDbDataReader()`.</span></span>|  
|<span data-ttu-id="a6476-153">**Préparer**</span><span class="sxs-lookup"><span data-stu-id="a6476-153">**Prepare**</span></span>|<span data-ttu-id="a6476-154">Cette commande analyse les `CommandText` et génère l’arborescence d’analyse de commande SQL.</span><span class="sxs-lookup"><span data-stu-id="a6476-154">This parses the `CommandText` and builds the SQL command parse tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6476-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6476-155">See Also</span></span>  
 [<span data-ttu-id="a6476-156">Étendre des Interfaces ADO.NET avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="a6476-156">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)