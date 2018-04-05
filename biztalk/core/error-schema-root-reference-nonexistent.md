---
title: 'Erreur : référence de racine du schéma inexistante | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.rootRefNonExistent
ms.assetid: 84eaa5fb-f0b5-4a41-b935-e6d3ed734aba
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d391af259d7e91f73e1979cc9515469f96a4f0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---schema-root-reference-nonexistent"></a><span data-ttu-id="f996c-102">Erreur : référence de racine du schéma inexistante</span><span class="sxs-lookup"><span data-stu-id="f996c-102">Error - Schema Root Reference Nonexistent</span></span>
<span data-ttu-id="f996c-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="f996c-103">**Error Code**</span></span>  
  
 <span data-ttu-id="f996c-104">BEC2006</span><span class="sxs-lookup"><span data-stu-id="f996c-104">BEC2006</span></span>  
  
 <span data-ttu-id="f996c-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="f996c-105">**Explanation**</span></span>  
  
 <span data-ttu-id="f996c-106">Le **référence de racine** propriété de la **schéma** nœud fait référence à un nœud racine qui n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="f996c-106">The **Root Reference** property of the **Schema** node is referencing a nonexistent root node.</span></span> <span data-ttu-id="f996c-107">Le nœud racine référencés ont été supprimé ou renommé après qu’il a été défini comme le **référence de racine** valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="f996c-107">The referenced root node may have been deleted or renamed after it was set as the **Root Reference** property value.</span></span>  
  
 <span data-ttu-id="f996c-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="f996c-108">**User Action**</span></span>  
  
 <span data-ttu-id="f996c-109">Définir le **référence de racine** propriété de la **schéma** à nouveau le nœud.</span><span class="sxs-lookup"><span data-stu-id="f996c-109">Set the **Root Reference** property of the **Schema** node again.</span></span> <span data-ttu-id="f996c-110">La liste déroulante de cette propriété inclut tous les choix valides pour ces nœuds racines.</span><span class="sxs-lookup"><span data-stu-id="f996c-110">The drop-down list for that property includes all currently valid choices for root nodes.</span></span>