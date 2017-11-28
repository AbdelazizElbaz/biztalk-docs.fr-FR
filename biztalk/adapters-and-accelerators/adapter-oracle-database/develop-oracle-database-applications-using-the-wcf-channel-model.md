---
title: "Développer des applications de base de données Oracle à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, streaming
- channel programming, streaming
- WCF channel model, performing operations
- developing applications, by using the WCF channel model
- streaming, using the WCF channel model
- WCF channel model, developingn applications
- channel programming, performing operations
ms.assetid: cb6bf5fd-ff90-44bd-a9dd-03b00f12a78d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77fb9b6ca1fc70a55b59c6708450b8d94a01eff8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-oracle-database-applications-using-the-wcf-channel-model"></a><span data-ttu-id="a2af4-102">Développer des applications de base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="a2af4-102">Develop Oracle Database applications using the WCF Channel Model</span></span>
<span data-ttu-id="a2af4-103">Vous pouvez utiliser la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de canal pour consommer le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] en envoyant des messages XML directement sur une instance de canal créée avec la liaison de base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="a2af4-103">You can use the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] channel model to consume the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] by sending XML messages directly over a channel instance created with the Oracle DB Binding.</span></span>  
  
 <span data-ttu-id="a2af4-104">Un avantage de l’utilisation du modèle de canal WCF en utilisant les classes fortement typées et les méthodes que le modèle de service WCF expose est que le modèle de canal fournit un contrôle plus précis sur les opérations que vous effectuez sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="a2af4-104">One advantage of using the WCF channel model over using the strongly-typed classes and methods that the WCF service model exposes is that the channel model provides more fine-grained control over the operations that you perform on the Oracle database.</span></span> <span data-ttu-id="a2af4-105">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="a2af4-105">Why?</span></span> <span data-ttu-id="a2af4-106">Dans le modèle de canal WCF vous contrôler directement le contenu des messages que vous envoyez sur le canal.</span><span class="sxs-lookup"><span data-stu-id="a2af4-106">In the WCF channel model you directly control the contents of the messages that you send over the channel.</span></span>  
  
 <span data-ttu-id="a2af4-107">Dans certains scénarios, ce niveau supplémentaire de contrôle peut être utile.</span><span class="sxs-lookup"><span data-stu-id="a2af4-107">In certain scenarios, this extra level of control can be beneficial.</span></span> <span data-ttu-id="a2af4-108">Par exemple, lorsque vous utilisez le modèle de canal WCF pour effectuer une opération de mise à jour sur une table, vous pouvez sélectivement mettre à jour colonnes dans les lignes de la cible en omettant les colonnes à partir du modèle de mise à jour que vous passez dans le message.</span><span class="sxs-lookup"><span data-stu-id="a2af4-108">For example, when you use the WCF channel model to perform an Update operation on a table, you can selectively update columns in the target rows by omitting columns from the update template that you pass in the message.</span></span> <span data-ttu-id="a2af4-109">La méthode de mise à jour exposée par un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client utilise un paramètre d’enregistrement de fortement typé pour le modèle qui inclut toutes les colonnes dans le schéma de table.</span><span class="sxs-lookup"><span data-stu-id="a2af4-109">The update method exposed by a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client uses a strongly-typed record parameter for the template that includes every column in the table schema.</span></span> <span data-ttu-id="a2af4-110">Si une colonne est « nillable = false » dans le WSDL, il doit être mis à jour à l’aide du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="a2af4-110">If a column has “nillable=false” in the WSDL, it must be updated using the WCF service model.</span></span>  
  
 <span data-ttu-id="a2af4-111">Un autre avantage clé qui fournit un modèle de canal WCF sur le modèle de service WCF est prise en charge plus complète de bout en bout pour la diffusion en continu des types de données Oracle LOB (large object).</span><span class="sxs-lookup"><span data-stu-id="a2af4-111">Another key advantage that the WCF channel model provides over the WCF service model is more comprehensive support for end-to-end streaming of Oracle large object (LOB) data types.</span></span> <span data-ttu-id="a2af4-112">En utilisant le modèle de canal WCF, vous pouvez effectuer la diffusion en continu de bout en bout :</span><span class="sxs-lookup"><span data-stu-id="a2af4-112">By using the WCF channel model you can perform end-to-end streaming:</span></span>  
  
