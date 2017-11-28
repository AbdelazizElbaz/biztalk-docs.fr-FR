---
title: "Comment créer une requête de recherche d’activité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Query Builder [BAM portal], creating queries
- queries [BAM], saving
- queries [BAM], creating
- queries [BAM], executing
- Query Builder [BAM portal], executing queries
- Query Builder [BAM portal], opening queries
- Query Builder [BAM portal], saving queries
- queries [BAM], opening
ms.assetid: 7940e47d-10e4-4eb1-b4e6-a8b98461e3a8
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: caca07dd077f171bc35f2e8e61260bb15940685f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-query-in-activity-search"></a><span data-ttu-id="d26c9-102">Création d'une requête dans Recherche d'activité</span><span class="sxs-lookup"><span data-stu-id="d26c9-102">How to Create a Query in Activity Search</span></span>
<span data-ttu-id="d26c9-103">Les utilisateurs finaux du processus d'entreprise et les autres utilisateurs qui ont besoin d'être avertis des événements et états correspondant à leur activité ont recours à des requêtes pour créer des recherches d'activité sur lesquelles baser des alertes.</span><span class="sxs-lookup"><span data-stu-id="d26c9-103">Business end users and other users who need to receive notification of events and status pertaining to their business use queries to create activity searches on which to base alerts.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d26c9-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d26c9-104">Prerequisites</span></span>  
 <span data-ttu-id="d26c9-105">Vous devez disposer d'une vue déployée.</span><span class="sxs-lookup"><span data-stu-id="d26c9-105">You must have a deployed view.</span></span>  
  
### <a name="to-open-a-query"></a><span data-ttu-id="d26c9-106">Pour ouvrir une requête</span><span class="sxs-lookup"><span data-stu-id="d26c9-106">To open a query</span></span>  
  
1.  <span data-ttu-id="d26c9-107">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Site Web du portail BAM**.</span><span class="sxs-lookup"><span data-stu-id="d26c9-107">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BAM Portal Web Site**.</span></span>  
  
2.  <span data-ttu-id="d26c9-108">Dans le **Mes vues** frame du portail, cliquez sur une vue existante pour développer les menus disponibles pour cette vue.</span><span class="sxs-lookup"><span data-stu-id="d26c9-108">In the **My Views** frame of the portal, click an existing view to expand the menus available to that view.</span></span>  
  
3.  <span data-ttu-id="d26c9-109">Cliquez sur **recherche d’activité** pour développer la liste des activités disponibles pour la vue.</span><span class="sxs-lookup"><span data-stu-id="d26c9-109">Click **Activity Search** to expand the list of activities available for the view.</span></span>  
  
4.  <span data-ttu-id="d26c9-110">Cliquez sur une activité dans la liste.</span><span class="sxs-lookup"><span data-stu-id="d26c9-110">Click an activity from the list.</span></span> <span data-ttu-id="d26c9-111">La page Recherche d'activité pour l'activité sélectionnée est chargée.</span><span class="sxs-lookup"><span data-stu-id="d26c9-111">This will load the Activity Search page for the selected activity.</span></span>  
  
5.  <span data-ttu-id="d26c9-112">Dans le cadre contenu, en haut de la page, cliquez sur le **Parcourir** bouton pour ouvrir la **choisir un fichier** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d26c9-112">In the content frame, at the top of the page, click the **Browse** button to open the **Choose file** dialog box.</span></span>  
  
6.  <span data-ttu-id="d26c9-113">Accédez au dossier dans lequel vous avez préalablement enregistré les requêtes.</span><span class="sxs-lookup"><span data-stu-id="d26c9-113">Browse to the folder where you have previously saved queries.</span></span>  
  
7.  <span data-ttu-id="d26c9-114">Cliquez sur Enregistrer requête.</span><span class="sxs-lookup"><span data-stu-id="d26c9-114">Click a save query.</span></span>  
  
8.  <span data-ttu-id="d26c9-115">Cliquez sur le **ouvrir** bouton.</span><span class="sxs-lookup"><span data-stu-id="d26c9-115">Click the **Open** button.</span></span> <span data-ttu-id="d26c9-116">Charger le chemin d’accès à la requête dans la zone de texte à gauche de la **Parcourir** bouton.</span><span class="sxs-lookup"><span data-stu-id="d26c9-116">This will load the path to the query in the text box to the left of the **Browse** button.</span></span> <span data-ttu-id="d26c9-117">Vous pouvez également entrer directement le chemin de la requête dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="d26c9-117">You can also type the path to the query directly into the text box.</span></span>  
  
