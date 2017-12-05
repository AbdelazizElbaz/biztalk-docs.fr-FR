---
title: "Détails d’implémentation adaptateur OPS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, Ops adapters
- Ops adapters, batching
- Ops adapters, creating ports
- Ops adapters, implementing
- Ops adapters, transaction handling
- process management solution tutorial, Ops adapters
ms.assetid: dbca31ca-c3d8-4a25-9356-ef4bbab671e1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3172759541f46ec6c3c8c2b3e684086747036f37
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="ops-adapter-implementation-details"></a><span data-ttu-id="d99ea-102">Détails de l'implémentation de l'adaptateur Ops</span><span class="sxs-lookup"><span data-stu-id="d99ea-102">Ops Adapter Implementation Details</span></span>
<span data-ttu-id="d99ea-103">La compréhension des aspects suivants de l'adaptateur Ops peut s'avérer utile lors de la modification de l'adaptateur ou de sa configuration par programme.</span><span class="sxs-lookup"><span data-stu-id="d99ea-103">You may find it useful to understand the following aspects of the Ops adapter when modifying the adapter or configuring it programmatically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d99ea-104">L'adaptateur Ops est créé à l'aide de l'infrastructure d'adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="d99ea-104">The Ops Adapter is built using the Adapter Framework.</span></span> <span data-ttu-id="d99ea-105">Pour plus d’informations sur la création de cartes avec l’infrastructure, consultez [développement des adaptateurs personnalisés](../core/developing-custom-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="d99ea-105">For information about building adapters with the framework, see [Developing Custom Adapters](../core/developing-custom-adapters.md).</span></span>  
  
## <a name="batch-processing"></a><span data-ttu-id="d99ea-106">Traitement par lots</span><span class="sxs-lookup"><span data-stu-id="d99ea-106">Batch Processing</span></span>  
 <span data-ttu-id="d99ea-107">L'adaptateur traite un message à la fois de manière à ce que chaque message soit traité séparément, et les opérations de restauration sont effectuées sur une commande à la fois.</span><span class="sxs-lookup"><span data-stu-id="d99ea-107">The adapter processes one message at a time so that each message is processed separately, and rollback operations are done on only one order at a time.</span></span> <span data-ttu-id="d99ea-108">Bien que l'adaptateur traite un message à la fois, il effectue cette opération à l'aide du traitement par lot avec une taille de lot égale à un.</span><span class="sxs-lookup"><span data-stu-id="d99ea-108">Although the adapter processes one message at a time, it does so using batching with a batch size of one.</span></span> <span data-ttu-id="d99ea-109">Cela simplifie la modification de l'adaptateur de manière à ce qu'il traite les messages par lots.</span><span class="sxs-lookup"><span data-stu-id="d99ea-109">This makes it easier to modify the adapter to handle messages in batches.</span></span>  
  
## <a name="transaction-handling"></a><span data-ttu-id="d99ea-110">Gestion des transactions</span><span class="sxs-lookup"><span data-stu-id="d99ea-110">Transaction Handling</span></span>  
 <span data-ttu-id="d99ea-111">L’adaptateur utilise les fonctionnalités de transaction fournies par Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] **System.Transactions** installations.</span><span class="sxs-lookup"><span data-stu-id="d99ea-111">The adapter uses the transaction facilities provided by the Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]**System.Transactions** facilities.</span></span> <span data-ttu-id="d99ea-112">L’adaptateur crée un nouveau **CommittableTransaction** et l’utilise avec un **TransactionScope**.</span><span class="sxs-lookup"><span data-stu-id="d99ea-112">The adapter creates a new **CommittableTransaction** and uses it with a **TransactionScope**.</span></span> <span data-ttu-id="d99ea-113">L’adaptateur appelle la **initialiser** et **Execute** méthodes dans le cadre de cette transaction.</span><span class="sxs-lookup"><span data-stu-id="d99ea-113">The adapter calls the **Initialize** and **Execute** methods within the context of this transaction.</span></span> <span data-ttu-id="d99ea-114">Code de l’assembly appelé peut participer à la transaction à l’aide de **Transaction.Current** une méthode statique pour obtenir le contexte de transaction.</span><span class="sxs-lookup"><span data-stu-id="d99ea-114">Code in the called assembly can participate in the transaction by using **Transaction.Current** static method to get the transaction context.</span></span> <span data-ttu-id="d99ea-115">L'exemple de gestionnaire d'erreurs n'exploite pas cette fonction.</span><span class="sxs-lookup"><span data-stu-id="d99ea-115">The sample error handler does not make use of this facility.</span></span> <span data-ttu-id="d99ea-116">Pour plus d’informations sur **System.Transactions**, consultez « System.Transactions Namespace » dans la version de la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d99ea-116">For more information about **System.Transactions**, see "System.Transactions Namespace" in the .NET Framework Class Library version.</span></span>  
  
