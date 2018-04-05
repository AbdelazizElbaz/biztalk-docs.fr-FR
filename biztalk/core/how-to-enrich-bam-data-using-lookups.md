---
title: Enrichissement des données BAM à l’aide de recherches | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, data lookups
ms.assetid: 8d10659e-97d6-4cd1-9b4d-307afd43c763
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43b42b42158bc3b3c179d624340a97a890072a17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enrich-bam-data-using-lookups"></a><span data-ttu-id="11fc8-102">Enrichissement des données BAM à l'aide de recherches</span><span class="sxs-lookup"><span data-stu-id="11fc8-102">How to Enrich BAM Data Using Lookups</span></span>
<span data-ttu-id="11fc8-103">Il pourra arriver que les données disponibles durant le fonctionnement ne contiennent pas tout ce dont vous avez besoin pour générer des rapports.</span><span class="sxs-lookup"><span data-stu-id="11fc8-103">There are cases in which the data that is available at operation time does not contain everything you need for reporting purposes.</span></span> <span data-ttu-id="11fc8-104">Par exemple, il se peut que vous disposiez d'un ProductID mais pas d'un ProductName lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="11fc8-104">For example, you may have a ProductID but not a ProductName at runtime.</span></span> <span data-ttu-id="11fc8-105">L'Activité BAM représentant une abstraction indépendante de la manière dont les données sont véritablement collectées, elle doit contenir un élément dont le nom soit celui des données finales que vous souhaitez voir apparaître dans le rapport « ProductName ».</span><span class="sxs-lookup"><span data-stu-id="11fc8-105">Since the BAM Activity represents an abstraction independent of how the data is actually collected, it should contain an item named as the final data that you want to see in the report "ProductName".</span></span> <span data-ttu-id="11fc8-106">Comme tout autre élément, vous pouvez utiliser cet élément dans des constructions d'interprétation telles que des groupes, des durées, des dimensions et des mesures d'étape majeure.</span><span class="sxs-lookup"><span data-stu-id="11fc8-106">Just like any other item, you can use this in interpretive constructs such as milestone groups, durations, dimensions, and measures.</span></span> <span data-ttu-id="11fc8-107">Le ProductName n'étant pas disponible au moment de l'exécution, vous devez vous procurer d'autres données suffisant pour effectuer une recherche, le ProductID par exemple.</span><span class="sxs-lookup"><span data-stu-id="11fc8-107">Since the ProductName is not available at runtime, you must get some additional data that is sufficient for performing a lookup, such as the ProductID.</span></span>  
  
 <span data-ttu-id="11fc8-108">Il est préférable que vous collectiez les données dans une même colonne, à la place des données dont vous avez besoin pour les rapports.</span><span class="sxs-lookup"><span data-stu-id="11fc8-108">You should collect the data in the same column, instead of the data that you need for reports.</span></span> <span data-ttu-id="11fc8-109">Par exemple, il vous faudra collecter le ProductID à la place de ProductName lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="11fc8-109">For example, you should collect the ProductID instead of ProductName at runtime.</span></span> <span data-ttu-id="11fc8-110">Si davantage de colonnes sont nécessaires, vous êtes autorisé à créer d'autres éléments dans l'activité mais pas à les utiliser dans les vues.</span><span class="sxs-lookup"><span data-stu-id="11fc8-110">If more columns are required, you may create more items in the activity but not use them in any View.</span></span>  
  
### <a name="to-enrich-bam-data-via-lookups"></a><span data-ttu-id="11fc8-111">Pour enrichir des données BAM à l'aide de recherches</span><span class="sxs-lookup"><span data-stu-id="11fc8-111">To enrich BAM data via lookups</span></span>  
  
1.  <span data-ttu-id="11fc8-112">Déployez votre définition BAM.</span><span class="sxs-lookup"><span data-stu-id="11fc8-112">Deploy your BAM definition.</span></span>  
  
