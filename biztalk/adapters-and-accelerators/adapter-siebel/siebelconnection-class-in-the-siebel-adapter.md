---
title: "Classe SiebelConnection dans l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, SiebelConnection
- SiebelConnection, supported properties and methods
- SiebelConnection
ms.assetid: 661d9876-4c14-4748-b05f-cc4fd1c4ebcf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fc99c2e3f019f2ddf88647b0faeb7e41644fd0e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="siebelconnection-class-in-the-siebel-adapter"></a><span data-ttu-id="01e3f-102">Classe SiebelConnection dans l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="01e3f-102">SiebelConnection class in the Siebel adapter</span></span>
<span data-ttu-id="01e3f-103">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] accède à sous-jacent [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] `Binding`, le `ConnectionFactory`, et `Channel` pour se connecter au système Siebel.</span><span class="sxs-lookup"><span data-stu-id="01e3f-103">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] accesses the underlying [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]`Binding`, the `ConnectionFactory`, and `Channel` to connect to the Siebel system.</span></span> <span data-ttu-id="01e3f-104">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] implémente la `DbConnection` fonctionnalités de la classe pour prendre en charge de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="01e3f-104">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] implements the `DbConnection` class to support the preceding features.</span></span>  
  
 <span data-ttu-id="01e3f-105">À l’aide d’une instance de `Microsoft.Data.SiebelClient.SiebelClientFactory`, un programme client peut obtenir une instance de la `System.Data.Common.DbConnection` classe pour se connecter au système Siebel.</span><span class="sxs-lookup"><span data-stu-id="01e3f-105">Using an instance of `Microsoft.Data.SiebelClient.SiebelClientFactory`, a client program can obtain an instance of the `System.Data.Common.DbConnection` class to connect to the Siebel system.</span></span>  
  
```  
//In this example, factory is an instance of SiebelClientFactory  
DbConnection connection = factory.CreateConnection();  
```  
  
 <span data-ttu-id="01e3f-106">L’approche suivante peut également être utilisée pour créer une connexion :</span><span class="sxs-lookup"><span data-stu-id="01e3f-106">Alternatively, the following approach can be used to create a connection:</span></span>  
  
```  
  
SiebelConnection connection = new SiebelConnection();  
connection.ConnectionString = connectionString;  
```  
  
 <span data-ttu-id="01e3f-107">Le `SiebelConnection` hérite de la classe `DbConnection`.</span><span class="sxs-lookup"><span data-stu-id="01e3f-107">The `SiebelConnection` class inherits from `DbConnection`.</span></span> <span data-ttu-id="01e3f-108">Il existe dans l’espace de noms `Microsoft.Data.SiebelClient`.</span><span class="sxs-lookup"><span data-stu-id="01e3f-108">It exists in the namespace `Microsoft.Data.SiebelClient`.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="01e3f-109">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="01e3f-109">Supported Properties</span></span>  
 <span data-ttu-id="01e3f-110">Le `SiebelConnection` classe prend en charge les éléments suivants `DbConnection` propriétés.</span><span class="sxs-lookup"><span data-stu-id="01e3f-110">The `SiebelConnection` class supports the following `DbConnection` properties.</span></span>  
  
