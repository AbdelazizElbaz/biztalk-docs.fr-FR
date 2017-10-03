---
title: "Pipelines d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines, message flow
- send pipelines, about send pipelines
- messages, message flow
- send pipelines, stages
- pipelines, send pipelines
- messages, send pipelines
ms.assetid: c963b2d8-3b2b-4575-8105-c750deae8189
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef08909dbc47e11f5c9fecae6f65e01dbe79441b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-pipelines"></a>Pipelines d’envoi
La figure présente le workflow de traitement d'un message en mettant en avant le rôle du pipeline d'envoi.  
  
 ![Diagramme de flux de travail pour le traitement d’un message. ] (../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")  
Illustration du workflow de traitement d'un message  
  
 Un pipeline d'envoi est chargé de traiter les documents avant leur envoi vers leur destination finale. Il prend en charge un message et produit un message à envoyer.  
  
 Vous pouvez créer un pipeline d'envoi ou utiliser l'un des deux pipelines d'envoi par défaut fournis avec BizTalk Server, le pipeline d'envoi de transfert et le pipeline d'envoi XML.  
  
 Par défaut, le pipeline d’envoi se compose de trois étapes vides : préassembler, assembler et coder. Cette rubrique regroupe des considérations relatives à la conception pour compléter ces étapes.  
  
> [!NOTE]
>  Un pipeline d'envoi peut ne produire aucun message quand un composant de consommation lui est ajouté.  
  
## <a name="pre-assemble-stage"></a>Étape Préassembler  
  
-   Cette étape est un espace réservé aux composants personnalisés qui doivent exécuter une action sur le message avant que ce dernier soit sérialisé.  
  
-   Cette étape est exécutée une seule fois par message.  
  
-   Cette étape peut contenir entre 0 et 255 composants.  
  
-   Tous les composants de cette étape sont exécutés.  
  
## <a name="assemble-stage"></a>Étape Assembler  
  
-   Les composants de cette étape sont chargés d'assembler ou de sérialiser le message et de le convertir au format XML ou à partir de ce format.  
  
-   Cette étape accepte zéro ou un composant.  
  
-   Tous les composants de cette étape sont exécutés.  
  
## <a name="encode-stage"></a>Étape Coder  
  
-   Cette étape est destinée aux composants qui codent ou chiffrent le message.  
  
    -   Vous devez placer le composant Encodeur MIME/SMIME ou un composant de codage personnalisé à cette étape si la signature du message est requise.  
  
-   Cette étape est exécutée une seule fois par message.  
  
-   Cette étape peut contenir entre 0 et 255 composants.  
  
-   Tous les composants de cette étape sont exécutés.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines de réception](../core/receive-pipelines.md)   
 [À propos des Pipelines, des étapes et des composants](../core/about-pipelines-stages-and-components.md)   
 [Types de Pipelines](../core/types-of-pipelines.md)   
 [Pipelines par défaut](../core/default-pipelines.md)   
 [Modèles de pipeline](../core/pipeline-templates.md)   
 [Composants de pipeline](../core/pipeline-components.md)   
 [Types de composants de Pipeline](../core/types-of-pipeline-components.md)