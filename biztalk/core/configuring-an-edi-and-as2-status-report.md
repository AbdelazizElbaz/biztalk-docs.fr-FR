---
title: "Configurer un EDI et le rapport d’état AS2 | Documents Microsoft"
description: "Créer l’EDI ou expression de requête de rapport d’état AS2 et sélectionner les données que vous souhaitez afficher dans le rapport pour dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6490864d-f1e6-4932-aefb-c332a595aad7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 833e3c6c26cdac57d7cc57d828b66a66b9eb37f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-an-edi-and-as2-status-report"></a><span data-ttu-id="fba3d-103">Configurer un EDI et le rapport d’état AS2</span><span class="sxs-lookup"><span data-stu-id="fba3d-103">Configure an EDI and AS2 Status Report</span></span>
<span data-ttu-id="fba3d-104">Une fois que vous avez activé EDI ou de rapports d’état AS2, vous affichez le rapport d’état souhaité à partir de la **rapports d’état EDI** ou **rapports d’état EDIINT** section de la **Hub du groupe** onglet de la **vue d’ensemble du groupe** page dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="fba3d-104">After you have enabled EDI or AS2 status reports, you display the status report you want from the **EDI Status Reports** or **EDIINT Status Reports** section of the **Group Hub** tab of the **Group Overview** page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="fba3d-105">Lorsque vous affichez un rapport d'état, vous verrez un ensemble de données par défaut.</span><span class="sxs-lookup"><span data-stu-id="fba3d-105">When you display a status report, you will see a default set of data.</span></span> <span data-ttu-id="fba3d-106">Vous pouvez configurer les aspects suivants des rapports d'état :</span><span class="sxs-lookup"><span data-stu-id="fba3d-106">You can configure the following aspects of the status reports:</span></span>  
  
-   <span data-ttu-id="fba3d-107">L'expression de requête qui est exécutée pour déterminer la plage des données pour lesquelles l'état est rapporté, par exemple, la plage de dates, le sens des données (reçues ou envoyées), ou la valeur d'état (Acceptée, Rejetée, Tout, etc.)</span><span class="sxs-lookup"><span data-stu-id="fba3d-107">The query expression that is run to determine the range of data that status is reported for, for example, the date range, the direction of the data (receive or send), or the status value (Accepted, Rejected, All, etc.)</span></span>  
  
-   <span data-ttu-id="fba3d-108">Le type de données affichées dans le volet de rapport d'état, comme déterminé par les colonnes de données dans le rapport.</span><span class="sxs-lookup"><span data-stu-id="fba3d-108">The type of data displayed in the status report pane, as determined by the data columns in the report.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fba3d-109">À chaque fois que les rapports d'état sont activés, tous les états seront enregistrés dans le stockage.</span><span class="sxs-lookup"><span data-stu-id="fba3d-109">Whenever status reporting is enabled, all status will be saved in storage.</span></span> <span data-ttu-id="fba3d-110">En personnalisant l'expression de requête ou les colonnes d'état, vous définissez quelles données enregistrées sont affichées.</span><span class="sxs-lookup"><span data-stu-id="fba3d-110">By customizing the query expression or status columns, you are defining which saved data is displayed.</span></span>  
  
 <span data-ttu-id="fba3d-111">Cinq rapports d’état EDI et AS2 différents sont disponibles (voir [Types de rapports EDI et AS2 état](../core/types-of-edi-and-as2-status-reports.md)).</span><span class="sxs-lookup"><span data-stu-id="fba3d-111">Five different EDI and AS2 status reports are available (see [Types of EDI and AS2 Status Reports](../core/types-of-edi-and-as2-status-reports.md)).</span></span> <span data-ttu-id="fba3d-112">La manière dont vous configurez chaque rapport est la même, même si les données pour chaque rapport sont différentes.</span><span class="sxs-lookup"><span data-stu-id="fba3d-112">The way that you configure each report is the same, even though the data for each report is different.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fba3d-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="fba3d-113">Prerequisites</span></span>  
 <span data-ttu-id="fba3d-114">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fba3d-114">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
## <a name="configure-the-status-report-query-expression"></a><span data-ttu-id="fba3d-115">Configurer l’expression de requête du rapport État</span><span class="sxs-lookup"><span data-stu-id="fba3d-115">Configure the status report query expression</span></span>  
  
1.  <span data-ttu-id="fba3d-116">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **groupe BizTalk** nœud pour afficher les **vue d’ensemble du groupe** volet.</span><span class="sxs-lookup"><span data-stu-id="fba3d-116">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **BizTalk Group** node to see the **Group Overview** pane.</span></span>  
  
2.  <span data-ttu-id="fba3d-117">Au bas de la **Hub du groupe** onglet dans le **vue d’ensemble du groupe** volet, cliquez sur le rapport d’état que vous souhaitez configurer, tel que **échange EDI et état ACK corrélé**.</span><span class="sxs-lookup"><span data-stu-id="fba3d-117">At the bottom of the **Group Hub** tab in the **Group Overview** pane, click the status report that you want to configure, such as **EDI Interchange and Correlated ACK Status**.</span></span>  
  
