---
title: "Les opérations sont prises en charge par l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP
- operations, performing
ms.assetid: d78dbeb8-9dab-4a71-982e-f7ada51472e8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 014b0fc6158c151d510152550c0093f6ffa9031b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-oracle-database-adapter"></a><span data-ttu-id="bd879-102">Les opérations sont prises en charge par l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd879-102">What operations are supported by the Oracle Database adapter</span></span>
<span data-ttu-id="bd879-103">Les clients de l’adaptateur peuvent effectuer des opérations sur la base de données Oracle en créant les projets BizTalk, en utilisant le modèle de canal WCF ou en utilisant le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="bd879-103">Adapter clients can perform operations on the Oracle database by creating BizTalk projects, by using the WCF channel model, or by using the WCF service model.</span></span> <span data-ttu-id="bd879-104">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications.</span><span class="sxs-lookup"><span data-stu-id="bd879-104">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="bd879-105">Ces opérations sont appelées en envoyant des messages SOAP sur un canal.</span><span class="sxs-lookup"><span data-stu-id="bd879-105">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="bd879-106">Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.</span><span class="sxs-lookup"><span data-stu-id="bd879-106">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="bd879-107">Pour plus d’informations sur la structure du message et l’action SOAP associée à chaque opération, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="bd879-107">For information about the message structure and the SOAP action associated with each operation, see [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span></span>  
  
 <span data-ttu-id="bd879-108">Cette section fournit des informations sur les opérations prises en charge sur la base de données Oracle à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd879-108">This section provides information about the operations supported on the Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd879-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bd879-109">In This Section</span></span>  
  
-   [<span data-ttu-id="bd879-110">Exécution de base Insert, Update, Delete et les opérations Select sur Oracle Tables et vues</span><span class="sxs-lookup"><span data-stu-id="bd879-110">Performing Basic Insert, Update, Delete, and Select Operations on Oracle Tables and Views</span></span>](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-and-select-operations-on-oracle-tables-and-views.md)  
  
-   [<span data-ttu-id="bd879-111">Opérations sur les Tables et vues qui contiennent des données LOB</span><span class="sxs-lookup"><span data-stu-id="bd879-111">Operations on Tables and Views That Contain LOB Data</span></span>](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md)  
  
-   [<span data-ttu-id="bd879-112">Opérations sur les fonctions et procédures stockées dans la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd879-112">Operations on Functions and Stored Procedures in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/operations-on-functions-and-stored-procedures-in-oracle-database.md)  
  
-   [<span data-ttu-id="bd879-113">Opérations sur les fonctions et procédures avec des paramètres REF CURSOR dans la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd879-113">Operations on Functions and Procedures with REF CURSOR Parameters in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/ref-cursor-parameters-in-oracle-database-adapter.md)  
  
-   [<span data-ttu-id="bd879-114">Opérations sur les fonctions et procédures avec des Types d’enregistrements de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd879-114">Operations on Functions and Procedures with RECORD Types in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/operations-on-functions-and-procedures-with-record-types-in-oracle-database.md)  
  
-   [<span data-ttu-id="bd879-115">Opérations sur les Tables avec des Types de données BFILE</span><span class="sxs-lookup"><span data-stu-id="bd879-115">Operations on Tables With BFILE Data Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)  
  
-   [<span data-ttu-id="bd879-116">Opérations sur les synonymes dans la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd879-116">Operations on Synonyms in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/operations-on-synonyms-in-oracle-database.md)  
  
-   [<span data-ttu-id="bd879-117">Opération SQLEXECUTE dans la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd879-117">SQLEXECUTE Operation in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md)  
  
-   [<span data-ttu-id="bd879-118">Effectuer des opérations composites dans la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd879-118">Performing Composite Operations in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md)  
  
-   [<span data-ttu-id="bd879-119">Prise en charge pour la réception des Messages de modification de données reposant sur l’interrogation dans la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd879-119">Support for Receiving Polling-based Data-changed Messages in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md)  
  
-   [<span data-ttu-id="bd879-120">Considérations relatives à la réception de base de données modifiées des Notifications à l’aide de l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd879-120">Considerations for Receiving Database Change Notifications Using the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [<span data-ttu-id="bd879-121">Prise en charge pour les Types définis par l’utilisateur Oracle dans la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd879-121">Support for Oracle User-Defined Types in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/support-for-oracle-user-defined-types-in-oracle-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="bd879-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd879-122">See Also</span></span>  
 [<span data-ttu-id="bd879-123">Vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd879-123">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)