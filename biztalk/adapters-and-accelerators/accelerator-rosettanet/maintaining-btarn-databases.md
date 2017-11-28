---
title: "Maintenance des bases de données BTARN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maintaining databases
- databases, maintaining
ms.assetid: b048f68c-1e12-42e3-b7bb-2a87fe977f4e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ba898931c4fe295c90d6eb94cad60b69d0910d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="maintaining-btarn-databases"></a><span data-ttu-id="a2f20-102">Maintenance des bases de données BTARN</span><span class="sxs-lookup"><span data-stu-id="a2f20-102">Maintaining BTARN Databases</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="a2f20-103">® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] bases de données peuvent augmenter ainsi que leur taille peut affecter les performances du système.</span><span class="sxs-lookup"><span data-stu-id="a2f20-103">® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] databases can grow so large that their size can affect system performance.</span></span> <span data-ttu-id="a2f20-104">Cela peut être dû à des circonstances particulières qui laissent les entrées non utilisées dans les tables, telles que les pièces jointes orphelins ou résumés inutilisés.</span><span class="sxs-lookup"><span data-stu-id="a2f20-104">This can result from specific circumstances that leave unused entries in the tables, such as orphan attachments or unused digests.</span></span> <span data-ttu-id="a2f20-105">Il peut également se produire de ne pas supprimer les anciennes entrées dans les tables.</span><span class="sxs-lookup"><span data-stu-id="a2f20-105">It can also occur from not deleting old entries in the tables.</span></span> <span data-ttu-id="a2f20-106">Suivez les procédures décrites dans cette section pour mettre à jour votre [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] donc aucun effet sur les performances des bases de données.</span><span class="sxs-lookup"><span data-stu-id="a2f20-106">Follow the procedures in this section to maintain your [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] databases so there is no effect on performance.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2f20-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a2f20-107">In This Section</span></span>  
  
-   [<span data-ttu-id="a2f20-108">Gestion des Tables de base de données de non-répudiation</span><span class="sxs-lookup"><span data-stu-id="a2f20-108">Maintaining the Non-Repudiation Database Tables</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/maintaining-the-non-repudiation-database-tables.md)  
  
-   [<span data-ttu-id="a2f20-109">Suppression des résumés</span><span class="sxs-lookup"><span data-stu-id="a2f20-109">Deleting Digests</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/deleting-digests.md)  
  
-   [<span data-ttu-id="a2f20-110">Suppression des pièces jointes orphelins</span><span class="sxs-lookup"><span data-stu-id="a2f20-110">Deleting Orphan Attachments</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/deleting-orphan-attachments.md)