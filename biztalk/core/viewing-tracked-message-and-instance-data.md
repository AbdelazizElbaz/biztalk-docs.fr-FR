---
title: "Affichage des messages suivis et les données d’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring, HAT
- HAT, about HAT
ms.assetid: e3cc7bef-90c7-4375-9f6c-7df00391132e
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 592fa5c85913a69f4536055cdd790d638b15bc32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="viewing-tracked-message-and-instance-data"></a><span data-ttu-id="f7bdc-102">Affichage des données de messages suivis et d'instances</span><span class="sxs-lookup"><span data-stu-id="f7bdc-102">Viewing Tracked Message and Instance Data</span></span>
<span data-ttu-id="f7bdc-103">Les données historiques et de suivi permettent de faciliter la résolution des problèmes liés à vos applications BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-103">You can use historical and tracked data to help troubleshoot your BizTalk Server applications.</span></span> <span data-ttu-id="f7bdc-104">Par exemple, les administrateurs système peuvent utiliser les données historiques et de suivi pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="f7bdc-104">For example, system administrators can use historical and tracked data to:</span></span>  
  
-   <span data-ttu-id="f7bdc-105">Consulter les événements suivis liés à un message, les propriétés de message et les corps de message à différentes étapes d'un flux de message.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-105">View tracked message events, message properties, and message bodies at various stages in a message’s flow.</span></span> <span data-ttu-id="f7bdc-106">Ces données peuvent ensuite être utilisées à des fins de dépannage ou d'audit.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-106">This data can be used for troubleshooting or auditing purposes.</span></span>  
  
-   <span data-ttu-id="f7bdc-107">Relire l'exécution d'une instance spécifique de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-107">Replay the execution of a specific orchestration instance.</span></span>  
  
-   <span data-ttu-id="f7bdc-108">Suivre les événements liés au déclenchement de règles pour reconstruire ultérieurement la séquence des événements.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-108">Track rule firing events to reconstruct the sequence of events at a later point in time.</span></span>  
  
-   <span data-ttu-id="f7bdc-109">Rechercher des messages en définissant des critères tels que le schéma et les paires propriété/valeur d'un message.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-109">Query for messages by specifying criteria such as message schema and message property/value pairs.</span></span> <span data-ttu-id="f7bdc-110">Une fois le message trouvé, ils peuvent déterminer son niveau d'avancement dans le flux de message.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-110">Having thus located the message, users can determine the point in the message flow to which the message has progressed.</span></span> <span data-ttu-id="f7bdc-111">Les utilisateurs expérimentés peuvent par ailleurs créer des requêtes SQL Server personnalisées pour les messages.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-111">Advanced users can also create custom SQL Server queries for messages.</span></span>  
  
-   <span data-ttu-id="f7bdc-112">Rechercher des données archivées dans une base de données archivée.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-112">Search for archived data in an archived database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7bdc-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f7bdc-113">In This Section</span></span>  
  
-   [<span data-ttu-id="f7bdc-114">Liste de vérification : Message et suivi des instances de données</span><span class="sxs-lookup"><span data-stu-id="f7bdc-114">Checklist: Message and Instance Data Tracking</span></span>](../core/checklist-message-and-instance-data-tracking.md)  
  
-   [<span data-ttu-id="f7bdc-115">Meilleures pratiques pour le Message et le suivi des instances de données</span><span class="sxs-lookup"><span data-stu-id="f7bdc-115">Best Practices for Message and Instance Data Tracking</span></span>](../core/best-practices-for-message-and-instance-data-tracking.md)  
  
-   [<span data-ttu-id="f7bdc-116">Considérations sur la sécurité des messages et le suivi des instances de données</span><span class="sxs-lookup"><span data-stu-id="f7bdc-116">Security Considerations for Message and Instance Data Tracking</span></span>](../core/security-considerations-for-message-and-instance-data-tracking.md)  
  
-   [<span data-ttu-id="f7bdc-117">Présentation des données suivies</span><span class="sxs-lookup"><span data-stu-id="f7bdc-117">Understanding Tracked Data</span></span>](../core/understanding-tracked-data.md)  
  
-   [<span data-ttu-id="f7bdc-118">Affichage des données historiques et de suivi</span><span class="sxs-lookup"><span data-stu-id="f7bdc-118">Viewing Historical and Tracked Data</span></span>](../core/viewing-historical-and-tracked-data.md)  
  
-   [<span data-ttu-id="f7bdc-119">Comment sélectionner une Source de données actives ou archivées</span><span class="sxs-lookup"><span data-stu-id="f7bdc-119">How to Select a Live or Archived Data Source</span></span>](../core/how-to-select-a-live-or-archived-data-source.md)  
  
-   [<span data-ttu-id="f7bdc-120">Comment modifier la valeur QueryTimeout du suivi</span><span class="sxs-lookup"><span data-stu-id="f7bdc-120">How to Change the Tracking QueryTimeout Value</span></span>](../core/how-to-change-the-tracking-querytimeout-value.md)  
  
-   [<span data-ttu-id="f7bdc-121">Comment enregistrer une requête de suivi</span><span class="sxs-lookup"><span data-stu-id="f7bdc-121">How to Save a Tracking Query</span></span>](../core/how-to-save-a-tracking-query.md)  
  
-   [<span data-ttu-id="f7bdc-122">Comment ouvrir une requête de suivi enregistrée</span><span class="sxs-lookup"><span data-stu-id="f7bdc-122">How to Open a Saved Tracking Query</span></span>](../core/how-to-open-a-saved-tracking-query.md)  
  
-   [<span data-ttu-id="f7bdc-123">Flux de messages d’affichage</span><span class="sxs-lookup"><span data-stu-id="f7bdc-123">Viewing Message Flow</span></span>](../core/viewing-message-flow.md)  
  
-   [<span data-ttu-id="f7bdc-124">Débogage d’une Orchestration</span><span class="sxs-lookup"><span data-stu-id="f7bdc-124">Debugging an Orchestration</span></span>](../core/debugging-an-orchestration.md)  
  
-   [<span data-ttu-id="f7bdc-125">Utilisation de la liste de résultats</span><span class="sxs-lookup"><span data-stu-id="f7bdc-125">Working with the Results List</span></span>](../core/working-with-the-results-list.md)