9. <span data-ttu-id="d26c9-118">Cliquez sur le **ouvrir la requête** bouton à droite de la **Parcourir** bouton.</span><span class="sxs-lookup"><span data-stu-id="d26c9-118">Click the **Open Query** button to the right of the **Browse** button.</span></span>  
  
### <a name="to-construct-a-query"></a><span data-ttu-id="d26c9-119">Pour créer une requête</span><span class="sxs-lookup"><span data-stu-id="d26c9-119">To construct a query</span></span>  
  
1.  <span data-ttu-id="d26c9-120">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Site Web du portail BAM**.</span><span class="sxs-lookup"><span data-stu-id="d26c9-120">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BAM Portal Web Site**.</span></span>  
  
2.  <span data-ttu-id="d26c9-121">Dans le **Mes vues** frame du portail est une liste de configuré des vues.</span><span class="sxs-lookup"><span data-stu-id="d26c9-121">In the **My Views** frame of the portal there is a list of currently configured views.</span></span> <span data-ttu-id="d26c9-122">Sous chaque vue figurent les trois tâches que vous pouvez y effectuer.</span><span class="sxs-lookup"><span data-stu-id="d26c9-122">Under each view there are three tasks that can be performed on the view.</span></span> <span data-ttu-id="d26c9-123">Si la vue est actuellement réduite, cliquez dessus pour développer la liste des tâches.</span><span class="sxs-lookup"><span data-stu-id="d26c9-123">If the view is currently collapsed, click the existing view to expand the list of tasks.</span></span>  
  
3.  <span data-ttu-id="d26c9-124">Cliquez sur **recherche d’activité** pour développer la liste des activités disponibles pour la vue.</span><span class="sxs-lookup"><span data-stu-id="d26c9-124">Click **Activity Search** to expand the list of activities available for the view.</span></span>  
  
4.  <span data-ttu-id="d26c9-125">Cliquez sur une activité dans la liste.</span><span class="sxs-lookup"><span data-stu-id="d26c9-125">Click an activity from the list.</span></span> <span data-ttu-id="d26c9-126">La page Recherche d'activité pour l'activité sélectionnée est chargée.</span><span class="sxs-lookup"><span data-stu-id="d26c9-126">This will load the Activity Search page for the selected activity.</span></span>  
  
5.  <span data-ttu-id="d26c9-127">Dans le cadre contenu, dans le **requête** , choisissez un champ à partir de la **données d’entreprise** liste déroulante à utiliser pour une comparaison dans la requête.</span><span class="sxs-lookup"><span data-stu-id="d26c9-127">In the content frame, in the **Query** box, choose a field from the **Business Data** drop-down list to use for a comparison in the query.</span></span>  
  
6.  <span data-ttu-id="d26c9-128">À partir de la **opérateur** liste déroulante, sélectionnez l’opérateur de comparaison à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d26c9-128">From the **Operator** drop-down list, select the comparison operator to use.</span></span>  
  
7.  <span data-ttu-id="d26c9-129">Dans le **valeur** , entrez la valeur à comparer.</span><span class="sxs-lookup"><span data-stu-id="d26c9-129">In the **Value** box, enter the value to compare against.</span></span> <span data-ttu-id="d26c9-130">Vous pourrez entrer uniquement une valeur adaptée au champ avec lequel effectuer la comparaison.</span><span class="sxs-lookup"><span data-stu-id="d26c9-130">You will only be able to enter a value appropriate to the field to which you are comparing.</span></span> <span data-ttu-id="d26c9-131">(Si l'élément de données d'entreprise est un champ de date, les données de comparaison sont une date ou une date et une heure formatées selon vos paramètres régionaux.)</span><span class="sxs-lookup"><span data-stu-id="d26c9-131">(If the business data item is a date field, then the comparison data is a date or date time formatted as appropriate for your culture settings.)</span></span>  
  
