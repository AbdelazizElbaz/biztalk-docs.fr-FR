---
title: "Implémentation du modèle de ventilation-regroupement pour plusieurs appels de Service Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 912512a4-9649-40df-bb82-b8f4b85c8ca6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03fb129d23b0884fdca518dca574be64d7672c6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-the-scatter-gather-pattern-for-multiple-web-service-invocations"></a>Implémentation du modèle de ventilation-regroupement pour plusieurs appels de Service Web
Dans ce cas de figure, un message contient une étape de service d’itinéraire qui spécifie plusieurs externe de service qui [!INCLUDE[prague](../includes/prague-md.md)] doit accéder. Il utilise la résolution dynamique pour déterminer les emplacements de service et mappe les points de terminaison et de n’importe quel BizTalk Service facultatif pour la transformation des données retournées. L’orchestration qui implémente ce service effectue la transformation et des appels, et tous les appels de service se produisent de façon asynchrone. Une fois que tous les appels de service terminé, le service d’itinéraire regroupe des réponses dans un message de réponse unique et envoie le message au client via un point de terminaison affecté dynamiquement. La figure 1 illustre ce cas de figure.  
  
 ![Nuage de points de mise en œuvre de rassembler modèle](../esb-toolkit/media/ch3-implementingscatter.gif "Ch3-ImplementingScatter")  
  
 **Figure 1**  
  
 **Implémentation du modèle de ventilation-regroupement pour plusieurs appels de service Web**  
  
 L’exemple de ventilation-regroupement fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.  
  
 Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de ventilation-regroupement](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md).