|<span data-ttu-id="01e3f-111">Nom</span><span class="sxs-lookup"><span data-stu-id="01e3f-111">Name</span></span>|<span data-ttu-id="01e3f-112">Get/Set.</span><span class="sxs-lookup"><span data-stu-id="01e3f-112">Get/Set</span></span>|<span data-ttu-id="01e3f-113"> Description</span><span class="sxs-lookup"><span data-stu-id="01e3f-113">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="01e3f-114">**ConnectionString**</span><span class="sxs-lookup"><span data-stu-id="01e3f-114">**ConnectionString**</span></span>|<span data-ttu-id="01e3f-115">Get et Set</span><span class="sxs-lookup"><span data-stu-id="01e3f-115">Get and Set</span></span>|<span data-ttu-id="01e3f-116">Obtient ou définit la chaîne utilisée pour ouvrir la connexion.</span><span class="sxs-lookup"><span data-stu-id="01e3f-116">Gets or sets the string used to open the connection.</span></span>|  
|<span data-ttu-id="01e3f-117">**Base de données**</span><span class="sxs-lookup"><span data-stu-id="01e3f-117">**Database**</span></span>|<span data-ttu-id="01e3f-118">Obtenir</span><span class="sxs-lookup"><span data-stu-id="01e3f-118">Get</span></span>|<span data-ttu-id="01e3f-119">Obtient le nom de la base de données actuelle après l’ouverture d’une connexion, ou le nom de base de données spécifié dans la chaîne de connexion avant que la connexion est ouverte.</span><span class="sxs-lookup"><span data-stu-id="01e3f-119">Gets the name of the current database after a connection is opened, or the database name specified in the connection string before the connection is opened.</span></span> <span data-ttu-id="01e3f-120">Il doit s’agir du nom de référentiel Siebel.</span><span class="sxs-lookup"><span data-stu-id="01e3f-120">This should be the Siebel repository name.</span></span>|  
|<span data-ttu-id="01e3f-121">**DataSource**</span><span class="sxs-lookup"><span data-stu-id="01e3f-121">**DataSource**</span></span>|<span data-ttu-id="01e3f-122">Obtenir</span><span class="sxs-lookup"><span data-stu-id="01e3f-122">Get</span></span>|<span data-ttu-id="01e3f-123">Obtient le nom de la passerelle Siebel pour cette connexion.</span><span class="sxs-lookup"><span data-stu-id="01e3f-123">Gets the name of the Siebel gateway for this connection.</span></span>|  
|<span data-ttu-id="01e3f-124">**ServerVersion**</span><span class="sxs-lookup"><span data-stu-id="01e3f-124">**ServerVersion**</span></span>|<span data-ttu-id="01e3f-125">Obtenir</span><span class="sxs-lookup"><span data-stu-id="01e3f-125">Get</span></span>|<span data-ttu-id="01e3f-126">Dans la version actuelle de [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], cette propriété retourne une valeur codée en dur, qui ne représente pas la version du serveur Siebel.</span><span class="sxs-lookup"><span data-stu-id="01e3f-126">In the current version of [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], this property returns a hard-coded value, which does not represent the actual version of the Siebel server.</span></span>|  
|<span data-ttu-id="01e3f-127">**État**</span><span class="sxs-lookup"><span data-stu-id="01e3f-127">**State**</span></span>|<span data-ttu-id="01e3f-128">Obtenir</span><span class="sxs-lookup"><span data-stu-id="01e3f-128">Get</span></span>|<span data-ttu-id="01e3f-129">Obtient une chaîne qui décrit l'état de la connexion.</span><span class="sxs-lookup"><span data-stu-id="01e3f-129">Gets a string that describes the state of the connection.</span></span> <span data-ttu-id="01e3f-130">Il peut contenir trois valeurs possibles : ouvrir, interrompue ou fermé.</span><span class="sxs-lookup"><span data-stu-id="01e3f-130">This can contain three possible values: OPEN, BROKEN, or CLOSED.</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="01e3f-131">Méthodes prises en charge</span><span class="sxs-lookup"><span data-stu-id="01e3f-131">Supported Methods</span></span>  
 <span data-ttu-id="01e3f-132">Le `SiebelConnection` classe prend en charge les éléments suivants `DbConnection` méthodes.</span><span class="sxs-lookup"><span data-stu-id="01e3f-132">The `SiebelConnection` class supports the following `DbConnection` methods.</span></span>  
  
|<span data-ttu-id="01e3f-133">Nom</span><span class="sxs-lookup"><span data-stu-id="01e3f-133">Name</span></span>|<span data-ttu-id="01e3f-134"> Description</span><span class="sxs-lookup"><span data-stu-id="01e3f-134">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="01e3f-135">**CreateDbCommand**</span><span class="sxs-lookup"><span data-stu-id="01e3f-135">**CreateDbCommand**</span></span>|<span data-ttu-id="01e3f-136">Cette méthode protégée fournit une nouvelle instance de la commande DbCommand.</span><span class="sxs-lookup"><span data-stu-id="01e3f-136">This protected method provides a new DbCommand instance.</span></span>|  
|<span data-ttu-id="01e3f-137">**ChangeDatabase**</span><span class="sxs-lookup"><span data-stu-id="01e3f-137">**ChangeDatabase**</span></span>|<span data-ttu-id="01e3f-138">Cette méthode publique n’est pas prise en charge et lève une exception si elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="01e3f-138">This public method is not supported, and will throw an exception if called.</span></span>|  
|<span data-ttu-id="01e3f-139">**Ouvrir**</span><span class="sxs-lookup"><span data-stu-id="01e3f-139">**Open**</span></span>|<span data-ttu-id="01e3f-140">Ouvre une connexion avec le système Siebel en créant un canal WCF.</span><span class="sxs-lookup"><span data-stu-id="01e3f-140">Opens a connection with the Siebel system by creating a WCF channel.</span></span>|  
|<span data-ttu-id="01e3f-141">**Fermer**</span><span class="sxs-lookup"><span data-stu-id="01e3f-141">**Close**</span></span>|<span data-ttu-id="01e3f-142">Ferme une connexion avec le système Siebel en fermant un canal WCF.</span><span class="sxs-lookup"><span data-stu-id="01e3f-142">Closes a connection with the Siebel system by closing a WCF channel.</span></span>|  
|<span data-ttu-id="01e3f-143">**CreateCommand**</span><span class="sxs-lookup"><span data-stu-id="01e3f-143">**CreateCommand**</span></span>|<span data-ttu-id="01e3f-144">Crée un objet de commande.</span><span class="sxs-lookup"><span data-stu-id="01e3f-144">Creates a command object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01e3f-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01e3f-145">See Also</span></span>  
 [<span data-ttu-id="01e3f-146">Étendre des Interfaces ADO.NET avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="01e3f-146">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)