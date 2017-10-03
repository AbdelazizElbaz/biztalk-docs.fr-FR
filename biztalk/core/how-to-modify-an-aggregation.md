---
title: "Comment modifier une agrégation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], modifying
- BAM portal, aggregations
ms.assetid: dd5ce211-32d3-4e1d-8ee0-1225ec2c45fb
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6f5f157da15cb53da41d6735524ed502cd35156
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-an-aggregation"></a><span data-ttu-id="c1985-102">Modification d'une agrégation</span><span class="sxs-lookup"><span data-stu-id="c1985-102">How to Modify an Aggregation</span></span>
<span data-ttu-id="c1985-103">Les rapports de tableau croisé dynamique s'utilisent dans Office Web Components de la même façon que dans Excel.</span><span class="sxs-lookup"><span data-stu-id="c1985-103">You use PivotTable reports in Office Web Components the same way you use PivotTable reports in Excel.</span></span> <span data-ttu-id="c1985-104">Vous pouvez ajouter et supprimer des lignes, des colonnes et des filtres pour générer des vues des données agrégées sur lesquelles vous pouvez créer des alertes.</span><span class="sxs-lookup"><span data-stu-id="c1985-104">You can add and remove rows, columns, and filters to generate views of the aggregated data on which you can create alerts.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c1985-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c1985-105">Prerequisites</span></span>  
 <span data-ttu-id="c1985-106">Pour suivre cette procédure, vous devez avoir déployé une vue contenant une agrégation.</span><span class="sxs-lookup"><span data-stu-id="c1985-106">To perform this procedure, you must have a deployed view that contains an aggregation.</span></span>  
  
### <a name="to-modify-an-aggregation"></a><span data-ttu-id="c1985-107">Pour modifier une agrégation</span><span class="sxs-lookup"><span data-stu-id="c1985-107">To modify an aggregation</span></span>  
  
1.  <span data-ttu-id="c1985-108">Sur le **agrégations** page, à partir de la **liste de champs de tableau croisé dynamique** fenêtre, faites glisser les champs avec les données que vous souhaitez afficher dans des lignes et déposez-les dans la colonne de gauche de la grille pour ajouter des champs de ligne.</span><span class="sxs-lookup"><span data-stu-id="c1985-108">On the **Aggregations** page, from the **PivotTable Field List** window, drag the fields with data that you want to display in rows and drop them onto the left column of the grid to add row fields.</span></span> <span data-ttu-id="c1985-109">Si la liste de champs n'apparaît pas, cliquez à l'intérieur des contours des zones de dépôt de tableau croisé dynamique et vérifiez que Afficher la liste des champs apparaît.</span><span class="sxs-lookup"><span data-stu-id="c1985-109">If you don't see the field list, click within the outlines of the PivotTable drop areas, and make sure Show Field List appears.</span></span> <span data-ttu-id="c1985-110">Pour voir quels sont les niveaux de détails disponibles dans les champs pourvus de niveaux, cliquez sur le signe plus (+) en regard des champs concernés.</span><span class="sxs-lookup"><span data-stu-id="c1985-110">To see what levels of detail are available in fields that have levels, click the plus sign (+) next to the appropriate field.</span></span>  
  
2.  <span data-ttu-id="c1985-111">Faites glisser les champs avec les données que vous souhaitez afficher dans des colonnes à la zone de dépôt dénommée **placer les champs de colonne ici**.</span><span class="sxs-lookup"><span data-stu-id="c1985-111">Drag fields with data that you want to display across columns to the drop area labeled **Drop Column Fields Here**.</span></span> <span data-ttu-id="c1985-112">Seuls les champs désignés comme des nombres ou des champs de progression peuvent être déplacés dans cette zone.</span><span class="sxs-lookup"><span data-stu-id="c1985-112">Only fields that are designated as counts or progress fields can be dragged to this area.</span></span>  
  
3.  <span data-ttu-id="c1985-113">Si vous ajoutez plusieurs champs de données, organisez ces champs dans l’ordre souhaité : avec le bouton droit à un champ de données, pointez sur **commande** dans le menu contextuel et utilisez les commandes sur le **commande** menu pour déplacer le champ.</span><span class="sxs-lookup"><span data-stu-id="c1985-113">If you add more than one data field, arrange these fields in the order you want: right-click a data field, point to **Order** on the shortcut menu, and use the commands on the **Order** menu to move the field.</span></span>  
  
4.  <span data-ttu-id="c1985-114">Pour réorganiser les champs, faites-les glisser d'une zone à l'autre.</span><span class="sxs-lookup"><span data-stu-id="c1985-114">To rearrange fields, drag them from one area to another.</span></span> <span data-ttu-id="c1985-115">Pour supprimer un champ, faites-le glisser hors du rapport de tableau croisé dynamique et déplacez-le dans le cadre de navigation.</span><span class="sxs-lookup"><span data-stu-id="c1985-115">To remove a field, drag it out of the PivotTable report onto the navigation frame.</span></span>  
  
5.  <span data-ttu-id="c1985-116">Dans la colonne des totaux du rapport de tableau croisé dynamique, cliquez avec le bouton droit sur la cellule contenant le total sur lequel vous comptez définir une alerte.</span><span class="sxs-lookup"><span data-stu-id="c1985-116">From the totals column in the PivotTable report, right-click the cell containing the total on which you are going to set an alert.</span></span> <span data-ttu-id="c1985-117">Sélectionnez **créer une alerte** pour ouvrir la page de gestion des alertes.</span><span class="sxs-lookup"><span data-stu-id="c1985-117">Select **Create Alert** to open the Alert Management page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1985-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1985-118">See Also</span></span>  
 <span data-ttu-id="c1985-119">[Les agrégations sur le portail BAM Page](../core/aggregations-on-the-bam-portal-page.md) </span><span class="sxs-lookup"><span data-stu-id="c1985-119">[Aggregations on the BAM Portal Page](../core/aggregations-on-the-bam-portal-page.md) </span></span>  
 [<span data-ttu-id="c1985-120">Comment définir une alerte</span><span class="sxs-lookup"><span data-stu-id="c1985-120">How to Set an Alert</span></span>](../core/how-to-set-an-alert.md)