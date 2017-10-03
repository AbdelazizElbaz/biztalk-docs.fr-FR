---
title: "À l’aide du suivi d’événements pour Windows1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW
- provider
- Receiver Logging Provider
- Transmitter Logging Provider
- controller application
- Management Logging Provider
- consumer application
- Event Tracing for Windows
- BTATIBCORVTrace command
ms.assetid: 9e0418e2-7938-4202-83b7-555a90348904
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b51ca273e63ce93ee1ce94a66d0d14a97f807767
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-event-tracing-for-windows"></a>À l’aide d’événements de suivi pour Windows
L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous consigne des messages d'erreur, d'avertissement et d'informations dans l'Observateur d'événements Windows. Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d’événements pour Windows (ETW). Lorsqu'il est activé, cet outil crée un fichier *.etl pour recevoir les messages. Ce fichier au format binaire doit être converti pour être lu. Pour ce faire, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl, par exemple, tracerpt.exe ou tracedmp.exe. Par exemple, l’application tracerpt.exe convertira la \*fichier .etl dans deux fichiers texte : summary.txt et dumpfile.csv.  
  
## <a name="etw-components"></a>Composants ETW  
 Le Suivi d'événements pour Windows comporte trois composants :  
  
-   **Application de contrôleur**: active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).  
  
     Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe. Cela permet de s’assurer que les appels BTATIBCO RendezvousTrace peuvent localiser tracelog.exe dans le système. Par défaut, BTATIBCO RendezvousTrace recherche le chemin d'accès actuel.  
  
> [!NOTE]
>  tracelog.exe est disponible dans le Kit de développement logiciel Microsoft (SDK) et est compatible avec les commandes fournies par l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous. Pour utiliser logman.exe, consultez la documentation de logman.  
  
-   **Application consommateur**: lit les événements enregistrés.  
  
     Pour que l'application consommateur puisse lire les événements dans le fichier .etl, l'outil Suivi d'événements pour Windows doit les vider dans ce fichier. Généralement, cette opération est effectuée lorsque le contrôleur désactive le suivi.  
  
     Pour utiliser l’application consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel, \<en temps réel > = -rt.  
  
-   **Fournisseur**: fournit l’événement.  
  
     L'adaptateur BizTalk pour TIBCO Rendezvous inclut trois fournisseurs distincts, Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation). Pour accéder aux fournisseurs enregistrés via le chemin d'accès root\WMI\EventTrace, vous pouvez utiliser des outils tels que WMI CIM Studio.  
  
 L'adaptateur BizTalk pour TIBCO Rendezvous inclut trois fournisseurs. Vous pouvez ainsi consigner différents types de messages :  
  
-   **Fournisseur de journalisation de récepteur**: le \<Trace element > commutateur est **-récepteur**.  
  
-   Utilisez **-récepteur** pour récupérer tous les messages du journal qui ont été reçus par l’adaptateur lors de l’exécution.  
  
-   **Fournisseur de journalisation de l’émetteur**: le \<Trace element > commutateur est **-émetteur**.  
  
     Utilisez **-émetteur** pour récupérer tous les messages du journal qui ont été transmis par l’adaptateur au moment de l’exécution.  
  
-   **Fournisseur de journalisation de gestion —**le \<Trace element > commutateur est **-gestion**.  
  
     Utilisez **-gestion**pour récupérer tous les messages du journal qui ont été générés pendant la navigation du système du serveur.  
  
## <a name="btatibcorvtrace-command"></a>Commande BTATIBCORVTrace  
 Pour utiliser ETW, exécutez l’adaptateur BizTalk pour commande TIBCO Rendezvous (btatibcbtatibcorvtrace.cmd). Utilisez-la comme suit :  
  
```  
BTATIBCORVTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTATIBCORVTrace <Trace element> -stop  
```  
  
 Où :  **\<Trace element >** (obligatoire) est le type de fournisseur.  
  
 Les options associées sont les suivantes :  
  
-   **-émetteur**  
  
-   **-récepteur**  
  
-   **-gestion**  
  
-   **-start, - stop**: activer ou désactiver le fournisseur.  
  
-   **-cir \<Mo >**: taille et type de fichier. **-cir** est un fichier circulaire. **\<Mo >**: taille en mégaoctets.  
  
-   **-seq \<Mo >**: taille et type de fichier. **-seq** est un fichier séquentiel. **\<Mo >**: taille en mégaoctets.  
  
-   **-rt**: définir le mode temps réel sur.  
  
-   **Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de c:\rtlog.etl).  
  
 Exemple :  
  
```  
BTATIBCORVTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTATIBCORVTrace -transmitter -stop  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage de TIBCO Rendezvous](../core/troubleshooting-tibco-rendezvous.md)