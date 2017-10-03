---
title: Avertissement - champ XPath promu introuvable | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.promoFieldXPathNotFound
ms.assetid: 21b8c240-5d6f-499d-8211-6e3f2ce2a79c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07f45bd1539817f010864226d07b76ca2feee8b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---promoted-field-xpath-not-found"></a><span data-ttu-id="dc8b0-102">Avertissement - champ XPath promu introuvable</span><span class="sxs-lookup"><span data-stu-id="dc8b0-102">Warning - Promoted Field XPath Not Found</span></span>
<span data-ttu-id="dc8b0-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="dc8b0-103">**Error Code**</span></span>  
  
 <span data-ttu-id="dc8b0-104">BEC1005</span><span class="sxs-lookup"><span data-stu-id="dc8b0-104">BEC1005</span></span>  
  
 <span data-ttu-id="dc8b0-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="dc8b0-105">**Explanation**</span></span>  
  
 <span data-ttu-id="dc8b0-106">Le nœud correspondant à la promotion du champ de propriété indiquée peut ne pas exister dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="dc8b0-106">The node corresponding to the indicated property field promotion may not exist in the schema.</span></span> <span data-ttu-id="dc8b0-107">L’Éditeur BizTalk ne peut pas résoudre des spécifications XPath complexes, et si vous avez modifié la XPath de propriété promue dans le **modifier le XPath d’Instance** boîte de dialogue, il peut ou peut identifier pas correctement le nœud que vous souhaitez promouvoir.</span><span class="sxs-lookup"><span data-stu-id="dc8b0-107">BizTalk Editor cannot resolve complex XPath specifications, and if you edited the promoted property XPath in the **Edit Instance XPath** dialog box, it may or may not correctly identify the node you intended to promote.</span></span>  
  
 <span data-ttu-id="dc8b0-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="dc8b0-108">**User Action**</span></span>  
  
 <span data-ttu-id="dc8b0-109">Vous pouvez conserver cet avertissement ne s’affiche plus, modifiez le XPath de la propriété promue dans le **modifier le XPath d’Instance** boîte de dialogue, vous pouvez accéder à partir de cellules dans le **chemin d’accès du nœud** colonne de la **Liste de champs de propriété** table sur le **champs de propriété** onglet dans le **promouvoir les propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="dc8b0-109">You can keep this warning from appearing by changing the XPath for the promoted property in the **Edit Instance XPath** dialog box, which you can access from cells in the **Node Path** column of the **Property Field List** table on the **Property Fields** tab in the **Promote Properties** dialog box.</span></span> <span data-ttu-id="dc8b0-110">Vous pouvez accéder à la **promouvoir les propriétés** boîte de dialogue à partir de la **promouvoir les propriétés** propriété de la **schéma** nœud dans le Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="dc8b0-110">You can access the **Promote Properties** dialog box from the **Promote Properties** property of the **Schema** node in the Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span>