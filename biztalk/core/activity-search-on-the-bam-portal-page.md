---
title: "Recherche d’activité sur le portail BAM Page | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], searching
- Activity Search page [BAM portal]
- BAM portal, activity searches
ms.assetid: 24a5111c-026f-4f77-8a17-65955aafd24c
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 670d73cb33d9e3cc3aa1a9162cf929382a4dd58a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="activity-search-on-the-bam-portal-page"></a><span data-ttu-id="b3c13-102">Recherche d'activité dans la page Portail BAM</span><span class="sxs-lookup"><span data-stu-id="b3c13-102">Activity Search on the BAM Portal Page</span></span>
<span data-ttu-id="b3c13-103">Les utilisateurs finaux, les développeurs et les analystes d'entreprise peuvent utiliser la page du portail BAM lorsqu'ils doivent effectuer des recherches sur des données BAM et des cas de figure relatifs à un processus d'entreprise particulier.</span><span class="sxs-lookup"><span data-stu-id="b3c13-103">Business end users, developers, and business analysts can use the BAM portal page when they need to perform searches against BAM data to find specific cases of a particular process.</span></span> <span data-ttu-id="b3c13-104">Ces processus sont définis en tant qu'activités BAM.</span><span class="sxs-lookup"><span data-stu-id="b3c13-104">These processes are defined as BAM activities.</span></span> <span data-ttu-id="b3c13-105">Une activité BAM représente une unité de travail dans une activité commerciale : un bon de commande ou une application d'emprunt, par exemple.</span><span class="sxs-lookup"><span data-stu-id="b3c13-105">A BAM activity represents a unit of work in a business, such as a purchase order or loan application.</span></span>  
  
## <a name="how-an-activity-search-works"></a><span data-ttu-id="b3c13-106">Fonctionnement d'une activité de recherche</span><span class="sxs-lookup"><span data-stu-id="b3c13-106">How an activity search works</span></span>  
 <span data-ttu-id="b3c13-107">Une recherche d’activité vous permet d’effectuer des recherches sur des données BAM pour rechercher les activités répondant aux critères que vous spécifiez en fonction de valeurs suivies et des éléments disponibles dans une vue BAM et pour afficher les activités afin que vous pouvez les modifier ou créer des alertes basées sur ces derniers.</span><span class="sxs-lookup"><span data-stu-id="b3c13-107">An activity search allows you to perform searches against BAM data to find activities that match criteria you specify based on tracked values and items available in a BAM view, and to display the activities so that you can edit them or create alerts based on them.</span></span>  
  
 <span data-ttu-id="b3c13-108">Les requêtes que vous créez pour vos recherches peuvent être enregistrées et réutilisées.</span><span class="sxs-lookup"><span data-stu-id="b3c13-108">Queries that you create for your searches can be saved and reused.</span></span> <span data-ttu-id="b3c13-109">Vous pouvez également les utiliser comme bases d'une alerte, par exemple « M'avertir chaque fois qu'un bon de commande du client spécifié est reçu. »</span><span class="sxs-lookup"><span data-stu-id="b3c13-109">You can also use them as the basis for an alert, for example, "Notify me any time a purchase order arrives from the specified customer."</span></span> <span data-ttu-id="b3c13-110">Vous pouvez utiliser les boutons figurant en haut de la page de contenu pour enregistrer, ouvrir et exécuter des requêtes, ainsi que pour définir des alertes.</span><span class="sxs-lookup"><span data-stu-id="b3c13-110">You use the buttons at the top of the content page to save, open, and run queries, as well as to set alerts.</span></span>  
  
 <span data-ttu-id="b3c13-111">Les recherches d'activité vous permettent de localiser les activités que vous souhaitez analyser.</span><span class="sxs-lookup"><span data-stu-id="b3c13-111">Activity searches allow you to locate the activities that you want to monitor.</span></span> <span data-ttu-id="b3c13-112">Une fois que vous avez créé une recherche d'activité, vous pouvez l'utiliser pour créer une alerte qui capable de vous signaler des événements significatifs.</span><span class="sxs-lookup"><span data-stu-id="b3c13-112">Once you create an activity search, you can use that search to create an alert that will notify you of events that are of interest.</span></span>  
  
## <a name="the-activity-search-page"></a><span data-ttu-id="b3c13-113">Page Recherche d'activité</span><span class="sxs-lookup"><span data-stu-id="b3c13-113">The Activity Search page</span></span>  
 <span data-ttu-id="b3c13-114">La page Recherche d'activité est divisée en trois sections principales à l'intérieur du cadre Contenu :</span><span class="sxs-lookup"><span data-stu-id="b3c13-114">The Activity Search page is divided into three main sections inside the Content frame:</span></span>  
  
-   <span data-ttu-id="b3c13-115">**Requête**: cette section permet aux utilisateurs de rechercher des activités en créant des clauses de recherche en fonction des éléments de données suivis spécifiques.</span><span class="sxs-lookup"><span data-stu-id="b3c13-115">**Query**: This section allows users to search for activities by building search clauses based on specific tracked data items.</span></span> <span data-ttu-id="b3c13-116">L'utilisateur peut ajouter ou supprimer des clauses selon ses besoins.</span><span class="sxs-lookup"><span data-stu-id="b3c13-116">The user can add and remove clauses as required.</span></span>  
  
-   <span data-ttu-id="b3c13-117">**Sélecteur de colonne**: cette section permet aux utilisateurs de spécifier les éléments de données, parmi ceux disponibles dans cette vue, à retourner si des enregistrements correspondent aux critères de recherche.</span><span class="sxs-lookup"><span data-stu-id="b3c13-117">**Column Chooser**: This section allows users to specify which items of data, from those available in that view, to return if any records match the search criteria.</span></span>  
  
-   <span data-ttu-id="b3c13-118">**Résultats**: résultats de la requête s’affichent dans cette section.</span><span class="sxs-lookup"><span data-stu-id="b3c13-118">**Results**: Results of the query display in this section.</span></span>  
  
 <span data-ttu-id="b3c13-119">Pour plus d’informations sur les recherches d’activité et de la page recherche d’activité, consultez [recherches d’activité dans le portail BAM](../core/activity-searches-in-the-bam-portal.md).</span><span class="sxs-lookup"><span data-stu-id="b3c13-119">For more information about activity searches and the Activity Search page, see [Activity Searches in the BAM Portal](../core/activity-searches-in-the-bam-portal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c13-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3c13-120">See Also</span></span>  
 <span data-ttu-id="b3c13-121">[Portail BAM](../core/bam-portal.md) </span><span class="sxs-lookup"><span data-stu-id="b3c13-121">[BAM Portal](../core/bam-portal.md) </span></span>  
 <span data-ttu-id="b3c13-122">[Implémentation d’activités BAM avec les flux d’événements](../core/implementing-bam-activities-with-event-streams.md) </span><span class="sxs-lookup"><span data-stu-id="b3c13-122">[Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md) </span></span>  
 [<span data-ttu-id="b3c13-123">Alert Manager sur le portail BAM Page</span><span class="sxs-lookup"><span data-stu-id="b3c13-123">Alert Manager on the BAM Portal Page</span></span>](../core/alert-manager-on-the-bam-portal-page.md)