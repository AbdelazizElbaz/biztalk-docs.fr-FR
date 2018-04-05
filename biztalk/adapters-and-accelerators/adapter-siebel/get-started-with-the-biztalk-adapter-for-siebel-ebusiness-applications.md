---
title: Prise en main l’adaptateur BizTalk pour Siebel eBusiness Applications | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, about
ms.assetid: 0867f95f-977f-48bf-8c46-70fd6e4df56b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba067d0479bbcdae6d04c3affdcb9ee60e564cc9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-the-biztalk-adapter-for-siebel-ebusiness-applications"></a><span data-ttu-id="3da84-102">Prise en main l’adaptateur BizTalk pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="3da84-102">Get started with the BizTalk Adapter for Siebel eBusiness Applications</span></span>
<span data-ttu-id="3da84-103">Cette section fournit une vue d’ensemble de l’adaptateur, les conditions préalables et les rubriques pour les utilisateurs qui sont nouveaux pour Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3da84-103">This section provides an overview of the adapter, prerequisites, and topics for users who are new to the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="3da84-104">Il traite des fonctionnalités de [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] et les différentes opérations qui peuvent être effectuées sur le système Siebel à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3da84-104">It discusses the features of [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] and the different operations that can be performed on the Siebel system using the adapter.</span></span>  
  
 <span data-ttu-id="3da84-105">Qu’est un adaptateur ?</span><span class="sxs-lookup"><span data-stu-id="3da84-105">What is an adapter?</span></span> <span data-ttu-id="3da84-106">Un adaptateur est un composant logiciel qui vous permet d’envoyer et recevoir des messages vers et depuis un système de métier (LOB).</span><span class="sxs-lookup"><span data-stu-id="3da84-106">An adapter is a software component that enables you to send and receive messages to and from a line-of-business (LOB) system.</span></span> <span data-ttu-id="3da84-107">L’objectif de conception principale des cartes est de faciliter l’échange de documents entre partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="3da84-107">The primary design goal of adapters is to facilitate the exchange of business documents between trading partners.</span></span> <span data-ttu-id="3da84-108">Étant donné que chaque système d’entreprise peut-être adhérer aux protocoles et formats de document spécifique, l’adaptateur doit utiliser un mécanisme de remise qui est conforme aux normes communément reconnus et protocoles.</span><span class="sxs-lookup"><span data-stu-id="3da84-108">Because each business system may adhere to specific document formats and protocols, the adapter must use a delivery mechanism that conforms to commonly recognized standards and protocols.</span></span>  
  
 <span data-ttu-id="3da84-109">Les adaptateurs peuvent être divisés en deux grandes catégories :</span><span class="sxs-lookup"><span data-stu-id="3da84-109">The adapters can be divided into two broad categories:</span></span>  
  
-   <span data-ttu-id="3da84-110">**Adaptateurs LOB**.</span><span class="sxs-lookup"><span data-stu-id="3da84-110">**LOB adapters**.</span></span> <span data-ttu-id="3da84-111">Ces adaptateurs fournissent un modèle de programmation orientée service à l’accès des systèmes métier, par exemple, les adaptateurs pour SAP ou Siebel.</span><span class="sxs-lookup"><span data-stu-id="3da84-111">Such adapters provide a service-oriented programming model to access LOB systems—for example, adapters for SAP or Siebel.</span></span>  
  
-   <span data-ttu-id="3da84-112">**Les adaptateurs de données**.</span><span class="sxs-lookup"><span data-stu-id="3da84-112">**Data adapters**.</span></span> <span data-ttu-id="3da84-113">Ces adaptateurs fournissent un modèle de programmation orientée service aux bases de données, par exemple, un adaptateur pour la base de données Oracle ou SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3da84-113">Such adapters provide a service-oriented programming model to access databases—for example, an adapter for the Oracle database or SQL Server.</span></span>  
  
 <span data-ttu-id="3da84-114">Il existe cinq adaptateurs dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3da84-114">There are five adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]<span data-ttu-id="3da84-115">(la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="3da84-115"> (the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="3da84-116">(la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="3da84-116"> (the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="3da84-117">(la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="3da84-117"> (the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]<span data-ttu-id="3da84-118">(le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]), y compris [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="3da84-118"> (the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]), including [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]<span data-ttu-id="3da84-119">(le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]), y compris [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="3da84-119"> (the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]), including [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3da84-120">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] n’est pas disponible pour des plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="3da84-120">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is not available for 64-bit platforms.</span></span>  
  
 <span data-ttu-id="3da84-121">Si vous ne connaissez pas déjà comment vous décidez d’utiliser le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] dans votre entreprise, il est recommandé que vous démarrez en explorant les fonctions et fonctionnalités de l’adaptateur décrites dans [vue d’ensemble de l’adaptateur BizTalk pour Siebel eBusiness Applications ](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md).</span><span class="sxs-lookup"><span data-stu-id="3da84-121">If you do not already know how you want to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] at your company, it is recommended that you start by exploring the features and functionality of the adapter described in [Overview of BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3da84-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3da84-122">In This Section</span></span>  
  
-   [<span data-ttu-id="3da84-123">Comprendre l’adaptateur BizTalk pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="3da84-123">Understand BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md) 
  
-   [<span data-ttu-id="3da84-124">Didacticiels de l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="3da84-124">Siebel Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-siebel/siebel-adapter-tutorials.md)  
  
-   [<span data-ttu-id="3da84-125">Ressources de la Communauté</span><span class="sxs-lookup"><span data-stu-id="3da84-125">Community Resources</span></span>](http://msdn.microsoft.com/library/ff5ec978-8cdd-418a-a25e-fd3746b64d8b)  
  
-   [<span data-ttu-id="3da84-126">Forum aux Questions</span><span class="sxs-lookup"><span data-stu-id="3da84-126">Frequently Asked Questions</span></span>](http://msdn.microsoft.com/library/66953c15-08c5-48ac-a4ff-a72a82174f15)