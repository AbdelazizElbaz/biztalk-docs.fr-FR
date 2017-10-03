---
title: Test de charge de saturation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LoadGen tool, simulating floodgate events
- performance, floodgate peaks
- floodgate events [performance]
ms.assetid: 937f2478-339b-4ae2-b107-56f3a4bfc579
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74954d8b94207832ceee5bbb699a7de1a245f61b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="floodgate-load-test"></a>Test de l'état de saturation
Les informations contenues dans cette rubrique fait référence aux tests décrits dans [des scénarios de Test pour mesurer le débit maximal acceptable du moteur de](../core/test-scenarios-for-measuring-mst-of-the-engine.md).  
  
## <a name="what-causes-floodgate-events"></a>Origines des événements de saturation  
 Il existe plusieurs scénarios où il y a seulement quelques pics (également appelé **événements de saturation**) massives de messages au niveau du système chaque jour. Entre ces pics d'activité, le débit peut être très modeste. Voici quelques exemples de ces scénarios :  
  
-   les opérations sur les actions, à l'ouverture et à la clôture du marché ;  
  
-   les systèmes bancaires, par exemple pendant le rapprochement des transactions en fin de journée.  
  
 D'autres types d'événements peuvent causer des retards similaires à ceux provoqués par les événements de saturation. Par exemple, si l'adresse d'envoi d'un partenaire devient indisponible et que les messages destinés à cette adresse doivent être renvoyés et/ou suspendus, cela peut entraîner une accumulation de travaux en retard. Quand le partenaire est à nouveau connecté, il risque d'y avoir un volume considérable de messages suspendus qu'il faut reprendre, ce qui génère un autre type d'événement de saturation. Le test suivant du système illustre ce fonctionnement :  
  
## <a name="simulating-a-floodgate-event"></a>Simulation d'un événement de saturation  
 Pour ce test, le système a fonctionné initialement à la moitié environ de son débit maximum et était donc très stable. Ensuite, pour simuler un événement de saturation, l'outil de génération de charge a été configuré afin d'envoyer 410 msg/s environ pendant un temps très court (le même que pour le test de surcharge). Le profil de charge obtenu, qui mesure les messages reçus par seconde et la profondeur du spouleur, est affiché ci-après.  
  
 **Profil de charge du test de charge de saturation**  
  
 ![Moniteur de performances de l’état de saturation](../core/media/bts06-floodgate-load.gif "BTS06_Floodgate_Load")  
  
 Notez que dans les tables de mise en file d'attente, le nombre de messages en attente de traitement augmente très vite pendant l'événement de saturation. Toutefois, l'événement étant relativement court et le taux de réception après l'événement inférieur au taux maximal, les fonctions de nettoyage ont pu s'exécuter et le système a pu récupérer de l'événement sans qu'il soit nécessaire d'interrompre la réception des messages. Pour ce test particulier, qui a duré 45 minutes environ, la base de données MessageBox était hébergée par SQL Server 2005.  
  
 Bien sûr, chaque système est différent, et les « valeurs limites » varieront de l'un à l'autre. Le meilleur moyen de vérifier qu'une récupération est possible consiste à faire un test avec une charge représentative avant le passage en production.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénarios de test pour mesurer le débit maximal acceptable du moteur](../core/test-scenarios-for-measuring-mst-of-the-engine.md)   
 [À l’aide du Panneau de configuration de BizTalk Server réglage des performances](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)   
 [Test de surcharge](../core/overdrive-load-test.md)   
 [Test de charge maximale](../core/sustainable-load-test.md)