---
title: "Avertissement : XPath de corps d’enregistrement introuvable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.recordBodyXPathNotFound
ms.assetid: d46e0732-08ce-4292-84d8-56dc020063e2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebd6640aa469fe9383b615d70235ab488c8798f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---record-body-xpath-not-found"></a><span data-ttu-id="65916-102">Avertissement : XPath de corps d’enregistrement introuvable</span><span class="sxs-lookup"><span data-stu-id="65916-102">Warning - Record Body XPath Not Found</span></span>
<span data-ttu-id="65916-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="65916-103">**Error Code**</span></span>  
  
 <span data-ttu-id="65916-104">BEC1008</span><span class="sxs-lookup"><span data-stu-id="65916-104">BEC1008</span></span>  
  
 <span data-ttu-id="65916-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="65916-105">**Explanation**</span></span>  
  
 <span data-ttu-id="65916-106">Le **XPath de corps** propriété du nœud racine indiqué dans le schéma d’enveloppe a été trouvée vide ou faisant référence à un nœud qui n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="65916-106">The **Body XPath** property of the indicated root node in this envelope schema was found to be empty or referencing a nonexistent node.</span></span> <span data-ttu-id="65916-107">Schémas d’enveloppe, tel que spécifié par le **enveloppe** propriété de la **schéma** nœud, doit être une valeur valide le **XPath de corps** propriété de la racine spécifiée nœud de référence dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="65916-107">Envelope schemas, as specified by the **Envelope** property of the **Schema** node, are required to have a valid value in the **Body XPath** property of the specified root reference node in the schema.</span></span>  
  
 <span data-ttu-id="65916-108">Si aucun nœud référence de racine ne spécifié par le **référence de racine** propriété de la **schéma** nœud, le premier nœud racine dans le schéma, le nœud de référence de racine par défaut, est requis pour qu’une valeur valide dans sa  **XPath de corps** propriété.</span><span class="sxs-lookup"><span data-stu-id="65916-108">If no root reference node is specified by the **Root Reference** property of the **Schema** node, the first root node in the schema, the default root reference node, is required to have a valid value in its **Body XPath** property.</span></span> <span data-ttu-id="65916-109">**XPath de corps** valeurs de propriété sont utilisées pour identifier le schéma de chacun des messages contenus dans l’enveloppe.</span><span class="sxs-lookup"><span data-stu-id="65916-109">**Body XPath** property values are used to identify the schema for the each of the messages contained within the envelope.</span></span>  
  
 <span data-ttu-id="65916-110">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="65916-110">**User Action**</span></span>  
  
 <span data-ttu-id="65916-111">Sélectionnez le nœud racine indiqué, puis sélectionnez la valeur de la **XPath de corps** propriété qui identifie correctement le schéma du corps du message associé.</span><span class="sxs-lookup"><span data-stu-id="65916-111">Select the indicated root node and then select the value for the **Body XPath** property that correctly identifies the schema of the associated message body.</span></span>