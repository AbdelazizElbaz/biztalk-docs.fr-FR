---
title: "La définition d’une activité d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business activities, creating [Excel add-in]
- monitoring business activities [BAM], creating business activities [Excel add-in]
- monitoring business activities [BAM], Excel add-in
ms.assetid: 305e3718-46b4-45df-bd52-f7ae36621576
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74cb0bb6f2bd0a5f92f6029dda65d55d219bcc12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-define-a-business-activity"></a><span data-ttu-id="be678-102">Définition d'une activité d'entreprise</span><span class="sxs-lookup"><span data-stu-id="be678-102">How to Define a Business Activity</span></span>
<span data-ttu-id="be678-103">Pour indiquer les données à collecter pour les rapports, vous devez définir une activité BAM.</span><span class="sxs-lookup"><span data-stu-id="be678-103">To indicate the data you need to collect for reports, you must define a BAM activity.</span></span> <span data-ttu-id="be678-104">Une activité BAM contient la liste des étapes majeures et des éléments de données sur lesquels portera le suivi effectué par l'analyse BAM. La procédure suivante explique comment créer une activité à l'aide du complément Excel BAM.</span><span class="sxs-lookup"><span data-stu-id="be678-104">This contains a list of the important milestones and data items you want BAM to track. Use the BAM Excel add-in to create an activity as shown in the following procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be678-105">Une fois qu'une activité a été déployée, les actions que vous pouvez effectuer sur celle-ci sont restreintes.</span><span class="sxs-lookup"><span data-stu-id="be678-105">Once an activity has been deployed, the actions you can take on an activity become restricted.</span></span> <span data-ttu-id="be678-106">Par exemple, vous pouvez supprimer des éléments d'une activité mais dans ce cas, votre administrateur devra annuler le déploiement de tous les ensembles des activités et des vues BAM, puis les redéployer.</span><span class="sxs-lookup"><span data-stu-id="be678-106">Specifically, you cannot delete items from an activity unless you are prepared to have your administrator undeploy the entire BAM activity and view sets and then redeploy them.</span></span> <span data-ttu-id="be678-107">Ceci peut causer une interruption de l'affichage et une perte de données si l'administrateur n'effectue pas de sauvegarde et de restauration des données.</span><span class="sxs-lookup"><span data-stu-id="be678-107">This can cause an interruption of visibility and loss of data unless the administrator does a backup and restore of the data.</span></span>  
  
### <a name="to-create-a-business-activity"></a><span data-ttu-id="be678-108">Pour créer un activité d'entreprise</span><span class="sxs-lookup"><span data-stu-id="be678-108">To create a business activity</span></span>  
  
1.  <span data-ttu-id="be678-109">Ouvrez Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="be678-109">Open Microsoft Excel.</span></span>  
  
2.  <span data-ttu-id="be678-110">Dans la barre d’outils, cliquez sur le **BAM** élément de menu, puis cliquez sur **activité BAM**.</span><span class="sxs-lookup"><span data-stu-id="be678-110">On the menu tool bar, click the **BAM** menu item, and click **BAM Activity**.</span></span>  
  
     <span data-ttu-id="be678-111">Le **entreprise Assistant activité BAM** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="be678-111">The **Business Activity Monitoring Activity Wizard** appears.</span></span>  
  
3.  <span data-ttu-id="be678-112">Cliquez sur **nouvelle activité**.</span><span class="sxs-lookup"><span data-stu-id="be678-112">Click **New Activity**.</span></span>  
  
     <span data-ttu-id="be678-113">Le **nouvelle activité** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="be678-113">The **New Activity** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="be678-114">Tapez un nom descriptif pour l’activité dans le **nom de l’activité** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="be678-114">Type a descriptive name for the activity in the **Activity Name** text box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be678-115">Une activité doit comporter au moins un élément d'activité.</span><span class="sxs-lookup"><span data-stu-id="be678-115">An activity must contain at least one activity item.</span></span>  
  
#### <a name="to-create-a-new-item"></a><span data-ttu-id="be678-116">Pour créer un élément</span><span class="sxs-lookup"><span data-stu-id="be678-116">To create a new item</span></span>  
  
1.  <span data-ttu-id="be678-117">Cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="be678-117">Click **New Item**.</span></span>  
  
2.  <span data-ttu-id="be678-118">Dans le **nouvel élément d’activité** boîte de dialogue le **nouvel élément d’activité** , tapez un nom descriptif pour l’élément d’activité.</span><span class="sxs-lookup"><span data-stu-id="be678-118">In the **New Activity Item** dialog box, in the **New Activity Item** box, type a descriptive name for the activity item.</span></span>  
  
