---
title: "À l’aide du suivi d’événements pour Windows5 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW
- events, Event Tracing for Windows
- controller application
- ETW components
- consumer application
- Provider
- Event Tracing for Windows
- Event Tracing for Windows, components
- BTAPeopleSoftTrace command
ms.assetid: 330ef84b-5e2a-4b79-85a9-72271eb489d2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60a317dabd31bc1a6f37645c6b3fb2ce25d6de43
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-event-tracing-for-windows"></a>À l’aide d’événements de suivi pour Windows
L'adaptateur BizTalk pour PeopleSoft Enterprise consigne les erreurs, avertissements et messages d'information dans l'Observateur d'événements Windows. Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d’événements pour Windows (ETW). Lorsqu'ETW est activé, l'outil crée un fichier *.etl pour recevoir les messages. Le fichier est au format binaire et doit être converti pour être lu. Pour cela, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl, par exemple, tracerpt.exe ou tracedmp.exe.  
  
## <a name="etw-components"></a>Composants ETW  
 Le Suivi d'événements pour Windows comporte trois composants :  
  
-   **Application de contrôleur**: active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).  
  
     Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe. Cela permet de s'assurer que les appels `BTAPeopleSoftTrace` sont en mesure de localiser tracelog.exe dans le système. Par défaut, BTAPeopleSoftTrace recherche le chemin d'accès actuel.  
  
    > [!NOTE]
    >  tracelog.exe est disponible dans le Kit de développement Microsoft (SDK) et il est compatible avec les commandes fournies par l'adaptateur BizTalk pour PeopleSoft Enterprise. Pour utiliser logman.exe, consultez la documentation de logman.  
  
-   **Application consommateur**: lit les événements enregistrés.  
  
     Pour que l'application consommateur puisse lire les événements du fichier .etl, le Suivi d'événements pour Windows doit les vider dans ce fichier. Généralement, cette opération est effectuée lorsque le contrôleur désactive le suivi.  
  
     Pour utiliser le consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel, \<en temps réel\> = -rt.  
  
-   **Fournisseur :** fournit l’événement.  
  
     L'adaptateur BizTalk pour PeopleSoft Enterprise dispose de cinq fournisseurs différents. Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation). Pour rechercher les fournisseurs enregistrés dans le **root\WMI\EventTrace** chemin d’accès, vous pouvez utiliser des outils tels que WMI CIM Studio.  
  
 L'adaptateur BizTalk pour PeopleSoft Enterprise dispose de cinq fournisseurs, vous permettant ainsi de consigner plusieurs sortes de messages :  
  
-   **Fournisseur de journalisation de récepteur**: le \<élément Trace\> commutateur est **-récepteur**.  
  
-   **Fournisseur castdetails pour le récepteur**: le \<élément Trace\> commutateur est **- castDetailsReceive**.  
  
-   **Fournisseur de journalisation de l’émetteur**: le \<élément Trace\> commutateur est **-émetteur**.  
  
-   **Fournisseur castdetails pour l’émetteur**: le \<élément Trace\> commutateur est **- castDetailsTransmit**.  
  
-   **Fournisseur de journalisation de gestion**: le \<élément Trace\> commutateur est **-gestion**.  
  
## <a name="btapeoplesofttrace-command"></a>Commande BTAPeopleSoftTrace  
 Pour utiliser ETW, exécutez la commande de la carte, **BTAPeopleSoftTrace.cmd**. Utilisez-la comme suit :  
  
```  
BTAPeopleSoftTrace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTAPeopleSoftTrace <Trace element> -stop  
```  
  
 Où :  
  
-   \<Élément trace\> (obligatoire) est le type de fournisseur.  
  
     Les options disponibles sont :  
  
    -   **-castDetailsTransmit**  
  
    -   **-émetteur**  
  
    -   **-castDetailsReceive**  
  
    -   **-récepteur**  
  
    -   **-gestion**  
  
    -   **-start, - stop**: activer ou désactiver le fournisseur.  
  
-   **-cir \<Mo\>**: taille et type de fichier. -cir signifie qu'il s'agit d'un fichier circulaire. \<Mo\>: taille en mégaoctets.  
  
-   **-seq \<Mo\>**: taille et type de fichier. -seq signifie qu'il s'agit d'un fichier séquentiel. \<Mo\>: taille en mégaoctets.  
  
-   **-rt**: définir le mode temps réel sur.  
  
-   **Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de C:\rtlog.etl).  
  
 Exemple :  
  
```  
BTAPeopleSoftTrace -transmitter -start -cir 10 -rt C:\log\mylog.etl  
BTAPeopleSoftTrace -transmitter -stop  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de PeopleSoft](../core/troubleshooting-peoplesoft.md)