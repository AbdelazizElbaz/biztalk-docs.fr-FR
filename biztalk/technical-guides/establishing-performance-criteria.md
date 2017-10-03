---
title: "L’établissement de critères de performances | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 181011d1-aa74-43fe-b05a-30b043956d70
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5317445a5cf7e1e0b3fc07ab6ac301c764501460
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="establishing-performance-criteria"></a>L’établissement de critères de performances
Les objectifs de performance d’une solution BizTalk Server appartiennent généralement à une des deux catégories, débit et de latence. Cette rubrique décrit les facteurs à prendre en compte lors de l’évaluation du débit ou la latence d’une solution BizTalk Server.  
  
> [!NOTE]  
>  Optimisation de débit et latence d’une solution BizTalk Server souvent représente des objectifs en conflit. Par exemple, vous pouvez améliorer le débit du fichier de l’adaptateur de réception en augmentant la taille de lot, mais cela réduit la latence. Dans ce scénario, l’adaptateur prend plus de temps à accumuler les messages pour une plus grande taille de lot, qui à son tour sera réduire la latence de bout en bout pour un message donné.  
  
## <a name="factors-affecting-throughput-of-a-biztalk-server-solution"></a>Facteurs qui affectent le débit d’une solution BizTalk Server  
 **Débit**- généralement mesurée en tant que le nombre de documents une solution BizTalk Server peut traiter dans un intervalle de temps donné.  
  
 Les facteurs qui affectent le débit sont les suivantes :  
  
-   **Taille de message** – messages plus volumineux consomment plus de charge que les messages plus petits, surtout si les messages sont transformés avec une carte et sont assez grandes afin qu’ils sont mis en mémoire tampon pour le système de fichiers lors de l’opération de mappage. Pour plus d’informations sur les effets de taille des messages sur les performances de BizTalk Server, consultez [comment BizTalk Server processus des Messages volumineux](http://go.microsoft.com/fwlink/?LinkId=139293) (http://go.microsoft.com/fwlink/?LinkId=139293).  
  
-   **Format de message** -Messages sont reçus dans BizTalk Server dans un des deux principaux formats, des fichiers XML ou des fichiers plats. Étant donné que les fichiers plats doivent être traduits dans le format XML pour être traités par le moteur de messagerie BizTalk, une surcharge supplémentaire est induite par le traitement des fichiers plats.  
  
-   **Exigences de carte** – différents adaptateurs ont souvent des capacités de performance différents. Par exemple, les adaptateurs qui requièrent la prise en charge de la transaction MSDTC entraîne supplémentaire des performances surcharge/réduits par rapport à un adaptateur qui n’utilise pas de transactions MSDTC. Adaptateurs utilisés par la solution BizTalk varie en fonction des exigences et/ou les impératifs de fonctionnement interne de votre partenaire commercial.  
  
-   **Le traitement des exigences d’orchestration** : Orchestrations fournissent une grande souplesse pour l’encapsulation et appliquer des processus d’entreprise pour les messages reçus par BizTalk Server. En même temps, les orchestrations consomment surcharge, ce qui doit être pris en compte lors de l’estimation du débit d’une solution BizTalk Server.  
  
-   **Conditions de charge maximale** – la plupart des traitements de document ne se produit pas nécessairement de manière ordonnée mesurée. Par exemple, une solution BizTalk Server peut supporter un grand pourcentage de sa charge de traitement à la fin d’une journée de travail. Par conséquent, les conditions de charge maximale et le Maximum acceptable débit acceptable d’une solution BizTalk Server doivent prendre en considération lors de l’établissement de critères de débit. Pour plus d’informations sur la mesure du débit maximal acceptable d’une solution BizTalk Server, consultez [mesure moteur débit maximal](http://go.microsoft.com/fwlink/?LinkID=154388) (http://go.Microsoft.com/fwlink/?) LinkID = 154388) et [mesurer le débit de suivi maximal acceptable](http://go.microsoft.com/fwlink/?LinkID=153815) (http://go.Microsoft.com/fwlink/?) LinkID = 153815).  
  
-   **Spécifications de suivi de document** : le suivi des documents impose une charge supplémentaire sur le système. Spécifications de suivi de document doit être une considération lorsque vous estimez les objectifs de débit d’une solution BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodologie de test de performances de BizTalk Server](../technical-guides/biztalk-server-performance-testing-methodology.md)