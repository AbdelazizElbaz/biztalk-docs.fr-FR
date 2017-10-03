---
title: "Comment définir une alerte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- alerts, creating
- Query Builder [BAM portal], creating alerts
- queries [BAM], aggregations
- Query Builder [BAM portal], activity searches
- Query Builder [BAM portal], aggregation alerts
- queries [BAM], alerts
- aggregations, alerts
ms.assetid: 8745d2c6-5bc0-4d7a-8c17-361535f5c6e6
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 774fbab86c1da1389b813f621c89f38cf0aa7656
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-an-alert"></a><span data-ttu-id="6f2a5-102">Définition d'une alerte</span><span class="sxs-lookup"><span data-stu-id="6f2a5-102">How to Set an Alert</span></span>
<span data-ttu-id="6f2a5-103">Vous pouvez définir une alerte en la joignant à une recherche d'activité ou en parcourant une agrégation.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-103">You can set an alert by attaching it to an activity search or drilling down through an aggregation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f2a5-104">Avant de définir une alerte sur une requête, il est préférable que vous exécutiez cette dernière et évaluiez si les durées des cycles d'alerte sont appropriées pour le processus dont vous effectuez l'analyse.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-104">Before setting an alert on a query, you should run the query and evaluate whether the alert cycle durations are appropriate for the process you are monitoring.</span></span> <span data-ttu-id="6f2a5-105">Si la durée d'un cycle est trop brève, il est possible qu'une condition d'alerte soit transitoire et qu'elle soit manquée par le système d'alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-105">If the cycle duration is too short, it is possible for an alert condition to occur in a transient manner and thus be missed by the alerting system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f2a5-106">Si vous cliquez sur le bouton précédent pendant ces procédures, vous pouvez recevoir le message suivant : « avertissement : page a expiré. »</span><span class="sxs-lookup"><span data-stu-id="6f2a5-106">If you click the back button during these procedures, you may receive the following message: "Warning: page has expired."</span></span> <span data-ttu-id="6f2a5-107">Pour revenir au contenu précédent, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-107">To return to the previous content, press F5.</span></span> <span data-ttu-id="6f2a5-108">(Vous devrez peut-être appuyer plusieurs fois sur F5.)</span><span class="sxs-lookup"><span data-stu-id="6f2a5-108">(You may have to press F5 several times.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f2a5-109">Lorsque vous créerez la première alerte dans une vue, aucune donnée associée ne sera affichée.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-109">When you create the first alert on a view, there will be no data displayed for the alert.</span></span> <span data-ttu-id="6f2a5-110">La définition d'une alerte n'entraîne pas la collection de données à partir du laps de temps précédant sa création.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-110">Defining an alert does not collect alert data from the time frame before the alert was created.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6f2a5-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="6f2a5-111">Prerequisites</span></span>  
 <span data-ttu-id="6f2a5-112">La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="6f2a5-112">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
-   <span data-ttu-id="6f2a5-113">Vous devez disposer d'une vue déployée.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-113">You must have a deployed view.</span></span>  
  
-   <span data-ttu-id="6f2a5-114">Vous devez disposez d'une recherche d'activité pour une alerte d'instance.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-114">You must have an activity search for an instance alert.</span></span>  
  
-   <span data-ttu-id="6f2a5-115">Vous devez disposer d'une agrégation renseignée pour une alerte d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-115">You must have a populated aggregation for an aggregation alert.</span></span>  
  
### <a name="to-set-an-alert-on-an-activity-search"></a><span data-ttu-id="6f2a5-116">Pour définir une alerte sur une recherche d'activité.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-116">To set an alert on an activity search</span></span>  
  
1.  <span data-ttu-id="6f2a5-117">Dans le **Mes vues** frame, cliquez sur une vue pour développer la liste des tâches pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-117">In the **My Views** frame, click a view to expand the list of tasks for the view.</span></span>  
  
2.  <span data-ttu-id="6f2a5-118">Cliquez sur le **recherche d’activité** tâche sous la vue que vous avez développé.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-118">Click the **Activity Search** task under the view you expanded.</span></span>  
  
3.  <span data-ttu-id="6f2a5-119">Créez ou ouvrez une recherche d'activité.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-119">Create or open an activity search.</span></span> <span data-ttu-id="6f2a5-120">Pour plus d’informations sur la procédure à suivre, consultez [la création d’une requête de recherche d’activité](../core/how-to-create-a-query-in-activity-search.md).</span><span class="sxs-lookup"><span data-stu-id="6f2a5-120">For information about how to do this, see [How to Create a Query in Activity Search](../core/how-to-create-a-query-in-activity-search.md).</span></span>  
  
4.  <span data-ttu-id="6f2a5-121">Dans le cadre contenu du portail BAM, cliquez sur le **définir l’alerte** bouton.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-121">In the content frame of the BAM portal, click the **Set Alert** button.</span></span> <span data-ttu-id="6f2a5-122">Le frame de contenu sera chargé avec le modèle de création de l'alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-122">The content frame will load with the alert creation template.</span></span>  
  
