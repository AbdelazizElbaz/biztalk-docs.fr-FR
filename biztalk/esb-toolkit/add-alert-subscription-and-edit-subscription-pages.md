---
title: "Ajouter l’abonnement aux alertes et modifier des Pages d’abonnement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad5e99f1-714e-458b-b5f0-85ac69be5335
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49bed9959b51439f21d625795a69804fd41d77ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="add-alert-subscription-and-edit-subscription-pages"></a><span data-ttu-id="8d2fc-102">Ajouter l’abonnement aux alertes et modifier des Pages d’abonnement</span><span class="sxs-lookup"><span data-stu-id="8d2fc-102">Add Alert Subscription and Edit Subscription Pages</span></span>
<span data-ttu-id="8d2fc-103">Les pages de l’abonnement aux alertes ajouter et modifier l’abonnement sont similaires.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-103">The Add Alert Subscription and Edit Subscription pages are similar.</span></span> <span data-ttu-id="8d2fc-104">Ils diffèrent la page Modifier l’abonnement affiche l’ID de l’abonné (le compte Microsoft Windows de l’utilisateur du portail actuel) et possède un ensemble différent de boutons.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-104">They differ in that the Edit Subscription page shows the subscriber ID (the Microsoft Windows account of the current portal user), and has a different set of buttons.</span></span> <span data-ttu-id="8d2fc-105">Figure 1 montre les pages d’abonnement aux alertes ajouter et modifier un abonnement.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-105">Figure 1 shows the Add Alert Subscription and Edit Subscription pages.</span></span>  
  
 <span data-ttu-id="8d2fc-106">![Ajouter un abonnement de modification d’alerte](../esb-toolkit/media/ch8-addalerteditsubscription.gif "Ch8-AddAlertEditSubscription")</span><span class="sxs-lookup"><span data-stu-id="8d2fc-106">![Add Alert Edit Subscription](../esb-toolkit/media/ch8-addalerteditsubscription.gif "Ch8-AddAlertEditSubscription")</span></span>  
  
 <span data-ttu-id="8d2fc-107">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="8d2fc-107">**Figure 1**</span></span>  
  
 <span data-ttu-id="8d2fc-108">**Les pages ESB Management Portal ajouter abonnement aux alertes et modifier un abonnement**</span><span class="sxs-lookup"><span data-stu-id="8d2fc-108">**The ESB Management Portal Add Alert Subscription and Edit Subscription pages**</span></span>  
  
 <span data-ttu-id="8d2fc-109">Les pages d’abonnement aux alertes ajouter et modifier un abonnement vous autorise à spécifier et modifier les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="8d2fc-109">The Add Alert Subscription and Edit Subscription pages allow you to specify and modify the following:</span></span>  
  
-   <span data-ttu-id="8d2fc-110">Une adresse de courrier électronique personnalisé à utiliser pour l’abonnement (au lieu de votre adresse de messagerie du compte Microsoft Windows)</span><span class="sxs-lookup"><span data-stu-id="8d2fc-110">A custom e-mail address to use for the subscription (instead of your Microsoft Windows account e-mail address)</span></span>  
  
-   <span data-ttu-id="8d2fc-111">La période de temps lorsque vous acceptez des notifications d’alerte</span><span class="sxs-lookup"><span data-stu-id="8d2fc-111">The time period when you will accept alert notifications</span></span>  
  
-   <span data-ttu-id="8d2fc-112">Un « noir » délai pour des événements tels que les vacances</span><span class="sxs-lookup"><span data-stu-id="8d2fc-112">A "black-out" period for events such as vacations</span></span>  
  
-   <span data-ttu-id="8d2fc-113">L’intervalle sur lequel le portail n’envoie pas d’alertes en double</span><span class="sxs-lookup"><span data-stu-id="8d2fc-113">The interval over which the portal will not send duplicate alerts</span></span>  
  
 <span data-ttu-id="8d2fc-114">Vous pouvez effectuer les opérations suivantes sur les pages d’abonnement aux alertes ajouter et modifier un abonnement :</span><span class="sxs-lookup"><span data-stu-id="8d2fc-114">You can do the following on the Add Alert Subscription and Edit Subscription pages:</span></span>  
  
-   <span data-ttu-id="8d2fc-115">Sélectionnez la case à cocher à côté du **par courrier électronique personnalisé** texte si vous souhaitez utiliser une adresse de messagerie pour l’abonnement qui est différent de votre adresse de messagerie du compte Windows standard, puis tapez l’adresse de messagerie par défaut dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-115">Select the check box next to the **Custom Email** text box if you want to use an e-mail address for the subscription that is different to your standard Windows account e-mail address, and then type the preferred e-mail address in the text box.</span></span>  
  
-   <span data-ttu-id="8d2fc-116">Activez la case à cocher en haut de la **planification** section si vous souhaitez spécifier une période pendant laquelle le portail doit envoyer des alertes pour vous et puis spécifiez les heures de début et de fin pour la période de la **l’heure de début** et **Heure de fin** listes déroulantes.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-116">Select the check box at the top of the **Schedule** section if you want to specify a period when the portal should send alerts to you, and then specify the start and end times for the period in the **Start Time** and **End Time** drop-down lists.</span></span> <span data-ttu-id="8d2fc-117">Les alertes qui se produisent en dehors de cette période sont en file d’attente et remis pendant la période spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-117">Alerts occurring outside this period are queued and delivered during the specified period.</span></span>  
  
-   <span data-ttu-id="8d2fc-118">Tapez la date de début et date de fin pour un **temps mort** s’il existe une période lorsque vous ne pouvez pas recevoir et d’agir sur les alertes.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-118">Type the start date and end date for a **Black-out Period** if there is a period when you will be unable to receive and act on alerts.</span></span> <span data-ttu-id="8d2fc-119">Utilisez le format mm/jj/aaaa pour les deux dates.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-119">Use the format mm/dd/yyyy for the two dates.</span></span>  
  
-   <span data-ttu-id="8d2fc-120">Sélectionnez un **intervalle** dans **Minutes** pendant qui le portail de comparer les alertes déclenchées et qu’un seul envoi lorsque plusieurs instances de la même alerte se produisent.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-120">Select an **Interval** in **Minutes** during which the portal will compare alerts raised and send only one when multiple instances of the same alert occur.</span></span> <span data-ttu-id="8d2fc-121">Cela empêche une erreur qui se produisent rapidement à partir de la création d’un grand nombre de messages d’alerte identiques.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-121">This prevents a rapidly occurring fault from creating a large number of identical alert messages.</span></span>  
  
-   <span data-ttu-id="8d2fc-122">Cliquez sur le **enregistrer** bouton pour créer ou mettre à jour l’abonnement.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-122">Click the **Save** button to create or update the subscription.</span></span>  
  
-   <span data-ttu-id="8d2fc-123">Cliquez sur le **supprimer** bouton (disponible uniquement dans la page Modifier l’abonnement) pour supprimer l’abonnement sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-123">Click the **Delete** button (available only on the Edit Subscription page) to delete the selected subscription.</span></span>  
  
-   <span data-ttu-id="8d2fc-124">Cliquez sur le **Annuler** bouton pour revenir à la [Page visionneuse alerte](../esb-toolkit/alert-viewer-page.md) sans la création ou la modification de l’abonnement.</span><span class="sxs-lookup"><span data-stu-id="8d2fc-124">Click the **Cancel** button to go back to the [Alert Viewer Page](../esb-toolkit/alert-viewer-page.md) without creating or modifying the subscription.</span></span>