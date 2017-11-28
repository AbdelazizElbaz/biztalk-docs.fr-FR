---
title: "Gérer les alertes (affichage d’Administration) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f8bf7d-15b7-448d-8c13-e4969b90d021
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc5472e96414fe5141de27630ebe3c810d2df28c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-alerts-administration-view"></a><span data-ttu-id="d5208-102">Gérer les alertes (affichage d’Administration)</span><span class="sxs-lookup"><span data-stu-id="d5208-102">Manage Alerts (Administration View)</span></span>
<span data-ttu-id="d5208-103">Figure 1 montre la page des alertes dans la vue administration, dont les administrateurs peuvent utiliser pour afficher une liste de toutes les alertes et un résumé de leur activité.</span><span class="sxs-lookup"><span data-stu-id="d5208-103">Figure 1 shows the Alerts page in administration view, which administrators can use to view a list of all alerts and a summary of their activity.</span></span> <span data-ttu-id="d5208-104">Une table affiche une ligne pour chaque alerte.</span><span class="sxs-lookup"><span data-stu-id="d5208-104">A table displays a row for each alert.</span></span> <span data-ttu-id="d5208-105">Chaque ligne affiche le nom de l’alerte, le nom du créateur, les statistiques générales de l’alerte (par exemple, le nombre d’activations alerte au sein de la dernière heure, jour ou mois), un nombre d’abonnés pour les alertes avec un lien pour afficher une liste et une colonne d’Actions contenant un ensemble de l’interface cli icônes ckable pour effectuer des actions sur l’alerte.</span><span class="sxs-lookup"><span data-stu-id="d5208-105">Each row shows the alert name, the name of the creator, general statistics for the alert (such as number of alert activations within the last hour, day, or month), a count of subscribers for the alerts with a link to view a list, and an Actions column containing a set of clickable icons to perform actions on the alert.</span></span>  
  
 <span data-ttu-id="d5208-106">![Page Gérer les alertes](../esb-toolkit/media/ch8-managealertspage.jpg "Ch8-ManageAlertsPage")</span><span class="sxs-lookup"><span data-stu-id="d5208-106">![Manage Alerts Page](../esb-toolkit/media/ch8-managealertspage.jpg "Ch8-ManageAlertsPage")</span></span>  
  
 <span data-ttu-id="d5208-107">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="d5208-107">**Figure 1**</span></span>  
  
 <span data-ttu-id="d5208-108">**La page des alertes gérer ESB Management Portal (affichage d’Administration)**</span><span class="sxs-lookup"><span data-stu-id="d5208-108">**The ESB Management Portal Manage Alerts (Administration view) page**</span></span>  
  
 <span data-ttu-id="d5208-109">La liste suivante explique comment vous pouvez utiliser les fonctionnalités de la page du portail de gestion ESB gérer les alertes :</span><span class="sxs-lookup"><span data-stu-id="d5208-109">The following list explains how you can use the features of the ESB Management Portal Manage Alerts page:</span></span>  
  
-   <span data-ttu-id="d5208-110">Cliquez sur le **créer une alerte** lien en haut de la page pour créer une nouvelle alerte.</span><span class="sxs-lookup"><span data-stu-id="d5208-110">Click the **Create Alert** link at the top of the page to create a new alert.</span></span>  
  
-   <span data-ttu-id="d5208-111">Cliquez sur le **exporter vers Excel** lien pour exporter la liste des alertes en tant qu’une feuille de calcul Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="d5208-111">Click the **Export To Excel** link to export the list of alerts as a Microsoft Excel spreadsheet.</span></span>  
  
-   <span data-ttu-id="d5208-112">Cliquez sur le + **vue abonnés** lien dans une ligne pour afficher une liste d’abonnés à l’alerte.</span><span class="sxs-lookup"><span data-stu-id="d5208-112">Click the + **View Subscribers** link in a row to show a list of subscribers for the alert.</span></span> <span data-ttu-id="d5208-113">La liste se développe dans la ligne, et une icône de suppression s’affiche dans la colonne Actions pour chacun d’eux qui permet aux administrateurs de supprimer un abonné à partir de l’alerte.</span><span class="sxs-lookup"><span data-stu-id="d5208-113">The list expands within the row, and a delete icon appears in the Actions column for each one that allows administrators to remove a subscriber from the alert.</span></span> <span data-ttu-id="d5208-114">En même temps, le lien devient - **masquer les abonnés**, ce qui vous permet de réduire la liste des abonnés.</span><span class="sxs-lookup"><span data-stu-id="d5208-114">At the same time, the link changes to - **Hide Subscribers**, allowing you to collapse the list of subscribers.</span></span>  
  
-   <span data-ttu-id="d5208-115">Cliquez sur une icône dans la colonne d’Actions à effectuer une tâche pour les alertes de cette ligne.</span><span class="sxs-lookup"><span data-stu-id="d5208-115">Click an icon in the Actions column to perform a task for the alerts in that row.</span></span> <span data-ttu-id="d5208-116">Les icônes (dans l’ordre de qu'apparition) et les tâches sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d5208-116">The icons (in the order they appear) and the tasks are the following:</span></span>  
  
    -   <span data-ttu-id="d5208-117">**Afficher les détails de l’alerte.**</span><span class="sxs-lookup"><span data-stu-id="d5208-117">**View alert details.**</span></span> <span data-ttu-id="d5208-118">Cette icône affiche les détails de l’alerte sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="d5208-118">This icon displays details of the selected alert.</span></span>  
  
    -   <span data-ttu-id="d5208-119">**Afficher l’historique**.</span><span class="sxs-lookup"><span data-stu-id="d5208-119">**View history**.</span></span> <span data-ttu-id="d5208-120">Cette icône affiche un tableau qui contient toutes les activations de l’alerte sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="d5208-120">This icon displays a table containing all the activations for the selected alert.</span></span>  
  
    -   <span data-ttu-id="d5208-121">**Ajouter un abonné**.</span><span class="sxs-lookup"><span data-stu-id="d5208-121">**Add subscriber**.</span></span> <span data-ttu-id="d5208-122">Cette icône permet aux administrateurs d’ajouter un abonné à l’alerte sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="d5208-122">This icon allows administrators to add a subscriber to the selected alert.</span></span>  
  
    -   <span data-ttu-id="d5208-123">**Modifier l’alerte**.</span><span class="sxs-lookup"><span data-stu-id="d5208-123">**Edit alert**.</span></span> <span data-ttu-id="d5208-124">Ce lien permet aux administrateurs de modifier les détails de l’alerte.</span><span class="sxs-lookup"><span data-stu-id="d5208-124">This link allows administrators to edit the alert details.</span></span>  
  
    -   <span data-ttu-id="d5208-125">**Suppression d’alerte**.</span><span class="sxs-lookup"><span data-stu-id="d5208-125">**Delete alert**.</span></span> <span data-ttu-id="d5208-126">Ce lien supprime une alertes et les abonnements.</span><span class="sxs-lookup"><span data-stu-id="d5208-126">This link deletes the alert and all associated subscriptions.</span></span>