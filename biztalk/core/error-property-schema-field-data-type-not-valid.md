---
title: Erreur - Type de données de champ d’un schéma de propriété non valide | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.propSchemaFieldDataTypeNotValid
ms.assetid: eba41c5c-5512-4cc9-ab10-07626cfbd178
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e0019ccb4f8d138245e2bd58174ed22a532ee7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---property-schema-field-data-type-not-valid"></a><span data-ttu-id="32d15-102">Erreur - Type de données de champ d’un schéma de propriété non valide</span><span class="sxs-lookup"><span data-stu-id="32d15-102">Error - Property Schema Field Data Type Not Valid</span></span>
<span data-ttu-id="32d15-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="32d15-103">**Error Code**</span></span>  
  
 <span data-ttu-id="32d15-104">BEC2010</span><span class="sxs-lookup"><span data-stu-id="32d15-104">BEC2010</span></span>  
  
 <span data-ttu-id="32d15-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="32d15-105">**Explanation**</span></span>  
  
 <span data-ttu-id="32d15-106">Le **Type de données** propriété du **élément de champ** nœuds dans les schémas de propriété doivent être définis sur un des types de données indiqué.</span><span class="sxs-lookup"><span data-stu-id="32d15-106">The **Data Type** property of **Field Element** nodes in property schemas must be set to one of the indicated data types.</span></span> <span data-ttu-id="32d15-107">La promotion de propriétés étant limitée à ces types de données, vous ne pouvez pas en utiliser d'autres dans les schémas de propriété.</span><span class="sxs-lookup"><span data-stu-id="32d15-107">Because property promotion is limited to data of these types only, you cannot use other data types in property schemas.</span></span>  
  
 <span data-ttu-id="32d15-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="32d15-108">**User Action**</span></span>  
  
 <span data-ttu-id="32d15-109">Sélectionnez le **élément de champ** nœud, puis dans le Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, modifier le **Type de données** propriété à un des types de données indiquée.</span><span class="sxs-lookup"><span data-stu-id="32d15-109">Select the indicated **Field Element** node, and then in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, change the **Data Type** property to one of the indicated data types.</span></span>