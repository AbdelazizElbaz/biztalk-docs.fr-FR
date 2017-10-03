---
title: "Erreur - première entrée du fonctoid Extracteur de valeur non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.firstInputValueExtractorNotValid
ms.assetid: 7703ca5f-21aa-441f-8c28-b02da72c25c1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68b143cea7e1d7e99c1d5b378bd9d6619270fb70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---first-input-to-value-extractor-functoid-not-valid"></a><span data-ttu-id="22df3-102">Erreur - première entrée du fonctoid Extracteur de valeur non valide</span><span class="sxs-lookup"><span data-stu-id="22df3-102">Error - First Input to Value Extractor Functoid Not Valid</span></span>
<span data-ttu-id="22df3-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="22df3-103">**Error Code**</span></span>  
  
 <span data-ttu-id="22df3-104">btm1002</span><span class="sxs-lookup"><span data-stu-id="22df3-104">btm1002</span></span>  
  
 <span data-ttu-id="22df3-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="22df3-105">**Explanation**</span></span>  
  
 <span data-ttu-id="22df3-106">Le premier paramètre d’entrée pour le fonctoid **extracteur de valeur** fonctoid doit correspondre à la sortie (jeu d’enregistrements ADO) à partir de la **recherche de base de données** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="22df3-106">The first input parameter to the indicated **Value Extractor** functoid must be the output (an ADO recordset) from the **Database Lookup** functoid.</span></span>  
  
 <span data-ttu-id="22df3-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="22df3-107">**User Action**</span></span>  
  
 <span data-ttu-id="22df3-108">Vérifiez que la première entrée à tous les **extracteur de valeur** fonctoids est un lien entre un **recherche de base de données** fonctoid à gauche de la page de grille de mappage.</span><span class="sxs-lookup"><span data-stu-id="22df3-108">Ensure that the first input to all **Value Extractor** functoids is a link from a **Database Lookup** functoid to their left in a map grid page.</span></span>