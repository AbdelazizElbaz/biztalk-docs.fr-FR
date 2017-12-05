---
title: "Erreur - le nombre de paramètres d’entrée non valide du fonctoid Création de Table | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.badParamCountForTableLooping
ms.assetid: 616e54aa-f6e3-4a49-afe2-278a0724e226
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2df0a6780485b91fc89356aecb73823643276be1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---input-parameter-count-for-table-looping-functoid-not-valid"></a><span data-ttu-id="aed9e-102">Erreur - le nombre de paramètres d’entrée non valide du fonctoid Création de Table</span><span class="sxs-lookup"><span data-stu-id="aed9e-102">Error - Input Parameter Count for Table Looping Functoid Not Valid</span></span>
<span data-ttu-id="aed9e-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="aed9e-103">**Error Code**</span></span>  
  
 <span data-ttu-id="aed9e-104">btm1070</span><span class="sxs-lookup"><span data-stu-id="aed9e-104">btm1070</span></span>  
  
 <span data-ttu-id="aed9e-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="aed9e-105">**Explanation**</span></span>  
  
 <span data-ttu-id="aed9e-106">Le nombre de paramètres d’entrée défini pour le **bouclage de Table** fonctoid n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="aed9e-106">The number of input parameters specified for the relevant **Table Looping** functoid is not valid.</span></span>  
  
 <span data-ttu-id="aed9e-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="aed9e-107">**User Action**</span></span>  
  
 <span data-ttu-id="aed9e-108">Vérifiez que les paramètres d’entrée pour le **bouclage de Table** fonctoid, accessibles via le **paramètres d’entrée** propriété et la **configurer \<fonctoid\> Fonctoid** boîte de dialogue, sont comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="aed9e-108">Ensure that the input parameters to the **Table Looping** functoid, as accessed through the **Input Parameters** property and the **Configure \<Functoid\> Functoid** dialog box, are as shown in the following table.</span></span>  
  
|<span data-ttu-id="aed9e-109">Nombre de paramètres d'entrée du fonctoid Création de table</span><span class="sxs-lookup"><span data-stu-id="aed9e-109">Table Looping functoid input parameter number</span></span>|<span data-ttu-id="aed9e-110"> Description</span><span class="sxs-lookup"><span data-stu-id="aed9e-110">Description</span></span>|  
|---------------------------------------------------|-----------------|  
|<span data-ttu-id="aed9e-111">1</span><span class="sxs-lookup"><span data-stu-id="aed9e-111">1</span></span>|<span data-ttu-id="aed9e-112">Lien à partir d’un enregistrement ou champ du schéma source, le nombre d’occurrences de laquelle un message d’instance d’entrée contrôle le nombre de fois associés de **extracteur de Table** fonctoids sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="aed9e-112">Link from a record or field in the source schema, the number of occurrences of which an input instance message controls the number of times the set of associated **Table Extractor** functoids are run.</span></span>|  
|<span data-ttu-id="aed9e-113">2</span><span class="sxs-lookup"><span data-stu-id="aed9e-113">2</span></span>|<span data-ttu-id="aed9e-114">Le nombre de colonnes dans la table de données configuré par le biais du **grille Bouclage de Table** propriété du **bouclage de Table** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="aed9e-114">The number of columns in the data table configured through the **Table Looping Grid** property of the relevant **Table Looping** functoid.</span></span>|  
|<span data-ttu-id="aed9e-115">3 – 100</span><span class="sxs-lookup"><span data-stu-id="aed9e-115">3 – 100</span></span>|<span data-ttu-id="aed9e-116">Constantes et liens (depuis le schéma source ou la sortie d'autres fonctoids) pouvant devenir des sources possibles de données dans la grille de création de table.</span><span class="sxs-lookup"><span data-stu-id="aed9e-116">Constants and links (from the source schema or output from other functoids) that will become possible sources of data with the table looping grid.</span></span>|