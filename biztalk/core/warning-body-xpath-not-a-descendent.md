---
title: 'Avertissement : XPath de corps est pas un descendant. | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.bodyXPathNotDescendant
ms.assetid: bfeff370-9b84-4fd9-81e9-1e54b166f561
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70b5d228e1119bc7c569b45cc6795f3f5b8454ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---body-xpath-not-a-descendent"></a><span data-ttu-id="11fb7-102">Avertissement : XPath de corps est pas un descendant.</span><span class="sxs-lookup"><span data-stu-id="11fb7-102">Warning - Body XPath Not A Descendent</span></span>
<span data-ttu-id="11fb7-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="11fb7-103">**Error Code**</span></span>  
  
 <span data-ttu-id="11fb7-104">BEC1004</span><span class="sxs-lookup"><span data-stu-id="11fb7-104">BEC1004</span></span>  
  
 <span data-ttu-id="11fb7-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="11fb7-105">**Explanation**</span></span>  
  
 <span data-ttu-id="11fb7-106">Le **XPath de corps** propriété du nœud racine indiqué dans le schéma d’enveloppe fait référence à un nœud qui n’est pas un descendant de ce nœud racine, en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="11fb7-106">The **Body XPath** property of the indicated root node in this envelope schema references a node that is not a descendent of that root node, as required.</span></span> <span data-ttu-id="11fb7-107">Cette erreur ne doit pas se produire si le **XPath de corps** propriété est modifiée en dehors de l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="11fb7-107">This error should not occur unless the **Body XPath** property is modified outside of BizTalk Editor.</span></span>  
  
 <span data-ttu-id="11fb7-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="11fb7-108">**User Action**</span></span>  
  
 <span data-ttu-id="11fb7-109">Sélectionnez le nœud racine indiqué et sélectionnez la valeur de la **XPath de corps** propriété qui identifie correctement le nœud de niveau supérieur du corps du message associé.</span><span class="sxs-lookup"><span data-stu-id="11fb7-109">Select the indicated root node and select the value for the **Body XPath** property that correctly identifies the top-level node of the associated message body.</span></span>