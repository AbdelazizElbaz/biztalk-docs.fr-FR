---
title: "Erreur : nom de Type non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.typeNameNotValid
ms.assetid: 4c9bceeb-b009-4279-ad16-19af09e6b091
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dac6d85d3b16ec691a4cc73b179515b70686791
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---type-name-not-valid"></a><span data-ttu-id="e80e9-102">Erreur : nom de Type non valide</span><span class="sxs-lookup"><span data-stu-id="e80e9-102">Error - Type Name Not Valid</span></span>
<span data-ttu-id="e80e9-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="e80e9-103">**Error Code**</span></span>  
  
 <span data-ttu-id="e80e9-104">BEC2011</span><span class="sxs-lookup"><span data-stu-id="e80e9-104">BEC2011</span></span>  
  
 <span data-ttu-id="e80e9-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="e80e9-105">**Explanation**</span></span>  
  
 <span data-ttu-id="e80e9-106">Le **nom de Type** propriété de ce fichier de schéma n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="e80e9-106">The **Type Name** property of this schema file is not valid.</span></span> <span data-ttu-id="e80e9-107">Étant donné que la valeur de la **nom de Type** propriété est utilisée comme nom d’un nom de classe c# généré automatiquement, elle doit être un identificateur c# valid et ne peut pas être un mot clé BizTalk réservé.</span><span class="sxs-lookup"><span data-stu-id="e80e9-107">Because the value of the **Type Name** property is used as the name of an automatically generated C# class name, it must be a valid C# identifier and cannot be a reserved BizTalk keyword.</span></span>  
  
 <span data-ttu-id="e80e9-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="e80e9-108">**User Action**</span></span>  
  
 <span data-ttu-id="e80e9-109">Sélectionnez le fichier de schéma approprié dans Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, puis, dans la fenêtre Propriétés, modifiez la **nom de Type** propriété une valeur qui est un identificateur c# valide et n’est pas un mot clé BizTalk réservé.</span><span class="sxs-lookup"><span data-stu-id="e80e9-109">Select the relevant schema file in Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, and then in the Properties window, change the **Type Name** property to a value that is a valid C# identifier and is not a reserved BizTalk keyword.</span></span>