## <a name="handling-data-other-than-error-reports"></a><span data-ttu-id="d99ea-117">Traitement de données autres que des rapports d'erreurs</span><span class="sxs-lookup"><span data-stu-id="d99ea-117">Handling Data Other Than Error Reports</span></span>  
 <span data-ttu-id="d99ea-118">Dans la solution, l'adaptateur gère les messages des rapports d'erreurs grâce à la nouvelle fonctionnalité de signalement d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="d99ea-118">In the solution, the adapter handles error report messages from the new error reporting feature.</span></span> <span data-ttu-id="d99ea-119">Toutefois, étant donné que la **Execute** méthode prend un tableau d’octets comme seul argument, rien ne spécifiquement limite ce qui peut être passé à la **Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="d99ea-119">However, because the **Execute** method takes a byte array as its only argument, there is nothing that specifically limits what can be passed to the **Execute** method.</span></span>  
  
## <a name="using-the-adapter-when-creating-ports-programmatically"></a><span data-ttu-id="d99ea-120">Utilisation de l'adaptateur lors de la création de ports par programme</span><span class="sxs-lookup"><span data-stu-id="d99ea-120">Using the Adapter When Creating Ports Programmatically</span></span>  
 <span data-ttu-id="d99ea-121">Vous pouvez spécifier un adaptateur lors de la création de ports à partir d'un code.</span><span class="sxs-lookup"><span data-stu-id="d99ea-121">You can specify the adapter when creating ports from code.</span></span> <span data-ttu-id="d99ea-122">Le tableau suivant illustre les noms des propriétés personnalisées et la manière dont elles correspondent à leur nom complet.</span><span class="sxs-lookup"><span data-stu-id="d99ea-122">The following table shows the custom property names and how they correspond to the display names.</span></span>  
  
|<span data-ttu-id="d99ea-123">Nom de la propriété personnalisée d'envoi</span><span class="sxs-lookup"><span data-stu-id="d99ea-123">Send Custom Property Name</span></span>|<span data-ttu-id="d99ea-124">Nom complet</span><span class="sxs-lookup"><span data-stu-id="d99ea-124">Display Name</span></span>|  
|-------------------------------|------------------|  
|<span data-ttu-id="d99ea-125">**DotNetAssemblyStrongName**</span><span class="sxs-lookup"><span data-stu-id="d99ea-125">**DotNetAssemblyStrongName**</span></span>|<span data-ttu-id="d99ea-126">**DotNetAssemblyStrongName**</span><span class="sxs-lookup"><span data-stu-id="d99ea-126">**DotNetAssemblyStrongName**</span></span>|  
|<span data-ttu-id="d99ea-127">**DotNetClassName**</span><span class="sxs-lookup"><span data-stu-id="d99ea-127">**DotNetClassName**</span></span>|<span data-ttu-id="d99ea-128">**DotNetClassName**</span><span class="sxs-lookup"><span data-stu-id="d99ea-128">**DotNetClassName**</span></span>|  
|<span data-ttu-id="d99ea-129">**InitializationData**</span><span class="sxs-lookup"><span data-stu-id="d99ea-129">**InitializationData**</span></span>|<span data-ttu-id="d99ea-130">**InitializationData**</span><span class="sxs-lookup"><span data-stu-id="d99ea-130">**InitializationData**</span></span>|  
|<span data-ttu-id="d99ea-131">**TransportLocationUri**</span><span class="sxs-lookup"><span data-stu-id="d99ea-131">**TransportLocationUri**</span></span>|<span data-ttu-id="d99ea-132">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="d99ea-132">Not applicable.</span></span>|  
  
 <span data-ttu-id="d99ea-133">Toutes les propriétés renvoient des valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="d99ea-133">All of the properties are string values.</span></span> <span data-ttu-id="d99ea-134">Vous construisez la valeur de la propriété TransportLocationUri à partir du nom de l'assembly et du nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="d99ea-134">You construct the value of the TransportLocationUri property from the assembly name and the class name.</span></span> <span data-ttu-id="d99ea-135">L’URI a la valeur OPS : / /\<DotNetAssemblyStrongName\>/\<DotNetClassName\> où les espaces réservés sont remplacés par les valeurs de la propriété personnalisée correspondante.</span><span class="sxs-lookup"><span data-stu-id="d99ea-135">The URI has the value OPS://\<DotNetAssemblyStrongName\>/\<DotNetClassName\> where the placeholders are replaced by the values of the corresponding custom property.</span></span>  
  
 <span data-ttu-id="d99ea-136">Pour plus d’informations sur la création de ports à partir de code, consultez [comment créer des emplacements de réception MSMQ et les Ports d’envoi à partir de Code](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md).</span><span class="sxs-lookup"><span data-stu-id="d99ea-136">For information about creating ports from code, see [How to Create MSMQ Receive Locations and Send Ports from Code](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d99ea-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d99ea-137">See Also</span></span>  
 [<span data-ttu-id="d99ea-138">Adaptateur Ops</span><span class="sxs-lookup"><span data-stu-id="d99ea-138">The Ops Adapter</span></span>](../core/the-ops-adapter.md)