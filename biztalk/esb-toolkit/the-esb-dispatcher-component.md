---
title: "Le composant de répartiteur ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85655b5f-4717-42d1-b005-0a5592d5653b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe377221034637eab23b70c50ccf48a8454a23bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-dispatcher-component"></a>Le composant de répartiteur ESB
Services d’itinéraire basés sur la messagerie sont exécutées dans le composant du répartiteur d’ESB. Le composant de répartiteur peut définir également dynamiquement les propriétés d’emplacement de point de terminaison pour les messages sortants et transformer dynamiquement des messages.  
  
## <a name="component-properties"></a>Propriétés du composant  
 Le composant de répartiteur a six propriétés :  
  
-   **RoutingServiceName**. Cette propriété spécifie le nom enregistré pour le service de routage basé sur la messagerie. La valeur par défaut est **Microsoft.Practices.ESB.Services.Routing**.  
  
-   **TransformServiceName**. Cette propriété spécifie le nom inscrit pour le service de messagerie-en fonction de transformation. La valeur par défaut est **Microsoft.Practices.ESB.Services.Transform**.  
  
-   **Valider**. Cette propriété spécifie si un message doit être validée.  
  
-   **Activé**. Cette propriété Active ou désactive le composant.  
  
-   **Point de terminaison**. Cette propriété est une chaîne de connexion de programme de résolution dans un format enregistré avec BizTalk ESB Toolkit.  
  
-   **Nom de mappage**. Cette propriété est le nom qualifié complet d’un mappage ou un format de chaîne de connexion est inscrite avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:  
  
    -   Voici un exemple d’un nom de mappage :  
  
        ```  
        GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN, GlobalBank.ESB.DynamicResolution.Transforms, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c2c8b2b87f54180a  
        ```