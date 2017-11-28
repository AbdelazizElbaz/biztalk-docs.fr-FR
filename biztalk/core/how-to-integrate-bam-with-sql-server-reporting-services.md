---
title: "L’intégration BAM avec SQL Server Reporting Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e2d66b7-c8eb-4871-8a47-544955ccd51e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61478bde3dd224029a6e3d6fd7c73ee84554f93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-integrate-bam-with-sql-server-reporting-services"></a><span data-ttu-id="2fa81-102">Intégration de l'analyse BAM avec SQL Server Reporting Services</span><span class="sxs-lookup"><span data-stu-id="2fa81-102">How to Integrate BAM with SQL Server Reporting Services</span></span>
<span data-ttu-id="2fa81-103">La création d'un rapport basé sur les données de l'infrastructure BAM fait appel aux même tâches que la création d'un rapport pour n'importe quelle autre source de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2fa81-103">Creating a report based on data in the BAM infrastructure use the typical tasks associated with creating a report for any other SQL Server data source.</span></span> <span data-ttu-id="2fa81-104">Pour plus d’informations sur la création d’un rapport avec le Concepteur de rapports, consultez [http://go.microsoft.com/fwlink/?LinkId=82437](http://go.microsoft.com/fwlink/?LinkId=82437).</span><span class="sxs-lookup"><span data-stu-id="2fa81-104">For more information about creating a report with Report Designer, see [http://go.microsoft.com/fwlink/?LinkId=82437](http://go.microsoft.com/fwlink/?LinkId=82437).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2fa81-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2fa81-105">Prerequisites</span></span>  
 <span data-ttu-id="2fa81-106">Vous devez détenir les autorisations d'accès aux données nécessaires pour créer le rapport.</span><span class="sxs-lookup"><span data-stu-id="2fa81-106">You must have permissions to access the data necessary to create the report.</span></span>  
  
### <a name="how-to-create-a-report-in-bam-by-using-sql-server-reporting-service"></a><span data-ttu-id="2fa81-107">Création d'un rapport dans BAM à l'aide de SQL Server Reporting Services</span><span class="sxs-lookup"><span data-stu-id="2fa81-107">How to Create a Report in BAM by Using SQL Server Reporting Service</span></span>  
  
1.  <span data-ttu-id="2fa81-108">Sélectionnez la source de données à partir de laquelle créer le rapport.</span><span class="sxs-lookup"><span data-stu-id="2fa81-108">Select the data source from which to create the report.</span></span>  
  
     <span data-ttu-id="2fa81-109">BAM propose deux sources de données vers lesquelles pointe Reporting Services.</span><span class="sxs-lookup"><span data-stu-id="2fa81-109">BAM provides two data sources to which Reporting Services can point.</span></span>  
  
    |<span data-ttu-id="2fa81-110">Source de données</span><span class="sxs-lookup"><span data-stu-id="2fa81-110">Data Source</span></span>|<span data-ttu-id="2fa81-111"> Description</span><span class="sxs-lookup"><span data-stu-id="2fa81-111">Description</span></span>|  
    |-----------------|-----------------|  
    |<span data-ttu-id="2fa81-112">Base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="2fa81-112">BAM Primary Import database</span></span>|<span data-ttu-id="2fa81-113">Contient les vues sur les instances d'activité et les agrégations en temps réel.</span><span class="sxs-lookup"><span data-stu-id="2fa81-113">Contains views on activity instances and real-time aggregations.</span></span> <span data-ttu-id="2fa81-114">Sélectionnez Type = « Microsoft SQL Server » et la chaîne de connexion = « Source de données =\<*nom du serveur*> ; Catalogue initial =\<*nom de la base de données*> », où \< *nom du serveur*> et \< *nom de la base de données*> sont les noms de serveur et de base de données de votre base de données d’importation principale Bam.</span><span class="sxs-lookup"><span data-stu-id="2fa81-114">Select Type=”Microsoft SQL Server” and Connection String=”Data Source=\<*server name*>; Initial Catalog=\<*database name*>”, where \<*server name*> and \<*database name*> are the server and database names of your Bam Primary Import database.</span></span>|  
    |<span data-ttu-id="2fa81-115">Base de données d'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="2fa81-115">BAM Analysis database</span></span>|<span data-ttu-id="2fa81-116">Contient les données utilisées pour interroger le cube d'analyse.</span><span class="sxs-lookup"><span data-stu-id="2fa81-116">Contains data that is used to query the analysis cube.</span></span> <span data-ttu-id="2fa81-117">Sélectionnez Type = « Microsoft SQL Server Analysis Server » et la chaîne de connexion = « Source de données =\<*nom du serveur*> ; Catalogue initial =\<*nom de la base de données*> », où \< *nom du serveur*> et \< *nom de la base de données*> sont les noms de serveur et de base de données de votre base de données analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="2fa81-117">Select Type=”Microsoft SQL Server Analysis Server” and Connection String=”Data Source=\<*server name*>; Initial Catalog=\<*database name*>”, where \<*server name*> and \<*database name*> are the server and database names of your BAM Analysis database.</span></span>|  
  
