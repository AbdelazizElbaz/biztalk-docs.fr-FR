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
# <a name="error---schema-file-not-in-build"></a>Erreur : le fichier de schéma dans la Build
**Explication**  
  
 La commande (**valider l’Instance**, **générer l’Instance**, ou **valider le schéma**) ne peut pas être effectuée car le **Action de génération** propriété du fichier de schéma est définie sur **aucun**, empêchant ainsi le schéma de participer à ces commandes.  
  
 **Action de l’utilisateur**  
  
 Sélectionnez le fichier de schéma approprié dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, puis, dans la fenêtre Propriétés, modifiez la **Action de génération** propriété un **compiler**. Tentez ensuite la **valider l’Instance**, **générer l’Instance**, ou **valider le schéma** réexécutez la commande.