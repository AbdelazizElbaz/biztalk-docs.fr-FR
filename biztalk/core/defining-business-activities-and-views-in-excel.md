---
title: "Définir des vues et des activités d’entreprise dans Excel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], creating business activities
- monitoring business activities [BAM], creating business activities
ms.assetid: 000532f0-cb9a-40ac-a6c5-a8bd4e49f8d0
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91b9d3b213a6a6429759c0bb0d826798afa36da3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-business-activities-and-views-in-excel"></a><span data-ttu-id="5a1e1-102">Définition des activités et des vues d'entreprise dans Excel</span><span class="sxs-lookup"><span data-stu-id="5a1e1-102">Defining Business Activities and Views in Excel</span></span>
<span data-ttu-id="5a1e1-103">La première étape à effectuer pour créer une solution BAM consiste à identifier les données qui vous intéressent et la manière dont elles doivent être interprétées.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-103">Your first step in creating any BAM solution is to identify what data you're interested in and how that data should be interpreted.</span></span> <span data-ttu-id="5a1e1-104">Pour ce faire, utilisez le complément BAM pour Excel.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-104">To do this, you use the BAM Add-in for Excel.</span></span> <span data-ttu-id="5a1e1-105">Ce complément vous permet d'établir une liste souhaitée des données d'intérêt en définissant une activité d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-105">The add-in allows you to define a wish-list of the data of interest by defining a business activity.</span></span> <span data-ttu-id="5a1e1-106">Vous pouvez également définir la manière dont les données doivent être interprétées et affichées pour différentes catégories d'utilisateurs d'activités.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-106">You can also define the way the data should be interpreted and shown to different categories of business users.</span></span>  
  
 <span data-ttu-id="5a1e1-107">Le complément BAM vous permet également de définir des agrégations.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-107">The BAM Add-in also enables you to define aggregations.</span></span>  
  
 <span data-ttu-id="5a1e1-108">Vous pouvez par ailleurs renommer des éléments d'activité, si la terminologie à laquelle certains utilisateurs sont habitués ne correspond pas aux dénominations des éléments de données correspondants dans l'activité.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-108">You can also rename activity items, for example, where the terminology some users are familiar with does not match the names of the corresponding data items in the activity.</span></span> <span data-ttu-id="5a1e1-109">Par exemple, si la vue est affichée dans une langue différente.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-109">One explanation for this is where the view is in a different language.</span></span>  
  
 <span data-ttu-id="5a1e1-110">Une fois la définition des activités terminée, Excel génère des données de prévisualisation de manière aléatoire pour définir les graphiques souhaités, ainsi que d'autres modes de présentation.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-110">After you complete the activity definition, Excel generates random preview data that you can use to define the desired charts and other means of presentation.</span></span> <span data-ttu-id="5a1e1-111">Pour plus d’informations sur les données d’aperçu, consultez [comment utiliser le tableau croisé dynamique](../core/how-to-use-the-pivottable.md).</span><span class="sxs-lookup"><span data-stu-id="5a1e1-111">For more information about preview data, see [How to Use the PivotTable](../core/how-to-use-the-pivottable.md).</span></span>  
  
 <span data-ttu-id="5a1e1-112">La définition d'activité définit les points de données et les événements qui doivent être collectés lors de l'exécution d'un processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-112">The completed activity definition defines the data points and events that you need collected when a business process is run.</span></span> <span data-ttu-id="5a1e1-113">Vous pouvez obtenir le complément BAM pour Excel à partir de diverses sources.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-113">You can get the BAM Add-in from a variety of sources.</span></span>  
  
 <span data-ttu-id="5a1e1-114">Vous pouvez installer le BAM complément XLA lors de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-114">You can install the BAM Add-in XLA during the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span></span> <span data-ttu-id="5a1e1-115">Pour plus d’informations, consultez [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)</span><span class="sxs-lookup"><span data-stu-id="5a1e1-115">For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)</span></span>  
  
 <span data-ttu-id="5a1e1-116">L’analyse BAM. XLA est installé dans un des emplacements suivants :</span><span class="sxs-lookup"><span data-stu-id="5a1e1-116">The BAM.XLA file is installed in one of the following locations:</span></span>  
  
-   <span data-ttu-id="5a1e1-117">Si Microsoft Office n’est pas installé sur l’ordinateur, puis le fichier BAM.xla est installé dans le Files\Microsoft BizTalk Server 20*xx*\ExcelDir\ dossier.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-117">If Microsoft Office is not installed on the computer, then the BAM.xla is installed to the \Program Files\Microsoft BizTalk Server 20*xx*\ExcelDir\ folder.</span></span>  
  