8.  <span data-ttu-id="d26c9-132">Si vous avez des clauses à ajouter à la requête, cliquez sur le **ajouter** bouton à droite de la zone de requête.</span><span class="sxs-lookup"><span data-stu-id="d26c9-132">If you have more clauses to add to the query, click the **Add** button to the right of the query box.</span></span> <span data-ttu-id="d26c9-133">Une nouvelle ligne est alors ajoutée pour la clause suivante.</span><span class="sxs-lookup"><span data-stu-id="d26c9-133">This will add a new line for the next clause.</span></span> <span data-ttu-id="d26c9-134">Vous pouvez choisir de joindre ou non les clauses en utilisant AND ou OR.</span><span class="sxs-lookup"><span data-stu-id="d26c9-134">You can select whether the clauses are join by using an AND or an OR.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d26c9-135">Vous ne pouvez pas regrouper des clauses pour constituer des requêtes plus complexes.</span><span class="sxs-lookup"><span data-stu-id="d26c9-135">You cannot group clauses to form more complex queries.</span></span> <span data-ttu-id="d26c9-136">Une requête est un ensemble simple de clauses jointes par un opérateur AND ou OR.</span><span class="sxs-lookup"><span data-stu-id="d26c9-136">A query is a simple set of clauses joined by an AND or an OR operator.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d26c9-137">Si vous cliquez sur le bouton précédent pendant ces procédures et que vous recevez un « avertissement : page a expiré, « vous pouvez appuyer sur F5 pour revenir à votre contenu d’origine.</span><span class="sxs-lookup"><span data-stu-id="d26c9-137">If you click the back button during these procedures and receive a "warning: page has expired," you can press F5 to get your original contents back.</span></span> <span data-ttu-id="d26c9-138">Vous devrez éventuellement appuyer plusieurs fois sur F5.</span><span class="sxs-lookup"><span data-stu-id="d26c9-138">You may have to press F5 several times.</span></span>  
  
9. <span data-ttu-id="d26c9-139">Dans le sélecteur de colonne, sélectionnez les données ou les étapes majeures à partir de la **données disponibles et les étapes majeures** zone de liste pour la requête retourner sous forme de données.</span><span class="sxs-lookup"><span data-stu-id="d26c9-139">In the Column Chooser select the data or milestones from the **Available Data and Milestones** list box for the query to return as data.</span></span> <span data-ttu-id="d26c9-140">Il est possible de sélectionner plusieurs éléments adjacents en cliquant sur le premier élément puis, tout en maintenant enfoncée la touche MAJ, sur le dernier élément du groupe à retourner.</span><span class="sxs-lookup"><span data-stu-id="d26c9-140">You can select multiple items by holding down the SHIFT key and clicking the first and last items in the group you want to return.</span></span> <span data-ttu-id="d26c9-141">Vous pouvez également sélectionner plusieurs éléments de la liste en maintenant enfoncée la touche CTRL et en sélectionnant les divers éléments à retourner.</span><span class="sxs-lookup"><span data-stu-id="d26c9-141">You can also select multiple items from the list by holding down the CTRL key and selecting the items to return.</span></span>  
  
10. <span data-ttu-id="d26c9-142">Utilisez le  **>>**  bouton pour déplacer les éléments sélectionnés vers le **éléments à afficher** zone de liste.</span><span class="sxs-lookup"><span data-stu-id="d26c9-142">Use the **>>** button to move the selected items to the **Items to show** list box.</span></span> <span data-ttu-id="d26c9-143">Vous pouvez supprimer des éléments dans cette liste en les sélectionnant et en utilisant le  **<<**  bouton à les replacer dans la zone de liste données et étapes majeures.</span><span class="sxs-lookup"><span data-stu-id="d26c9-143">You can remove items from this list by selecting them and using the **<<** button to move them back to the data and milestones list box.</span></span>  
  
11. <span data-ttu-id="d26c9-144">Une fois que vous avez sélectionné tous les éléments à retourner par la requête, vous pouvez réorganiser les résultats pour déterminer l'ordre d'affichage des colonnes.</span><span class="sxs-lookup"><span data-stu-id="d26c9-144">Once you have selected all the items that the query will return, you can rearrange the results to determine in what order the columns are shown.</span></span> <span data-ttu-id="d26c9-145">Pour déplacer une colonne à la première position dans le jeu de données retourné, sélectionnez-le en cliquant dessus et en cliquant sur le **monter** bouton jusqu'à ce qu’il soit en haut de la liste des éléments.</span><span class="sxs-lookup"><span data-stu-id="d26c9-145">To move a column to the first position in the returned data set, select it by clicking it and clicking the **Move Up** button until it is at the top of the list of items.</span></span> <span data-ttu-id="d26c9-146">De même, pour déplacer un élément à une position postérieure dans le jeu de données retourné, sélectionnez l’élément en cliquant dessus, puis en cliquant sur le **Descendre** bouton jusqu'à ce qu’il se trouve dans la position dans laquelle vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="d26c9-146">Similarly, to move an item to a later position in the returned data set, select the item by clicking it and then clicking the **Move Down** button until it is in the position in which you want it to display.</span></span>  
  