-   <span data-ttu-id="a2af4-113">Pour mettre à jour une colonne LOB dans une table ou vue à l’aide de l’opération UpdateLOB.</span><span class="sxs-lookup"><span data-stu-id="a2af4-113">To update an LOB column in a table or view using the UpdateLOB operation.</span></span>  
  
-   <span data-ttu-id="a2af4-114">DÉCOUVRIR et contenant des paramètres de sortie des données qui sont retournées par les procédures et fonctions de LOB.</span><span class="sxs-lookup"><span data-stu-id="a2af4-114">On OUT and IN OUT parameters containing LOB data that are returned by procedures and functions.</span></span>  
  
-   <span data-ttu-id="a2af4-115">Sur des données LOB, qui est contenue dans le résultat d’une opération SQLEXECUTE.</span><span class="sxs-lookup"><span data-stu-id="a2af4-115">On LOB data that is contained in the result of a SQLEXECUTE operation.</span></span>  
  
-   <span data-ttu-id="a2af4-116">Sur les colonnes de données LOB qui sont retournées dans l’opération POLLINGSTMT.</span><span class="sxs-lookup"><span data-stu-id="a2af4-116">On LOB data columns that are returned in the POLLINGSTMT operation.</span></span>  
  
-   <span data-ttu-id="a2af4-117">Sur les colonnes de données LOB qui sont retournées par une opération Select sur une table ou vue.</span><span class="sxs-lookup"><span data-stu-id="a2af4-117">On LOB data columns that are returned by a Select operation on a table or view.</span></span>  
  
 <span data-ttu-id="a2af4-118">Il s’agit, car dans le modèle de canal WCF vous contrôlez directement comment vous fournissez le corps du message sur les messages sortants et le mode de traitement du corps du message sur les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="a2af4-118">This is because in the WCF channel model you directly control how you provide the message body on outgoing messages and how you process the message body on incoming messages.</span></span>  
  
 <span data-ttu-id="a2af4-119">En revanche, le modèle de service WCF fournit uniquement :</span><span class="sxs-lookup"><span data-stu-id="a2af4-119">In contrast, the WCF service model only provides:</span></span>  
  
-   <span data-ttu-id="a2af4-120">De bout en bout pour les données LOB dans une seule opération, l’opération ReadLOB de diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="a2af4-120">End-to-end streaming for LOB data on one operation, the ReadLOB operation.</span></span>  
  
-   <span data-ttu-id="a2af4-121">N’arrive pas à mettre à jour la base de données Oracle dans une diffusion en continu des données LOB.</span><span class="sxs-lookup"><span data-stu-id="a2af4-121">No capability to update LOB data on the Oracle database in a streamed fashion.</span></span>  
  
 <span data-ttu-id="a2af4-122">Les sections de cette rubrique expliquent comment effectuer les opérations sur les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] en utilisant le modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="a2af4-122">The sections in this topic explain how to perform operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by using the WCF channel model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2af4-123">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a2af4-123">In This Section</span></span>  
  
-   [<span data-ttu-id="a2af4-124">Vue d’ensemble du modèle de canal WCF avec l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="a2af4-124">Overview of the WCF channel model with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-channel-model-with-the-oracle-database-adapter.md) 
  
-   [<span data-ttu-id="a2af4-125">Créer un canal à l’aide de la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="a2af4-125">Create a channel using Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md) 
  
-   [<span data-ttu-id="a2af4-126">Appeler des opérations sur la base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="a2af4-126">Invoke Operations on the Oracle Database Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/invoke-operations-on-the-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="a2af4-127">Exécuter une opération SQLEXECUTE dans la base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="a2af4-127">Run a SQLEXECUTE Operation in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="a2af4-128">Exécuter une opération d’insertion dans la base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="a2af4-128">Run an Insert Operation in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="a2af4-129">Appeler une fonction dans la base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="a2af4-129">Invoke a Function in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="a2af4-130">Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="a2af4-130">Receive Polling-based Data-changed Messages in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)  
  
-   [<span data-ttu-id="a2af4-131">Diffusion en continu de base de données LOB Types de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="a2af4-131">Streaming Oracle Database LOB Data Types Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)