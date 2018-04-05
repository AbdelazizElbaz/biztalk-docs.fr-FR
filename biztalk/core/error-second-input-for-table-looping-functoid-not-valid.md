---
title: 'Erreur : la deuxième entrée de fonctoid Bouclage non valide de la Table | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.secondInputForTableLoopingNotValid
ms.assetid: 22771f36-5969-40b1-a957-3ca67e19c3fd
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abb321a26300a514357225713db1b197fb828851
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---second-input-for-table-looping-functoid-not-valid"></a><span data-ttu-id="f8b3a-102">Erreur : la deuxième entrée de fonctoid Bouclage non valide de la Table</span><span class="sxs-lookup"><span data-stu-id="f8b3a-102">Error - Second Input for Table Looping Functoid Not Valid</span></span>
<span data-ttu-id="f8b3a-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="f8b3a-103">**Error Code**</span></span>  
  
 <span data-ttu-id="f8b3a-104">btm1072</span><span class="sxs-lookup"><span data-stu-id="f8b3a-104">btm1072</span></span>  
  
 <span data-ttu-id="f8b3a-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="f8b3a-105">**Explanation**</span></span>  
  
 <span data-ttu-id="f8b3a-106">La deuxième entrée de paramètre au **bouclage de Table** fonctoid n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="f8b3a-106">The second input parameter to the relevant **Table Looping** functoid is not valid.</span></span> <span data-ttu-id="f8b3a-107">Ce paramètre doit être un entier positif qui indique le nombre de colonnes de la Grille Création de table associée.</span><span class="sxs-lookup"><span data-stu-id="f8b3a-107">This parameter must be a positive integer that indicates the number of columns in the associated table looping grid.</span></span>  
  
 <span data-ttu-id="f8b3a-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="f8b3a-108">**User Action**</span></span>  
  
 <span data-ttu-id="f8b3a-109">Vérifiez que les paramètres d’entrée pour le **bouclage de Table** fonctoid, accessibles via le **paramètres d’entrée** propriété et la **configurer \<fonctoid\> Fonctoid** boîte de dialogue, sont comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f8b3a-109">Ensure that the input parameters to the **Table Looping** functoid, as accessed through the **Input Parameters** property and the **Configure \<Functoid\> Functoid** dialog box, are as shown in the following table.</span></span>  
  
|<span data-ttu-id="f8b3a-110">Nombre de paramètres d'entrée du fonctoid Création de table</span><span class="sxs-lookup"><span data-stu-id="f8b3a-110">Table Looping functoid input parameter number</span></span>|<span data-ttu-id="f8b3a-111"> Description</span><span class="sxs-lookup"><span data-stu-id="f8b3a-111">Description</span></span>|  
|---------------------------------------------------|-----------------|  
|<span data-ttu-id="f8b3a-112">1</span><span class="sxs-lookup"><span data-stu-id="f8b3a-112">1</span></span>|<span data-ttu-id="f8b3a-113">Lien à partir d’un enregistrement ou champ du schéma source, le nombre d’occurrences de laquelle un message d’instance d’entrée contrôle le nombre de fois associés de **extracteur de Table** fonctoids sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="f8b3a-113">Link from a record or field in the source schema, the number of occurrences of which an input instance message controls the number of times the set of associated **Table Extractor** functoids are run.</span></span>|  
|<span data-ttu-id="f8b3a-114">2</span><span class="sxs-lookup"><span data-stu-id="f8b3a-114">2</span></span>|<span data-ttu-id="f8b3a-115">Le nombre de colonnes dans la table de données configuré par le biais du **grille Bouclage de Table** propriété du **bouclage de Table** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="f8b3a-115">The number of columns in the data table configured through the **Table Looping Grid** property of the relevant **Table Looping** functoid.</span></span>|  
|<span data-ttu-id="f8b3a-116">3 – 100</span><span class="sxs-lookup"><span data-stu-id="f8b3a-116">3 – 100</span></span>|<span data-ttu-id="f8b3a-117">Constantes et liens (depuis le schéma source ou la sortie d'autres fonctoids) pouvant devenir des sources possibles de données dans la grille de création de table.</span><span class="sxs-lookup"><span data-stu-id="f8b3a-117">Constants and links (from the source schema or output from other functoids) that will become possible sources of data with the table looping grid.</span></span>|