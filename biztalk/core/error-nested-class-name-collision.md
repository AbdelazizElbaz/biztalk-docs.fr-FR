---
title: "Erreur : Collision de nom de classe imbriquée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.nestedClassNameCollision
ms.assetid: dd636d25-d0c1-41be-a2ba-b38ea97b973d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4a9fa7a9f57088b3fb93e2eb6024e9b6aad49c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---nested-class-name-collision"></a><span data-ttu-id="fc023-102">Erreur : Collision de nom de classe imbriquée</span><span class="sxs-lookup"><span data-stu-id="fc023-102">Error - Nested Class Name Collision</span></span>
<span data-ttu-id="fc023-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="fc023-103">**Error Code**</span></span>  
  
 <span data-ttu-id="fc023-104">BEC2017</span><span class="sxs-lookup"><span data-stu-id="fc023-104">BEC2017</span></span>  
  
 <span data-ttu-id="fc023-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="fc023-105">**Explanation**</span></span>  
  
 <span data-ttu-id="fc023-106">Le **nom de Type** propriété de ce schéma a été trouvée pour être le même que le **RootNode TypeName** propriété de l’un des nœuds racines dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="fc023-106">The **Type Name** property of this schema was found to be the same as the **RootNode TypeName** property of one of the root nodes in the schema.</span></span> <span data-ttu-id="fc023-107">Les classes imbriquées portant le même nom ne sont pas prises en charge par C#. Par conséquent, une erreur est renvoyée.</span><span class="sxs-lookup"><span data-stu-id="fc023-107">C# disallows nested classes with the same names; therefore this condition causes an error.</span></span>  
  
 <span data-ttu-id="fc023-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="fc023-108">**User Action**</span></span>  
  
 <span data-ttu-id="fc023-109">Changez l'une des valeurs de propriété concernées de façon à ne plus avoir de conflit de nom.</span><span class="sxs-lookup"><span data-stu-id="fc023-109">You must change one or both of the relevant property values so that you avoid the name collision.</span></span> <span data-ttu-id="fc023-110">Vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="fc023-110">Either:</span></span>  
  
-   <span data-ttu-id="fc023-111">Sélectionnez le fichier de schéma approprié dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, puis, dans la fenêtre Propriétés, modifiez la **nom de Type** propriété à une valeur valide unique.</span><span class="sxs-lookup"><span data-stu-id="fc023-111">Select the relevant schema file in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, and then in the Properties window, change the **Type Name** property to a unique valid value.</span></span>  
  
     <span data-ttu-id="fc023-112">\- ou -</span><span class="sxs-lookup"><span data-stu-id="fc023-112">\- or -</span></span>  
  
-   <span data-ttu-id="fc023-113">Sélectionnez le nœud racine indiqué, puis, dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, modifier le **RootNode TypeName** propriété à une valeur valide unique.</span><span class="sxs-lookup"><span data-stu-id="fc023-113">Select the indicated root node, and then in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, change the **RootNode TypeName** property to a unique valid value.</span></span>