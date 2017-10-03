---
title: "Messages suspendus sont inclus dans le nombre de messages dans le seuil de limitation de la base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eb708bb-6d6d-4494-8b8d-67aa44800a20
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f8ea0643ccf2d6206ba86bc56b5dd54c0d51115
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="suspended-messages-are-included-in-the-message-count-in-database-throttling-threshold"></a>Les messages interrompus sont inclus dans le seuil de limitation Nombre de messages dans la base de données
Par défaut, l’hôte **nombre dans la base de données de messages** seuil de limitation est définie à 50 000, ce qui déclenchera une condition de limitation dans les circonstances suivantes :  
  
-   Le nombre total de messages publiés par l'instance de l'hôte dans les files d'attente de travail, de messages interrompus et d'état des hôtes d'abonnement est supérieur à 50 000.  
  
-   Le nombre de messages de la table de mise en file d’attente ou des tables de suivi est supérieur à 500 000.  
  
 Étant donné que les messages interrompus sont inclus dans le **nombre dans la base de données de messages** calcul, la limitation de publication peut se produire même si le serveur BizTalk server rencontre faible de message ou pas de charge.  
  
## <a name="recommendations"></a>Recommandations  
  
-   Si vous pensez que peut avoir un grand nombre de messages suspendus, envisagez d’augmenter la valeur par défaut pour le **nombre dans la base de données de messages** seuil en prenant en compte l’espace requis par le serveur SQL qui contient le Bases de données BizTalk. Envisagez également d’augmenter la **multiplicateur de Spool** et **multiplicateur de données de suivi** valeurs pour permettre d’en souffrance dans la table du spouleur.  
  
     Pour plus d’informations sur ces valeurs, consultez [comment modifier les ressources de limitation paramètres](../core/how-to-modify-resource-based-throttling-settings.md).  
  
-   Utilisez le **état de limitation de publication de messages** compteur Analyseur de performances associé **BizTalk:MessageAgent** catégorie d’objet de performance pour mesurer l’état de limitation actuel. Si ce compteur renvoie la valeur 6, recherchez les instances interrompues et reprenez ou mettez fin à celles-ci, selon les besoins.  
  
     Pour plus d’informations sur la limitation des compteurs de performance de l’hôte, consultez [hôte la limitation des compteurs de Performance](../core/host-throttling-performance-counters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Limitation des recommandations sur la conception](../core/throttling-design-recommendations.md)