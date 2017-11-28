---
title: "Les opérations sont prises en charge par l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64cd124a-5e7f-4ee8-85d3-f9540b25d766
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7236c21f1e298f2ccd4cbb97db481cbd3626d186
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="fbc65-102">Les opérations sont prises en charge par l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="fbc65-102">What operations are supported by the Oracle E-Business Suite adapter</span></span>
## <a name="overview"></a><span data-ttu-id="fbc65-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="fbc65-103">Overview</span></span>
<span data-ttu-id="fbc65-104">Les clients de carte peuvent effectuer des opérations dans Oracle E-Business Suite par :</span><span class="sxs-lookup"><span data-stu-id="fbc65-104">Adapter clients can perform operations in Oracle E-Business Suite by:</span></span>  
  
-   <span data-ttu-id="fbc65-105">Création de projets BizTalk</span><span class="sxs-lookup"><span data-stu-id="fbc65-105">Creating BizTalk projects</span></span>  
  
-   <span data-ttu-id="fbc65-106">À l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="fbc65-106">Using the WCF channel model</span></span>  
  
-   <span data-ttu-id="fbc65-107">À l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="fbc65-107">Using the WCF service model</span></span>  
  
 <span data-ttu-id="fbc65-108">Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications.</span><span class="sxs-lookup"><span data-stu-id="fbc65-108">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="fbc65-109">Ces opérations sont appelées en envoyant des messages SOAP sur un canal.</span><span class="sxs-lookup"><span data-stu-id="fbc65-109">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="fbc65-110">Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.</span><span class="sxs-lookup"><span data-stu-id="fbc65-110">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="fbc65-111">Pour plus d’informations sur la structure du message et l’action SOAP associée à chaque opération, consultez [messages et des schémas de message pour l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="fbc65-111">For information about the message structure and the SOAP action associated with each operation, see [messages and message schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).</span></span>  
  
 <span data-ttu-id="fbc65-112">Cette section fournit des informations sur les opérations prises en charge dans Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbc65-112">This section provides information about the operations supported in Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fbc65-113">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="fbc65-113">In this section</span></span>  
  
-   [<span data-ttu-id="fbc65-114">Définir le contexte de l’Application</span><span class="sxs-lookup"><span data-stu-id="fbc65-114">Set Application Context</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)  
  
-   [<span data-ttu-id="fbc65-115">Opérations sur les Tables d’Interface et les vues de l’Interface</span><span class="sxs-lookup"><span data-stu-id="fbc65-115">Operations on Interface Tables and Interface Views</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)  
  
-   [<span data-ttu-id="fbc65-116">Opérations sur les API PL/SQL</span><span class="sxs-lookup"><span data-stu-id="fbc65-116">Operations on PL/SQL APIs</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-pl-sql-apis.md)  
  
-   [<span data-ttu-id="fbc65-117">Opérations sur les programmes simultanés</span><span class="sxs-lookup"><span data-stu-id="fbc65-117">Operations on Concurrent Programs</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)  
  
-   [<span data-ttu-id="fbc65-118">Opérations sur des ensembles de demande</span><span class="sxs-lookup"><span data-stu-id="fbc65-118">Operations on Request Sets</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md)  
  
-   [<span data-ttu-id="fbc65-119">Opérations sur les Tables d’Interface, les vues de l’Interface, les Tables et les vues qui contiennent des données LOB</span><span class="sxs-lookup"><span data-stu-id="fbc65-119">Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)  
  
-   [<span data-ttu-id="fbc65-120">Opérations sur les Tables qui contiennent des Types de données BFILE</span><span class="sxs-lookup"><span data-stu-id="fbc65-120">Operations on Tables That Contain BFILE Data Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)  
  
-   [<span data-ttu-id="fbc65-121">Opérations sur les fonctions et procédures stockées</span><span class="sxs-lookup"><span data-stu-id="fbc65-121">Operations on Functions and Stored Procedures</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-stored-procedures1.md)  
  
-   [<span data-ttu-id="fbc65-122">Opérations sur les fonctions et procédures avec des paramètres REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="fbc65-122">Operations on Functions and Procedures with REF CURSOR Parameters</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)  
  
-   [<span data-ttu-id="fbc65-123">Opérations sur les fonctions et procédures avec des Types d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="fbc65-123">Operations on Functions and Procedures with RECORD Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
-   [<span data-ttu-id="fbc65-124">Opérations sur les synonymes</span><span class="sxs-lookup"><span data-stu-id="fbc65-124">Operations on Synonyms</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-synonyms2.md)  
  
-   [<span data-ttu-id="fbc65-125">Considération pour recevoir des Notifications de modification de base de données</span><span class="sxs-lookup"><span data-stu-id="fbc65-125">Consideration for Receiving Database Change Notifications</span></span>](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [<span data-ttu-id="fbc65-126">Prise en charge pour les appels entrants à l’aide de l’interrogation</span><span class="sxs-lookup"><span data-stu-id="fbc65-126">Support for Inbound Calls Using Polling</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)  
  
-   [<span data-ttu-id="fbc65-127">Prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et</span><span class="sxs-lookup"><span data-stu-id="fbc65-127">Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)  
  
-   [<span data-ttu-id="fbc65-128">Prise en charge des opérations composites</span><span class="sxs-lookup"><span data-stu-id="fbc65-128">Support for Composite Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md)  
  
-   [<span data-ttu-id="fbc65-129">Prise en charge pour les Types définis par l’utilisateur Oracle</span><span class="sxs-lookup"><span data-stu-id="fbc65-129">Support for Oracle User-Defined Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-oracle-user-defined-types2.md)  
  
## <a name="see-also"></a><span data-ttu-id="fbc65-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbc65-130">See Also</span></span>  
[<span data-ttu-id="fbc65-131">Comprendre l’adaptateur BizTalk pour Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="fbc65-131">Understand BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)