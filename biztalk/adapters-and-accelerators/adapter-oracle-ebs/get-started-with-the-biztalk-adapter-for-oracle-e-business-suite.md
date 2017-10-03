---
title: "Prise en main l’adaptateur BizTalk pour Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 852d5855-c58a-4fa3-8efd-6afea9e527df
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84c149c18da6d08283d0969b89a4634581b0001a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-the-biztalk-adapter-for-oracle-e-business-suite"></a><span data-ttu-id="dc048-102">Prise en main l’adaptateur BizTalk pour Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="dc048-102">Get started with the BizTalk Adapter for Oracle E-Business Suite</span></span>
<span data-ttu-id="dc048-103">Vue d’ensemble de l’adaptateur, les conditions préalables et les rubriques pour les utilisateurs qui débutent avec Microsoft BizTalk Adapter Pack.</span><span class="sxs-lookup"><span data-stu-id="dc048-103">Overview of the adapter, prerequisites, and topics for users who are new to Microsoft BizTalk Adapter Pack.</span></span> <span data-ttu-id="dc048-104">Fournit des informations sur les fonctionnalités de [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] et les différentes opérations qui peuvent être effectuées sur la base de données Oracle à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="dc048-104">Information is provided about the features of [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] and the different operations that can be performed on the Oracle database by using the adapter.</span></span>  
  
## <a name="what-is-an-adapter"></a><span data-ttu-id="dc048-105">Qu’est un adaptateur ?</span><span class="sxs-lookup"><span data-stu-id="dc048-105">What is an adapter?</span></span>  
  
 <span data-ttu-id="dc048-106">Un adaptateur est un composant logiciel qui vous permet d’envoyer et recevoir des messages vers et depuis un système de métier (LOB).</span><span class="sxs-lookup"><span data-stu-id="dc048-106">An adapter is a software component that enables you to send and receive messages to and from a line-of-business (LOB) system.</span></span> <span data-ttu-id="dc048-107">L’objectif principal d’un adaptateur est de faciliter l’échange de documents entre partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="dc048-107">The primary goal of an adapter is to facilitate the exchange of business documents between trading partners.</span></span> <span data-ttu-id="dc048-108">Étant donné que chaque système d’entreprise peut-être adhérer aux protocoles et formats de document spécifique, l’adaptateur doit utiliser un mécanisme de remise qui est conforme aux normes communément reconnus et protocoles pour fournir une interface uniforme pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="dc048-108">Because each business system may adhere to specific document formats and protocols, the adapter must use a delivery mechanism that conforms to commonly recognized standards and protocols to provide a uniform interface to the users.</span></span>  
  
 <span data-ttu-id="dc048-109">Les adaptateurs dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] peut être divisé en deux grandes catégories :</span><span class="sxs-lookup"><span data-stu-id="dc048-109">The adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] can be divided into two broad categories:</span></span>  
  
-   <span data-ttu-id="dc048-110">**Adaptateurs LOB**: adaptateurs LOB fournissent un modèle de programmation orientée service à l’accès des systèmes métier, par exemple, les adaptateurs pour les applications SAP ou Siebel.</span><span class="sxs-lookup"><span data-stu-id="dc048-110">**LOB adapters**: LOB adapters provide a service-oriented programming model to access LOB systems—for example, adapters for SAP or Siebel applications.</span></span>  
  
-   <span data-ttu-id="dc048-111">**Les adaptateurs de données**: les adaptateurs de données fournissent un modèle de programmation orientée service aux bases de données, par exemple, les adaptateurs pour la base de données Oracle ou SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dc048-111">**Data adapters**: Data adapters provide a service-oriented programming model to access databases — for example, adapters for the Oracle database or SQL Server.</span></span>  
  
 <span data-ttu-id="dc048-112">Il existe cinq adaptateurs dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="dc048-112">There are five adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="dc048-113"> ([!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="dc048-113"> ([!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]<span data-ttu-id="dc048-114"> ([!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="dc048-114"> ([!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="dc048-115"> ([!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="dc048-115"> ([!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]<span data-ttu-id="dc048-116"> ([!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="dc048-116"> ([!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]<span data-ttu-id="dc048-117"> ([!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="dc048-117"> ([!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)])</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dc048-118">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] n’est pas disponible pour des plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="dc048-118">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is not available for 64-bit platforms.</span></span>  
  
 <span data-ttu-id="dc048-119">Si vous ne connaissez pas le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], nous vous recommandons de commencer à Explorer les fonctionnalités et les fonctionnalités de l’adaptateur décrites dans [comprendre l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="dc048-119">If you are new to the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], then we recommend you start by exploring the features and functionality of the adapter described in [Understand BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc048-120">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="dc048-120">In this section</span></span>  
  
-   [<span data-ttu-id="dc048-121">Comprendre l’adaptateur BizTalk pour Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="dc048-121">Understand BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)  
  
-   [<span data-ttu-id="dc048-122">Didacticiel : Présentation des données à partir d’Oracle E-Business Suite sur un SharePoint Site</span><span class="sxs-lookup"><span data-stu-id="dc048-122">Tutorial: Presenting data from Oracle E-Business Suite on a SharePoint Site</span></span>](Tutorial:%20Presenting%20Data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)
  
- [<span data-ttu-id="dc048-123">Dépannage de l’adaptateur Oracle eBusiness Suite</span><span class="sxs-lookup"><span data-stu-id="dc048-123">Troubleshooting the Oracle EBS adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)