5.  <span data-ttu-id="6f2a5-123">Dans le **nom** texte, tapez un nom descriptif pour l’alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-123">In the **Name** text box, type a descriptive name for the alert.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f2a5-124">Les noms sont limités à 100 caractères et ne peut pas contenir les caractères suivants : ~ ! @# $% ^&amp;* () ;  Si vous entrez un de ces caractères dans un nom, une bordure rouge pointillée apparaît autour du champ de texte signalant une erreur que vous devez corriger pour terminer l’action.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-124">Names are limited to 100 characters and cannot contain the following characters: ~!@#$%^&amp;*();  If you enter any of these characters in a name, a dashed red border appears around the text field indicating an error that you must correct to complete the action.</span></span>  
  
6.  <span data-ttu-id="6f2a5-125">Si vous ne souhaitez pas l’alerte soit activée pour l’instant, désactivez le **alerte activée** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-125">If you do not want the alert enabled at this time, clear the **Alert Enabled** check box.</span></span>  
  
7.  <span data-ttu-id="6f2a5-126">Dans le **Message** texte, tapez le message est remis lorsque l’alerte est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-126">In the **Message** text box, type the message that is delivered when the alert is triggered.</span></span>  
  
8.  <span data-ttu-id="6f2a5-127">À partir de la **priorité** liste déroulante, sélectionnez le niveau de priorité pour cette alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-127">From the **Priority** drop-down list, choose the priority level for this alert.</span></span> <span data-ttu-id="6f2a5-128">Le paramètre de priorité indique la gravité du problème sur laquelle l'alerte a été définie.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-128">The priority setting indicates the severity of the issue on which the alert was set.</span></span>  
  
9. <span data-ttu-id="6f2a5-129">Dans le **propriétaires** zone de texte, tapez les alias des propriétaires de cette alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-129">In the **Owners** text box, type the aliases of the owners of this alert.</span></span> <span data-ttu-id="6f2a5-130">Utilisez des points-virgules entre les noms de plusieurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-130">Use semicolons between the names of multiple users.</span></span>  
  
10. <span data-ttu-id="6f2a5-131">Dans le **alerte sécurité** zone, sélectionnez la case à cocher pour autoriser d’autres utilisateurs à voir cette alerte et vous abonner à ce dernier.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-131">In the **Alert Security** area, select the check box to allow other users to see this alert and subscribe to it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f2a5-132">Vous pouvez basculer entre la sécurité d'alerte privée et publique à tout moment ; l'existence d'abonnés à l'alerte n'a pas d'incidence sur cette action.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-132">You can switch the alert security between private and public at any time; the presence of subscribers to the alert does not affect this action.</span></span> <span data-ttu-id="6f2a5-133">Néanmoins, lorsque vous faites passer la sécurité d'alerte de publique à privée, demandez-vous s'il y a des abonnés à l'alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-133">When you switch the alert security from public to private, however, you should consider whether there are any subscribers to the alert.</span></span> <span data-ttu-id="6f2a5-134">Si c'est le cas, ils n'auront aucun moyen de modifier leur abonnement à partir du moment où l'alerte sera privée.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-134">If there are subscribers to the alert, they will have no way to edit their subscription when the alert is made private.</span></span>  
  
11. <span data-ttu-id="6f2a5-135">Dans le coin supérieur droit de la **détails de l’alerte** zone, cliquez sur le **enregistrer l’alerte** bouton.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-135">In the upper-right corner of the **Alert Details** area, click the **Save Alert** button.</span></span>  
  
### <a name="to-set-an-alert-on-an-aggregation"></a><span data-ttu-id="6f2a5-136">Pour définir une alerte sur une agrégation</span><span class="sxs-lookup"><span data-stu-id="6f2a5-136">To set an alert on an aggregation</span></span>  
  
1.  <span data-ttu-id="6f2a5-137">Dans le **Mes vues** frame, cliquez sur une vue pour développer la liste des tâches pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-137">In the **My Views** frame, click a view to expand the list of tasks for the view.</span></span>  
  
2.  <span data-ttu-id="6f2a5-138">Cliquez sur le **agrégations** de tâches dans **Mes vues** sous la vue que vous avez développé.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-138">Click the **Aggregations** task in **My Views** under the view you expanded.</span></span>  
  
3.  <span data-ttu-id="6f2a5-139">Dans le frame de contenu du portail BAM, cliquez avec le bouton droit sur une cellule de la colonne des totaux du rapport de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-139">In the content frame of the BAM portal, right-click a cell in the totals column of the PivotTable report.</span></span> <span data-ttu-id="6f2a5-140">Cela aura pour effet d'ouvrir un menu contextuel contenant des fonctions à exécuter sur le total d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-140">This opens a context menu with functions that are available to perform on the aggregation total.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f2a5-141">Vous pouvez définir une alerte sur un composant spécifique du total d'agrégation en développant cet élément de ligne.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-141">You can set an alert on a specific component of the aggregation total by expanding that line item.</span></span> <span data-ttu-id="6f2a5-142">Vous pouvez développer de cette façon plusieurs niveaux se succédant jusqu'à ce que vous ayez atteint le niveau auquel vous désirez définir votre alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-142">You can expand succeeding levels in this manner until you reach the level at which you want to set your alert.</span></span>  
  
