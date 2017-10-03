---
title: "Gestion des bases de données MessageBox | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [MessageBox database], about managing MessageBox database
- managing [MessageBox database]
- MessageBox database, managing
ms.assetid: 9675b5d5-7a69-468d-be42-34a72cd6e5c2
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e854ad0f7014de8241f8a7b6af6addd49cb4da5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-messagebox-databases"></a><span data-ttu-id="1eb66-102">Gestion des bases de données MessageBox</span><span class="sxs-lookup"><span data-stu-id="1eb66-102">Managing MessageBox Databases</span></span>
<span data-ttu-id="1eb66-103">La base de données MessageBox permet d'effectuer trois fonctions essentielles.</span><span class="sxs-lookup"><span data-stu-id="1eb66-103">The MessageBox database has three essential functions.</span></span> <span data-ttu-id="1eb66-104">Elle stocke les abonnements et les informations de suivi et envoie les messages aux services correspondant aux abonnements.</span><span class="sxs-lookup"><span data-stu-id="1eb66-104">It stores subscriptions and tracking information and it delivers the messages to the services that match the subscriptions.</span></span> <span data-ttu-id="1eb66-105">C'est une plateforme hôte qui stocke les files d'attente et les tables d'état de chaque hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1eb66-105">The MessageBox database is a host platform that stores the queues and state tables for each BizTalk Host.</span></span> <span data-ttu-id="1eb66-106">Elle stocke également les messages et leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="1eb66-106">The MessageBox database also stores messages and message properties.</span></span>  
  
 <span data-ttu-id="1eb66-107">Si les bases de données MessageBox sont très exposées aux risques dans votre environnement, nous vous recommandons d'utiliser la sécurité du protocole Internet (IPSec) ou SSL (Secure Sockets Layer) pour limiter et sécuriser la communication avec les bases de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="1eb66-107">If the MessageBox databases are an asset with high-risk exposure in your environment, we recommend that you use Internet Protocol security (IPSec) or Secure Sockets Layer (SSL) to restrict and secure communication to and from the MessageBox databases.</span></span>  
  
 <span data-ttu-id="1eb66-108">Si vous utilisez Windows Server 2003, vous devez activer le coordinateur de transactions distribuées (DTC) sur la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="1eb66-108">If you use Windows Server 2003, you must enable the distributed transaction coordinator (DTC) on the MessageBox database.</span></span> <span data-ttu-id="1eb66-109">Vous devez également activer les clients réseau dans le cas de déploiements sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="1eb66-109">You must also enable network clients for multicomputer deployments.</span></span> <span data-ttu-id="1eb66-110">Pour plus d’informations, consultez [Ports pour le serveur d’Administration](../core/ports-for-the-administration-server.md).</span><span class="sxs-lookup"><span data-stu-id="1eb66-110">For more information, see [Ports for the Administration Server](../core/ports-for-the-administration-server.md).</span></span>  
  
 <span data-ttu-id="1eb66-111">Cette section contient des procédures de gestion des bases de données MessageBox dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="1eb66-111">This section contains procedural information about managing MessageBox databases in your environment.</span></span> <span data-ttu-id="1eb66-112">Pour plus d’informations conceptuelles sur les bases de données MessageBox et l’abonnement modèle Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise pour traiter les messages, consultez [la base de données MessageBox](../core/the-messagebox-database.md).</span><span class="sxs-lookup"><span data-stu-id="1eb66-112">For conceptual information about MessageBox databases and the subscription model Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses to process messages, see [The MessageBox Database](../core/the-messagebox-database.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1eb66-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1eb66-113">In This Section</span></span>  
  
-   [<span data-ttu-id="1eb66-114">Comment ajouter une nouvelle base de données MessageBox</span><span class="sxs-lookup"><span data-stu-id="1eb66-114">How to Add a New MessageBox Database</span></span>](../core/how-to-add-a-new-messagebox-database.md)  
  
-   [<span data-ttu-id="1eb66-115">Comment désactiver la Publication des nouveaux messages</span><span class="sxs-lookup"><span data-stu-id="1eb66-115">How to Disable New Message Publication</span></span>](../core/how-to-disable-new-message-publication.md)  
  
-   [<span data-ttu-id="1eb66-116">Comment supprimer une base de données MessageBox</span><span class="sxs-lookup"><span data-stu-id="1eb66-116">How to Delete a MessageBox Database</span></span>](../core/how-to-delete-a-messagebox-database.md)