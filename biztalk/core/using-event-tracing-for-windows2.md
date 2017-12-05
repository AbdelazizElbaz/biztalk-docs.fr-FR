---
title: "À l’aide du suivi d’événements pour Windows2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW
- Event Tracing for Windows
ms.assetid: 88b91b74-2b2e-40e0-a3e9-1ebd6367abe8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c5f610d75048b250fc90aba7f723cee39c4f2e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-event-tracing-for-windows"></a>À l’aide d’événements de suivi pour Windows
L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld consigne les erreurs, avertissements et messages d'information dans l'Observateur d'événements Windows. Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d'événements pour Windows (ETW). Lorsqu'il est activé, cet outil crée un fichier *.etl pour recevoir les messages. Ce fichier au format binaire doit être converti pour être lu. Pour ce faire, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl : par exemple, tracerpt.exe ou tracedmp.exe.  
  
## <a name="etw-components"></a>Composants ETW  
 Le Suivi d'événements pour Windows comporte trois composants :  
  
-   **Application de contrôleur.** active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).  
  
     Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe. Cela permet de s'assurer que les appels BTAJDEdwardsOneWorldTrace sont en mesure de localiser tracelog.exe dans le système. Par défaut, BTAJDEdwardsOneWorldTrace recherche le chemin d'accès actuel.  
  
    > [!NOTE]
    >  tracelog.exe est disponible dans le kit de développement Microsoft et il est compatible avec les commandes fournies par l'adaptateur BizTalk pour JD Edwards OneWorld. Pour utiliser logman.exe, consultez la documentation de logman.  
  
-   **Application consommateur.** lit les événements enregistrés.  
  
     Pour que l'application consommateur puisse lire les événements du fichier .etl, le Suivi d'événements pour Windows doit les vider dans ce fichier. Normalement, cette opération est effectuée lorsque le contrôleur désactive le suivi.  
  
     Pour utiliser l’application consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel,  **\<en temps réel\> = -rt**.  
  
-   **Fournisseur.** fournit l'événement.  
  
 L'adaptateur BizTalk pour JD Edwards OneWorld inclut cinq fournisseurs différents. Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation). Pour accéder aux fournisseurs enregistrés via le chemin d'accès root\WMI\EventTrace, vous pouvez utiliser des outils tels que WMI CIM Studio.  
  
 L'adaptateur BizTalk pour JD Edwards OneWorld dispose de cinq fournisseurs, vous permettant ainsi de consigner plusieurs sortes de messages :  
  
-   **Fournisseur de journalisation du récepteur.** Le \<élément Trace\> commutateur est **-récepteur**.  
  
-   **Fournisseur castdetails pour le récepteur.** Le \<élément Trace\> commutateur est **- castDetailsReceive**.  
  
-   **Fournisseur de journalisation d’émetteur.** Le \<élément Trace\> commutateur est **-émetteur**.  
  
-   **Fournisseur castdetails pour l’émetteur.** Le \<élément Trace\> commutateur est **- castDetailsTransmit**.  
  
-   **Fournisseur de journalisation de gestion.** Le \<élément Trace\> commutateur est **-gestion**.  
  
 Commande BTAJDEOneWorldTrace  
  
 Pour utiliser le Suivi d'événements pour Windows, exécutez la commande d'adaptateur BizTalk pour JD Edwards OneWorld, à savoir BTAJDEOneWorldTrace.cmd. Utilisez-la comme suit :  
  
```  
BTAJDEOneWorldTrace <Trace element> -start [-cir <MB>|   
      -seq <MB>] [-rt] logfile  
BTAJDEOneWorldTrace <Trace element> -stop  
```  
  
 Où :  
  
-   **\<Élément trace\>**  (obligatoire) est le type de fournisseur.  
  
-   Les options associées sont :  
  
    -   **-castDetailsTransmit**  
  
    -   **-émetteur**  
  
    -   **-castDetailsReceive**  
  
    -   **-récepteur**  
  
    -   **-gestion**  
  
    -   **-start, - stop**: activer ou désactiver le fournisseur.  
  
    -   **-cir \<Mo\>**: taille et type de fichier. -cir signifie qu'il s'agit d'un fichier circulaire. \<Mo\>: taille en mégaoctets.  
  
    -   **-seq \<Mo\>**: taille et type de fichier. -seq signifie qu'il s'agit d'un fichier séquentiel. \<Mo\>: taille en mégaoctets.  
  
    -   **-rt**: définir le mode temps réel sur.  
  
    -   **Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de c:\rtlog.etl).  
  
 Exemple :  
  
```  
BTAJDEOneWorldTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAJDEOneWorldTrace -transmitter -stop  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de JD Edwards OneWorld](../core/troubleshooting-jd-edwards-oneworld.md)