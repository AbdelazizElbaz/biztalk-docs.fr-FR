---
title: "Comment configurer les Types de corrélations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, correlation types
- correlation types, configuring
- correlation types, deleting
- configuring, correlation types
ms.assetid: cfae4d2e-ec79-45c8-93b3-799dc5e0576e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 646ac7dafd5207a2558e45252077efe2d9616a70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-correlation-types"></a>Configuration de types de corrélations
Vous utilisez la **propriétés de corrélation** boîte de dialogue pour ajouter ou supprimer des propriétés d’un type de corrélation. Le type de corrélation répertorie dans un ensemble de corrélations les propriétés utilisées par les activités d'envoi et de réception pour garantir que les messages entrants sont correctement corrélés avec les bonnes instances d'une orchestration lors de l'exécution.  
  
 La boîte de dialogue contient deux volets comportant chacun une liste de propriétés. Le volet gauche, « Propriétés disponibles », contient une arborescence de toutes les propriétés définies dans votre projet ou référencées par lui. Les propriétés qui apparaissent par défaut sont des propriétés système définies par BizTalk Server, mais vous pouvez également définir vos propres propriétés dans un schéma de propriété. Pour plus d’informations sur la création de schémas de propriété, consultez [les schémas de propriété](../core/property-schemas.md).  
  
> [!NOTE]
>  Avant de pouvoir être utilisés dans un type de corrélation, les schémas de propriété doivent être promus. Pour plus d’informations, consultez [promotion des propriétés](../core/promoting-properties.md).  
  
### <a name="to-add-and-configure-a-correlation-type"></a>Ajout et configuration d'un type de corrélation  
  
-   Dans la fenêtre Vue Orchestration, cliquez sur **Types de corrélations** puis cliquez sur **nouveau Type de corrélation**.  
  
     Le **propriétés de corrélation** boîte de dialogue s’affiche. Ajoutez les propriétés à inclure dans votre type de corrélation.  
  
    > [!NOTE]
    >  Si vous accédez à la **propriétés de corrélation** boîte de dialogue directement à partir d’une corrélation défini, un type de corrélation pour l’ensemble de corrélations est créé s’il n’existe pas déjà. Vos modifications seront sauvegardées sous le nouveau type de corrélation et l'ensemble de corrélations sera configuré de manière à l'utiliser. Si un type de corrélation existe déjà pour l'ensemble de corrélations et que vous apportez des modifications, ce type sera modifié.  
  
### <a name="to-remove-a-correlation-type"></a>Suppression d'un type de corrélation  
  
-   Dans la fenêtre Vue Orchestration, cliquez sur le type de corrélation que vous souhaitez supprimer, puis cliquez sur **supprimer**.