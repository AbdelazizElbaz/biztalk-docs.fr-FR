---
title: "Dépassement de Test de charge | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d16d0a8-4255-4f5a-86a2-26cc11bb9a70
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cff4592c58dd165a85d63666958721231cfcbd4c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="overdrive-load-test"></a>Test Overdrive de chargement
Les informations contenues dans cette rubrique fait référence aux tests décrits dans [des scénarios de Test pour mesurer le débit maximal acceptable du moteur de](../core/test-scenarios-for-measuring-mst-of-the-engine.md).  
  
 L'outil de génération de charge, LoadGen 2007, vous permet de simuler de lourdes charges sur un système BizTalk Server.  
  
> [!NOTE]
>  Télécharger [LoadGen](https://www.microsoft.com/download/details.aspx?id=14925). La version précédente de cet outil, l’outil de génération de charge de BizTalk Server 2004 est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?linkid=108999](http://go.microsoft.com/fwlink/?linkid=108999).  
  
 Pour simuler un système fonctionnant en permanence au-delà de ses capacités, LoadGen 2007 a été configuré de sorte à envoyer environ 410 msgs/s, à savoir 120 msgs/s de plus que le débit maximal acceptable mesuré.  
  
 Ce test a été conçu non seulement pour dépasser le système, mais aussi pour savoir combien de temps cela prendrait pour le récupérer après une accumulation d'une profondeur de mise en file d'attente d'environ 2 millions d'enregistrements.  
  
 Pour ce faire, le système a été poussé à la vitesse supérieure jusqu'à ce que la profondeur de mise en file d'attente atteigne environ 2 millions d'enregistrements. Lorsque cette profondeur a atteint le niveau désiré, aucune autre charge n'est générée.  
  
 Pour vous assurer que le mécanisme de limitation BizTalk ne pas limiter l’hôte de réception, ce qui empêcherait l’accumulation d’un backlog de la table spool, le **nombre dans la base de données de messages** seuil de limitation de l’hôte de réception a été modifié à partir de la valeur par défaut 50000 à 2000000. Pour plus d’informations sur la modification de la **nombre dans la base de données de messages** seuil de limitation, consultez [comment modifier les ressources de limitation paramètres](../core/how-to-modify-resource-based-throttling-settings.md). Pour plus d’informations sur l’hôte par défaut de paramètres de limitation, consultez [à l’aide de paramètres de tableau de bord pour BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).  
  
 Le graphique suivant présente les mêmes indicateurs que le graphique ci-dessus.  
  
 **Profil de charge du test de surcharge**  
  
 ![Affichage dans l’Analyseur de performances de la surcharge](../core/media/bts06-overdrive-load.gif "BTS06_Overdrive_Load")  
  
 Comme le montre le graphique, la profondeur de mise en file d'attente a commencé à augmenter immédiatement pour atteindre jusqu'à 2 millions d'enregistrements. À ce taux, il a fallu environ 2 heures et demi pour atteindre l'accumulation de messages prévue de 2 millions d'enregistrements. Une fois la charge arrêtée, il a fallu environ 8 heures pour que les fonctions de nettoyage récupèrent de l'accumulation de messages.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénarios de test pour mesurer le débit maximal acceptable du moteur](../core/test-scenarios-for-measuring-mst-of-the-engine.md)   
 [À l’aide du Panneau de configuration de BizTalk Server réglage des performances](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)   
 [Test de charge maximale](../core/sustainable-load-test.md)