2.  <span data-ttu-id="11fc8-113">Dans SQL Server Management Studio, ajoutez le serveur qui contient les données d'intérêt en tant que serveur distant.</span><span class="sxs-lookup"><span data-stu-id="11fc8-113">In SQL Server Management Studio, add the server that contains the data of interest as a remote server.</span></span>  
  
3.  <span data-ttu-id="11fc8-114">Recherchez le package d'analyse de données appelé BAM_AN_`<View Name>`.</span><span class="sxs-lookup"><span data-stu-id="11fc8-114">Locate the data analysis package named BAM_AN_`<View Name>`.</span></span> <span data-ttu-id="11fc8-115">Par exemple, si la vue est SalesMgr, il s'appellera BAM_AN_SalesMgr.</span><span class="sxs-lookup"><span data-stu-id="11fc8-115">For example if the view is SalesMgr, this will be BAM_AN_SalesMgr.</span></span>  
  
4.  <span data-ttu-id="11fc8-116">Réglez le zoom de façon à agrandir l'affichage du package (par exemple à 100 %).</span><span class="sxs-lookup"><span data-stu-id="11fc8-116">Set the zoom to magnify the view of the package (e.g. 100%)</span></span>  
  
5.  <span data-ttu-id="11fc8-117">Ajoutez une connexion SQL que vous utiliserez dans les recherches.</span><span class="sxs-lookup"><span data-stu-id="11fc8-117">Add a SQL connection that you will be using in the lookups.</span></span>  
  
6.  <span data-ttu-id="11fc8-118">Localisez la tâche de transformation des données après l'étape « Nettoyage du test ».</span><span class="sxs-lookup"><span data-stu-id="11fc8-118">Locate the transform data task after the step "Cleanup Staging".</span></span> <span data-ttu-id="11fc8-119">C'est là où vous déplacez les données de la base de données d'importation principale dans la base de données de schémas en étoile.</span><span class="sxs-lookup"><span data-stu-id="11fc8-119">This is where you move the data from the PrimaryImport to the StarSchema database.</span></span> <span data-ttu-id="11fc8-120">Il y a deux instances de cette tâche : l'une pour les activités terminées, l'autre pour celle en cours.</span><span class="sxs-lookup"><span data-stu-id="11fc8-120">There are two instances of this task—one for the completed activities, and another for the one that is in progress.</span></span> <span data-ttu-id="11fc8-121">Appliquez la suite des étapes aux deux tâches.</span><span class="sxs-lookup"><span data-stu-id="11fc8-121">Apply all the rest of the steps to both tasks.</span></span>  
  
7.  <span data-ttu-id="11fc8-122">Cliquez sur la transformation.</span><span class="sxs-lookup"><span data-stu-id="11fc8-122">Click the transformation.</span></span>  
  
8.  <span data-ttu-id="11fc8-123">Sélectionnez Recherche, puis ajoutez votre recherche « LookupProductByID » à l'aide de la connexion de recherche (voir la documentation en ligne de SQL à propos des recherches).</span><span class="sxs-lookup"><span data-stu-id="11fc8-123">Select Lookups; add your lookup "LookupProductByID" using the lookup connection (see SQL books online for lookups).</span></span> <span data-ttu-id="11fc8-124">Si la recherche est par exemple un simple tableau « LookupProduct » doté des colonnes ProductID et ProductName, le texte de la recherche sera le suivant :</span><span class="sxs-lookup"><span data-stu-id="11fc8-124">If for example the lookup is a simple table "LookupProduct", the with columns ProductID and ProductName, the text of the lookup will be:</span></span>  
  
    ```  
    SELECT ProductName  
    FROM   LookupProduct  
    WHERE ProductID=?  
    ```  
  
