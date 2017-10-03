---
title: "Création de Pipelines à l’aide du Concepteur de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, processing messages
- pipelines, Pipeline Designer
- Pipeline Designer, about Pipeline Designer
ms.assetid: 858302d8-a912-4199-95e5-4322db789b4e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18b693a4e8df20a7f39f81fb820810c1191ef637
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-pipelines-using-pipeline-designer"></a>Création de Pipelines à l’aide du Concepteur de Pipeline
Microsoft BizTalk Server fonctionne principalement avec le format de document XML. Pour qu'un message puisse pleinement profiter du traitement BizTalk Server, son format natif doit souvent être converti en sa représentation XML. Les pipelines BizTalk Server effectuent cette conversion, ainsi que d'autres actions spécifiques aux données (chiffrement ou déchiffrement de données, promotion des propriétés, etc.) sur les messages entrants et sortants. Cette section fournit des informations concernant les concepts et les tâches spécifiques aux pipelines et au Concepteur de pipeline.  
  
 L'objectif d'un pipeline est de préparer les messages soit en vue de leur traitement par le serveur après leur réception par un adaptateur, soit en vue de leur envoi après leur traitement par le serveur.  
  
 Tâches couramment effectuées par les pipelines :  
  
-   Régularisation des données à partir de divers formats vers le format XML  
  
-   Conversion des données à partir du format XML vers divers formats  
  
-   Promotion et rétrogradation des propriétés  
  
-   Désassemblage et assemblage de documents  
  
-   Codage et décodage de documents  
  
-   Chiffrement et déchiffrement de documents  
  
-   Signature de documents et vérification de signatures numériques  
  
 La figure ci-dessous montre le workflow que suppose le traitement d'un message à l'aide de pipelines.  
  
 ![Diagramme de flux de travail pour le traitement d’un message. ] (../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")  
Illustration du workflow de traitement d'un message  
  
 Comme le montre la figure, le message passe de l'adaptateur au pipeline de réception, où il est converti au format XML. Le message peut alors être utilisé par des orchestrations ou être transmis à un pipeline d'envoi puis à un adaptateur d'envoi.  
  
 Pour plus d’informations sur l’utilisation des raccourcis clavier pour le Concepteur de Pipeline, consultez [raccourcis clavier de Concepteur de Pipeline](../core/pipeline-designer-keyboard-shortcuts.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [À propos des Pipelines, des étapes et des composants](../core/about-pipelines-stages-and-components.md)  
  
-   [À l’aide du Concepteur de Pipeline](../core/using-pipeline-designer.md)  
  
-   [Création de Pipelines avec le Concepteur de Pipeline](../core/creating-pipelines-with-pipeline-designer.md)  
  
-   [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)  
  
-   [Comment déployer des Pipelines](../core/how-to-deploy-pipelines.md)  
  
-   [Sécurisation des Pipelines](../core/how-to-secure-pipelines.md)