4.  <span data-ttu-id="6f2a5-143">En haut du menu contextuel, cliquez sur **créer une alerte**.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-143">At the top of the context menu, click **Create Alert**.</span></span> <span data-ttu-id="6f2a5-144">Le frame de contenu sera chargé avec le modèle de création de l'alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-144">The content frame will load with the alert creation template.</span></span>  
  
5.  <span data-ttu-id="6f2a5-145">Dans le **nom** texte, tapez un nom descriptif pour l’alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-145">In the **Name** text box, type a descriptive name for the alert.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f2a5-146">Les noms sont limités à 100 caractères et ne peut pas contenir les caractères suivants : ~ ! @# $% ^&amp;* () ;  Si vous entrez un de ces caractères dans un nom, une bordure rouge pointillée apparaît autour du champ de texte signalant une erreur que vous devez corriger pour terminer l’action.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-146">Names are limited to 100 characters and cannot contain the following characters: ~!@#$%^&amp;*();  If you enter any of these characters in a name, a dashed red border appears around the text field indicating an error that you must correct to complete the action.</span></span>  
  
6.  <span data-ttu-id="6f2a5-147">Si vous ne souhaitez pas l’alerte soit activée pour l’instant, désactivez le **alerte activée** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-147">If you do not want the alert enabled at this time, clear the **Alert Enabled** check box.</span></span>  
  
7.  <span data-ttu-id="6f2a5-148">Dans le **Message** texte, tapez le message est remis lorsque l’alerte est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-148">In the **Message** text box, type the message that is delivered when the alert is triggered.</span></span>  
  
8.  <span data-ttu-id="6f2a5-149">À partir de la **priorité** liste déroulante, sélectionnez le niveau de priorité pour cette alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-149">From the **Priority** drop-down list, choose the priority level for this alert.</span></span> <span data-ttu-id="6f2a5-150">Le paramètre de priorité indique la gravité du problème sur laquelle l'alerte a été définie.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-150">The priority setting indicates the severity of the issue on which the alert was set.</span></span>  
  
9. <span data-ttu-id="6f2a5-151">Dans le **propriétaires** zone de texte, tapez les alias des propriétaires de cette alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-151">In the **Owners** text box, type the aliases of the owners of this alert.</span></span> <span data-ttu-id="6f2a5-152">Utilisez des points-virgules entre les noms de plusieurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-152">Use semicolons between the names of multiple users.</span></span>  
  
10. <span data-ttu-id="6f2a5-153">Dans le **seuil** zone, sélectionnez une condition de comparaison de la **nombre** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-153">In the **Threshold** area, select a comparison condition from the **Count** drop-down list.</span></span>  
  
11. <span data-ttu-id="6f2a5-154">Dans le **durée** texte, entrez le nombre d’unités de temps sur laquelle le seuil est mesuré.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-154">In the **Duration** text box, enter the number of time units across which the threshold is measured.</span></span>  
  
12. <span data-ttu-id="6f2a5-155">À partir de la **durée** liste déroulante, sélectionnez l’unité de temps.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-155">From the **Duration** drop-down list, select the unit of time.</span></span>  
  
13. <span data-ttu-id="6f2a5-156">Dans le **alerte sécurité** zone, sélectionnez la case à cocher pour autoriser d’autres utilisateurs à voir cette alerte et vous abonner à ce dernier.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-156">In the **Alert Security** area, select the check box to allow other users to see this alert and subscribe to it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f2a5-157">Vous pouvez basculer entre la sécurité d'alerte privée et publique à tout moment ; l'existence d'abonnés à l'alerte n'a pas d'incidence sur cette action.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-157">You can switch the alert security between private and public at any time; the presence of subscribers to the alert does not affect this action.</span></span> <span data-ttu-id="6f2a5-158">Néanmoins, lorsque vous faites passer la sécurité d'alerte de publique à privée, demandez-vous s'il y a des abonnés à l'alerte.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-158">When you switch the alert security from public to private, however, you should consider whether there are any subscribers to the alert.</span></span> <span data-ttu-id="6f2a5-159">Si c'est le cas, ils n'auront aucun moyen de modifier leur abonnement à partir du moment où l'alerte sera privée.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-159">If there are subscribers to the alert, they will have no way to edit their subscription when the alert is made private.</span></span>  
  
14. <span data-ttu-id="6f2a5-160">Dans le coin supérieur droit de la **détails de l’alerte** zone, cliquez sur le **enregistrer l’alerte** bouton.</span><span class="sxs-lookup"><span data-stu-id="6f2a5-160">In the upper-right corner of the **Alert Details** area, click the **Save Alert** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f2a5-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f2a5-161">See Also</span></span>  
 [<span data-ttu-id="6f2a5-162">Comment créer une requête de recherche d’activité</span><span class="sxs-lookup"><span data-stu-id="6f2a5-162">How to Create a Query in Activity Search</span></span>](../core/how-to-create-a-query-in-activity-search.md)