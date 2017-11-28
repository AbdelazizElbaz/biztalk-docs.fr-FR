---
title: "Opérations sur les fonctions et procédures avec enregistrement Types1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afc1c84f-2e36-493c-9ea8-4bc2248331db
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43974d1c392a357b9781ff7f6fae5286e282513a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-functions-and-procedures-with-record-types"></a><span data-ttu-id="89bc4-102">Opérations sur les fonctions et procédures avec des Types d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="89bc4-102">Operations on Functions and Procedures with RECORD Types</span></span>
<span data-ttu-id="89bc4-103">Types d’enregistrements Oracle sont utilisés pour représenter des informations hiérarchiques dans les paramètres passés aux procédures et fonctions de PL/SQL.</span><span class="sxs-lookup"><span data-stu-id="89bc4-103">Oracle RECORD types are used to represent hierarchical information in parameters passed to PL/SQL functions and procedures.</span></span> <span data-ttu-id="89bc4-104">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence des types d’enregistrement en tant que types XML complexes.</span><span class="sxs-lookup"><span data-stu-id="89bc4-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces RECORD types as complex XML types.</span></span> 

## <a name="supported-record-types"></a><span data-ttu-id="89bc4-105">Prise en charge des types d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="89bc4-105">Supported RECORD types</span></span>
<span data-ttu-id="89bc4-106">Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] prend en charge les types de types d’enregistrements suivants :</span><span class="sxs-lookup"><span data-stu-id="89bc4-106">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] supports the following kinds of RECORD types:</span></span>  
  
-   <span data-ttu-id="89bc4-107">Types d’enregistrements qui sont déclarés en tant que TABLE % ROWTYPE paramètres dans les procédures stockées et fonctions.</span><span class="sxs-lookup"><span data-stu-id="89bc4-107">RECORD types that are declared as TABLE%ROWTYPE parameters in stored procedures and functions.</span></span>  
  
-   <span data-ttu-id="89bc4-108">Types d’enregistrements qui sont déclarés en tant que paramètres de TYPE d’enregistrement dans les packages de PL/SQL.</span><span class="sxs-lookup"><span data-stu-id="89bc4-108">RECORD types that are declared as TYPE of RECORD parameters in PL/SQL packages.</span></span> <span data-ttu-id="89bc4-109">Par exemple, tapez rec_type1 est RECORD(name varchar2(100), age number(3));</span><span class="sxs-lookup"><span data-stu-id="89bc4-109">For example, TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));</span></span>  
  
-   <span data-ttu-id="89bc4-110">Types d’enregistrements qui contiennent des enregistrements imbriqués.</span><span class="sxs-lookup"><span data-stu-id="89bc4-110">RECORD types that contain nested records.</span></span>  
  
-   <span data-ttu-id="89bc4-111">Types d’enregistrements qui s’affichent, OUT ou paramètres dans des procédures ou des fonctions.</span><span class="sxs-lookup"><span data-stu-id="89bc4-111">RECORD types that appear as IN, OUT, or IN OUT parameters to procedures or functions.</span></span>  
  
-   <span data-ttu-id="89bc4-112">Types d’enregistrements qui sont des valeurs de retour des fonctions.</span><span class="sxs-lookup"><span data-stu-id="89bc4-112">RECORD types that are RETURN values of functions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="89bc4-113">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les types BFILE en tant que membres de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="89bc4-113">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support BFILE types as RECORD members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89bc4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89bc4-114">See Also</span></span>  
 <span data-ttu-id="89bc4-115">[Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="89bc4-115">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>