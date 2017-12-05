---
title: Transformer et acheminer les messages vers plusieurs points de terminaison | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 544db12c-95fc-4321-b397-ec9e7410e37d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c0fc2b3b9893607f760c564d03fc6090a7f1ea0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="transforming-and-routing-a-message-to-multiple-endpoints"></a>Transformer et acheminer les messages vers plusieurs points de terminaison
Dans ce cas de figure, l’architecture ESB effectue une transformation sur un message envoyé via le Web de l’itinéraire service rampe d’entrée. Une recherche de résolution dynamique détermine le nom de mappage et transforme le message entrant. En outre, l’itinéraire spécifie un nombre n de point de terminaison cible résoudre dynamiquement le service de la feuille de route et à laquelle il achemine le message transformé. Toutes les opérations se produisent au niveau de la couche de messagerie, comme illustré dans la Figure 1.  
  
 ![Transformation de plusieurs points de terminaison](../esb-toolkit/media/ch3-transformingmultipleendpoints.gif "Ch3-TransformingMultipleEndpoints")  
  
 **Figure 1**  
  
 **Transformer et acheminer les messages vers plusieurs points de terminaison**  
  
 L’exemple de résolution dynamique fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. Il montre comment utiliser les composants de pipeline ESB, spécifiquement le composant désassembleur de Dispatch ESB, dynamiquement résoudre l’emplacement du point de terminaison, définir des propriétés de routage et résoudre et exécuter BizTalk Server mappe au niveau de la messagerie, sans utiliser un orchestration. Il montre également les modèles de messagerie unidirectionnels ou bidirectionnels.  
  
 Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md) et [installer et exécuter l’exemple de Services Web plusieurs](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).