2.  <span data-ttu-id="2fa81-118">Concevez la requête.</span><span class="sxs-lookup"><span data-stu-id="2fa81-118">Design the query.</span></span> <span data-ttu-id="2fa81-119">Pour la base de données d'importation principale BAM, il existe deux types de vues :</span><span class="sxs-lookup"><span data-stu-id="2fa81-119">For the BAM Primary Import database, there are two types of views:</span></span>  
  
    |<span data-ttu-id="2fa81-120">Nom de la vue</span><span class="sxs-lookup"><span data-stu-id="2fa81-120">View Name</span></span>|<span data-ttu-id="2fa81-121"> Description</span><span class="sxs-lookup"><span data-stu-id="2fa81-121">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="2fa81-122">dbo.bam_\<*nom de la vue*> _\<*nom de l’activité*> View_View.</span><span class="sxs-lookup"><span data-stu-id="2fa81-122">dbo.bam_\<*view name*>_\<*activity name*>View_View.</span></span>|<span data-ttu-id="2fa81-123">Cette vue contient les données d'instance.</span><span class="sxs-lookup"><span data-stu-id="2fa81-123">This view contains instance data.</span></span>|  
    |<span data-ttu-id="2fa81-124">dbo.bam_\<*nom de la vue*> _\<*nom de table de tableau croisé dynamique d’agrégation en temps réel*> _RTAView</span><span class="sxs-lookup"><span data-stu-id="2fa81-124">dbo.bam_\<*view name*>_\<*real time aggregation pivot table name*>_RTAView</span></span>|<span data-ttu-id="2fa81-125">Cette vue contient les données utilisées dans les agrégations en temps réel.</span><span class="sxs-lookup"><span data-stu-id="2fa81-125">This view contains data used in real-time aggregations.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="2fa81-126">Vous pouvez taper **sélectionnez \* à partir de la vue** pour retourner le résultat souhaité.</span><span class="sxs-lookup"><span data-stu-id="2fa81-126">You can type **select \* from view** to return the desired result set.</span></span> <span data-ttu-id="2fa81-127">Pour la base de données analyse BAM, cliquez sur le Générateur de requêtes et faites glisser les dimensions et mesures du cube nommé \< *nom de la vue*> pour retourner le résultat souhaité.</span><span class="sxs-lookup"><span data-stu-id="2fa81-127">For the BAM Analysis database, click the query builder and drag the dimensions and measures of the cube named \<*view name*> to return the desired result set.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2fa81-128">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2fa81-128">Next Steps</span></span>  
 <span data-ttu-id="2fa81-129">Exécutez les étapes décrites dans l'Assistant Rapport afin de spécifier les données à présenter et la manière dont elles doivent être présentées.</span><span class="sxs-lookup"><span data-stu-id="2fa81-129">Complete the steps in the Report Wizard to specify which data you are going to present and how the data is to be presented.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa81-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fa81-130">See Also</span></span>  
 [<span data-ttu-id="2fa81-131">Gestion des bases de données BAM</span><span class="sxs-lookup"><span data-stu-id="2fa81-131">Managing BAM Databases</span></span>](../core/managing-bam-databases.md)