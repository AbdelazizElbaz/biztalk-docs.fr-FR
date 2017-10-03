---
title: Abonnement aux alertes | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfa46b63-c1c7-47cd-86b0-557fd322dc8f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02ef5f136002f5afca6e062362b92d25a20baa99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="subscribing-to-alerts"></a><span data-ttu-id="ab6ff-102">S’abonner aux alertes</span><span class="sxs-lookup"><span data-stu-id="ab6ff-102">Subscribing to Alerts</span></span>
### <a name="to-subscribe-to-an-alert"></a><span data-ttu-id="ab6ff-103">Pour vous abonner à une alerte</span><span class="sxs-lookup"><span data-stu-id="ab6ff-103">To subscribe to an alert</span></span>  
  
1.  <span data-ttu-id="ab6ff-104">Ouvrez le [Page alertes du portail](../esb-toolkit/portal-alerts-page.md) pour afficher une liste des alertes existantes et vos abonnements en cours pour ces alertes.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-104">Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md) to see a list of existing alerts and your current subscriptions to these alerts.</span></span>  
  
2.  <span data-ttu-id="ab6ff-105">Dans la colonne Action, cliquez sur le **AddSubscriber** icône pour une alerte existante.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-105">In the Action column, click the **AddSubscriber** icon for an existing alert.</span></span> <span data-ttu-id="ab6ff-106">Cette opération ouvre le [ajouter un abonnement aux alertes et modifier les Pages abonnement](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md).</span><span class="sxs-lookup"><span data-stu-id="ab6ff-106">This opens the [Add Alert Subscription and Edit Subscription Pages](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md).</span></span>  
  
3.  <span data-ttu-id="ab6ff-107">Le portail envoie des notifications d’alerte à l’adresse de messagerie associée au compte que vous utilisez pour accéder au portail.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-107">The portal sends alert notifications to the e-mail address associated with the account you use to access the portal.</span></span> <span data-ttu-id="ab6ff-108">Si vous souhaitez utiliser une adresse de messagerie différente, sélectionnez la case à cocher à côté du **par courrier électronique personnalisé** zone de texte, puis tapez l’adresse de messagerie par défaut dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-108">If you want to use a different e-mail address, select the check box next to the **Custom Email** text box, and then type the preferred e-mail address in the text box.</span></span>  
  
4.  <span data-ttu-id="ab6ff-109">Activez la case à cocher dans la **planification** section si vous souhaitez spécifier une période pendant laquelle le portail doit envoyer des alertes pour vous et puis spécifiez les heures de début et de fin pour la période de la **l’heure de début** et **EndTime** listes déroulantes.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-109">Select the check box in the **Schedule** section if you want to specify a period when the portal should send alerts to you, and then specify the start and end times for the period in the **Start Time** and **EndTime** drop-down lists.</span></span>  
  
5.  <span data-ttu-id="ab6ff-110">S’il existe une période lorsque vous ne pouvez pas recevoir et agissent sur les alertes, tapez les dates de début et de fin dans le **temps mort** cases.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-110">If there is a period when you will be unable to receive and act upon alerts, type the start and end dates in the **Black-out Period** boxes.</span></span>  
  
6.  <span data-ttu-id="ab6ff-111">Sélectionnez un **intervalle** dans **Minutes** pendant qui le portail de comparer les alertes déclenchées et qu’un seul envoi lorsque plusieurs instances de la même alerte se produisent.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-111">Select an **Interval** in **Minutes** during which the portal will compare alerts raised and send only one when multiple instances of the same alert occur.</span></span> <span data-ttu-id="ab6ff-112">Cela empêche une erreur qui se produisent rapidement à partir de la création d’un grand nombre de messages d’alerte identiques.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-112">This prevents a rapidly occurring fault from creating a large number of identical alert messages.</span></span>  
  
7.  <span data-ttu-id="ab6ff-113">Cliquez sur le **enregistrer** bouton permettant de créer le nouvel abonnement.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-113">Click the **Save** button to create the new subscription.</span></span>  
  
### <a name="to-edit-an-existing-alert-subscription"></a><span data-ttu-id="ab6ff-114">Pour modifier un abonnement aux alertes existant</span><span class="sxs-lookup"><span data-stu-id="ab6ff-114">To edit an existing alert subscription</span></span>  
  
