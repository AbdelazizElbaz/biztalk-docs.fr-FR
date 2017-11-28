---
title: "Erreur : champ de propriété manquant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.propFieldMissing
ms.assetid: 8d07e72b-f876-4a37-8c95-ec7aa0033983
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d77311e4c8585cfb7f6108364e6a5085619595a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---property-field-missing"></a><span data-ttu-id="3d6c8-102">Erreur : champ de propriété manquant</span><span class="sxs-lookup"><span data-stu-id="3d6c8-102">Error - Property Field Missing</span></span>
<span data-ttu-id="3d6c8-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="3d6c8-103">**Error Code**</span></span>  
  
 <span data-ttu-id="3d6c8-104">BEC2008</span><span class="sxs-lookup"><span data-stu-id="3d6c8-104">BEC2008</span></span>  
  
 <span data-ttu-id="3d6c8-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="3d6c8-105">**Explanation**</span></span>  
  
 <span data-ttu-id="3d6c8-106">Le nœud indiqué dans ce schéma est promu à un **élément de champ** nœud dans le schéma de propriété correspondant n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="3d6c8-106">The indicated node in this schema is being promoted to a **Field Element** node in the corresponding property schema that does not exist.</span></span> <span data-ttu-id="3d6c8-107">Cette condition peut se produire lorsqu’un **élément de champ** nœud est supprimé ou renommé dans un schéma de propriété une fois qu’il a été utilisé comme cible de la promotion des propriétés.</span><span class="sxs-lookup"><span data-stu-id="3d6c8-107">This condition can occur when a **Field Element** node is removed from, or renamed in, a property schema after it has been used as the target of a property promotion.</span></span>  
  
 <span data-ttu-id="3d6c8-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="3d6c8-108">**User Action**</span></span>  
  
 <span data-ttu-id="3d6c8-109">Modifiez le schéma de propriété pour qu’il contienne manquants **élément de champ** nœud, ou utilisez le **promouvoir les propriétés** boîte de dialogue pour supprimer ou de modifier la promotion des propriétés appropriée.</span><span class="sxs-lookup"><span data-stu-id="3d6c8-109">Either modify the property schema so that it contains the missing **Field Element** node, or use the **Promote Properties** dialog box to delete or otherwise modify the relevant property promotion.</span></span>