9. <span data-ttu-id="11fc8-125">Cliquez sur l'onglet Transformations. Effacez la transformation de données par défaut « Transformer » et créez une transformation ActiveX à la place.</span><span class="sxs-lookup"><span data-stu-id="11fc8-125">Click the Transformations tab. Delete the default data transformation "Transform", and create ActiveX transformation instead.</span></span> <span data-ttu-id="11fc8-126">Cliquez sur Colonnes source et ajoutez toutes les colonnes.</span><span class="sxs-lookup"><span data-stu-id="11fc8-126">Click Source Columns and add all columns.</span></span> <span data-ttu-id="11fc8-127">Cliquez sur Colonnes de destination et ajoutez toutes les colonnes.</span><span class="sxs-lookup"><span data-stu-id="11fc8-127">Click Destination Columns and add all columns.</span></span>  
  
10. <span data-ttu-id="11fc8-128">Cliquez sur l’onglet Général, puis sur Propriétés.</span><span class="sxs-lookup"><span data-stu-id="11fc8-128">Click the General tab, and then Properties.</span></span> <span data-ttu-id="11fc8-129">Cela entraîne la génération automatique d'un script qui exécute la transformation de copie triviale comme illustré :</span><span class="sxs-lookup"><span data-stu-id="11fc8-129">This results in automatic generation of a script that performs the trivial copy transformation as shown:</span></span>  
  
    ```  
    Function Main()  
       ...  
       DTSDestination("ProductName") = DTSSource("ProductName")  
       ...  
       Main = DTSTransformStat_OK  
    End Function  
    ```  
  
11. <span data-ttu-id="11fc8-130">Modifiez la valeur en utilisant la recherche comme illustré :</span><span class="sxs-lookup"><span data-stu-id="11fc8-130">Change the value by using the lookup as shown:</span></span>  
  
    ```  
    Function Main()  
       ...  
       DTSDestination("Product")= _  
                      DTSLookups( "LookupProductByID" ).Execute(  _                                  DTSSource("Product"))  
       ...  
       Main = DTSTransformStat_OK  
    End Function  
    ```  
  
12. <span data-ttu-id="11fc8-131">Enregistrez puis exécutez le package.</span><span class="sxs-lookup"><span data-stu-id="11fc8-131">Save and then run the package.</span></span>  
  
13. <span data-ttu-id="11fc8-132">Assurez-vous que les données qui arrivent dans le cube OLAP sont les bonnes.</span><span class="sxs-lookup"><span data-stu-id="11fc8-132">Ensure that the correct data ends up in the OLAP cube.</span></span> <span data-ttu-id="11fc8-133">Il est conseillé que vous enregistriez le package en tant que VBScript ou en tant que fichier de stockage structuré car il contient votre code personnalisé et non pas uniquement des étapes auto-générées à partir de l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="11fc8-133">You should save the package as VBScript or a structured storage file, because it contains your custom code, not just the auto-generated steps from BAM.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11fc8-134">La recherche ne fonctionne qu'avec les rapports planifiés que vous exécutez avec DTS et OLAP.</span><span class="sxs-lookup"><span data-stu-id="11fc8-134">The lookup works only for the scheduled reports that you perform with DTS and OLAP.</span></span> <span data-ttu-id="11fc8-135">Si vous avez besoin d'autres données que celles collectées dans l'agrégation RTA, vous devez les extraire avant d'appeler l'API BAM.</span><span class="sxs-lookup"><span data-stu-id="11fc8-135">If you need different data than what is collected in the real-time aggregation, then you must retrieve the data before calling the BAM API.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fc8-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11fc8-136">See Also</span></span>  
 <span data-ttu-id="11fc8-137">[À l’aide de Business Activity Monitoring](../core/using-business-activity-monitoring.md) </span><span class="sxs-lookup"><span data-stu-id="11fc8-137">[Using Business Activity Monitoring](../core/using-business-activity-monitoring.md) </span></span>  
 [<span data-ttu-id="11fc8-138">Déploiement des fichiers XML d’analyse BAM localisés</span><span class="sxs-lookup"><span data-stu-id="11fc8-138">Deploying Localized BAM XML Files</span></span>](../core/deploying-localized-bam-xml-files.md)