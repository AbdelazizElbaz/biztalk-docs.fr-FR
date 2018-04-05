---
title: Sur le fournisseur de données pour Siebel | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, overview
ms.assetid: 461fe4d8-75f2-49d5-9fc2-3baab4ccf13f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81cac425bf1671166b4f40cecae3e1a3aca1c8e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-data-provider-for-siebel"></a><span data-ttu-id="db689-102">Sur le fournisseur de données pour Siebel</span><span class="sxs-lookup"><span data-stu-id="db689-102">About the Data Provider for Siebel</span></span>
## <a name="overview"></a><span data-ttu-id="db689-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="db689-103">Overview</span></span>
<span data-ttu-id="db689-104">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] repose sur le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db689-104">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] is built on top of the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span> <span data-ttu-id="db689-105">Vous pouvez utiliser le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] à :</span><span class="sxs-lookup"><span data-stu-id="db689-105">You can use the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] to:</span></span>  
  
-   <span data-ttu-id="db689-106">Écrire un client ADO.NET pour se connecter au système Siebel.</span><span class="sxs-lookup"><span data-stu-id="db689-106">Write an ADO.NET client to connect to the Siebel system.</span></span> <span data-ttu-id="db689-107">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] présente certaines classes qui vous permettent d’interagir avec le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="db689-107">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] exposes certain classes that enable you to interface with the provider.</span></span>  
  
-   <span data-ttu-id="db689-108">Exécutez une requête SELECT sur un composant d’entreprise Siebel</span><span class="sxs-lookup"><span data-stu-id="db689-108">Run a SELECT query on a Siebel business component</span></span>
  
-   <span data-ttu-id="db689-109">Exécuter une requête EXEC sur un service d’entreprise Siebel</span><span class="sxs-lookup"><span data-stu-id="db689-109">Run an EXEC query on a Siebel business service</span></span>
  
-   <span data-ttu-id="db689-110">Utilisez le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] avec SQL Server Integration Services (SSIS)</span><span class="sxs-lookup"><span data-stu-id="db689-110">Use the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] with SQL Server Integration Services (SSIS)</span></span>
  
<span data-ttu-id="db689-111">[Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md) est un bon point de départ pour plus d’informations sur :</span><span class="sxs-lookup"><span data-stu-id="db689-111">[Use  the .NET Framework Data Provider for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md) is a great resource for information on:</span></span>  
  
-   <span data-ttu-id="db689-112">Les interfaces ADO.NET étendu par le[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db689-112">The ADO.NET interfaces extended by the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]</span></span>  
  
-   <span data-ttu-id="db689-113">La chaîne de connexion pour se connecter à un système Siebel</span><span class="sxs-lookup"><span data-stu-id="db689-113">The connection string to connect to a Siebel system</span></span>  
  
-   <span data-ttu-id="db689-114">Syntaxe des instructions SELECT et EXEC</span><span class="sxs-lookup"><span data-stu-id="db689-114">Syntax for the SELECT and EXEC statements</span></span>  
  
-   <span data-ttu-id="db689-115">À l’aide de la [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] avec SSIS</span><span class="sxs-lookup"><span data-stu-id="db689-115">Using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] with SSIS</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="db689-116">Limitations</span><span class="sxs-lookup"><span data-stu-id="db689-116">Limitations</span></span>
<span data-ttu-id="db689-117">Les éléments suivants sont connus des limitations de la [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="db689-117">The following are known limitations of the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]:</span></span>  
  
-   <span data-ttu-id="db689-118">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge les alias noms pour les tables dans la clause SELECT, mais pas dans la clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="db689-118">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports alias names for tables in the SELECT clause, but not in the WHERE clause.</span></span>  
  
-   <span data-ttu-id="db689-119">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] ne parvient pas à créer une table avec les noms de colonnes qui ont le caractère spécial, «] ».</span><span class="sxs-lookup"><span data-stu-id="db689-119">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] fails to create a table with column names that have the special character, "]".</span></span> <span data-ttu-id="db689-120">Vous pouvez ignorer le caractère spécial en incluant un autre crochet fermant.</span><span class="sxs-lookup"><span data-stu-id="db689-120">You can escape the special character by including another closing square bracket.</span></span> <span data-ttu-id="db689-121">Par conséquent, vous devez inclure »]] » au lieu de «] ».</span><span class="sxs-lookup"><span data-stu-id="db689-121">So, you should include"]]" instead of "]".</span></span>  
  
-   <span data-ttu-id="db689-122">En raison de problèmes de délai d’attente un traitement par le client Siebel sous-jacent API, le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] ne prend pas en charge le délai d’attente de connexion et de commande.</span><span class="sxs-lookup"><span data-stu-id="db689-122">Due to issues with timeout handling by the underlying Siebel client API, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] does not support command and connection timeout.</span></span>  
  
-   <span data-ttu-id="db689-123">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] ne prend pas en charge le comportement asynchrone de la commande.</span><span class="sxs-lookup"><span data-stu-id="db689-123">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] does not support asynchronous command behavior.</span></span>  
  
-   <span data-ttu-id="db689-124">Lorsqu’il est utilisé avec un projet SQL Server Integration Services (SSIS), le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] ne parvient pas à récupérer des données pour les colonnes qui contiennent des valeurs avec plus de 8 000 caractères.</span><span class="sxs-lookup"><span data-stu-id="db689-124">When used with a SQL Server Integration Services (SSIS) project, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] fails to retrieve data for columns that contain values with more than 8000 characters.</span></span> <span data-ttu-id="db689-125">Il s’agit en raison d’une restriction SSIS en fonction desquelles :</span><span class="sxs-lookup"><span data-stu-id="db689-125">This is due to an SSIS restriction according to which:</span></span>  
  
    -   <span data-ttu-id="db689-126">Les valeurs supérieures à 4 000 caractères dans la variable SSIS ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="db689-126">Values greater than 4000 characters in SSIS variable are not supported.</span></span>  
  
    -   <span data-ttu-id="db689-127">Les valeurs supérieures à 4 000 caractères larges ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="db689-127">Values greater than 4000 wide characters are not supported.</span></span>  
  
    -   <span data-ttu-id="db689-128">Les valeurs supérieures à 8 000 caractères codés sur un octet ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="db689-128">Values greater than 8000 single-byte characters are not supported.</span></span>  
  
-   <span data-ttu-id="db689-129">L’opération EXEC ne sera pas fonctionnelle lors de l’utilisation du [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] avec SQL Server Integration Services (SSIS).</span><span class="sxs-lookup"><span data-stu-id="db689-129">The EXEC operation will not be functional while using the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] with SQL Server Integration Services (SSIS).</span></span> <span data-ttu-id="db689-130">Par exemple, les clients de l’adaptateur ne pourra donc en mesure d’exécuter un service d’entreprise dans Siebel (à l’aide de [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) tout en utilisant les fournisseurs de données avec SSIS.</span><span class="sxs-lookup"><span data-stu-id="db689-130">So, for example, adapter clients will not be able to execute a business service in Siebel (using [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) while using the data providers with SSIS.</span></span> 

## <a name="see-also"></a><span data-ttu-id="db689-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db689-131">See also</span></span>
[<span data-ttu-id="db689-132">Limitations de l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="db689-132">Limitations of the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/limitations-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
[<span data-ttu-id="db689-133">Dépanner l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="db689-133">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)