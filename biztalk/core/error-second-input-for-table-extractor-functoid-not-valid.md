---
title: "Erreur : la deuxième entrée de fonctoid Extracteur de Table non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.secondInputForTableExtractorNotValid
ms.assetid: 099f7374-8625-40af-a74b-24c4de941a7b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5970c0bfa23cc7da33b2c041cc326987ec278e09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---second-input-for-table-extractor-functoid-not-valid"></a><span data-ttu-id="53dc6-102">Erreur : la deuxième entrée de fonctoid Extracteur de Table non valide</span><span class="sxs-lookup"><span data-stu-id="53dc6-102">Error - Second Input for Table Extractor Functoid Not Valid</span></span>
<span data-ttu-id="53dc6-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="53dc6-103">**Error Code**</span></span>  
  
 <span data-ttu-id="53dc6-104">btm1073</span><span class="sxs-lookup"><span data-stu-id="53dc6-104">btm1073</span></span>  
  
 <span data-ttu-id="53dc6-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="53dc6-105">**Explanation**</span></span>  
  
 <span data-ttu-id="53dc6-106">La deuxième entrée de paramètre au **extracteur de Table** fonctoid n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="53dc6-106">The second input parameter to the relevant **Table Extractor** functoid is not valid.</span></span> <span data-ttu-id="53dc6-107">Ce paramètre doit être une constante entière positive qui indique une colonne valide dans la grille de bouclage de table le **bouclage de Table** fonctoid qui est indiqué par le premier paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="53dc6-107">This parameter must be a positive integer constant that indicates a valid column in the table looping grid configured for the **Table Looping** functoid that is indicated by the first input parameter.</span></span>  
  
 <span data-ttu-id="53dc6-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="53dc6-108">**User Action**</span></span>  
  
 <span data-ttu-id="53dc6-109">Vérifiez que les paramètres d’entrée au **extracteur de Table** fonctoid, accessibles via son **paramètres d’entrée** propriété et la **configurer \<fonctoid > Fonctoid** boîte de dialogue, sont comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="53dc6-109">Ensure that the input parameters to the relevant **Table Extractor** functoid, as accessed through its **Input Parameters** property and the **Configure \<Functoid> Functoid** dialog box, are as shown in the following table.</span></span>  
  
|<span data-ttu-id="53dc6-110">Numéro du paramètre d'entrée du fonctoid Extracteur de table</span><span class="sxs-lookup"><span data-stu-id="53dc6-110">Table Extractor functoid input parameter number</span></span>|<span data-ttu-id="53dc6-111"> Description</span><span class="sxs-lookup"><span data-stu-id="53dc6-111">Description</span></span>|  
|-----------------------------------------------------|-----------------|  
|<span data-ttu-id="53dc6-112">1</span><span class="sxs-lookup"><span data-stu-id="53dc6-112">1</span></span>|<span data-ttu-id="53dc6-113">Lien à partir de la **bouclage de Table** fonctoid à partir duquel le **extracteur de Table** fonctoid extraira les données de la colonne tel qu’indiqué par son deuxième paramètre.</span><span class="sxs-lookup"><span data-stu-id="53dc6-113">Link from the **Table Looping** functoid from which this **Table Extractor** functoid will pull column data as indicated by its second parameter.</span></span>|  
|<span data-ttu-id="53dc6-114">2</span><span class="sxs-lookup"><span data-stu-id="53dc6-114">2</span></span>|<span data-ttu-id="53dc6-115">Le nombre d’une colonne valide dans la table de données configurée par le biais du **grille Bouclage de Table** propriété de la **bouclage de Table** fonctoid spécifié par le premier paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="53dc6-115">The number of a valid column in the data table configured through the **Table Looping Grid** property of the **Table Looping** functoid specified by the first input parameter.</span></span>|