### <a name="to-save-a-query"></a><span data-ttu-id="d26c9-147">Pour enregistrer une requête</span><span class="sxs-lookup"><span data-stu-id="d26c9-147">To save a query</span></span>  
  
1.  <span data-ttu-id="d26c9-148">Dans le cadre contenu, en haut de la page, cliquez sur le **enregistrer la requête** bouton pour ouvrir la **enregistrer le fichier** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d26c9-148">In the content frame, at the top of the page, click the **Save Query** button to open the **Save File** dialog box.</span></span>  
  
2.  <span data-ttu-id="d26c9-149">Sur le **télécharger le fichier** boîte de dialogue, cliquez sur le **enregistrer** bouton.</span><span class="sxs-lookup"><span data-stu-id="d26c9-149">On the **File Download** dialog box, click the **Save** button.</span></span>  
  
3.  <span data-ttu-id="d26c9-150">Accédez à l'emplacement où vous souhaitez enregistrer la requête.</span><span class="sxs-lookup"><span data-stu-id="d26c9-150">Browse to the location where you want to save the query.</span></span>  
  
4.  <span data-ttu-id="d26c9-151">Vous pouvez accepter le nom par défaut de la requête ou vous pouvez entrer un nouveau nom dans la **nom de fichier** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="d26c9-151">You can accept the default name provided for the query or you can enter a new name in the **File Name** text box.</span></span>  
  
5.  <span data-ttu-id="d26c9-152">Cliquez sur le **enregistrer** bouton.</span><span class="sxs-lookup"><span data-stu-id="d26c9-152">Click the **Save** button.</span></span>  
  
### <a name="to-execute-a-query"></a><span data-ttu-id="d26c9-153">Pour exécuter une requête</span><span class="sxs-lookup"><span data-stu-id="d26c9-153">To execute a query</span></span>  
  
1.  <span data-ttu-id="d26c9-154">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Site Web du portail BAM**.</span><span class="sxs-lookup"><span data-stu-id="d26c9-154">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BAM Portal Web Site**.</span></span>  
  
2.  <span data-ttu-id="d26c9-155">Dans le **Mes vues** frame du portail, cliquez sur une vue existante pour développer les menus disponibles pour cette vue.</span><span class="sxs-lookup"><span data-stu-id="d26c9-155">In the **My Views** frame of the portal, click an existing view to expand the menus available to that view.</span></span>  
  
3.  <span data-ttu-id="d26c9-156">Cliquez sur **recherche d’activité** pour développer la liste des activités disponibles pour la vue.</span><span class="sxs-lookup"><span data-stu-id="d26c9-156">Click **Activity Search** to expand the list of activities available for the view.</span></span>  
  
4.  <span data-ttu-id="d26c9-157">Cliquez sur une activité dans la liste.</span><span class="sxs-lookup"><span data-stu-id="d26c9-157">Click an activity from the list.</span></span> <span data-ttu-id="d26c9-158">La page Recherche d'activité pour l'activité sélectionnée est chargée.</span><span class="sxs-lookup"><span data-stu-id="d26c9-158">This will load the Activity Search page for the selected activity.</span></span>  
  
5.  <span data-ttu-id="d26c9-159">Ouvrez une requête existante ou créez-en une.</span><span class="sxs-lookup"><span data-stu-id="d26c9-159">Either open an existing query or build a new query.</span></span>  
  
6.  <span data-ttu-id="d26c9-160">Dans le cadre contenu du portail, cliquez sur le **exécuter la requête** bouton.</span><span class="sxs-lookup"><span data-stu-id="d26c9-160">In the content frame of the portal, click the **Execute Query** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d26c9-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d26c9-161">See Also</span></span>  
 [<span data-ttu-id="d26c9-162">Recherches d’activité dans le portail BAM</span><span class="sxs-lookup"><span data-stu-id="d26c9-162">Activity Searches in the BAM Portal</span></span>](../core/activity-searches-in-the-bam-portal.md)