3.  <span data-ttu-id="fba3d-118">Dans le **Expression de requête** zone du volet de rapport d’état, vérifiez que tous les critères de filtre que vous souhaitez définir pour la requête sont présents.</span><span class="sxs-lookup"><span data-stu-id="fba3d-118">In the **Query Expression** area of the status report pane, verify that all filter criteria that you want to define for the query are present.</span></span> <span data-ttu-id="fba3d-119">Dans le cas contraire, cliquez sur la flèche vers le bas dans la ligne vide dans le **nom de champ** colonne au bas de l’expression de requête et sélectionnez un critère de filtre que vous souhaitez ajouter à l’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="fba3d-119">If not, click the down arrow in the empty row in the **Field Name** column at the bottom of the query expression, and select any filter criteria that you want to add to the query expression.</span></span> <span data-ttu-id="fba3d-120">Vous pouvez supprimer une ligne de critères de filtre en sélectionnant la ligne en cliquant sur le **supprimer** bouton sur le clavier.</span><span class="sxs-lookup"><span data-stu-id="fba3d-120">You can delete a filter criteria row by selecting the row and clicking the **Delete** button on the keyboard.</span></span>  
  
4.  <span data-ttu-id="fba3d-121">Vérifiez que les valeurs pour les expressions de filtre sont celles désirées.</span><span class="sxs-lookup"><span data-stu-id="fba3d-121">Verify that the values for the filter expressions are as desired.</span></span> <span data-ttu-id="fba3d-122">Dans le cas contraire, cliquez sur la flèche bas de la **opérateur** colonne pour sélectionner une opération de requête, entrez la valeur appropriée dans le **valeur** colonne.</span><span class="sxs-lookup"><span data-stu-id="fba3d-122">If not, click the down arrow for the **Operator** column to select a query operation, and enter the appropriate value in the **Value** column.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fba3d-123">Les opérateurs et les valeurs disponibles pour les critères de filtre dans les expressions de requête sont décrits dans [Types de rapports EDI et AS2 état](../core/types-of-edi-and-as2-status-reports.md) et **l’interface utilisateur de rapports EDI AS2 état** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="fba3d-123">The operators and values available for filter criteria in the query expressions are described in [Types of EDI and AS2 Status Reports](../core/types-of-edi-and-as2-status-reports.md) and the **EDI-AS2 Status Reports UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
5.  <span data-ttu-id="fba3d-124">Pour exécuter la requête, en affichant le rapport d’état en fonction de critères de filtre, cliquez sur **exécuter la requête**.</span><span class="sxs-lookup"><span data-stu-id="fba3d-124">To run the query, displaying the status report according to the filter criteria, click **Run Query**.</span></span>  
  
6.  <span data-ttu-id="fba3d-125">Pour enregistrer une expression de requête sous forme de fichier .btq, cliquez sur **enregistrer en tant que**, spécifiez le dossier et entrez un nom de fichier, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="fba3d-125">To save a query expression as a .btq file, click **Save As**, specify the folder and enter a filename, and then click **Save**.</span></span>  
  
7.  <span data-ttu-id="fba3d-126">Pour ouvrir un fichier .btq enregistré, cliquez sur **ouvrir une requête**.</span><span class="sxs-lookup"><span data-stu-id="fba3d-126">To open a saved .btq file, click **Open Query**.</span></span>  
  
## <a name="configure-the-type-of-data-displayed-in-the-status-report-pane"></a><span data-ttu-id="fba3d-127">Configurer le type de données affichées dans le volet de rapport d’état</span><span class="sxs-lookup"><span data-stu-id="fba3d-127">Configure the type of data displayed in the status report pane</span></span>  
  
1.  <span data-ttu-id="fba3d-128">Avec le bouton droit de la zone des résultats du volet de rapport d’état, puis cliquez sur **Ajout/Suppression de colonnes**.</span><span class="sxs-lookup"><span data-stu-id="fba3d-128">Right-click the status results area of the status report pane, and then click **Add/Remove Columns**.</span></span>  
  
2.  <span data-ttu-id="fba3d-129">Pour ajouter une catégorie d’état à la liste des colonnes affichées, cliquez sur une colonne dans la **colonnes disponibles** liste, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="fba3d-129">To add a status category to the displayed columns list, click a column in the **Available columns** list, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="fba3d-130">Pour supprimer une catégorie de statut de la liste des colonnes affichées, cliquez sur une colonne dans la **colonnes affichées** liste, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="fba3d-130">To remove a status category from the displayed columns list, click a column in the **Displayed columns** list, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba3d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fba3d-131">See Also</span></span>  
 <span data-ttu-id="fba3d-132">[Surveillance des Solutions EDI et AS2](../core/monitoring-edi-and-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="fba3d-132">[Monitoring EDI and AS2 Solutions](../core/monitoring-edi-and-as2-solutions.md) </span></span>  
 <span data-ttu-id="fba3d-133">[EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md) </span><span class="sxs-lookup"><span data-stu-id="fba3d-133">[EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md) </span></span>  
 <span data-ttu-id="fba3d-134">[L’activation des rapports d’état AS2 et EDI](../core/enabling-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="fba3d-134">[Enabling EDI and AS2 Status Reports](../core/enabling-edi-and-as2-status-reports.md) </span></span>  
 [<span data-ttu-id="fba3d-135">Afficher un EDI ou le rapport d’état AS2</span><span class="sxs-lookup"><span data-stu-id="fba3d-135">Displaying an EDI or AS2 Status Report</span></span>](../core/displaying-an-edi-or-as2-status-report.md)