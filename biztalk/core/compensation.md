---
title: Compensation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compensations, errors
- compensations
- errors, compensations
- compensations, about compensations
- compensations, atomic transactions
- atomic transactions, compensations
- transactions, compensations
ms.assetid: 0a80dd16-fd35-4f45-95b7-52bb9df80cbb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c572638ea6212c3fb79e6b239aa8ffbe713c3c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="compensation"></a>Compensation
Si une erreur se produit et que vous avez besoin d'annuler ou d'inverser les effets d'une transaction validée avec succès, vous pouvez le faire en ajoutant un code de compensation à votre orchestration.  
  
 La compensation peut être appelée une fois toutes les actions de la transaction effectuées avec succès. À ce stade, l'état de l'orchestration est connu, et les informations relatives à cet état sont disponibles dans le code de la compensation, ce qui signifie que vous pouvez écrire un code qui agira de manière appropriée en fonction de l'état de l'orchestration lorsque la transaction est validée.  
  
 Les compensations sont également possibles pour les transactions atomiques. Ces compensations ne peuvent être appelées qu'une fois la transaction atomique validée. Vous devez écrire un code pour annuler ou inverser le déroulement de l'exécution normale de la compensation.  
  
 Le bloc de compensation est flexible ; il peut contenir toute autre forme, y compris une autre étendue de transaction.  
  
> [!NOTE]
>  Vous ne pouvez utiliser une compensation qu'une seule fois par étendue.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment configurer la forme compenser](../core/how-to-configure-the-compensate-shape.md)  
  
-   [L’ajout d’une Compensation personnalisée à une Orchestration](../core/how-to-add-custom-compensation-to-an-orchestration.md)  
  
-   [L’ajout d’un bloc de Compensation](../core/how-to-add-a-compensation-block.md)