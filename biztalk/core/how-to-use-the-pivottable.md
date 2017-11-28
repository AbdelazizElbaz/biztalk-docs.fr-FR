---
title: "Comment utiliser le tableau croisé dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM views, pivot tables
- BAM views, previewing data
ms.assetid: af34494b-f577-4d36-9a9e-5d6e9c5fafbe
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aed416f7a04392804c4c031a69940c4229eabe99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-pivottable"></a><span data-ttu-id="629ac-102">Utilisation du tableau croisé dynamique</span><span class="sxs-lookup"><span data-stu-id="629ac-102">How to Use the PivotTable</span></span>
<span data-ttu-id="629ac-103">Lorsque vous avez défini une vue BAM incluant des dimensions et des mesures, vous devez mettre à jour un ou plusieurs tableaux croisés dynamiques associés à cette vue.</span><span class="sxs-lookup"><span data-stu-id="629ac-103">When you have defined a BAM view that includes dimensions and measures, you need to update one or more PivotTables associated with that view.</span></span>  
  
 <span data-ttu-id="629ac-104">Un rapport de tableau croisé dynamique dans Excel est un tableau interactif qui vous permet de combiner et de comparer facilement de grandes quantités de données.</span><span class="sxs-lookup"><span data-stu-id="629ac-104">A PivotTable report in Excel is an interactive table that enables you to easily combine and compare large amounts of data.</span></span> <span data-ttu-id="629ac-105">Vous pouvez faire pivoter les valeurs figurant dans les lignes et les colonnes pour afficher divers récapitulatifs des données affichées.</span><span class="sxs-lookup"><span data-stu-id="629ac-105">The values in its rows and columns can be rotated to look at different summaries of the displayed data.</span></span> <span data-ttu-id="629ac-106">Un tableau croisé dynamique vous permet d'effectuer des calculs sur les données, tels que des regroupements de nombres ou de moyennes.</span><span class="sxs-lookup"><span data-stu-id="629ac-106">A PivotTable also enables you perform calculations on the data, such as aggregate counts or averages.</span></span>  
  
 <span data-ttu-id="629ac-107">Pour utiliser le tableau croisé dynamique une fois celui-ci créé, effectuez la procédure ci-après.</span><span class="sxs-lookup"><span data-stu-id="629ac-107">To use the PivotTable after you have created it, follow the steps in this procedure.</span></span> <span data-ttu-id="629ac-108">Pour plus d'informations sur l'utilisation des tableaux croisés dynamiques, consultez la documentation Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="629ac-108">For more information about using PivotTables, see the Microsoft Excel documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="629ac-109">Lorsque vous créez un tableau croisé dynamique d'agrégation en temps réel, celui-ci peut comporter jusqu'à 14 niveaux de dimension.</span><span class="sxs-lookup"><span data-stu-id="629ac-109">When you create a real-time aggregation pivot table, it can contain a maximum of 14 dimension levels.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="629ac-110">Si vous définissez plusieurs tableaux croisés dynamiques dans la feuille de calcul Excel, il est possible que les tableaux résultants grandissent et se chevauchent si l'activité génère un ensemble de données important.</span><span class="sxs-lookup"><span data-stu-id="629ac-110">If you define multiple PivotTables on the Excel Worksheet, it is possible the resulting tables can grow and overlap each other if the Activity returns a large dataset.</span></span> <span data-ttu-id="629ac-111">Dans cette situation, vous recevez alors un message indiquant qu'un tableau croisé dynamique ne doit pas chevaucher un autre tableau croisé dynamique lorsque vous actualisez les données.</span><span class="sxs-lookup"><span data-stu-id="629ac-111">In this scenario, you will receive "A PivotTable report cannot overlap another PivotTable report" when you refresh the data.</span></span> <span data-ttu-id="629ac-112">Vous pouvez remédier à ce problème en ajoutant des colonnes ou des lignes supplémentaires entre les tableaux croisés dynamiques afin d'éviter leur chevauchement s'ils grandissent.</span><span class="sxs-lookup"><span data-stu-id="629ac-112">You can correct this error by adding addition columns or rows between the pivot tables to allow the tables to grow with out overlapping.</span></span>  
  
### <a name="to-use-the-pivottable"></a><span data-ttu-id="629ac-113">Pour utiliser le tableau croisé dynamique</span><span class="sxs-lookup"><span data-stu-id="629ac-113">To use the PivotTable</span></span>  
  
1.  <span data-ttu-id="629ac-114">Créez une vue BAM à utiliser avec un tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="629ac-114">Create a BAM view to be used with a PivotTable.</span></span> <span data-ttu-id="629ac-115">Pour plus d’informations sur la création d’une vue BAM, consultez [définition d’une vue activité d’entreprise](../core/defining-a-bam-view.md)</span><span class="sxs-lookup"><span data-stu-id="629ac-115">For more information about creating a BAM view, see [Defining a Business Activity View](../core/defining-a-bam-view.md)</span></span>  
  
2.  <span data-ttu-id="629ac-116">À l’aide de la **liste de champs de tableau croisé dynamique**, glisser-déplacer une ou plusieurs dimensions disponibles dans les zones de ligne et de colonne du modèle de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="629ac-116">Using the **PivotTable Field List**, drag-and-drop one or more available dimensions into the column and row areas of the PivotTable template.</span></span>  
  
3.  <span data-ttu-id="629ac-117">À l’aide de la **liste de champs de tableau croisé dynamique**, glisser-déplacer une ou plusieurs mesures dans la zone d’éléments de données du modèle de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="629ac-117">Using the  **PivotTable Field List**, drag-and-drop one or more available measures into the data items area of the PivotTable template.</span></span>  
  
     <span data-ttu-id="629ac-118">Lors de la mise à jour du tableau croisé dynamique, vous remarquerez qu'il est complété par des exemples de données.</span><span class="sxs-lookup"><span data-stu-id="629ac-118">As you are updating the PivotTable, you will notice that it is populated with sample data.</span></span> <span data-ttu-id="629ac-119">Ces données vous donnent des indications sur la manière dont le tableau croisé dynamique doit être configuré.</span><span class="sxs-lookup"><span data-stu-id="629ac-119">This helps you determine how the PivotTable should be configured.</span></span>  
  
4.  <span data-ttu-id="629ac-120">À l’aide de la **tableau croisé dynamique** barre d’outils, associez un graphique du tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="629ac-120">Using the **PivotTable** toolbar, associate a chart with the PivotTable.</span></span>  
  
5.  <span data-ttu-id="629ac-121">Enregistrez votre classeur Excel.</span><span class="sxs-lookup"><span data-stu-id="629ac-121">Save your Excel workbook.</span></span>