---
title: "Prise en main l’adaptateur BizTalk pour SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c3b6e36-ddfb-4ede-adf5-b9762231224b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61a2ecd7ae8020865dff7b67fbc57388d1f15af6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-the-biztalk-adapter-for-sql"></a><span data-ttu-id="5d784-102">Prise en main l’adaptateur BizTalk pour SQL</span><span class="sxs-lookup"><span data-stu-id="5d784-102">Get started with the BizTalk adapter for SQL</span></span>

  
 <span data-ttu-id="5d784-103">Cette section fournit une vue d’ensemble de l’adaptateur, les conditions préalables et les rubriques pour les utilisateurs qui sont nouveaux pour Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5d784-103">This section provides an overview of the adapter, prerequisites, and topics for users who are new to Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="5d784-104">Il traite des fonctionnalités de [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] et les différentes opérations qui peuvent être effectuées sur la base de données SQL Server à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="5d784-104">It discusses the features of [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] and the different operations that can be performed on the SQL Server database by using the adapter.</span></span>  
  
 <span data-ttu-id="5d784-105">Qu’est un adaptateur ?</span><span class="sxs-lookup"><span data-stu-id="5d784-105">What is an adapter?</span></span> <span data-ttu-id="5d784-106">Un adaptateur est un composant logiciel qui vous permet d’envoyer et recevoir des messages vers et depuis un système de métier (LOB).</span><span class="sxs-lookup"><span data-stu-id="5d784-106">An adapter is a software component that enables you to send and receive messages to and from a line-of-business (LOB) system.</span></span> <span data-ttu-id="5d784-107">L’objectif de conception principale d’un adaptateur est de faciliter l’échange de documents entre partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="5d784-107">The primary design goal of an adapter is to facilitate the exchange of business documents between trading partners.</span></span> <span data-ttu-id="5d784-108">Étant donné que chaque système d’entreprise peut-être adhérer aux protocoles et formats de document spécifique, l’adaptateur doit utiliser un mécanisme de remise qui est conforme aux normes communément reconnus et protocoles pour fournir une interface uniforme pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5d784-108">Because each business system may adhere to specific document formats and protocols, the adapter must use a delivery mechanism that conforms to commonly recognized standards and protocols to provide a uniform interface to the users.</span></span>  
  
 <span data-ttu-id="5d784-109">Les adaptateurs dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] peut être divisé en deux grandes catégories :</span><span class="sxs-lookup"><span data-stu-id="5d784-109">The adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] can be divided into two broad categories:</span></span>  
  
-   <span data-ttu-id="5d784-110">**Adaptateurs LOB**.</span><span class="sxs-lookup"><span data-stu-id="5d784-110">**LOB adapters**.</span></span> <span data-ttu-id="5d784-111">Ces adaptateurs fournissent le modèle de programmation orientée service à l’accès des systèmes métier, par exemple, les adaptateurs pour SAP ou Siebel.</span><span class="sxs-lookup"><span data-stu-id="5d784-111">Such adapters provide service-oriented programming model to access LOB systems—for example, adapters for SAP or Siebel.</span></span>  
  
-   <span data-ttu-id="5d784-112">**Les adaptateurs de données**.</span><span class="sxs-lookup"><span data-stu-id="5d784-112">**Data adapters**.</span></span> <span data-ttu-id="5d784-113">Ces adaptateurs fournissent le modèle de programmation orientée service aux bases de données, par exemple, les adaptateurs pour la base de données Oracle ou SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5d784-113">Such adapters provide service-oriented programming model to access databases—for example, adapters for the Oracle database or SQL Server.</span></span>  
  
 <span data-ttu-id="5d784-114">Il existe cinq adaptateurs dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="5d784-114">There are five adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]<span data-ttu-id="5d784-115"> ([!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="5d784-115"> ([!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5d784-116">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est également disponible en dehors de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] comme un adaptateur séparé.</span><span class="sxs-lookup"><span data-stu-id="5d784-116">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is also available outside the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] as a separate adapter.</span></span>  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="5d784-117"> ([!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="5d784-117"> ([!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]).</span></span>  
  
-   [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="5d784-118"> ([!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="5d784-118"> ([!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]).</span></span>  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]<span data-ttu-id="5d784-119"> ([!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="5d784-119"> ([!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]).</span></span>  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]<span data-ttu-id="5d784-120"> ([!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="5d784-120"> ([!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5d784-121">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] n’est pas disponible pour des plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5d784-121">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is not available for 64-bit platforms.</span></span>  
  
 <span data-ttu-id="5d784-122">Si vous ne connaissez déjà pas comment vous décidez d’utiliser l’adaptateur SQL dans votre entreprise, il est recommandé que vous démarrez en explorant les fonctions et fonctionnalités de l’adaptateur décrites dans [comprendre l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="5d784-122">If you do not already know how you want to use the SQL adapter at your company, it is recommended that you start by exploring the features and functionality of the adapter described in [Understand BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5d784-123">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5d784-123">In This Section</span></span>  
  
-   [<span data-ttu-id="5d784-124">Comprendre l’adaptateur BizTalk pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="5d784-124">Understand BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)  
  
-   [<span data-ttu-id="5d784-125">Didacticiels de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="5d784-125">SQL Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sql/sql-adapter-tutorials.md)  
  
-   [<span data-ttu-id="5d784-126">Forum aux Questions</span><span class="sxs-lookup"><span data-stu-id="5d784-126">Frequently Asked Questions</span></span>](../../adapters-and-accelerators/adapter-sql/sql-adapter-faqs.md)