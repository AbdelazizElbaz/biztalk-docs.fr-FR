---
title: "Comprendre l’adaptateur BizTalk pour base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF LOB Adapter SDK
- features of Oracle database adapter
- table
- adapter client
- service model
- WCF
- artifacts
- database tables
- adapters, features
- Windows Communication Foundation
- adapter features
- channel model
ms.assetid: a8691957-0430-4cba-83f8-b60c21a86849
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aee5761ad466f755e2eb944dcfb2526729bea07c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understand-the-biztalk-adapter-for-oracle-database"></a><span data-ttu-id="9770a-102">Comprendre l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="9770a-102">Understand the BizTalk Adapter for Oracle Database</span></span>
<span data-ttu-id="9770a-103">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] permet un accès par programmation orientée service pour pouvoir interagir avec un système externe.</span><span class="sxs-lookup"><span data-stu-id="9770a-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access in order to interact with an external system.</span></span> <span data-ttu-id="9770a-104">Les cartes présentent les avantages suivants aux clients :</span><span class="sxs-lookup"><span data-stu-id="9770a-104">The adapters provide the following advantages to clients:</span></span>  
  
-   <span data-ttu-id="9770a-105">**Expérience de conception cohérente**.</span><span class="sxs-lookup"><span data-stu-id="9770a-105">**Consistent design-time experience**.</span></span> <span data-ttu-id="9770a-106">Les adaptateurs fournissent une expérience au moment du design commune et conviviale pour parcourir, rechercher et récupérer les métadonnées des artefacts LOB.</span><span class="sxs-lookup"><span data-stu-id="9770a-106">The adapters provide a common and user-friendly design-time experience for browsing, searching, and retrieving metadata of LOB artifacts.</span></span>  
  
-   <span data-ttu-id="9770a-107">**Diverses options de programmation**.</span><span class="sxs-lookup"><span data-stu-id="9770a-107">**Varied programming options**.</span></span> <span data-ttu-id="9770a-108">Les adaptateurs fournissent un choix de modèle de programmation y compris le modèle de canal de Windows Communication Foundation (WCF), WCF service services Web de modèle, ADO.NET, ou BizTalk pris en charge les modèles.</span><span class="sxs-lookup"><span data-stu-id="9770a-108">The adapters provide a choice of programming model including the Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, Web services, or BizTalk supported models.</span></span>  
  
-   <span data-ttu-id="9770a-109">**Uniforme d’expérience sur LOB**.</span><span class="sxs-lookup"><span data-stu-id="9770a-109">**Uniform experience across LOBs**.</span></span> <span data-ttu-id="9770a-110">Les adaptateurs de normaliser l’utilisation de WCF et [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]et donc fournir une expérience uniforme d’accéder à n’importe quel système LOB.</span><span class="sxs-lookup"><span data-stu-id="9770a-110">The adapters standardize on using WCF and [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], and hence provide a uniform experience of gaining access to any LOB system.</span></span>  
  
 <span data-ttu-id="9770a-111">Comme indiqué, les adaptateurs sont générés sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9770a-111">As mentioned, the adapters are built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="9770a-112">Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une base commune pour la création d’adaptateurs d’intégration qui consommable une variété d’applications clientes telles que BizTalk Server et Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="9770a-112">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume.</span></span> <span data-ttu-id="9770a-113">Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligne la stratégie de carte avec la stratégie de Services Microsoft en exposant des adaptateurs d’intégration en tant que les canaux de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9770a-113">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligns the adapter strategy with the Microsoft Services strategy by exposing integration adapters as Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="9770a-114">Pour plus d’informations sur la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], consultez la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation.</span><span class="sxs-lookup"><span data-stu-id="9770a-114">For more information about the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], see the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation.</span></span> <span data-ttu-id="9770a-115">Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation est installée avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], généralement sous \<lecteur d’installation > : \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.</span><span class="sxs-lookup"><span data-stu-id="9770a-115">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation is installed along with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], typically under \<installation drive>:\Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.</span></span>  
  
 <span data-ttu-id="9770a-116">Pour effectuer des opérations sur une base de données Oracle, les clients de l’adaptateur doivent avoir accès aux tables appropriées, les fonctions et procédures.</span><span class="sxs-lookup"><span data-stu-id="9770a-116">To perform operations on an Oracle database, adapter clients must have access to relevant tables, functions, and procedures.</span></span> <span data-ttu-id="9770a-117">Les tables de base de données sont l’unité de stockage dans la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="9770a-117">Database tables are the basic unit of storage in the Oracle database.</span></span> <span data-ttu-id="9770a-118">Des applications externes peuvent ajouter ou supprimer des données d’une table à l’aide d’instructions SQL.</span><span class="sxs-lookup"><span data-stu-id="9770a-118">External applications can add or remove data from a table by using SQL statements.</span></span> <span data-ttu-id="9770a-119">Les applications peuvent également accéder aux données dans les tables à l’aide de vues, fonctions et procédures.</span><span class="sxs-lookup"><span data-stu-id="9770a-119">Applications can also access data in the tables by using views, functions, and procedures.</span></span> <span data-ttu-id="9770a-120">Avec [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)], les clients de l’adaptateur peuvent parcourir les artefacts tels que des tables, des procédures, des packages, des vues et des autres éléments de ce type dans une base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="9770a-120">With [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)], adapter clients can browse the artifacts such as tables, procedures, packages, views, and other such items in an Oracle database.</span></span> <span data-ttu-id="9770a-121">Les clients de l’adaptateur peuvent sélectionner les artefacts qu’ils requièrent pour leur solution et récupérer des métadonnées pour ces artefacts.</span><span class="sxs-lookup"><span data-stu-id="9770a-121">Adapter clients can select the artifacts they require for their solution and retrieve metadata for those artifacts.</span></span> <span data-ttu-id="9770a-122">Cela permet aux utilisateurs d’accéder et d’exécuter les opérations sur les artefacts dans la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="9770a-122">This enables users to access and execute the operations on the artifacts in the Oracle database.</span></span>  
  
 <span data-ttu-id="9770a-123">Cette section répertorie les fonctionnalités de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9770a-123">This section lists the features of the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9770a-124">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9770a-124">In This Section</span></span>  
  
-   [<span data-ttu-id="9770a-125">Vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="9770a-125">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)  
  
-   [<span data-ttu-id="9770a-126">Principales fonctionnalités de l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="9770a-126">Key Features in BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md)  
  
-   [<span data-ttu-id="9770a-127">Limitations de l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="9770a-127">Limitations of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/limitations-of-biztalk-adapter-for-oracle-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="9770a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9770a-128">See Also</span></span>  
[<span data-ttu-id="9770a-129">Prise en main de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9770a-129">Getting started with BizTalk Server</span></span>](../../core/getting-started-with-biztalk-server.md)