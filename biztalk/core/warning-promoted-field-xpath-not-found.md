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
# <a name="warning---promoted-field-xpath-not-found"></a>Avertissement - champ XPath promu introuvable
**Code d’erreur**  
  
 BEC1005  
  
 **Explication**  
  
 Le nœud correspondant à la promotion du champ de propriété indiquée peut ne pas exister dans le schéma. L’Éditeur BizTalk ne peut pas résoudre des spécifications XPath complexes, et si vous avez modifié la XPath de propriété promue dans le **modifier le XPath d’Instance** boîte de dialogue, il peut ou peut identifier pas correctement le nœud que vous souhaitez promouvoir.  
  
 **Action de l’utilisateur**  
  
 Vous pouvez conserver cet avertissement ne s’affiche plus, modifiez le XPath de la propriété promue dans le **modifier le XPath d’Instance** boîte de dialogue, vous pouvez accéder à partir de cellules dans le **chemin d’accès du nœud** colonne de la **Liste de champs de propriété** table sur le **champs de propriété** onglet dans le **promouvoir les propriétés** boîte de dialogue. Vous pouvez accéder à la **promouvoir les propriétés** boîte de dialogue à partir de la **promouvoir les propriétés** propriété de la **schéma** nœud dans le Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés.