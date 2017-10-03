---
title: "Basculement de serveur du Service de Bus BAM événement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f12378c8-09bb-45c1-ade1-d9b20131461f
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c1fafc3e97d9905a6efd0de8ff0f389c2a389bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-event-bus-service-server-failover"></a>Basculement du serveur de service Bus d'événements BAM
Le service Bus d'événements BAM inclut la logique de tolérance de pannes qui lui permet de récupérer et de redémarrer à partir d'une erreur inattendue sans perdre de données.  
  
 Lorsque vous activez le service Bus d'événements BAM sur plusieurs ordinateurs et que ce service échoue, la logique de basculement et de déplacement détecte cet état de fait et démarre automatiquement une nouvelle instance du service Bus d'événements BAM sur un autre ordinateur.  
  
 La figure suivante illustre comment le Bus d'événements BAM gère les défaillances d'ordinateurs ou de réseaux en effectuant un simple équilibrage de charge. Deux sources et une destination ont été configurées avant le démarrage du Bus d'événements BAM.  
  
 ![](../core/media/ebiz-bam-admin-evntbuspoolfail.gif "ebiz_bam_admin_evntbuspoolfail")  
Comment le service Bus d'événements BAM effectue l'équilibrage de charge  
  
 Le service Bus d'événements BAM effectue l'équilibrage de charge comme suit :  
  
-   **R : serveur1 traite les données d’événement de 2 sources (sessions)**. Avant qu'une instance du service Bus d'événements BAM soit créée sur Serveur2, une instance d'orchestration du bus d'événements BAM est créée sur Serveur1. Le serveur constate l'indisponibilité des autres serveurs et récupère les deux sessions de Src1 et Src2.  
  
-   **B : serveur2 est mis en ligne et rejoint le pool Bus d’événements BAM**. Une fois que l'instance du service Bus d'événements BAM est créée sur Serveur2, Serveur1 abandonne une session du service Bus d'événements BAM et Serveur2 la récupère.  
  
-   **C: défaillance de Serveur1 de**. Défaillance de Serveur1 une fois que Serveur2 a rejoint le pool Bus d'événements BAM.  
  
-   **D: serveur2 traite les données d’événement de 2 sources (sessions)**. Serveur2 récupère les deux sessions pour Src1 et Src2.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion de Service Bus d’événements BAM](../core/managing-the-bam-event-bus-service.md)   
 [Recommandations de sécurité BAM](../core/bam-security-recommendations.md)   
 [Business Activity Monitoring (BAM)](../core/business-activity-monitoring-bam.md)