---
title: 'Erreur : le fichier de schéma dans la Build | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.schemaFileNotInBuild
ms.assetid: 9190868d-a1ae-48bf-ac85-510086805887
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3b5d6d11bec6b9f263e2f204f004a9a162de471
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---schema-file-not-in-build"></a><span data-ttu-id="cf0cb-102">Erreur : le fichier de schéma dans la Build</span><span class="sxs-lookup"><span data-stu-id="cf0cb-102">Error - Schema File Not In Build</span></span>
<span data-ttu-id="cf0cb-103">**Explication**</span><span class="sxs-lookup"><span data-stu-id="cf0cb-103">**Explanation**</span></span>  
  
 <span data-ttu-id="cf0cb-104">La commande (**valider l’Instance**, **générer l’Instance**, ou **valider le schéma**) ne peut pas être effectuée car le **Action de génération** propriété du fichier de schéma est définie sur **aucun**, empêchant ainsi le schéma de participer à ces commandes.</span><span class="sxs-lookup"><span data-stu-id="cf0cb-104">The command (**Validate Instance**, **Generate Instance**, or **Validate Schema**) could not be performed because the **Build Action** property of the schema file is set to **None**, preventing this schema from participating in these commands.</span></span>  
  
 <span data-ttu-id="cf0cb-105">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="cf0cb-105">**User Action**</span></span>  
  
 <span data-ttu-id="cf0cb-106">Sélectionnez le fichier de schéma approprié dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, puis, dans la fenêtre Propriétés, modifiez la **Action de génération** propriété un **compiler**.</span><span class="sxs-lookup"><span data-stu-id="cf0cb-106">Select the relevant schema file in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, and then in the Properties window, change the **Build Action** property to a **Compile**.</span></span> <span data-ttu-id="cf0cb-107">Tentez ensuite la **valider l’Instance**, **générer l’Instance**, ou **valider le schéma** réexécutez la commande.</span><span class="sxs-lookup"><span data-stu-id="cf0cb-107">Then attempt the **Validate Instance**, **Generate Instance**, or **Validate Schema** command again.</span></span>