-   <span data-ttu-id="5a1e1-118">Si Microsoft Office est installé, le fichier BAM.xla est installé dans le Files\Microsoft Office\OFFICE*xx*\Library\ dossier.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-118">If Microsoft Office is installed, the BAM.xla is installed in the \Program Files\Microsoft Office\OFFICE*xx*\Library\ folder.</span></span>  
  
 <span data-ttu-id="5a1e1-119">Vous pouvez également copier le fichier BAM.xla sur votre ordinateur à partir d'un dossier partagé se trouvant sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-119">You can also copy the BAM.xla to your computer from a shared folder on another computer.</span></span> <span data-ttu-id="5a1e1-120">Vous pourrez ensuite inscrire le XLA en le sélectionnant à partir de l'emplacement où vous l'avez copié.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-120">You can then register the XLA by selecting it from the location to which you copied it.</span></span>  
  
 <span data-ttu-id="5a1e1-121">Pour activer le complément BAM dans la barre d’outils du menu Excel, cliquez sur le **fichier** menu, puis cliquez sur **Options**, puis cliquez sur **compléments**. Sélectionnez **Business Activity Monitoring**, puis cliquez sur **accédez**, dans la fenêtre compléments, activez la case à cocher ensuite **Business Activity Monitoring**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-121">To enable the BAM Add-in on the Excel menu toolbar, click the **File** menu, then click **Options**, and then click **Add-Ins**. Select **Business Activity Monitoring**, then click **GO**, In the Ad-ins window, select the check box next to **Business Activity Monitoring**, and then click **OK**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a1e1-122">L'utilisation du complément BAM pour Excel exclut la possibilité d'exécuter Excel avec deux instances chargées dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-122">Using the BAM Add-in precludes running Excel with two instances loaded into the same process.</span></span>  <span data-ttu-id="5a1e1-123">Lors de l'utilisation du complément, plusieurs instances peuvent exister dans le même processus dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="5a1e1-123">When using the add-in, multiple instances in the same process can occur in the following situations:</span></span>  
>   
>  <span data-ttu-id="5a1e1-124">Lorsqu'une feuille de calcul Excel est ouverte, avec le complément BAM activé, et que vous double-cliquez sur une feuille de calcul Excel différente, Excel tente de charger la feuille de calcul dans l'instance en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-124">When you have an Excel spreadsheet open with the BAM Add-in enabled, and you double-click a different Excel spreadsheet, Excel attempts to load the spreadsheet into the currently running instance.</span></span>  
>   
>  <span data-ttu-id="5a1e1-125">Lorsqu'une feuille de calcul Excel est ouverte, avec le complément BAM activé, et que vous utilisez l'option de menu Fichier/Ouvrir pour charger une autre feuille de calcul Excel.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-125">When you have an Excel spreadsheet open, with the BAM Add-in enabled, and you use the File/Open menu option to load another Excel spreadsheet.</span></span>  
  
 <span data-ttu-id="5a1e1-126">Ces situations ne vous permettent pas d'utiliser correctement le complément BAM.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-126">You cannot use the add-in properly in such situations.</span></span> <span data-ttu-id="5a1e1-127">Pour ouvrir plusieurs feuilles de calcul Excel lorsque le complément BAM est activé, vous devez ouvrir une nouvelle copie d'Excel et charger la feuille de calcul dans cette instance d'Excel.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-127">To open multiple Excel spreadsheets when you have the BAM Add-in enabled, you must open a new copy of Excel and load the spreadsheet into that instance of Excel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a1e1-128">Lorsque vous utilisez BAM.xla dans Excel, vous pouvez obtenir l’erreur « ce classeur a perdu son projet VBA, contrôles ActiveX et autres fonctionnalités liées à la programmabilité. »</span><span class="sxs-lookup"><span data-stu-id="5a1e1-128">When you use BAM.xla in Excel, you may get the error “This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.”</span></span> <span data-ttu-id="5a1e1-129">Pour plus d’informations sur l’erreur, consultez [BAM de dépannage](../core/troubleshooting-bam.md).</span><span class="sxs-lookup"><span data-stu-id="5a1e1-129">For more information about the error, see [Troubleshooting BAM](../core/troubleshooting-bam.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a1e1-130">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5a1e1-130">In This Section</span></span>  
  
-   [<span data-ttu-id="5a1e1-131">La définition d’une activité d’entreprise</span><span class="sxs-lookup"><span data-stu-id="5a1e1-131">How to Define a Business Activity</span></span>](../core/how-to-define-a-business-activity.md)  
  
-   [<span data-ttu-id="5a1e1-132">Définition d’une vue BAM</span><span class="sxs-lookup"><span data-stu-id="5a1e1-132">Defining a BAM View</span></span>](../core/defining-a-bam-view.md)  
  
## <a name="see-also"></a><span data-ttu-id="5a1e1-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a1e1-133">See Also</span></span>  
 [<span data-ttu-id="5a1e1-134">Analyse des activités d’entreprise avec BAM</span><span class="sxs-lookup"><span data-stu-id="5a1e1-134">Monitoring Business Activities with BAM</span></span>](../core/monitoring-business-activities-with-bam.md)