1.  <span data-ttu-id="ab6ff-115">Ouvrez le [Page alertes du portail](../esb-toolkit/portal-alerts-page.md) pour afficher une liste des alertes existantes et vos abonnements en cours pour ces alertes.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-115">Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md) to see a list of existing alerts and your current subscriptions to these alerts.</span></span>  
  
2.  <span data-ttu-id="ab6ff-116">Cliquez sur le **modifier** lien en regard de l’abonnement que vous souhaitez modifier dans la liste dans le **Mes abonnements** section de la page pour ouvrir la [ajouter un abonnement aux alertes et modifier les Pages abonnement](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md).</span><span class="sxs-lookup"><span data-stu-id="ab6ff-116">Click the **Edit** link next to the subscription you want to modify in the list in the **My Subscriptions** section of the page to open the [Add Alert Subscription and Edit Subscription Pages](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md).</span></span>  
  
3.  <span data-ttu-id="ab6ff-117">Le portail envoie des notifications d’alerte à l’adresse de messagerie associée au compte que vous utilisez pour accéder au portail.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-117">The portal sends alert notifications to the e-mail address associated with the account you use to access the portal.</span></span> <span data-ttu-id="ab6ff-118">Si vous souhaitez utiliser une adresse de messagerie différente, sélectionnez la case à cocher à côté du **par courrier électronique personnalisé** zone de texte, puis tapez l’adresse de messagerie par défaut dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-118">If you want to use a different e-mail address, select the check box next to the **Custom Email** text box, and then type the preferred e-mail address in the text box.</span></span>  
  
4.  <span data-ttu-id="ab6ff-119">Activez la case à cocher dans la **planification** section si vous souhaitez spécifier une période pendant laquelle le portail doit envoyer des alertes pour vous et puis spécifiez les heures de début et de fin pour la période de la **l’heure de début** et **EndTime** listes déroulantes.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-119">Select the check box in the **Schedule** section if you want to specify a period when the portal should send alerts to you, and then specify the start and end times for the period in the **Start Time** and **EndTime** drop-down lists.</span></span>  
  
5.  <span data-ttu-id="ab6ff-120">Taper les dates de début et de fin pour un **temps mort** s’il existe une période lorsque vous ne pouvez pas recevoir et agissent sur les alertes.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-120">Type the start and end dates for a **Black-out Period** if there is a period when you will be unable to receive and act upon alerts.</span></span>  
  
6.  <span data-ttu-id="ab6ff-121">Sélectionnez un **intervalle** dans **Minutes** pendant le portail qui comparera les alertes déclenchées et qu’un seul enverra lorsque plusieurs instances de la même alerte se produisent.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-121">Select an **Interval** in **Minutes** during which the portal will compare alerts raised and will send only one when multiple instances of the same alert occur.</span></span> <span data-ttu-id="ab6ff-122">Cela empêche une erreur qui se produisent rapidement à partir de la création d’un grand nombre de messages d’alerte identiques.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-122">This prevents a rapidly occurring fault from creating a large number of identical alert messages.</span></span>  
  
7.  <span data-ttu-id="ab6ff-123">Cliquez sur le **enregistrer** bouton Mettre à jour l’abonnement.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-123">Click the **Save** button to update the subscription.</span></span>  
  
### <a name="to-delete-an-existing-alert-subscription"></a><span data-ttu-id="ab6ff-124">Pour supprimer un abonnement aux alertes existant</span><span class="sxs-lookup"><span data-stu-id="ab6ff-124">To delete an existing alert subscription</span></span>  
  
1.  <span data-ttu-id="ab6ff-125">Ouvrez le [Page alertes du portail](../esb-toolkit/portal-alerts-page.md) pour afficher une liste des alertes existantes et vos abonnements en cours pour ces alertes.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-125">Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md) to see a list of existing alerts and your current subscriptions to these alerts.</span></span>  
  
2.  <span data-ttu-id="ab6ff-126">Cliquez sur le **supprimer** lien en regard de l’abonnement que vous souhaitez supprimer dans la liste dans le **Mes abonnements** section de la page.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-126">Click the **Delete** link next to the subscription you want to delete in the list in the **My Subscriptions** section of the page.</span></span>