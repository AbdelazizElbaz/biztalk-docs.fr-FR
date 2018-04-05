---
title: 'Erreur : données non valides de bouclage de Table | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.tableLoopingDataNotValid
ms.assetid: 19c38e79-bab0-4899-ae24-e1485327e891
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9478026980ecaf3e2049773737250c56d18262c8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---table-looping-data-not-valid"></a><span data-ttu-id="f93de-102">Erreur : données non valides de bouclage de Table</span><span class="sxs-lookup"><span data-stu-id="f93de-102">Error - Table Looping Data Not Valid</span></span>
<span data-ttu-id="f93de-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="f93de-103">**Error Code**</span></span>  
  
 <span data-ttu-id="f93de-104">btm1065</span><span class="sxs-lookup"><span data-stu-id="f93de-104">btm1065</span></span>  
  
 <span data-ttu-id="f93de-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="f93de-105">**Explanation**</span></span>  
  
 <span data-ttu-id="f93de-106">La table de données associées **bouclage de Table** fonctoid n’est pas valide, probablement en raison d’un deuxième paramètre d’entrée configuré de façon incorrecte pour le fonctoid, ou une grille Bouclage de table mal configurée.</span><span class="sxs-lookup"><span data-stu-id="f93de-106">The table of data associated with the relevant **Table Looping** functoid is not valid, probably due to an incorrectly configured second input parameter to the functoid, or an incorrectly configured table looping grid.</span></span>  
  
 <span data-ttu-id="f93de-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="f93de-107">**User Action**</span></span>  
  
 <span data-ttu-id="f93de-108">Vérifiez que les paramètres d’entrée pour le **bouclage de Table** fonctoid, accessibles via le **paramètres d’entrée** propriété et la **configurer \<fonctoid\> Fonctoid** boîte de dialogue, sont comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f93de-108">Ensure that the input parameters to the **Table Looping** functoid, as accessed through the **Input Parameters** property and the **Configure \<Functoid\> Functoid** dialog box, are as shown in the following table.</span></span>  
  
|<span data-ttu-id="f93de-109">Nombre de paramètres d'entrée du fonctoid Création de table</span><span class="sxs-lookup"><span data-stu-id="f93de-109">Table Looping functoid input parameter number</span></span>|<span data-ttu-id="f93de-110"> Description</span><span class="sxs-lookup"><span data-stu-id="f93de-110">Description</span></span>|  
|---------------------------------------------------|-----------------|  
|<span data-ttu-id="f93de-111">1</span><span class="sxs-lookup"><span data-stu-id="f93de-111">1</span></span>|<span data-ttu-id="f93de-112">Lien à partir d’un enregistrement ou champ du schéma source, le nombre d’occurrences de laquelle un message d’instance d’entrée contrôle le nombre de fois associés de **extracteur de Table** fonctoids sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="f93de-112">Link from a record or field in the source schema, the number of occurrences of which an input instance message controls the number of times the set of associated **Table Extractor** functoids are run.</span></span>|  
|<span data-ttu-id="f93de-113">2</span><span class="sxs-lookup"><span data-stu-id="f93de-113">2</span></span>|<span data-ttu-id="f93de-114">Le nombre de colonnes dans la table de données configuré par le biais du **grille Bouclage de Table** propriété du **bouclage de Table** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="f93de-114">The number of columns in the data table configured through the **Table Looping Grid** property of the relevant **Table Looping** functoid.</span></span>|  
|<span data-ttu-id="f93de-115">3 – 100</span><span class="sxs-lookup"><span data-stu-id="f93de-115">3 – 100</span></span>|<span data-ttu-id="f93de-116">Constantes et liens (depuis le schéma source ou la sortie d'autres fonctoids) pouvant devenir des sources possibles de données dans la grille de création de table.</span><span class="sxs-lookup"><span data-stu-id="f93de-116">Constants and links (from the source schema or output from other functoids) that will become possible sources of data with the table looping grid.</span></span>|  
  
 <span data-ttu-id="f93de-117">En outre, assurez-vous de configurer correctement la grille de bouclage de table accessibles via la **grille Bouclage de Table** propriété et la **Configuration de bouclage de Table** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f93de-117">Also, ensure that you properly configure the table looping grid, as accessed through the **Table Looping Grid** property and the **Table Looping Configuration** dialog box.</span></span> <span data-ttu-id="f93de-118">Une valeur constante ou un lien doit être choisie pour chaque cellule qui sera accessible par associé à un **extracteur de Table** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="f93de-118">A constant or link value must be chosen for every cell that will be accessed by an associated **Table Extractor** functoid.</span></span>