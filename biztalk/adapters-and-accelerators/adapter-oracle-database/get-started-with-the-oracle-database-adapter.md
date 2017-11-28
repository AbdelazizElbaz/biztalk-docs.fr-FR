---
title: "Prise en main la carte de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, about
- data adapter
- LOB adapter
ms.assetid: ed5b3510-11c4-4b10-bf85-c4066f3f80df
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7aa93ae3f64f4f2f914a51508a3a8dee4e3be41
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-the-oracle-database-adapter"></a><span data-ttu-id="369b0-102">Prise en main la carte de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="369b0-102">Get started with the Oracle Database adapter</span></span>
<span data-ttu-id="369b0-103">Cette section fournit une vue d’ensemble de l’adaptateur, les conditions préalables et les rubriques pour les utilisateurs qui sont nouveaux pour Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="369b0-103">This section provides an overview of the adapter, prerequisites, and topics for users who are new to Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="369b0-104">Il traite des fonctionnalités de [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] et les différentes opérations qui peuvent être effectuées sur la base de données Oracle à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="369b0-104">It discusses the features of [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] and the different operations that can be performed on the Oracle database using the adapter.</span></span>  
  
 <span data-ttu-id="369b0-105">Qu’est un adaptateur ?</span><span class="sxs-lookup"><span data-stu-id="369b0-105">What is an adapter?</span></span> <span data-ttu-id="369b0-106">Un adaptateur est un composant logiciel qui vous permet d’envoyer et recevoir des messages vers et depuis un système de métier (LOB).</span><span class="sxs-lookup"><span data-stu-id="369b0-106">An adapter is a software component that enables you to send and receive messages to and from a line-of-business (LOB) system.</span></span> <span data-ttu-id="369b0-107">L’objectif de conception principale des cartes est de faciliter l’échange de documents entre partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="369b0-107">The primary design goal of adapters is to facilitate the exchange of business documents between trading partners.</span></span> <span data-ttu-id="369b0-108">Étant donné que chaque système d’entreprise permettre adhérer aux protocoles et formats de document spécifique, l’adaptateur utilise un mécanisme de remise qui est conforme aux normes communément reconnus et protocoles.</span><span class="sxs-lookup"><span data-stu-id="369b0-108">Because each business system can adhere to specific document formats and protocols, the adapter uses a delivery mechanism that conforms to commonly recognized standards and protocols.</span></span>  
  
 <span data-ttu-id="369b0-109">Les adaptateurs peuvent être divisés en deux grandes catégories :</span><span class="sxs-lookup"><span data-stu-id="369b0-109">The adapters can be divided into two broad categories:</span></span>  
  
-   <span data-ttu-id="369b0-110">**Adaptateurs LOB**.</span><span class="sxs-lookup"><span data-stu-id="369b0-110">**LOB adapters**.</span></span> <span data-ttu-id="369b0-111">Ces adaptateurs fournissent un modèle de programmation orientée service à l’accès des systèmes métier, par exemple, les adaptateurs pour SAP ou Siebel.</span><span class="sxs-lookup"><span data-stu-id="369b0-111">Such adapters provide a service-oriented programming model to access LOB systems—for example, adapters for SAP or Siebel.</span></span>  
  
-   <span data-ttu-id="369b0-112">**Les adaptateurs de données**.</span><span class="sxs-lookup"><span data-stu-id="369b0-112">**Data adapters**.</span></span> <span data-ttu-id="369b0-113">Ces adaptateurs fournissent un modèle de programmation orientée service aux bases de données, par exemple, un adaptateur pour la base de données Oracle ou SQL Server.</span><span class="sxs-lookup"><span data-stu-id="369b0-113">Such adapters provide a service-oriented programming model to access databases—for example, an adapter for the Oracle database or SQL Server.</span></span>  
  
 <span data-ttu-id="369b0-114">Il existe cinq adaptateurs dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="369b0-114">There are five adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]<span data-ttu-id="369b0-115">(la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="369b0-115"> (the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="369b0-116">(la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="369b0-116"> (the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="369b0-117">(la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="369b0-117"> (the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]<span data-ttu-id="369b0-118">(le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]), y compris [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="369b0-118"> (the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]), including [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]<span data-ttu-id="369b0-119">(le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]), y compris [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="369b0-119"> (the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]), including [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="369b0-120">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] n’est pas disponible pour des plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="369b0-120">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is not available for 64-bit platforms.</span></span>  
  
 <span data-ttu-id="369b0-121">Si vous ne connaissez pas déjà comment vous décidez d’utiliser le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] dans votre entreprise, il est recommandé que vous démarrez en explorant les fonctions et fonctionnalités de l’adaptateur décrites dans [présentation de l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="369b0-121">If you do not already know how you want to use the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] at your company, it is recommended that you start by exploring the features and functionality of the adapter described in [Understanding the BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md).</span></span>  
  
