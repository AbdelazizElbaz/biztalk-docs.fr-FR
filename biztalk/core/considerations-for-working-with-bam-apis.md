---
title: "Considérations pour l’utilisation des API BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd8ccf63-6989-4ad6-a193-cf3043e9a466
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b00eb00013fefde42e1972b89a661d0a2ba0de6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-for-working-with-bam-apis"></a>Éléments à prendre en compte pour travailler avec les API de l'analyse BAM
Lors de l'utilisation d'un objet « Microsoft.BizTalk.Bam.EventObservation.EventStream » tel que DirectEventStream, BufferedEventStream, MessagingEventStream ou OrchestrationEventStream, l'analyse BAM capture des étapes majeures de sorte qu'elles sont automatiquement enregistrées au format UTC (Coordinated Universal Time, également appelé Greenwich Mean Time, ou heure du méridien de Greenwich). Lorsque vous envoyez des dates et des heures à l'analyse BAM à l'aide des API, elles sont reçues au format envoyé et ne sont pas converties au format UTC. Veuillez tenir compte des considérations suivantes lorsque vous développez vos solutions d'analyse BAM :  
  
-   Les données suivies à partir de BizTalk Server sont reçues au format UTC. Il se peut qu'elles diffèrent des autres données issues du flux d'événements.  
  
-   Si vous utilisez les API de flux d'événements pour fournir des données de suivi de date et d'heure au format d'heure locale, les données figurant dans le portail BAM seront incorrectes, car toutes les dates et les heures des données BAM sont censées être au format UTC.  
  
 Si certaines de vos applications utilisent l'heure locale, que vous effectuez une mise à niveau et envisagez d'utiliser le portail BAM, vous devez modifier vos données afin de les rendre conformes au format UTC. Vous devez également modifier votre application personnalisée afin de la convertir au format UTC.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de Solutions BAM](../core/implementing-bam-solutions.md)