---
title: "L’ajout d’un bloc de Compensation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compensations, compensation blocks
- compensation blocks, adding
ms.assetid: 1bdeed92-3144-44ef-ad0d-1c6976f46a36
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2dec4f4dd01c2bbf522dfff44ec8aaf0c2f5e89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-compensation-block"></a>Ajout d'un bloc de compensation
Si vous n'ajoutez pas votre propre compensation, le moteur d'exécution effectue une compensation par défaut qui appelle les compensations de toutes les transactions imbriquées au sein de la transaction actuelle. Il appelle d'abord la compensation de la transaction terminée la plus récente, puis remonte jusqu'à-ce que toutes les transactions imbriquées aient été compensées.  
  
 Cela est vrai même lorsque votre compensation a lieu à l’intérieur d’une forme boucle : les compensations seront exécutées dans l’ordre inverse. La compensation de la dernière itération de la boucle sera la première appelée, puis la compensation de l'itération précédente sera appelée, et ainsi de suite.  
  
> [!CAUTION]
>  Vu que les données doivent être conservées dans la mémoire physique pour que la compensation fonctionne, l'utilisation de compensations dans une boucle peut affecter les performances, ce qui peut poser problème dans le cas d'un nombre important d'itérations.  
  
 Si l'ordre par défaut ne convient pas à vos besoins, vous pouvez écrire votre propre gestionnaire de compensation qui appellera explicitement les gestionnaires de compensation des étendues imbriquées dans l'ordre de votre choix.  
  
### <a name="to-add-a-compensation-block"></a>Pour ajouter un bloc de compensation  
  
1.  Avec le bouton droit le **étendue** forme de la transaction à laquelle vous souhaitez ajouter un **bloc de Compensation**, puis cliquez sur **nouveau bloc de Compensation**.  
  
    > [!NOTE]
    >  Pour ajouter un **bloc de Compensation** à un **étendue** mettre en forme le **Type de Transaction** propriété de la **étendue** forme doit être définie sur **Atomique** ou **longue**.  
  
     A **bloc de Compensation** est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.  
  
2.  À l’intérieur de la **bloc de Compensation** forme, ajouter des formes pour créer le processus d’annulation d’une transaction validée.