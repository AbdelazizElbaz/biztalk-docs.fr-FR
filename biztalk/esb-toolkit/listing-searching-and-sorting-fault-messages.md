---
title: "Affichage de la liste, recherche et tri des Messages d’erreur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 850b9682-8eba-4a3f-8508-d3eefcd715b7
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 768dd7f51ff09bad76115f8a7e2a95a11ce47981
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="listing-searching-and-sorting-fault-messages"></a><span data-ttu-id="50cae-102">Affichage de la liste, recherche et tri des Messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="50cae-102">Listing, Searching, and Sorting Fault Messages</span></span>
<span data-ttu-id="50cae-103">Vous pouvez utiliser la page d’accueil du portail de gestion ESB pour obtenir une vue d’ensemble de l’état des applications qui s’exécutent dans Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="50cae-103">You can use the Home page of the ESB Management Portal to obtain an overall view of the status of the applications executing within Microsoft BizTalk Server.</span></span> <span data-ttu-id="50cae-104">La page d’erreurs peut être utilisée pour rechercher des messages d’erreur, basé sur une plage de critères.</span><span class="sxs-lookup"><span data-stu-id="50cae-104">The Faults page can be used to query for fault messages, based on a range of criteria.</span></span>  
  
### <a name="to-see-an-overview-of-the-status-of-current-biztalk-server-applications"></a><span data-ttu-id="50cae-105">Pour afficher une vue d’ensemble de l’état des applications de BizTalk Server en cours</span><span class="sxs-lookup"><span data-stu-id="50cae-105">To see an overview of the status of current BizTalk Server applications</span></span>  
  
1.  <span data-ttu-id="50cae-106">Ouvrez le [Page d’accueil du portail](../esb-toolkit/portal-home-page.md).</span><span class="sxs-lookup"><span data-stu-id="50cae-106">Open the [Portal Home Page](../esb-toolkit/portal-home-page.md).</span></span> <span data-ttu-id="50cae-107">Cette page affiche l’état global d’application, un résumé des erreurs, les demandes récentes pour inscription Universal Description, Discovery and Integration (UDDI) et les graphiques qui montrent une répartition des erreurs par type et par application.</span><span class="sxs-lookup"><span data-stu-id="50cae-107">This page displays the overall application state, a summary of faults, recent requests for Universal Description, Discovery, and Integration (UDDI) registration, and charts that show a breakdown of faults by type and by application.</span></span>  
  
2.  <span data-ttu-id="50cae-108">Pour sélectionner les applications pour lesquelles vous souhaitez afficher plus d’informations, cliquez sur le **sélectionner des Applications** ci-dessus le premier graphique, puis activez ou désactivez les cases à cocher dans la liste des applications installées de BizTalk Server qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="50cae-108">To select the applications for which you want to view information, click the **Select Applications** link above the first chart, and then select or clear the check boxes in the list of installed BizTalk Server applications that appears.</span></span>  
  
3.  <span data-ttu-id="50cae-109">Pour modifier la période pour laquelle le portail affiche des informations, sélectionnez **heure, jour, semaine, mois, trimestre, année,** ou **tous les** dans la liste déroulante au-dessus du premier graphique.</span><span class="sxs-lookup"><span data-stu-id="50cae-109">To change the period for which the portal displays information, select **Hour, Day, Week, Month, Quarter, Year,** or **ALL** in the drop-down list above the first chart.</span></span>  
  
4.  <span data-ttu-id="50cae-110">Pour modifier les paramètres par défaut utilisés sur la page d’accueil pour obtenir la liste d’applications et de la période d’affichage, modifiez les paramètres sur le [Page Paramètres de portail](../esb-toolkit/portal-my-settings-page.md).</span><span class="sxs-lookup"><span data-stu-id="50cae-110">To change the default settings used on the Home page for the list of applications and the display period, edit the settings on the [Portal My Settings Page](../esb-toolkit/portal-my-settings-page.md).</span></span>  
  
### <a name="to-list-search-for-and-sort-fault-messages-in-the-esb-management-portal"></a><span data-ttu-id="50cae-111">Pour répertorier, rechercher et trier les messages dans le portail de gestion ESB d’erreur</span><span class="sxs-lookup"><span data-stu-id="50cae-111">To list, search for, and sort fault messages in the ESB Management Portal</span></span>  
  
1.  <span data-ttu-id="50cae-112">Ouvrez le [Page Paramètres d’erreur](../esb-toolkit/fault-settings-page.md).</span><span class="sxs-lookup"><span data-stu-id="50cae-112">Open the [Fault Settings Page](../esb-toolkit/fault-settings-page.md).</span></span> <span data-ttu-id="50cae-113">Cette page affiche la liste de propriétés pour chaque erreur tronquée et prend en charge l’analyse des erreurs par une plage de critères.</span><span class="sxs-lookup"><span data-stu-id="50cae-113">This page displays a truncated list of properties for each fault and supports analysis of faults by a range of criteria.</span></span>  
  
2.  <span data-ttu-id="50cae-114">Pour filtrer la liste d’erreurs affichés sur la page, utilisez les listes déroulantes et les zones de texte au-dessus de la liste d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="50cae-114">To filter the list of faults displayed on the page, use the drop-down lists and text boxes above the list of faults.</span></span> <span data-ttu-id="50cae-115">Vous pouvez filtrer les lignes affichées par application, période, numéro de code d’erreur, nom de catégorie d’erreur, texte du type d’erreur et gravité d’erreur de valeur minimale/maximale.</span><span class="sxs-lookup"><span data-stu-id="50cae-115">You can filter the rows displayed by application, period, fault code number, fault category name, error type text, and minimum/maximum fault severity.</span></span> <span data-ttu-id="50cae-116">Renseignez les contrôles pour récupérer tous les messages, quel que soit leur valeur pour ce critère.</span><span class="sxs-lookup"><span data-stu-id="50cae-116">Leave any of the controls empty to retrieve all messages irrespective of their value for this criterion.</span></span>  
  
3.  <span data-ttu-id="50cae-117">Cliquez sur **appliquer des filtres** pour afficher la liste des erreurs de mise en correspondance.</span><span class="sxs-lookup"><span data-stu-id="50cae-117">Click **Apply Filters** to see the list of matching faults.</span></span> <span data-ttu-id="50cae-118">Le filtrage sur les bases de données des erreurs très volumineux peut prendre de quelques secondes pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="50cae-118">Note that filtering on very large fault databases may take a few seconds to display results.</span></span>  
  
4.  <span data-ttu-id="50cae-119">Pour afficher plus ou moins de lignes dans la page, sélectionnez la valeur appropriée dans le **enregistrements par Page** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="50cae-119">To display more or fewer rows in the page, select the appropriate value in the **Records Per Page** drop-down list.</span></span>  
  
5.  <span data-ttu-id="50cae-120">Pour trier la liste des messages d’erreur, cliquez sur un en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="50cae-120">To sort the list of fault messages, click a column heading.</span></span> <span data-ttu-id="50cae-121">Pour trier les lignes dans l’ordre inverse, cliquez sur l’en-tête de la même colonne.</span><span class="sxs-lookup"><span data-stu-id="50cae-121">To sort the rows in reverse order, click the same column heading again.</span></span>  
  
6.  <span data-ttu-id="50cae-122">Cliquez sur **exporter vers Excel** pour télécharger la liste complète des messages d’erreur dans un format que vous pouvez afficher dans Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="50cae-122">Click **Export To Excel** to download the complete list of fault messages in a format that you can view in Microsoft Excel.</span></span>