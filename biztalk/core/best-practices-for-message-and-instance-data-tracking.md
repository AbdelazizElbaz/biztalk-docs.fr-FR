---
title: "Meilleures pratiques pour le Message et le suivi des instances de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HAT, best practices
- best practices, HAT
ms.assetid: 2ac5c87b-2059-4912-9cec-2ae4eaac56df
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a6f673b0a70903575918eb87dc4bd8edc9841e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-message-and-instance-data-tracking"></a>Méthodes conseillées pour le suivi des données de message et d'instance
Consultez les méthodes conseillées suivantes relatives à l'utilisation des données d'historique et de suivi.  
  
-   **Passez en revue les considérations de sécurité pour l’utilisation des données historiques et suivies**  
  
    -   Pour plus d’informations sur les considérations de sécurité pour les données historiques et de suivi, consultez [considérations sur la sécurité de Message et le suivi des données d’Instance](../core/security-considerations-for-message-and-instance-data-tracking.md).  
  
-   **Vérifiez que le service SQL Server Agent s’exécute sur toutes les bases de données MessageBox**  
  
    -   L'Agent SQL Server rend les corps de message disponibles pour la WMI, ainsi que les données d'historique et de suivi. Vous pouvez ainsi exécuter des tâches pour nettoyer les bases de données MessageBox. Pour plus d'informations sur l'Agent SQL Server, consultez la documentation en ligne de SQL Server.  
  
-   **Activer le suivi du corps de message**  
  
    -   Le suivi du corps des messages doit être activé pour permettre l'enregistrement des messages une fois le traitement des instances de service terminé.  
  
-   **Configurer le suivi en fonction de vos besoins**  
  
    -   Avant de pouvoir afficher les données d'historique et de suivi, vous devez configurer le suivi à l'aide de la console Administration de BizTalk Server. Vous devez garder plusieurs considérations à l'esprit lorsque vous activez ou désactivez des options de suivi. Plus le volume de données suivi est important, plus la taille de la base de données de suivi BizTalk (BizTalkDTADb) augmentera rapidement, au détriment des performances d'exécution. Pour plus d’informations, consultez [configuration de suivi à l’aide de la Console Administration de BizTalk Server](http://msdn.microsoft.com/en-us/49b7f9d3-60b5-41bd-ba8b-029253926bef).  
  
-   **Sélectionnez le type approprié de suivi pour le dépannage ou l’audit**  
  
    -   Pour le dépannage dans un environnement de développement ou dans un environnement intermédiaire ou de production, vous devez activer toutes les options de suivi afin de pouvoir consulter les événements d'artefact, les propriétés de message, les corps de message et les événements d'orchestration en détail. Vous disposerez ainsi d'un ensemble étoffé d'informations de suivi, que vous pourrez utiliser pour recréer la séquence d'événements dans votre système et déboguer votre application.  
  
    -   Pour un audit au niveau de la production, choisissez soigneusement les événements à auditer et activez le suivi pour ces événements uniquement. Par exemple, de nombreuses entreprises souhaitent être en mesure de prouver qu'un message est entré ou sorti de leur système. Dans ce cas, vous devez activer le suivi des entrées sur le port de réception approprié et le suivi des sorties sur le port d'envoi correspondant. Au besoin, vous pouvez ajouter le suivi des propriétés et des corps de message.  
  
    -   Pour mesurer les indicateurs clés de performance (KPI) ou l'avancement par rapport à des étapes majeures commerciales préalablement déterminées, vous pouvez mettre en place le suivi de l'analyse BAM. Le suivi BAM offre des capacités limitées en matière de suivi et de stockage des corps de messages. Si ce point est important pour vous, vous devez utiliser les données d'historique et de suivi conjointement avec le suivi BAM. Pour plus d’informations sur le suivi BAM, consultez [à l’aide de l’analyse BAM](../core/using-business-activity-monitoring.md).  
  
-   **Archiver et purger les données de la base de données des suivis BizTalk (BizTalkDTADb) sur une base régulière**  
  
    -   Si vous avez activé le suivi, vous devez archiver et purger régulièrement les données de la base de données de suivi BizTalk afin de lui conserver une taille raisonnable et de préserver les performances du système. Pour plus d’informations, consultez [l’archivage et la purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des messages suivis et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md)