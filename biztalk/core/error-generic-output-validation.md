---
title: 'Erreur : Validation de sortie générique | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.genericOutputValidation
ms.assetid: 27fb2233-3add-42f8-a96b-872e2e38f797
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c1bac5235788f6e369cc316ed1236357a51c004
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---generic-output-validation"></a><span data-ttu-id="f84e6-102">Erreur : Validation de sortie générique</span><span class="sxs-lookup"><span data-stu-id="f84e6-102">Error - Generic Output Validation</span></span>
<span data-ttu-id="f84e6-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="f84e6-103">**Error Code**</span></span>  
  
 <span data-ttu-id="f84e6-104">btm1047</span><span class="sxs-lookup"><span data-stu-id="f84e6-104">btm1047</span></span>  
  
 <span data-ttu-id="f84e6-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="f84e6-105">**Explanation**</span></span>  
  
 <span data-ttu-id="f84e6-106">Le fichier de message de l'instance de sortie créé par l'opération Test Map n'a pas été validé avec le schéma de destination pour une raison inconnue.</span><span class="sxs-lookup"><span data-stu-id="f84e6-106">The output instance message file created by the Test Map operation could not be validated against the destination schema for an unspecified reason.</span></span>  
  
 <span data-ttu-id="f84e6-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="f84e6-107">**User Action**</span></span>  
  
 <span data-ttu-id="f84e6-108">Ouvrir le schéma de destination dans l’Éditeur BizTalk et utiliser le **valider le schéma**, **valider l’Instance**, et **générer l’Instance** commandes, disponibles lorsque vous cliquez sur un schéma dans l’Explorateur de solutions, pour isoler le problème.</span><span class="sxs-lookup"><span data-stu-id="f84e6-108">Open the destination schema in BizTalk Editor and use the **Validate Schema**, **Validate Instance**, and **Generate Instance** commands, available when you right-click a schema in Solution Explorer, to isolate the problem.</span></span>