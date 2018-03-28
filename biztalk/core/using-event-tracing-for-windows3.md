---
title: À l’aide du suivi d’événements pour Windows3 | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ETW
- provider
- Receiver Logging Provider
- Transmitter Logging Provider
- controller application
- consumer application
- BTATIBCOEMSTrace command
- Event Tracing for Windows
ms.assetid: 71954431-2015-4d50-b69e-500c883b1e04
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75b2b339c99dcf1b64368c73381d1dbe81e0fb39
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="using-event-tracing-for-windows"></a>À l’aide d’événements de suivi pour Windows
L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service consigne des messages d'erreur, d'avertissement et d'informations dans l'Observateur d'événements Windows. Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d’événements pour Windows (ETW). Lorsqu'il est activé, cet outil crée un fichier *.etl pour recevoir les messages. Ce fichier au format binaire doit être converti pour être lu. Pour ce faire, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl, par exemple, tracerpt.exe ou tracedmp.exe. Par exemple, l’application tracerpt.exe convertit le \*fichier .etl dans deux fichiers texte : summary.txt et dumpfile.csv.  
  
## <a name="etw-components"></a>Composants ETW  
 Le Suivi d'événements pour Windows comporte trois composants :  
  
-   **Application de contrôleur**: active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).  
  
     Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe. Cela permet de s’assurer que les appels BTATIBCO EMSTrace peuvent localiser tracelog.exe dans le système. Par défaut, BTATIBCO EMSTrace recherche le chemin d'accès actuel.  
  
    > [!NOTE]
    >  tracelog.exe est disponible dans le Kit de développement logiciel Microsoft (SDK) et est compatible avec les commandes fournies par l'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service. Pour utiliser logman.exe, consultez la documentation de logman.  
  
-   **Application consommateur**: lit les événements enregistrés.  
  
     Pour que l'application consommateur puisse lire les événements dans le fichier .etl, l'outil Suivi d'événements pour Windows doit les vider dans ce fichier. Généralement, cette opération est effectuée lorsque le contrôleur désactive le suivi.  
  
     Pour utiliser l’application consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel, \<en temps réel\> = -rt.  
  
-   **Fournisseur**: fournit l’événement.  
  
     L'adaptateur BizTalk pour TIBCO Enterprise Message Service inclut trois fournisseurs distincts, Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation). Pour accéder aux fournisseurs enregistrés via le chemin d'accès root\WMI\EventTrace, vous pouvez utiliser des outils tels que WMI CIM Studio.  
  
 L'adaptateur BizTalk pour TIBCO Enterprise Message Service inclut des fournisseurs qui permettent de consigner plusieurs types de messages :  
  
-   **Fournisseur de journalisation de récepteur**: le \<élément Trace\> commutateur est **-récepteur**.  
  
     Utilisez **-récepteur** pour obtenir tous les messages du journal qui ont été reçus par l’adaptateur au moment de l’exécution.  
  
-   **Fournisseur de journalisation de l’émetteur**: le \<élément Trace\> commutateur est **-émetteur**.  
  
     Utilisez **-émetteur**pour obtenir tous les messages du journal qui ont été transmis par l’adaptateur au moment de l’exécution.  
  
### <a name="btatibcoemstrace-command"></a>Commande BTATIBCOEMSTrace  
 Pour utiliser ETW, exécutez l’adaptateur BizTalk pour commande TIBCO Enterprise Message Service (btatibcoemstrace.cmd). Utilisez-la comme suit :  
  
```  
BTATIBCOEMSTrace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTA TIBCOEMSTrace <Trace element> -stop  
```  
  
 Où :  
  
-   **\<Élément trace\>**  (obligatoire) est le type de fournisseur.  
  
 Les options associées sont les suivantes :  
  
-   **-transmitter**  
  
-   **-receiver**  
  
-   **-start, - stop**: activer ou désactiver le fournisseur.  
  
-   **-cir \<Mo\>**: taille et type de fichier. **-cir** est un fichier circulaire. **\<Mo\>**: taille en mégaoctets.  
  
-   **-seq \<Mo\>**: taille et type de fichier. **-seq** est un fichier séquentiel. **\<Mo\>**: taille en mégaoctets.  
  
-   **-rt**: définir le mode temps réel sur.  
  
-   **Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de c:\rtlog.etl).  
  
 Par exemple :  
  
```  
BTATIBCOEMSTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTATIBCOEMSTrace -transmitter -stop  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage de TIBCO Enterprise Message Service](../core/troubleshooting-tibco-enterprise-message-service.md)