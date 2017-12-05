---
title: "À l’aide de l’onglet requête de la Console Administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Administration Console [BizTalk Server], Query tab
- Query tab [Administration Console]
ms.assetid: 7655f0b6-9217-46c4-88e0-ca2e661ce7a6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36b95a4213f4ef449aa78441a7caabc1e7f6f074
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-administration-console-query-tab"></a><span data-ttu-id="2820e-102">Utilisation de l'onglet Requête de la console Administration</span><span class="sxs-lookup"><span data-stu-id="2820e-102">Using the Administration Console Query Tab</span></span>
<span data-ttu-id="2820e-103">L'onglet Requête de la page Hub du groupe dans la console Administration de BizTalk Server permet de rechercher et de localiser des abonnements, des messages ou des instances de service spécifiques en cours d'exécution ou interrompus.</span><span class="sxs-lookup"><span data-stu-id="2820e-103">You can use the Query tab on the Group Hub page in the BizTalk Server Administration Console to search for and locate specific running and suspended service instances, messages, or subscriptions.</span></span> <span data-ttu-id="2820e-104">Les requêtes exécutées à l'aide de la console Administration localisent des éléments actifs, qui sont stockés dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="2820e-104">Queries performed using the Administration Console locate live items, which are stored in the MessageBox database.</span></span> <span data-ttu-id="2820e-105">Un onglet de requête vierge apparaît à chaque fois que vous lancez une nouvelle requête.</span><span class="sxs-lookup"><span data-stu-id="2820e-105">A new query tab appears each time you run a new query.</span></span>  
  
 <span data-ttu-id="2820e-106">Le suivi des instances de service et des événements de message permet de localiser des instances de service ou des messages archivés ou suivis.</span><span class="sxs-lookup"><span data-stu-id="2820e-106">To locate tracked or archived messages or service instances, you use message event and service instance tracking.</span></span> <span data-ttu-id="2820e-107">Pour plus d’informations, consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md).</span><span class="sxs-lookup"><span data-stu-id="2820e-107">For more information, see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2820e-108">Lorsque vous exécutez une requête pour les instances de service, le jeu de résultats retourné affiche la valeur de  **\<nom n’est pas disponible\>**  pour le **ServiceName** champ d’un service instance si le correspondant port d’envoi, l’emplacement de réception ou l’orchestration a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="2820e-108">When you execute a query for service instances, the result set that is returned will display a value of **\<Name is not available\>** for the **ServiceName** field of a service instance if the corresponding send port, receive location, or orchestration has been deleted.</span></span>  <span data-ttu-id="2820e-109">Le **ServiceName** champ d’une instance de service est rempli par une recherche dans la base de données de gestion BizTalk pour le nom convivial du port d’envoi, l’emplacement de réception, ou orchestration.</span><span class="sxs-lookup"><span data-stu-id="2820e-109">The **ServiceName** field of a service instance is populated by a lookup into the BizTalk management database for the friendly name of the send port, receive location, or orchestration.</span></span>  <span data-ttu-id="2820e-110">Si le port d’envoi, emplacement de réception, ou d’orchestration a été supprimé puis de la recherche du nom convivial échoue et  **\<nom n’est pas disponible\>**  s’affiche.</span><span class="sxs-lookup"><span data-stu-id="2820e-110">If the send port, receive location, or orchestration is deleted then the lookup for the friendly name fails and **\<Name is not available\>** is displayed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2820e-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2820e-111">In This Section</span></span>  
  
-   [<span data-ttu-id="2820e-112">Comment ouvrir une requête enregistrée</span><span class="sxs-lookup"><span data-stu-id="2820e-112">How to Open a Saved Query</span></span>](../core/how-to-open-a-saved-query.md)  
  
-   [<span data-ttu-id="2820e-113">Comment rechercher toutes les Instances de Service</span><span class="sxs-lookup"><span data-stu-id="2820e-113">How to Search for All Service Instances</span></span>](../core/how-to-search-for-all-service-instances.md)  
  
-   [<span data-ttu-id="2820e-114">Comment rechercher des Instances de Service en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="2820e-114">How to Search for Running Service Instances</span></span>](../core/how-to-search-for-running-service-instances.md)  
  
-   [<span data-ttu-id="2820e-115">Comment rechercher des Instances de Service suspendues</span><span class="sxs-lookup"><span data-stu-id="2820e-115">How to Search for Suspended Service Instances</span></span>](../core/how-to-search-for-suspended-service-instances.md)  
  
-   [<span data-ttu-id="2820e-116">Comment rechercher des Messages</span><span class="sxs-lookup"><span data-stu-id="2820e-116">How to Search for Messages</span></span>](../core/how-to-search-for-messages.md)  
  
-   [<span data-ttu-id="2820e-117">Comment rechercher des abonnements</span><span class="sxs-lookup"><span data-stu-id="2820e-117">How to Search for Subscriptions</span></span>](../core/how-to-search-for-subscriptions.md)  
  
-   [<span data-ttu-id="2820e-118">Comment enregistrer une requête</span><span class="sxs-lookup"><span data-stu-id="2820e-118">How to Save a Query</span></span>](../core/how-to-save-a-query.md)  
  
-   [<span data-ttu-id="2820e-119">Comment rechercher des événements de Message suivis</span><span class="sxs-lookup"><span data-stu-id="2820e-119">How to Search for Tracked Message Events</span></span>](../core/how-to-search-for-tracked-message-events.md)  
  
-   [<span data-ttu-id="2820e-120">Comment rechercher des Instances de Service suivies</span><span class="sxs-lookup"><span data-stu-id="2820e-120">How to Search for Tracked Service Instances</span></span>](../core/how-to-search-for-tracked-service-instances.md)