3.  <span data-ttu-id="be678-119">À partir de la **le type d’élément** menu déroulant, sélectionnez un type de cet élément.</span><span class="sxs-lookup"><span data-stu-id="be678-119">From the **Item type** drop-down menu, select a type for this item.</span></span> <span data-ttu-id="be678-120">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="be678-120">Possible values include:</span></span>  
  
    |<span data-ttu-id="be678-121">Type d’élément</span><span class="sxs-lookup"><span data-stu-id="be678-121">Item type</span></span>|<span data-ttu-id="be678-122"> Description</span><span class="sxs-lookup"><span data-stu-id="be678-122">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="be678-123">Étape majeure commerciale</span><span class="sxs-lookup"><span data-stu-id="be678-123">Business Milestone</span></span>|<span data-ttu-id="be678-124">Valeur de date et heure.</span><span class="sxs-lookup"><span data-stu-id="be678-124">A date/time value.</span></span> <span data-ttu-id="be678-125">Par exemple, la date d'approbation d'un bon de commande.</span><span class="sxs-lookup"><span data-stu-id="be678-125">For example, an approval date for a purchase order.</span></span>|  
    |<span data-ttu-id="be678-126">Données d'entreprise - Texte</span><span class="sxs-lookup"><span data-stu-id="be678-126">Business Data – Text</span></span>|<span data-ttu-id="be678-127">Chaîne de caractères alphanumériques.</span><span class="sxs-lookup"><span data-stu-id="be678-127">A string containing any alphanumeric characters.</span></span> <span data-ttu-id="be678-128">Par exemple, destinataire : code ville, Département/Province et Code Postal.</span><span class="sxs-lookup"><span data-stu-id="be678-128">For example, Ship to: City, State/Province and Zip/Postal code.</span></span>|  
    |<span data-ttu-id="be678-129">Données d'entreprise - Entier</span><span class="sxs-lookup"><span data-stu-id="be678-129">Business Data – Integer</span></span>|<span data-ttu-id="be678-130">Valeur de nombre entier.</span><span class="sxs-lookup"><span data-stu-id="be678-130">A whole number value.</span></span> <span data-ttu-id="be678-131">Par exemple, le nombre total d'achats.</span><span class="sxs-lookup"><span data-stu-id="be678-131">For example, the total number of purchases.</span></span>|  
    |<span data-ttu-id="be678-132">Données d'entreprise - Décimal</span><span class="sxs-lookup"><span data-stu-id="be678-132">Business Data – Decimal</span></span>|<span data-ttu-id="be678-133">Valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="be678-133">A decimal value.</span></span> <span data-ttu-id="be678-134">Par exemple, le montant total en euros du bon de commande.</span><span class="sxs-lookup"><span data-stu-id="be678-134">For example the total dollar amount of the PO.</span></span>|  
  
     <span data-ttu-id="be678-135">Si vous sélectionnez l’élément de type « Données entreprise-texte », vous devez entrer le nombre maximal de caractères pour la chaîne dans le **longueur maximale** boîte.</span><span class="sxs-lookup"><span data-stu-id="be678-135">If you select the item type "Business Data – Text", you must enter the maximum number of characters for the string in the **Maximum length** box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be678-136">Pour plus d'informations sur la création de ces éléments, voir la rubrique « Gestion des partenaires et analyse de l'activité d'entreprise » du didacticiel de Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="be678-136">For more information about creating these items, see "Partner Management and Business Activity Monitoring" in the Microsoft BizTalk Server tutorial.</span></span>  
  
4.  <span data-ttu-id="be678-137">Répétez les étapes 1 à 3 pour ajouter le nombre d'éléments nécessaires à cette activité.</span><span class="sxs-lookup"><span data-stu-id="be678-137">Repeat steps 1 through 3 to add as many items as needed to this activity.</span></span>  
  
5.  <span data-ttu-id="be678-138">Dès que l'exécution de l'Assistant Activité BAM est terminée, l'Assistant Vue BAM démarre automatiquement.</span><span class="sxs-lookup"><span data-stu-id="be678-138">After you complete the Business Activity Monitoring Activity Wizard, the Business Activity Monitoring View Wizard starts automatically.</span></span>  
  
 <span data-ttu-id="be678-139">Pour plus d’informations sur l’utilisation de cet Assistant, consultez [définition d’une vue BAM](../core/defining-a-bam-view.md).</span><span class="sxs-lookup"><span data-stu-id="be678-139">For more information about using this wizard, see [Defining a BAM View](../core/defining-a-bam-view.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be678-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be678-140">See Also</span></span>  
 <span data-ttu-id="be678-141">[Définition d’une vue BAM](../core/defining-a-bam-view.md) </span><span class="sxs-lookup"><span data-stu-id="be678-141">[Defining a BAM View](../core/defining-a-bam-view.md) </span></span>  
 [<span data-ttu-id="be678-142">Définir des vues et des activités d’entreprise dans Excel</span><span class="sxs-lookup"><span data-stu-id="be678-142">Defining Business Activities and Views in Excel</span></span>](../core/defining-business-activities-and-views-in-excel.md)