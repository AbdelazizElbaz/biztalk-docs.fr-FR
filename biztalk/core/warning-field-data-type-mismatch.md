---
title: 'Avertissement : incompatibilité de Type de données de champ | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.fieldDataTypeMismatch
ms.assetid: 0c15d926-1d05-404b-bb16-a5fe8bc3575d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af42f5c921333e34c9ee219020cdb0fba97a7b5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---field-data-type-mismatch"></a><span data-ttu-id="4cd2f-102">Avertissement : incompatibilité de Type de données de champ</span><span class="sxs-lookup"><span data-stu-id="4cd2f-102">Warning - Field Data Type Mismatch</span></span>
<span data-ttu-id="4cd2f-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="4cd2f-103">**Error Code**</span></span>  
  
 <span data-ttu-id="4cd2f-104">BEC1002</span><span class="sxs-lookup"><span data-stu-id="4cd2f-104">BEC1002</span></span>  
  
 <span data-ttu-id="4cd2f-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="4cd2f-105">**Explanation**</span></span>  
  
 <span data-ttu-id="4cd2f-106">Le **Type de données** propriété du nœud indiqué a été trouvée pour être différente de celle la **Type de données** propriété de la **élément de champ** nœud auquel il est promu dans le schéma de propriété correspondant.</span><span class="sxs-lookup"><span data-stu-id="4cd2f-106">The **Data Type** property of the indicated node was found to be different than the **Data Type** property of the **Field Element** node to which it is being promoted in the corresponding property schema.</span></span> <span data-ttu-id="4cd2f-107">Le type de données d’un nœud dans un schéma doit correspondre au type de données affecté à la **élément de champ** nœud utilisé pour la promotion du champ de propriété, ou au moins, les types de données affecté doivent correspondre au même type common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4cd2f-107">The data type of a node in a schema should match the data type assigned to the **Field Element** node used for its Property Field promotion, or at least, the assigned data types should map to the same common language runtime (CLR) type.</span></span>  
  
 <span data-ttu-id="4cd2f-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="4cd2f-108">**User Action**</span></span>  
  
 <span data-ttu-id="4cd2f-109">Modifier la **Type de données** propriétés du nœud indiqué et **élément de champ** nœud auquel il est en cours de promotion aux mêmes données de type valeur, ou au moins pour les données de type de valeurs qui correspondent au même type de données CLR.</span><span class="sxs-lookup"><span data-stu-id="4cd2f-109">Change the **Data Type** properties of the indicated node and the **Field Element** node to which it is being promoted to the same data type value, or at least to data type values that map to the same CLR data type.</span></span>